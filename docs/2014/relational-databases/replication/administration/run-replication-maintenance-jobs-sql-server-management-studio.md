---
title: Ausführen von Aufträgen zur Replikationswartung (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server replication]
ms.assetid: 0dc485a0-5a50-41eb-a29d-f2b2fb920174
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 23dc128b2c880334fa37093e00a77251094478b9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48108478"
---
# <a name="run-replication-maintenance-jobs-sql-server-management-studio"></a>Ausführen von Aufträgen zur Replikationswartung (SQL Server Management Studio)
  Bei der Replikation werden folgende Wartungsaufträge verwendet:  
  
-   **Abonnements mit Datenüberprüfungsfehlern neu initialisieren**  
  
-   **Agentverlaufscleanup: Verteilung**  
  
-   **Aktualisierung für die Replikationsüberwachung für Verteilung.**  
  
-   **Überprüfung des Replikations-Agents**  
  
-   **Verteilungscleanup: Verteilung**  
  
-   **Cleanup abgelaufener Abonnements**  
  
 Diese Aufträge können über den Ordner **Aufträge** in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] sowie über die Registerkarte **Agents** im Replikationsmonitor gestartet und beendet werden. Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](../monitor/start-the-replication-monitor.md). Die Eigenschaften der einzelnen Aufträge können im Dialogfeld **Auftragseigenschaften - \<Auftrag>** angezeigt und überprüft werden. Der Zugriff hierauf ist über denselben Ordner/dieselbe Registerkarte verfügbar.  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-management-studio"></a>So starten Sie einen Auftrag zur Replikationswartung in Management Studio  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verteiler her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **SQL Server-Agent** und anschließend den Ordner **Aufträge** .  
  
3.  Klicken Sie mit der rechten Maustaste auf einen Auftrag, und klicken Sie dann auf **Auftrag starten** oder **Auftrag beenden**.  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-replication-monitor"></a>So starten Sie einen Auftrag zur Replikationswartung im Replikationsmonitor  
  
1.  Erweitern Sie im Replikationsmonitor eine Verlegergruppe, und wählen Sie dann einen Verleger aus.  
  
2.  Klicken Sie auf die Registerkarte **Agents** .  
  
3.  Klicken Sie mit der rechten Maustaste auf einen Auftrag, und klicken Sie dann auf **Auftrag starten** oder **Auftrag beenden**.  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-management-studio"></a>So zeigen Sie Eigenschaften für einen Auftrag zur Replikationswartung in Management Studio an oder ändern sie  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verteiler her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **SQL Server-Agent** und anschließend den Ordner **Aufträge** .  
  
3.  Klicken Sie mit der rechten Maustaste auf einen Auftrag, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Ändern Sie im Dialogfeld **Auftragseigenschaften - \<Auftrag>** im Bedarfsfall die Eigenschaften, und klicken Sie dann auf **OK**.  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-replication-monitor"></a>So zeigen Sie Eigenschaften für einen Auftrag zur Replikationswartung im Replikationsmonitor an oder ändern sie  
  
1.  Erweitern Sie im Replikationsmonitor eine Verlegergruppe, und wählen Sie dann einen Verleger aus.  
  
2.  Klicken Sie auf die Registerkarte **Agents** .  
  
3.  Klicken Sie mit der rechten Maustaste auf einen Auftrag im Raster, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Ändern Sie im Dialogfeld **Auftragseigenschaften - \<Auftrag>** im Bedarfsfall die Eigenschaften, und klicken Sie dann auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten und Beenden eines Replikations-Agents &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)   
 [Anzeigen von Informationen und Ausführen von Aufgaben für einen Verleger &#40;Replication Monitor&#41;](../monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)   
 [Replikations-Agent-Verwaltung](../agents/replication-agent-administration.md)  
  
  
