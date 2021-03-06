---
title: Verwenden des Aufzeichnungsmodus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, capture mode
- capture mode [SMO]
- SMO [SQL Server], capture mode
ms.assetid: ace29bf0-705a-434f-82e4-db99d01c5008
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5195430b502873c79d3962270ffddd19121a5e62
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129200"
---
# <a name="using-capture-mode"></a>Verwenden des Aufzeichnungsmodus
  SMO-Programme können die entsprechenden [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen, die vom Programm anstelle der ausgeführten Anweisungen (oder zusätzlich zu diesen) ausgegeben werden, aufzeichnen. Sie können den Aufzeichnungsmodus mithilfe des <xref:Microsoft.SqlServer.Management.Common.ServerConnection>-Objekts oder mithilfe der <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>-Eigenschaft des <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekts aktivieren.  
  
## <a name="example"></a>Beispiel  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="enabling-capture-mode-in-visual-basic"></a>Aktivieren des Aufzeichnungsmodus in Visual Basic  
 In diesem Codebeispiel wird zunächst der Aufzeichnungsmodus aktiviert, anschließend werden die im Aufzeichnungspuffer enthaltenen [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Befehle angezeigt.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBCapture1](SMO How to#SMO_VBCapture1)]  -->  
  
## <a name="enabling-capture-mode-in-visual-c"></a>Aktivieren des Aufzeichnungsmodus in Visual C#  
 In diesem Codebeispiel wird zunächst der Aufzeichnungsmodus aktiviert, anschließend werden die im Aufzeichnungspuffer enthaltenen [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Befehle angezeigt.  
  
```  
{   
// Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
// Set the execution mode to CaptureSql for the connection.   
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.CaptureSql;   
// Make a modification to the server that is to be captured.   
srv.UserOptions.AnsiNulls = true;   
srv.Alter();   
// Iterate through the strings in the capture buffer and display the captured statements.   
string s;   
foreach ( String p_s in srv.ConnectionContext.CapturedSql.Text ) {   
   Console.WriteLine(p_s);   
}   
// Execute the captured statements.   
srv.ConnectionContext.ExecuteNonQuery(srv.ConnectionContext.CapturedSql.Text);   
// Revert to immediate execution mode.   
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.ExecuteSql;   
}  
```  
  
  
