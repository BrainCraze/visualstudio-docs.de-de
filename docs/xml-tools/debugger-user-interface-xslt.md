---
title: Debuggerbenutzeroberfläche (XSLT) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3d4f5638ce7f61a1ba79ff6536a0e6f98e4de1c9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="debugger-user-interface-xslt"></a>Benutzeroberfläche des XSLT-Debuggers
In diesem Thema werden die Fenster und Dialogfelder des Debuggers beschrieben. Es werden nur die Elemente der Benutzeroberfläche erläutert, die ein XSLT-spezifisches Debugverhalten aufweisen.  
  
 Weitere Informationen finden Sie unter der [Benutzeroberflächenreferenz Debuggen](../debugger/debugging-user-interface-reference.md).  
  
## <a name="locals-window"></a>Lokalfenster  
 Im Lokalfenster werden Informationen zu allen im Stylesheet definierten Variablen angezeigt. Das Lokalfenster enthält drei Spalten mit Informationen:  
  
 **Name**  
 Diese Spalte enthält die Namen aller lokalen Variablen im aktuellen Gültigkeitsbereich. Knotengruppen verfügen über eine Strukturansicht, die Sie erweitern können, um die Unterordner anzuzeigen.  
  
 **Wert**  
 In dieser Spalte wird für jede Variable der vorhandene Wert angezeigt. Für Attribut-, Verarbeitungsanweisungs-, Kommentar-, Text- und CDATA-Knoten wird der Textwert des Knotens angezeigt. Für Namespace-Knoten wird der Namespace-URI angezeigt.  
  
 **Type**  
 Diese Spalte gibt den Datentyp der einzelnen Variablen aufgeführt, die der **Namen** Spalte.  
  
 Im Lokalfenster werden auch die vordefinierten Kontextvariablen angezeigt, mit denen der Kontext der XSLT-Transformation verfolgt wird. In der folgenden Tabelle werden die vom XSLT-Debugger verwendeten vordefinierten Kontextvariablen beschrieben.  
  
|Name|Beschreibung|  
|----------|-----------------|  
|`last()`|Die Kontextgröße.|  
|`position()`|Die Position bzw. Indexnummer des Kontextknotens in Bezug auf die Kontextgröße.|  
|`self::node()`|Der Wert des Kontextknotens.|  
  
## <a name="output-window"></a>Ausgabefenster  
 Im Ausgabefenster werden alle während des Debuggens ausgegebenen Fehlermeldungen und aufgetretenen Sicherheitsausnahmen angezeigt.  
  
 Die Debuggerausgabe wird vom XSLT-Debugger in einem separaten Fenster angezeigt. Dies ist das gleiche Fenster zur Anzeige der Ausgabe einer **XSL-Ausgabe anzeigen** Befehl.  
  
## <a name="task-list"></a>Aufgabenliste  
 In der Aufgabenliste werden alle Kompilierungsfehler im Stylesheet aufgelistet. Durch Doppelklicken auf den Fehler wird der Cursor auf der fehlerhaften Zeile platziert.  
  
 Die Aufgabenliste enthält alle Fehler, die in den Skriptblöcken in der XSLT-Datei auftreten.  
  
> [!NOTE]
>  Der XSLT-Debugger gibt keine Warnungen aus. Daher werden keine Warnungen in der Aufgabenliste angezeigt.  
  
## <a name="breakpoints-window"></a>Fenster "Haltepunkte"  
 Im Fenster Haltepunkte werden alle im aktuellen Projekt festgelegten Haltepunkte angezeigt. Wenn während der Anzeige dieses Fensters ein Haltepunkt hinzugefügt wird, wird das Fenster automatisch aktualisiert, sodass der neue Haltepunkt ebenfalls angezeigt wird.  
  
 Das Fenster Haltepunkte weist dasselbe Verhalten wie andere Debuggern von Visual Studio auf.  
  
## <a name="command-windowimmediate-window"></a>Befehlsfenster/Direktfenster  
 In diesem Release des XSLT-Debuggers nicht implementiert.  
  
## <a name="watch-window"></a>Überwachungsfenster  
 Das Überwachungsfenster wird zum Auswerten der Variablen verwendet. Sie können dort auch die Werte der Variablen ändern.  
  
 Die im Überwachungsfenster angezeigten Variablen beziehen sich auf den aktuellen Kontext (auf das oberste Element in der Aufrufliste). Beim Ändern des Kontexts wird das Überwachungsfenster aktualisiert, und es werden die für den betreffenden Kontext festgelegten Variablen angezeigt.  
  
## <a name="call-stack-window"></a>Aufruflistenfenster  
 Im Aufruflistenfenster werden die Namen der Funktionen in der Aufrufliste, die Parametertypen und Parameterwerte angezeigt. Aufruflisteninformationen werden nur angezeigt, wenn sich das derzeit debuggte Programm im Haltezustand befindet.  
  
 Die Aufrufliste stellt die verschiedenen Kontexte dar, die bei der XSLT-Ausführung durchlaufen werden. Wenn beispielsweise ein Aufruf der Vorlage "b" von der Vorlage "a" aus erfolgt, werden die Vorlagen "a" und "b" im Aufruflistenfenster mit dem aktuellen Kontext in der Liste an oberster Position angezeigt. Für den Benutzer wird die derzeit ausgeführte Abfrage angezeigt.  
  
 Wenn die Vorlagen in der XSLT-Datei keinen Namen aufweisen, werden die vom XSLT-Prozessor generierten Namen verwendet.  
  
 Wenn auf ein anderes Element als das Element an oberster Position in der Liste geklickt wird, wird dem Betrachter mithilfe der standardmäßigen grünen Hervorhebung und grünen Pfeile angezeigt, welche XSLT-Verzweigung gerade ausgeführt wird.  
  
## <a name="quickwatch-dialog-box"></a>Dialogfeld "Schnellüberwachung"  
 Die **Schnellüberwachung** Dialogfeld wird verwendet, um XPath 1.0-Ausdrücke ausgewertet werden. Der Kontextknoten (der `self::node()`-Knoten im Lokalfenster) stellt den Kontext für die Ausführung des XPath-Ausdrucks bereit. Das Ergebnis der Ausführung des XPath-Ausdrucks wird im Überwachungsfenster angezeigt.  
  
 In der folgenden Liste werden einige Einschränkungen für die Auswertung von XPath-Ausdrücken beschrieben.  
  
-   Nur integrierte XPath-Funktionen sind zulässig.  
  
-   Integrierte XPath-Funktionen (z. B. `document()`, `key()` usw.) sind nicht zulässig.  
  
-   Benutzerdefinierte Funktionen sind nicht zulässig.  
  
Weitere Informationen finden Sie unter [wie: Auswerten eines XPath-Ausdrucks](../xml-tools/how-to-evaluate-an-xpath-expression.md).  
  
## <a name="disassembly-window"></a>Disassemblyfenster  
 Im Disassemblyfenster wird der vom XSLT-Compiler generierte Assemblycode angezeigt. Dieser Fenster kann in gleicher Weise wie alle anderen Disassemblyfenster in Visual Studio verwendet werden.  
  
 Weitere Informationen [wie: Verwenden des Fensters Disassembly](../debugger/how-to-use-the-disassembly-window.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von XSLT](../xml-tools/debugging-xslt.md)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)   
 [Untersuchen von Variablen in der "Auto" und "lokal" Fenstern in Visual Studio](../debugger/autos-and-locals-windows.md)