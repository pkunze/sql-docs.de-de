---
title: Verlauf der Desktop-Datenbanktreiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], history
- ODBC desktop database drivers [ODBC], history
- desktop database drivers [ODBC], history
ms.assetid: b4a2aff8-bde7-4bd5-8580-bc50f27311c8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a77aeafff6b27b2de0b947700cef1c7251cd7548
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622498"
---
# <a name="history-of-the-desktop-database-drivers"></a>Versionsgeschichte der Desktop-Datenbanktreiber
Die folgende Tabelle zeigt den Versionsverlauf für die Desktop-Datenbanktreiber.  
  
|Version|Veröffentlichungsdatum|Description|  
|-------------|------------------|-----------------|  
|1,0|August 1993|Verwendet der Abfrageprozessor SIMBA erzeugten PageAhead Software. SIMBA empfangen ODBC-Aufrufe und SQL-Anweisungen, verarbeitet diese in Microsoft Jet installierbare ISAM-Aufrufe und anschließend aufgerufen, die Microsoft Jet-ISAM-Dispatch-Ebene, um das Laden, und rufen den entsprechenden installierbaren ISAM-Treiber.|  
|2.0|Dezember 1994|Wird verwendet, mit ODBC-Version 2.0, die ODBC-Funktionalität erheblich erweitert. Die wesentliche Änderung in der Version 2.0 war, dass die Microsoft Jet-Datenbank-Engine den Abfrageprozessor SIMBA ersetzt. Die Microsoft Jet-Datenbank-Engine integriert die Desktop-Datenbanktreiber viel enger mit dem Microsoft Jet installierbare ISAM-Treiber und Microsoft Access-Technologie. Bedeutende Verbesserungen wurden:<br /><br /> -Native Unterstützung für scrollfähige Cursor.<br />-Native Unterstützung für äußere Joins, aktualisiert und heterogene Joins und Transaktionen.<br />-32-Bit-Versionen der Treiber für Microsoft Windows NT.|  
|3.0|Oktober 1995|Unterstützung für Windows 95 und Windows NT Workstation oder NT Server 3.51 wird bereitgestellt. Nur 32-Bit-Treiber wurden in dieser Version enthalten; die 16-Bit-Treiber für Windows-Version 3.1 wurden entfernt.|  
|3.5|Oktober 1996|Diese Treiber wurden Doppelbyte-Zeichensatz (DBCS)-aktiviert, wurden besser geeignet für die Verwendung mit Internet-Anwendungen als in vorherigen Versionen und die Verwendung von Datenquellennamen (DSNs) an die Datei untergebracht. Die Microsoft Access-Treiber wurde in einer RISC-Version für die Verwendung auf Alpha-Plattformen für Windows 95/98 und Windows NT 3.51 und späteren Betriebssystemen freigegeben.|  
|4.0|Spät 1998|Bietet Unterstützung für Microsoft Jet-Modul-Unicode-Format sowie die Kompatibilität für ANSI-Format von Vorgängerversionen.|  
  
> [!NOTE]  
>  Die Treiber version3.5 wurden entwickelt, mit ODBC2 arbeiten. *x*. Obwohl sie auch mit ODBC 3.0 funktionieren, unterstützen sie nicht alle ODBC 3.0-Features. Weitere Informationen zur Funktionsweise von diese Treiber mit ODBC-Version 3.0, finden Sie unter [Abwärtskompatibilität und zur Einhaltung von Standards](../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).
