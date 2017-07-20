---
title: "Schritt&#160;4: Erstellen des Layouts f&#252;r das Formular mit einem TableLayoutPanel-Steuerelement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Schritt&#160;4: Erstellen des Layouts f&#252;r das Formular mit einem TableLayoutPanel-Steuerelement
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Schritt fügen Sie dem Formular ein `TableLayoutPanel`\-Steuerelement hinzu.  Das TableLayoutPanel hilft, Steuerelemente im Formular ordnungsgemäß auszurichten, die Sie später hinzufügen.  
  
 ![Link zu Video](../data-tools/media/playvideo.png "PlayVideo") Eine Videoversion dieses Themas finden Sie im [Video 1 zum Lernprogramm 2: Erstellen eines Bildanzeigeprogramms in Visual Basic](http://go.microsoft.com/fwlink/?LinkId=205211) oder im [Video 1 zum Lernprogramm 2: Erstellen eines Bildanzeigeprogramms in C\#](http://go.microsoft.com/fwlink/?LinkId=205200).  Diese Videos verwenden eine frühere Version von Visual Studio, sodass Menübefehle und andere Benutzeroberflächenelemente geringfügig abweichen können.  Allerdings funktionieren die Konzepte und Prozeduren in der aktuellen Version von Visual Studio auf ähnliche Weise.  
  
### So erstellen Sie ein Layout für das Formular mit einem TableLayoutPanel\-Steuerelement  
  
1.  Suchen Sie auf der linken Seite der Visual Studio\-IDE nach der Registerkarte **Werkzeugkasten**.  Wählen Sie die Registerkarte **Werkzeugkasten** aus, und der Werkzeugkasten wird angezeigt. \(Oder wählen Sie in der Menüleiste **Ansicht**, **Werkzeugkasten** aus.\)  
  
2.  Wählen Sie das kleine Dreieck neben der Gruppe **Container** zum Öffnen aus, wie im folgenden Bild dargestellt.  
  
     ![Containergruppe](../ide/media/express_toolbox.png "Express\_Toolbox")  
Containergruppe  
  
3.  Sie können dem Formular Steuerelemente hinzufügen, z. B. Schaltflächen, Kontrollkästchen und Beschriftungen.  Doppelklicken Sie in der Toolbox auf das `TableLayoutPanel`\-Steuerelement. \(Sie können auch das Steuerelement vom Werkzeugkasten in das Formular ziehen.\) Dies bewirkt, dass die IDE dem Formular ein `TableLayoutPanel`\-Steuerelement hinzufügt, wie im folgenden Bild gezeigt.  
  
     ![TableLayoutPanel&#45;Steuerelement](../ide/media/express_formtablelayout.png "Express\_FormTableLayout")  
TableLayoutPanel\-Steuerelement  
  
    > [!NOTE]
    >  Wenn im Formular ein Fenster mit dem Titel **TableLayoutPanel\-Aufgaben** angezeigt wird, nachdem Sie das TableLayoutPanel\-Steuerelement hinzugefügt haben, wählen Sie eine beliebige Stelle im Formular aus, um es zu schließen.  Später im Lernprogramm erfahren Sie mehr über dieses Fenster.  
  
     Beachten Sie, wie der Werkzeugkasten erweitert wird, um das Formular abzudecken, wenn Sie die Registerkarte auswählen, und geschlossen wird, nachdem Sie eine Stelle außerhalb des Formulars ausgewählt haben.  Das ist die IDE\-Funktion "Automatisch im Hintergrund".  Sie können die Funktion für alle Fenster aktivieren oder deaktivieren, indem Sie oben rechts im Fenster das Ortsmarkensymbol auswählen, um die Automatisch im Hintergrund\-Funktion ein\- und auszuschalten.  Das Ortsmarkensymbol sieht wie folgt aus.  
  
     ![Pinsymbol](../ide/media/express_pushpintoolbox.png "Express\_PushpinToolbox")  
Symbol "Ortsmarke"  
  
4.  Stellen Sie sicher, dass Sie **TableLayoutPanel** auswählen.  Sie können überprüfen, welches Steuerelement ausgewählt ist, indem Sie sich die Dropdownliste oben im **Eigenschaftenfenster** ansehen, so wie im folgenden Bild gezeigt.  
  
     ![Eigenschaftenfenster mit TableLayoutPanel&#45;Steuerelement](../ide/media/express_controlspropwin.png "Express\_ControlsPropWin")  
Eigenschaftenfenster mit dem TableLayoutPanel\-Steuerelement  
  
5.  Wählen Sie die Schaltfläche **Alphabetisch** auf der Symbolleiste im Fenster **Eigenschaften** aus.  Hierdurch wird die Liste der Eigenschaften im Fenster **Eigenschaften** in alphabetischer Reihenfolge angezeigt. Dies erleichtert die Suche nach Eigenschaften in diesem Lernprogramm.  
  
6.  Die Steuerelementauswahl ist eine Dropdownliste oben im **Eigenschaftenfenster**.  In diesem Beispiel ist ein Steuerelement mit dem Namen `tableLayoutPanel1` ausgewählt.  Sie können Steuerelemente auswählen, indem Sie entweder einen Bereich im Windows Forms\-Designer auswählen oder in der Steuerelementauswahl das gewünschte Steuerelement auswählen.  Suchen Sie bei ausgewähltem `TableLayoutPanel`\-Steuerelement nach der Eigenschaft **Dock**, und wählen Sie die Eigenschaft **Dock** aus, die auf **None** gesetzt sein sollte.  Beachten Sie, dass neben dem Wert ein Dropdownpfeil angezeigt wird.  Wählen Sie den Pfeil aus, und wählen Sie dann die Schaltfläche **Fill** \(die große Schaltfläche in der Mitte\) aus, wie im folgenden Bild gezeigt.  
  
     ![Eigenschaftenfenster mit ausgewählter Option "Füllen"](../ide/media/express_docktable.png "Express\_DockTable")  
Eigenschaftenfenster mit Auswahl von "Fill"  
  
     *Andocken* in Visual Studio bedeutet, dass ein Fenster an ein anderes Fenster oder einen anderen Bereich der IDE angefügt wird.  So kann z. B. das Eigenschaftenfenster abgedockt werden \(d. h. es wird getrennt und ist in Visual Studio nicht verankert\), oder es kann an den **Projektmappen\-Explorer** angedockt werden.  
  
7.  Nachdem Sie die **Dock**\-Eigenschaft des TableLayoutPanel\-Steuerelements auf **Fill** festgelegt haben, nimmt der Bereich das ganze Formular ein.  Wenn Sie die Größe des Formulars wieder ändern, bleibt das TableLayoutPanel\-Steuerelement verankert und passt sich an die Formulargröße an.  
  
    > [!NOTE]
    >  Ein TableLayoutPanel\-Steuerelement funktioniert wie eine Tabelle in Microsoft Office Word: Es weist Zeilen und Spalten auf, und eine einzelne Zelle kann mehrere Zeilen und Spalten umfassen.  Jede Zelle kann ein Steuerelement enthalten \(z. B. eine Schaltfläche, ein Kontrollkästchen oder eine Beschriftung\).  Das TableLayoutPanel\-Steuerelement verfügt über ein `PictureBox`\-Steuerelement, das sich auf die gesamte oberste Zeile erstreckt, ein `CheckBox`\-Steuerelement in der Zelle unten links und vier `Button`\-Steuerelemente in der Zelle unten rechts.  
  
8.  Derzeit weist das TableLayoutPanel\-Steuerelement zwei gleich große Zeilen und zwei gleich große Spalten auf.  Sie müssen die Größe der Zeilen und Spalten ändern, damit die oberste Zeile und die rechte Spalte sehr viel größer sind.  Wählen Sie im Windows Forms\-Designer das TableLayoutPanel\-Steuerelement aus.  Oben rechts in der Ecke befindet sich eine Schaltfläche in Form eines kleinen schwarzen Dreiecks, die wie folgt aussieht.  
  
     ![Schaltfläche für Dreieck](../ide/media/express_iconblacktriangle.png "Express\_IconBlackTriangle")  
Dreiecksschaltfläche  
  
     Diese Schaltfläche zeigt an, dass das Steuerelement über Aufgaben verfügt, die Sie beim automatischen Festlegen von Eigenschaften unterstützen.  
  
9. Wählen Sie das Dreieck aus, um die Aufgabenliste des Steuerelements anzuzeigen, wie im folgenden Bild gezeigt.  
  
     ![TableLayoutPanel&#45;Aufgaben](../ide/media/express_tablepanel.png "Express\_TablePanel")  
TableLayoutPanel\-Aufgaben  
  
10. Wählen Sie die Aufgabe **Zeilen und Spalten bearbeiten** aus, um das Fenster **Spalten\- und Zeilenstile** anzuzeigen.  Wählen Sie **Column1** aus, und legen Sie die Größe auf 15 Prozent fest, indem Sie die Schaltfläche **Prozent** auswählen und im Feld `Prozent` den Wert **15** eingeben. \(Das ist ein `NumericUpDown`\-Steuerelement, das Sie in einem späteren Lernprogramm verwenden.\) Wählen Sie **Column2** aus, und legen Sie die Größe auf 85 Prozent fest.  Wählen Sie noch nicht die Schaltfläche **OK** aus, da sonst das Fenster geschlossen wird. \(Wenn das Fenster geschlossen ist, können Sie es über die Aufgabenliste erneut öffnen.\)  
  
     ![Zeilen&#45; und Spaltenstile für TableLayoutPanel](../ide/media/vs_tablelayoutpanel_setup.png "VS\_TableLayoutPanel\_Setup")  
Spalten\- und Zeilenstile des TableLayoutPanel\-Steuerelements  
  
11. Wählen Sie in der Dropdownliste **Anzeigen** oben im Fenster **Zeilen** aus.  Legen Sie **Row1** auf 90 Prozent und **Row2** auf 10 Prozent fest.  
  
12. Klicken Sie auf die Schaltfläche **OK**.  Das TableLayoutPanel\-Steuerelement sollte jetzt über eine große oberste Zeile, eine kleine unterste Zeile, eine kleine linke Spalte und eine große rechte Spalte verfügen.  Sie können die Größe der Zeilen und Spalten im TableLayoutPanel\-Steuerelement ändern, indem Sie tableLayoutPanel1 im Formular auswählen und dann die Zeilen\- und Spaltenränder ziehen.  
  
     ![Form1 mit TableLayoutPanel in geänderter Größe](../ide/media/vs_formafterlayoutpanel.png "VS\_FormAfterLayoutPanel")  
Form1 mit TableLayoutPanel\-Steuerelement in geänderter Größe  
  
### So fahren Sie fort oder überprüfen die Angaben  
  
-   Um zum nächsten Schritt des Lernprogramms zu wechseln, klicken Sie auf [Schritt 5: Hinzufügen von Steuerelementen zum Formular](../ide/step-5-add-controls-to-your-form.md).  
  
-   Um zum vorherigen Schritt des Lernprogramms zurückzukehren, klicken Sie auf [Schritt 3: Festlegen der Formulareigenschaften](../ide/step-3-set-your-form-properties.md).