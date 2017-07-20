---
title: "Exemplarische Vorgehensweise: Anzeigen von benutzerdefinierten Aufgabenbereichen in E-Mails in Outlook"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Outlook [Office-Entwicklung in Visual Studio], benutzerdefinierte Aufgabenbereiche"
  - "Aufgabenbereiche [Office-Entwicklung in Visual Studio], Anzeigen in E-Mails"
  - "Anzeigen von benutzerdefinierten Aufgabenbereichen in E-Mails"
  - "E-Mail [Office-Entwicklung in Visual Studio], benutzerdefinierte Aufgabenbereiche angezeigt in"
  - "Benutzerdefinierte Aufgabenbereiche [Office-Entwicklung in Visual Studio], Anzeigen in E-Mails"
ms.assetid: 04943967-a7ef-4876-9584-84ada427e3f3
caps.latest.revision: 59
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 58
---
# Exemplarische Vorgehensweise: Anzeigen von benutzerdefinierten Aufgabenbereichen in E-Mails in Outlook
  Diese exemplarische Vorgehensweise veranschaulicht, wie eine eindeutige Instanz eines benutzerdefinierten Aufgabenbereichs in jeder erstellten oder geöffneten E\-Mail angezeigt wird. Benutzer können den benutzerdefinierten Aufgabenbereich über eine Schaltfläche auf dem Menüband jeder E\-Mail anzeigen oder ausblenden.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Wenn Sie einen benutzerdefinierten Aufgabenbereich mit mehreren Explorer\- oder Inspektor\-Fenstern anzeigen möchten, müssen Sie eine Instanz des benutzerdefinierten Aufgabenbereichs für jedes geöffnete Fenster erstellen. Weitere Informationen über das Verhalten benutzerdefinierter Aufgabenbereiche in Outlook\-Fenstern finden Sie unter [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md).  
  
> [!NOTE]  
>  In dieser exemplarischen Vorgehensweise wird der VSTO\-Add\-In\-Code in kleinen Abschnitten dargestellt, um die dem Code zugrunde liegende Logik einfacher zu erläutern.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Entwerfen der Benutzeroberfläche des benutzerdefinierten Aufgabenbereichs  
  
-   Erstellen einer benutzerdefinierten Menüband\-Benutzeroberfläche  
  
-   Anzeigen der benutzerdefinierten Menüband\-Benutzeroberfläche in E\-Mails  
  
-   Erstellen einer Klasse zum Verwalten von Inspektor\-Fenstern und benutzerdefinierten Aufgabenbereichen  
  
-   Initialisieren und Bereinigen von Ressourcen, die durch das VSTO\-Add\-In verwendet werden  
  
-   Synchronisieren der Umschaltfläche des Menübands mit dem benutzerdefinierten Aufgabenbereich  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio\-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] oder Microsoft Outlook 2010.  
  
 ![Link zu Video](../vsto/media/playvideo.png "Link zu Video") Eine entsprechende Videodemo finden Sie unter [Gewusst wie: Verwenden von Aufgabenbereichen in Outlook](http://go.microsoft.com/fwlink/?LinkID=130309).  
  
## Erstellen des Projekts  
 Benutzerdefinierte Aufgabenbereiche werden in VSTO\-Add\-Ins implementiert. Beginnen Sie mit der Erstellung eines VSTO\-Add\-In\-Projekts für Outlook.  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein **Outlook\-Add\-In**\-Projekt mit dem Namen **OutlookMailItemTaskPane**. Verwenden Sie die Projektvorlage **Outlook\-Add\-In**. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] öffnet die Codedatei **ThisAddIn.cs** oder **ThisAddIn.vb** und fügt dem **Projektmappen\-Explorer** das **OutlookMailItemTaskPane**\-Projekt hinzu.  
  
## Entwerfen der Benutzeroberfläche des benutzerdefinierten Aufgabenbereichs  
 Es gibt keinen visuellen Designer für benutzerdefinierte Aufgabenbereiche, Sie können aber dennoch ein Benutzersteuerelement mit der gewünschten Benutzeroberfläche entwerfen. Der benutzerdefinierte Aufgabenbereich in diesem VSTO\-Add\-In entspricht einer einfachen Benutzeroberfläche, die ein <xref:System.Windows.Forms.TextBox>\-Steuerelement enthält. Im weiteren Verlauf dieser exemplarischen Vorgehensweise fügen Sie dem benutzerdefinierten Aufgabenbereich das Benutzersteuerelement hinzu.  
  
#### So entwerfen Sie die Benutzeroberfläche des benutzerdefinierten Aufgabenbereichs  
  
1.  Klicken Sie im **Projektmappen\-Explorer** auf das Projekt **OutlookMailItemTaskPane**.  
  
2.  Klicken Sie im Menü **Projekt** auf **Benutzersteuerelement hinzufügen**.  
  
3.  Ändern Sie im Dialogfeld **Neues Element hinzufügen** den Namen des Benutzersteuerelements in **TaskPaneControl**, und klicken Sie dann auf **Hinzufügen**.  
  
     Das Benutzersteuerelement wird im Designer geöffnet.  
  
4.  Ziehen Sie ein **TextBox**\-Steuerelement von der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** auf das Benutzersteuerelement.  
  
## Entwerfen der Benutzeroberfläche des Menübands  
 Eines der Ziele dieses VSTO\-Add\-Ins besteht darin, Benutzern über das Menüband jeder E\-Mail das Anzeigen oder Ausblenden des benutzerdefinierten Aufgabenbereichs zu ermöglichen. Wenn Sie die Benutzeroberfläche bereitstellen möchten, erstellen Sie eine benutzerdefinierte Menüband\-Benutzeroberfläche mit einer Umschaltfläche, über die Benutzer den benutzerdefinierten Aufgabenbereich durch Klicken anzeigen oder ausblenden können.  
  
#### So erstellen Sie eine benutzerdefinierte Menüband\-Benutzeroberfläche  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Menüband \(Visueller Designer\)** aus.  
  
3.  Ändern Sie den Namen des neuen Menübands in **ManageTaskPaneRibbon**, und klicken Sie auf **Hinzufügen**.  
  
     Die Datei **ManageTaskPaneRibbon.cs** oder **ManageTaskPaneRibbon.vb** wird im Menüband\-Designer geöffnet. Sie enthält eine Standardregisterkarte und \-gruppe.  
  
4.  Klicken Sie im Menüband\-Designer auf **group1**.  
  
5.  Legen Sie im Fenster **Eigenschaften** die Eigenschaft **Label** auf **Task Pane Manager** fest.  
  
6.  Ziehen Sie ein ToggleButton\-Steuerelement von der Registerkarte **Steuerelemente für Office\-Menübänder** der **Toolbox** auf die Gruppe **Task Pane Manager**.  
  
7.  Klicken Sie auf **toggleButton1**.  
  
8.  Legen Sie im Fenster **Eigenschaften** die Eigenschaft **Label** auf **Aufgabenbereich anzeigen** fest.  
  
## Anzeigen der benutzerdefinierten Menüband\-Benutzeroberfläche in E\-Mails  
 Der in dieser exemplarischen Vorgehensweise erstellte benutzerdefinierte Aufgabenbereich ist so konzipiert, dass er nur in Inspektor\-Fenstern angezeigt wird, die E\-Mails enthalten. Lesen Sie die Eigenschaften daher so fest, dass die benutzerdefinierte Menüband\-Benutzeroberfläche nur in diesen Fenstern angezeigt wird.  
  
#### So zeigen Sie die benutzerdefinierte Menüband\-Benutzeroberfläche in E\-Mails an  
  
1.  Klicken Sie im Menüband\-Designer auf das Menüband **ManageTaskPaneRibbon**.  
  
2.  Klicken Sie im Fenster **Eigenschaften** auf die Dropdownliste neben **RibbonType**, und wählen Sie **Microsoft.Outlook.Mail.Compose** und **Microsoft.Outlook.Mail.Read** aus.  
  
## Erstellen einer Klasse zum Verwalten von Inspektor\-Fenstern und benutzerdefinierten Aufgabenbereichen  
 Es gibt mehrere Fälle, in denen das VSTO\-Add\-In angeben muss, welcher benutzerdefinierte Aufgabenbereich einer bestimmten E\-Mail zugeordnet ist. Dazu gehören folgende Situationen:  
  
-   Der Benutzer schließt eine E\-Mail. In diesem Fall muss das VSTO\-Add\-In den entsprechenden benutzerdefinierten Aufgabenbereich entfernen, um sicherzustellen, dass die vom VSTO\-Add\-In verwendeten Ressourcen ordnungsgemäß bereinigt werden.  
  
-   Der Benutzer schließt den benutzerdefinierten Aufgabenbereich. In diesem Fall muss das VSTO\-Add\-In den Zustand der Umschaltfläche auf dem Menüband der E\-Mail aktualisieren.  
  
-   Der Benutzer klickt auf die Umschaltfläche auf dem Menüband. In diesem Fall muss das VSTO\-Add\-In den entsprechenden Aufgabenbereich anzeigen oder ausblenden.  
  
 Damit das VSTO\-Add\-In nachverfolgen kann, welcher benutzerdefinierte Aufgabenbereich den einzelnen geöffneten E\-Mails zugeordnet ist, erstellen Sie eine benutzerdefinierte Klasse, die Paare von <xref:Microsoft.Office.Interop.Outlook.Inspector>\- und <xref:Microsoft.Office.Tools.CustomTaskPane>\-Objekten umschließt. Diese Klasse erstellt für jede E\-Mail ein neues Objekt für einen benutzerdefinierten Aufgabenbereich und löscht den benutzerdefinierten Aufgabenbereich, sobald die entsprechende E\-Mail geschlossen wird.  
  
#### So erstellen Sie eine Klasse zum Verwalten von Inspektor\-Fenstern und benutzerdefinierten Aufgabenbereichen  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf die Datei **ThisAddIn.cs** oder **ThisAddIn.vb**, und klicken Sie dann auf **Code anzeigen**.  
  
2.  Fügen Sie am Anfang der Datei die folgenden Anweisungen ein.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_OutlookMailItemTaskPane#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#2)]  
  
3.  Fügen Sie der Datei **ThisAddIn.cs** oder **ThisAddIn.vb** folgenden Code außerhalb der `ThisAddIn`\-Klasse hinzu \(für Visual C\# fügen Sie diesen Code im `OutlookMailItemTaskPane`\-Namespace hinzu\). Die `InspectorWrapper`\-Klasse verwaltet ein Paar von <xref:Microsoft.Office.Interop.Outlook.Inspector>\- und <xref:Microsoft.Office.Tools.CustomTaskPane>\-Objekten. Sie schließen die Definition dieser Klasse in den folgenden Schritten ab.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_OutlookMailItemTaskPane#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#3)]  
  
4.  Fügen Sie nach dem Code, den Sie im vorherigen Schritt hinzugefügt haben, den folgenden Konstruktor hinzu. Dieser Konstruktor erstellt und initialisiert einen neuen benutzerdefinierten Aufgabenbereich, der dem übergebenen <xref:Microsoft.Office.Interop.Outlook.Inspector>\-Objekt zugeordnet ist. In C\# fügt der Konstruktor außerdem Ereignishandler an das <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close>\-Ereignis des <xref:Microsoft.Office.Interop.Outlook.Inspector>\-Objekts und das <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>\-Ereignis des <xref:Microsoft.Office.Tools.CustomTaskPane>\-Objekts an.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_OutlookMailItemTaskPane#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#4)]  
  
5.  Fügen Sie nach dem Code, den Sie im vorherigen Schritt hinzugefügt haben, die folgende Methode hinzu. Diese Methode ist ein Ereignishandler für das <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>\-Ereignis des in der `InspectorWrapper`\-Klasse enthaltenen <xref:Microsoft.Office.Tools.CustomTaskPane>\-Objekts. Dieser Code aktualisiert den Zustand der Umschaltfläche, sobald der Benutzer den benutzerdefinierten Aufgabenbereich öffnet oder schließt.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_OutlookMailItemTaskPane#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#5)]  
  
6.  Fügen Sie nach dem Code, den Sie im vorherigen Schritt hinzugefügt haben, die folgende Methode hinzu. Diese Methode ist ein Ereignishandler für das <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close>\-Ereignis des <xref:Microsoft.Office.Interop.Outlook.Inspector>\-Objekts, das die aktuelle E\-Mail enthält. Der Ereignishandler gibt Ressourcen frei, sobald die E\-Mail geschlossen wird. Der Ereignishandler entfernt auch den aktuellen benutzerdefinierten Aufgabenbereich aus der `CustomTaskPanes`\-Auflistung. Dadurch wird die Erstellung mehrerer Instanzen des benutzerdefinierten Aufgabenbereichs verhindert, wenn die nächste E\-Mail geöffnet wird.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_OutlookMailItemTaskPane#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#6)]  
  
7.  Fügen Sie nach dem Code, den Sie im vorherigen Schritt hinzugefügt haben, den folgenden Code hinzu. Weiter unten in dieser exemplarischen Vorgehensweise rufen Sie diese Eigenschaft von einer Methode in der benutzerdefinierten Menüband\-Benutzeroberfläche auf, um den benutzerdefinierten Aufgabenbereich anzuzeigen oder auszublenden.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_OutlookMailItemTaskPane#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#7)]  
  
## Initialisieren und Bereinigen der vom Add\-In verwendeten Ressourcen  
 Fügen Sie der `ThisAddIn`\-Klasse Code hinzu, durch den das VSTO\-Add\-In beim Laden initialisiert und die vom VSTO\-Add\-In verwendeten Ressourcen beim Entladen des Add\-Ins bereinigt werden. Sie initialisieren das VSTO\-Add\-In, indem Sie einen Ereignishandler für das <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>\-Ereignis einrichten und alle vorhandenen E\-Mails an diesen Ereignishandler übergeben. Sobald das VSTO\-Add\-In entladen wird, trennen Sie den Ereignishandler und bereinigen die vom VSTO\-Add\-In verwendeten Objekte.  
  
#### So initialisieren und bereinigen Sie die vom VSTO\-Add\-In verwendeten Ressourcen  
  
1.  Suchen Sie in der Datei **ThisAddIn.cs** oder **ThisAddIn.vb** die Definition der `ThisAddIn`\-Klasse.  
  
2.  Fügen Sie der `ThisAddIn`\-Klasse die folgenden Deklarationen hinzu:  
  
    -   Das `inspectorWrappersValue`\-Feld enthält alle vom VSTO\-Add\-In verwalteten <xref:Microsoft.Office.Interop.Outlook.Inspector>\- und `InspectorWrapper`\-Objekte.  
  
    -   Das `inspectors`\-Feld behält einen Verweis auf die Auflistung von Inspektor\-Fenstern in der aktuellen Outlook\-Instanz. Dieser Verweis verhindert, dass der Garbage Collector den Arbeitsspeicher freigibt, der den Ereignishandler für das <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>\-Ereignis enthält, das Sie im nächsten Schritt deklarieren.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#8)]
     [!code-vb[Trin_OutlookMailItemTaskPane#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#8)]  
  
3.  Ersetzen Sie die `ThisAddIn_Startup`\-Methode durch folgenden Code: Dieser Code fügt einen Ereignishandler an das <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>\-Ereignis an und übergibt alle vorhandenen <xref:Microsoft.Office.Interop.Outlook.Inspector>\-Objekte an den Ereignishandler. Wenn der Benutzer das VSTO\-Add\-In bei ausgeführtem Outlook lädt, verwendet das VSTO\-Add\-In diese Informationen, um benutzerdefinierte Aufgabenbereiche für alle bereits geöffneten E\-Mails zu erstellen.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_OutlookMailItemTaskPane#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#9)]  
  
4.  Ersetzen Sie die `ThisAddIn_ShutDown`\-Methode durch folgenden Code: Dieser Code trennt den <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>\-Ereignishandler und bereinigt die vom VSTO\-Add\-In verwendeten Objekte.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_OutlookMailItemTaskPane#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#10)]  
  
5.  Fügen Sie der `ThisAddIn`\-Klasse den folgenden <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>\-Ereignishandler hinzu. Wenn ein neuer <xref:Microsoft.Office.Interop.Outlook.Inspector> eine E\-Mail enthält, erstellt die Methode eine Instanz eines neuen `InspectorWrapper`\-Objekts, das die Beziehung zwischen der E\-Mail und dem entsprechenden Aufgabenbereich verwaltet.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_OutlookMailItemTaskPane#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#11)]  
  
6.  Fügen Sie der `ThisAddIn`\-Klasse folgende Eigenschaft hinzu. Diese Eigenschaft macht das private `inspectorWrappersValue`\-Feld für Code außerhalb der `ThisAddIn`\-Klasse verfügbar.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_OutlookMailItemTaskPane#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#12)]  
  
## Checkpoint  
 Erstellen Sie Ihr Projekt, um sicherzustellen, dass es ohne Fehler kompiliert wird.  
  
#### So erstellen Sie das Projekt  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projekt **OutlookMailItemTaskPane**, und klicken Sie dann auf **Erstellen**. Vergewissern Sie sich, dass das Projekt ohne Fehler kompiliert wurde.  
  
## Synchronisieren der Umschaltfläche des Menübands mit dem benutzerdefinierten Aufgabenbereich  
 Die Umschaltfläche erscheint gedrückt, wenn der Aufgabenbereich sichtbar ist, und nicht gedrückt, wenn der Aufgabenbereich ausgeblendet ist. Wenn Sie den Zustand der Schaltfläche mit dem benutzerdefinierten Aufgabenbereich synchronisieren möchten, ändern Sie den <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>\-Ereignishandler der Umschaltfläche.  
  
#### So synchronisieren Sie den benutzerdefinierten Aufgabenbereich mit der Umschaltfläche  
  
1.  Doppelklicken Sie im Menüband\-Designer auf die Umschaltfläche **Aufgabenbereich anzeigen**.  
  
     Visual Studio generiert automatisch einen Ereignishandler namens `toggleButton1_Click`, der das <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>\-Ereignis der Umschaltfläche verarbeitet. Visual Studio öffnet außerdem die Datei **ManageTaskPaneRibbon.cs** oder **ManageTaskPaneRibbon.vb** im Code\-Editor.  
  
2.  Fügen Sie die folgenden Anweisungen am Anfang der Datei **ManageTaskPaneRibbon.cs** oder **ManageTaskPaneRibbon.vb** ein.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ManageTaskPaneRibbon.cs#14)]
     [!code-vb[Trin_OutlookMailItemTaskPane#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ManageTaskPaneRibbon.vb#14)]  
  
3.  Ersetzen Sie den `toggleButton1_Click`\-Ereignishandler durch den folgenden Code. Wenn der Benutzer auf die Umschaltfläche klickt, wird der benutzerdefinierte Aufgabenbereich, der dem aktuellen Inspektor\-Fenster zugeordnet ist, durch diese Methode angezeigt oder ausgeblendet.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ManageTaskPaneRibbon.cs#15)]
     [!code-vb[Trin_OutlookMailItemTaskPane#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ManageTaskPaneRibbon.vb#15)]  
  
## Testen des Projekts  
 Sobald Sie das Debuggen des Projekts starten, wird Outlook geöffnet und das VSTO\-Add\-In geladen. Das VSTO\-Add\-In zeigt mit jeder geöffneten E\-Mail eine eindeutige Instanz des benutzerdefinierten Aufgabenbereichs an. Erstellen Sie mehrere neue E\-Mails, um den Code zu testen.  
  
#### So testen Sie das VSTO\-Add\-In  
  
1.  Drücken Sie F5.  
  
2.  Klicken Sie in Outlook auf **Neu**, um eine neue E\-Mail zu erstellen.  
  
3.  Klicken Sie auf dem Menüband der E\-Mail auf die Registerkarte **Add\-Ins**, und klicken Sie dann auf die Schaltfläche **Aufgabenbereich anzeigen**.  
  
     Überprüfen Sie, ob ein Aufgabenbereich mit dem Titel **Mein Aufgabenbereich** in der E\-Mail angezeigt wird.  
  
4.  Geben Sie im Aufgabenbereich **Erster Aufgabenbereich** in das Textfeld ein.  
  
5.  Schließen Sie den Aufgabenbereich.  
  
     Überprüfen Sie, ob sich der Zustand der Schaltfläche **Aufgabenbereich anzeigen** ändert, sodass sie nicht mehr gedrückt erscheint.  
  
6.  Klicken Sie erneut auf die Schaltfläche **Aufgabenbereich anzeigen**.  
  
     Stellen Sie sicher, dass der Aufgabenbereich geöffnet wird und das Textfeld weiterhin die Zeichenfolge **Erster Aufgabenbereich** enthält.  
  
7.  Klicken Sie in Outlook auf **Neu**, um eine zweite E\-Mail zu erstellen.  
  
8.  Klicken Sie auf dem Menüband der E\-Mail auf die Registerkarte **Add\-Ins**, und klicken Sie dann auf die Schaltfläche **Aufgabenbereich anzeigen**.  
  
     Überprüfen Sie, ob ein Aufgabenbereich mit dem Titel **Mein Aufgabenbereich** in der E\-Mail angezeigt wird und ob das Textfeld in diesem Aufgabenbereich leer ist.  
  
9. Geben Sie im Aufgabenbereich **Zweiter Aufgabenbereich** in das Textfeld ein.  
  
10. Setzen Sie den Fokus auf die erste E\-Mail.  
  
     Überprüfen Sie, ob in dem dieser E\-Mail zugeordneten Aufgabenbereich nach wie vor **Erster Aufgabenbereich** im Textfeld angezeigt wird.  
  
 Das VSTO\-Add\-In behandelt auch komplexere Szenarien, die Sie ausprobieren können. So können Sie z. B. das Verhalten bei der Anzeige von E\-Mails testen, indem Sie die Schaltflächen **Nächstes Element** und **Vorheriges Element** verwenden. Sie können auch das Verhalten testen, das sich beim Entladen des VSTO\-Add\-Ins, Öffnen mehrerer E\-Mails und erneuten Laden des VSTO\-Add\-Ins zeigt.  
  
## Nächste Schritte  
 Weitere Informationen über das Erstellen benutzerdefinierter Aufgabenbereiche finden Sie in den folgenden Themen:  
  
-   Erstellen eines benutzerdefinierten Aufgabenbereichs in einem VSTO\-Add\-In für eine andere Anwendung. Weitere Informationen über die Anwendungen, die benutzerdefinierte Aufgabenbereiche unterstützen, finden Sie unter [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md).  
  
-   Automatisieren einer Microsoft Office\-Anwendung mithilfe eines benutzerdefinierten Aufgabenbereichs. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Automatisieren einer Anwendung über einen benutzerdefinierten Aufgabenbereich](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).  
  
-   Erstellen einer Menübandschaltfläche in Excel, über die ein benutzerdefinierter Aufgabenbereich ausgeblendet oder angezeigt werden kann. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Synchronisieren eines benutzerdefinierten Aufgabenbereichs mit einer Multifunktionsleistenschaltfläche](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
## Siehe auch  
 [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)   
 [Gewusst wie: Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Exemplarische Vorgehensweise: Automatisieren einer Anwendung über einen benutzerdefinierten Aufgabenbereich](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [Exemplarische Vorgehensweise: Synchronisieren eines benutzerdefinierten Aufgabenbereichs mit einer Multifunktionsleistenschaltfläche](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)   
 [Übersicht über das Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)   
 [Zugreifen auf die Multifunktionsleiste zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  