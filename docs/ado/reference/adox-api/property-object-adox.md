---
title: Property-Objekt (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Property object [ADOX]
ms.assetid: 6a56def6-dbe6-4ccc-a491-8d076889f019
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2502dcdab170102f526aa1ea0fe67235e6bf3048
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47815598"
---
# <a name="property-object-adox"></a>Property-Objekt (ADOX)
Stellt ein Merkmal eines ADOX-Objekts dar.  
  
## <a name="remarks"></a>Hinweise  
 ADO-Objekte umfassen zwei Typen von Eigenschaften: integrierte und dynamische.  
  
 Integrierte Eigenschaften sind diese Eigenschaften, die für jedes neue Objekt, mit der Syntax MyObject.Property sofort verfügbar. Sie erscheinen nicht als Eigenschaft eines Objekts Objekte [Properties-Auflistung](../../../ado/reference/ado-api/properties-collection-ado.md), sodass Sie ihre Werte können jedoch ändern, können Sie ihre Merkmale nicht ändern.  
  
 Dynamische Eigenschaften werden von den zugrunde liegenden Datenanbieter definiert und in die eigenschaftenauflistung für das entsprechende ADOX-Objekt angezeigt werden.  Dynamische Eigenschaften können nur über die Auflistung, die mit der Syntax MyObject.Properties(0) oder MyObject.Properties("Name") verwiesen werden.  
  
 Beide Arten der Eigenschaft kann nicht gelöscht werden.  
  
 Ein dynamisches Objekt verfügt über vier integrierte eigenen Eigenschaften:  
  
 Die [Namen](../../../ado/reference/ado-api/name-property-ado.md) Eigenschaft ist eine Zeichenfolge, die die Eigenschaft identifiziert.  
  
 Die [Typ](../../../ado/reference/ado-api/type-property-ado.md) -Eigenschaft ist eine ganze Zahl, die den Datentyp der Eigenschaft angibt.  
  
 Die [Wert](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft ist eine Variante, die die Einstellung der Eigenschaft enthält. Wert ist die Standardeigenschaft für ein Objekt.  
  
 Die [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) -Eigenschaft ist ein long-Wert, der Merkmale der Eigenschaft für den Anbieter spezifisch angibt.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [ADOX-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/adox-property-object-properties-methods-and-events.md)
