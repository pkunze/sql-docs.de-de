---
title: Korrelieren einer Ablaufverfolgung mit Windows-Leistungsprotokolldaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- correlating trace with log data
- logs [SQL Server], traces
- Profiler [SQL Server Profiler], correlating trace with log data
- traces [SQL Server], logs
- SQL Server Profiler, correlating trace with log data
ms.assetid: 1e4412c8-d27c-4aae-9b35-214128d1d00a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7d8806911251c15a8de0e7f71f032038c8686df4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48217840"
---
# <a name="correlate-a-trace-with-windows-performance-log-data"></a>Korrelieren einer Ablaufverfolgung mit Windows-Leistungsprotokolldaten
  Mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]können Sie ein Microsoft Windows-Leistungsprotokoll öffnen, die Leistungsindikatoren auswählen, die Sie mit einer Ablaufverfolgung korrelieren möchten, und die ausgewählten Leistungsindikatoren zusammen mit der Ablaufverfolgung auf der grafischen Benutzeroberfläche von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] anzeigen. Wenn Sie ein Ereignis im Ablaufverfolgungsfenster auswählen, zeigt ein senkrechter roter Strich im Datenfensterbereich des Systemmonitors von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] an, welche Leistungsprotokolldaten mit dem ausgewählten Ablaufverfolgungsereignis korrelieren.  
  
 Um eine Ablaufverfolgung mit Leistungsindikatoren zu korrelieren, öffnen Sie eine Ablaufverfolgungsdatei oder -tabelle, die die Datenspalten **StartTime** und **EndTime** data columns, und then click **Datei** von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Leistungsdaten importieren** . Anschließend können Sie das Leistungsprotokoll öffnen und die Systemmonitor-Objekte und -Leistungsindikatoren auswählen, die Sie mit der Ablaufverfolgung korrelieren möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Korrelieren einer Ablaufverfolgung mit Windows-Leistungsprotokolldaten &#40;SQL Server Profiler&#41;](correlate-a-trace-with-windows-performance-log-data.md)  
  
  
