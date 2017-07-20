---
title: "Optionen, Text-Editor, Standard (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Visual_Basic.Editor"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.Editor"
  - "VS.ToolsOptionsPages.Visual_Basic_Editor.Editor"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage"
  - "VS.ToolsOptionsPages.Text_Editor.Basic"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific"
helpviewer_keywords: 
  - "Basic (Text-Editor im Dialogfeld Optionen)"
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Optionen, Text-Editor, Standard (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die Eigenschaftenseite **VB\-Spezifisch**, die Sie im Menü **Extras** über das Dialogfeld **Optionen** im Unterordner **Standard** des Ordners **Text\-Editor** aufrufen können, enthält die folgenden Eigenschaften:  
  
 **End\-Konstruktionen automatisch einfügen**  
 Wenn Sie z. B. die erste Zeile einer Prozedurdeklaration, `Sub Main—`, eingeben und die EINGABETASTE drücken, wird im Text\-Editor eine entsprechende `End Sub`\-Zeile hinzugefügt.  Ebenso wird beim Hinzufügen einer [For](/dotnet/visual-basic/language-reference/statements/for-next-statement)\-Schleife im Text\-Editor eine entsprechende `Next`\-Anweisung hinzugefügt.  Wenn diese Option ausgewählt ist, wird im Code\-Editor automatisch das end\-Konstrukt eingefügt.  
  
 **Automatische Strukturierung und Einrückung des Programmcodes**  
 Der Text\-Editor formatiert den Code entsprechend neu.  Wenn diese Option aktiviert ist, führt der Code\-Editor die folgenden Aufgaben durch:  
  
-   Ausrichten des Codes an der richtigen Tabulatorposition  
  
-   Ändern der Groß\-\/Kleinschreibung von Schlüsselwörtern, Variablen und Objekten in die richtige Schreibweise  
  
-   Hinzufügen eines fehlenden `Then` zu einer `If...Then`\-Anweisung  
  
-   Hinzufügen von Klammern zu Funktionsaufrufen  
  
-   Hinzufügen fehlender Anführungszeichen am Ende von Zeichenfolgen  
  
-   Neuformatieren der exponentiellen Notation  
  
-   Neuformatieren von Datumsangaben  
  
 **Gliederungsmodus aktivieren**  
 Wenn Sie eine Datei im Code\-Editor öffnen, können Sie das Dokument im Gliederungsmodus anzeigen.  Weitere Informationen finden Sie unter [Gliedern](../../ide/outlining.md).  Ist diese Option ausgewählt, wird die Gliederungsfunktion beim Öffnen einer Datei aktiviert.  
  
 **Schnittstellen\- und MustOverride\-Member automatisch einfügen**  
 Wenn Sie ein Commit für eine `Implements`\-Anweisung oder eine `Inherits`\-Anweisung für eine Klasse ausführen, fügt der Text\-Editor Prototypen für die Member ein, die implementiert bzw. überschrieben werden müssen.  
  
 **Zeilentrennzeichen zwischen Prozeduren anzeigen**  
 Der Text\-Editor gibt den visuellen Bereich von Prozeduren an.  In den VB\-Quelldateien des Projekts werden an den in der folgenden Tabelle aufgeführten Positionen Linien gezeichnet:  
  
|Position in der VB\-Quelldatei|Beispiel für die Linienposition|  
|------------------------------------|-------------------------------------|  
|Nach dem Schließen eines Blockdeklarationskonstrukts|-   Am Ende einer Klasse, einer Struktur, eines Moduls, einer Schnittstelle oder einer Enumeration<br />-   Hinter einer Eigenschaft, Funktion oder Sub<br />-   Nicht zwischen den get\- und set\-Klauseln in einer Eigenschaft|  
|Nach mehreren Einzelzeilenkonstrukten|-   Hinter import\-Anweisungen, vor einer Typdefinition in einer Klassendatei<br />-   Hinter den in einer Klasse deklarierten Variablen, vor jeglichen Prozeduren|  
|Nach Einzelzeilendeklarationen \(Deklarationen, die nicht auf Blockebene erfolgen\)|-   Nach import\-Anweisungen, inherits\-Anweisungen, Variablendeklarationen, Ereignisdeklarationen, Delegatdeklarationen und declare\-Anweisungen für DLLs|  
  
 **Vorschläge für Fehlerkorrektur aktivieren**  
 Der Text\-Editor kann Lösungsvorschläge zu allgemeinen Fehlern ausgeben und bietet die Möglichkeit, die geeignete Korrekturmaßnahme auszuwählen, die dann auf den Code angewendet wird.  
  
 **Markierung von Verweisen und Schlüsselwörtern aktivieren**  
 Der Text\-Editor kann alle Instanzen eines Symbols oder alle Schlüsselwörter in Klauseln wie `If..Then`, `While...End While` oder `Try...Catch...Finally` hervorheben.  Sie können zwischen markierten Verweisen oder Schlüsselwörtern durch Drücken von STRG\+UMSCHALT\+NACH\-UNTEN oder STRG\+UMSCHALT\+NACH\-OBEN navigieren.  
  
## Siehe auch  
 [Allgemein, Umgebung, Dialogfeld "Optionen"](../../ide/reference/general-environment-options-dialog-box.md)   
 [Optionen, Text\-Editor, Alle Sprachen, Registerkarten](../../ide/reference/options-text-editor-all-languages-tabs.md)