---
title: Startbildschirm des Data Quality-Clients | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.clienthome.f1
ms.assetid: 7c6ec469-bc7d-4d19-8e21-11dcf8ade108
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 318ad51d389a25905056fd08b8789bc3250383c3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48186988"
---
# <a name="data-quality-client-home-screen"></a>Startbildschirm des Data Quality-Clients
  Über diesen Bildschirm können Sie auf die Benutzeroberflächen für die drei wichtigsten [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] -Taskgruppen (DSQ) zugreifen: Wissensdatenbank-Verwaltung, Data Quality-Projekte und Verwaltung.  
  
## <a name="options"></a>Tastatur  
  
### <a name="knowledge-base-management"></a>Wissensdatenbank-Verwaltung  
 Eine DQS-Wissensdatenbank ist ein Repository mit Metadaten, die von DQS zur Verbesserung der Datenqualität verwendet werden. Diese Metadaten werden von der DQS-Plattform in einem computergestützten Wissensermittlungsprozess und vom Data Steward in einem interaktiven Domänenverwaltungsprozess erstellt.  
  
 **Neue Wissensdatenbank**  
 Erstellen Sie eine Wissensdatenbank entweder von Grund auf neu oder basierend auf den Metadaten einer vorhandenen Wissensdatenbank. Mit diesem Befehl wird eine Seite geöffnet, in der Sie die Wissensdatenbank identifizieren können, basierend auf einer vorhandenen Datenbank die gewünschte Wissensdatenbankaktivität ausführen können und anschließend die Wissensdatenbank erstellen können.  
  
 **Öffnen der Wissensdatenbank**  
 Öffnen Sie eine Wissensdatenbank, um die Domänen zu verwalten, die Wissensermittlung auszuführen oder eine Abgleichsrichtlinie erstellen zu können. Wenn Sie auf die Schaltfläche **Wissensdatenbank öffnen** klicken, wird die Seite **Öffnen der Wissensdatenbank** angezeigt, auf der eine Liste vorhandener Wissensdatenbanken mitsamt deren Eigenschaften, aktuellen Status, Wissensdatenbanken und Details zu den Domänen angezeigt wird. Wählen Sie eine Wissensdatenbank aus, und öffnen Sie sie mittels **Wissensdatenbank öffnen**.  
  
 **Zuletzt verwendete Wissensdatenbank**  
 Öffnen Sie eine bereits erstellte Wissensdatenbank aus der Liste auf dem Bildschirm. Wenn keine Sperrung vorliegt, klicken Sie mit der rechten Maustaste, und wählen Sie dann die Aktivität aus, mit der Sie die Wissensdatenbank starten möchten (Domänenverwaltung, Wissensermittlung oder Abgleichsrichtlinie).  
  
 Sie können eine gesperrte Wissensdatenbank nur dann öffnen und bearbeiten, wenn Sie sie selbst gesperrt haben. Wenn dies der Fall ist, wird die Wissensdatenbank mit dem Status geöffnet, den sie beim Schließen aufwies. Selbiges ist in Klammern angegeben. Wenn eine Wissensdatenbank gesperrt wird und Sie sie nicht gesperrt haben, können Sie sie nur schreibgeschützt öffnen.  
  
### <a name="data-quality-projects"></a>Data Quality-Projekte  
 Ein Data Quality-Projekt ist der Prozess, bei dem DQS die Datenbereinigung oder den Datenabgleich ausführt, wobei für beide eine computergestützte Datenkorrektur und eine interaktive Datenbereinigung verwendet werden.  
  
 **Neues Data Quality-Projekt**  
 Starten Sie das Projekt zum Erstellen eines neuen Projekts. Mit diesem Befehl wird eine Seite geöffnet, in der Sie das Projekt identifizieren, es einer Wissensdatenbank zuordnen, Details über die Datenbank anzeigen, die gewünschte Projektaktivität auswählen und anschließend das Projekt erstellen können.  
  
 **Data Quality-Projekt öffnen**  
 Öffnen Sie ein Projekt, um die Datenbereinigung oder den Datenabgleich auszuführen. Wenn Sie auf die Schaltfläche **Data Quality-Projekt öffnen** klicken, wird die Seite **Data Quality-Projekt öffnen** angezeigt, auf der eine Liste vorhandener Projekte mitsamt deren Eigenschaften, aktuellen Status, Wissensdatenbanken und Details zu den Domänen und Abgleichsrichtlinienregeln angezeigt wird. Wählen Sie ein Projekt aus, und öffnen Sie es mittels **Data Quality-Projekt öffnen**.  
  
 **Zuletzt verwendetes Data Quality-Projekt**  
 Wählen Sie ein bereits erstelltes Projekt aus der Liste auf dem Bildschirm aus. Sie können ein gesperrtes Projekt nur öffnen, wenn Sie es selbst gesperrt haben. Wenn dies der Fall ist, wird das Projekt mit dem Status geöffnet, den es beim Schließen aufwies. Selbiges ist in Klammern angegeben. Wenn das Projekt abgeschlossen wurde, wird es im Exportschritt der Aktivität geöffnet.  
  
### <a name="administration"></a>Verwaltung  
 Die DQS-Verwaltung ermöglicht die Überwachung, Konfiguration und Wartung von DQS.  
  
 **Aktivitätsüberwachung**  
 Zeigen Sie eine Sicht mit dem Status aller (aktuellen und vergangenen) Aktivitäten an, die sich auf den verbundenen [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]beziehen. Die überwachten Aktivitätstypen umfassen die Wissensverwaltung, ein Data Quality-Projekt und die SSIS-basierte Datenkorrektur.  
  
 **Configuration**  
 Zeigen Sie die Konfigurationseigenschaften für Verweisdatendienstkonten, (beide durch Windows Azure Marketplace und direkt zu Verweisdatendiensten) allgemeine Einstellungen (interaktive Bereinigung, Abgleich und Profilerstellung) und Einstellungen über den Protokollschweregrad an.  
  
## <a name="see-also"></a>Siehe auch  
 [DQS-Wissensdatenbanken und -Domänen](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)   
 [Data Quality-Projekte &#40;DQS&#41;](../../2014/data-quality-services/data-quality-projects-dqs.md)   
 [DQS-Verwaltung](../../2014/data-quality-services/dqs-administration.md)  
  
  
