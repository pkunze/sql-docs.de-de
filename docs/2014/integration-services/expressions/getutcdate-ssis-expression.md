---
title: GETUTCDATE (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], GETUTCDATE
- current date
- UTC time
- GETUTCDATE function
ms.assetid: 2282339c-c24f-493e-8e66-181ea8af5ad0
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d266d5c329776279f21dfbfdaa51a823f460a407
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087100"
---
# <a name="getutcdate-ssis-expression"></a>GETUTCDATE (SSIS-Ausdruck)
  Gibt das aktuelle Datum des Systems als UTC-Zeit (Universal Time Coordinate oder Greenwich Mean Time) in einem DT_DBTIMESTAMP-Format zurück. Die GETUTCDATE-Funktion weist keine Argumente auf.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
GETUTCDATE()  
```  
  
## <a name="arguments"></a>Argumente  
 None  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird das Jahr des aktuellen Datums als UTC-Zeit zurückgegeben.  
  
```  
DATEPART("year",GETUTCDATE())  
```  
  
 In diesem Beispiel wird die Anzahl von Tagen zwischen einem Datum in der **ModifiedDate** -Spalte und dem aktuellen UTC-Datum zurückgegeben.  
  
```  
DATEDIFF("dd",ModifiedDate,GETUTCDATE())  
```  
  
 In diesem Beispiel werden dem aktuellen UTC-Datum drei Monate hinzugefügt.  
  
```  
DATEADD("Month",3,GETUTCDATE())  
```  
  
## <a name="see-also"></a>Siehe auch  
 [GETDATE &#40;SSIS-Ausdruck&#41;](getdate-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
