---
title: StorageBoundInMB-Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- StorageBoundInMB element
ms.assetid: a8374910-bf68-4edb-b464-53a3a705e7f4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e5e6cf3c0be2ec3ab8587bd086c99b32e718cd78
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48069449"
---
# <a name="storageboundinmb-element-dta"></a>StorageBoundInMB-Element (DTA)
  Gibt die maximale Größe des Speicherplatzes in Megabyte an, der von der Optimierungsempfehlung des Datenbankoptimierungsratgebers (Index und Partitionierung) beansprucht werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <StorageBoundInMB>...</ StorageBoundInMB >  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|**Datentyp und -länge**|`unsignedInt`, unbegrenzte Länge.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Optional. Kann nur einmalig für das `TuningOptions`-Element verwendet werden.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[TuningOptions-Element &#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**Untergeordnete Elemente**|None|  
  
## <a name="remarks"></a>Hinweise  
 Wenn mehrere Datenbanken optimiert werden, werden bei der Berechnung des Speicherplatzes Empfehlungen für alle Datenbanken berücksichtigt. Standardmäßig nimmt der Datenbankoptimierungsratgeber die kleinere der folgenden Speichergrößen an:  
  
-   Das Dreifache der aktuellen Rohdatengröße, einschließlich der Gesamtgröße von Heaps und gruppierten Indizes für Tabellen.  
  
-   Der freie Speicherplatz auf allen angefügten Laufwerken plus die Rohdatengröße.  
  
 Nicht im Standardspeicherplatz enthalten sind nicht gruppierte Indizes und indizierte Sichten.  
  
 Wenn der angegebene Wert für die `StorageBoundInMB` Element den tatsächlichen Speicherplatz überschreitet, gibt der Datenbankoptimierungsratgeber einen Fehler, sondern setzt die Optimierung fort. Nach der Optimierung können Sie Speicherplatz hinzufügen, wenn Sie die Empfehlung implementieren möchten.  
  
## <a name="example"></a>Beispiel  
  
## <a name="description"></a>Description  
 Im folgenden Codebeispiel wird veranschaulicht, wie 1500 Megabytes als maximaler Speicherplatz festgelegt werden, der von einer Empfehlung zur Optimierung belegt werden kann:  
  
## <a name="code"></a>Code  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <StorageBoundInMB>1500</StorageBoundInMB>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Eingabedateireferenz &amp;#40;Datenbankoptimierungsratgeber&amp;#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
