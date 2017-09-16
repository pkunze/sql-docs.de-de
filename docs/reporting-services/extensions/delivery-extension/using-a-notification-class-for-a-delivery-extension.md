---
title: "Verwenden einer Notification-Klasse für eine Übermittlungserweiterung | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- delivery extensions [Reporting Services], notifications
- notifications [Reporting Services]
- retry queues
- Nofication class
ms.assetid: 549c40c4-d33d-46c2-9d6a-7bbb671ac67a
caps.latest.revision: 33
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 064d5556dca130324f69dd49d14f3caa76c8eec8
ms.contentlocale: de-de
ms.lasthandoff: 08/12/2017

---
# <a name="using-a-notification-class-for-a-delivery-extension"></a>Verwenden einer Notification-Klasse für eine Übermittlungserweiterung
  Die <xref:Microsoft.ReportingServices.Interfaces.Notification>-Klasse befindet sich im <xref:Microsoft.ReportingServices.Interfaces>-Namespace und stellt Abonnementdaten dar, die die Übermittlungserweiterungen für die Übermittlung von Berichten verwenden. Die <xref:Microsoft.ReportingServices.Interfaces.Notification>-Klasse verfügt über mehrere Eigenschaften, die verwendet werden können, um die Berichte für die Übermittlung zu rendern, den Status der Benachrichtigung zu bestimmen und die Benutzerdaten festzulegen.  
  
 ![Bericht Benachrichtigungsverfahren](../../../reporting-services/extensions/delivery-extension/media/bk-ext-03.gif "Benachrichtigungsverfahren melden")  
Die Benachrichtigung ist das zentrale Objekt einer jeden Übermittlung  
  
 Wenn ein Ereignis eintritt, das zu einem Abonnement gehört, das Ihre benutzerdefinierte Übermittlungserweiterung verwendet, wird eine Benachrichtigung mit einem <xref:Microsoft.ReportingServices.Interfaces.Report>-Objekt erstellt. Das <xref:Microsoft.ReportingServices.Interfaces.Report>-Objekt umfasst Funktionen, die benötigt werden, um einen bestimmten Bericht in einem unterstützten Renderingformat zu rendern, und enthält berichtsspezifische Eigenschaften, wie die URL zum Bericht auf dem Server und den Namen des Berichts. Weitere Informationen zu den <xref:Microsoft.ReportingServices.Interfaces.Report> Klasse, finden Sie unter [mithilfe der Berichts-Klasse für eine Übermittlungserweiterung](../../../reporting-services/extensions/delivery-extension/using-the-report-class-for-a-delivery-extension.md).  
  
 Sie übergeben das <xref:Microsoft.ReportingServices.Interfaces.Notification>-Objekt an die <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A>-Methode Ihrer Übermittlungserweiterung. Die <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A>-Methode sollte speziellen Code zur Verarbeitung der Benachrichtigung und zur Übermittlung des Berichts enthalten.  
  
 Ein Beispiel zum Verwenden der <xref:Microsoft.ReportingServices.Interfaces.Notification> Klasse, finden Sie unter [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="retry-functionality"></a>Funktion zum Wiederholen  
 Mit [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] können Sie für Benachrichtigungen, die nicht sofort übermittelt werden können, eine Wiederholungswarteschlange erstellen. Nachdem der Berichtsserver die <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A>-Methode einer Übermittlungserweiterung aufruft, kann die Übermittlungserweiterung anfordern, dass der Berichtsserver die Übermittlung zu einem späteren Zeitpunkt wiederholt. In diesem Fall stellt der Berichtsserver die Benachrichtigung in eine interne Warteschlange und wiederholt die Übermittlung nach einem bestimmten Zeitraum. Administratoren können die maximale Anzahl von Wiederholungsversuchen an, der der Berichtsserver ausführt und den Zeitraum zwischen zwei Wiederholungen einlegen, in der Übermittlung-Abschnitt der Datei "rsreportserver.config" mit Konfigurieren der **MaxNumberOfRetries** XML-Element und die **PeriodBetweenRetries** XML-Element. Benachrichtigungen werden aus der Wiederholungswarteschlange entfernt, wenn die Übermittlung später erfolgreich oder die maximale Anzahl an Wiederholungsversuchen erreicht ist. Wenn die Übermittlung nach der maximalen Anzahl von Wiederholungen fehlschlägt, wird die Benachrichtigung entfernt.  
  
## <a name="see-also"></a>Siehe auch  
 [Implementing a Delivery Extension](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services-Erweiterungsbibliothek](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  