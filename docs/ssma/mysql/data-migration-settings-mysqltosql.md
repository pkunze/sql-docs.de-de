---
title: Daten-Migrationseinstellungen (MySQLToSQL) | Microsoft Docs
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9c396df4-5676-4f32-9c57-70d4f15f9b7a
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 10658cfa7c181836aa823df7ff2fdb963ebdc795
ms.contentlocale: de-de
ms.lasthandoff: 08/02/2017

---
# <a name="data-migration-settings-mysqltosql"></a>Daten-Migrationseinstellungen (MySQLToSQL)
  
## <a name="data-migration-settings"></a>Einstellungen für die Migration von Daten  
**Einstellungen für die Migration von Daten** ermöglicht es dem Benutzer, benutzerdefinierte Abfragen für die Datenmigration zu schreiben.  
  
-   Diese Registerkarte ist verfügbar, wenn **erweiterte Optionen für die Migration von Daten** festgelegt ist, um **anzeigen** und wird ausgeblendet, wenn die Einstellung, um festgelegt ist **ausblenden** in den Projekteinstellungen. Weitere Informationen zu Projekteinstellungen für die Migration, finden Sie unter [Projekteinstellungen (Migration)](http://msdn.microsoft.com/en-us/2a3cba9e-cd54-4a8b-b858-8fc4cf2580d9) .  
  
-   Analysieren von benutzerdefinierten SQL-Anweisungen in implementiert **migrationseinstellungen Daten** Table-Knoten auf der Registerkarte.  
  
-   Es folgen zwei Kontrollkästchen Dialogfeldern, die in der **Daten Migrationseinstellungen** begrenzt.:  
  
    1.  Schneiden Sie SQL Server-Tabelle  
  
    2.  Verwenden Sie benutzerdefinierte auswählen  
  
1.  **Schneiden Sie die SQL Server-Tabelle:**  
     Diese Option ermöglicht dem Benutzer, eine klare Sicht der migrierten Daten an die Zieldatenbank haben.  
  
    -   Standardmäßig wird dieses Textfeld überprüft.  
  
    -   Wenn dieses Textfeld deaktiviert ist, werden die Daten, die migriert werden an die vorhandenen Daten auf der Zieldatenbank hinzugefügt werden.  
  
2.  **Verwenden Sie benutzerdefinierte auswählen:**  
     Diese Option ermöglicht dem Benutzer zum Ändern der **wählen** Anweisung vorhanden (**wählen** Anweisung ermöglicht den Benutzern zur Auswahl der Daten in die Zieldatenbank angezeigt werden).  
  
    1.  Dieses Textfeld ist standardmäßig deaktiviert.  
  
    2.  Wenn dieses Textfeld aktiviert ist, ermöglicht Benutzern das Ändern der **wählen** Anweisung vorhanden.  
  
Es begrenzt sind zwei Schaltflächen vorhanden.:  
  
-   **Übernehmen:** klicken Sie auf **übernehmen** zum Anwenden der Einstellungen, die geändert wurden.  
  
-   **"Abbrechen":** klicken Sie auf **"Abbrechen"** vorhanden wiederhergestellt, bevor die Änderungen wurden vorgenommen wird.  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von MySQL-Daten in SQL Server-oder SQL Azure](http://msdn.microsoft.com/en-us/a6a7f4d6-68aa-4a38-93bf-53eba0d7dc82)  
  
