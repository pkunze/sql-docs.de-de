---
title: Vom Server zum Client ausgeführte Konvertierungen | Microsoft-Dokumentation
description: Server/Client-Konvertierungen
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-date-time
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB], server to client
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: c5b69cb8fac0d91728e9cef945e83159e3151bc5
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43024418"
---
# <a name="conversions-performed-from-server-to-client"></a>Server/Client-Konvertierungen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Beschreibt date/time-Konvertierungen, die zwischen [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (oder höher) und einer Clientanwendung durchgeführt werden, die mit dem OLE DB-Treiber für SQL Server geschrieben wurde.  
  
## <a name="conversions"></a>Konvertierungen  
 Die folgende Tabelle beschreibt die Konvertierungen der Typen, die an den Client zurückgegeben werden, und die in der Bindung verwendeten Typen. Für Output-Parameter, wenn ICommandWithParameters:: SetParameterInfo aufgerufen wurde und des Typs in *PwszDataSourceType* entspricht nicht der tatsächliche Typ auf dem Server eine implizite Konvertierung durch den Server erfolgt , und der an den Client zurückgegebene Typ entspricht den Typ, der über ICommandWithParameters:: SetParameterInfo angegeben. Dies kann zu unerwarteten Konvertierungsergebnissen führen, wenn sich die Konvertierungsregeln des Servers von den in diesem Artikel genannten Regeln unterscheiden. Wenn beispielsweise ein Standarddatum bereitgestellt werden muss, verwendet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 1900-1-1, nicht 1899-12-30.  
  
|To -><br /><br /> Von|DATE|DBDATE|DBTIME|DBTIME2|DBTIMESTAMP|DBTIMESTAMPOFFSET|FILETIME|BYTES|VARIANT|SSVARIANT|BSTR|STR|WSTR|  
|----------------------|----------|------------|------------|-------------|-----------------|-----------------------|--------------|-----------|-------------|---------------|----------|---------|----------|  
|date|1, 7|OK|-|-|1|1, 3|1, 7|-|OK (VT_BSTR)|OK|OK|4|4|  
|Uhrzeit|5, 6, 7|-|9|OK|6|3, 6|5, 6|-|OK (VT_BSTR)|OK|OK|4|4|  
|Smalldatetime|7|8|9, 10|10|OK|3|7|-|7 (VT_DATE)|OK|OK|4|4|  
|DATETIME|5, 7|8|9, 10|10|OK|3|7|-|7 (VT_DATE)|OK|OK|4|4|  
|Datetime2|5, 7|8|9, 10|10|7|3|5, 7|-|OK (VT_BSTR)|OK|OK|4|4|  
|Datetimeoffset|5, 7, 11|8, 11|9, 10, 11|10, 11|7, 11|OK|5, 7, 11|-|OK (VT_BSTR)|OK|OK|4|4|  
|Char, Varchar,<br /><br /> Nchar, Nvarchar|7, 13|12|12, 9|12|12|12|7, 13|–|–|–|–|–|–|  
|Sql_variant<br /><br /> (datetime)|7|8|9, 10|10|OK|3|7|-|7(VT_DATE)|OK|OK|4|4|  
|Sql_variant<br /><br /> (smalldatetime)|7|8|9, 10|10|OK|3|7|-|7(VT_DATE)|OK|OK|4|4|  
|Sql_variant<br /><br /> (date)|1, 7|OK|2|2|1|1, 3|1, 7|-|OK(VT_BSTR)|OK|OK|4|4|  
|Sql_variant<br /><br /> (time)|5, 6, 7|2|6|OK|6|3, 6|5, 6|-|OK(VT_BSTR)|OK|OK|4|4|  
|Sql_variant<br /><br /> (datetime2)|5, 7|8|9, 10|10|OK|3|5, 7|-|OK(VT_BSTR)|OK|OK|4|4|  
|Sql_variant<br /><br /> (datetimeoffset)|5, 7, 11|8, 11|9, 10, 11|10, 11|7, 11|OK|5, 7, 11|-|OK(VT_BSTR)|OK|OK|4|4|  
  
## <a name="key-to-symbols"></a>Aufschlüsselung der Symbole  
  
|Symbol|Bedeutung|  
|------------|-------------|  
|OK|Keine Konvertierung notwendig.|  
|-|Es wird keine Konvertierung unterstützt. Wenn die Bindung überprüft wird, wenn IAccessor:: CreateAccessor aufgerufen wird, wird DBBINDSTATUS_UPSUPPORTEDCONVERSION in zurückgegeben *RgStatus*. Bei Verzögerung der Accessorüberprüfung wird DBSTATUS_E_BADACCESSOR festgelegt.|  
|1|Für die Uhrzeitfelder wird 0 festgelegt.|  
|2|DBSTATUS_E_CANTCONVERTVALUE wird festgelegt.|  
|3|Für die Zeitzone wird 0 festgelegt.|  
|4|Wenn der Clientpuffer nicht groß genug ist, wird DBSTATUS_S_TRUNCATED festgelegt. Wenn der Serverdatentyp Sekundenbruchteile enthält, entspricht die Anzahl der Stellen in der Ergebniszeichenfolge genau den Dezimalstellen des Serverdatentyps.|  
|5|Das Abschneiden von Sekunden oder Sekundenbruchteilen wird ignoriert.|  
|6|Für das Datum wird das aktuelle Datum angenommen, es sei denn, die Quelle ist ein Zeichenfolgenliteral für time, und das Ziel ist DBTYPE_DATE. In diesem Fall wird 1899-12-30 verwendet.|  
|7|Wenn der Wert überläuft, wird DBSTATUS_E_DATAOVERFLOW festgelegt.|  
|8|Zeitfelder werden ignoriert.|  
|9|Felder für Sekundenbruchteile werden ignoriert.|  
|10|Die Datumskomponente wird ignoriert.|  
|11|Die Zeitangabe wird in die Clientzeitzone konvertiert. Wenn während dieser Konvertierung ein Fehler auftritt, wird DBSTATUS_E_DATAOVERFLOW festgelegt.|  
|12|Die Zeichenfolge wird als ISO-Literal analysiert und in den Zieltyp konvertiert. Falls dies fehlschlägt, wird die Zeichenfolge als OLE-Datumsliteral analysiert (welches gleichfalls Zeitkomponenten enthält) und vom OLE-Datumstyp (DBTYPE_DATE) in den Zieldatumstyp konvertiert. Die Zeichenfolge muss mit der für die ISO-Formatanalyse zulässigen Syntax für Literale des Zieltyps übereinstimmen, damit der Vorgang ordnungsgemäß ausgeführt werden kann. Die Zeichenfolge muss mit der von OLE erkannten Syntax übereinstimmen, damit die OLE-Analyse ordnungsgemäß ausgeführt werden kann. Wenn die Zeichenfolge nicht analysiert werden kann, wird DBSTATUS_E_CANTCONVERTVALUE festgelegt. Wenn Komponentenwerte außerhalb des Gültigkeitsbereichs liegen, wird DBSTATUS_E_DATAOVERFLOW festgelegt.|  
|13|Die Zeichenfolge wird als ISO-Literal analysiert und in den Zieltyp konvertiert. Falls dies fehlschlägt, wird die Zeichenfolge als OLE-Datumsliteral analysiert (welches gleichfalls Zeitkomponenten enthält) und vom OLE-Datumstyp (DBTYPE_DATE) in den Zieldatumstyp konvertiert. Die Zeichenfolge muss der Syntax für datetime-Literale entsprechen, außer wenn das Ziel DBTYPE_DATE oder DBTYPE_DBTIMESTAMP ist. Wenn dies der Fall ist, ist ein Literal vom Typ datetime oder vom Typ time für die erfolgreiche ISO-Formatanalyse zulässig. Die Zeichenfolge muss mit der von OLE erkannten Syntax übereinstimmen, damit die OLE-Analyse ordnungsgemäß ausgeführt werden kann. Wenn die Zeichenfolge nicht analysiert werden kann, wird DBSTATUS_E_CANTCONVERTVALUE festgelegt. Wenn Komponentenwerte außerhalb des Gültigkeitsbereichs liegen, wird DBSTATUS_E_DATAOVERFLOW festgelegt.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Bindungen und Konvertierungen &#40;OLE DB&#41;](../../oledb/ole-db-date-time/conversions-ole-db.md)  
  
  
