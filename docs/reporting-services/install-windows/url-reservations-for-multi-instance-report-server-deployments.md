---
title: "URL-Reservierungen für mit mehreren Instanzen Bericht Serverbereitstellungen | Microsoft Docs"
ms.custom: 
ms.date: 05/18/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- URL reservations
ms.assetid: f67c83c0-1f74-42bb-bfc1-e50c38152d3d
caps.latest.revision: 7
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: e046d1afc8cc2f774e56f70ac9448e9ba9660cbb
ms.contentlocale: de-de
ms.lasthandoff: 08/09/2017

---
# <a name="url-reservations-for-multi-instance-report-server-deployments"></a>URL-Reservierungen für Berichtsserver-Bereitstellungen mit mehreren Instanzen
  Wenn Sie mehrere Instanzen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auf demselben Computer installieren, müssen Sie überlegen, wie Sie die URL-Reservierungen für die einzelnen Instanzen definieren. Innerhalb jeder Instanz müssen Sie dem Berichtsserver-Webdienst und dem [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] mindestens jeweils eine URL-Reservierung zuweisen. Der gesamte Reservierungssatz muss in HTTP.SYS eindeutig sein.  
  
 Doppelte URLs werden bei der URL-Registrierung beim Starten des Diensts erkannt. Wenn Sie URL-Reservierungen erstellen, die nicht eindeutig sind, wird der Namenskonflikt möglicherweise erst beim Starten des Diensts erkannt. Verwenden Sie aus diesem Grund Benennungskonventionen oder Regeln, um sicherzustellen, dass alle Werte eindeutig sind.  
  
## <a name="default-naming-conventions"></a>Standard-Benennungskonventionen  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] kann innerhalb einer benannten Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert werden. Wenn Sie einen Berichtsserver innerhalb einer benannten Instanz installieren oder konfigurieren, wird der Instanzname automatisch dem virtuellen Verzeichnis in der von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] bereitgestellten Standard-URL-Reservierung hinzugefügt. Die folgende Tabelle zeigt die URL-Reservierungen für eine Standardinstanz und eine benannte Instanz.  
  
|SQL Server-Instanz|Standard-URL-Reservierung|  
|-------------------------|-----------------------------|  
|Standard (MSSQLServer)|`http://+:80/reportserver`|  
|Benannt (MynamedInstance)|`http://+:80/reportserver_MyNamedInstance`|  
  
 Wenn es sich um eine benannte Instanz handelt, enthält das virtuelle Verzeichnis den Instanznamen. Die Standardinstanz und die benannte Instanz lauschen auf demselben Port, durch die eindeutigen Namen der virtuellen Verzeichnisse wird jedoch festgelegt, an welchen Berichtsserver die jeweilige Anforderung weitergeleitet wird.  
  
 Eine Empfehlung für eine bewährte Vorgehensweise ist, den Namen des virtuellen Verzeichnisses zur Unterscheidung zwischen den Berichtsserverinstanzen zu verwenden. So wird eine eindeutige Entsprechung zwischen einer URL und der Zielinstanz definiert und sichergestellt, dass die Anwendungsnamen systemweit eindeutig sind.  
  
## <a name="custom-naming-conventions"></a>Benutzerdefinierte Benennungskonventionen  
 Die Verwendung des Instanznamens wird empfohlen, Sie können jedoch auch die URL-Syntax und Ihre eigenen Benennungskonventionen verwenden, um die Eindeutigkeitsanforderungen für URL-Reservierungen zu erfüllen. In den folgenden Beispielen werden verschiedene Ansätze zum Erstellen von eindeutigen URLs für jede Instanz veranschaulicht.  
  
|Standard-Berichtsserverinstanz (MSSQLSERVER)|ReportServer_MyNamedInstance|Eindeutigkeit|  
|----------------------------------------------------|-----------------------------------|----------------|  
|`http://+:80/reportserver`|`http://+:8888/reportserver`|Jede Instanz lauscht auf einem anderen Port.|  
|`http://www.contoso.com/reportserver`|`http://SRVR-46/reportserver`|Jede Instanz reagiert auf einen anderen Servernamen (vollqualifizierter Domänenname und Computername).|  
  
## <a name="uniqueness-requirements"></a>Eindeutigkeitsanforderungen  
 Die von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendeten zugrunde liegenden Technologien erzwingen Anforderungen für eindeutige Namen. HTTP.SYS erfordert, dass alle URLs innerhalb des Repositorys eindeutig sind. Zum Erstellen einer eindeutigen URL können Sie den Portnamen, den Hostnamen oder den Namen des virtuellen Verzeichnisses ändern. [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] erfordert, dass alle Anwendungsidentitäten innerhalb eines Prozesses eindeutig sind. Diese Anforderung wirkt sich auf die Namen virtueller Verzeichnisse aus. Sie legt fest, dass innerhalb einer Berichtsserverinstanz keine identischen Verzeichnisnamen zulässig sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren des Berichtsserver-URLs &#40; SSRS-Konfigurations-Manager &#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Konfigurieren einer URL &#40; SSRS-Konfigurations-Manager &#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)  
  
  
