---
title: Sys.sp_rda_reconcile_indexes (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sp_rda_reconcile_indexes
- sp_rda_reconcile_indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_indexes stored procedure
ms.assetid: 96b31ab9-bf84-46d6-9990-81f5c51f885a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 329446a2ca5b7719e68123b2257d32ceddcd0e8a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47756518"
---
# <a name="syssprdareconcileindexes-transact-sql"></a>Sys.sp_rda_reconcile_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Fügt eine Schemaaufgabe an, wenn Sie Indizes in der Remotetabelle abstimmen möchten. Nachdem diese Aufgabe erfolgreich abgeschlossen wurde, hat die Remotetabelle die gleichen Indizes, die auf der lokalen Stretch-aktivierte Tabelle vorhanden sind.  
  
 Liegt eine andere Aufgabe in der Warteschlange Indizes ausgleichen, wenn Sie Sie aufrufen **Sp_rda_reconcile_indexes**, diese gespeicherte Prozedur nicht in die Warteschlange eines doppelten Vorgangs.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_rda_reconcile_indexes [@objname = ] 'objname'  
  
```  
  
## <a name="arguments"></a>Argumente  
 [@objname =] *"Objname"*  
 Ist der qualifizierte oder nicht qualifizierte Name der Stretch-aktivierte Tabelle für die Indizes abgestimmt werden sollen. Anführungszeichen sind erforderlich, nur dann, wenn Sie ein qualifiziertes Objekt angeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder >0 (Fehler)  
  
## <a name="see-also"></a>Siehe auch  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
