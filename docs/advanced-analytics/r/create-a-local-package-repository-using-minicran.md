---
title: Erstellen Sie ein lokales R-Paket-Repository mit MiniCRAN (SQL Server-Machine Learning) | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 1f7ba3b4acde90d9e416eb092ac80cb0dfcbba8a
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34585642"
---
# <a name="create-a-local-r-package-repository-using-minicran"></a>Erstellen Sie ein lokales R-Paket-Repository mit miniCRAN
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[MiniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) vom erstellte Paket [Andre de Vries](http://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html), identifiziert und downloads, Pakete und Abhängigkeiten in einem einzelnen Ordner, den Sie mit anderen Computern für die Offlineinstallation von R-Paket kopieren können.

Geben Sie ein oder mehrere Pakete als Eingabe. **MiniCRAN** rekursiv liest die Abhängigkeitsstruktur für diese Pakete und nur die aufgelisteten Pakete und ihre Abhängigkeiten von CRAN oder ähnliche Repositorys herunterlädt.

Als Ausgabe verwenden **MiniCRAN** ein intern konsistent Repository bestehend aus der ausgewählten Pakete und alle erforderlichen Abhängigkeiten erstellt. Sie können dieses lokale Repository auf den Server verschoben, und fahren Sie mit der Pakete ohne Internetverbindung installieren.

> [!NOTE]
> Erfahrene Benutzer von R werden häufig für die Liste der abhängigen Pakete in der DESCRIPTION-Datei für das heruntergeladene Paket suchen. Allerdings Pakete aufgeführt, **Importe** möglicherweise Abhängigkeiten der zweiten Ebene. Aus diesem Grund empfehlen wir **MiniCRAN** für die vollständige Auflistung der erforderlichen Pakete zusammenstellen.

## <a name="why-create-a-local-repository"></a>Warum erstellt ein lokales repository

Das Ziel zum Erstellen einer lokalen paketrepository ist an einen zentralen Ort zu bieten, den ein Serveradministrator oder anderen Benutzern in der Organisation verwenden können, um neue R-Pakete auf einem Server, insbesondere wenn er zu installieren, die über keinen Zugriff auf das Internet. Nach dem Erstellen des Repositorys an, können Sie es durch Hinzufügen von neuen Paketen oder aktualisieren die Version der vorhandenen Pakete ändern.

Paket-Repositorys sind in diesen Szenarien nützlich:

- **Sicherheit**: viele R-Benutzer sind daran gewöhnt, zum Herunterladen und installieren neue R-Pakete werden, vom CRAN oder von einem Spiegel Standorte. Jedoch aus Sicherheitsgründen Produktionsservern ausgeführt [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] haben für gewöhnlich keine Internetverbindung.

- **Einfacher Offlineinstallation**: beim Installieren des Pakets mit einem offline-Server erfordert, dass Sie auch alle paketabhängigkeiten herunterladen, mit MiniCRAN erleichtert es, rufen Sie alle Abhängigkeiten im richtigen Format ab.

    Mithilfe von MiniCRAN können Sie Paket Abhängigkeit Fehler vermeiden, bei der Vorbereitung der Pakete für die Installation mit den [externe Bibliothek erstellen](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) Anweisung.

- **Verbesserte versionsverwaltung**: In einer mehrbenutzerumgebung, es gibt gute Gründe für die uneingeschränkte Paketversionen auf dem Server-Installation zu verhindern. Verwenden Sie ein lokales Repository, um ein konsistenter Satz von Paketen für die Verwendung durch Ihre Analytiker bereitzustellen. 

> [!TIP]
> Sie können auch MiniCRAN Vorbereiten von Paketen für die Verwendung in Azure Machine Learning verwenden. Weitere Informationen finden Sie in diesem Blog: [MiniCRAN in Azure ML von Michele Usuelli verwenden](https://www.r-bloggers.com/using-minicran-in-azure-ml/) 

## <a name="install-minicran"></a>Installieren von miniCRAN

Die **MiniCRAN** Paket selbst 18 CRAN-Paketen abhängig ist zwischen also die **RCurl** Paket, das von einem System abhängig ist auf die **Curl entwickl** Paket. Auf ähnliche Weise Paket **XML** abhängt **libxml2 entwickl**. Um Abhängigkeiten zu beheben, wird empfohlen, dass Sie Ihr lokale Repository anfangs auf einem Computer mit vollständigen Zugriff auf das Internet erstellen. 

Führen die folgenden Befehle auf einem Computer mit einer Basis R, R-Tools und Internet-Verbindung. Es wird davon ausgegangen, dass dies *nicht* SQL Server-Computers. Installieren Sie die folgenden Befehle die **MiniCRAN** Paket und das erforderliche **Igraph** Paket. In diesem Beispiel wird überprüft, ob das Paket bereits installiert ist, können Sie die If umgeht jedoch Anweisungen und Installieren der Pakete direkt.

```R
if(!require("miniCRAN")) install.packages("miniCRAN") 
if(!require("igraph")) install.packages("igraph") 
library("miniCRAN")
```

## <a name="set-the-cran-mirror-and-mran-snapshot"></a>Festlegen der CRAN-Spiegel und der MRAN Momentaufnahme

Geben Sie eine gespiegelte Site beim Abrufen der Pakete verwenden. Z. B. können die MRAN-Website, oder einen anderen Standort in Ihrer Region Sie, die die Pakete enthält, die Sie benötigen. Wenn der Downloadvorgang abgebrochen, versuchen Sie eine andere gespiegelte Site aus.

```R
CRAN_mirror <- c(CRAN = "https://mran.microsoft.com")
CRAN_mirror <- c(CRAN = "https://cran.cnr.berkeley.edu")
```

## <a name="create-a-local-folder"></a>Erstellen Sie einen lokalen Ordner

Erstellen Sie einen lokalen Ordner, z. B. `C:\mylocalrepo` , um die gesammelten Pakete zu speichern. Wenn dies häufig wiederholt wird, sollten Sie wahrscheinlich einen aussagekräftigeren Namen, z. B. "MiniCRANZooPackages" oder "miniCRANMyRPackagev2" verwenden.

Geben Sie den Ordner als das lokale Repository. R-Syntax verwendet, einen Schrägstrich für Pfadnamen, die entgegengesetzten wird von Windows-Konventionen.

```R
local_repo <- "C:/mylocalrepo"
```

## <a name="add-packages-to-the-local-repo"></a>Hinzufügen von Paketen auf das lokale Repository

Nach dem **MiniCRAN** ist installiert und geladen, erstellen Sie eine Liste, der angibt, die weitere Pakete heruntergeladen werden soll.

Führen Sie **nicht** Abhängigkeiten zu dieser anfänglichen Liste hinzufügen. Die **Igraph** Paket, die von **MiniCRAN** die Liste der Abhängigkeiten für Sie generiert. Weitere Informationen zur Verwendung der generierten Abhängigkeitsdiagramm finden Sie unter [MiniCRAN zum Identifizieren von paketabhängigkeiten verwendet](https://cran.r-project.org/web/packages/miniCRAN/vignettes/miniCRAN-dependency-graph.html).

1. Fügen Sie die Ziel-Pakete, "Zoo" und "Planung", um eine Variable hinzu.

    ```R
    pkgs_needed <- c("zoo", "forecast")
    ```

2. Optional, das Abhängigkeitsdiagramm zeichnen, aber es kann sehr informativ sein.
    
    ```R
    plot(makeDepGraph(pkgs_needed))
    ```

3. Erstellen Sie das lokale Repository. Achten Sie darauf, dass die R-Version ändern, soweit erforderlich, um die Version auf SQL Server-Instanz installiert werden. 3.2.2-Version ist auf SQL Server 2016, Version 3.3 ist auf SQL Server-2017. Wenn Sie ein Upgrade von Integrationskomponenten verwendet haben, kann Ihre neuere sein. Weitere Informationen finden Sie unter [R abrufen und Python-Paketinformationen](determine-which-packages-are-installed-on-sql-server.md).

    ```R
    pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror);
    makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.3");
    ```

   Aus diesen Informationen erstellt das MiniCRAN-Paket die Ordnerstruktur, die Sie benötigen, kopieren Sie die Pakete für die [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] später erneut.

An diesem Punkt sollten Sie einen Ordner, in dem Sie Pakete haben, und alle zusätzlichen Pakete, die erforderlich waren. Der Pfad sollte ähnlich wie in diesem Beispiel werden: C:\mylocalrepo\bin\windows\contrib\3.3 und es müssen eine Auflistung von komprimierten Paketen enthalten. Entpacken Sie die Pakete nicht, oder benennen Sie alle Dateien.

Führen Sie optional den folgenden Code aus, um die im lokalen MiniCRAN Repository enthaltenen Pakete aufzulisten.

```R
pdb <- as.data.frame(pkgAvail(local_repo, type = "win.binary", Rversion = "3.3"), stringsAsFactors = FALSE);
head(pdb);
pdb$Package;
pdb[, c("Package", "Version", "License")]
```

## <a name="add-packages-to-the-instance-library"></a>Hinzufügen von Paketen in der Instanz-Bibliothek

Nachdem Sie ein lokales Repository mit den Paketen, die Sie benötigen haben, verschieben Sie den paketrepository auf den SQL Server-Computer. Das folgende Verfahren beschreibt, wie die Pakete mithilfe von R-Tools zu installieren.

1. Kopieren Sie den Ordner mit dem Repository MiniCRAN in seiner Gesamtheit, mit dem Server, auf dem die Pakete installiert werden sollen. Der Ordner ist in der Regel für diese Struktur: MiniCRAN-Stamm > "bin" > Windows > für die Altersvorsorge > Version > alle Pakete. In den folgenden Beispielen gehen wir davon aus, einen Ordner aus dem Stammlaufwerk: 

2. Öffnen Sie ein R-Tool, mit der Instanz verknüpft ist (z. B. können Sie Rgui.exe). Mit der rechten Maustaste **als Administrator ausführen** ermöglichen das Tool Aktualisierungen am System vornehmen.

    - Für SQL Server 2017 ist der Speicherort für "rgui.exe" `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`.

    - Für SQL Server 2016, He-Dateispeicherort für "rgui.exe" ist `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`.

3. Rufen Sie den Pfad für die Instanz-Bibliothek, und fügen Sie es der Liste der Library-Pfade. Auf SQL Server-2017 ist der Pfad im folgenden Beispiel ähnelt.

    ```R
    outputlib <- "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library"
    ```

4. Geben Sie den neuen Speicherort auf dem Server, in denen Sie kopiert, die **MiniCRAN** -Repository als `server_repo`.

    In diesem Beispiel wird davon ausgegangen, dass Sie das Repository in einen temporären Ordner auf dem Server kopiert haben.

    ```R
    inputlib <- "C:/temp/mylocalrepo"
    ```

5. Da Sie in einem neuen R-Arbeitsbereich auf dem Server arbeiten, müssen Sie auch die Liste der Pakete zu installieren sind.

    ```R
    mypackages <- c("zoo", "forecast")
    ```

6. Installieren Sie die Pakete, die den Pfad zur lokalen Kopie des Repositorys MiniCRAN bereitstellen.

    ```R
    install.packages(mypackages, repos = file.path("file://", normalizePath(inputlib, winslash = "/")), lib = outputlib, type = "win.binary", dependencies = TRUE);
    ```

7. Von der Instanz bereitgestellt werden können Sie die installierten Pakete, die mit einem Befehl wie folgt anzeigen:

    ```R
    installed.packages()
    ```

## <a name="see-also"></a>Siehe auch

+ [Paketinformationen abrufen](determine-which-packages-are-installed-on-sql-server.md)
+ [R-Lernprogramme](../tutorials/sql-server-r-tutorials.md)
+ [Anleitungen](sql-server-machine-learning-tasks.md)


