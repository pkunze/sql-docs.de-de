---
title: CSV-Geräteinformationseinstellungen | Microsoft-Dokumentation
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- CSV [Reporting Services]
- device information settings [Reporting Services], CSV rendering
ms.assetid: f96f83a6-50bc-48ce-9fcd-fd9e1952d40a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 320ad1972dcf949200b6fafa5eafc4fda3bd2348
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678598"
---
# <a name="csv-device-information-settings"></a>CSV-Geräteinformationseinstellungen
  Die Geräteinformationseinstellungen für die CSV-Renderingerweiterung ermöglichen das Ändern von Trennzeichen und Qualifizierern sowie das Festlegen der Behandlung von Zeilenumbrüchen. Zudem können die Erweiterung der Datei gesendet sowie die Codierung und der Einschluss von Kopfzeilen in der Ausgabe gesendet werden. Da es sich bei Trennzeichen meist um Sonderzeichen handelt, sollten Sie sie in einem CDATA-Abschnitt codieren, wenn die Einstellungen als XML geschrieben werden.  
  
 In der folgenden Tabelle sind die Geräteinformationseinstellungen zum Rendern in das Textformat aufgeführt.  
  
|Einstellung|value|  
|-------------|-----------|  
|**Codierung**|Der Internet Assigned Numbers Authority (IANA)-Name einer Zeichencodierung, die von .NET Framework unterstützt wird. Der Standardwert ist **UTF-8**. Beispiele für andere Werte: ASCII, UTF-7 und UTF-16.|  
|**ExcelMode**|Gibt an, dass die Zielausgabe für Excel bestimmt ist. Der Standardwert ist **true**.|  
|**FieldDelimiter**|Das Trennzeichen, das in das Ergebnis eingefügt werden soll. Der Standardwert ist ein Komma (,). Sie sollten den Wert dieser Geräteinformationen URL-codieren, wenn Sie ihn in einer URL übergeben. Beispielsweise sollte ein als Trennzeichen verwendetes Tabstoppzeichen als "%09" angegeben werden.<br /><br /> Sie können das Standardfeldtrennzeichen in ein beliebiges Zeichen ändern, einschließlich TAB, indem Sie die Geräteinformationseinstellungen in der Konfigurationsdatei ändern. Um z.B. TAB zu verwenden, aktualisieren Sie die FieldDelimiter-Einstellung auf \<FieldDelimiter xml:space="preserve">[TAB]\</FieldDelimiter><br /><br /> In diesem Beispiel ist [TAB] ein wirkliches Tabstoppzeichen. Dies bedeutet, dass in der Konfigurationsdatei Leerzeichen angezeigt werden. Das "xml:space"-Attribut weist Parser an, Leerzeichen beizubehalten.|  
|**FileExtension**|Die Dateierweiterung, die für das Ergebnis verwendet wird. Der Standardwert lautet **.CSV**. Wenn sowohl **FileExtension** als auch **Extension** angegeben wird, hat **FileExtension** Vorrang.|  
|**NoHeader**|Gibt an, ob die Kopfzeile aus der Ausgabe ausgeschlossen ist. Der Standardwert ist **false**.|  
|**Qualifizierer**|Die Qualifiziererzeichenfolge, die um Ergebnisse gesetzt werden soll, welche das Feldtrennzeichen oder das Datensatztrennzeichen enthalten. Wenn die Ergebnisse den Qualifizierer enthalten, wird der Qualifizierer wiederholt. Die **Qualifier** -Einstellung muss sich von der **FieldDelimiter** -Einstellung und der **RecordDelimiter** -Einstellung unterscheiden. Der Standardwert ist ein Anführungszeichen (").|  
|**RecordDelimiter**|Das Datensatztrennzeichen, das am Ende jedes Datensatzes gesetzt werden soll. Der Standardwert ist \<cr>\<lf>.|  
|**SuppressLineBreaks**|Gibt an, ob Zeilenumbrüche aus den in der Ausgabe enthaltenen Daten entfernt werden. Der Standardwert ist **false**. Wenn der Wert **true**ist, können die **FieldDelimiter**-Einstellung, die **RecordDelimiter**-Einstellung und die **Qualifier** -Einstellung kein Leerzeichen sein.|  
|**UseFormattedValues**|Gibt an, ob formatierte Zeichenfolgen in die CSV-Ausgabe gestellt werden. Der Standardwert ist **true** , wenn **ExcelMode** den Wert **true**hat; ansonsten ist es **false**.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Anpassen der Parameter für Renderingerweiterungen in der Datei „RSReportServer.config“](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Technische Referenz (SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
