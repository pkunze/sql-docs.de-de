---
title: "Verwenden von Zertifikaten für einen Datenbankspiegelungs-Endpunkt (Transact-SQL) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- certificates [SQL Server], database mirroring
- authentication [SQL Server], database mirroring
- database mirroring [SQL Server], security
ms.assetid: f7c23cc2-48dc-4b78-b441-89ca29a0bd9e
caps.latest.revision: 34
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 5ece75ebe6293747d9ac677a4913bc7323615c8f
ms.contentlocale: de-de
ms.lasthandoff: 08/02/2017

---
# <a name="use-certificates-for-a-database-mirroring-endpoint-transact-sql"></a>Verwenden von Zertifikaten für einen Datenbankspiegelungs-Endpunkt (Transact-SQL)
  Um die Zertifikatsauthentifizierung für die Datenbankspiegelung für eine bestimmte Serverinstanz zu aktivieren, muss der Systemadministrator jede Serverinstanz konfigurieren, um Zertifikate sowohl für ausgehende als auch für eingehende Verbindungen zu verwenden. Ausgehende Verbindungen müssen zuerst konfiguriert werden.  
  
> [!NOTE]  
>  Alle Spiegelungsverbindungen auf einer Serverinstanz verwenden einen gemeinsamen Datenbankspiegelungsendpunkt. Sie müssen beim Erstellen dieses Endpunktes die Authentifizierungsmethode der Serverinstanz angeben. Aus diesem Grund können Sie pro Serverinstanz jeweils nur eine Art der Authentifizierung für die Datenbankspiegelung verwenden.  
  
## <a name="configuring-outbound-connections"></a>Konfigurieren ausgehender Verbindungen  
 Führen Sie die folgenden Schritte für jede Serverinstanz aus, die Sie für die Datenbankspiegelung konfigurieren:  
  
1.  Erstellen Sie einen Datenbankhauptschlüssel in der **master** -Datenbank.  
  
2.  Erstellen eines verschlüsselten Zertifikats für die Serverinstanz in der **master** -Datenbank  
  
3.  Erstellen eines Endpunktes für die Serverinstanz mithilfe ihres Zertifikats  
  
4.  Sichern des Zertifikats in einer Datei und sicheres Kopieren dieses Zertifikats zum anderen System bzw. zu den anderen Systemen  
  
 Diese Schritte müssen Sie für jeden Partner und ggf. den Zeugen ausführen.  
  
 Weitere Informationen finden Sie unter [Ermöglichen des Verwendens von Zertifikaten für ausgehende Verbindungen für einen Datenbankspiegelungs-Endpunkt &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md).  
  
## <a name="configuring-inbound-connections"></a>Konfigurieren eingehender Verbindungen  
 Führen Sie anschließend die folgenden Schritte für jeden Partner durch, den Sie für die Datenbankspiegelung konfigurieren. In der **master** -Datenbank:  
  
1.  Erstellen eines Anmeldenamens für das andere System  
  
2.  Erstellen Sie einen Benutzer für den Anmeldenamen.  
  
3.  Abrufen des Zertifikats für den Spiegelungsendpunkt der anderen Serverinstanz  
  
4.  Ordnen Sie das Zertifikat dem in Schritt 2 erstellten Benutzer zu.  
  
5.  Erteilen der CONNECT-Berechtigung für den Anmeldenamen für den entsprechenden Spiegelungsendpunkt  
  
 Falls ein Zeuge vorhanden ist, müssen Sie auch eingehende Verbindungen für diesen einrichten. Hierfür ist es erforderlich, Anmeldenamen, Benutzer und Zertifikate für den Zeugen auf beiden Partnern (und umgekehrt) einzurichten.  
  
 Weitere Informationen finden Sie unter [Ermöglichen des Verwendens von Zertifikaten für eingehende Verbindungen für einen Datenbankspiegelungs-Endpunkt &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/database-mirroring-use-certificates-for-inbound-connections.md).  
  
## <a name="security"></a>Sicherheit  
 Sofern Sie nicht garantieren können, dass Ihr Netzwerk sicher ist, wird das Verschlüsseln bei Verbindungen zur Datenbankspiegelung empfohlen. Weitere Informationen finden Sie unter [Der Datenbankspiegelungs-Endpunkt &#40;SQL Server&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md).  
  
 Verwenden Sie zum Kopieren eines Zertifikats zu einem anderen System eine sichere Kopiermethode. Seien Sie äußerst vorsichtig, um Ihre Zertifikate zu schützen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Datenbank-Hauptschlüssels](../../relational-databases/security/encryption/create-a-database-master-key.md)   
 [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-master-key-transact-sql.md)   
 [Transportsicherheit für Datenbankspiegelung und Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/database-mirroring/transport-security-database-mirroring-always-on-availability.md)   
 [Sicherheitscenter für SQL Server-Datenbankmodul und Azure SQL-Datenbank](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)   
 [Der Datenbankspiegelungs-Endpunkt &#40;SQL Server&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
  
  
