---
title: Deterministische und nicht deterministische Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- built-in functions [SQL Server]
- nondeterministic functions
- extended stored procedures [SQL Server], functions that call
- deterministic functions
- user-defined functions [SQL Server], deterministic
ms.assetid: 2f3ce5f5-c81c-4470-8141-8144d4f218dd
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 5463ac19caf9a82e48dd59c4ba05873587b74324
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48214710"
---
# <a name="deterministic-and-nondeterministic-functions"></a>Deterministische und nicht deterministische Funktionen
  Deterministische Funktionen geben bei jedem Aufrufen dasselbe Ergebnis zurück, wenn sie mit einem bestimmten Satz von Eingabewerten aufgerufen werden und die Datenbank denselben Status aufweist. Nicht deterministische Funktionen können bei jedem Aufrufen unterschiedliche Ergebnisse zurückgeben, wenn sie mit einem bestimmten Satz von Eingabewerten aufgerufen werden – selbst wenn die Datenbank, auf die zugegriffen wird, immer denselben Status aufweist. Beispielsweise gibt die AVG-Funktion immer dasselbe Ergebnis zurück, sofern die zuvor genannten Bedingungen erfüllt sind. Die GETDATE-Funktion hingegen, die den aktuellen datetime-Wert liefert, gibt immer ein anderes Ergebnis zurück.  
  
 Benutzerdefinierte Funktionen weisen eine Reihe von Eigenschaften auf, mit denen festgelegt wird, ob das [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in der Lage ist, die Ergebnisse der Funktion zu indizieren – entweder durch Indizes für berechnete Spalten, die die Funktion aufrufen, oder durch indizierte Sichten, die auf die Funktion verweisen. Der Determinismus einer Funktion ist eine solche Eigenschaft. Für eine Sicht kann z. B. kein gruppierter Index erstellt werden, falls die Sicht auf nicht deterministische Funktionen verweist. Weitere Informationen zu Eigenschaften von Funktionen, einschließlich Determinismus, finden Sie unter [Benutzerdefinierte Funktionen](user-defined-functions.md).  
  
 In diesem Thema werden der Determinismus integrierter Systemfunktionen und die Auswirkungen auf die deterministische Eigenschaft benutzerdefinierter Funktionen erläutert, wenn in dieser ein Aufruf erweiterter gespeicherter Prozeduren enthalten ist.  
  
## <a name="built-in-function-determinism"></a>Determinismus integrierter Funktionen  
 Der Determinismus integrierter Funktionen kann nicht beeinflusst werden. Jede integrierte Funktion ist abhängig von deren Implementierung durch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]deterministisch oder nicht deterministisch. Wenn beispielsweise eine ORDER BY-Klausel in einer Abfrage angegeben wird, wird der Determinismus einer Funktion, die in der Abfrage verwendet wird, nicht geändert.  
  
 Alle integrierten Zeichenfolgenfunktionen sind deterministisch. Eine Liste dieser Funktionen finden Sie unter [Zeichenfolgenfunktionen &#40;Transact-SQL&#41;](/sql/t-sql/functions/string-functions-transact-sql).  
  
 Die folgenden integrierten Funktionen aus Kategorien anderer integrierter Funktionen als Zeichenfolgenfunktionen sind immer deterministisch:  
  
||||  
|-|-|-|  
|ABS|DATEDIFF|POWER|  
|ACOS|DAY|RADIANS|  
|ASIN|DEGREES|ROUND|  
|ATAN|EXP|SIGN|  
|ATN2|FLOOR|SIN|  
|CEILING|ISNULL|SQUARE|  
|COALESCE|ISNUMERIC|SQRT|  
|COS|LOG|TAN|  
|COT|LOG10|YEAR|  
|DATALENGTH|MONTH||  
|DATEADD|NULLIF||  
  
 Die folgenden Funktionen sind nicht immer deterministisch, können jedoch in indizierten Sichten oder Indizes für berechnete Spalten verwendet werden, wenn sie als deterministische Funktion angegeben werden.  
  
|Funktion|Kommentare|  
|--------------|--------------|  
|alle Aggregatfunktionen|Alle Aggregatfunktionen sind deterministisch, es sei denn, sie werden mit den OVER- und ORDER BY-Klauseln angegeben. Eine Liste dieser Funktionen finden Sie unter [Aggregatfunktionen &#40;Transact-SQL&#41;](/sql/t-sql/functions/aggregate-functions-transact-sql).|  
|CAST|Deterministisch, wenn nicht mit `datetime`, `smalldatetime` oder `sql_variant` verwendet.|  
|CONVERT|Deterministisch, wenn nicht eine der folgenden Bedingungen vorliegt:<br /><br /> Der Quelltyp ist `sql_variant`.<br /><br /> Zieltyp `sql_variant` und der Quelltyp ist nicht deterministisch.<br /><br /> Der Quell- oder Zieltyp ist `datetime` oder `smalldatetime`, der andere Quell- oder Zieltyp ist eine Zeichenfolge, und es wird ein nicht deterministisches Format angegeben. Ein deterministisches Format kann nur verwendet werden, wenn der style-Parameter konstant ist. Wenn die Werte für "style" kleiner oder gleich 100 sind, sind sie nicht deterministisch, mit Ausnahme der style-Werte 20 und 21. style-Werte über 100 sind deterministisch, mit Ausnahme der style-Werte 106, 107, 109 und 113.|  
|CHECKSUM|Deterministisch, mit Ausnahme von CHECKSUM(*).|  
|ISDATE|Nur deterministisch in Verbindung mit der CONVERT-Funktion, wenn der style-Parameter von CONVERT angegeben ist und "style" nicht den Wert 0, 100, 9 oder 109 aufweist.|  
|RAND|RAND ist nur deterministisch, wenn ein *seed* -Parameter angegeben wird.|  
  
 Alle Konfigurations-, Cursor-, Metadaten-, Sicherheits- und statistischen Systemfunktionen sind nicht deterministisch. Eine Liste dieser Funktionen finden Sie unter [Konfigurationsfunktionen &#40;Transact-SQL&#41;](/sql/t-sql/functions/configuration-functions-transact-sql), [Cursorfunktionen &#40;Transact-SQL&#41;](/sql/t-sql/functions/cursor-functions-transact-sql), [Metadatenfunktionen &#40;Transact-SQL&#41;](/sql/t-sql/functions/metadata-functions-transact-sql), [Sicherheitsfunktionen &#40;Transact-SQL&#41;](/sql/t-sql/functions/security-functions-transact-sql) und [Statistische Systemfunktionen &#40;Transact-SQL&#41;](/sql/t-sql/functions/system-statistical-functions-transact-sql).  
  
 Die folgenden integrierten Funktionen aus anderen Kategorien sind immer nicht deterministisch:  
  
|||  
|-|-|  
|@@CONNECTIONS|GETDATE|  
|@@CPU_BUSY|GETUTCDATE|  
|@@DBTS|GET_TRANSMISSION_STATUS|  
|@@IDLE|LAG|  
|@@IO_BUSY|LAST_VALUE|  
|@@MAX_CONNECTIONS|LEAD|  
|@@PACK_RECEIVED|MIN_ACTIVE_ROWVERSION|  
|@@PACK_SENT|NEWID|  
|@@PACKET_ERRORS|NEWSEQUENTIALID|  
|@@TIMETICKS|NEXT VALUE FOR|  
|@@TOTAL_ERRORS|NTILE|  
|@@TOTAL_READ|PARSENAME|  
|@@TOTAL_WRITE|PERCENTILE_CONT|  
|CUME_DIST|PERCENTILE_DISC|  
|CURRENT_TIMESTAMP|PERCENT_RANK|  
|DENSE_RANK|RAND|  
|FIRST_VALUE|RANK|  
||ROW_NUMBER|  
||TEXTPTR|  
  
## <a name="calling-extended-stored-procedures-from-functions"></a>Aufrufen erweiterter gespeicherter Prozeduren aus Funktionen  
 Funktionen, die erweiterte gespeicherte Prozeduren aufrufen, sind nicht deterministisch, da erweiterte gespeicherte Prozeduren Nebeneffekte im Hinblick auf die Datenbank verursachen können. Nebeneffekte sind Änderungen am globalen Status der Datenbank, wie z. B. ein Update einer Tabelle, oder an einer externen Ressource, wie z. B. einer Datei oder des Netzwerkes. Beispiel: Änderungen an einer Datei oder Senden einer E-Mail-Nachricht. Sie sollten sich nicht auf die Rückgabe eines konsistenten Resultsets verlassen, wenn Sie eine erweiterte gespeicherte Prozedur von einer benutzerdefinierten Funktion aus ausführen. Die Verwendung benutzerdefinierter Funktionen, die zu Nebeneffekten hinsichtlich der Datenbank führen, wird nicht empfohlen.  
  
 Wenn eine erweiterte gespeicherte Prozedur aus einer Funktion heraus aufgerufen wird, kann die Prozedur keine Resultsets an den Client zurückgeben. Jede Open Data Services-API, die Resultsets an den Client zurückgibt, weist den Rückgabecode FAIL auf.  
  
 Die erweiterte gespeicherte Prozedur kann erneut eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]herstellen. Die Prozedur kann jedoch keine Verbindung mit derselben Transaktion wie die ursprüngliche Funktion herstellen, durch die die erweiterte gespeicherte Prozedur aufgerufen wurde.  
  
 Wie bei Aufrufen von einem Batch oder einer gespeicherten Prozedur aus wird die erweiterte gespeicherte Prozedur im Kontext des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Sicherheitskontos ausgeführt, unter dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird. Der Besitzer der erweiterten gespeicherten Prozedur sollte dies berücksichtigen, wenn er anderen Benutzern Berechtigungen zum Ausführen der Prozedur erteilt.  
  
  
