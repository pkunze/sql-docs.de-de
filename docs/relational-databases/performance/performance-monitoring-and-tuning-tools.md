---
title: Tools für die Leistungsüberwachung und -optimierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- tools [SQL Server], monitoring performance
- monitoring server performance [SQL Server], tools
- monitoring performance [SQL Server], tools
- database performance [SQL Server], tools
- tuning databases [SQL Server], tools
- database monitoring [SQL Server], tools
- performance [SQL Server], monitoring tools
- server performance [SQL Server], tools
ms.assetid: 31529dfe-68e7-49f7-b3c2-39fcecf33a95
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c5411043ae54d4082cd4d1b2c194b48ae9d78b65
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626838"
---
# <a name="performance-monitoring-and-tuning-tools"></a>Tools für die Leistungsüberwachung und -optimierung
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt einen umfassenden Satz von Tools für die Überwachung von Ereignissen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und für die Optimierung des physischen Datenbankentwurfs bereit. Das richtige Tool ergibt sich aus der Art der gewünschten Überwachung oder Optimierung sowie aus den jeweils zu überwachenden Ereignissen.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stehen die folgenden Tools zur Überwachung und Optimierung zur Verfügung:  
  
|Tool|und Beschreibung|  
|----------|-----------------|  
|[sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] verfolgt Engine-Prozessereignisse wie das Starten eines Batches oder einer Transaktion. So können Sie die Server- und Datenbankaktivität überwachen (z.B. Deadlocks, schwerwiegende Fehler oder Anmeldeaktivität). Sie können [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] -Daten in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle oder -Datei aufzeichnen und später analysieren oder die aufgezeichneten Ereignisse in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] schrittweise wiedergeben, um den genauen Ablauf anzuzeigen.|  
|[SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay kann Ablaufverfolgungsdaten mithilfe mehrerer Computer wiedergeben und eine missionskritische Arbeitsauslastung simulieren.|  
|[Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)|Der Systemmonitor verfolgt hauptsächlich die Ressourcennutzung, wie die Anzahl der verwendeten Seitenanforderungen des Puffer-Managers. So können Sie die Serverleistung und Aktivität mit vordefinierten Objekten und Leistungsindikatoren überwachen oder benutzerdefinierte Leistungsindikatoren zum Überwachen von Ereignissen verwenden. Der Systemmonitor erfasst Leistungsindikatoren und Raten für die Ereignisse anstelle von Daten über die Ereignisse (z. B. Speicherauslastung, Anzahl der aktiven Transaktionen, Anzahl der blockierten Sperren oder CPU-Aktivität). Für bestimmte Leistungsindikatoren können Schwellwerte festgelegt werden, um Warnungen zu generieren, durch die Operatoren benachrichtigt werden.<br /><br /> Der Systemmonitor kann unter den Betriebssystemen Microsoft Windows Server und Windows ausgeführt werden. Hiermit können Sie eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (remotely oder lokal) unter Windows NT 4.0 (oder höher) überwachen.<br /><br /> Der wichtigste Unterschied zwischen [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] und dem Systemmonitor liegt darin, dass bei [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] die Datenbank-Engine-Ereignisse verfolgt werden, im Systemmonitor dagegen die Ressourcennutzung im Zusammenhang mit Serverprozessen.|  
|[Öffnen des Aktivitätsmonitors &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)|Der Aktivitätsmonitor von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eignet sich für eine Ad-hoc-Ansicht der aktuellen Aktivität. Außerdem werden darin die folgenden Informationen grafisch angezeigt:<br /><br /> Prozesse, die unter einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt werden<br /><br /> Gesperrte Prozesse<br /><br /> Sperren<br /><br /> Benutzeraktivität|  
|[Live-Abfragestatistik](../../relational-databases/performance/live-query-statistics.md)|Zeigt Echtzeitstatistiken zu den Ausführungsschritten einer Abfrage an. Da diese Daten bereits während der Ausführung einer Abfrage verfügbar sind, ist diese Statistik eine große Hilfe beim Debuggen von Leistungsproblemen in Zusammenhang mit Abfragen.|  
|[Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)|Erweiterte Ereignisse ist ein Lightweight-Leistungsüberwachungssystem, das sehr wenige Leistungsressourcen verwendet. Die Funktion „Erweiterte Ereignisse“ stellt zwei grafische Benutzeroberflächen („Assistent für neue Sitzungen“ und „Neue Sitzung“) zum Erstellen, Ändern, Anzeigen und Analysieren der Sitzungsdaten bereit.|  
|[Execution Related Dynamic Management Views and Functions &#40;Transact-SQL&#41; (Dynamische Verwaltungssichten und Funktionen im Zusammenhang mit der Ausführung (Transact-SQL))](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)|Dynamische Verwaltungssichten im Zusammenhang mit der Ausführung ermöglichen Ihnen das Überprüfen von Informationen im Zusammenhang mit der Ausführung.|
|[SQL-Ablaufverfolgung](../../relational-databases/sql-trace/sql-trace.md)|[!INCLUDE[tsql](../../includes/tsql-md.md)] gespeicherte Prozeduren, mit denen die Ablaufverfolgung erstellt, gefiltert und definiert wird:<br /><br /> [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)<br /><br /> [sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)<br /><br /> [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)<br /><br /> [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)<br /><br /> [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)|  
|Fehlerprotokolle|Das Windows-Anwendungsereignisprotokoll liefert ein Gesamtbild der Ereignisse in den Betriebssystemen Windows Server und Windows insgesamt sowie der Ereignisse in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent und der Volltextsuche. Hier sind Informationen zu Ereignissen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthalten, die anderweitig nicht zur Verfügung stehen. Sie können die Informationen im Fehlerprotokoll für die Problembehandlung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]nutzen.|  
|[Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)|Die folgenden im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -System gespeicherten Prozeduren bilden eine leistungsfähige Alternative für zahlreiche Überwachungsaufgaben:<br /><br /> [sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md):<br />                    Meldet Momentaufnahme-Informationen zu aktuellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Benutzern und -Prozessen, einschließlich der derzeit ausgeführten Anweisung und der Information, ob die Anweisung blockiert wurde.<br /><br /> [sp_lock &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md):<br />                    Meldet Momentaufnahme-Informationen zu Sperren, einschließlich der Objekt-ID, der Index-ID, des Sperrentyps und des Typs oder der Ressource, auf die die Sperre angewendet wird.<br /><br /> [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md): <br />                    Zeigt einen Schätzwert des Speicherplatzes an, der von einer Tabelle (oder einer gesamten Datenbank) belegt wird.<br /><br /> [sp_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md):<br />                    Zeigt Statistiken, wie die CPU-Auslastung, die E/A-Verwendung und die Leerlaufzeit seit der letzten Ausführung von **sp_monitor** an.|  
|[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)|DBCC-Anweisungen (Database Consistency Checker, Datenbankkonsistenzprüfer) ermöglichen die Überprüfung der Leistungsstatistik und der logischen und physischen Konsistenz einer Datenbank.|  
|[Integrierte Funktionen &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)|Integrierte Funktionen zeigen Momentaufnahmestatistiken über die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Aktivität seit dem Starten des Servers an, die in vordefinierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Leistungsindikatoren gespeichert werden. So enthält beispielsweise **@@CPU_BUSY** die Zeitspanne, während der die CPU [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Code ausführte; **@@CONNECTIONS** enthält die Anzahl der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verbindungen oder versuchten Verbindungen, und **@@PACKET_ERRORS** enthält die Anzahl der Netzwerkpakete, die über [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verbindungen übertragen wurden.|  
|[Ablaufverfolgungsflags &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)|Ablaufverfolgungsflags zeigen Informationen zu einer bestimmten Aktivität im Server an und werden für die Diagnose von Problemen oder Leistungskriterien (z. B. mehrere Deadlocks in Folge) verwendet.|  
|[Datenbankoptimierungsratgeber](../../relational-databases/performance/database-engine-tuning-advisor.md)|Der Datenbankoptimierungsratgeber analysiert die Leistungsauswirkungen von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen, die auf die Datenbanken für die Optimierung ausgeführt werden. Der Datenbankoptimierungsratgeber bietet Empfehlungen zum Hinzufügen, Entfernen oder Ändern von Indizes, indizierten Sichten und Partitionierungen.|  
  
## <a name="choosing-a-monitoring-tool"></a>Auswählen von Überwachungstools  
 Die Wahl eines geeigneten Überwachungstools hängt von der Art des Ereignisses und der Aktivität, die überwacht werden sollen, ab.  
  
|Ereignis oder Aktivität|Erweiterte Ereignisse|SQL Server Profiler|Distributed Replay|Systemmonitor|Aktivitätsmonitor|Transact-SQL|Fehlerprotokolle|  
|-----------------------|-----------------------|-------------------------|------------------------|--------------------|----------------------|-------------------|----------------|  
|Trendanalyse|Benutzerkontensteuerung|Benutzerkontensteuerung||Benutzerkontensteuerung||||  
|Wiedergeben aufgezeichneter Ereignisse||Ja (von einem einzelnen Computer)|Ja (von mehreren Computern)|||||  
|Ad-hoc-Überwachung||Benutzerkontensteuerung|||Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Generieren von Warnungen||||Benutzerkontensteuerung||||  
|Grafische Schnittstelle|Benutzerkontensteuerung|Benutzerkontensteuerung||Benutzerkontensteuerung|Benutzerkontensteuerung||Benutzerkontensteuerung|  
|Verwendung im Rahmen von benutzerdefinierten Anwendungen|Benutzerkontensteuerung|Ja*||||Benutzerkontensteuerung||  
  
 *Mithilfe von gespeicherten [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] -Systemprozeduren.  
  
## <a name="windows-monitoring-tools"></a>Windows-Überwachungstools  
 Die Windows-Betriebssysteme sowie Windows Server 2003 enthalten außerdem die folgenden Überwachungstools:  
  
|Tool|und Beschreibung|  
|----------|-----------------|  
|Task-Manager|Zeigt eine vergleichende Übersicht über die Prozesse und Anwendungen an, die im System ausgeführt werden.|  
|Netzwerkmonitor-Agent|Überwacht die Netzwerkbelastung.|  
  
 Weitere Informationen zu den Windows-Betriebssystemen oder zu den Windows-Server-Tools finden Sie in der Windows-Dokumentation.  
  
  
