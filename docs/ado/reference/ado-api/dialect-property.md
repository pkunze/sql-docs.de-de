---
title: Dialect-Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Command::Dialect
helpviewer_keywords:
- Dialect property
ms.assetid: 329c3a71-ba88-4009-b04f-2f52195a5957
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ef18eb3d6251bc07ae25ef8cbc3445a87b8390b4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810518"
---
# <a name="dialect-property"></a>Dialect-Eigenschaft
Gibt den Dialekt des der [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) oder [' CommandStream '](../../../ado/reference/ado-api/commandstream-property-ado.md) Eigenschaften. Der Dialekt definiert die Syntax und die allgemeinen Regeln, die der Anbieter verwendet, um die Zeichenfolge oder den Stream zu analysieren.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Die **Dialekt** Eigenschaft enthält eine gültige GUID an, der Dialekt, der die Befehlstext oder den Stream darstellt. Der Standardwert für diese Eigenschaft ist {C8B521FB-5CF3-11CE-ADE5-00AA0044773D}, was bedeutet, dass der Anbieter die Befehlstext oder den Stream zu interpretieren auswählen sollten.  
  
## <a name="remarks"></a>Hinweise  
 ADO fragt nicht den Anbieter, wenn der Benutzer den Wert dieser Eigenschaft liest; Es gibt eine Zeichenfolgendarstellung des Werts, der derzeit im gespeicherten der [Befehl](../../../ado/reference/ado-api/command-object-ado.md) Objekt.  
  
 Wenn der Benutzer legt die **Dialekt** ADO-Eigenschaft überprüft die GUID, und ein Fehler ausgelöst, wenn der angegebene Wert nicht über eine gültige GUID ist. Finden Sie in der Dokumentation für Ihren Anbieter, um zu bestimmen, die GUID-Werte, die von unterstützt die **Dialekt** Eigenschaft.  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Execute-Methode (ADO Command)](../../../ado/reference/ado-api/execute-method-ado-command.md)
