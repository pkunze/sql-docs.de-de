---
title: Programmieren von AMO-komplementärer Klassen und Methoden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- restores [AMO]
- assemblies [AMO]
- AMO, backup and restore
- capture logs [AMO]
- programming [AMO]
- Analysis Management Objects, backup and restore
- traces [AMO]
- backups [AMO]
ms.assetid: 14aed554-d2e2-49e5-9c72-26660759bce2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: afcf4a2bfcae71564d467e182282f7a8db3d3a65
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48225282"
---
# <a name="programming-amo-complementary-classes-and-methods"></a>Programmieren AMO-komplementärer Klassen und Methoden
  Dieses Thema enthält folgende Abschnitte:  
  
-   [Assembly-Klasse](#Assembly)  
  
-   [Backup and Restore (Sichern und Wiederherstellen)](#BU)  
  
-   [Trace-Klasse](#TRC)  
  
-   [CaptureLog-Klasse und CaptureXML-Attribut](#CL)  
  
##  <a name="Assembly"></a> Assembly-Klasse  
 Assemblys können Benutzer Erweitern der Funktionalität von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] durch Hinzufügen von neuen gespeicherten Prozeduren oder Funktionen (Multidimensional Expressions). Weitere Informationen finden Sie unter [andere AMO-Klassen und Methoden](amo-other-classes-and-methods.md).  
  
 Das Hinzufügen und Löschen von Assemblys ist einfach und kann online ausgeführt werden. Sie müssen Datenbankadministrator sein, um der Datenbank eine Assembly hinzufügen zu können, bzw. Serveradministrator, um die Assembly dem Serverobjekt hinzufügen zu können.  
  
 Im folgenden Beispiel wird eine Assembly der bereitgestellten Datenbank hinzugefügt und das Dienstkonto zur Ausführung der Assembly zugewiesen. Wenn die Assembly in der Datenbank vorhanden ist, wird sie vor dem Versuch, sie hinzuzufügen, gelöscht.  
  
```  
static public void CreateStoredProcedures(Database db)  
{  
    ClrAssembly clrAssembly;  
  
    // Verify That assembly exist in database and drop it  
    if (db.Assemblies.ContainsName("StoredProcedures"))  
    {  
        clrAssembly = db.Assemblies.FindByName("StoredProcedures");  
        clrAssembly.Drop();  
    }  
  
    // Create the CLR assembly  
    clrAssembly = db.Assemblies.Add("StoredProcedures");  
    clrAssembly.ImpersonationInfo = new ImpersonationInfo(  
        ImpersonationMode.ImpersonateServiceAccount);  
    clrAssembly.PermissionSet = PermissionSet.Unrestricted;  
  
    // Load the assembly files  
    clrAssembly.LoadFiles(Environment.CurrentDirectory  
        + @"\StoredProcedures2.dll", false);  
  
    clrAssembly.Update();  
}  
  
```  
  
##  <a name="BU"></a> Backup- und Restore-Methoden  
 Mit den Methoden Backup und Restore können Administratoren Datenbanken sichern und sie wiederherstellen.  
  
 Im folgenden Beispiel werden Sicherungen für alle Datenbanken auf dem angegebenen Server erstellt. Wenn bereits eine Sicherungsdatei vorhanden ist, wird sie überschrieben. Sicherungsdateien werden im Sicherungsordner des Datenordners von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] gespeichert.  
  
```  
static public void BackUpAllDatabases(Server svr)  
{  
    string fileName;  
    if ((svr != null) && ( svr.Connected))  
        foreach (Database db in svr.Databases)  
        {  
            fileName = db.Name + "_" + ((Int64)(DateTime.Today.Year * 10000 + DateTime.Today.Month * 100 + DateTime.Today.Day)).ToString()+ ".abf";  
            db.Backup(fileName, true);  
        }  
}  
```  
  
 Im folgenden Beispiel wird die "Adventure Works"-Sicherung aus dem vorherigen Beispiel wiederhergestellt. Wenn die "My Adventure WorksDW"-Datenbank bereits vorhanden ist, dann wird die Datenbank überschrieben.  
  
```  
static public void RestoreAdventureWorks(Server svr)  
{  
    svr.Restore("Adventure Works DW_20051025.abf", "My Adventure WorksDW", true);  
}  
```  
  
##  <a name="TRC"></a> Trace-Klasse  
 Die Überwachung der Serveraktivität erfordert zwei Arten von Ablaufverfolgungen: Sitzungsablaufverfolgungen und Serverablaufverfolgungen. Mithilfe der Ablaufverfolgung des Servers können Sie die Leistung des aktuellen Tasks auf dem Server (Sitzungsablaufverfolgungen) oder die Gesamtaktivität auf dem Server ermitteln, ohne dass Sie mit dem Server verbunden sind (Serverablaufverfolgungen).  
  
 Bei der Ablaufverfolgung der aktuellen Aktivität (Sitzungsablaufverfolgungen) sendet der Server der laufenden Anwendung Benachrichtigungen über die Ereignisse, die auf dem Server stattfinden und von der Anwendung verursacht werden. Ereignisse werden mithilfe von Ereignishandlern in der aktuellen Anwendung aufgezeichnet. Sie weisen zuerst dem <xref:Microsoft.AnalysisServices.SessionTrace>-Objekt die Ereignisbehandlungsroutinen zu und starten dann die Sitzungsablaufverfolgung.  
  
 Das folgende Beispiel zeigt, wie Sie eine Sitzungsablaufverfolgung zur Verfolgung aktueller Aktivitäten einrichten. Ereignisbehandlungsroutinen stehen am Ende des Beispiels; damit werden alle Ablaufverfolgungsinformationen an das System.Console-Objekt ausgegeben. Um Ablaufverfolgungsereignisse zu generieren, wird der "Adventure Works"-Beispielcube vollständig verarbeitet, nachdem die Ablaufverfolgung gestartet hat.  
  
```  
static public void TestSessionTraces(Server svr)  
{  
    // Start the default trace  
  
    svr.SessionTrace.OnEvent  
        += new TraceEventHandler(DefaultTrace_OnEvent);  
    svr.SessionTrace.Stopped  
        += new TraceStoppedEventHandler(DefaultTrace_Stopped);  
    svr.SessionTrace.Start();  
  
    // Process the databases  
    // The trace handlers will output all progress notifications   
    // to the console  
    Database db = svr.Databases.FindByName("Adventure Works DW Multidimensional 2012");  
    Cube cube = db.Cubes.FindByName("Adventure Works");  
    cube.Process(ProcessType.ProcessFull);  
  
    // Stop the default trace  
    svr.SessionTrace.Stop();  
  
}  
static public void DefaultTrace_OnEvent(object sender, TraceEventArgs e)  
{  
    Console.WriteLine("{0}", e.TextData);  
}  
  
static public void DefaultTrace_Stopped(ITrace sender, TraceStoppedEventArgs e)  
{  
    switch (e.StopCause)  
    {  
        case TraceStopCause.StoppedByUser:  
        case TraceStopCause.Finished:  
            Console.WriteLine("Processing completed successfully");  
            break;  
  
        case TraceStopCause.StoppedByException:  
            Console.WriteLine("Processing failed: {0}",  
                e.Exception.Message);  
            break;  
    }  
}  
```  
  
 Serverablaufverfolgungen können konfiguriert werden, um alles in einer Ablaufverfolgungsdatei zu protokollieren. Sie können beim Neustart des Dienstes automatisch neu gestartet werden.  
  
 Zum Festlegen einer Serverablaufverfolgung müssen Sie zuerst definieren, welche Ereignisse auf dem Server überwacht und welche Daten aus dem Ereignis in der Ablaufverfolgungsdatei gespeichert werden sollen. Für jedes Ereignis müssen Sie die Datenspalten definieren, die in der Ablaufverfolgungsdatei gespeichert werden sollen.  
  
 Die Erstellung einer Serverablaufverfolgung erfordert vier Schritte:  
  
1.  Erstellen Sie das Ablaufverfolgungsobjekt des Servers, und füllen Sie die grundlegenden, allgemeinen Attribute auf.  
  
     In LogFileSize ist die maximale Größe der Ablaufverfolgungsdatei in Megabyte definiert. LogFileRollOver ermöglicht das Starten der Protokolldatei in einer anderen Datei, sobald das LogFileSize-Limit erreicht ist; bei Aktivierung wird eine Folgenummer an den Dateinamen angehängt. AutoRestart ermöglicht den Neustart der Ablaufverfolgung, wenn der Dienst neu gestartet wird.  
  
2.  Erstellen Sie die Ereignisse und die entsprechenden Datenspalten.  
  
3.  Starten und beenden Sie die Ablaufverfolgung nach Bedarf.  
  
     Auch nach Beendigung der Ablaufverfolgung bleibt diese auf dem Server bestehen und müsste erneut gestartet werden, wenn die Ablaufverfolgung als AutoRestart=`true` definiert wurde.  
  
4.  Löschen Sie die Ablaufverfolgung, wenn sie nicht mehr benötigt wird.  
  
 Wenn im folgenden Beispiel die Ablaufverfolgung bereits vorhanden ist, wird sie gelöscht und dann neu erstellt. Ablaufverfolgungsdateien werden im Protokollordner der Datenordner von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] gespeichert.  
  
```  
static public void TestServerTraces(Server svr)  
{  
    Trace trc;  
    TraceEvent te;  
  
        trc = svr.Traces.FindByName("TestServerTraces");  
        if (trc != null)  
            trc.Drop();  
        trc = svr.Traces.Add("TestServerTraces", "TestServerTraces");  
        trc.LogFileName = ("TestServerTraces_" +((Int64)(DateTime.Now.Year * 10000 + DateTime.Now.Month * 100 + DateTime.Now.Day)).ToString() + "_" +  
                ((Int64)(DateTime.Now.Hour * 10000 + DateTime.Now.Minute * 100 + DateTime.Now.Second)).ToString() + ".trc");  
        trc.LogFileSize = 100;  
        trc.LogFileRollover = true;  
        trc.AutoRestart = false;  
  
        #region Define Events to trace & data columns per event  
        te = trc.Events.Add(TraceEventClass.ProgressReportBegin);  
        te.Columns.Add(TraceColumn.TextData);  
        te.Columns.Add(TraceColumn.StartTime);  
        te.Columns.Add(TraceColumn.ObjectName);  
        te.Columns.Add(TraceColumn.ObjectPath);  
        te.Columns.Add(TraceColumn.DatabaseName);  
        te.Columns.Add(TraceColumn.NTCanonicalUserName);  
  
        te = trc.Events.Add(TraceEventClass.ProgressReportCurrent);  
        te.Columns.Add(TraceColumn.TextData);  
        te.Columns.Add(TraceColumn.CurrentTime);  
        te.Columns.Add(TraceColumn.ObjectName);  
        te.Columns.Add(TraceColumn.ObjectPath);  
        te.Columns.Add(TraceColumn.DatabaseName);  
  
        te = trc.Events.Add(TraceEventClass.ProgressReportEnd);  
        te.Columns.Add(TraceColumn.TextData);  
        te.Columns.Add(TraceColumn.StartTime);  
        te.Columns.Add(TraceColumn.CurrentTime);  
        te.Columns.Add(TraceColumn.EndTime);  
        te.Columns.Add(TraceColumn.Success);  
        te.Columns.Add(TraceColumn.Error);  
        te.Columns.Add(TraceColumn.ObjectName);  
        te.Columns.Add(TraceColumn.ObjectPath);  
        te.Columns.Add(TraceColumn.DatabaseName);  
        te.Columns.Add(TraceColumn.NTCanonicalUserName);  
        #endregion  
  
        trc.Update();  
        trc.Start();  
  
        #region Process the Adventure Works Cube  
        // The trace settings will output all progress notifications   
        // to the trace file  
        Database db = svr.Databases.FindByName("Adventure Works DW Multidimensional 2012");  
        Cube cube = db.Cubes.FindByName("Adventure Works");  
        cube.Process(ProcessType.ProcessFull);  
        #endregion  
  
        trc.Stop();  
        trc.Drop();  
  
}  
```  
  
##  <a name="CL"></a> Capturelog- und CaptureXml-Attribute  
 Das CaptureLog-Attribut ermöglicht Ihnen die Erstellung von XMLA-Batchdateien aus den AMO-Vorgängen. Mit CaptureLog können Sie Serverobjekte als Datenbanken, Cubes, Dimensionen, Miningstrukturen und anderes ausgeben.  
  
 Für die Erstellung eines CaptureLog sind folgende Schritte erforderlich:  
  
1.  Beginnen Sie mit der Aufzeichnung des XMLA-Protokolls, indem Sie das CaptureXml-Serverattribut auf `true` einstellen.  
  
     Durch diese Option werden alle AMO-Vorgänge nicht zum Server gesendet, sondern in eine Zeichenfolgenauflistung gespeichert.  
  
2.  Starten Sie die AMO-Aktivität wie üblich, aber denken Sie daran, dass keine Aktion an den Server gesendet wird. Aktivitäten können Vorgänge wie Verarbeiten, Erstellen, Löschen, Aktualisieren oder jede andere Aktion an einem Objekt umfassen.  
  
3.  Beenden Sie die Aufzeichnung des XMLA-Protokolls, indem Sie CaptureXml auf `false` zurücksetzen.  
  
4.  Überprüfen Sie die XMLA-Aufzeichnung, indem Sie entweder die einzelnen Zeichenfolgen in der CaptureLog-Zeichenfolgenauflistung überprüfen oder eine vollständige Zeichenfolge mit der ConcatenateCaptureLog-Methode erzeugen. Mit ConcatenateCaptureLog können Sie den XMLA-Batch als einzelne Transaktion generieren und dem Batch die parallele Prozessoption hinzufügen.  
  
 Im folgenden Beispiel wird eine Zeichenfolge mit den Batchbefehlen zurückgegeben, um für alle Dimensionen und alle Cubes einen vollständigen Prozess in der [Adventure Works DW Multidimensional 2012]-Datenbank auszuführen.  
  
```  
static public string TestCaptureLog(Server svr)  
{  
    String capturedXmla = "";  
    if ((svr != null) && (svr.Connected))  
    {  
        svr.CaptureXml = true;  
  
        #region Actions to be captured to an XMLA file  
        //No action is executed during CaptureXml = true  
        Database db = svr.Databases.FindByName("Adventure Works DW Multidimensional 2012");  
        foreach (Dimension dim in db.Dimensions)  
            dim.Process(ProcessType.ProcessFull);  
        foreach (Cube cube in db.Cubes)  
            cube.Process(ProcessType.ProcessFull);  
        #endregion  
  
        svr.CaptureXml = false;  
  
        capturedXmla = svr.ConcatenateCaptureLog(true, true);  
  
    }  
  
    return capturedXmla;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.AnalysisServices>   
 [Einführung in AMO-Klassen](amo-classes-introduction.md)   
 [AMO andere Klassen und Methoden](amo-other-classes-and-methods.md)   
 [Logische Architektur &#40;Analysis Services – mehrdimensionale Daten&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Datenbankobjekte &#40;Analysis Services – mehrdimensionale Daten&#41;](../olap-logical/database-objects-analysis-services-multidimensional-data.md)   
 [Verarbeitung von mehrdimensionalen Modellobjekten](../processing-a-multidimensional-model-analysis-services.md)  
  
  
