---
title: Aktualisieren Sie aus der Datenbank (DB2ToSQL) | Microsoft Docs
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
ms.assetid: 613a8368-b372-443f-8252-fb6dc31a003d
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 5c0d2d3ad83249c4e438e01a31a41d9e8e226ce8
ms.contentlocale: de-de
ms.lasthandoff: 08/02/2017

---
# <a name="refresh-from-database-db2tosql"></a>Aktualisieren Sie aus der Datenbank (DB2ToSQL)
Die **aus der Datenbank aktualisieren** Dialogfeld können Sie auswählen, welche Objekte von der DB2-Datenbank zu aktualisieren. Zeilen, die Sie im Dialogfeld sind farblich codiert, basierend auf dem Status der Metadaten:  
  
-   Wenn die Metadaten des Objekts lokal und in der DB2-Datenbank geändert wurde, ist die Zeile blau.  
  
-   Wenn die Objektmetadaten in der DB2-Datenbank jedoch nicht in SSMA geändert wurde, ist die Zeile gelb.  
  
-   Wenn die Metadaten des Objekts wurde lokal geändert, aber nicht in der DB2-Datenbank, die Zeile grün ist.  
  
-   Wenn das Objekt in der DB2-Datenbank neu ist, ist die Zeile rosa.  
  
Sie können angeben, die Einstellungen der Standardrichtlinie Objekt aktualisieren in der **Projekteinstellungen** (Dialogfeld). Weitere Informationen finden Sie unter [Projekteinstellungen &#40; Synchronisierung &#41; &#40; DB2ToSQL &#41; ](../../ssma/db2/project-settings-synchronization-db2tosql.md).  
  
Für den Zugriff auf die **aus der Datenbank aktualisieren** mit der rechten Maustaste ein Objekt in DB2-Metadaten-Explorer, und klicken Sie im Dialogfeld **aus der Datenbank aktualisieren**.  
  
## <a name="options"></a>enthalten  
**Reduzieren (-)**  
Reduzieren Sie alle Objektgruppen, um einzelne Objekte auszublenden.  
  
**Erweitern (+)**  
Erweitern Sie alle Objektgruppen, um einzelne Objekte anzuzeigen.  
  
**Gleich Objekte ein-/ausblenden**  
Objekte aus der Liste wird ausgeblendet, wenn die Objektmetadaten in der DB2-Datenbank und in SSMA ist.  
  
**Aktualisieren Sie aus der Datenbank (Pfeil)**  
Verwenden Sie die Pfeiltaste klicken, um anzugeben, dass die Metadaten für die ausgewählten Objekte in SSMA aktualisiert werden sollen.  
  
**Führen Sie aus der Datenbank nicht aktualisiert werden (X-Schaltfläche)**  
Verwenden Sie die Schaltfläche "X", um anzugeben, dass die Metadaten für die ausgewählten Objekte in SSMA nicht aktualisiert werden sollten.  
  
**Legende**  
Zeigt eine **Legende** (Dialogfeld). Die Legende enthält die Zuordnung zwischen Zeilenfarben und Metadaten-Status.  
  
Beibehalten der **Legende** Dialogfeld auf der Basis von der **aus der Datenbank aktualisieren** wählen Sie im Dialogfeld die **im Vordergrund anzeigen** Kontrollkästchen.  
  
