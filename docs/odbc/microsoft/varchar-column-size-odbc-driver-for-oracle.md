---
title: VARCHAR-Spaltengröße (ODBC-Treiber für Oracle) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], ODBC driver for Oracle
- varchar column size [ODBC]
- ODBC driver for Oracle [ODBC], data types
ms.assetid: eb4cb410-3d00-4251-8c5e-a06f36c4dac7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db2871324f92ef6d84a8bf8313db105489100a96
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47847568"
---
# <a name="varchar-column-size-odbc-driver-for-oracle"></a>VARCHAR-Spaltengröße (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 In 8 wurde die maximale Größe einer VARCHAR-Spalte von 2000 auf 4.000 Byte erhöht. Die Oracle-Clientsoftware 7.3.x hat keine Möglichkeit, einen Parameterwert, der größer als 2000 Bytes zu binden. Aus diesem Grund, wenn Sie eine Tabelle mit einer VARCHAR-Spalte, der größer als 2000 Bytes erstellen, werden Sie zum Ausführen von parametrisierten einfügungen, Updates, löschungen und Abfragen dafür mit Daten, die überschreitet den Grenzwert von 2000-Byte-der-Clientsoftware kann nicht. Da sowohl der ODBC-Treiber für Oracle der OLE DB-Anbieter für Oracle verwenden parametrisierte einfügungen, Updates, löschungen und Abfragen, werden sie in diesem Fall ORA-01026 Fehler gemeldet. Daten, die innerhalb der Beschränkungen, die von der Oracle-Clientsoftware funktioniert. Um diese 2000-Byte-Grenze zu vermeiden, müssen Sie die Clientsoftware auf 8 aktualisieren (8.0.4.1.1c oder höher).
