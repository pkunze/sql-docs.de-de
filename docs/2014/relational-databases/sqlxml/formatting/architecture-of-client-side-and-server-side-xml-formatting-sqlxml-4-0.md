---
title: Architektur der Client- und serverseitigen XML-Formatierung (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], XML formatting architecture
- SQLOLEDB provider
- client-side XML formatting
- data providers [SQLXML], XML formatting architecture
- SQLNCLI, XML
- server-side XML formatting
- SQL Server Native Client, XML
- SQLXMLOLEDB Provider, XML formatting architecture
ms.assetid: 52440d9e-89fd-4c15-a008-a1ea99f41387
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 07e8a5bc78ea6c4aa156ff43e4d9a12dae20591e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48086504"
---
# <a name="architecture-of-client-side-and-server-side-xml-formatting-sqlxml-40"></a>Architektur clientseitiger und serverseitiger XML-Formatierung (SQLXML 4.0)
  Die folgende Abbildung zeigt die Architektur der XML-Formatierung auf Serverseite:  
  
 ![Architektur der XML-Formatierung auf dem Server. ](../../../database-engine/dev-guide/media/serversidexml.gif "Architektur der XML-Formatierung auf dem Server.")  
  
 In diesem Beispiel wird der Befehl, der auf dem Client angegeben wird, an den Server gesendet. Der Server erstellt ein XML-Dokument und sendet es an den Client zurück. In diesem Fall hat der Server eine Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Bei der serverseitigen XML-Formatierung können Sie entweder den SQLXMLOLEDB-Anbieter oder den SQLOLEDB-Anbieter verwenden.  Der SQLXMLOLEDB-Anbieter verwendet die Datei Sqlxml4.dll, die in SQLXML 4.0 enthalten ist. Bei der Verwendung des SQLOLEDB-Anbieters erhalten Sie die von Sqlxmlx.dll bereitgestellte SQLXML-Funktionalität standardmäßig. Diese Funktionalität wird in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows oder in Microsoft Data Access Components (MDAC) 2.6 oder höher angeboten. Um Sqlxml4.dll mit SQLOLEDB zu verwenden, müssen Sie die SQLXML-Version-Eigenschaft auf "SQLXML.4.0" für den SQLOLEDB-Verbindungsobjekt festlegen. In beiden Fällen erzeugt der Server das XML-Dokument und sendet es an den Client.  
  
> [!NOTE]  
>  XPath-Abfragen und Updategrams werden auf dem Client analysiert. Um die XPath-Vorlage oder Updategramfunktionalität in SQLXML 4.0 zu erhalten, verwenden Sie Sqlxml4.dll.  
  
 Die folgende Abbildung zeigt die Architektur der XML-Formatierung auf Clientseite.  
  
 ![Architektur der XML-Formatierung auf Clientseite. ](../../../database-engine/dev-guide/media/clientsidexml.gif "Architektur der XML-Formatierung auf Clientseite.")  
  
 In diesem Beispiel verwendet der Client den SQLXMLOLEDB-Anbieter. In der Verbindungszeichenfolge muss die Datenanbieter-Eigenschaft SQLOLEDB festgelegt werden. (Dies ist der einzige in SQLXML 4.0 akzeptierte Wert.) Der auf dem Client ausgeführte Befehl wird an den Server gesendet. Das auf dem Server generierte Rowset wird an den Client gesendet. Die Formatierung des XML-Dokuments aus dem Rowset wird auf dem Client ausgeführt.  
  
 In SQLXML 4.0 kann entweder der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) oder der SQLOLEDB-Anbieter als Datenanbieter verwendet werden. Sie können potenziell auf jede Datenquelle zugreifen. Vorausgesetzt, die Abfrage gibt ein einzelnes Rowset zurück, kann die XML-Transformation auf dem Client angewendet werden.  
  
  
