---
title: MSrepl_commands (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSrepl_commands
- MSrepl_commands_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_commands system table
ms.assetid: 53b9f9cd-9429-47a0-aba2-908fc60e7036
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 44b9b1868959b744bf0d24300f828b351b521f54
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47834518"
---
# <a name="msreplcommands-transact-sql"></a>MSrepl_commands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSrepl_commands** -Tabelle enthält Zeilen mit replizierten Befehlen. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|Die ID der Verlegerdatenbank.|  
|**xact_seqno**|**varbinary(16)**|Die Transaktionssequenznummer.|  
|**type**|**int**|Der Befehlstyp.|  
|**article_id**|**int**|Die ID des Artikels.|  
|**originator_id**|**int**|Die ID des Urhebers.|  
|**command_id**|**int**|Die Befehls-ID.|  
|**verbleiben**|**bit**|Gibt an, ob es sich um einen Teilbefehl handelt.|  
|**Befehl**|**varbinary(1024)**|Der Befehlswert.|  
|**Hashkey**|**int**|Intern-nur zur Verwendung.|  
|**originator_lsn**|**varbinary(16)**|Identifiziert die LSN des Befehls in der Ausgangsveröffentlichung. Wird in der Peer-zu-Peer-Transaktionsreplikation verwendet.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [Sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)  
  
  
