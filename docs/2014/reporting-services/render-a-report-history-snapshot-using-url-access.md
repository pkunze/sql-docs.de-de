---
title: Rendern von Berichtsverlaufs-Momentaufnahmen mit URL-Zugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services], report history
- history snapshots [Reporting Services]
- historical data [Reporting Services]
- snapshots [Reporting Services], URL access
- snapshots [Reporting Services], rendering report history
ms.assetid: 3f87f82d-0e61-4492-9c4b-f5238c39e8cd
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: f8b857d0aab5cc64255e3d041d58fdc7ab398358
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48216620"
---
# <a name="render-a-report-history-snapshot-using-url-access"></a>Rendern von Berichtsverlaufs-Momentaufnahmen mit URL-Zugriff
  Sie können einen Bericht auf der Grundlage einer Berichtsverlaufs-Momentaufnahme rendern, indem Sie den Parameter *rs:Snapshot* angeben und seinen Wert auf eine gültige Momentaufnahme-ID festlegen. Der Parameterwert hat das Format YYYY-MM-DDTHH:MM:SS und basiert auf dem ISO-Standard 8601 (Standard International Organization for Standardization).  
  
 Wenn Sie diesen Parameter weglassen, wird der Bericht gemäß den Optionseinstellungen für die Berichtsausführung und Cacheverwaltung des Berichtsservers gerendert. Weitere Informationen zur Ausführung von Berichten finden Sie unter [Festlegen von Berichtsverarbeitungseigenschaften](report-server/set-report-processing-properties.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine URL, die eine Berichtsverlaufs-Momentaufnahme abruft:  
  
```  
http://myrshost/reportserver?/SampleReports/Company Sales&rs:Snapshot=2003-04-07T13:40:02  
```  
  
## <a name="see-also"></a>Siehe auch  
 [URL-Zugriff &#40;SSRS&#41;](url-access-ssrs.md)   
 [URL Access Parameter Reference (URL-Zugriffsparameterverweis)](url-access-parameter-reference.md)  
  
  
