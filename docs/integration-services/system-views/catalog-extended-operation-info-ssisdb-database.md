---
title: catalog.extended_operation_info (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: db299b45-557d-4c62-8e14-355cdb051f63
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 360c51b7f1accd1c21b2026d8ae33dba463db72d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47747158"
---
# <a name="catalogextendedoperationinfo-ssisdb-database"></a>catalog.extended_operation_info (SSISDB-Datenbank)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Zeigt erweiterte Informationen für alle Vorgänge im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Katalog an.  
  
|Spaltenname|Datentyp|und Beschreibung|  
|-----------------|---------------|-----------------|  
|info_id|**bigint**|Der eindeutige Bezeichner (ID) der erweiterten Informationen.|  
|operation_id|**bigint**|Die eindeutige ID des Vorgangs, der den erweiterten Informationen entspricht.|  
|object_name|**nvarchar(260)**|Der Name des Objekts.|  
|object_type|**smallint**|Der Typ des von dem Vorgang betroffenen Objekts. Bei dem Objekt kann es sich um einen Ordner (`10`), ein Projekt (`20`), ein Paket (`30`), eine Umgebung (`40`) oder eine Instanz der Ausführung (`50`) handeln.|  
|reference_id|**bigint**|Die eindeutige ID des Verweises, der im Vorgang verwendet wird.|  
|status|**int**|Der Status des Vorgangs. Die möglichen Werte lauten "erstellt" (`1`), "wird ausgeführt" (`2`), "abgebrochen" (`3`), "fehlerhaft" (`4`), "ausstehend" (`5`), "unerwartet beendet" (`6`), "erfolgreich" (`7`), "wird beendet" (`8`) und "abgeschlossen" (`9`).|  
|start_time|**datetimeoffset(7)**|Datum und Uhrzeit für das Starten des Vorgangs.|  
|end_time|**datetimeoffset(7)**|Datum und Uhrzeit für das Beenden des Vorgangs.|  
  
## <a name="remarks"></a>Remarks  
 Ein einzelner Vorgang kann über mehrere Zeilen mit erweiterten Informationen verfügen.  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung für den Vorgang  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
> [!NOTE]  
>  Wenn Sie über die Berechtigung verfügen, einen Vorgang auf dem Server auszuführen, verfügen Sie auch über die Berechtigung, Informationen zu dem Vorgang anzuzeigen. Sicherheit auf Zeilenebene wird erzwungen. Es werden nur Zeilen angezeigt, zu deren Anzeige Sie berechtigt sind.  
  
  
