---
title: PowerShell-Cmdlets für SharePoint-Modus von Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 7835bc97-2827-4215-b0dd-52f692ce5e02
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2427b5d40c0e088b50965ac30d891f493bdde99f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227990"
---
# <a name="powershell-cmdlets-for-reporting-services-sharepoint-mode"></a>PowerShell-Cmdlets für SharePoint-Modus von Reporting Services
  Bei der Installation von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im SharePoint-Modus werden auch PowerShell-Cmdlets installiert, die Unterstützung für Berichtsserver im SharePoint-Modus bieten. Die Cmdlets decken drei Funktionalitätskategorien ab.  
  
-   Installation von der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] gemeinsamer SharePoint-Diensts und -Proxys.  
  
-   Bereitstellung und Verwaltung von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -dienstanwendungen und zugeordneten Proxys.  
  
-   Verwaltung von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Funktionen, z. B. Erweiterungen und Verschlüsselungsschlüssel.  
  
||  
|-|  
|[!INCLUDE[applies](../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im SharePoint-Modus|  
  
 **Dieses Thema enthält Folgendes:**  
  
-   [Cmdlet-Zusammenfassung](#bkmk_cmdlet_sum)  
  
-   [Shared Service- und Proxy-Cmdlets](#bkmk_sharedservice_cmdlets)  
  
-   [Dienstanwendungs- und Proxy-Cmdlets](#bkmk_serviceapp_cmdlets)  
  
-   [Benutzerdefinierte Reporting Services-Funktionalitäts-Cmdlets](#bkmk_ssrsfeatures_cmdlets)  
  
-   [Einfache Beispiele](#bkmk_basic_samples)  
  
-   [Ausführliche Beispiele](#bkmk_detailedsamples)  
  
    -   [Erstellen eines Reporting Services-dienstanwendung und -Proxys](#bkmk_example_create_service_application)  
  
    -   [Überprüfen Sie, und Aktualisieren einer Reporting Services-übermittlungserweiterung](#bkmk_example_delivery_extension)  
  
    -   [Abrufen und Festlegen von Eigenschaften der Reporting-Anwendungsdatenbank, z. B. Timeout der Datenbank](#bkmk_example_db_properties)  
  
    -   [Auflisten der reporting services-datenerweiterungen – SharePoint-Modus](#bkmk_example_list_data_extensions)  
  
    -   [Ändern und Auflisten von abonnementbesitzern](#bkmk_change_subscription_owner)  
  
##  <a name="bkmk_cmdlet_sum"></a> Cmdlet-Zusammenfassung  
 Um die Cmdlets auszuführen, müssen Sie die SharePoint-Verwaltungsshell öffnen. Sie können auch den Editor für grafische Benutzeroberflächen **Windows PowerShell Integrated Scripting Environment (ISE)** verwenden, der in Microsoft Windows enthalten ist. Weitere Informationen finden Sie unter [Starten von Windows PowerShell unter Windows Server](http://technet.microsoft.com/library/hh847814.aspx) (http://technet.microsoft.com/library/hh847814.aspx). In den folgenden Cmdlet-Zusammenfassungen verweisen die Verweise auf die Dienstanwendung "databases" auf sämtliche mit einer [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienstanwendung erstellten und von ihr verwendeten Datenbanken. Dies schließt die Konfigurations- und Warnungsdatenbanken sowie temporären Datenbanken ein.  
  
 Wenn Sie bei der Eingabe der PowerShell-Beispiele eine Fehlermeldung mit etwa folgendem Wortlaut sehen:  
  
-   Install-SPRSService: Die Benennung 'Install-SPRSService' wurde nicht als  
    Name eines Cmdlets, einer Funktion, einer Skriptdatei oder eines ausführbaren Programms erkannt. Überprüfen Sie die Schreibweise des Namens, oder ob der Pfad enthalten und korrekt ist, und wiederholen Sie den Vorgang.  
  
 Eines der folgenden Probleme tritt auf:  
  
-   [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Modus nicht installiert ist und daher die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Cmdlets nicht installiert sind.  
  
-   Sie haben den PowerShell-Befehl in Windows PowerShell oder Windows PowerShell ISE statt in der SharePoint-Verwaltungsshell ausgeführt. Verwenden Sie die SharePoint-Verwaltungsshell, oder fügen Sie dem Windows PowerShell-Fenster mithilfe des folgenden Befehls das SharePoint-Snap-In hinzu:  
  
    ```  
    Add-PSSnapin Microsoft.SharePoint.PowerShell  
    ```  
  
 Weitere Informationen finden Sie unter [mithilfe von Windows PowerShell zur Verwaltung von SharePoint 2013](http://technet.microsoft.com/library/ee806878.aspx) (http://technet.microsoft.com/library/ee806878.aspx).  
  
#### <a name="to-open-the-sharepoint-management-shell-and-run-cmdlets"></a>So öffnen Sie die SharePoint-Verwaltungsshell und führen Cmdlets aus  
  
1.  Klicken Sie auf die Schaltfläche **Start** .  
  
2.  Klicken Sie auf die Gruppe **Microsoft SharePoint-Produkte** .  
  
3.  Klicken Sie auf **SharePoint-Verwaltungsshell**.  
  
 Um die Befehlszeilenhilfe für ein Cmdlet anzuzeigen, verwenden Sie in der PowerShell-Eingabeaufforderung den PowerShell-Befehl "Get-Help". Zum Beispiel:  
  
 `Get-Help Get-SPRSServiceApplicationServers`  
  
###  <a name="bkmk_sharedservice_cmdlets"></a> Shared Service- und Proxy-Cmdlets  
 Die folgende Tabelle enthält die PowerShell-Cmdlets für den gemeinsamen SharePoint-Dienst für [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
|Cmdlet|Description|  
|------------|-----------------|  
|Install-SPRSService|Installiert und registriert bzw. deinstalliert den gemeinsamen [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Dienst. Dies kann nur auf dem Computer erfolgen, auf dem SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im SharePoint-Modus installiert ist. Für die Installation sind zwei Vorgänge möglich:<br /><br /> (1) die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Dienst in der Farm installiert ist.<br /><br /> (2) der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienstinstanz wird auf dem aktuellen Computer installiert.<br /><br /> Für die Deinstallation sind zwei Vorgänge möglich:<br />(1) die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienst wird auf dem aktuellen Computer deinstalliert.<br />(2) der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienst wird aus der Farm deinstalliert.<br /><br /> <br /><br /> Hinweis: Wenn andere Computer in der Farm, die die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienst installiert ist, oder wenn immer noch [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] dienstanwendungen, die in der Farm ausgeführt werden, es wird eine Warnmeldung angezeigt.|  
|Install-SPRSServiceProxy|Installiert und registriert bzw. deinstalliert den Reporting Services-Dienstproxy in der SharePoint-Farm.|  
|Get-SPRSProxyUrl|Ruft die URL(s) für den Zugriff auf die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Service.|  
|Get-SPRSServiceApplicationServers|Ruft alle Server in der lokalen SharePoint-Farm ab, die eine Installation des gemeinsamen Diensts für [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] enthalten. Dieses Cmdlet ist hilfreich für [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Upgrades, um die Server zu ermitteln, auf denen der freigegebene Dienst ausgeführt wird und die folglich aktualisiert werden müssen.|  
  
###  <a name="bkmk_serviceapp_cmdlets"></a> Dienstanwendungs- und Proxy-Cmdlets  
 Die folgende Tabelle enthält die PowerShell-Cmdlets für [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienstanwendungen und ihre zugeordneten Proxys.  
  
|Cmdlet|Description|  
|------------|-----------------|  
|Get-SPRSServiceApplication|Ruft mindestens ein [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Dienstanwendungsobjekt ab.|  
|New-SPRSServiceApplication|Erstellen Sie eine neue Reporting Services-Dienstanwendung und zugeordnete Datenbanken.<br /><br /> LogonType-Parameter: Gibt an, ob der Berichtsserver das SSRS-Anwendungspoolkonto oder einen SQL Server-Anmeldenamen für den Zugriff auf die Berichtsserver-Datenbank verwendet. Folgende Werte sind möglich:<br /><br /> 0 Windows-Authentifizierung<br /><br /> 1 SQL Server<br /><br /> 2 Anwendungspoolkonto (Standard)|  
|Remove-SPRSServiceApplication|Entfernt die angegebene Reporting Services-Dienstanwendung. Dadurch werden auch die zugeordneten Datenbanken entfernt.|  
|Set-SPRSServiceApplication|Bearbeitet die Eigenschaften einer vorhandenen Reporting Services-Dienstanwendung.|  
|New-SPRSServiceApplicationProxy|Erstellt einen neuen Proxy für die Reporting Services-Dienstanwendung.|  
|Get-SPRSServiceApplicationProxy|Ruft eine oder mehrere [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienstanwendungsproxy.|  
|Dismount-SPRSDatabase|Hebt die Einbindung der Dienstanwendungsdatenbank für eine [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Dienstanwendung auf.|  
|Remove-SPRSDatabase|Entfernt die dienstanwendungs-Datenbanken für eine [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -dienstanwendung.|  
|Set-SPRSDatabase|Legt die Eigenschaften der einer [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Dienstanwendung zugeordneten Datenbanken fest.|  
|Mount-SPRSDatabase|Bindet Datenbanken für eine [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -dienstanwendung.|  
|New-SPRSDatabase|Erstellen Sie neue dienstanwendungs-Datenbanken für die angegebene [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -dienstanwendung.|  
|Get-SPRSDatabaseCreationScript|Gibt für eine [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Dienstanwendung das Datenbankerstellungsskript auf dem Bildschirm aus. Sie können dann das Skript in SQL Server Management Studio ausführen.|  
|Get-SPRSDatabase|Ruft mindestens eine [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Dienstanwendungsdatenbank ab. Rufen Sie über den Befehl die ID der Dienstanwendungsdatenbank ab, damit Sie anhand des Set-SPRSDatabase-Cmdlets Eigenschaften ändern können, beispielsweise das `querytimeout`. Sehen Sie sich das Beispiel unter dem Thema [Abrufen und Festlegen von Eigenschaften der Reporting Services-Anwendungsdatenbank, z. B. Timeout der Datenbank](#bkmk_example_db_properties).|  
|Get-SPRSDatabaseRightsScript|Gibt das Datenbankrechte-Skript zum Bildschirm für die ein [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -dienstanwendung. Es fordert die Eingabe des gewünschten Benutzers und der Datenbank und gibt dann Transact-SQL zurück, das zum Ändern von Berechtigungen ausgeführt werden kann. Sie können dann dieses Skript in SQL Server Management Studio ausführen.|  
|Get-SPRSDatabaseUpgradeScript|Gibt ein Datenbankupgradeskript auf dem Bildschirm aus. Das Skript führt ein Upgrade der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienstanwendungsdatenbanken auf die Datenbankversion der aktuellen [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Installation durch.|  
  
###  <a name="bkmk_ssrsfeatures_cmdlets"></a> Benutzerdefinierte Reporting Services-Funktionalitäts-Cmdlets  
  
|Cmdlet|Description|  
|------------|-----------------|  
|Update-SPRSEncryptionKey|Aktualisiert den Verschlüsselungsschlüssel für die angegebene Reporting Services-Dienstanwendung und verschlüsselt die Daten erneut.|  
|Restore-SPRSEncryptionKey|Stellt einen zuvor gesicherten Verschlüsselungsschlüssel für eine Reporting Services-Dienstanwendung wieder her.|  
|Remove-SPRSEncryptedData|Löscht die verschlüsselten Daten für die angegebene Reporting Services-Dienstanwendung.|  
|Backup-SPRSEncryptionKey|Sichert den Verschlüsselungsschlüssel für die angegebene Reporting Services-Dienstanwendung.|  
|New-SPRSExtension|Registriert eine neue Erweiterung bei einer Reporting Services-Dienstanwendung.|  
|Set-SPRSExtension|Legt die Eigenschaften einer vorhandenen Reporting Services-Erweiterung fest.|  
|Remove-SPRSExtension|Entfernt eine Erweiterung aus einer Reporting Services-Dienstanwendung.|  
|Get-SPRSExtension|Ruft eine oder mehrere [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Erweiterungen für eine [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -dienstanwendung.<br /><br /> Gültige Werte sind:<br /><br /> **Übermittlung**<br /><br /> **DeliveryUI**<br /><br /> **Render**<br /><br /> **Data**<br /><br /> **Security**<br /><br /> **Authentifizierung**<br /><br /> **EventProcessing**<br /><br /> **Berichtselemente**<br /><br /> **Designer**<br /><br /> **ReportItemDesigner**<br /><br /> **ReportItemConverter**<br /><br /> **ReportDefinitionCustomization**|  
|Get-SPRSSite|Ruft die SharePoint-Websites abhängig davon ab, ob die Funktion "ReportingService" aktiviert ist. Standardmäßig werden Websites zurückgegeben, für die die Funktion "ReportingService" aktiviert ist.|  
  
##  <a name="bkmk_basic_samples"></a> Einfache Beispiele  
 Gibt eine Liste von Cmdlets zurück, die "SPRS" im Namen enthalten. Dadurch werden die vollständige Liste der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Cmdlets.  
  
```  
Get-command –noun *SPRS*  
```  
  
 Alternativ erfolgt die Weiterleitung an eine Textdatei namens "commandlist.txt" mit genaueren Details.  
  
```  
Get-command -noun *SPRS* | Select name, definition | Format-List | Out-File c:\commandlist.txt  
```  
  
 Installieren Sie den [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Dienst und -Dienstproxy.  
  
```  
Install-SPRSService  
```  
  
```  
Install-SPRSServiceProxy  
```  
  
 Starten Sie den [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Service  
  
```  
get-spserviceinstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
```  
  
 Geben Sie den folgenden Befehl in der SharePoint-Verwaltungsshell ein, um eine gefilterte Zeilenliste aus der Protokolldatei abzurufen. Durch den Befehl werden Zeilen herausgefiltert, die "ssrscustomactionerror" enthalten. Dieses Beispiel bezieht sich auf die Protokolldatei, die bei der Installation von "rssharepoint.msi" erstellt wurde.  
  
```  
Get-content -path C:\Users\testuser\AppData\Local\Temp\rs_sp_0.log | select-string "ssrscustomactionerror"  
```  
  
##  <a name="bkmk_detailedsamples"></a> Ausführliche Beispiele  
 Zusätzlich zu den folgenden Beispielen finden Sie weitere Beispiele im Abschnitt "Windows PowerShell-Skript" im Thema [Windows PowerShell script for Steps 1–4](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md#bkmk_full_script).  
  
###  <a name="bkmk_example_create_service_application"></a> Erstellen eines Reporting Services-dienstanwendung und -Proxys  
 Dieses Beispielskript führt die folgenden Tasks aus:  
  
1.  Erstellt eine Reporting Services-Dienstanwendung und einen entsprechenden Proxy. Das Skript geht davon aus, dass der Anwendungspool "Mein Anwendungspool" bereits vorhanden ist.  
  
2.  Hinzufügen des Proxys zur Standardproxygruppe  
  
3.  Gewähren Sie der Dienstanwendung Zugriff auf die Inhaltsdatenbank der Webanwendung (Port 80). Das Skript geht davon aus, Website "http://sitename" ist bereits vorhanden.  
  
```  
# Create service application and service application proxy  
$appPool = Get-SPServiceApplicationPool “My App Pool”  
$serviceApp = New-SPRSServiceApplication “My RS Service App” –ApplicationPool $appPool  
$serviceAppProxy = New-SPRSServiceApplicationProxy –Name “My RS Service App Proxy” –ServiceApplication $serviceApp  
  
# Add service application proxy to default proxy group.  Any web application that uses the default proxy group will now be able to use this service application.  
Get-SPServiceApplicationProxyGroup –default | Add-SPServiceApplicationProxyGroupMember –Member $serviceAppProxy  
  
# Grant application pool account access to the port 80 web application’s content database.  
$webApp = Get-SPWebApplication “http://sitename”  
$appPoolAccountName = $appPool.ProcessAccount.LookupName()  
$webApp.GrantAccessToProcessIdentity($appPoolAccountName)  
  
```  
  
###  <a name="bkmk_example_delivery_extension"></a> Überprüfen Sie, und Aktualisieren einer Reporting Services-übermittlungserweiterung  
 Das folgende PowerShell-Skript-Beispiel aktualisiert die Konfiguration der Berichtsserver-E-Mail-Übermittlungserweiterung für die Dienstanwendung mit dem Namen `My RS Service App`. Aktualisieren Sie die Werte für den SMTP-Server (`<email server name>`) und für den E-Mail-Absenderalias „FROM“ (`<your FROM email address>`).  
  
```  
$app=get-sprsserviceapplication -Name "My RS Service App"  
$emailCfg = Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml   
$emailXml = [xml]$emailCfg   
$emailXml.SelectSingleNode("//SMTPServer").InnerText = “<email server name>”  
$emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
$emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
$emailXml.SelectSingleNode("//From").InnerText = '<your FROM email address>'  
Set-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
```  
  
 Wenn Sie im oben genannten Beispiel den genauen Namen der Dienstanwendung nicht kennen, besteht die Möglichkeit, die erste Anweisung umzuschreiben, um die Dienstanwendung auf Grundlage einer Suche nach dem Teilnamen abzurufen. Zum Beispiel:  
  
```  
$app=get-sprsserviceapplication | where {$_.name -like " ssrs_testapp *"}  
```  
  
 Das folgende Skript gibt die aktuellen Konfigurationswerte für die Berichtsserver-E-Mail-Übermittlungserweiterung der Dienstanwendung namens "Reporting Services-Anwendung" zurück. Im ersten Schritt wird der Wert der Variablen $app auf das Objekt der Dienstanwendung mit dem Namen "Meine RS-Dienstanwendung" festgelegt.  
  
 Die zweite Anweisung ruft die Übermittlungserweiterung "Berichtsserver-E-Mail" für das Dienstanwendungsobjekt in der Variablen $app ab und wählt configurationXML aus.  
  
```  
$app=get-sprsserviceapplication –Name "Reporting Services Application"  
Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml  
```  
  
 Sie können die beiden oben stehenden Anweisungen auch in einer Anweisung zusammenfassen:  
  
```  
get-sprsserviceapplication –Name "Reporting Services Application" | Get-SPRSExtension -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml  
```  
  
###  <a name="bkmk_example_db_properties"></a> Abrufen und Festlegen von Eigenschaften der Reporting-Anwendungsdatenbank, z. B. Timeout der Datenbank  
 Mit dem folgenden Beispiel wird eine Liste von Datenbanken und Eigenschaften zurückgegeben, sodass Sie die Datenbank-GUID (ID) bestimmen können, die Sie anschließend zum Festlegen des Befehls angeben. Eine vollständige Liste der Eigenschaften erhalten Sie anhand von `Get-SPRSDatabase | format-list`.  
  
```  
get-SPRSDatabase | select id, querytimeout,connectiontimeout, status, server, ServiceInstance   
```  
  
 Unten ist ein Beispiel für die Ausgabe angegeben. Bestimmen Sie die ID für die zu ändernde Datenbank und verwenden Sie die ID im SET-Cmdlet.  
  
-   `Id                : 56f8d1bc-cb04-44cf-bd41-a873643c5a14`  
  
     `QueryTimeout      : 120`  
  
     `ConnectionTimeout : 15`  
  
     `Status            : Online`  
  
     `Server            : SPServer Name=uetestb01`  
  
     `ServiceInstance   : SPDatabaseServiceInstance`  
  
```  
Set-SPRSDatabase –identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 -QueryTimeout 300  
```  
  
 Um zu überprüfen, ob der Wert festgelegt ist, führen Sie das GET-Cmdlet erneut aus.  
  
```  
Get-SPRSDatabase –identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 | select id, querytimeout,connectiontimeout, status, server, ServiceInstance  
```  
  
###  <a name="bkmk_example_list_data_extensions"></a> Auflisten der reporting services-datenerweiterungen – SharePoint-Modus  
 Das folgende Beispiel durchläuft alle [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienstanwendungen und listet aktuelle Datenerweiterungen für diese auf.  
  
```  
$apps = Get-SPRSServiceApplication  
foreach ($app in $apps)   
{  
Write-host -ForegroundColor "yellow" Service App Name $app.Name  
Get-SPRSExtension -identity $app -ExtensionType “Data” | select name,extensiontype | Format-Table -AutoSize  
}  
```  
  
 **Beispielausgabe:**  
  
-   `Name           ExtensionType`  
  
     `----           -------------`  
  
     `SQL                     Data`  
  
     `SQLAZURE                Data`  
  
     `SQLPDW                  Data`  
  
     `OLEDB                   Data`  
  
     `OLEDB-MD                Data`  
  
     `ORACLE                  Data`  
  
     `ODBC                    Data`  
  
     `XML                     Data`  
  
     `SHAREPOINTLIST          Data`  
  
###  <a name="bkmk_change_subscription_owner"></a> Ändern und Auflisten von abonnementbesitzern  
 Siehe [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von PowerShell, um Reporting Services-Abonnenten zu ändern und aufzulisten sowie ein Abonnement auszuführen](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)   
 [Prüfliste: Überprüfen von PowerPivot für SharePoint mithilfe von PowerShell](../analysis-services/instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint.md)   
 [CodePlex-SharePoint-Verwaltungs-PowerShell-Skripts](http://sharepointpsscripts.codeplex.com/)   
 [Verwalten von SSRS mit PowerShell](https://curatedviews.cloudapp.net/13107/how-to-administer-ssrs-using-powershell)  
  
  
