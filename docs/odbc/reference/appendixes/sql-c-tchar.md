---
title: SQL_C_TCHAR | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- sql_c_tchar [ODBC]
- pseudo-type identifiers [ODBC], SQL_C_TCHAR
- data types [ODBC], pseudo-type identifiers
ms.assetid: 9e27c8bd-ee15-4ce9-b70a-34cf1bf16f4c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 42afb911dda26cbda53f9cd14c883abb3775b94b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792344"
---
# <a name="sqlctchar"></a>SQL_C_TCHAR
Der Typbezeichner SQL_C_TCHAR identifiziert nicht tatsächlich einen Datentyp; Es ist ein Makro, das in der Headerdatei für die Unicode-Konvertierung vorhanden ist. Sie wird von SQL_C_CHAR oder SQL_C_WCHAR ersetzt, abhängig von der Einstellung des Unicode- **#define**. Es empfiehlt sich für eine Anwendung, Übertragen von Zeichendaten, die als eine ANSI- und Unicode-Anwendung kompiliert werden.
