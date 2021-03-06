---
title: DISCOVER_KEYWORDS-Rowset (XMLA) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4950b157fcf2b64bf6dd634f20a59dc82eb072d9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34037514"
---
# <a name="discoverkeywords-rowset-xmla"></a>DISCOVER_KEYWORDS-Rowset (XMLA)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Gibt Informationen über vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis-Anbieter (XMLA) reservierte Schlüsselwörter zurück.  
  
 Wenn Sie die [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) -Methode mit dem **DISCOVER_KEYWORDS** -Enumerationswert im [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) -Element aufrufen, gibt die **Discover** -Methode das **DISCOVER_KEYWORDS** -Rowset zurück.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Das **DISCOVER_KEYWORDS** -Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|**Schlüsselwort**|**DBTYPE_WSTR**||Eine Liste aller von einem Anbieter reservierten Schlüsselwörter.<br /><br /> Beispiel: **AND**|  
  
 Dieses Schemarowset ist nicht sortiert.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Das **DISCOVER_KEYWORDS** -Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|**Schlüsselwort**|**DBTYPE_WSTR**|Optional.|  
  
## <a name="see-also"></a>Siehe auch  
 [XML for Analysis-Schemarowsets](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)   
 [DISCOVER_LITERALS-Rowset](../../../analysis-services/schema-rowsets/xml/discover-literals-rowset.md)  
  
  
