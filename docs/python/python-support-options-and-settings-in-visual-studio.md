---
title: Optionen und Einstellungen für Python | Microsoft-Dokumentation
description: Eine Referenz zu den verschiedenen Einstellungen in Visual Studio, die sich auf Python-Code und -Projekte beziehen.
ms.custom: ''
ms.date: 03/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Python_Tools
- VS.ToolsOptionsPages.Python_Tools.General
- VS.ToolsOptionsPages.Python_Tools.Debugging
- VS.ToolsOptionsPages.Python_Tools.Diagnostics
- VS.ToolsOptionsPages.Python_Tools.Experimental
- VS.ToolsOptionsPages.Python_Tools.Interactive_Windows
- VS.ToolsOptionsPages.Text_Editor.Python.Advanced
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 71c6e3424d93af2b3696f19193498ed6940cbc7a
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
---
# <a name="options-for-python-in-visual-studio"></a>Optionen für Python in Visual Studio

Um Python-Optionen anzuzeigen, verwenden Sie den Menübefehl **Extras > Optionen**, achten Sie darauf, dass **Alle Einstellungen anzeigen** ausgewählt ist, und navigieren Sie dann zu **Python Tools**:

![Dialogfeld „Python-Optionen“, Registerkarte „Allgemein“](media/options-general.png)

Zusätzliche Python-spezifische Optionen finden Sie auch auf der Registerkarte **Text-Editor > Python > Erweitert** sowie auf der Registerkarte **Umgebung > Schriftarten und Farben** in der Gruppe „Text-Editor“.

> [!Note]
> Die Gruppe **Experimentell** enthält Optionen für Features, die sich noch in der Entwicklung befinden und hier noch nicht dokumentiert wurden. Diese werden häufig in Beiträgen des Blogs [Python engineering at Microsoft (Python-Entwicklung bei Microsoft)](https://blogs.msdn.microsoft.com/pythonengineering/) erläutert.

## <a name="general-options"></a>Allgemeine Optionen

(Registerkarte **Extras > Optionen > Python**.)

| Option | Standard | description |
| --- | --- | --- |
| Beim Erstellen virtueller Umgebungen das Ausgabefenster anzeigen| Ein | Deaktivieren Sie diese Option, um zu verhindern, dass das Ausgabefenster angezeigt wird. |
| Anzeigen des Ausgabefensters beim Installieren oder Löschen von Paketen | Ein | Deaktivieren Sie diese Option, um zu verhindern, dass das Ausgabefenster angezeigt wird. |
| "Pip" immer als Administrator ausführen | Aus | Erhöht `pip install`-Vorgänge immer in allen Umgebungen Beim Installieren von Paketen fordert Visual Studio die Eingabe von Administratorberechtigungen, wenn sich die Umgebung in einem geschützten Bereichs des Dateisystems wie z.B. `c:\Program Files` befindet. In dieser Aufforderung können Sie auswählen, dass `pip install` immer für diese eine Umgebung erhöht ist. Siehe [Registerkarte „Pakete“](python-environments-window-tab-reference.md#packages-tab). |
| Bei erster Verwendung automatisch Vervollständigungsdatenbank generieren | Ein | *Gilt für Visual Studio 2017 Version 15.5 und früher sowie bei Verwendung einer IntelliSense-Datenbank für höhere Versionen.* Priorisiert die Vervollständigung der Datenbank für eine Bibliothek, wenn Sie Code schreiben, der diese verwendet. Weitere Informationen finden Sie unter [Referenz zu den Registerkarten im Fenster „Python-Umgebungen“](python-environments-window-tab-reference.md). |
| Systemweite PYTHONPATH-Variablen ignorieren | Ein | PYTHONPATH wird standardmäßig ignoriert, weil Visual Studio eine direktere Möglichkeit bietet, Suchpfade in Umgebungen und Projekten anzugeben. Weitere Informationen finden Sie unter [Suchpfade](search-paths.md). |
| Suchpfade beim Hinzufügen verknüpfter Dateien aktualisieren | Ein | Wenn diese Option festgelegt ist, werden [Suchpfade](search-paths.md) durch das Hinzufügen einer [verknüpften Datei](managing-python-projects-in-visual-studio.md#linked-files) zu einem Projekt aktualisiert, sodass IntelliSense die Inhalte des Ordners der verknüpften Datei in seine Vervollständigungsdatenbank einbeziehen kann. Deaktivieren Sie diese Option, um derartigen Inhalt aus der Vervollständigungsdatenbank auszuschließen. |
| Warnen, wenn das importierte Modul nicht gefunden wird | Ein | Deaktivieren Sie diese Option, um Warnungen zu unterdrücken, wenn Sie wissen, dass ein importiertes Modul aktuell nicht verfügbar ist, den Codevorgang aber ansonsten nicht beeinträchtigt. |
| Inkonsistenten Einzug melden als | Warnungen | Da der Python-Interpreter stark von korrekten Einzügen abhängt, um den Umfang bestimmen zu können, sendet Visual Studio standardmäßig Warnungen, wenn es inkonsistente Einzüge erkennt, die möglicherweise auf Codierungsfehler hinweisen. Legen Sie die Option auf *Errors* (Fehler) fest, um noch strenger zu sein, damit das Programm in derartigen Fällen beendet wird. Um dieses Verhalten komplett zu deaktivieren, wählen Sie *Don‘t* (Nicht) aus. |
| Auf Umfrage/Nachrichten überprüfen | Einmal pro Woche | Legt die Häufigkeit fest, mit der Visual Studio ein Fenster mit einer Webseite mit verfügbaren Umfragen und neuen Elementen im Zusammenhang mit Python öffnen darf. Sie können zwischen *Nie*, *Einmal am Tag*, *Einmal in der Woche* und *Einmal im Monat* wählen. |
| Zurücksetzen aller permanent verborgenen Dialogfelder (Schaltfläche) | n/v | In verschiedene Dialogfeldern haben Sie die Möglichkeit, **Diese Meldung nicht mehr anzeigen** auszuwählen. Verwenden Sie diese Schaltfläche, um diese Optionen zu deaktivieren und die Dialogfelder erneut zu öffnen. |

![Dialogfeld „Python-Optionen“, Registerkarte „Allgemein“](media/options-general.png)

## <a name="debugging-options"></a>Debugoptionen

(Registerkarte **Extras > Optionen > Python > Debuggen**.)

| Option | Standard | description |
| --- | --- | --- |
| Eingabeaufforderung vor der Ausführung, wenn Fehler vorliegen | Ein | Wenn diese Option aktiviert ist, werden Sie aufgefordert zu bestätigen, dass Sie Code ausführen möchten, der Fehler enthält. Deaktivieren Sie diese Option, um das Warnen auszuschalten. |
| Auf Eingabe warten, wenn der Prozess abnormal beendet wird<br/><br/>Auf Eingabe warten, wenn der Prozess normal beendet wird | Ein (für beide) | Ein aus Visual Studio gestartetes Python-Programm wird in seinem eigenen Konsolenfenster ausgeführt. Standardmäßig wartet das Fenster, bis Sie eine Taste drücken, bevor es schließt, unabhängig davon, wie das Programm beendet wird. Um diese Aufforderung zu deaktivieren und das Fenster automatisch zu schließen, deaktivieren Sie mindestens eine dieser beiden Optionen. |
| Programmausgabe mithilfe von "tee" an Debugausgabefenster senden | Ein | Zeigt die Programmausgabe sowohl in einem separaten Konsolenfenster als auch im Ausgabefenster von Visual Studio an. Deaktivieren Sie diese Option, um die Ausgabe nur im separaten Konsolenfenster anzuzeigen. |
| Bei SystemExit-Ausnahme mit Exitcode 0 anhalten | Aus | Wenn diese Option aktiviert ist, wird der Debugger für diese Option beendet. Wenn diese Option deaktiviert ist, wird der Debugger ohne Unterbrechung beendet. |
| Debuggen der Python-Standardbibliothek aktivieren | Aus | Mit dieser Option ist es möglich, den Quellcode der Standardbibliothek beim Debuggen schrittweise auszuführen. Dadurch dauert das Starten des Debuggers allerdings länger.|

![Dialogfeld „Python-Optionen“, Registerkarte „Debuggen“](media/options-debugging.png)

## <a name="diagnostics-options"></a>Diagnoseoptionen

(Registerkarte **Extras > Optionen > Python > Diagnose**.)

| Option | Standard | description |
| --- | --- | --- |
| Einbeziehen von Analyseprotokollen | Ein | Enthält ausführliche Protokolle zur Analyse von installierten Python-Umgebungen beim Speichern von Diagnosen in Dateien oder beim Kopieren dieser in die Zwischenablage mithilfe von Schaltflächen. Die Option kann die Größe der generierten Datei deutlich erhöhen, ist aber häufig für das Diagnostizieren von Problemen bei IntelliSense erforderlich. |
| Diagnose in Datei speichern (Schaltfläche) | n/v | Erfordert einen Dateinamen und speichert das Protokoll anschließend in einer Textdatei |
| Diagnose in Zwischenablage kopieren (Schaltfläche) | n/v | Nimmt das gesamte Protokoll in die Zwischenablage auf. Dieser Vorgang kann je nach Größe des Protokolls einige Zeit in Anspruch nehmen. |

![Dialogfeld „Optionen“ von Python, Registerkarte „Diagnose“](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>Optionen für das interaktive Fenster

(Registerkarte **Extras > Optionen > Python > Interaktive Fenster**.)

| Option | Standard | description |
| --- | --- | --- |
| Skripts | n/v | Gibt einen allgemeinen Ordner an, den Startskripts auf interaktive Fenster für alle Umgebungen anwenden. Weitere Informationen finden Sie unter [Startskripte](python-environments-window-tab-reference.md#startup-scripts). Beachten Sie, dass diese Funktion im Moment nicht funktioniert. |
| NACH-OBEN- und NACH-UNTEN-TASTEN zum Navigieren des Verlaufs | Ein | Verwenden Sie die Pfeiltasten, um durch den Verlauf im interaktiven Fenster zu Navigieren. Deaktivieren Sie diese Einstellung, um die Pfeiltasten stattdessen zum Navigieren der Ausgabe im interaktiven Fenster zu verwenden. |
| Beendigungsmodus | Nur Ausdrücke ohne Funktionsaufrufe auswerten | Für das Bestimmen der verfügbaren Member in einem Ausdruck im interaktiven Fenster ist möglicherweise das Auswerten des aktuellen unvollständigen Ausdrucks notwendig. Dies kann Nebenwirkungen haben oder dazu führen, dass Funktionen mehrmals aufgerufen werden. Die Standardeinstellung *Nur Ausdrücke ohne Funktionsaufrufe auswerten* schließt Ausdrücke aus, die eine Funktion aufrufen, wertet aber andere Ausdrücke aus. Beispielsweise wird `a.b` ausgewertet, `a().b` aber nicht.  *Ausdrücke nie auswerten* verhindert alle Nebenwirkungen, indem nur das gängige IntelliSense-Modul für Vorschläge verwendet wird. *Alle Ausdrücke auswerten* wertet den vollständigen Ausdruck aus, um Vorschläge abzurufen, unabhängig von Nebenwirkungen. |
| Vorschläge zur statischen Analyse ausblenden | Aus | Wenn diese Option aktiviert ist, werden nur Vorschläge angezeigt, die durch das Abrufen von Ausdrücken entstanden sind. Wenn diese Option mit der Option *Ausdrücke nie auswerten* im Beendigungsmodus kombiniert wird, werden keine brauchbaren Vervollständigungen im interaktiven Fenster angezeigt. |

![Dialogfeld „Python-Optionen“, Registerkarte „Interaktives Fenster“](media/options-interactive-windows.png)

## <a name="advanced-python-editor-options"></a>Erweiterte Optionen des Python-Editors

(Registerkarte **Extras > Optionen > Text-Editor > Python > Erweitert**.)

### <a name="completion-results"></a>Vervollständigungsergebnisse

| Option | Standard | description |
| --- | --- | --- |
| Membervervollständigung zeigt Schnittmenge der Member an | Aus | Wenn diese Option aktiviert ist, werden nur die Vervollständigungen angezeigt, die von allen möglichen Typen unterstützt werden. |
| Liste basierend auf Suchzeichenfolge filtern | Ein | Wendet den Filter auf Vervollständigungsvorschläge an, während Sie eine Eingabe machen (Standard ist aktiviert). |
| Automatisch Vervollständigung für alle Bezeichner anzeigen | Ein | Deaktivieren Sie diese Option, um das Vervollständigen im Editor und im interaktiven Fenster auszuschalten. |

### <a name="selection-in-completion-list"></a>Auswahl in Vervollständigungslisten

| Option | Standard | description |
| --- | --- | --- |
| Commit bei Eingabe der folgenden Zeichen | `{}[]().,:;+-*/%&&#124;^~=<>#@\` | Diese Zeichen folgen üblicherweise auf einen Bezeichner, den Sie aus einer Vervollständigungsliste auswählen können. Deshalb ist es praktisch, die Vervollständigung zu committen, indem Sie einfach ein Zeichen eingeben. Sie können spezifische Zeichen nach Ihren Wünschen einer Liste hinzufügen oder aus dieser entfernen.  |
| Bei EINGABE wird die aktuelle Vervollständigung übernommen | Ein | Wenn diese Option aktiviert ist, wählt die EINGABE-TASTE die aktuell ausgewählte Vervollständigung aus und wendet diese an wie mit den oben stehenden Zeichen (es gibt natürlich kein Zeichen für EINGABE, weshalb es nicht direkt in die Liste aufgenommen werden kann). |
| Mit EINGABE neue Zeile nach jedem ganzen Wort | Aus | Wenn Sie das gesamte Wort eingeben, das im Vervollständigungspopupfenster angezeigt wird, und dann EINGABE drücken, wird diese Vervollständigung standardmäßig committet. Wenn Sie diese Option festlegen, committen Sie Vervollständigungen mit Abschluss der Eingabe des Bezeichners, sodass EINGABE eine neue Zeile einfügt. |

### <a name="miscellaneous-options"></a>Sonstige Optionen

| Option | Standard | description |
| --- | --- | --- |
| Beim Öffnen von Dateien in Gliederungsmodus wechseln | Ein | Aktivieren Sie die Gliederungsfunktion von Visual Studio automatisch im Editor, wenn Sie eine Python-Codedatei öffnen. |
| Entfernte REPL-Aufforderungen einfügen | Ein | Entfernt „>>>“ und „...“ aus eingefügtem Text, sodass Code leicht aus dem interaktiven Fenster in den Editor übertragen werden kann. Deaktivieren Sie diese Option, wenn Sie diese Zeichen behalten möchten, wenn Sie aus anderen Quellen einfügen. |
| Namen basierend auf Typen farblich markieren | Ein | Ermöglicht das Einfärben von Syntax in Python-Code. |

![Python-Editor-Optionen (Dialogfeld), Registerkarte „Erweitert“](media/options-editor-advanced.png)

## <a name="fonts-and-colors-options"></a>Optionen für Schriftarten und Farben

(Registerkarte **Umgebung > Schriftarten und Farben** in der Gruppe „Text-Editor“.)

Die Namen aller Python-Optionen sind mit dem Präfix „Python“ versehen und damit selbsterklärend. Die Standardschriftart für alle Visual Studio-Farbdesigns ist 10 pt Consolas regulär (nicht fett). Die Standardfarben variieren je nach Design. In der Regel ändern Sie eine Schriftart oder Farbe, wenn Sie meinen, dass der Text mit den Standardeinstellungen schwer zu lesen ist.

![Schriftarten- und Farboptionen für Python](media/options-fonts-and-colors.png)