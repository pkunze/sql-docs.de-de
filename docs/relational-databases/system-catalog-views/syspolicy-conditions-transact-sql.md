---
title: Syspolicy_conditions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_conditions
- syspolicy_conditions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_conditions view
ms.assetid: af97d26c-4bd5-4b08-be51-8419e3b2832c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c0f9efbedc1f380bca66c198accae17b70cb4da2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47823108"
---
# <a name="syspolicyconditions-transact-sql"></a>syspolicy_conditions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeigt eine Zeile für jede Bedingung der richtlinienbasierten Verwaltung in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Syspolicy_conditions gehört zum Dbo-Schema in der Msdb-Datenbank. In der folgenden Tabelle werden die Spalten in der syspolicy_conditions-Sicht beschrieben.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|condition_id|**int**|Bezeichner dieser Bedingung. Jede Bedingung stellt eine Auflistung eines oder mehrerer Bedingungsausdrücke dar.|  
|NAME|**sysname**|Name der Bedingung.|  
|date_created|**datetime**|Datum und Uhrzeit der Erstellung der Bedingung.|  
|description|**nvarchar(max)**|Beschreibung der Bedingung. Die Beschreibungsspalte ist optional und kann NULL sein.|  
|created_by|**sysname**|Anmeldung, die die Bedingung erstellt hat.|  
|modified_by|**sysname**|Anmeldung, die die Bedingung zuletzt geändert hat. Ist NULL, wenn nie geändert.|  
|date_modified|**datetime**|Datum und Uhrzeit der Erstellung der Bedingung. Ist NULL, wenn nie geändert.|  
|is_name_condition|**smallint**|Gibt an, ob die Bedingung eine Benennungsbedingung ist.<br /><br /> 0 = Der Bedingungsausdruck enthält nicht die Variable @Name.<br /><br /> 1 = Der Bedingungsausdruck enthält die Variable @Name.|  
|Facet|**nvarchar(max)**|Name des Facets, auf dem die Bedingung basiert.|  
|expression|**nvarchar(max)**|Ausdruck des Facet-Status.|  
|obj_name|**sysname**|Der @Name zugewiesene Objektname, wenn der Bedingungsausdruck diese Variable enthält.|  
  
## <a name="remarks"></a>Hinweise  
 Bei der Problembehandlung in der richtlinienbasierten Verwaltung fragen Sie in der syspolicy_conditions-Sicht ab, wer die Bedingung erstellt oder zuletzt geändert hat.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Servern mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Sichten der richtlinienbasierten Verwaltung &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
