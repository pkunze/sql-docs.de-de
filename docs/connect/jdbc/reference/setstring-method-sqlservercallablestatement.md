---
title: SetString-Methode (SQLServerCallableStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f38b97b5-d4f0-4f74-a33d-740241a85842
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a2fa007aa6edfc764534f745029ae6107edd6d6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32844105"
---
# <a name="setstring-method-sqlservercallablestatement"></a>setString-Methode (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf den angegebenen Java **Zeichenfolge** Wert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setString(java.lang.String sCol,  
                      java.lang.String s)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sCol*  
  
 Ein **Zeichenfolge** , die den Namen des Parameters enthält.  
  
 *S*  
  
 Ein **Zeichenfolge** Wert.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Hinweise  
 Diese SetString-Methode wird von der SetString-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
 Binäre Konvertierungen von Zeichenfolgen in erfolgen nur, wenn [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] weiß der Zieltyp binär ist. In Fällen, in dem der JDBC-Treiber nicht den zugrunde liegenden Typ bekannt, übergeben sie die **Zeichenfolge** literal und ein Serverfehler zurückgegeben, wenn der Server die Konvertierung nicht ausführen kann.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
