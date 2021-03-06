---
title: Parallelitätssteuerung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
ms.assetid: 75e4adb3-3d43-49c5-8c5e-8df96310d912
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 44d31fc1f929ca60d34e49db135cefd1a8ae7ebc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47831368"
---
# <a name="concurrency-control"></a>Parallelitätssteuerung
*Parallelität* ist die Fähigkeit von zwei Transaktionen, die die gleichen Daten zur gleichen Zeit verwenden und mit höheren Transaction Isolation in der Regel weniger ist. Dies ist da Transaktionsisolation normalerweise durch Sperren von Zeilen implementiert wird und wie weitere Zeilen gesperrt sind, weniger Transaktionen abgeschlossen werden, können ohne durch eine gesperrte Zeile zumindest vorübergehend blockiert. Während reduzierter Parallelität in der Regel als ein Kompromiss für höheren Isolationsstufen von Transaktionen beibehalten Datenbankintegrität akzeptiert wird, kann es ein Problem bei der interaktiven Anwendungen, mit hoher Lese-/Schreibzugriff-Aktivität, die Cursor verwendet werden.  
  
 Nehmen wir beispielsweise an, die eine Anwendung ausgeführt wird, die SQL-Anweisung **wählen \* FROM Orders**. Ruft **SQLFetchScroll** , scrollen Sie auf das Ergebnis festgelegt und ermöglicht dem Benutzer, zu aktualisieren, löschen oder Einfügen von Bestellungen. Nachdem der Benutzer aktualisieren, löschen oder eine Bestellung fügt, überträgt die Anwendung die Transaktion aus.  
  
 Wenn die Isolationsstufe Repeatable Read ist, kann bei die Transaktion – je nach Implementierung ist – jede Zeile, die vom Sperren **SQLFetchScroll**. Wenn die Isolationsstufe Serializable ist, kann die Transaktion die gesamte Orders-Tabelle sperren. In beiden Fällen gibt die Transaktion ihre Sperren frei, nur, wenn sie ein Commit oder Rollback ausgeführt. Also wenn der Benutzer viel Zeit mit dem Lesen von Bestellungen und sehr wenig Zeit verbringt, aktualisieren, löschen oder eingefügt werden, ist die Transaktion problemlos eine große Anzahl von Zeilen sperren kann, sodass sie nicht verfügbar sind, anderen Benutzern.  
  
 Dies ist ein Problem, selbst wenn der Cursor schreibgeschützt ist, und die Anwendung dem Benutzer ermöglicht, die nur vorhandene Bestellungen zu lesen. In diesem Fall die Anwendung führt einen Commit der Transaktion und sperren, freigegeben, wenn aufgerufen **SQLCloseCursor** (im Autocommit-Modus) oder **SQLEndTran** (im Manualcommit-Modus).  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Parallelitätstypen](../../../odbc/reference/develop-app/concurrency-types.md)  
  
-   [Vollständige Parallelität](../../../odbc/reference/develop-app/optimistic-concurrency.md)
