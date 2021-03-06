---
title: Ausführung von Projekten und Paketen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, running
- SSIS packages, running
- packages [Integration Services], running
- SQL Server Integration Services packages, running
- executing packages [Integration Services]
- running packages [Integration Services]
- Integration Services, (See also Integration Services packages)
ms.assetid: c5fecc23-6f04-4fb2-9a29-01492ea41404
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7138207d6f612fa8ee9075b9994e9d8f4f63e552
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48158860"
---
# <a name="execution-of-projects-and-packages"></a>Ausführung von Projekten und Paketen
  Zum Ausführen eines [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakets können Sie, abhängig vom Speicherort dieser Pakete, unterschiedliche Tools verwenden. Die Tools werden in der Tabelle unten aufgeführt.  
  
 Zum Speichern eines Pakets auf dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Server verwenden Sie das Projektbereitstellungsmodell, um das Projekt auf dem Server bereitzustellen. Weitere Informationen finden Sie unter [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md).  
  
 Zum Speichern eines Pakets im SSIS-Paketspeicher, in der MSDB-Datenbank oder im Dateisystem verwenden Sie das Paketbereitstellungsmodell. Weitere Informationen finden Sie unter [Paketbereitstellung &#40;SSIS&#41;](legacy-package-deployment-ssis.md).  
  
|Tool|Pakete, die auf dem Integration Services-Server gespeichert werden|Im SSIS-Paketspeicher oder in der MSDB-Datenbank gespeicherte Pakete|Pakete, die im Dateisystem außerhalb des Speicherorts, der Teil des SSIS-Paketspeichers ist, gespeichert werden|  
|----------|-----------------------------------------------------------------|--------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|  
|**SQL Server Data Tools**|nein|nein<br /><br /> Sie können jedoch einem Projekt ein vorhandenes Paket aus dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paketspeicher hinzufügen, der die msdb-Datenbank enthält. Wenn ein vorhandenes Paket auf diese Weise dem Projekt hinzugefügt wird, wird im Dateisystem eine lokale Kopie des Pakets erstellt.|Benutzerkontensteuerung|  
|**SQL Server Management Studio, wenn eine Verbindung mit einer Instanz der Datenbank-Engine besteht, die den Server Integration Services hostet**<br /><br /> Weitere Informationen finden Sie unter [Execute Package Dialog Box](../execute-package-dialog-box.md).|Benutzerkontensteuerung|nein<br /><br /> Pakete können jedoch von diesen Speicherorten auf den Server importiert werden.|nein<br /><br /> Pakete können jedoch aus dem Dateisystem auf den Server importiert werden.|  
|**SQL Server Management Studio, wenn eine Verbindung mit dem Integration Services-Dienst besteht, der den SSIS-Paketspeicher verwaltet**|nein|Benutzerkontensteuerung|nein<br /><br /> Pakete können jedoch aus dem Dateisystem in den [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paketspeicher importiert werden.|  
|**dtexec**<br /><br /> Weitere Informationen finden Sie unter [dtexec Utility](dtexec-utility.md).|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|**dtexecui**<br /><br /> Weitere Informationen finden Sie unter [Paketausführungshilfsprogramm &#40;DtExecUI&#41; – Referenz zur Benutzeroberfläche](execute-package-utility-dtexecui-ui-reference.md).|nein|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|**SQL Server-Agent**<br /><br /> Mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Auftrag können Sie ein Paket planen.<br /><br /> Weitere Informationen finden Sie unter [SQL Server Agent Jobs for Packages](sql-server-agent-jobs-for-packages.md).|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|**Integrierte gespeicherte Prozedur**<br /><br /> Weitere Informationen finden Sie unter [catalog.start_execution &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database).|Benutzerkontensteuerung|nein|nein|  
|**Verwaltete API, mit Typen und Elementen im** <xref:Microsoft.SqlServer.Management.IntegrationServices> -Namespace|Benutzerkontensteuerung|nein|nein|  
|**Verwaltete API, mit Typen und Elementen im** <xref:Microsoft.SqlServer.Dts.Runtime> -Namespace|Gegenwärtig nicht|Benutzerkontensteuerung|Benutzerkontensteuerung|  
  
## <a name="execution-and-logging"></a>Ausführung und Protokollierung  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakete können für die Protokollierung aktiviert werden, und Sie können die Laufzeitinformationen in Protokolldateien erfassen. Weitere Informationen finden Sie unter [Integration Services-Protokollierung &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md).  
  
 Mit Vorgangsberichten können Sie [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakete überwachen, die auf dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Server bereitgestellt und ausgeführt werden. Die Berichte sind in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]verfügbar. Weitere Informationen finden Sie unter [Berichte für den Integration Services-Server](../reports-for-the-integration-services-server.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Planen eines Pakets mit dem SQL Server-Agent](../schedule-a-package-by-using-sql-server-agent.md)  
  
-   [Ausführen eines Pakets in SQL Server Data Tools](../run-a-package-in-sql-server-data-tools.md)  
  
-   [Ausführen eines Pakets auf dem SSIS-Server mit SQL Server Management Studio](../run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="see-also"></a>Siehe auch  
 [dtexec (Hilfsprogramm)](dtexec-utility.md)   
 [SQL Server-Import/Export-Assistent](../import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)  
  
  
