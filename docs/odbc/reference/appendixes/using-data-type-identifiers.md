---
title: -Datentypbezeichner mit | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], identifiers
- identifiers [ODBC], data types
ms.assetid: 467e0c0c-a818-4737-8a24-3d8e15c7e162
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9f29b6e27866b5893c6875ee5c438d7c13a996e9
ms.contentlocale: de-de
ms.lasthandoff: 09/09/2017

---
# <a name="using-data-type-identifiers"></a>Mithilfe von-Datentypbezeichner
Anwendungen-Datentypbezeichner auf zwei Arten verwenden: ihre Puffer an den Treiber zu beschreiben und zum Abrufen von Metadaten über das Resultset aus dem Treiber, damit sie feststellen können, welche Art von C puffert, um zum Speichern der Daten zu verwenden. Anwendungen rufen Sie die folgenden Funktionen zum Durchführen dieser Aufgaben:  
  
-   **SQLBindParameter**, **SQLBindCol**, und **SQLGetData** – C-Datentyp der Anwendungspuffer beschreiben.  
  
-   **SQLBindParameter** – um die SQL-Datentyp von dynamischen Parametern zu beschreiben.  
  
-   **SQLColAttribute** und **SQLDescribeCol** – um die SQL-Datentypen der Spalten im Resultset abzurufen.  
  
-   **SQLDescribeParameter** – die SQL-Datentypen von Parametern abgerufen.  
  
-   **SQLColumns**, **SQLProcedureColumns**, und **SQLSpecialColumns** – die SQL-Datentypen von verschiedenen Schemainformationen abrufen  
  
-   **SQLGetTypeInfo** – zum Abrufen einer Liste der unterstützten Datentypen  
  
 -Datentypbezeichner werden in das Feld SQL_DESC_CONCISE_TYPE einen Deskriptor gespeichert. Der Deskriptor Funktionen **SQLSetDescField** und **SQLSetDescRec** können mit den entsprechenden Typen verwendet werden, um in der vorherigen Liste aufgeführten Aufgaben ausführen. Weitere Informationen finden Sie unter [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).