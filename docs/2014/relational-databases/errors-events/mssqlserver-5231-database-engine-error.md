---
title: MSSQLSERVER_5231 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5231 (Database Engine error)
ms.assetid: 6954ae84-ed0b-4f4c-9d0a-e73f3d71476c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6c57150dd8fac6dab1c2c9cf6fdf7cefbdb1b5f8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048491"
---
# <a name="mssqlserver5231"></a>MSSQLSERVER_5231
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|5231|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC4_DEADLOCK_SKIPPED_OBJECT|  
|Meldungstext|Objekt-ID O_ID (Objekt 'NAME'): Deadlock beim Versuch, dieses Objekt für die Überprüfung zu sperren. Das Objekt wurde ausgelassen und wird nicht verarbeitet.|  
  
## <a name="explanation"></a>Erklärung  
 Es kam zu einem Deadlock, als von DBCC versucht wurde, das Objekt zu sperren. DBCC wurde als Deadlockopfer ausgewählt. Das Objekt wird nicht verarbeitet.  
  
## <a name="user-action"></a>Benutzeraktion  
 None  
  
  
