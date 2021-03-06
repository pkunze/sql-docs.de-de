---
title: Grundlegendes zu den Analysis Services-Bereitstellungsskript | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services Deployment Wizard, scripts
- deploying [Analysis Services], scripts
- Analysis Services deployments, scripts
- scripts [Analysis Services], deployment
ms.assetid: a63ebee9-9848-48f1-82ad-64ecf2e47019
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 84bc0e699a0fb47b78b1b0d075a0ef87c8a4dcc3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099291"
---
# <a name="understanding-the-analysis-services-deployment-script"></a>Grundlegendes zum Analysis Services-Bereitstellungsskript
  Das vom [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Bereitstellungs-Assistenten erstellte XMLA-Bereitstellungsskript besteht aus zwei Abschnitten:  
  
-   Der erste Teil des Bereitstellungsskripts enthält die Befehle, die zum Erstellen, Ändern oder Löschen der entsprechenden [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Objekte in der Zieldatenbank erforderlich sind. Standardmäßig basieren die vom [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt generierten Eingabedateien auf einer inkrementellen Bereitstellung. Folglich wirkt sich das XMLA-Bereitstellungsskript nur auf Objekte aus, die geändert oder gelöscht wurden.  
  
-   Der zweite Teil des Bereitstellungsskripts enthält die Befehle, die zum Verarbeiten der Objekte erforderlich sind, die auf dem Zielserver erstellt oder geändert wurden (Option Standard verarbeiten), oder zum vollständigen Verarbeiten der Zieldatenbank. Sie können auch festlegen, dass das Bereitstellungsskript keine Verarbeitungsbefehle enthalten soll.  
  
 Das gesamte Bereitstellungsskript kann in einer einzelnen Transaktion oder in mehreren Transaktionen ausgeführt werden. Wenn das Skript in mehreren Transaktionen ausgeführt wird, wird der erste Teil des Skripts als einzelne Transaktion ausgeführt, und jedes Objekt wird in einer eigenen Transaktion verarbeitet.  
  
> [!IMPORTANT]  
>  Der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Bereitstellungs-Assistent stellt nur Objekte in einer einzelnen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank bereit. Er stellt keinerlei Objekte oder Daten auf Serverebene bereit.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen des Bereitstellungs-Assistenten für Analysis Services](running-the-analysis-services-deployment-wizard.md)   
 [Grundlegendes zu den zum Erstellen des Bereitstellungsskripts verwendeten Eingabedateien](deployment-script-files-input-used-to-create-deployment-script.md)  
  
  
