---
title: "PPTX-Geräteinformationseinstellungen | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 09/11/2015
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- render
- powerpoint
- pptx
- export
ms.assetid: 4dc2045f-8025-41a3-8f9d-5635fb24cf4a
caps.latest.revision: 6
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3aa67165e961e76569daadff1fc610c4d16a1e63
ms.contentlocale: de-de
ms.lasthandoff: 08/09/2017

---
# <a name="pptx-device-information-settings"></a>PPTX-Geräteinformationseinstellungen
  In der folgenden Tabelle werden die Einstellungen der Geräteinformationen zum Rendern von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichten im PPTX-Format aufgeführt.  
  
|Einstellung|Wert|  
|-------------|-----------|  
|**Spalten**|Die für den Bericht gewünschte Anzahl der Spalten. Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**ColumnSpacing**|Der für den Bericht gewünschte Spaltenabstand. Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**DpiX**|Die horizontale Auflösung des Ausgabebilds. Der Standardwert ist **96** Gilt für die Ausgabeformate **BMP**, **GIF**, **PNG**und **TIFF** .|  
|**DpiY**|Die vertikale Auflösung des Ausgabebilds. Der Standardwert ist **96** Gilt für die Ausgabeformate **BMP**, **GIF**, **PNG**und **TIFF** .|  
|**EndPage**|Die letzte Seite des zu rendernden Berichts. Der Standardwert ist der Wert für **StartPage**.|  
|**MarginBottom**|Der für den Bericht gewünschte Wert für den unteren Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z.B. **1in**). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**MarginLeft**|Der für den Bericht gewünschte Wert für den linken Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z.B. **1in**). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**MarginRight**|Der für den Bericht gewünschte Wert für den rechten Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z.B. **1in**). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**MarginTop**|Der für den Bericht gewünschte Wert für den oberen Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z.B. **1in**). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**PageHeight**|Die für den Bericht gewünschte Seitenhöhe in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z.B. **11in**). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**PageWidth**|Die für den Bericht gewünschte Seitenbreite in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert angeben, gefolgt von „in“ (z.B. **8,5in**). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**StartPage**|Die erste Seite des zu rendernden Berichts. Der Wert **0** gibt an, dass alle Seiten des Berichts gerendert werden. Der Standardwert ist **1**.|  
|**UseReportPageSize**|Wenn „UseReportPageSize =**false** “, ist die Standardfoliengröße der PowerPoint-Standard 13,333” x 7,5” (Seitenverhältnis 16:9). Wenn "UseReportPageSize =true", ist die Standardfoliengröße die definierte Seitengröße des Berichts.<br /><br /> Der Standardwert ist **false**<br /><br /> Beachten Sie, dass die PageWidth- und PageHeight-Einstellungen die Standardbreite und -höhe überschreiben.|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Anpassen der Parameter für Renderingerweiterungen in "rsreportserver.config"](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Technische Referenz &#40; SSRS &#41;](../reporting-services/technical-reference-ssrs.md)  
  
  
