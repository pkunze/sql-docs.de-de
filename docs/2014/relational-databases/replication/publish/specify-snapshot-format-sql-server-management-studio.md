---
title: Angeben des Momentaufnahmeformats (SQL Server Management Studio) | Microsoft Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], formats
- snapshot replication [SQL Server], formats
ms.assetid: 7c95f545-731a-4743-9acb-0b325ef9b98b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fe570f8e23d933dfc1974564401069305e9a88a3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48199930"
---
# <a name="specify-snapshot-format-sql-server-management-studio"></a>Angeben des Momentaufnahmeformats (SQL Server Management Studio)
  Geben Sie das Momentaufnahmeformat auf der Seite **Momentaufnahme** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** an. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](view-and-modify-publication-properties.md).  
  
### <a name="to-specify-snapshot-format"></a>So geben Sie das Momentaufnahmeformat an  
  
1.  Wählen Sie auf der Seite **Momentaufnahme** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** die Option **Natives Format von SQL Server - alle Abonnenten müssen Server mit SQL Server sein** oder **Zeichen - erforderlich, wenn auf einem Verleger oder Abonnenten SQL Server nicht ausgeführt wird** aus.  
  
    > [!NOTE]  
    >  Sie sollten das systemeigene Format auswählen, sofern diese Veröffentlichung keine Abonnements für eine [!INCLUDE[ssEW](../../../includes/ssew-md.md)] -Datenbank und keine Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datenbank unterstützen muss.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Momentaufnahmeeigenschaften &#40;Replikationsprogrammierung mit Transact-SQL&#41;](configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Ändern von Veröffentlichungs- und Artikeleigenschaften](change-publication-and-article-properties.md)   
 [Initialisieren eines Abonnements mit einer Momentaufnahme](../initialize-a-subscription-with-a-snapshot.md)  
  
  
