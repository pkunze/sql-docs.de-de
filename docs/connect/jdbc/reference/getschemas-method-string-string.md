---
title: GetSchemas-Methode (String, String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 672171ac-976f-4605-9bee-2a5e141d92cb
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0684e2ec5e840d6fbe2f45cdcb66f39feb404320
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32837545"
---
# <a name="getschemas-method-string-string"></a>getSchemas-Methode (String, String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die in der aktuellen Datenbank verfügbaren Schemanamen unter Verwendung des angegebenen Katalognamens und des Schemanamens ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public ResultSet getSchemas(java.lang.String catalog,  
                       java.lang.String schemaPattern)  
```  
  
#### <a name="parameters"></a>Parameter  
 *catalog*  
  
 Der Name eines Katalogs in der Datenbank. Bei einer leeren Zeichenfolge ("") enthält das Ergebnis die Schemas ohne einen Katalog. Ist er **null**, der Name des Katalogs wird nicht für die Suche verwendet.  
  
 *schemaPattern*  
  
 Der Name eines Schemas. Ist er **null**, der Schemaname wird nicht für die Suche verwendet.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Hinweise  
 Diese GetSchemas-Methode wird von der GetSchemas-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 GetSchemas-Methode zurückgegebene Resultset enthält die folgenden Informationen an:  
  
|Name|Typ|Description|  
|----------|----------|-----------------|  
|TABLE_SCHEM|**String**|Der Name des Schemas.|  
|TABLE_CATALOG|**String**|Der Katalogname für das Schema.|  
  
 Die Ergebnisse werden nach "TABLE_CATALOG" und dann nach "TABLE_SCHEM" sortiert. In jeder Zeile bildet "TABLE_SCHEM" die erste Spalte und "TABLE_CATALOG" die zweite Spalte.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
