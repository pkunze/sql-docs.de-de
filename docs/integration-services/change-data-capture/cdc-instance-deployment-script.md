---
title: CDC Instance Deployment Script | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8fa82822-ac99-48ef-a18d-f4f3a77105b4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4483851081fc87fb10c2ca6d4f1ad2087bb1c89c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47665128"
---
# <a name="cdc-instance-deployment-script"></a>CDC Instance Deployment Script
  In diesem Abschnitt wird das Dialogfeld CDC Instance Deployment Script beschrieben, in dem das Bereitstellungsskript der CDC-Instanz angezeigt wird. Dieses Skript kann verwendet werden, um die CDC-Datenbank mit ihren Artefakten auf einer anderen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz neu zu erstellen.  
  
 Nach Abschluss des Bereitstellungsskripts sollten Sie Folgendes sicherstellen:  
  
-   Das Bereitstellungsskript setzt voraus, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Zielinstanz für Oracle CDC mit der Oracle CDC Service Configuration Console oder mit dem vom Programm erstellten **prepare script** (Vorbereitungsskript) vorbereitet wurde.  
  
-   Der Teil des Skripts, der zum Aktivieren der Datenbank für CDC verwendet wird, muss von einem `sysadmin`ausgeführt werden.  
  
-   Das Skript behält das Oracle Log Mining-Kennwort nicht bei. Das Kennwort muss manuell festgelegt werden, nachdem das Skript ausgeführt und der Oracle CDC Service gestartet wurde.  
  
 Aktivieren Sie im Dialogfeld **CDC Instance Deployment Script** die folgenden Optionen.  
  
 **Speichern unter**  
 Speichert das Skript in einer Textdatei, die Sie an einem beliebigen Speicherort ablegen können. Sie können die Datei mit dem Skript auf einen beliebigen anderen Server kopieren, um es dort auszuführen.  
  
 **Kopieren**  
 Kopiert das Skript in die Zwischenablage. Sie können das Skript dann in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder einen beliebigen Texteditor einfügen, um die Skripts später auszuführen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Vorbereiten von SQL Server für CDC](../../integration-services/change-data-capture/prepare-sql-server-for-cdc.md)  
  
  
