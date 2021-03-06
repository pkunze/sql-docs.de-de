---
title: 'Schritt 2: Erstellen einer beschädigten Datei | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: cd0b18dc-66c3-4d88-86ef-8e40cb660fae
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7a348823679ab464bb35520d309d5c8cc50b3ae2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47829630"
---
# <a name="lesson-4-2---creating-a-corrupted-file"></a>Lektion 4-2: Erstellen einer beschädigten Datei
Um die Konfiguration und die Behandlung von Transformationsfehlern zu demonstrieren, müssen Sie eine Beispielflatfile erstellen, die beim Verarbeiten für eine Komponente einen Fehler erzeugt.  
  
In dieser Aufgabe erstellen Sie eine Kopie einer vorhandenen Beispielflatfile. Anschließend öffnen Sie die Datei im Editor und bearbeiten die **CurrencyID** -Spalte, um sicherzustellen, dass von ihr keine Übereinstimmung während der Transformationssuche produziert wird. Wenn die neue Datei verarbeitet wird, erzeugt der Suchfehler einen Fehler der Currency Key Lookup-Transformation, sodass auch der Rest des Pakets fehlschlägt. Nach dem Erstellen der beschädigten Beispieldatei führen Sie das Paket aus, um den vom Paket verursachten Fehler anzuzeigen.  
  
### <a name="to-create-a-corrupted-sample-flat-file"></a>So erstellen Sie eine beschädigte Beispielflatfile  
  
1.  Öffnen Sie in Editor oder einem anderen Texteditor die Datei Currency_VEB.txt.  
  
    Die Beispieldaten sind in den SSIS-Lektionspaketen enthalten. Um die Beispieldaten und die Lektionspakete herunterzuladen, gehen Sie wie folgt vor.  
  
    1.  Navigieren Sie zu [Integration Services Product Samples](http://go.microsoft.com/fwlink/?LinkID=267527).  
  
    2.  Klicken Sie auf die Registerkarte **DOWNLOADS** .  
  
    3.  Klicken Sie auf die Datei SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
2.  Suchen Sie mithilfe der Funktion des Texteditors zum Suchen und Ersetzen alle Instanzen von **VEB** und ersetzen Sie sie durch **BAD**.  
  
3.  Speichern Sie im gleichen Ordner wie die anderen Beispieldatendateien die geänderte Datei als **Currency_BAD.txt**.  
  
    > [!IMPORTANT]  
    > Speichern Sie **Currency_BAD.txt** im selben Ordner wie die anderen Beispieldatendateien.  
  
4.  Schließen Sie den Texteditor.  
  
### <a name="to-verify-that-an-error-will-occur-during-run-time"></a>So überprüfen Sie das Auftreten eines Fehlers während der Laufzeit  
  
1.  Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
    In der dritten Iteration des Datenflusses wird von der Lookup Currency Key-Transformation versucht, die Datei Currency_BAD.txt zu verarbeiten, und die Transformation erzeugt einen Fehler. Der Fehler der Transformation erzeugt einen Fehler des gesamten Pakets.  
  
2.  Klicken Sie im Menü **Debuggen** auf **Debuggen beenden**.  
  
3.  Klicken Sie auf der Entwurfsoberfläche auf die Registerkarte **Ausführungsergebnisse** .  
  
4.  Durchsuchen Sie das Protokoll und überprüfen Sie, ob der folgende nicht behandelte Fehler aufgetreten ist:  
  
    `[Lookup Currency Key[27]] Error: Row yielded no match during lookup.`  
  
    > [!NOTE]  
    > Die Zahl 27 ist die ID der Komponente. Dieser Wert wird zugewiesen, wenn Sie den Datenfluss erstellen. Der Wert in Ihrem Paket kann sich von diesem Wert unterscheiden.  
  
## <a name="next-steps"></a>Next Steps  
[Schritt 3: Hinzufügen von Fehlerflussumleitungen](../integration-services/lesson-4-3-adding-error-flow-redirection.md)  
  
  
  
