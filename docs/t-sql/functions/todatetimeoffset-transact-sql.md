---
title: TODATETIMEOFFSET (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TO_DATETIMEOFFSET_TSQL
- SWITCH_TZ_TSQL
- SWITCH_TZ
- TO_DATETIMEOFFSET
dev_langs:
- TSQL
helpviewer_keywords:
- date and time [SQL Server], TODATETIMEOFFSET
- TODATETIMEOFFSET function
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
ms.assetid: b5fafc08-efd4-4a3b-a0b3-068981a0a685
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 77d42b2484563d162d78e1caad28389cc26f6cee
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="todatetimeoffset-transact-sql"></a>TODATETIMEOFFSET (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine **"DateTimeOffset"** -Wert, der aus übersetzt werden eine **datetime2** Ausdruck.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
TODATETIMEOFFSET ( expression , time_zone )  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Ist ein [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) , die aufgelöst wird, um eine [datetime2](../../t-sql/data-types/datetime2-transact-sql.md) Wert.  
  
> [!NOTE]  
>  Der Ausdruck kann nicht vom Typ **Text**, **Ntext**, oder **Image** , da diese Typen implizit konvertiert werden können **Varchar** oder **Nvarchar**.  
  
 *time_zone*  
 Ein Ausdruck, der den Zeitzonenoffset in Minuten (bei einer ganzen Zahl), z. B. -120, oder in Stunden und Minuten (bei einer Zeichenfolge), z. B. '+13.00' darstellt. Der Bereich liegt zwischen +14 und -14 (in Stunden). Der Ausdruck wird in Ortszeit für die angegebene time_zone interpretiert.  
  
> [!NOTE]  
>  Wenn der Ausdruck eine Zeichenfolge ist, muss er folgendes Format aufweisen: {+ | -} TZH:THM.  
  
## <a name="return-type"></a>Rückgabetyp  
 **"DateTimeOffset"**. Die Genauigkeit von Bruchteile ist identisch mit der *"DateTime"* Argument.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-changing-the-time-zone-offset-of-the-current-date-and-time"></a>A. Ändern des Zeitzonenoffsets für das aktuelle Datum und die aktuelle Uhrzeit  
 Im folgenden Beispiel ändert sich der Zeitzonenoffset des aktuellen Datums und der aktuellen Uhrzeit zur Zeitzone `-07:00`.  
  
```  
DECLARE @todaysDateTime datetime2;  
SET @todaysDateTime = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDateTime, '-07:00');  
-- RETURNS 2007-08-30 15:51:34.7030000 -07:00  
```  
  
### <a name="b-changing-the-time-zone-offset-in-minutes"></a>B. Ändern des Zeitzonenoffsets zu Minuten  
 Im folgenden Beispiel ändert sich die aktuelle Zeitzone zu `-120` Minuten.  
  
```  
DECLARE @todaysDate datetime2;  
SET @todaysDate = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDate, -120);  
-- RETURNS 2007-08-30 15:52:37.8770000 -02:00  
```  
  
### <a name="c-adding-a-13-hour-time-zone-offset"></a>C. Hinzufügen eines 13-Stunden-Zeitzonenoffsets  
 Im folgenden Beispiel wird ein 13-Stunden-Zeitzonenoffset einem Datum und einer Uhrzeit hinzugefügt.  
  
```  
DECLARE @dateTime datetimeoffset(7)= '2007-08-28 18:00:30';  
SELECT TODATETIMEOFFSET (@dateTime, '+13:00');  
-- RETURNS 2007-08-28 18:00:30.0000000 +13:00  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-changing-the-time-zone-offset-of-the-current-date-and-time"></a>D. Ändern des Zeitzonenoffsets für das aktuelle Datum und die aktuelle Uhrzeit  
 Im folgenden Beispiel ändert sich der Zeitzonenoffset des aktuellen Datums und der aktuellen Uhrzeit zur Zeitzone `-07:00`.  
  
```  
DECLARE @todaysDateTime datetime2;  
SET @todaysDateTime = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDateTime, '-07:00');  
-- RETURNS 2007-08-30 15:51:34.7030000 -07:00  
```  
  
### <a name="e-changing-the-time-zone-offset-in-minutes"></a>E. Ändern des Zeitzonenoffsets zu Minuten  
 Im folgenden Beispiel ändert sich die aktuelle Zeitzone zu `-120` Minuten.  
  
```  
DECLARE @todaysDate datetime2;  
SET @todaysDate = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDate, -120);  
-- RETURNS 2007-08-30 15:52:37.8770000 -02:00  
```  
  
### <a name="f-adding-a-13-hour-time-zone-offset"></a>F. Hinzufügen eines 13-Stunden-Zeitzonenoffsets  
 Im folgenden Beispiel wird ein 13-Stunden-Zeitzonenoffset einem Datum und einer Uhrzeit hinzugefügt.  
  
```  
DECLARE @dateTime datetimeoffset(7)= '2007-08-28 18:00:30';  
SELECT TODATETIMEOFFSET (@dateTime, '+13:00');  
-- RETURNS 2007-08-28 18:00:30.0000000 +13:00  
```  
  
## <a name="see-also"></a>Siehe auch  
 [CAST und CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Datums- und Zeitdaten Typen und-Funktionen &#40; Transact-SQL &#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [ZEITZONE &AMP; #40; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)  
  
  

