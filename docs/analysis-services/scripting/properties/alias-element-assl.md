---
title: Alias-Element (ASSL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Alias Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Alias
helpviewer_keywords:
- Alias element
ms.assetid: 674fdb06-e33c-4f35-bd6a-d9bbb13ececa
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 114a3c8a022ef55a221e2c6474f3f34ce9733f0e
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="alias-element-assl"></a>Alias-Element (ASSL)
  Definiert einen Alias für eine [Konto](../../../analysis-services/scripting/objects/account-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Aliases>  
      <Alias>...</Alias>  
</Aliases>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|String|  
|Standardwert|Keine|  
|Kardinalität|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Aliase](../../../analysis-services/scripting/collections/aliases-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert des **Alias** -Elements wird als alternativer Name für das Konto verwendet, das vom übergeordneten **Account** -Element definiert wird, und hilft bei der Identifizierung des Kontotyps und der Aggregatfunktion bei einer Benutzeroberfläche.  
  
 Das Element, das das übergeordnete Element des entspricht, der **Aliase** Auflistung im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  