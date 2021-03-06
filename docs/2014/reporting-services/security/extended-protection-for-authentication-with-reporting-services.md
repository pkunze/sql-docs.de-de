---
title: Erweiterter Schutz für die Authentifizierung mit Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: eb5c6f4a-3ed5-430b-a712-d5ed4b6b9b2b
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c2a857d433a39958c6018ef8026de2ca3e1efba1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168260"
---
# <a name="extended-protection-for-authentication-with-reporting-services"></a>Erweiterter Schutz für die Authentifizierung mit Reporting Services
  Erweiterter Schutz ist eine Gruppe von Erweiterungen zu den letzten Versionen des [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Windows-Betriebssystems. Erweiterter Schutz verbessert den Schutz der Anmeldeinformationen und der Authentifizierung durch Anwendungen. Das Feature selbst bietet keinen Schutz gegen bestimmte Angriffe, z.B. Anmeldeinformationen-Weiterleitung, aber es bietet eine Infrastruktur für Anwendungen wie z. B. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] zum erweiterten Schutz für die Authentifizierung zu erzwingen.  
  
 Die Hauptauthentifizierungserweiterungen, die Teil des erweiterten Schutzes sind, sind Dienstbindung und Kanalbindung. Die Kanalbindung verwendet ein Kanalbindungstoken (Channel Binding Token oder CBT), um zu überprüfen, ob der zwischen zwei Endpunkten festgelegte Kanal nicht beeinträchtigt wurde. Dienstbindung überprüft das beabsichtigte Ziel von Authentifizierungstokens mithilfe von Dienstprinzipalnamen (Service Principal Names oder SPN). Weitere Hintergrundinformationen zu erweitertem Schutz finden Sie unter [Integrierte Windows-Authentifizierung unter Verwendung von „Erweiterter Schutz“](http://go.microsoft.com/fwlink/?LinkId=179922).  
  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] unterstützt und erzwingt erweiterten Schutz, der im Betriebssystem aktiviert und konfiguriert wurde [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Standardmäßig akzeptiert [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Anforderungen, die Negotiate- oder NTLM-Authentifizierung angeben und daher im Betriebssystem von der Unterstützung des erweiterten Schutzes und der erweiterten [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Schutzfunktionen profitieren könnten.  
  
> [!IMPORTANT]  
>  Windows aktiviert den erweiterten Schutz nicht standardmäßig. Informationen zum Aktivieren des erweiterten Schutzes in Windows finden Sie unter [Erweiterter Schutz für die Authentifizierung](http://go.microsoft.com/fwlink/?LinkID=178431). Sowohl das Betriebssystem als auch der Clientauthentifizierungsstapel müssen den erweiterten Schutz unterstützen, damit die Authentifizierung erfolgreich ist. Bei älteren Betriebssystemen müssen Sie möglicherweise mehr als ein Update für einen Computer mit vollständigem erweiterten Schutz installieren. Informationen zu aktuellen Entwicklungen mit erweitertem Schutz finden Sie in den [aktualisierten Informationen mit erweitertem Schutz](http://go.microsoft.com/fwlink/?LinkId=183362).  
  
## <a name="reporting-services-extended-protection-overview"></a>Übersicht über Reporting Services mit erweitertem Schutz  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] unterstützt und erzwingt erweiterten Schutz, der im Betriebssystem aktiviert wurde. Wenn das Betriebssystem keinen erweiterten Schutz unterstützt oder das Feature im Betriebssystem nicht aktiviert wurde, tritt bei der Authentifizierung der Funktion von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] für erweiterten Schutz ein Fehler auf. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Erweiterter Schutz erfordert auch ein SSL-Zertifikat. Weitere Informationen finden Sie unter [Konfigurieren von SSL-Verbindungen auf einem Berichtsserver im einheitlichen Modus](configure-ssl-connections-on-a-native-mode-report-server.md).  
  
> [!IMPORTANT]  
>  In der Standardeinstellung [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] erweiterten Schutz nicht aktiviert. Die Funktion kann aktiviert werden, indem Sie entweder die `rsreportserver.config`-Konfigurationsdatei bearbeiten oder die WMI-APIs verwenden, um die Konfigurationsdatei zu aktualisieren. [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] stellt nicht bereit, um erweiterte schutzeinstellungen durch eine Benutzeroberfläche zu ändern oder anzuzeigen. Weitere Informationen finden Sie im Abschnitt [Konfigurationseinstellungen](#ConfigurationSettings) in diesem Thema.  
  
 Häufige Probleme, die wegen Änderungen in erweiterten Schutzeinstellungen oder falsch konfigurierten Einstellungen auftreten, werden nicht mit offensichtlichen Fehlermeldungen oder Dialogfeldern angezeigt. Probleme mit Bezug auf die erweiterte Schutzkonfiguration und Kompatibilität führen zu Authentifizierungsfehlern und Fehlern in den [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Ablaufverfolgungsprotokollen.  
  
> [!IMPORTANT]  
>  Einige Technologien für den Datenzugriff unterstützen möglicherweise nicht den erweiterten Schutz. Für die Verbindung mit SQL Server-Datenquellen und der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Katalogdatenbank wird eine Datenzugriffstechnologie verwendet. Falls die Datenzugriffstechnologie den erweiterten Schutz nicht unterstützt, hat dies die folgenden Auswirkungen auf [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]:  
>   
>  -   Auf dem SQL Server, auf dem die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Katalogdatenbank ausgeführt wird, kann der erweiterte Schutz nicht aktiviert sein, da der Berichtsserver ansonsten keine Verbindung zur Katalogdatenbank herstellt und Authentifizierungsfehler zurückgibt.  
> -   SQL Server-Instanzen, die verwendet werden, als [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Bericht Datenquellen können nicht aktivierten erweiterten Schutz haben oder versucht, die vom Berichtsserver für die Verbindung mit der Berichtsdatenquelle fehlschlagen und Authentifizierungsfehler zurückgegeben.  
>   
>  Die Dokumentation einer Datenzugriffstechnologie sollte Informationen zu Unterstützung des erweiterten Schutzes enthalten.  
  
### <a name="upgrade"></a>UPGRADE  
  
-   Aktualisieren einer [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Server [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] Konfigurationseinstellungen mit Standardwerten hinzugefügt der `rsreportserver.config` Datei. Wenn die Einstellungen bereits vorhanden waren die [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] Installation behalten Sie sie in der `rsreportserver.config` Datei.  
  
-   Wenn die Konfigurationseinstellungen hinzugefügt werden die `rsreportserver.config` XML-Konfigurationsdatei für das Standardverhalten ist die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Schutzfunktion deaktiviert, und Sie müssen die Funktion aktivieren, wie in diesem Thema beschrieben. Weitere Informationen finden Sie im Abschnitt [Konfigurationseinstellungen](#ConfigurationSettings) in diesem Thema.  
  
-   Der Standardwert für die `RSWindowsExtendedProtectionLevel`-Einstellung ist `Off`.  
  
-   Der Standardwert für die `RSWindowsExtendedProtectionScenario`-Einstellung ist `Proxy`.  
  
-   [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] Der Upgrade Advisor überprüft nicht, ob das Betriebssystem oder die aktuelle Installation von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Unterstützung des erweiterten Schutzes aktiviert hat.  
  
### <a name="what-reporting-services-extended-protection-does-not-cover"></a>Was der erweiterte Schutz der Reporting Services nicht abdeckt  
 Die folgenden Funktionsbereiche und Szenarios werden nicht unterstützt, indem die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Schutzfunktion:  
  
-   Autoren von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] benutzerdefinierte sicherheitserweiterungen müssen ihrer benutzerdefinierten sicherheitserweiterung Unterstützung für erweiterten Schutz hinzufügen.  
  
-   Drittanbieter-Komponenten hinzugefügt oder von Ihr verwendet eine [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Installation muss aktualisiert werden, vom Anbieter von Drittanbietern, um erweiterten Schutz unterstützen. Weitere Informationen erhalten Sie vom Drittanbieter.  
  
## <a name="deployment-scenarios-and-recommendations"></a>Bereitstellungsszenarios und -empfehlungen  
 Die folgenden Szenarien veranschaulichen verschiedene Bereitstellungen und Topologien und die empfohlene Konfiguration, um sie mit erweitertem [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Schutz zu sichern.  
  
### <a name="direct"></a>Direkt  
 Dieses Szenario beschreibt das direkte Herstellen einer Verbindung mit einem Berichtsserver, z. B. eine Intranetumgebung.  
  
|Szenario|Szenariodiagramm|So sichern Sie|  
|--------------|----------------------|-------------------|  
|direkte SSL-Kommunikation.<br /><br /> Der Berichtsserver erzwingt die Kanalbindung zwischen Client und Berichtsserver.|![RS_ExtendedProtection_DirectSSL](../media/rs-extendedprotection-directssl.gif "RS_ExtendedProtection_DirectSSL")<br /><br /> 1) Clientanwendung<br /><br /> 2) Berichtsserver|Dienstbindung ist nicht notwendig, da der SSL-Kanal für Kanalbindung verwendet wird.<br /><br /> Legen Sie `RSWindowsExtendedProtectionLevel` zu `Allow` oder `Require`.<br /><br /> Legen Sie `RSWindowsExtendedProtectionScenario` zu `Direct`.|  
|direkte HTTP-Kommunikation. Der Berichtsserver erzwingt die Dienstbindung zwischen Client und Berichtsserver.|![RS_ExtendedProtection_Direct](../media/rs-extendedprotection-direct.gif "RS_ExtendedProtection_Direct")<br /><br /> 1) Clientanwendung<br /><br /> 2) Berichtsserver|Es gibt keinen SSL-Kanal. Daher ist keine Erzwingung der Kanalbindung möglich.<br /><br /> Dienstbindung kann überprüft werden, es ist jedoch keine vollständige Verteidigung ohne Kanalbindung. Dienstbindung allein schützt nur vor grundlegenden Bedrohungen.<br /><br /> Legen Sie `RSWindowsExtendedProtectionLevel` zu `Allow` oder `Require`.<br /><br /> Legen Sie `RSWindowsExtendedProtectionScenario` zu `Any`.|  
  
### <a name="proxy-and-network-load-balancing"></a>Proxy und Netzwerklastenausgleich  
 Clientanwendungen stellen eine Verbindung mit einem Gerät oder einer Software her, die SSL ausführt, und gibt die Anmeldeinformationen zum Server zur Authentifizierung weiter, z. B. ein Extranet, Internet oder Sicheres Intranet. Der Client stellt eine Verbindung mit einem Proxy her, oder alle Clients verwenden einen Proxy.  
  
 Beim Verwenden eines Netzwerklastenausgleichsgeräts (NLB-Geräts) ist die Situation identisch.  
  
|Szenario|Szenariodiagramm|So sichern Sie|  
|--------------|----------------------|-------------------|  
|HTTP-Kommunikation. Der Berichtsserver erzwingt die Dienstbindung zwischen Client und Berichtsserver.|![RS_ExtendedProtection_Indirect](../media/rs-extendedprotection-indirect.gif "RS_ExtendedProtection_Indirect")<br /><br /> 1) Clientanwendung<br /><br /> 2) Berichtsserver<br /><br /> 3) Proxy|Es gibt keinen SSL-Kanal. Daher ist keine Erzwingung der Kanalbindung möglich.<br /><br /> Legen Sie `RSWindowsExtendedProtectionLevel` zu `Allow` oder `Require`.<br /><br /> Legen Sie `RSWindowsExtendedProtectionScenario` zu `Any`.<br /><br /> Beachten Sie, dass der Berichtsserver so konfiguriert werden muss, um zu erfahren, den Namen des Proxyservers, um sicherzustellen, dass die dienstbindung ordnungsgemäß erzwungen wird.|  
|HTTP-Kommunikation.<br /><br /> Der Berichtsserver erzwingt die Kanalbindung zwischen Client und Proxy sowie die Dienstbindung zwischen Client und Berichtsserver.|![RS_ExtendedProtection_Indirect_SSL](../media/rs-extendedprotection-indirect-ssl.gif "RS_ExtendedProtection_Indirect_SSL")<br /><br /> 1) Clientanwendung<br /><br /> 2) Berichtsserver<br /><br /> 3) Proxy|SSL-Kanal zum Proxy ist verfügbar, daher kann die Kanalbindung zum Proxy erzwungen werden.<br /><br /> Auch Dienstbindung kann erzwungen werden.<br /><br /> Der Proxyname muss dem Berichtsserver bekannt sein, und der Berichtsserveradministrator sollte entweder eine URL-Reservierung mit einem Hostheader für ihn erstellen oder den Proxynamen im Windows-Registrierungseintrag `BackConnectionHostNames` konfigurieren.<br /><br /> `RSWindowsExtendedProtectionLevel` oder `Allow` in `Require`<br /><br /> Legen Sie `RSWindowsExtendedProtectionScenario` zu `Proxy`.|  
|Indirekte HTTPS-Kommunikation mit einem sicheren Proxy. Der Berichtsserver erzwingt die Kanalbindung zwischen Client und Proxy sowie die Dienstbindung zwischen Client und Berichtsserver.|![RS_ExtendedProtection_IndirectSSLandHTTPS](../media/rs-extendedprotection-indirectsslandhttps.gif "RS_ExtendedProtection_IndirectSSLandHTTPS")<br /><br /> 1) Clientanwendung<br /><br /> 2) Berichtsserver<br /><br /> 3) Proxy|SSL-Kanal zum Proxy ist verfügbar, daher kann die Kanalbindung zum Proxy erzwungen werden.<br /><br /> Auch Dienstbindung kann erzwungen werden.<br /><br /> Der Proxyname muss dem Berichtsserver bekannt sein, und der Berichtsserveradministrator sollte entweder eine URL-Reservierung mit einem Hostheader für ihn erstellen oder den Proxynamen im Windows-Registrierungseintrag `BackConnectionHostNames` konfigurieren.<br /><br /> `RSWindowsExtendedProtectionLevel` oder `Allow` in `Require`<br /><br /> Legen Sie `RSWindowsExtendedProtectionScenario` zu `Proxy`.|  
  
### <a name="gateway"></a>Gateway  
 Dieses Szenario beschreibt Clientanwendungen, die eine Verbindung mit einem Gerät oder einer Software herstellen, die SSL ausführt und den Benutzer authentifiziert. Dann führt das Gerät oder die Software einen Identitätswechsel für den Benutzerkontext oder einen anderen Benutzerkontext durch, bevor es eine Anforderung an den Berichtsserver stellt.  
  
|Szenario|Szenariodiagramm|So sichern Sie|  
|--------------|----------------------|-------------------|  
|indirekte HTTP-Kommunikation.<br /><br /> Gateway erzwingt die Kanalbindung vom Client zum Gateway. Es gibt eine Dienstbindung vom Gateway zum Berichtsserver.|![RS_ExtendedProtection_Indirect_SSL](../media/rs-extendedprotection-indirect-ssl.gif "RS_ExtendedProtection_Indirect_SSL")<br /><br /> 1) Clientanwendung<br /><br /> 2) Berichtsserver<br /><br /> 3) Gatewaygerät|Kanalbindung vom Client zum Berichtsserver ist nicht möglich, da das Gateway für einen Kontext einen Identitätswechsel durchführt und daher ein neues NTLM-Token erstellt.<br /><br /> Es gibt kein SSL vom Gateway zum Berichtsserver, daher kann die Kanalbindung nicht erzwungen werden.<br /><br /> Dienstbindung kann erzwungen werden.<br /><br /> Legen Sie `RSWindowsExtendedProtectionLevel` zu `Allow` oder `Require`.<br /><br /> Legen Sie `RSWindowsExtendedProtectionScenario` zu `Any`.<br /><br /> Das Gatewaygerät sollte vom Administrator so konfiguriert werden, dass Kanalbindung erzwungen wird.|  
|Indirekte HTTPS-Kommunikation mit einem sicheren Gateway. Das Gateway erzwingt die Kanalbindung zwischen Client und Gateway, und der Berichtsserver erzwingt die Kanalbindung zwischen Gateway und Berichtsserver.|![RS_ExtendedProtection_IndirectSSLandHTTPS](../media/rs-extendedprotection-indirectsslandhttps.gif "RS_ExtendedProtection_IndirectSSLandHTTPS")<br /><br /> 1) Clientanwendung<br /><br /> 2) Berichtsserver<br /><br /> 3) Gatewaygerät|Kanalbindung vom Client zum Berichtsserver ist nicht möglich, da das Gateway für einen Kontext einen Identitätswechsel durchführt und daher ein neues NTLM-Token erstellt.<br /><br /> SSL vom Gateway zum Berichtsserver bedeutet, dass Kanalbindung erzwungen werden kann.<br /><br /> Dienstbindung ist nicht erforderlich.<br /><br /> Legen Sie `RSWindowsExtendedProtectionLevel` zu `Allow` oder `Require`.<br /><br /> Legen Sie `RSWindowsExtendedProtectionScenario` zu `Direct`.<br /><br /> Das Gatewaygerät sollte vom Administrator so konfiguriert werden, dass Kanalbindung erzwungen wird.|  
  
### <a name="combination"></a>Kombination  
 Dieses Szenario beschreibt Extranet- oder Internetumgebungen, in denen der Client einen Proxy verbindet. Dies geschieht in Verbindung mit einer Intranetumgebung, in der ein Client eine Verbindung zum Berichtsserver herstellt.  
  
|Szenario|Szenariodiagramm|So sichern Sie|  
|--------------|----------------------|-------------------|  
|Indirekter und direkter Zugriff vom Client auf den Berichtsserverdienst ohne SSL auf keiner der Verbindungen vom Client zum Proxy und vom Client zum Berichtsserver.|1) Clientanwendung<br /><br /> 2) Berichtsserver<br /><br /> 3) Proxy<br /><br /> 4) Clientanwendung|Dienstbindung von Client zum Berichtsserver kann erzwungen werden.<br /><br /> Der Proxyname muss dem Berichtsserver bekannt sein, und der Berichtsserveradministrator sollte entweder eine URL-Reservierung mit einem Hostheader für ihn erstellen oder den Proxynamen im Windows-Registrierungseintrag `BackConnectionHostNames` konfigurieren.<br /><br /> Legen Sie `RSWindowsExtendedProtectionLevel` zu `Allow` oder `Require`.<br /><br /> Legen Sie `RSWindowsExtendedProtectionScenario` zu `Any`.|  
|Indirekter und direkter Zugriff vom Client auf den Berichtsserver, wo der Client eine SSL-Verbindung zum Proxy oder dem Berichtsserver herstellt.|![RS_ExtendedProtection_CombinationSSL](../media/rs-extendedprotection-combinationssl.gif "RS_ExtendedProtection_CombinationSSL")<br /><br /> 1) Clientanwendung<br /><br /> 2) Berichtsserver<br /><br /> 3) Proxy<br /><br /> 4) Clientanwendung|Kanalbindung kann verwendet werden.<br /><br /> Der Proxyname muss dem Berichtsserver bekannt sein, und der Berichtsserveradministrator sollte entweder eine URL-Reservierung für den Proxy mit einem Hostheader erstellen oder den Proxynamen im Windows-Registrierungseintrag `BackConnectionHostNames` konfigurieren.<br /><br /> Legen Sie `RSWindowsExtendedProtectionLevel` zu `Allow` oder `Require`.<br /><br /> Legen Sie `RSWindowsExtendedProtectionScenario` zu `Proxy`.|  
  
## <a name="configuring-reporting-rervices-extended-protection"></a>Konfigurieren des erweiterten Schutzes für Reporting Services  
 Die `rsreportserver.config` -Datei enthält die Konfigurationswerte, die Steuerung des Verhaltens [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] erweiterter Schutz.  
  
 Weitere Informationen zum verwenden und Bearbeiten der `rsreportserver.config` finden Sie unter [RSReportServer-Konfigurationsdatei](../report-server/rsreportserver-config-configuration-file.md). Die erweiterten Schutzeinstellungen können auch geändert und mithilfe von WMI-APIs überprüft werden. Weitere Informationen finden Sie unter [SetExtendedProtectionSettings-Methode &#40;WMI: MSReportServer_ConfigurationSetting&#41;](../wmi-provider-library-reference/configurationsetting-method-setextendedprotectionsettings.md).  
  
 Wenn die Überprüfung der Konfigurationseinstellungen fehlschlägt, werden die Authentifizierungstypen `RSWindowsNTLM`, `RSWindowsKerberos` und `RSWindowsNegotiate` auf dem Berichtsserver deaktiviert.  
  
###  <a name="ConfigurationSettings"></a> Konfigurationseinstellungen für den erweiterten Schutz der Reporting Services  
 Die folgende Tabelle enthält Informationen zu Konfigurationseinstellungen, die in angezeigt werden. die `rsreportserver.config` für erweiterten Schutz.  
  
|Einstellung|Description|  
|-------------|-----------------|  
|`RSWindowsExtendedProtectionLevel`|Gibt den Grad der Erzwingung des erweiterten Schutzes an. Gültige Werte sind `Off`, `Allow`, und `Require`.<br /><br /> Der Standardwert lautet `Off`.<br /><br /> Der Wert `Off` gibt keine Kanal- oder Dienstbindungsüberprüfung an.<br /><br /> Der Wert `Allow` unterstützt erweiterten Schutz, erfordert ihn aber nicht. Der Wert "Zulassen" gibt Folgendes an:<br /><br /> Erweiterter Schutz wird für Clientanwendungen, die unter Betriebssystemen ausgeführt werden, die erweiterten Schutz unterstützen, erzwungen. Wie Schutz erzwungen wird, wird durch das Festlegen von `RsWindowsExtendedProtectionScenario` bestimmt.<br /><br /> Der Authentifizierung ist für Anwendungen zulässig, die unter Betriebssystemen ausgeführt werden, die keinen erweiterten Schutz unterstützen.<br /><br /> Der Wert `Require` gibt Folgendes an:<br /><br /> Erweiterter Schutz wird für Clientanwendungen, die unter Betriebssystemen ausgeführt werden, die erweiterten Schutz unterstützen, erzwungen.<br /><br /> Die Authentifizierung ist **nicht** für Anwendungen, die unter Betriebssystemen ausgeführt werden, die keinen erweiterten Schutz unterstützen zulässig.|  
|`RsWindowsExtendedProtectionScenario`|Gibt an, welche Arten des erweiterten Schutzes überprüft werden: Kanalbindung, Dienstbindung oder beide. Gültige Werte sind `Any`, `Proxy`, und `Direct`.<br /><br /> Der Standardwert lautet `Proxy`.<br /><br /> Der Wert `Any` gibt Folgendes an:<br /><br /> – Windows-NTLM-, Kerberos- und Negotiate-Authentifizierung sowie eine Kanalbindung sind nicht erforderlich.<br /><br /> – Dienstbindung wird erzwungen.<br /><br /> Der Wert `Proxy` gibt Folgendes an:<br /><br /> – Windows-NTLM-, Kerberos- und Negotiate-Authentifizierung, wenn ein Kanalbindungstoken vorhanden ist.<br /><br /> – Dienstbindung wird erzwungen.<br /><br /> Der Wert `Direct` gibt Folgendes an:<br /><br /> – Windows-NTLM-, Kerberos- und Negotiate-Authentifizierung, wenn ein CBT vorhanden ist, eine SSL-Verbindung zum aktuellen Dienst vorhanden ist und das CBT für die SSL-Verbindung dem CBT des NTLM-, Kerberos- oder Negotiate-Tokens entspricht.<br /><br /> – Dienstbindung wird nicht erzwungen.<br /><br /> <br /><br /> Hinweis: Diese Einstellung wird ignoriert, wenn `RsWindowsExtendedProtectionLevel` nastaven NA hodnotu `OFF`.|  
  
 Beispieleinträge in die `rsreportserver.config` Konfigurationsdatei:  
  
```  
<Authentication>  
         <RSWindowsExtendedProtectionLevel>Allow</RSWindowsExtendedProtectionLevel>  
         <RSWindowsExtendedProtectionScenario>Proxy</RSWindowsExtendedProtectionLevel>  
</Authentication>  
```  
  
## <a name="service-binding-and-included-spns"></a>Dienstbindung und eingeschlossene SPNs  
 Die Dienstbindung nutzt Dienstprinzipalnamen (Service Principal Names oder SPN) zur Überprüfung des beabsichtigten Ziels von Authentifizierungstokens. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] verwendet die vorhandene URL-Reservierungsinformationen eine Liste von SPNs zu erstellen, die als gültig angesehen werden. Durch das Verwenden der URL-Reservierungsinformationen zur Überprüfung von SPN- und URL-Reservierungen können Systemadministratoren beide von einem einzelnen Standort aus verwalten.  
  
 Die Liste der gültigen SPNs wird aktualisiert, wenn der Berichtsserver startet, die Konfigurationseinstellungen für erweiterten Schutz geändert werden oder wenn die Anwendungsdomäne wiederverwendet wird.  
  
 Für jede Anwendung gibt es eine spezielle gültige Liste der SPNs. Für Berichts-Manager und Berichtsserver werden z. B. verschiedene Listen mit gültigen SPNs berechnet.  
  
 Die Liste der gültigen SPNs, die für eine Anwendung berechnet wurde, wird von den folgenden Faktoren bestimmt:  
  
-   Jede URL-Reservierung.  
  
-   Jeder SPN, der vom Domänencontroller für das Reporting Services-Dienstkonto abgerufen wird.  
  
-   Wenn eine URL-Reservierung Platzhalterzeichen ('*' oder '+') enthält, fügt der Berichtsserver jeden einzelnen Eintrag aus der Hosts-Auflistung hinzu.  
  
### <a name="hosts-collection-sources"></a>Hosts-Auflistungsquellen.  
 In der folgenden Tabelle sind die potenziellen Quellen für die Hosts-Auflistung aufgeführt.  
  
|Typ der Quelle|Description|  
|--------------------|-----------------|  
|ComputernameDnsDomäne|Der Name der dem lokalen Computer zugewiesenen DNS-Domäne. Wenn der lokale Computer ein Knoten in einem Cluster ist, wird der DNS-Domänenname des virtuellen Clusterservers verwendet.|  
|ComputernameDnsVollqualifiziert|Der vollqualifizierte DNS-Name, der den lokalen Computer eindeutig identifiziert. Dieser Name ist eine Kombination des DNS-Hostnamens und des DNS-Domänennamens und verwendet die Form *Hostname*.*Domänenname*. Wenn der lokale Computer ein Knoten in einem Cluster ist, wird der vollqualifizierte DNS-Domänenname des virtuellen Clusterservers verwendet.|  
|ComputernameDnsHostname|Der DNS-Hostname des lokalen Computers. Wenn der lokale Computer ein Knoten in einem Cluster ist, wird der DNS-Hostname des virtuellen Clusterservers verwendet.|  
|ComputernameNetBIOS|Der NetBIOS-Name des lokalen Computers. Wenn der lokale Computer ein Knoten in einem Cluster ist, wird der NetBIOS-Name des virtuellen Clusterservers verwendet.|  
|ComputernamePhysischeDnsDomäne|Der Name der dem lokalen Computer zugewiesenen DNS-Domäne. Wenn der lokale Computer ein Knoten in einem Cluster ist, wird der DNS-Domänenname des lokalen Computers verwendet, nicht der Name des virtuellen Clusterservers.|  
|ComputernamePhysischerDnsVollqualifiziert|Der vollqualifizierte DNS-Name, der den Computer eindeutig identifiziert. Wenn der lokale Computer ein Knoten in einem Cluster ist, wird der vollqualifizierte DNS-Name des lokalen Computers verwendet, nicht der Name des virtuellen Clusterservers.<br /><br /> Der vollqualifizierte DNS-Name ist eine Kombination des DNS-Hostnamens und des DNS-Domänennamens und verwendet die Form *Hostname*.*Domänenname*.|  
|ComputernamePhysischerDnsHostname|Der DNS-Hostname des lokalen Computers. Wenn der lokale Computer ein Knoten in einem Cluster ist, wird der DNS-Hostname des lokalen Computers verwendet, nicht der Name des virtuellen Clusterservers.|  
|ComputernamePhysischerNetBIOS|Der NetBIOS-Name des lokalen Computers. Wenn der lokale Computer ein Knoten in einem Cluster ist, wird der NetBIOS-Name des lokalen Computers verwendet, nicht der Name des virtuellen Clusterservers.|  
  
 Wenn SPNs hinzugefügt werden, wird dem Ablaufverfolgungsprotokoll, das etwa folgendermaßen aussieht, ein Eintrag hinzugefügt:  
  
 `rshost!rshost!10a8!01/07/2010-19:29:38:: i INFO: SPN Whitelist Added <ComputerNamePhysicalNetBIOS> - <theservername>.`  
  
 `rshost!rshost!10a8!01/07/2010-19:29:38:: i INFO: SPN Whitelist Added <ComputerNamePhysicalDnsHostname> - <theservername>.`  
  
 Weitere Informationen finden Sie unter [Registrieren eines Dienstprinzipalnamens &#40;SPN&#41; für einen Berichtsserver](../report-server/register-a-service-principal-name-spn-for-a-report-server.md) und [Informationen zu URL-Reservierungen und -Registrierungen &#40;SSRS-Konfigurations-Manager&#41;](../install-windows/about-url-reservations-and-registration-ssrs-configuration-manager.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Herstellen einer Verbindung mit der Datenbank-Engine unter Verwendung von Erweiterter Schutz](../../database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection.md)   
 [Übersicht über den erweiterten Schutz für die Authentifizierung (möglicherweise auf Englisch)](http://go.microsoft.com/fwlink/?LinkID=177943)   
 [Integrierte Windows-Authentifizierung unter Verwendung von „Erweiterter Schutz“](http://go.microsoft.com/fwlink/?LinkId=179922)   
 [Microsoft-Sicherheitsempfehlung: Erweiterter Schutz für die Authentifizierung (möglicherweise auf Englisch)](http://go.microsoft.com/fwlink/?LinkId=179923)   
 [Berichtsserver-Ablaufverfolgungsprotokoll](../report-server/report-server-service-trace-log.md)   
 [RSReportServer-Konfigurationsdatei](../report-server/rsreportserver-config-configuration-file.md)   
 [SetExtendedProtectionSettings-Methode &#40;WMI: MSReportServer_ConfigurationSetting&#41;](../wmi-provider-library-reference/configurationsetting-method-setextendedprotectionsettings.md)  
  
  
