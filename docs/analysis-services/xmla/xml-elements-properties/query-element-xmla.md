---
title: Abfrage-Element (XMLA) | Microsoft-Dokumentation
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 861f216ac263de32b9f2afc3e0fcd4e43b3dfb4a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37984641"
---
# <a name="query-element-xmla"></a>Query-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält eine Abfrage innerhalb der [Abfragen](../../../analysis-services/xmla/xml-elements-properties/queries-element-xmla.md) Auflistung für die [DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md) -Befehl während verwendungsbasierter Optimierung.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Queries>  
   ...  
   <Query>...</Query>  
   ...  
</Queries>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Abfragen](../../../analysis-services/xmla/xml-elements-properties/queries-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der **DesignAggregations** -Befehl unterstützt verwendungsbasierte Optimierung durch die Einbindung ein oder mehrerer **Query** -Elemente in die **Queries** -Auflistung des Befehls. Jedes **Query** -Element stellt eine Zielabfrage dar, die der Entwurfsprozess nutzt, um Aggregationen zu definieren, die auf die am häufigsten verwendeten Abfragen abzielen. Sie können entweder Ihre eigenen zielabfragen festlegen, oder Sie können die von einer Instanz von Analysis Services im Abfrageprotokoll gespeicherte Informationen zum Abrufen von Informationen zu den am häufigsten verwendeten Abfragen.  
  
 Wenn Sie Aggregationen iterativ entwerfen, nur müssen Sie zielabfragen im ersten übergeben **DesignAggregations** Befehl, weil die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Instanz diese zielabfragen speichert und verwendet Sie diese Abfragen während der nachfolgenden  **DesignAggregations** Befehle. Nachdem Sie Zielabfragen im ersten **DesignAggregations** -Befehl eines iterativen Prozesses weitergegeben haben, generiert jeder darauf folgende **DesignAggregations** -Befehl, der über Zielabfragen in der **Queries** -Eigenschaft verfügt, einen Fehler.  
  
 Das **Query** -Element enthält einen durch Trennzeichen getrennten Wert, der die folgenden Argumente beinhaltet:  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *Häufigkeit*  
 Ein Gewichtungsfaktor, der der Anzahl der Male entspricht, die eine Abfrage zuvor ausgeführt wurde. Wenn das **Query** -Element eine neue Abfrage darstellt, gibt der *Frequency* -Wert den Gewichtungsfaktor an, der vom Entwurfsprozess für die Evaluierung der Abfrage verwendet wird. Bei steigendem Häufigkeitswert, steigt die Gewichtung auf die Abfrage während des Entwurfsprozesses.  
  
 *DataSet*  
 Eine numerische Zeichenfolge, die festlegt, welche Attribute einer Dimension in die Abfrage eingebunden werden. Diese Zeichenfolge muss die gleiche Anzahl an Zeichen wie die Anzahl an Attributen in der Dimension haben. null (0) zeigt an, dass das Attribut an der angegebenen Ordnungsposition für die angegebene Dimension nicht in der Abfrage enthalten ist. Eins (1) zeigt an, dass das Attribut an der angegebenen Ordnungsposition für die angegebene Dimension in der Abfrage enthalten ist.  
  
 Beispielsweise bezieht sich die Zeichenfolge "011" auf eine Abfrage mit einer Dimension mit drei Attributen, von denen das zweite und dritte Attribut in der Abfrage enthalten sind.  
  
> [!NOTE]  
>  Einige Attribute sind von der Berücksichtigung im Dataset ausgenommen. Weitere Informationen über ausgenommene Attribute finden Sie unter [Eigenschaften (XMLA)](../../../analysis-services/xmla/xml-elements-properties/query-element-xmla.md).  
  
 Jede Dimension in der Measuregruppe, die einen Aggregationsentwurf enthält, wird durch einen *Dataset* -Wert im **Query** -Element dargestellt. Die Reihenfolge der *Dataset* -Werte muss der Reihenfolge der Dimensionen entsprechen, die in die Measuregruppe eingebunden sind.  
  
## <a name="see-also"></a>Siehe auch
 [Entwerfen von Aggregationen &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/designing-aggregations-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
