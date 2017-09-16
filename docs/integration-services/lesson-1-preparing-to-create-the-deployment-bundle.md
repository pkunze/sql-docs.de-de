---
title: 'Lektion 1: Vorbereiten der Erstellung des Bereitstellungspakets | Microsoft Docs'
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: b6fe283c-9856-4ba1-a497-e3912424fd18
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0850bf9b55f3960736d45b1730f25f6c96c667a9
ms.contentlocale: de-de
ms.lasthandoff: 08/03/2017

---
# <a name="lesson-1-preparing-to-create-the-deployment-bundle"></a>Lektion 1: Vorbereiten der Erstellung des Bereitstellungspakets
In dieser Lektion erstellen Sie die Arbeitsordner und Umgebungsvariablen zur Unterstützung des Lernprogramms. Sie erstellen weiterhin ein [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt, fügen diesem mehrere Pakete und die zugehörigen Unterstützungsdateien hinzu und implementieren Konfigurationen in Paketen.  
  
Von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] werden Pakete auf Projektbasis bereitgestellt. Deshalb müssen Sie als ersten Schritt beim Erstellen des Bereitstellungspakets alle Pakete und Paketabhängigkeiten in einem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt sammeln. Oft ist es nützlich, weitere Informationen in die bereitgestellten Pakete einzufügen: Sie fügen z. B. dem Projekt auch eine Infodatei hinzu, die eine grundlegende Dokumentation für diese Gruppe von Paketen enthält.  
  
Nachdem Sie die Pakete und Dateien hinzugefügt haben, fügen Sie den Paketen Konfigurationen hinzu, von denen noch keine Konfigurationen verwendet werden. Durch die Konfigurationen werden die Eigenschaften von Paketen und Paketobjekten zur Laufzeit aktualisiert. In einer späteren Lektion ändern Sie die Werte dieser Konfigurationen während der Paketbereitstellung, um die Pakete in der Umgebung zu unterstützen, in der sie bereitgestellt werden.  
  
Nachdem Sie die Konfigurationen hinzugefügt haben, sollten Sie die Pakete im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer, dem grafischen [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Tool zum Erstellen von ETL-Paketen, öffnen und die Eigenschaften der Pakete und Paketelemente sowie die Paketkonfigurationen untersuchen, um die Probleme besser zu verstehen, die bei der Bereitstellung berücksichtigt werden müssen. Zum Beispiel werden durch eines der Pakete Daten aus Textdateien extrahiert, sodass der Speicherort der Datendateien aktualisiert werden muss, damit die bereitgestellten Pakete erfolgreich ausgeführt werden.  
  
**Geschätzte Zeit zum Bearbeiten dieser Lektion:** 1 Stunde  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
Diese Lektion enthält die folgenden Aufgaben:  
  
-   [Schritt 1: Erstellen von Arbeitsordnern und Umgebungsvariablen](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
-   [Schritt 2: Erstellen des Bereitstellungsprojekts](../integration-services/lesson-1-2-creating-the-deployment-project.md)  
  
-   [Schritt 3: Hinzufügen von Paketen und weiteren Dateien](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
-   [Schritt 4: Hinzufügen von Paketkonfigurationen](../integration-services/lesson-1-4-adding-package-configurations.md)  
  
-   [Schritt 5: Testen des aktualisierten Pakets](../integration-services/lesson-1-5-testing-the-updated-packages.md)  
  
## <a name="start-the-lesson"></a>Lektion beginnen  
[Schritt 1: Erstellen von Arbeitsordnern und Umgebungsvariablen](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
  
  
