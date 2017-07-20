---
title: "Optionen, Text-Editor, JavaScript, Formatierung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing"
  - "VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General"
  - "VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines"
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Optionen, Text-Editor, JavaScript, Formatierung
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Verwenden Sie die Seite **Formatierung** im Dialogfeld **Optionen**, um Optionen zur Formatierung von Code im Code\-Editor festzulegen.  Öffnen Sie diese Seite, indem Sie auf der Menüleiste **Extras** und **Optionen** auswählen und anschließend **Text\-Editor**, **JavaScript** und **Formatierung** erweitern.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## Automatische Formatierung  
 Diese Optionen bestimmen, wann die Formatierung in der **Quellansicht** vorgenommen wird.  
  
## UIElement-Liste  
  
|Option|Beschreibung|  
|------------|------------------|  
|**Abgeschlossene Zeile durch Eingabe formatieren**|Wenn diese Option ausgewählt ist, formatiert der Code\-Editor nach Drücken der EINGABETASTE automatisch die Zeile.|  
|**Abgeschlossene Anweisung bei ";" formatieren**|Wenn diese Option ausgewählt ist, formatiert der Code\-Editor nach Drücken der SEMIKOLONTASTE automatisch die Zeile.|  
|**Abgeschlossenen Block bei "}" formatieren**|Wenn diese Option ausgewählt ist, formatiert der Code\-Editor nach Drücken der schließenden geschweiften Klammer automatisch die Zeile.|  
|**Beim Einfügen formatieren**|Wenn diese Option ausgewählt ist, formatiert der Code\-Editor den Code beim Einfügen in den Editor erneut.  Der Editor verwendet die aktuell definierten Formatierungsregeln.  Wenn diese Option nicht ausgewählt ist, verwendet der Editor die ursprüngliche Formatierung des eingefügten Codes.|  
  
## Neue Zeilen  
 Diese Optionen bestimmen, ob der Code\-Editor eine öffnende geschweifte Klammer für Funktionen und Kontrollblöcke in einer neuen Zeile einfügt.  
  
## UIElement-Liste  
  
|Option|Beschreibung|  
|------------|------------------|  
|**Öffnende geschweifte Klammer für Funktionen in neuer Zeile platzieren**|Wenn diese Option ausgewählt ist, verschiebt der Code\-Editor die mit einer Funktion verknüpfte öffnende geschweifte Klammer in eine neue Zeile.|  
|**Öffnende geschweifte Klammer für Kontrollblöcke in neuer Zeile platzieren**|Wenn diese Option ausgewählt ist, verschiebt der Code\-Editor die mit einem Kontrollblock verknüpfte öffnende geschweifte Klammer \(z. B. `if`\- und `while`\-Kontrollblöcke\) in eine neue Zeile.|  
  
## Abstand  
 Diese Optionen bestimmen, wie Abstände in der **Quellansicht** eingefügt werden.  
  
## UIElement-Liste  
  
|Option|Beschreibung|  
|------------|------------------|  
|**Leerzeichen nach Kommatrennzeichen einfügen**|Wenn diese Option ausgewählt ist, wird im Code\-Editor ein Leerzeichen nach einem Kommatrennzeichen eingefügt.|  
|**In for\-Anweisung Leerzeichen nach Semikolon einfügen**|Wenn diese Option ausgewählt ist, wird im Code\-Editor hinter jedem Semikolon in der ersten Zeile einer `for`\-Schleife ein Leerzeichen eingefügt.|  
|**Leerzeichen vor und nach binären Operatoren einfügen**|Wenn diese Option ausgewählt ist, wird im Code\-Editor ein Leerzeichen vor und nach einem binären Operator \(z. B. \+, \-, &&, &#124;&#124;\) eingefügt.|  
|**Leerzeichen nach Schlüsselwörtern in Anweisungen für die Ablaufsteuerung einfügen**|Wenn diese Option ausgewählt ist, wird im Code\-Editor in Anweisungen für die Ablaufsteuerung ein Leerzeichen nach JavaScript\-Schüsselwörtern eingefügt.|  
|**Leerzeichen nach function\-Schlüsselwort für anonyme Funktionen einfügen**|Wenn diese Option ausgewählt ist, wird im Code\-Editor ein Leerzeichen hinter dem `function`\-Schlüsselwort für anonyme Funktionen eingefügt.|  
|**Leerzeichen nach öffnender und vor schließender nicht leerer Klammer einfügen**|Wenn diese Option ausgewählt ist, wird im Code\-Editor ein Leerzeichen hinter die öffnende Klammer und vor der schließenden Klammer eingefügt, sofern nicht leere Zeichen innerhalb der Klammern vorhanden sind.|  
  
## Siehe auch  
 [Allgemein, Umgebung, Dialogfeld "Optionen"](../../ide/reference/general-environment-options-dialog-box.md)