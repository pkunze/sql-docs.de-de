---
title: GRANT (Zertifikatberechtigungen) (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- granting permissions [SQL Server], certificates
- certificates [SQL Server], permissions
- permissions [SQL Server], certificates
- GRANT statement, certificates
ms.assetid: 77270245-a24b-4a20-b481-e6a5ea05b499
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 447fe67a9fa97fbb475f9d6daaed181347cabe50
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47656008"
---
# <a name="grant-certificate-permissions-transact-sql"></a>GRANT (Zertifikatberechtigungen) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Erteilt Berechtigungen für ein Zertifikat in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```
GRANT permission  [ ,...n ]    
    ON CERTIFICATE :: certificate_name   
    TO principal [ ,...n ] [ WITH GRANT OPTION ]   
    [ AS granting_principal ]   
```  
  
## <a name="arguments"></a>Argumente  
 *permission*  
 Gibt eine Berechtigung an, die für ein Zertifikat erteilt werden kann. Unten aufgeführt.  
  
 ON CERTIFICATE **::***certificate_name*  
 Gibt das Zertifikat an, für das die Berechtigung erteilt wird. Der Bereichsqualifizierer "::" ist erforderlich.  
  
 *database_principal*  
 Gibt den Prinzipal an, für den die Berechtigung erteilt wird. Einer der folgenden Typen:  
  
-   Datenbankbenutzer  
-   Datenbankrolle (database role)  
-   Anwendungsrolle  
-   Einem Windows-Anmeldenamen zugeordneter Datenbankbenutzer  
-   Einer Windows-Gruppe zugeordneter Datenbankbenutzer  
-   Einem Zertifikat zugeordneter Datenbankbenutzer  
-   Einem asymmetrischen Schlüssel zugeordneter Datenbankbenutzer  
-   Keinem Serverprinzipal zugeordneter Datenbankbenutzer.  
  
GRANT OPTION  
 Gibt an, dass der Prinzipal die angegebene Berechtigung auch anderen Prinzipalen erteilen kann.  
  
AS *granting_principal*  
 Gibt einen Prinzipal an, von dem der Prinzipal, der diese Abfrage ausführt, sein Recht zum Erteilen der Berechtigung ableitet. Einer der folgenden Typen:  
  
-   Datenbankbenutzer  
-   Datenbankrolle (database role)  
-   Anwendungsrolle  
-   Einem Windows-Anmeldenamen zugeordneter Datenbankbenutzer  
-   Einer Windows-Gruppe zugeordneter Datenbankbenutzer  
-   Einem Zertifikat zugeordneter Datenbankbenutzer  
-   Einem asymmetrischen Schlüssel zugeordneter Datenbankbenutzer  
-   Keinem Serverprinzipal zugeordneter Datenbankbenutzer.  
  
## <a name="remarks"></a>Remarks  
 Ein Zertifikat ist ein sicherbares Element auf Datenbankebene in der Datenbank, die dessen übergeordnetes Element in der Berechtigungshierarchie ist. Die spezifischsten und am meisten beschränkten Berechtigungen, die für ein Zertifikat erteilt werden können, sind unten aufgeführt. Auch die allgemeineren Berechtigungen sind aufgeführt, die diese implizit enthalten.  
  
|Zertifikatsberechtigung|Impliziert durch die Zertifikatsberechtigung|Impliziert durch Datenbankberechtigung|  
|----------------------------|---------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY CERTIFICATE|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Berechtigungen  
 Der Berechtigende (oder der mit der AS-Option angegebene Prinzipal) benötigt entweder die Berechtigung selbst mit GRANT OPTION oder eine höhere Berechtigung, die die erteilte Berechtigung impliziert.  
  
 Wenn Sie die Option AS verwenden, gelten die folgenden zusätzlichen Anforderungen.  
  
|AS *granting_principal*|Zusätzliche Berechtigung erforderlich|  
|------------------------------|------------------------------------|  
|Datenbankbenutzer|IMPERSONATE-Berechtigung für den Benutzer, die Mitgliedschaft in der festen Datenbankrolle **db_securityadmin** und **db_owner** oder die Mitgliedschaft in der festen Serverrolle **sysadmin**.|  
|Einem Windows-Anmeldenamen zugeordneter Datenbankbenutzer|IMPERSONATE-Berechtigung für den Benutzer, die Mitgliedschaft in der festen Datenbankrolle **db_securityadmin** und **db_owner** oder die Mitgliedschaft in der festen Serverrolle **sysadmin**.|  
|Einer Windows-Gruppe zugeordneter Datenbankbenutzer|Mitgliedschaft in der Windows-Gruppe, Mitgliedschaft in der festen Datenbankrolle **db_securityadmin**, Mitgliedschaft in der festen Datenbankrolle **db_owner** oder Mitgliedschaft in der festen Serverrolle **sysadmin**.|  
|Einem Zertifikat zugeordneter Datenbankbenutzer|Mitgliedschaft in der festen Datenbankrolle **db_securityadmin**, Mitgliedschaft in der festen Datenbankrolle **db_owner** oder Mitgliedschaft in der festen Serverrolle **sysadmin**.|  
|Einem asymmetrischen Schlüssel zugeordneter Datenbankbenutzer|Mitgliedschaft in der festen Datenbankrolle **db_securityadmin**, Mitgliedschaft in der festen Datenbankrolle **db_owner** oder Mitgliedschaft in der festen Serverrolle **sysadmin**.|  
|Einem Serverprinzipal zugeordneter Datenbankbenutzer|IMPERSONATE-Berechtigung für den Benutzer, die Mitgliedschaft in der festen Datenbankrolle **db_securityadmin** und **db_owner** oder die Mitgliedschaft in der festen Serverrolle **sysadmin**.|  
|Datenbankrolle|ALTER-Berechtigung für die Rolle, Mitgliedschaft in der festen Datenbankrolle **db_securityadmin**, Mitgliedschaft in der festen Datenbankrolle **db_owner** oder Mitgliedschaft in der festen Serverrolle **sysadmin**.|  
|Anwendungsrolle|ALTER-Berechtigung für die Rolle, Mitgliedschaft in der festen Datenbankrolle **db_securityadmin**, Mitgliedschaft in der festen Datenbankrolle **db_owner** oder Mitgliedschaft in der festen Serverrolle **sysadmin**.|  
  
 Objektbesitzer können Berechtigungen für die Objekte erteilen, die sie besitzen. Prinzipale mit CONTROL-Berechtigung für ein sicherungsfähiges Element können die Berechtigung für dieses sicherungsfähige Element erteilen.  
  
 Empfänger der CONTROL SERVER-Berechtigung, wie z.B. Mitglieder der festen Serverrolle **sysadmin**, können jede beliebige Berechtigung für jedes beliebige sicherungsfähige Element auf dem Server erteilen. Empfänger der CONTROL-Berechtigung für eine Datenbank, wie z.B. Mitglieder der festen Datenbankrolle **db_owner**, können jede beliebige Berechtigung für jedes beliebige sicherungsfähige Element in der Datenbank erteilen. Empfänger der CONTROL-Berechtigung für ein Schema können jede beliebige Berechtigung für jedes Objekt innerhalb des Schemas erteilen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [Berechtigungen &amp;amp;#40;Datenbank-Engine&amp;amp;#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Prinzipale &amp;amp;#40;Datenbank-Engine&amp;amp;#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
