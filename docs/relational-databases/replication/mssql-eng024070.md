---
title: MSSQL_ENG024070 | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG024070 error
ms.assetid: 23ac7e00-fab6-429b-9f85-2736a322aa65
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 205b2f0da8ad8a8f3523b8d554c84235df45d619
ms.contentlocale: de-de
ms.lasthandoff: 06/22/2017

---
# <a name="mssqleng024070"></a>MSSQL_ENG024070
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|24070|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Dem Client fehlt ein erforderliches Privileg.|  
  
## <a name="explanation"></a>Erklärung  
 Es handelt sich um einen allgemeinen Fehler, der unabhängig von der Verwendung der Replikation ausgelöst werden kann. Auf einem Server in einer Replikationstopologie tritt der Fehler im Allgemeinen auf, weil das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Dienstkonto mithilfe des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Dienstkontroll-Managers anstelle des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Managers geändert wurde. Wenn Sie versuchen, nach der Änderung des Dienstkontos einen Agentauftrag auszuführen, erzeugt dieser Auftrag möglicherweise einen Fehler, und es wird eine Fehlermeldung wie die folgende angezeigt:  
  
 `Executed as user: \<UserAccount>. Replication-Replication Snapshot Subsystem: agent \<AgentName> failed. Executed as user: \<UserAccount>. A required privilege is not held by the client. The step failed. [SQLSTATE 42000] (Error 14151). The step failed.`  
  
 Dieses Problem tritt auf, weil der Windows-Dienstkontroll-Manager dem neuen Dienstkonto nicht die erforderlichen Berechtigungen für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent zuweisen kann.  
  
## <a name="user-action"></a>Benutzeraktion  
 Verwenden Sie zum Ändern von Dienstkonten und Kennwörtern immer den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager anstelle des Windows-Dienstkontroll-Managers, um dieses Problem in Zukunft zu vermeiden.  
  
 Ändern Sie das Dienstkonto mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Managers zurück in das ursprüngliche Konto, um das Problem zu beheben. Verwenden Sie anschließend den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager, um das Dienstkonto in das neue Konto zu ändern. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager fügt das neue Konto dann der folgenden Sicherheitsgruppe hinzu:  
  
 SQLServer2008SQLAgentUser$ComputerName$InstanceName  
  
 Als Mitglied dieser Sicherheitsgruppe verfügt das neue Konto über die erforderlichen Berechtigungen, um den Auftrag des Replikations-Agents auszuführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Verwalten von Anmeldeinformationen und Kennwörtern bei der Replikation](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [SQL Server-Konfigurations-Manager](../../relational-databases/sql-server-configuration-manager.md)  
  
  
