---
title: "Gespeicherte Überprüfungsprozedur (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 332d3c86-4440-4f12-a6cb-ffbfbccde52c
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4c0606a05973dfbcd8e43f24898c8a9ce01d9fc8
ms.contentlocale: de-de
ms.lasthandoff: 08/02/2017

---
# <a name="validation-stored-procedure-master-data-services"></a>Gespeicherte Überprüfungsprozedur (Master Data Services)
  Überprüfen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]eine Version, um Geschäftsregeln auf alle Elemente in der Modellversion anzuwenden.  
  
 Dieses Thema erklärt, wie die gespeicherte Prozedur **mdm.udpValidateModel** verwendet wird, um Daten zu überprüfen. Wenn Sie Administrator in der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung sind, können Sie stattdessen eine Überprüfung in der Benutzeroberfläche ausführen. Weitere Informationen finden Sie unter [Validate a Version against Business Rules &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md).  
  
> [!NOTE]  
>  Wenn Sie Überprüfung vor dem Abschluss des Stagingprozesses aufrufen, werden Elemente nicht überprüft, für die das Staging noch nicht beendet ist.  
  
## <a name="example"></a>Beispiel  
  
```  
DECLARE @ModelName nVarchar(50) = 'Customer'   
DECLARE @Model_id int   
DECLARE @UserName nvarchar(50)= 'DOMAIN\user_name'   
DECLARE @User_ID int   
DECLARE @Version_ID int   
  
SET @User_ID = (SELECT ID    
                 FROM mdm.tblUser u   
                 WHERE u.UserName = @UserName)   
SET @Model_ID = (SELECT Top 1 Model_ID   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_Name = @ModelName)   
SET @Version_ID = (SELECT MAX(ID)   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_ID = @Model_ID)  
  
EXECUTE mdm.udpValidateModel @User_ID, @Model_ID, @Version_ID, 1  
  
```  
  
## <a name="parameters"></a>Parameter  
 Zu dieser Prozedur gehören die folgenden Parameter:  
  
|Parameter|Description|  
|---------------|-----------------|  
|UserID|Die Benutzer-ID.|  
|Model_ID|Die Modell-ID.|  
|Version_ID|Die Versions-ID.|  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht: Importieren von Daten aus Tabellen &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [Überprüfen einer Version anhand von Geschäftsregeln &#40; Master Data Services &#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
  