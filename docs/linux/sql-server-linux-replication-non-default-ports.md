---
title: Konfigurieren von SQL Server-Replikation momentaufnahmefreigaben Ordner unter Linux | Microsoft-Dokumentation
description: Dieser Artikel beschreibt, wie SQLServer-Replikation von Momentaufnahmen Ordner Freigaben unter Linux konfigurieren.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 9/24/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.workload: On Demand
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: dae79e05ff7f92e9e93543fd3540b5a2b019e255
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47850098"
---
# <a name="configure-replication-with-non-default-ports"></a>Konfigurieren der Replikation mit nicht standardmäßigen ports

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Sie können mit SQL Server auf Linux-Instanzen Lauschen an einem beliebigen Port konfiguriert werden, mit der Mssql-Conf-Einstellung network.tcpport Replikation konfigurieren. Der Port muss, um den Namen des Servers während der Konfiguration angefügt werden soll, wenn die folgenden Bedingungen erfüllt sind:

1. Einrichten der Replikation umfasst eine Instanz von SQL Server unter Linux
2. Jede Instanz (Windows oder Linux) lauscht an einem nicht standardmäßigen Port. 

Der Servername einer Instanz von ausgeführt wird, @ finden@servername auf der Instanz.

## <a name="examples"></a>Beispiele

"Server1" lauscht an Port 1500 für Linux. Führen Sie zum Konfigurieren von "Server1" für die Verteilung `sp_adddistributor` mit `@distributor`. Zum Beispiel: 

```sql
exec sp_adddistributor @distributor = 'Server1,1500'
```

"Server1" lauscht an Port 1500 für Linux. Um einen Verleger für den Verteiler konfigurieren, führen Sie `sp_adddistpublisher` mit `@publisher`. Zum Beispiel:

```sql
exec sp_adddistpublisher @publisher = 'Server1,1500' ,  ,  
```

"Server2" Lauscht auf Port 6549 unter Linux. Führen Sie zum Konfigurieren von "Server2" als einen Abonnenten `sp_addsubscription` mit `@subscriber`. Zum Beispiel:

```sql
exec sp_addsubscription @subscriber = 'Server2,6549' ,  ,  
```

"Server3" Lauscht auf Port 6549 auf Windows, die mit Server3 Servernamen und Instanznamen des MSSQL2017. Um "Server3" als einen Abonnenten zu konfigurieren, führen die `sp_addsubscription` mit `@subscriber`. Zum Beispiel:

```sql
exec sp_addsubscription @subscriber = 'Server3/MSSQL2017,6549',  ,  
```

## <a name="next-steps"></a>Nächste Schritte

[Konzepte: SQLServer-Replikation unter Linux](sql-server-linux-replication.md)

[Gespeicherte Replikationsprozeduren](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

