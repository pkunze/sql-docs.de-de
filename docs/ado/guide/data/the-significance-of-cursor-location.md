---
title: Die Bedeutung der Cursorposition | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- server-side cursors [ADO]
- cursors [ADO], client-side
- client-side cursors [ADO]
- cursors [ADO], server-side
ms.assetid: 70ef5b1c-0459-41a1-b796-031f61a29a8a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d25153a3c84340ad6feea43aa969ef52d358fe4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47717718"
---
# <a name="the-significance-of-cursor-location"></a>Die Bedeutung der Cursorposition
Alle Cursor werden temporäre Ressourcen zum Speichern der Daten verwendet. Diese Ressourcen können Speicher, eine Auslagerungsdatei des Datenträgers, temporäre Dateien oder sogar temporären Speicherplatz in der Datenbank sein. Der Cursor wird aufgerufen, eine *clientseitige* -Cursor, wenn diese Ressourcen auf dem Clientcomputer gespeichert sind. Der Cursor wird aufgerufen, eine *serverseitige* -Cursor, wenn diese Ressourcen auf dem Server gespeichert sind.  
  
## <a name="client-side-cursors"></a>Clientcursor  
 Rufen Sie in ADO für einen clientseitigen Cursor durch Verwendung der **AdUseClient CursorLocationEnum.** Mit einer nicht-Client-Side Keysetcursor sendet der Server das gesamte Resultset, die über das Netzwerk an den Clientcomputer an. Der Client-Computer bietet und verwaltet die temporäre Ressourcen, die durch die Menge Cursor und Ergebnis erforderlich. Die Client-Anwendung kann das gesamte Resultset zur Ermittlung der Zeilen muss durchsuchen.  
  
 Statische und keysetgesteuerte clientseitigen Cursorn können eine spürbare Last auf Ihrer Arbeitsstation platzieren, wenn sie zu viele Zeilen enthalten. Während alle Cursorbibliotheken zum Erstellen von Cursorn mit Tausenden von Zeilen sind, können Anwendungen entwickelt werden solche großen Rowsets abgerufen unbefriedigend. Es gibt natürlich Ausnahmen. Bei einigen Anwendungen ist ein große clientseitigen Cursor kann durchaus sinnvoll sein, und Leistung möglicherweise ein Problem nicht.  
  
 Ein offensichtlicher Vorteil besteht, von der clientseitigen Cursor ist die schnelle Reaktion. Nachdem das Resultset an den Clientcomputer heruntergeladen wurde, ist das Durchsuchen der Zeilen sehr schnell. Ihre Anwendung ist in der Regel stärker skalierbare mit clientseitigen Cursorn, da die ressourcenanforderungen des Cursors auf jedem Client separate und nicht auf dem Server platziert werden.  
  
## <a name="server-side-cursors"></a>Serverseitiger Cursor  
 Rufen Sie in ADO für einen serverseitigen Cursor durch Verwendung der **AdUseServer CursorLocationEnum.** Mit einem serverseitigen Cursor verwaltet der Server das Resultset mit Ressourcen, die vom Server-Computer bereitgestellt. Der serverseitige Cursor werden nur die angeforderten Daten zurück, über das Netzwerk. Diese Art von Cursor bieten manchmal eine bessere Leistung als die clientseitigen Cursor verwenden, insbesondere in Situationen, in denen zu übermäßig hohem Netzwerkverkehr ein Problem aufgetreten ist.  
  
 Allerdings ist es wichtig, darauf hinzuweisen, dass ein serverseitige Cursor – zumindest vorübergehend, wertvolle Serverressourcen verbraucht, für jeden aktiven Client. Sie müssen entsprechend planen, um sicherzustellen, dass Ihre Serverhardware verwalten all die serverseitige Cursor, die von aktiven Clients angefordert werden kann. Darüber hinaus ein serverseitigen Cursor kann langsam sein, da sie nur Zugriff auf einzelne Zeilen enthält, wird kein Cursor Batch verfügbar sind.  
  
 Serverseitige Cursor sind nützlich, beim Einfügen, aktualisieren oder Löschen von Datensätzen. Mit Server-Cursor haben Sie mehrere aktive Anweisungen über die gleiche Verbindung.
