---
title: "Optionen, Text-Editor, JavaScript, IntelliSense | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References"
  - "VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General"
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Optionen, Text-Editor, JavaScript, IntelliSense
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Verwenden Sie die Seite **IntelliSense** des Dialogfelds **Optionen**, um Einstellungen zu ändern, die das Verhalten von IntelliSense für JavaScript beeinflussen. Sie erreichen die **IntelliSense**\-Seite, indem Sie **Tools**, **Optionen** in der Menüleiste wählen und anschließend **Text\-Editor**, **JavaScript** und **IntelliSense** erweitern.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
 Die Seite **IntelliSense** enthält folgende Abschnitte:  
  
## Validierung  
 Sie können diese Optionen verwenden, um Einstellungen dafür festzulegen, wie der JavaScript\-Editor Syntax im Dokument überprüft.  
  
## UIElement-Liste  
 **Syntaxfehler anzeigen**  
 Wenn dieses Kontrollkästchen nicht aktiviert ist, werden im JavaScript\-Editor keine Syntaxfehler gezeigt. Dies ist nützlich, wenn Sie mit Code arbeiten, der nicht Ihr eigener ist und in dem Sie nicht beabsichtigen, Syntaxfehler zu beheben.  
  
 Wenn dieses Kontrollkästchen aktiviert ist, haben Sie die Möglichkeit, das Kontrollkästchen **Fehler als Warnung anzeigen** zu aktivieren.  
  
 **Fehler als Warnungen anzeigen**  
 Wenn dieses Kontrollkästchen aktiviert ist, werden JavaScript\-Fehler als Warnungen und nicht in der Fehlerliste angezeigt.  
  
 **Remoteverweise \(z. B. http:\/\/\) für Dateien im Projekt "Sonstige Dateien" herunterladen**  
 Wenn dieses Kontrollkästchen aktiviert ist und Sie eine JavaScript\-Datei haben, die nicht im Kontext eines Projekts geöffnet ist, lädt Visual Studio remote JavaScript\-Dateien herunter, auf die in der Datei verwiesen wird mit dem Ziel, IntelliSense\-Informationen bereitzustellen. Wenn diese Option aktiviert ist, werden Dateien heruntergeladen, wenn Sie diese als Verweis in der JavaScript\-Datei eingeschlossen haben.  
  
> [!NOTE]
>  Für Webprojekte werden die Remotedateien, auf die im Projekt verwiesen wird, standardmäßig heruntergeladen.  
  
## Anweisungsvervollständigung  
 Sie können diese Optionen verwenden, um das Verhalten der IntelliSense\-Anweisungsvervollständigung zu ändern.  
  
## UIElement-Liste  
 **Nur mit TAB\- oder EINGABETASTE bestätigen**  
 Wenn dieses Kontrollkästchen aktiviert ist, erweitert der JavaScript\-Code\-Editor Anweisungen nur dann mit Elementen, die Sie in der Vervollständigungsliste ausgewählt haben, wenn Sie die Taste TAB oder die EINGABETASTE wählen. Wenn dieses Kontrollkästchen deaktiviert ist, können auch andere Zeichen, wie Punkt, Komma, Doppelpunkt, öffnende runde Klammer und öffnende geschweiften Klammer \({\) Anweisungen mit den ausgewählten Elementen erweitern.  
  
## Verweise  
 Sie können diese Optionen verwenden, um die Typen von IntelliSense\-JS\-Dateien anzugeben, die für verschiedene JavaScript\-Projekttypen verfügbar sind. Die IntelliSense\-Verweise werden normalerweise verwendet, um die IntelliSense\-Unterstützung für globale Objekte bereitzustellen. Sie können diese Seite auch verwenden, um die Ladereihenfolge für Skripts festlegen, die zur Laufzeit geladen werden müssen, und um IntelliSense\-Erweiterungsdateien hinzuzufügen.  
  
## UIElement-Liste  
 **Verweisgruppen**  
 Diese Option gibt den Verweisgruppentyp an. Drei Verweisgruppen werden unterstützt:  
  
 Sie können vordefinierte Verweisgruppen verwenden, um anzugeben, dass bestimmte IntelliSense\-JS\-Dateien für verschiedene JavaScript\-Projekte verfügbar sind. Vier Verweisgruppen sind verfügbar:  
  
-   Implizit \(Windows\-*Version*\) für [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)]\-Apps, die JavaScript verwenden. Die in dieser Gruppe enthalten Dateien sind verfügbar für jede im Code\-Editor geöffnete JS\-Datei für [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)]\-Apps mit JavaScript.  
  
-   Implizit \(Internet\), für HTML5\-Projekte. Die Dateien, die in dieser Gruppe enthalten sind, sind im Bereich für jede JS\-Datei, die im Code\-Editor für die Projekttypen geöffnet ist.  
  
-   Dedizierte Workerverweisgruppen, für HTML5\-Web\-Worker. Die Dateien, die in dieser Gruppe angegeben werden, sind für JS\-Dateien verfügbar, die einen expliziten Verweis auf eine dedizierte Workerverweisgruppe haben.  
  
-   Generisch, für andere JavaScript\-Projekttypen.  
  
 **Eingeschlossene Dateien**  
 Diese Option gibt die Reihenfolge an, in der Dateien in den Kontext des Sprachdiensts geladen werden. Sie können die Reihenfolge konfigurieren, indem Sie die Schaltflächen **Entfernen**, **Nach oben** und **Nach unten** verwenden. Damit IntelliSense ordnungsgemäß funktioniert, muss eine Datei, die von einer anderen abhängig ist, im Anschluss an diese geladen werden.  
  
> [!CAUTION]
>  Wenn ein Objekt ohne Einschränkung in zwei oder mehr impliziten Verweisen definiert ist, wird der letzte Verweis in dieser Liste verwendet, um das Objekt zu definieren.  
  
 **Fügen Sie der Gruppe einen Verweis hinzu**  
 Diese Option bietet die Möglichkeit, nach zusätzlichen IntelliSense\-JS\-Dateien zu suchen und solche Dateien hinzuzufügen.  
  
## Siehe auch  
 [JavaScript IntelliSense](../../ide/javascript-intellisense.md)