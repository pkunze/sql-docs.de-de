---
title: Ändern der Eigenschaften einer Miningstruktur | Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8064fcc088c7ae9e7dd96c5c132b1246fe0ae2db
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34014047"
---
# <a name="change-the-properties-of-a-mining-structure"></a>Ändern der Eigenschaften einer Miningstruktur
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Es gibt zwei Arten von Eigenschaften in einer Miningstruktur, die jeweils geändert werden können:  
  
-   Eigenschaften der Miningstruktur, die die gesamte Struktur betreffen.  
  
-   Eigenschaften in einzelnen Spalten in der Struktur  
  
 Einige Eigenschaften sind von anderen Eigenschafteneinstellungen abhängig. Sie können beispielsweise keine Eigenschaften festlegen, die das Diskretisierungsverhalten steuern (wie <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> oder <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>), solange Sie den Datentyp der Spalte auf **Diskretisiert**festgelegt haben.  
  
 Weitere Informationen zu Miningstruktureigenschaften finden Sie unter [Miningstrukturspalten](../../analysis-services/data-mining/mining-structure-columns.md).  
  
### <a name="to-change-the-properties-of-a-mining-structure"></a>So ändern Sie die Eigenschaften einer Miningstruktur  
  
1.  Klicken Sie auf der Registerkarte **Miningstruktur** im Data Mining-Designer mit der rechten Maustaste entweder auf die Miningstruktur oder auf eine Spalte innerhalb der Miningstruktur, und klicken Sie anschließend auf **Eigenschaften**.  
  
     Im rechten Bildschirmbereich wird das **Eigenschaften** -Fenster geöffnet, wenn es nicht bereits sichtbar war.  
  
2.  Wählen Sie im **Eigenschaften** -Fenster den Wert aus, der der Eigenschaft entspricht, die Sie ändern möchten, und geben Sie dann den neuen Wert ein.  
  
     Der neue Wert wird wirksam, wenn Sie ein anderes Element im Designer auswählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks und Anweisungen für Miningstrukturen](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
