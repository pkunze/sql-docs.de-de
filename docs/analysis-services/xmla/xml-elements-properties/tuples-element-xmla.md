---
title: Tuples-Element (XMLA) | Microsoft-Dokumentation
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c0578c541c39bdaceede6bff8afdea3d642abcef
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38062544"
---
# <a name="tuples-element-xmla"></a>Tuples-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält eine Reihe von [Tupel](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md) von Objekten für die ein [Achse](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md) -Element, das verwendet die [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) von zurückgegebener Datentyp die [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Axis>  
   ...  
   <Tuples>  
      <Tuple>...</Tuple>  
   </Tuples>  
   ...  
</Axis>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Axis](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
|Untergeordnete Elemente|[Tupel](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Clientanwendung die **AxisFormat**-Eigenschaft auf *TupleFormat* festlegt, wird eine Achse als Menge von Tupeln dargestellt. Jedes **Axis**-Element enthält ein **Tuples**-Element, das die Menge von Tupeln auf dieser Achse darstellt. Jedes Tupel wird mithilfe eines **Tuple**-Elements dargestellt, das [Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)-Elemente aus jeder Hierarchie auf der Achse enthält.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Struktur der **Tupel** -Element, wenn ein Client angibt, *TupleFormat* oder *CustomFormat* für die **AxisFormat**  XML for Analysis (XMLA)-Eigenschaft, wobei die folgenden Elemente für die Achse:  
  
|||||  
|-|-|-|-|  
|**Time**-Hierarchie|1999|1999|2000|  
|**Category**-Hierarchie|Tatsächlich|Budget|Budget|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <Tuples>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
      </Tuples>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>Siehe auch
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
