---
title: Sicherheitsmodell des Replikations-Agents | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/07/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- Snapshot Agent, security
- agents [SQL Server replication], security
- Distribution Agent, security
- logins [SQL Server replication], permissions for agents
- security [SQL Server replication], agent security model
- Log Reader Agent, security
- Queue Reader Agent, security
- Merge Agent, security
- replication [SQL Server], agents and profiles
ms.assetid: 6d09fc8d-843a-4a7a-9812-f093d99d8192
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b17b7cccec50c9dc8d1eccc5cb6e1caacee47e2a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135664"
---
# <a name="replication-agent-security-model"></a>Sicherheitsmodell des Replikations-Agents
  Das Sicherheitsmodell des Replikations-Agents ermöglicht die präzise Steuerung der Konten, unter denen Replikations-Agents ausgeführt werden und Verbindungen herstellen. Für jeden Agent kann ein gesondertes Konto angegeben werden. Weitere Informationen zur Vorgehensweise beim Angeben von Konten finden Sie unter [Verwalten von Anmeldenamen und Kennwörtern bei der Replikation](manage-logins-and-passwords-in-replication.md).  
  
> [!IMPORTANT]  
>  Wenn ein Mitglied der festen Serverrolle **sysadmin** die Replikation konfiguriert, kann es die Replikations-Agents so konfigurieren, dass sie die Identität des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agentkontos annehmen. Dies geschieht, indem für den Replikations-Agent kein Anmeldename oder Kennwort angegeben wird. Dieser Ansatz ist jedoch nicht empfehlenswert. Sie sollten besser als bewährte Methode in Bezug auf die Sicherheit für jeden Agent ein Konto mit den im Abschnitt zu den für Agents erforderlichen Berechtigungen beschriebenen minimalen Privilegien angeben.  
  
 Replikations-Agents werden wie alle ausführbaren Dateien im Kontext eines Windows-Kontos ausgeführt. Die Agents stellen mithilfe dieses Kontos Verbindungen über die integrierte Sicherheit von Windows her. Unter welchem Konto der Agent ausgeführt wird, ist davon abhängig, wie er gestartet wird:  
  
-   Starten des Agents aus einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agentauftrag heraus (Standardeinstellung): Wenn ein [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agentauftrag zum Starten eines Replikations-Agents verwendet wird, wird dieser Agent im Kontext eines Kontos ausgeführt, das Sie während der Replikationskonfiguration angeben. Weitere Informationen zum [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent und der Replikation finden Sie im Abschnitt "Agentsicherheit mit SQL Server-Agent" weiter unten in diesem Thema. Informationen zu den Berechtigungen, die für das Konto erforderlich sind, unter dem der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Agent ausgeführt wird, finden Sie unter [Konfigurieren des SQL Server Agents](../../../ssms/agent/configure-sql-server-agent.md).  
  
-   Starten des Agents von einer MS-DOS Befehlszeile, entweder direkt oder über ein Skript: Der Agent wird im Kontext des Benutzerkontos ausgeführt, der den Agent in der Befehlszeile ausführt.  
  
-   Starten des Agents aus einer Anwendung, von der Replikationsverwaltungsobjekte (RMO) oder ein ActiveX-Steuerelement verwendet werden: Der Agent wird im Kontext der Anwendung ausgeführt, die RMO bzw. das ActiveX-Steuerelement aufruft.  
  
    > [!NOTE]  
    >  ActiveX-Steuerelemente sind als veraltet markiert.  
  
 Es empfiehlt sich, Verbindungen im Kontext der integrierten Sicherheit von Windows herzustellen. Aus Gründen der Abwärtskompatibilität kann auch die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Sicherheit verwendet werden. Weitere Informationen zu bewährten Methoden finden Sie unter [Replication Security Best Practices](replication-security-best-practices.md).  
  
## <a name="permissions-that-are-required-by-agents"></a>Für Agents erforderliche Berechtigungen  
 Die Konten, unter denen Agents ausgeführt werden und über die sie Verbindungen herstellen, erfordern verschiedene Berechtigungen. Eine Beschreibung zu diesen Berechtigungen finden Sie in der folgenden Tabelle. Es empfiehlt sich, jeden Agent unter einem gesonderten Windows-Konto auszuführen. Außerdem sollten den einzelnen Konten lediglich die erforderlichen Berechtigungen erteilt werden. Weitere Informationen zur Veröffentlichungszugriffsliste (Publication Access List oder PAL), die für eine Reihe von Agents relevant ist, finden Sie unter [Sichern des Verlegers](secure-the-publisher.md).  
  
> [!NOTE]  
>  Durch die Benutzerkontensteuerung (User Account Control, UAC) in einigen Windows-Betriebssystemen kann der Administratorzugriff auf die Momentaufnahmefreigabe verhindert werden. Sie müssen daher den vom Momentaufnahme-Agent, Verteilungs-Agent und Merge-Agent verwendeten Windows-Konten explizit Berechtigungen für die Momentaufnahmefreigabe erteilen. Dies ist auch dann erforderlich, wenn die Windows-Konten Mitglieder der Administratorengruppe sind. Weitere Informationen finden Sie unter [Schützen des Momentaufnahmeordners](secure-the-snapshot-folder.md).  
  
|Agent|Berechtigungen|  
|-----------|-----------------|  
|Momentaufnahme-Agent|Das Windows-Konto, unter dem der Agent ausgeführt wird, wird verwendet, wenn er Verbindungen mit dem Verteiler herstellt. Für dieses Konto ist Folgendes erforderlich:<br /><br /> – Es muss mindestens Mitglied der festen Datenbankrolle **db_owner** in der Verteilungsdatenbank sein.<br /><br /> – Es muss über Lese-, Schreib- und Änderungsberechtigungen für die Momentaufnahmefreigabe verfügen.<br /><br /> <br /><br /> Das zum Herstellen der Verbindung mit dem Verleger verwendete Konto muss zumindest Mitglied der festen Datenbankrolle **db_owner** in der Veröffentlichungsdatenbank sein.|  
|Protokolllese-Agent|Das Windows-Konto, unter dem der Agent ausgeführt wird, wird verwendet, wenn er Verbindungen mit dem Verteiler herstellt. Dieses Konto muss zumindest Mitglied der festen Datenbankrolle **db_owner** in der Verteilungsdatenbank sein.<br /><br /> Das zum Herstellen der Verbindung mit dem Verleger verwendete Konto muss zumindest Mitglied der festen Datenbankrolle **db_owner** in der Veröffentlichungsdatenbank sein.<br /><br /> Bei der Auswahl der `sync_type` Optionen *nur replikationsunterstützung*, *initialisieren mit der Sicherung*, oder *von Lsn initialisieren*, muss der Protokolllese-Agent nach dem Ausführen Ausführen von `sp_addsubscription`, sodass die festgelegten Skripts in die Verteilungsdatenbank geschrieben werden. Der Protokolllese-Agent muss unter einem Konto ausgeführt werden, das Mitglied der festen Serverrolle **sysadmin** ist. Wenn die `sync_type` Option wird festgelegt, um *automatische*, es sind keine speziellen Aktionen für den Protokolllese-Agent erforderlich.|  
|Verteilungs-Agent für Pushabonnements|Das Windows-Konto, unter dem der Agent ausgeführt wird, wird verwendet, wenn er Verbindungen mit dem Verteiler herstellt. Für dieses Konto ist Folgendes erforderlich:<br /><br /> – Es muss mindestens Mitglied der festen Datenbankrolle **db_owner** in der Verteilungsdatenbank sein.<br /><br /> – Es muss Mitglied der PAL sein.<br /><br /> – Es muss über Leseberechtigungen für die Momentaufnahmefreigabe verfügen.<br /><br /> – Es muss über die Leseberechtigung für das Installationsverzeichnis des OLE DB-Anbieters für den Abonnenten verfügen, wenn das Abonnement für einen Nicht-SQL Server-Abonnenten vorgesehen ist.<br /><br /> – Bei der Replikation von LOB-Daten muss der Verteilungs-Agent über Schreibberechtigungen auf dem Replikationsordner **C:\Programme\Microsoft SQL Server\XX\COMfolder** verfügen, wobei „XX“ für die Instanz-ID steht.<br /><br /> <br /><br /> Das zum Herstellen der Verbindung mit dem Abonnenten verwendete Konto muss mindestens Mitglied der festen Datenbankrolle **db_owner** in der Abonnementdatenbank sein oder über vergleichbare Berechtigungen verfügen, wenn das Abonnement nicht SQL Server betrifft.<br /><br /> Hinweis: Bei Verwendung `-subscriptionstreams >= 2` für den Verteilungs-Agent, Sie müssen außerdem gewähren, der `View Server State` Berechtigung auf dem Abonnenten, um Deadlocks zu erkennen.|  
|Verteilungs-Agent für Pullabonnements|Das Windows-Konto, unter dem der Agent ausgeführt wird, wird verwendet, wenn er Verbindungen mit dem Abonnenten herstellt. Dieses Konto muss zumindest Mitglied der festen Datenbankrolle **db_owner** in der Abonnementdatenbank sein. Für das zum Herstellen der Verbindung mit dem Verteiler verwendete Konto ist Folgendes erforderlich:<br /><br /> – Es muss Mitglied der PAL sein.<br /><br /> – Es muss über Leseberechtigungen für die Momentaufnahmefreigabe verfügen.<br /><br /> – Bei der Replikation von LOB-Daten muss der Verteilungs-Agent über Schreibberechtigungen auf dem Replikationsordner **C:\Programme\Microsoft SQL Server\XX\COMfolder** verfügen, wobei „XX“ für die Instanz-ID steht.<br /><br /> <br /><br /> Hinweis: Bei Verwendung `-subscriptionstreams >= 2` für den Verteilungs-Agent, Sie müssen außerdem gewähren, der `View Server State` Berechtigung auf dem Abonnenten, um Deadlocks zu erkennen.|  
|Merge-Agent für Pushabonnements|Das Windows-Konto, unter dem der Agent ausgeführt wird, wird verwendet, wenn er Verbindungen mit dem Verleger und dem Verteiler herstellt. Für dieses Konto ist Folgendes erforderlich:<br /><br /> – Es muss mindestens Mitglied der festen Datenbankrolle **db_owner** in der Verteilungsdatenbank sein.<br /><br /> – Es muss Mitglied der PAL sein.<br /><br /> – Die Anmeldung muss mit einem Benutzer in der Veröffentlichungsdatenbank verknüpft sein.<br /><br /> – Es muss über Leseberechtigungen für die Momentaufnahmefreigabe verfügen.<br /><br /> <br /><br /> Das zum Herstellen der Verbindung mit dem Abonnenten verwendete Konto muss zumindest Mitglied der festen Datenbankrolle **db_owner** in der Abonnementdatenbank sein.|  
|Merge-Agent für Pullabonnements|Das Windows-Konto, unter dem der Agent ausgeführt wird, wird verwendet, wenn er Verbindungen mit dem Abonnenten herstellt. Dieses Konto muss zumindest Mitglied der festen Datenbankrolle **db_owner** in der Abonnementdatenbank sein. Für das zum Herstellen der Verbindung mit dem Verleger und Verteiler verwendete Konto ist Folgendes erforderlich:<br /><br /> – Es muss Mitglied der PAL sein.<br /><br /> – Die Anmeldung muss mit einem Benutzer in der Veröffentlichungsdatenbank verknüpft sein.<br /><br /> – Die Anmeldung muss mit einem Benutzer in der Verteilungsdatenbank verknüpft sein. Der Benutzer kann sein der `Guest` Benutzer.<br /><br /> – Es muss über Leseberechtigungen für die Momentaufnahmefreigabe verfügen.|  
|Warteschlangenlese-Agent|Das Windows-Konto, unter dem der Agent ausgeführt wird, wird verwendet, wenn er Verbindungen mit dem Verteiler herstellt. Dieses Konto muss zumindest Mitglied der festen Datenbankrolle **db_owner** in der Verteilungsdatenbank sein.<br /><br /> Das zum Herstellen der Verbindung mit dem Verleger verwendete Konto muss zumindest Mitglied der festen Datenbankrolle **db_owner** in der Veröffentlichungsdatenbank sein.<br /><br /> Das zum Herstellen der Verbindung mit dem Abonnenten verwendete Konto muss zumindest Mitglied der festen Datenbankrolle **db_owner** in der Abonnementdatenbank sein.|  
  
## <a name="agent-security-under-sql-server-agent"></a>Agentsicherheit mit SQL Server-Agent  
 Wenn Sie die Replikation mithilfe von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Prozeduren oder RMO konfigurieren, wird standardmäßig ein [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agentauftrag für jeden Agent erstellt. Die Agents werden dann im Kontext eines Auftragsschritts ausgeführt, unabhängig davon, ob sie kontinuierlich, nach einem Zeitplan oder bei Bedarf ausgeführt werden. Diese Aufträge können im Ordner **Aufträge** in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]angezeigt werden. Die Auftragsnamen sind in der folgenden Tabelle aufgeführt.  
  
|Agent|Auftragsname|  
|-----------|--------------|  
|Momentaufnahme-Agent|**\<Verleger>-\<Veröffentlichungsdatenbank>-\<Veröffentlichung>-\<Ganzzahl>**|  
|Momentaufnahme-Agent für eine Mergeveröffentlichungspartition|**Dyn_\<Verleger>-\<Veröffentlichungsdatenbank>-\<Veröffentlichung>-\<GUID>**|  
|Protokolllese-Agent|**\<Verleger>-\<Veröffentlichungsdatenbank>-\<Ganzzahl>**|  
|Merge-Agent für Pullabonnements|**\<Verleger>-\<Veröffentlichungsdatenbank>-\<Veröffentlichung>-\<Abonnent>-\<Abonnementdatenbank>-\<Ganzzahl>**|  
|Merge-Agent für Pushabonnements|**\<Verleger>-\<Veröffentlichungsdatenbank>-\<Veröffentlichung>-\<Abonnent>-\<Ganzzahl>**|  
|Verteilungs-Agent für Pushabonnements|**\<Verleger>-\<Veröffentlichungsdatenbank>-\<Veröffentlichung>-\<Abonnent>-\<Integer>** <sup>1</sup>|  
|Verteilungs-Agent für Pullabonnements|**\<Verleger>-\<Veröffentlichungsdatenbank>-\<Veröffentlichung>-\<Abonnent>-\<Abonnementdatenbank>-\<GUID>** <sup>2</sup>|  
|Verteilungs-Agent für Pushabonnements für Nicht-SQL Server-Abonnenten|**\<Verleger>-\<Veröffentlichungsdatenbank>-\<Veröffentlichung>-\<Abonnent>-\<Ganzzahl>**|  
|Warteschlangenlese-Agent|**[\<Verteiler>].\<Ganzzahl>**|  
  
 <sup>1</sup> bei Pushabonnements für Oracle-Veröffentlichungen lautet der Auftragsname ist  **\<Verleger >-\<Verleger**> anstelle von  **\<Verleger >-\< PublicationDatabase >**.  
  
 <sup>2</sup> bei Pullabonnements für Oracle-Veröffentlichungen lautet der Auftragsname ist  **\<Verleger >-\<DistributionDatabase**> anstelle von  **\<Verleger >-\< PublicationDatabase >**.  
  
 Wenn Sie die Replikation konfigurieren, geben Sie Konten an, unter denen die Agents ausgeführt werden sollen. Sämtliche Auftragsschritte werden jedoch im Sicherheitskontext eines *Proxys*ausgeführt, somit führt die Replikation folgende Zuordnungen für die von Ihnen angegebenen Agentkonten intern aus:  
  
-   Das Konto wird zunächst mithilfe des [!INCLUDE[tsql](../../../includes/tsql-md.md)] [CREATE CREDENTIAL](/sql/t-sql/statements/create-credential-transact-sql) statement. Von[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent-Proxys werden Anmeldeinformationen zum Speichern von Informationen zu Windows-Benutzerkonten verwendet.  
  
-   Die gespeicherte Prozedur [sp_add_proxy](/sql/relational-databases/system-stored-procedures/sp-add-proxy-transact-sql) wird aufgerufen, und die Anmeldeinformationen werden zum Erstellen eines Proxys verwendet.  
  
> [!NOTE]  
>  Diese Informationen werden bereitgestellt, damit Sie besser verstehen, was für die Ausführung von Agents im angemessenen Sicherheitskontext erforderlich ist. Sie müssen in der Regel nicht direkt mit den Anmeldeinformationen oder Proxys interagieren, die erstellt wurden.  
  
## <a name="see-also"></a>Siehe auch  
 [Replication Security Best Practices](replication-security-best-practices.md)   
 [Sicherheit und Schutz &#40;Replikation&#41;](security-and-protection-replication.md)   
 [Sichern des Momentaufnahmeordners](secure-the-snapshot-folder.md)  
  
  
