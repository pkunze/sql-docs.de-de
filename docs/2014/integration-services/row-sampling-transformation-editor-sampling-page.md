---
title: Row Sampling Transformation Editor (Seite Stichprobenentnahme) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.ROWSAMPLINGTRANSFORMATION.COLUMNS.F1
- sql12.dts.designer.rowsamplingtransformation.f1
helpviewer_keywords:
- Row Sampling Transformation Editor
ms.assetid: 544c7709-6de0-4c08-bda3-759985be9a05
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cc815dd914df7f7bb3c3fa1e65b274143ddc4741
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48069980"
---
# <a name="row-sampling-transformation-editor-sampling-page"></a>Transformations-Editor für Zeilenstichprobe (Seite Stichprobenentnahme)
  Im Dialogfeld **Transformations-Editor für Zeilenstichprobe** können Sie einen Teil der Eingabe mithilfe der angegebenen Anzahl von Zeilen als Stichprobe entnehmen. Durch diese Transformation wird die Eingabe in zwei getrennte Ausgaben geteilt.  
  
 Weitere Informationen zur Transformation für Zeilenstichproben finden Sie unter [Row Sampling Transformation](data-flow/transformations/row-sampling-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Anzahl von Zeilen**  
 Geben Sie die Anzahl der Zeilen in der Eingabe an, die als Stichprobe verwendet werden sollen.  
  
 Der Wert dieser Eigenschaft kann mithilfe eines Eigenschaftsausdrucks angegeben werden.  
  
 **Ausgabename für Stichprobendaten**  
 Geben Sie einen eindeutigen Namen für die Ausgabe an, die die als Stichprobe entnommenen Zeilen enthalten wird. Der angegebene Name wird im SSIS-Designer angezeigt.  
  
 **Ausgabename für nicht ausgewählte Daten**  
 Geben Sie einen eindeutigen Namen für die Ausgabe an, die die Zeilen enthalten wird, die nicht zur Stichprobe gehören. Der angegebene Name wird im SSIS-Designer angezeigt.  
  
 **Folgenden zufälligen Ausgangswert verwenden**  
 Geben Sie den Ausgangswert für den Zufallszahlen-Generator an, der von der Transformation zum Erstellen der Stichprobe verwendet wird. Dies wird ausschließlich für Entwicklung und Tests empfohlen. Wenn kein zufälliger Ausgangswert angegeben wird, wird von der Transformation die Taktanzahl aus Microsoft Windows als Ausgangswert verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Transformation für Prozentwert-Stichproben](data-flow/transformations/percentage-sampling-transformation.md)  
  
  
