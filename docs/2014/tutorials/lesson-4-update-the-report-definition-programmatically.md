---
title: 'Lektion 4: Aktualisieren die Berichtsdefinition programmgesteuert | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 1f0a1d46-6d6d-4f67-b51e-06dbbbffacf9
author: craigg-msft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5b1b996e2135953e862b27d992d22c6a7666904c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48137130"
---
# <a name="lesson-4-update-the-report-definition-programmatically"></a>Lektion 4: Programmgesteuertes Update der Berichtsdefinition
  Nachdem die Berichtsdefinition vom Berichtsserver geladen wurde und mit dem Berichtsfelds ein Verweis darauf vorhanden ist, müssen Sie die Berichtsdefinition aktualisieren. In diesem Beispiel aktualisieren Sie die `Description` -Eigenschaft für den Bericht.  
  
### <a name="to-update-the-report-definition"></a>So aktualisieren Sie die Berichtsdefinition  
  
1.  Ersetzen Sie den Code für die UpdateReportDefinition()-Methode in der Datei Program.cs (Module1.vb für [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) durch den folgenden Code:  
  
    ```csharp  
    private void UpdateReportDefinition()  
    {  
        System.Console.WriteLine("Updating Report Definition");  
  
        // Create a list of the Items Choices for the Report. The   
        // ItemsChoiceType118 enum represents all the properties  
        // available in the report and the ItemsElementName   
        // represents the properties that exist in the current   
        // instance of the report.  
        List<ItemsChoiceType118> _reportItems =   
            new List<ItemsChoiceType118>(_report.ItemsElementName);  
  
        // Locate the index for the Description property  
        int index = _reportItems.IndexOf(  
            ItemsChoiceType118.Description);  
  
        // The Description item is of type StringLocIDType, so   
        // cast the item type first and then assign new value.  
        System.Console.WriteLine("- Old Description: " +   
            ((StringLocIDType)_report.Items[index]).Value );  
  
        // Update the Description for the Report  
        ((StringLocIDType)_report.Items[index]).Value =   
            "New Report Description";  
  
        System.Console.WriteLine("- New Description: " +   
            ((StringLocIDType)_report.Items[index]).Value );  
    }  
    ```  
  
    ```vb  
    Private Sub UpdateReportDefinition()  
  
        System.Console.WriteLine("Updating Report Definition")  
  
        'Create a list of the Items Choices for the Report. The   
        'ItemsChoiceType118 enum represents all the properties  
        'available in the report and the ItemsElementName   
        'represents the properties that exist in the current   
        'instance of the report.  
        Dim reportItems As List(Of ItemsChoiceType118) = _  
            New List(Of ItemsChoiceType118)(m_report.ItemsElementName)  
  
        'Locate the index for the Description property  
        Dim index As Integer = _  
            reportItems.IndexOf(ItemsChoiceType118.Description)  
  
        'The Description item is of type StringLocIDType, so   
        'cast the item type first and then assign new value.  
        System.Console.WriteLine("- Old Description: " & _  
            DirectCast(m_report.Items(index), StringLocIDType).Value)  
  
        'Update the Description for the Report  
        DirectCast(m_report.Items(index), StringLocIDType).Value = _  
            "New Report Description"  
  
        System.Console.WriteLine("- New Description: " & _  
            DirectCast(m_report.Items(index), StringLocIDType).Value)  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a>Nächste Lektion  
 In der nächsten Lektion speichern Sie die aktualisierte Berichtsdefinition wieder auf dem Berichtsserver. Finden Sie unter [Lektion 5: Veröffentlichen der Berichtsdefinition auf dem Berichtsserver](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aktualisieren von Berichten mithilfe von Klassen, die aus dem RDL-Schema generiert &#40;SSRS-Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)  
  
  
