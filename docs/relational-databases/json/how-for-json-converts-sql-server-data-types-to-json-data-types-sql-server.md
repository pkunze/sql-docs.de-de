---
title: So konvertiert FOR JSON SQL Server-Datentypen in JSON-Datentypen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/07/2016
ms.prod: sql
ms.reviewer: douglasl
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- FOR JSON, data type conversion
ms.assetid: da356f06-efd0-4ea3-8157-77395bf790d7
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 16749ba0dbd2b3c59ac5691d120ce1442100650a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47648258"
---
# <a name="how-for-json-converts-sql-server-data-types-to-json-data-types-sql-server"></a>So konvertiert FOR JSON SQL Server-Datentypen in JSON-Datentypen (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Die **FOR JSON** -Klausel verwendet die folgenden Regeln, um SQL Server-Datentypen in JSON-Typen in der JSON-Ausgabe zu konvertieren.  
  
|Kategorie|SQL Server-Datentyp|JSON-Datentyp|  
|--------------|--------------|---------------|  
|Zeichen- und Zeichenfolgetypen|char, nchar, varchar, nvarchar|Zeichenfolge|  
|Numerische Typen|int, bigint, float, decimal, numeric|number|  
|Bit-Typ|bit|Boolesche Werte ("true" oder "false")|  
|Datum- und Uhrzeittypen|date, datetime, datetime2, time, datetimeoffset|Zeichenfolge|  
|Binärtypen|varbinary, binary, image, timestamp, rowversion|BASE64-codierte Zeichenfolge|  
|CLR-Typen|geometry, geography, andere CLR-Typen|Wird nicht unterstützt. Diese Typen geben einen Fehler zurück.<br /><br /> Verwenden Sie in der SELECT-Anweisung CAST oder CONVERT, oder verwenden Sie eine CLR-Eigenschaft oder -Methode, um die Quelldaten in einen SQL Server-Datentyp zu konvertieren, der erfolgreich in einen JSON-Typ konvertiert werden kann. Verwenden Sie z.B. **STAsText()** für den Geometrietyp oder **ToString()** für alle CLR-Typen. Der Typ des JSON-Ausgabewerts wird dann abgeleitet aus dem Rückgabetyp der Konvertierung, die Sie auf die SELECT-Anweisung anwenden.|  
|Andere Typen|uniqueidentifier, money|Zeichenfolge|  

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Weitere Informationen zu JSON in SQL Server und Azure SQL-Datenbank  
  
### <a name="microsoft-blog-posts"></a>Microsoft-Blogbeiträge  
  
Spezielle Lösungen, Anwendungsfälle und Empfehlungen finden Sie in den [Blogbeiträgen über die integrierte JSON-Unterstützung](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) in SQL-Server und in Azure SQL-Datenbank.  

### <a name="microsoft-videos"></a>Microsoft-Videos

Eine visuelle Einführung in die JSON-Unterstützung, die in SQL Server und Azure SQL-Datenbank integriert ist, finden Sie in den folgenden Videos:

-   [SQL Server 2016 and JSON Support](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support)

-   [Using JSON in SQL Server 2016 and Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database)

-   [JSON as a bridge between NoSQL and relational worlds](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds)
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Formatieren von Abfrageergebnisse als JSON mit FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  
