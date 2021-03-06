---
title: Aktualisieren von Formularbereichen in Outlook-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5195e9a268a38212f12d554eb5a86f4e923af421
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="updating-form-regions-in-outlook-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Aktualisieren von Formularbereichen in Outlook-Projekten, die zu .NET Framework 4 oder .NET Framework 4.5 migriert werden
  Wenn das Zielframework eines Outlook VSTO-Add-In-Projekts mit einem Formularbereich in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher geändert wird, müssen Sie einige Änderungen am generierten Formularbereichscode und an Code vornehmen, durch den bestimmte Formularbereichsklassen zur Laufzeit instanziiert werden.  
  
## <a name="updating-the-generated-form-region-code"></a>Aktualisieren des generierten Formularbereichscodes  
 Wenn das Zielframework des Projekts in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher geändert wird, müssen Sie den generierten Formularbereichscode ändern. Die vorgenommenen Änderungen sind bei Formularbereichen, die Sie in Visual Studio entworfen haben, und Formularbereichen, die Sie aus Outlook importiert haben, unterschiedlich. Weitere Informationen zu den Unterschieden zwischen diesen Formularbereichstypen finden Sie unter [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
#### <a name="to-update-the-generated-code-for-a-form-region-that-you-designed-in-visual-studio"></a>So aktualisieren Sie den generierten Code für einen in Visual Studio entworfenen Formularbereich  
  
1.  Öffnen Sie die CodeBehind-Datei des Formularbereichs im Code-Editor. Diese Datei hat den Namen " *IhrFormularbereich*.Designer.cs" oder " *IhrFormularbereich*.Designer.vb". Klicken Sie im **Projektmappen-Explorer** auf die Schaltfläche **Alle Dateien anzeigen**, um diese Datei in Visual Basic-Projekten anzuzeigen.  
  
2.  Ändern Sie die Deklaration der Formularbereichsklasse, sodass es abgeleitet <xref:Microsoft.Office.Tools.Outlook.FormRegionBase> statt Microsoft.Office.Tools.Outlook.FormRegionControl.  
  
3.  Ändern Sie den Konstruktor der Formularbereichklasse, wie in den folgenden Codebeispielen dargestellt.  
  
     Im folgenden Codebeispiel wird der Konstruktor einer Formularbereichsklasse in einem Projekt dargestellt, das auf .NET Framework 3.5 ausgerichtet ist.  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(formRegion)  
        Me.InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(formRegion)  
    {  
        this.InitializeComponent();  
    }  
    ```  
  
     Im folgenden Codebeispiel wird der Konstruktor einer Formularbereichsklasse in einem Projekt dargestellt, das auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]ausgerichtet ist.  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(Globals.Factory, formRegion)  
        Me.InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(Globals.Factory, formRegion)  
    {  
        this.InitializeComponent();  
    }  
    ```  
  
4.  Ändern Sie die Signatur der `InitializeManifest` -Methode, wie unten dargestellt. Stellen Sie sicher, dass Sie den Code in der Methode nicht ändern. Dieser Code stellt Formularbereichseinstellungen dar, die Sie im Designer angewendet haben. In Visual C#-Projekten müssen Sie den Bereich mit der Bezeichnung `Form Region Designer generated code` erweitern, um diese Methode anzuzeigen.  
  
     Im folgenden Codebeispiel wird die Signatur der `InitializeManifest` -Methode in einem Projekt dargestellt, das auf .NET Framework 3.5 ausgerichtet ist.  
  
    ```vb  
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest)  
  
        ' Do not change code in this method.  
    End Sub  
    ```  
  
    ```csharp  
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest)  
    {  
        // Do not change code in this method.  
    }  
    ```  
  
     Im folgenden Codebeispiel wird die Signatur der `InitializeManifest` -Methode in einem Projekt dargestellt, das auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]ausgerichtet ist.  
  
    ```vb  
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest,   
        ByVal factory As Microsoft.Office.Tools.Outlook.Factory)  
  
        ' Do not change code in this method.  
    End Sub  
    ```  
  
    ```csharp  
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest,   
        Microsoft.Office.Tools.Outlook.Factory factory)  
    {  
        // Do not change code in this method.  
    }  
    ```  
  
5.  Fügen Sie Ihrem Projekt ein neues Outlook-Formularbereichselement hinzu. Öffnen Sie die CodeBehind-Datei für den neuen Formularbereich, suchen Sie die *YourNewFormRegion*`Factory` - und `WindowFormRegionCollection` -Klassen in der Datei, und kopieren Sie diese Klassen in die Zwischenablage.  
  
6.  Löschen Sie den neuen Formularbereich, den Sie dem Projekt hinzugefügt haben.  
  
7.  Suchen Sie in der CodeBehind-Datei des Formularbereichs, den Sie aktualisieren, damit er im neu ausgerichteten Projekt funktioniert, die *YourOriginalFormRegion*`Factory` - und `WindowFormRegionCollection` -Klassen, und ersetzen Sie sie durch den Code, den Sie aus dem neuen Formularbereich kopiert haben.  
  
8.  Suchen Sie in den *YourNewFormRegion*`Factory` - und `WindowFormRegionCollection` -Klassen alle Verweise auf die *YourNewFormRegion* -Klasse, und ändern Sie jeden Verweis stattdessen in die *YourOriginalFormRegion* -Kasse. Wenn der aktualisierte Formularbereich z. B. `SalesDataFormRegion` und der neue in Schritt 5 erstellte Formularbereich `FormRegion1`heißt, ändern Sie alle Verweise von `FormRegion1` in `SalesDataFormRegion`.  
  
#### <a name="to-update-the-generated-code-for-a-form-region-that-you-imported-from-outlook"></a>So aktualisieren Sie den generierten Code für einen aus Outlook importierten Formularbereich  
  
1.  Öffnen Sie die CodeBehind-Datei des Formularbereichs im Code-Editor. Diese Datei hat den Namen " *IhrFormularbereich*.Designer.cs" oder " *IhrFormularbereich*.Designer.vb". Klicken Sie im **Projektmappen-Explorer** auf die Schaltfläche **Alle Dateien anzeigen**, um diese Datei in Visual Basic-Projekten anzuzeigen.  
  
2.  Ändern Sie die Deklaration der Formularbereichsklasse, sodass es abgeleitet <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase> statt Microsoft.Office.Tools.Outlook.ImportedFormRegion.  
  
3.  Ändern Sie den Konstruktor der Formularbereichklasse, wie in den folgenden Codebeispielen dargestellt.  
  
     Im folgenden Codebeispiel wird der Konstruktor einer Formularbereichsklasse in einem Projekt dargestellt, das auf .NET Framework 3.5 ausgerichtet ist.  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(formRegion)  
    End Sub  
    ```  
  
    ```csharp  
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(formRegion)  
    {  
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);  
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);  
    }  
    ```  
  
     Im folgenden Codebeispiel wird die Signatur des Konstruktors einer Formularbereichsklasse in einem Projekt dargestellt, das auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]ausgerichtet ist.  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(Globals.Factory, formRegion)  
    End Sub  
    ```  
  
    ```csharp  
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(Globals.Factory, formRegion)  
    {  
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);  
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);  
    }  
    ```  
  
4.  Ändern Sie für jede Codezeile in der `InitializeControls` -Methode, die ein Steuerelement in der Formularbereichsklasse initialisiert, den Code wie unten dargestellt.  
  
     Im folgenden Codebeispiel wird veranschaulicht, wie ein Steuerelement in einem Projekt initialisiert wird, das auf .NET Framework 3.5 ausgerichtet ist. In diesem Code verfügt die GetFormRegionControl-Methode einen Typparameter, der den Typ des Steuerelements angibt, der zurückgegeben wird.  
  
    ```vb  
    Me.olkTextBox1 = Me.GetFormRegionControl(Of Microsoft.Office.Interop.Outlook.OlkTextBox)("OlkTextBox1")  
    ```  
  
    ```csharp  
    this.olkTextBox1 = this.GetFormRegionControl<Microsoft.Office.Interop.Outlook.OlkTextBox>("OlkTextBox1");  
    ```  
  
     Im folgenden Codebeispiel wird veranschaulicht, wie ein Steuerelement in einem Projekt initialisiert wird, das auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]ausgerichtet ist. In diesem Code weist die <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase.GetFormRegionControl%2A> -Methode keinen Typparameter auf. Sie müssen den Rückgabewert in den Typ des Steuerelements umwandeln, das Sie initialisieren.  
  
    ```vb  
    Me.olkTextBox1 = CType(GetFormRegionControl("OlkTextBox1"), Microsoft.Office.Interop.Outlook.OlkTextBox)  
    ```  
  
    ```csharp  
    this.olkTextBox1 = (Microsoft.Office.Interop.Outlook.OlkTextBox)GetFormRegionControl("OlkTextBox1");  
    ```  
  
5.  Fügen Sie Ihrem Projekt ein neues Outlook-Formularbereichselement hinzu. Öffnen Sie die CodeBehind-Datei für den neuen Formularbereich, suchen Sie die *YourNewFormRegion*`Factory` - und `WindowFormRegionCollection` -Klassen in der Datei, und kopieren Sie diese Klassen in die Zwischenablage.  
  
6.  Löschen Sie den neuen Formularbereich, den Sie dem Projekt hinzugefügt haben.  
  
7.  Suchen Sie in der CodeBehind-Datei des Formularbereichs, den Sie aktualisieren, damit er im neu ausgerichteten Projekt funktioniert, die *YourOriginalFormRegion*`Factory` - und `WindowFormRegionCollection` -Klassen, und ersetzen Sie sie durch den Code, den Sie aus dem neuen Formularbereich kopiert haben.  
  
8.  Suchen Sie in den *YourNewFormRegion*`Factory` - und `WindowFormRegionCollection` -Klassen alle Verweise auf die *YourNewFormRegion* -Klasse, und ändern Sie jeden Verweis stattdessen in die *YourOriginalFormRegion* -Kasse. Wenn der aktualisierte Formularbereich z. B. `SalesDataFormRegion` und der neue in Schritt 5 erstellte Formularbereich `FormRegion1`heißt, ändern Sie alle Verweise von `FormRegion1` in `SalesDataFormRegion`.  
  
## <a name="instantiating-form-region-classes"></a>Instanziieren von Formularbereichklassen  
 Sie müssen jeden Code ändern, durch den bestimmte Formularbereichsklassen dynamisch instanziiert werden. In Projekten, die auf .NET Framework 3.5 abzielen, können Sie Formularbereichklassen wie z. B. Microsoft.Office.Tools.Outlook.FormRegionManifest nicht direkt instanziieren. In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, sind diese Klassen Schnittstellen, die Sie nicht direkt instanziieren können.  
  
 Wenn das Zielframework des Projekts, um geändert wird die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher müssen Sie die Schnittstellen instanziieren, mithilfe der Methoden, die von der Eigenschaft Globals.Factory bereitgestellt werden. Weitere Informationen zur Eigenschaft Globals.Factory finden Sie unter [globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).  
  
 In der folgenden Tabelle sind die Formularbereichstypen und die Methode aufgeführt, die zum Instanziieren der Typen in Projekten verwendet wird, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind.  
  
|Typ|Zu verwendende Factorymethode|  
|----------|---------------------------|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|  
  
## <a name="see-also"></a>Siehe auch  
 [Migrieren von Office-Projektmappen zu .NET Framework 4 oder höher](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)  
  