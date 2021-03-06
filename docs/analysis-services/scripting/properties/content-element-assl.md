---
title: Content-Element (ASSL) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ee3c1babd828463e8654280c421d616535aca88e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34036461"
---
# <a name="content-element-assl"></a>Content-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Beschreibt den Inhalt der Spalte in der [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ScalarMiningStructureColumn>  
   ...  
   <Content>...</Content>  
   ...  
</ScalarMiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|Keine|  
|Kardinalität|1-1: Erforderliches Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Diese Enumeration beschreibt den Inhaltstyp, der von einer Miningstrukturspalte dargestellt wird, und kann je nach Bedarf durch Mining-Algorithmusanbieter erweitert werden. Weitere Informationen zu Inhaltstypen finden Sie unter [Inhaltstypen &#40;Data Mining&#41;](../../../analysis-services/data-mining/content-types-data-mining.md).  
  
 Die in der folgenden Tabelle aufgelisteten Werte werden i. d. R. von allen Mining-Algorithmusanbietern unterstützt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*Diskrete*|Diese Spalte enthält diskrete Werte.|  
|*Fortlaufende*|Die Werte für die Spalte definieren einen fortlaufenden Satz von numerischen Daten.|  
|*Diskretisiert*|Die Werte in der Spalte stellen Gruppen (oder Buckets) von Werten dar, die von einer kontinuierlichen Spalte abgeleitet sind.|  
|*sortiert*|Die Werte für die Spalte definieren eine geordnete Menge.|  
|*Zyklisch*|Die Werte für die Spalte definieren eine zyklisch geordnete Menge.|  
|*Wahrscheinlichkeit*|Die Werte für die Spalte geben eine Wahrscheinlichkeit für die Spalten in der [ClassifiedColumns](../../../analysis-services/scripting/collections/classifiedcolumns-element-assl.md) Element des übergeordneten Elements **ScalarMiningStructureColumn**.|  
|*Variance*|Die Werte für die Spalte geben eine Varianz für die Spalten in der **ClassifiedColumns** Element des übergeordneten Elements **ScalarMiningStructureColumn**.|  
|*StdDev*|Die Werte für die Spalte geben eine Standardabweichung für die Spalten in der **ClassifiedColumns** Element des übergeordneten Elements **ScalarMiningStructureColumn**.|  
|*ProbabilityVariance*|Die Werte für die Spalte geben eine Varianz der Wahrscheinlichkeit für die Spalten in der **ClassifiedColumns** Element des übergeordneten Elements **ScalarMiningStructureColumn**.|  
|*ProbabilityStdDev*|Die Werte für die Spalte geben eine Standardabweichung der Wahrscheinlichkeit für die Spalten in der **ClassifiedColumns** Element des übergeordneten Elements **ScalarMiningStructureColumn**.|  
|*Unterstützung*|Die Werte für die Spalte geben Supportinformationen für die Spalte in der **ClassifiedColumns** Element des übergeordneten Elements **ScalarMiningStructureColumn**.<br /><br /> Hinweis: Diese Spalte wird als Teil des Standards für Mining-Algorithmusanbietern von Drittanbietern bereitgestellt. Von Microsoft bereitgestellte Algorithmen nehmen Sie keine dieser Spalte verwenden.|  
|*Key*|Die Spalte ist eine Schlüsselspalte.<br /><br /> Hinweis: Dieser Inhaltstyp gilt nur für Schlüsselspalten in dem die **IsKey** -Elementgruppe ist **"true"**.|  
  
 Zusätzlich zu diesen Standardwerten mining-Algorithmusanbietern enthaltene [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] unterstützen die Werte in der folgenden Tabelle.  
  
|Wert|Description|  
|-----------|-----------------|  
|*Tastenkombination*|Diese Spalte ist eine Schlüsselspalte, und die Werte für diese Spalte stellen eine Folge von Ereignissen dar.<br /><br /> Hinweis: Dieser Inhaltstyp gilt nur für Schlüsselspalten in dem die **IsKey** -Elementgruppe ist **"true"**.|  
|*Die Schlüsselzeit*|Diese Spalte ist eine Schlüsselspalte, und die Werte für diese Spalte stellen Zeitmaßeinheiten dar.<br /><br /> Hinweis: Dieser Inhaltstyp gilt nur für Schlüsselspalten in dem die **IsKey** -Elementgruppe ist **"true"**.|  
|*Sequenz*|Die Werte für diese Spalte stellen eine Folge von Ereignissen dar.|  
|*Zeit*|Die Werte für die Spalte stellen Zeitmaßeinheiten dar.|  
  
 Die Enumeration, die den zulässigen Werten für die entsprechende **Content** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Siehe auch  
 [ClassifiedColumns-Element &#40;ASSL&#41;](../../../analysis-services/scripting/collections/classifiedcolumns-element-assl.md)   
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
