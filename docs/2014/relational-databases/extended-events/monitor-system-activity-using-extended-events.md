---
title: Überwachen der Systemaktivität mit erweiterten Ereignissen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- xe
- extended events [SQL Server], monitoring system activity
ms.assetid: d83ad88f-818c-49fe-a9a9-299f704fca53
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 96897590a9d6b0607422ab98682cb6415f11e3d4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48143130"
---
# <a name="monitor-system-activity-using-extended-events"></a>Überwachen der Systemaktivität mit erweiterten Ereignisses
  Das folgende Verfahren veranschaulicht, wie Extended Events mit der Ereignisablaufverfolgung für Windows (ETW) zum Überwachen der Systemaktivität verwendet werden kann. Außerdem wird gezeigt, wie die Anweisungen CREATE EVENT SESSION, ALTER EVENT SESSION und DROP EVENT SESSION verwendet werden.  
  
 Das Ausführen dieser Tasks umfasst die Verwendung des Abfrage-Editors in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , um den folgenden Vorgang durchzuführen. Das Verfahren erfordert außerdem, mithilfe der Eingabeaufforderung ETW-Befehle auszuführen.  
  
### <a name="to-monitor-system-activity-using-extended-events"></a>So überwachen Sie die Systemaktivität mit erweiterten Ereignissen  
  
1.  Geben Sie im Abfrage-Editor die folgenden Anweisungen aus, um eine Ereignissitzung zu erstellen und zwei Ereignisse hinzuzufügen. Diese Ereignisse, checkpoint_begin und checkpoint_end, werden am Anfang und am Ende eines Datenbankprüfpunkts ausgelöst.  
  
    ```  
    CREATE EVENT SESSION test0  
    ON SERVER  
    ADD EVENT sqlserver.checkpoint_begin,  
    ADD EVENT sqlserver.checkpoint_end  
    WITH (MAX_DISPATCH_LATENCY = 1 SECONDS)  
    go  
    ```  
  
2.  Fügen Sie das Ziel mit 32 Buckets hinzu, um die Anzahl der Prüfpunkte basierend auf der Datenbank-ID zu zählen.  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    ADD TARGET package0.histogram  
    (  
          SET slots = 32, filtering_event_name = 'sqlserver.checkpoint_end', source_type = 0, source = 'database_id'  
    )  
    go  
    ```  
  
3.  Geben Sie die folgenden Anweisungen aus, um das ETW-Ziel hinzuzufügen. So können Sie die Anfangs- und Endereignisse anzeigen, mit denen die Dauer des Prüfpunkts bestimmt wird.  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    ADD TARGET package0.etw_classic_sync_target  
    go  
    ```  
  
4.  Geben Sie die folgenden Anweisungen aus, um die Sitzung und die Ereignisauflistung zu starten.  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    STATE = start  
    go  
    ```  
  
5.  Geben Sie die folgenden Anweisungen aus, um drei Ereignisse auszulösen.  
  
    ```  
    USE tempdb  
          checkpoint  
    go  
    USE master  
          checkpoint  
          checkpoint  
    go  
    ```  
  
6.  Geben Sie die folgenden Anweisungen aus, um die Ereigniszähler anzuzeigen.  
  
    ```  
    SELECT CAST(xest.target_data AS xml) Bucketizer_Target_Data_in_XML  
    FROM sys.dm_xe_session_targets xest  
    JOIN sys.dm_xe_sessions xes ON xes.address = xest.event_session_address  
    JOIN sys.server_event_sessions ses ON xes.name = ses.name  
    WHERE xest.target_name = 'histogram' AND xes.name = 'test0'  
    go  
    ```  
  
7.  Geben Sie die folgenden Befehle an der Eingabeaufforderung aus, um die ETW-Daten anzuzeigen.  
  
    > [!NOTE]  
    >  Um Hilfe für den **tracerpt** -Befehl aufzurufen, geben Sie an der Eingabeaufforderung `tracerpt /?`ein.  
  
    ```  
    logman query -ets --- List the ETW sessions. This is optional.  
    logman update XE_DEFAULT_ETW_SESSION -fd -ets --- Flush the ETW log.  
    tracerpt %temp%\xeetw.etl -o xeetw.txt --- Dump the events so they can be seen.  
    ```  
  
8.  Geben Sie die folgenden Anweisungen aus, um die Ereignissitzung zu beenden und vom Server zu entfernen.  
  
    ```  
    ALTER EVENT SESSION test0  
    ON SERVER  
    STATE = STOP  
    go  
  
    DROP EVENT SESSION test0  
    ON SERVER  
    go  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)   
 [DROP EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-event-session-transact-sql)   
 [Ereignisse Katalogsichten für erweiterte &#40;Transact-SQL&#41;] (~/relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql   
 [Dynamische Verwaltungssichten für erweiterte Ereignisse](../views/views.md)   
 [SQL Server Extended Events Targets](../../database-engine/sql-server-extended-events-targets.md)  
  
  
