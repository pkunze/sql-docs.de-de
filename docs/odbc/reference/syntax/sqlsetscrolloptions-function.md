---
title: SQLSetScrollOptions-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetScrollOptions
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetScrollOptions
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC]
ms.assetid: 2a825ba7-7942-4c23-bcdb-c80dc12f8c86
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a738e4e1206c8df393fe7cfc5562fc72c080ba32
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47709728"
---
# <a name="sqlsetscrolloptions-function"></a>SQLSetScrollOptions-Funktion
**Übereinstimmung mit Standards**  
 Version eingeführt: ODBC-1.0-Standards-Compliance: als veraltet markiert  
  
 **Zusammenfassung**  
 In ODBC 3.*.x*, die ODBC 2.0-Funktion **SQLSetScrollOptions** wurde ersetzt durch Aufrufe von **SQLGetInfo** und **SQLSetStmtAttr**.  
  
> [!NOTE]  
>  Weitere Informationen dazu, was der Treiber-Manager diese Funktion auf, wenn einer ODBC 2. zuordnet *.x* Anwendung arbeitet mit einer ODBC 3.*.x* -Treiber verwenden, finden Sie unter [veraltet Zuordnungsfunktionen](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)in Anhang G: Treiber-Richtlinien für die Abwärtskompatibilität.  
  
> [!NOTE]  
>  Wenn der Treiber-Manager zugeordnet **SQLSetScrollOptions** für eine Anwendung, die Arbeit mit einer ODBC 3.*.x* Treiber, der nicht unterstützt. **SQLSetScrollOptions**, den Treiber Legt Manager die SQL_ROWSET_SIZE setzen Option-Anweisung, nicht das SQL_ATTR_ROW_ARRAY_SIZE-Anweisungsattribut, zu der *RowsetSize* -Argument in **SQLSetScrollOption**. Daher **SQLSetScrollOptions** kann nicht von einer Anwendung verwendet werden, wenn mehrere Zeilen durch einen Aufruf zum Abrufen von **SQLFetch** oder **SQLFetchScroll**. Kann verwendet werden, nur dann, wenn das Abrufen von mehreren durch einen Aufruf von Zeilen **SQLExtendedFetch**.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Ihre Anwendung auf einem 64-Bit-Betriebssystem ausgeführt wird, finden Sie unter [ODBC 64-Bit-Informationen](../../../odbc/reference/odbc-64-bit-information.md).  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
