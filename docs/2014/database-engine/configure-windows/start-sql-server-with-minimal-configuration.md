---
title: Starten von SQL Server mit Minimalkonfiguration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- minimal configuration [SQL Server]
- starting SQL Server, minimal configuration
ms.assetid: 4d733c99-28b3-42d8-b7f6-7b943b548173
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 146682e4de1e74359bef52e0de6860dcabe8b0c4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48150620"
---
# <a name="start-sql-server-with-minimal-configuration"></a>Starten Sie von SQL Server mit Minimalkonfiguration
  Wenn Konfigurationsprobleme auftreten, die das Starten des Servers verhindern, können Sie eine Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe der Startoption für die Minimalkonfiguration starten. Dies ist die Startoption **-f**. Durch das Starten einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit Minimalkonfiguration wird der Server automatisch in den Einzelbenutzermodus versetzt.  
  
 Beachten Sie Folgendes, wenn Sie eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Modus der Minimalkonfiguration starten:  
  
-   Nur ein einziger Benutzer kann eine Verbindung herstellen, und der CHECKPOINT-Prozess wird nicht ausgeführt.  
  
-   Der Remotezugriff und das Read-Ahead werden deaktiviert.  
  
-   Für den Startvorgang vorgesehene gespeicherte Prozeduren werden nicht ausgeführt.  
  
 Nach dem Starten des Servers mit Minimalkonfiguration sollten Sie den oder die entsprechenden Optionswert(e) des Servers ändern, den Server dann beenden und neu starten.  
  
> [!IMPORTANT]  
>  Stellen Sie mithilfe des **sqlcmd** -Hilfsprogramms und der dedizierten Administratorverbindung (Dedicated Administrator Connection; DAC) eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]her. Wenn Sie eine typische Verbindung verwenden, sollten Sie den SQL Server-Agent-Dienst beenden, bevor Sie eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Modus der Minimalkonfiguration herstellen. Andernfalls verwendet der SQL Server-Agent-Dienst die Verbindung und blockiert sie dadurch.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten, Beenden oder Anhalten des SQL Server-Agent-Dienstes](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)   
 [Diagnoseverbindung für Datenbankadministratoren](diagnostic-connection-for-database-administrators.md)   
 [sqlcmd (Hilfsprogramm)](../../tools/sqlcmd-utility.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Startoptionen für den Datenbank-Engine-Dienst](database-engine-service-startup-options.md)  
  
  
