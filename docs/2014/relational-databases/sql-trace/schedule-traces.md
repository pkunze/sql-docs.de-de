---
title: Planen von Ablaufverfolgungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], events
- traces [SQL Server]
- traces [SQL Server], stopping
- events [SQL Server], filters
- scheduling traces [SQL Server]
- traces [SQL Server], scheduling
- stopping traces
ms.assetid: 620b79db-924b-4502-8af3-39efcfca245d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0c680ea7b2fc8360fce0ff81f0d22f1816107f49
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48157244"
---
# <a name="schedule-traces"></a>Planen von Ablaufverfolgungen
  Es gibt zwei Möglichkeiten, um die Ablaufverfolgung in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu planen. Folgende Aktionen sind möglich:  
  
-   Beendigungszeit für Ablaufverfolgung aktivieren.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent zum Planen einer Ablaufverfolgung verwenden.  
  
## <a name="specifying-a-stop-time"></a>Angeben einer Beendigungszeit  
 Sie können eine Beendigungszeit für die Ablaufverfolgung angeben, wenn Sie gespeicherte Prozeduren von [!INCLUDE[tsql](../../includes/tsql-md.md)] oder [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]verwenden. Die Beendigungszeit muss festgelegt werden, wenn die Ablaufverfolgung konfiguriert wird.  
  
## <a name="scheduling-traces-by-using-sql-server-agent"></a>Planen von Ablaufverfolgungen mithilfe des SQL Server-Agents  
 Die beste Möglichkeit zum Planen von Ablaufverfolgungen ist die Verwendung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents, um die Ablaufverfolgung zu starten und dann mit der gespeicherten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Prozedur **sp_trace_setstatus**oder mit dem [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]eine Beendigungszeit für die Ablaufverfolgung anzugeben.  
  
 **So legen Sie einen Beendigungszeitfilter für Ablaufverfolgungen fest**  
  
 [Filtern von Ereignissen anhand der Ereignisendzeit &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
 [sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)  
  
## <a name="see-also"></a>Siehe auch  
 [Automatisierte Administrationstasks &#40;SQL Server Agent&#41;](../../ssms/agent/sql-server-agent.md)  
  
  
