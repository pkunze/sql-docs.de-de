---
title: SAP BW Ziel-Editor (Seite erweitert) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.sapbwdestination.advanced.f1
ms.assetid: 862957db-bbc6-4dda-bc0e-591457f1baa7
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e15c7e770bc46c3ddc3a9f58ae99a5440617720d
ms.contentlocale: de-de
ms.lasthandoff: 08/03/2017

---
# <a name="sap-bw-destination-editor-advanced-page"></a>Ziel-Editor für SAP BW (Seite Erweitert)
  Auf der Seite **Erweitert** im **Ziel-Editor für SAP BW** legen Sie erweiterte Einstellungen wie Paketgröße und Timoutinformationen fest.  
  
 Weitere Informationen zum SAP BW-Ziel von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW finden Sie unter [SAP BW-Ziel](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Die Dokumentation für Microsoft Connector 1.1 for SAP BW setzt Kenntnisse der SAP NetWeaver BW-Umgebung voraus. Weitere Informationen zu SAP NetWeaver BW oder Informationen zur Konfiguration von SAP NetWeaver BW-Objekten und -Prozessen finden Sie in der SAP-Dokumentation.  
  
 **So öffnen Sie die Seite "Erweitert"**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket, in dem das SAP BW-Ziel enthalten ist.  
  
2.  Doppelklicken Sie auf der Registerkarte **Datenfluss** auf das SAP BW-Ziel.  
  
3.  Klicken Sie im **Ziel-Editor für SAP BW**auf **Erweitert** , um die Seite **Erweitert** des Editors zu öffnen.  
  
## <a name="options"></a>enthalten  
  
> [!NOTE]  
>  Wenn Sie nicht alle Werte kennen, die zur Konfiguration des Ziels erforderlich sind, müssen Sie ggf. Ihren SAP-Administrator um Unterstützung bitten.  
  
 **Paketgröße**  
 Geben Sie an, wie viele Datenzeilen auf einmal übertragen werden. Der optimale Wert für diesen Parameter hängt vom SAP NetWeaver BW-System und ggf. zusätzlichen Schritten zur Verarbeitung der Daten ab. In der Regel liefern Werte zwischen 2.000 und 20.000 die beste Leistung.  
  
 **Prozesskette auslösen**  
 (Optional) Geben Sie den Namen einer Prozesskette an, die ausgelöst wird, nachdem die Daten vollständig geladen wurden.  
  
 **Timeout beim Warten auf InfoPackage**  
 Geben Sie die maximale Anzahl von Sekunden an, die das Ziel wartet, bis das InfoPackage erstellt ist.  
  
 **Warten, bis Datenübertragung abgeschlossen ist**  
 Geben Sie an, ob das Ziel warten soll, bis das SAP NetWeaver BW-System die Daten vollständig geladen hat.  
  
 **InfoPackage nicht starten (nur warten)**  
 Geben Sie an, dass vom Ziel kein InfoPackage ausgelöst, sondern nur auf eine Benachrichtigung gewartet wird, dass das SAP NetWeaver BW-System mit dem Laden der Daten begonnen hat.  
  
## <a name="see-also"></a>Siehe auch  
 [Ziel-Editor für SAP BW &#40; Seite Verbindungs-Manager &#41;](../../integration-services/data-flow/sap-bw-destination-editor-connection-manager-page.md)   
 [Ziel-Editor für SAP BW &#40; Seite "Zuordnungen" &#41;](../../integration-services/data-flow/sap-bw-destination-editor-mappings-page.md)   
 [Ziel-Editor für SAP BW &#40; Seite "Fehlerausgabe" Fehler &#41;](../../integration-services/data-flow/sap-bw-destination-editor-error-output-page.md)   
 [F1-Hilfe zum Microsoft Connector for SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  