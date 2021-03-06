---
title: Sp_help_publication_access (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_help_publication_access
- sp_help_publication_access_TSQL
helpviewer_keywords:
- sp_help_publication_access
ms.assetid: 9408fa13-54a0-4cb1-8fb0-845e5536ef50
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1d1afcb1e5419e2ddd028440e1ece57f36bb3269
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818224"
---
# <a name="sphelppublicationaccess-transact-sql"></a>sp_help_publication_access (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Liste aller Anmeldenamen zurück, denen der Zugriff auf eine Veröffentlichung erteilt wurde. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_publication_access [ @publication = ] 'publication'  
    [ , [ @return_granted = ] 'return_granted' ]   
    [ , [ @login = ] 'login' ]  
    [ , [ @initial_list = ] initial_list ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publication=**] **'***publication***'**  
 Der Name der Veröffentlichung, auf die zugegriffen werden soll. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@return_granted=**] **"***Return_granted***"**  
 Die Login-ID *Return_granted* ist **Bit**, hat den Standardwert 1. Wenn **0** angegeben ist und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwendet wird, werden die verfügbaren Anmeldungen, die auf dem Verleger aber nicht auf dem Verteiler angezeigt werden zurückgegeben. Wenn **0** angegeben ist und Windows-Authentifizierung verwendet wird, die Anmeldungen nicht explizit verweigert wurde Zugriff auf den Verleger oder Verteiler zurückgegeben werden.  
  
 [  **@login=**] **"***Anmeldung***"**  
 Die Standardsicherheits-Anmelde-ID. *Anmeldung* ist **Sysname**, hat den Standardwert **%**.  
  
 [  **@initial_list =**] *Initial_list*  
 Gibt an, ob alle Elemente mit Veröffentlichungszugriff zurückgegeben werden oder nur die Elemente, die Zugriff hatten, bevor der Liste neue Elemente hinzugefügt wurden. *Initial_list* bit und hat den Standardwert **0**.  
  
 **1** gibt Informationen für alle Mitglieder der **Sysadmin** Serverrolle mit gültigen Anmeldenamen auf dem Verteiler, die vorhanden waren, wenn die Veröffentlichung erstellt wurde, sowie die aktuelle Anmeldung.  
  
 **0** gibt Informationen für alle Mitglieder der **Sysadmin** über gültige Anmeldenamen auf dem Verteiler, die vorhanden waren, beim Erstellen der Veröffentlichung sowie über sämtliche Benutzer in der veröffentlichungszugriffsliste, die keinen festen Serverrolle gehören zu den **Sysadmin** -Serverrolle sein.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**LoginName**|**nvarchar(256)**|Tatsächlicher Anmeldename|  
|**isntname**|**int**|**0** = Anmeldename ist kein Windows-Benutzer.<br /><br /> **1** = Anmeldename ist ein Windows-Benutzer.|  
|**isntgroup**|**int**|**0** = Anmeldename ist nicht mit einer Windows-Gruppe.<br /><br /> **1** = Anmeldename ist eine Windows-Gruppe.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_help_publication_access** wird in allen Replikationstypen verwendet.  
  
 Wenn beide **Isntname** und **Isntgroup** im Ergebnis sind **0**, davon aus, dass die Anmeldung ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldung.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder die **Db_owner** feste Datenbankrolle können ausführen **Sp_help_publication_access**.  
  
## <a name="see-also"></a>Siehe auch  
 [Sp_grant_publication_access &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql.md)   
 [Sp_revoke_publication_access &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
