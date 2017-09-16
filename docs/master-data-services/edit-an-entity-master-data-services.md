---
title: "Bearbeiten eine Entität (Master Data Services) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- entities [Master Data Services], changing name
ms.assetid: 6a5b9f14-6dfc-49d7-a771-e96461d4feae
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1364db68abbbff7ff13899180af78dc87478737d
ms.contentlocale: de-de
ms.lasthandoff: 08/02/2017

---
# <a name="edit-an-entity-master-data-services"></a>Bearbeiten einer Entität (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]können Sie eine Entität bearbeiten.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Systemverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-edit-an-entity"></a>So bearbeiten Sie eine Entität  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Wählen Sie auf der Seite **Modell verwalten** im Raster ein Modell aus, und klicken Sie dann auf **Entitäten**.  
  
3.  Wählen Sie auf der Seite **Entitäten verwalten** im Raster die Zeile für die Entität aus, die Sie ändern möchten, und klicken Sie anschließend auf **Bearbeiten**.  
  
4.  Geben Sie im Feld **Name** den aktualisierten Namen für die Entität ein.  
  
5.  Geben Sie im Feld **Beschreibung** die aktualisierte Beschreibung der Entität ein.  
  
6.  Geben Sie im Feld **Name für Stagingtabellen** den aktualisierten Namen für die Stagingtabelle ein.  
  
7.  Wählen Sie für das Feld **Transaktionsprotokolltyp** den aktualisierten Transaktionsprotokolltyp in der Dropdownliste aus.  
  
     Weitere Informationen finden Sie unter [Ändern des Transaktionsprotokolltyps von Entitäten &#40;Master Data Services&#41;](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md).  
  
8.  Aktivieren oder deaktivieren Sie das Kontrollkästchen **Codewerte automatisch erstellen**.  
  
     Weitere Informationen finden Sie unter [Automatische Codeerstellung &#40;Master Data Services&#41;](../master-data-services/automatic-code-creation-master-data-services.md)  
  
9. Aktivieren oder deaktivieren Sie das Kontrollkästchen **Datenkomprimierung aktivieren**. Die Zeilenkomprimierung ist standardmäßig aktiviert.  
  
     Weitere Informationen finden Sie unter [Datenkomprimierung](../relational-databases/data-compression/data-compression.md).  
  
## <a name="status"></a>Status  
 Die Statusspalte im Raster zeigt den Status des Vorgangs für die Entität. Wenn Sie auf **Entität speichern**klicken, wird das folgende Bild angezeigt, das angibt, dass die Entität aktualisiert wird.  
  
 ![Symbol für Status aktualisieren](../master-data-services/media/mds-statusicon-updating.png "Symbol für Status aktualisieren")  
  
 Wenn beim Erstellen oder Bearbeiten einer Entität Fehler auftreten, wird das folgende Bild angezeigt.  
  
 ![Symbol für Fehlerstatus](../master-data-services/media/mds-statusicon-error.png "Symbol für Fehlerstatus")  
  
 Falls der Status "OK" lautet, wird das folgende Bild angezeigt.  
  
 ![Symbol für Status OK](../master-data-services/media/mds-statusicon-ok.png "Symbol für Status OK")  
  
## <a name="see-also"></a>Siehe auch  
 [Explizite Hierarchien &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)   
 [Löschen einer Entität &#40; Master Data Services &#41;](../master-data-services/delete-an-entity-master-data-services.md)   
 [Entitäten &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
  