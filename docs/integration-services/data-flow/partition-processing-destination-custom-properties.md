---
title: "Benutzerdefinierte Eigenschaften des Ziels für partitionsverarbeitung | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3eac4413-0c90-4b06-8f7e-d0d72f4d869d
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9d3ae46aa1d06fd7d4d5a977d40e3b40a5af4170
ms.contentlocale: de-de
ms.lasthandoff: 08/03/2017

---
# <a name="partition-processing-destination-custom-properties"></a>Benutzerdefinierte Eigenschaften des Ziels für Partitionsverarbeitung
  Das Ziel für Partitionsverarbeitung verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 Die folgende Tabelle beschreibt die benutzerdefinierten Eigenschaften des Ziels für Partitionsverarbeitung. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaft|Datentyp|Description|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|Die Verbindungszeichenfolge zu einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt oder einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|KeyDuplicate|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration **FALSE**ist; ein Wert, der angibt, wie Fehler aufgrund doppelter Schlüssel behandelt werden. Die möglichen Werte sind **IgnoreError** (0), **ReportAndContinue** (1) und **ReportAndStop** (2). Der Standardwert dieser Eigenschaft ist **IgnoreError** (0).|  
|KeyErrorAction|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration **FALSE**ist; ein Wert, der angibt, wie Fehler aufgrund von Schlüsseln behandelt werden sollen. Die möglichen Werte sind **ConvertToUnknown** (0) und **DiscardRecord** (1). Der Standardwert dieser Eigenschaft ist **ConvertToUnknown** (0).|  
|KeyErrorLimit|Integer|Wenn UseDefaultConfiguration **FALSE**ist; die Obergrenze von erlaubten Schlüsselfehlern.|  
|KeyErrorLimitAction|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration **FALSE**ist; ein Wert, der angibt, welche Aktion aufgeführt werden soll, wenn **KeyErrorLimit** erreicht wird. Die möglichen Werte sind **StopLogging** (1) und **StopProcessing** (0). Der Standardwert dieser Eigenschaft ist **StopProcessing** (0).|  
|KeyErrorLogFile|String|Wenn UseDefaultConfiguration **FALSE**ist; der Pfad und Dateiname der Fehlerprotokolldatei.|  
|KeyNotFound|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration **FALSE**ist; ein Wert, der angibt, wie Fehler aufgrund fehlender Schlüssel behandelt werden sollen. Die möglichen Werte sind **IgnoreError** (0), **ReportAndContinue** (1) und **ReportAndStop** (2). Der Standardwert dieser Eigenschaft ist der **ReportAndContinue** (1).|  
|NullKeyConvertedToUnknown|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration **FALSE**ist; ein Wert, der angibt, wie NULL-Schlüssel behandelt werden sollen, die in den unbekannten Wert konvertiert wurden. Die möglichen Werte sind **IgnoreError** (0), **ReportAndContinue** (1) und **ReportAndStop** (2). Der Standardwert dieser Eigenschaft ist **IgnoreError** (0).|  
|NullKeyNotAllowed|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration **FALSE**ist; ein Wert, der angibt, wie nicht erlaubte Nullwerte behandelt werden sollen. Die möglichen Werte sind **IgnoreError** (0), **ReportAndContinue** (1) und **ReportAndStop** (2). Der Standardwert dieser Eigenschaft ist der **ReportAndContinue** (1).|  
|ProcessType|Ganze Zahl (Enumeration)|Der Typ der von der Transformation verwendeten Partitionsverarbeitung. Die möglichen Werte sind **ProcessAdd** (1) (inkrementell), **ProcessFull** (0) und **ProcessUpdate** (2).|  
|UseDefaultConfiguration|Boolean|Ein Wert, der angibt, ob die Transformation die Standardfehlerkonfiguration verwendet. Wenn diese Eigenschaft **FALSE**ist, verwendet die Transformation die Werte der benutzerdefinierten Fehlerbehandlungseigenschaften, die in dieser Tabelle aufgeführt sind, einschließlich KeyDuplicate, KeyErrorAction usw.|  
  
 Die Eingabe und die Eingabespalten des Ziels für Partitionsverarbeitung verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [Partition Processing Destination](../../integration-services/data-flow/partition-processing-destination.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Allgemeine Eigenschaften](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  