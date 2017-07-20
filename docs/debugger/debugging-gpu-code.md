---
title: "Debuggen von GPU-Code | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: c7e77a5a-cb57-4b11-9187-ecc89acc8775
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debuggen von GPU-Code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können C\+\+\-Code debuggen, der im Grafikprozessor \(Graphics Processing Unit, GPU\) ausgeführt wird.  Die GPU\-Debugunterstützung in Visual Studio umfasst die Raceerkennung, das Starten von Prozessen bzw. Anfügen an Prozesse sowie die Integration in die Debugfenster.  
  
## Unterstützte Plattformen  
 Debugging wird unter [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[win8](../debugger/includes/win8_md.md)], [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)] und [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] unterstützt.  Für das Debuggen im Softwareemulator ist [!INCLUDE[win8](../debugger/includes/win8_md.md)] oder [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] erforderlich.  Für das Debuggen auf der Hardware müssen Sie die Treiber für Ihre Grafikkarte installieren.  Nicht alle Hardwarehersteller implementieren sämtliche Debuggerfunktionen.  Weitere Informationen zu Einschränkungen finden Sie in der Dokumentation des Herstellers.  
  
> [!NOTE]
>  Unabhängige Hardwareanbieter, die GPU\-Debugging in Visual Studio unterstützen möchten, müssen eine DLL erstellen, mit der die VSD3DDebug\-Schnittstelle implementiert wird und die auf ihre eigenen Treiber ausgerichtet ist.  
  
## Konfigurieren von GPU\-Debugging  
 Der Debugger kann nicht beim CPU\- und GPU\-Code in der gleichen App\-Ausführung unterbrechen.  Standardmäßig unterbricht der Debugger beim CPU\-Code.  Um den GPU\-Code zu debuggen, verwenden Sie einen dieser beiden Schritte:  
  
-   Wählen Sie in der Liste **Debugtyp** auf der Symbolleiste **Standard** die Option **Nur GPU** aus.  
  
-   Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für das Projekt, und wählen Sie **Eigenschaften** aus.  Wählen Sie im Dialogfeld **Eigenschaftenseiten** die Option **Debugging** und dann in der Liste **Debuggertyp** die Option **Nur GPU** aus.  
  
## Starten von und Anfügen an Anwendungen  
 Sie können die Visual Studio\-Debuggingbefehle verwenden, um das GPU\-Debugging zu starten und zu beenden.  Weitere Informationen finden Sie unter [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md).  Sie können den GPU\-Debugger auch an einen laufenden Prozess anfügen, jedoch nur, wenn dieser Prozess GPU\-Code ausführt.  Weitere Informationen finden Sie unter [Anhängen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## Befehle "Aktuelle Kachel bis zum Cursor ausführen" und "Ausführen bis Cursor"  
 Wenn Sie im Grafikprozessor debuggen, stehen Ihnen zwei Möglichkeiten zum Ausführen bis zur Cursorposition zur Verfügung.  Die Befehle für beide Optionen sind im Kontextmenü des Code\-Editors verfügbar.  
  
1.  Mit dem Befehl **Ausführen bis Cursor** wird die App ausgeführt, bis sie die Cursorposition erreicht und dann angehalten wird.  Dies bedeutet nicht, dass der aktuelle Thread bis zur Cursorposition ausgeführt wird, sondern vielmehr, dass der erste Thread, der die Cursorposition erreicht, die Unterbrechung auslöst.  Siehe [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md).  
  
2.  Mit dem Befehl **Aktuelle Kachel bis zum Cursor ausführen** wird die App ausgeführt, bis alle Threads in der aktuellen Kachel die Cursorposition erreichen und dann angehalten werden.  
  
## Debugfenster  
 Wenn Sie bestimmte Debugfenster verwenden, können Sie GPU\-Threads überprüfen, kennzeichnen und einfrieren.  Weitere Informationen finden Sie in folgenden Themen:  
  
-   [Verwenden des Fensters "Parallele Stapel"](../debugger/using-the-parallel-stacks-window.md)  
  
-   [Verwenden des Fensters "Aufgaben"](../debugger/using-the-tasks-window.md)  
  
-   [Gewusst wie: Verwenden des parallelen Überwachungsfensters](../debugger/how-to-use-the-parallel-watch-window.md)  
  
-   [Debuggen von Threads und Prozessen](../debugger/debug-threads-and-processes.md) \(Symbolleiste für Debugspeicherort\)  
  
-   [Gewusst wie: Verwenden des Fensters "GPU\-Threads"](../debugger/how-to-use-the-gpu-threads-window.md)  
  
## Ausnahmen bei Datensynchronisierung  
 Der Debugger kann mehrere Datensynchronisierungsbedingungen während der Ausführung erkennen.  Wenn eine Bedingung erkannt wird, wechselt der Debugger in den Unterbrechungszustand.  Sie haben zwei Optionen: **Unterbrechen** oder **Weiter**.  Im Dialogfeld **Ausnahmen** können Sie konfigurieren, ob der Debugger diese Bedingungen erkennen soll und bei welchen Bedingungen eine Unterbrechung ausgelöst werden soll.  Weitere Informationen finden Sie unter [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md).  Sie können im Dialogfeld **Optionen** auch angeben, ob der Debugger Ausnahmen ignorieren soll, wenn geschriebene Daten den Wert der Daten nicht ändern.  Weitere Informationen finden Sie unter [Allgemein, Debuggen, Dialogfeld "Optionen"](../debugger/general-debugging-options-dialog-box.md).  
  
## Problembehandlung  
  
### Festlegen einer Zugriffstaste  
 Haltepunkte im GPU\-Code werden nur erreicht, wenn der Code auf der REF\-Zugriffstaste [accelerator::direct3d\_ref](../Topic/accelerator::direct3d_ref%20Data%20Member.md) ausgeführt wird.  Wenn Sie keine Zugriffstaste im Code angeben, wird die REF\-Zugriffstaste automatisch als **Debuggingbeschleunigungstyp** in den Projekteigenschaften ausgewählt.  Wenn der Code explizit eine Zugriffstaste auswählt, wird die REF\-Zugriffstaste nicht beim Debuggen verwendet und die Haltepunkte werden nicht erreicht, es sei denn, die GPU\-Hardware verfügt über Debugunterstützung.  Um dieses Problem zu beheben, schreiben Sie den Code so, dass die REF\-Zugriffstaste beim Debuggen verwendet wird.  Weitere Informationen finden Sie in den Projekteigenschaften sowie unter [Verwenden von accelerator\-Objekten und accelerator\_view\-Objekten](/visual-cpp/parallel/amp/using-accelerator-and-accelerator-view-objects) und [Projekteinstellungen für eine C\+\+\-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### Bedingte Haltepunkte  
 Bedingte Haltepunkte im GPU\-Code werden unterstützt, jedoch kann nicht jeder Ausdruck auf dem Gerät ausgewertet werden.  Wenn ein Ausdruck nicht auf dem Gerät ausgewertet werden kann, wird er im Debugger ausgewertet.  Der Debugger wird wahrscheinlich langsamer ausgeführt als das Gerät.  
  
### Fehler: Bei der Konfiguration des ausgewählten Debuggingbeschleunigungstyps ist ein Problem aufgetreten.  
 Dieser Fehler tritt auf, wenn es zwischen den Projekteinstellungen und der Konfiguration des PCs, auf dem Sie debuggen, eine Inkonsistenz gibt.  Weitere Informationen finden Sie unter [Projekteinstellungen für eine C\+\+\-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### Fehler: Der Debugtreiber für den ausgewählten Debuggingbeschleunigungstyp ist nicht auf dem Zielcomputer installiert.  
 Dieser Fehler tritt auf, wenn Sie auf einem Remotecomputer debuggen.  Der Debugger kann bis zur Laufzeit nicht bestimmen, ob die Treiber auf dem Remotecomputer installiert sind.  Die Treiber sind vom Hersteller der Grafikkarte erhältlich.  
  
### Fehler: Auf der Remotesite muss TDR \(Timeout Detection and Recovery\) deaktiviert sein.  
 Es ist möglich, dass die C\+\+ AMP\-Berechnungen das Standardzeitintervall überschreiten, das durch den Windows\-TDR\-Prozess \(Timeout Detection and Recovery\) festgelegt wird.  Wenn dies geschieht, wird die Berechnung abgebrochen und die Daten gehen verloren.  Weitere Informationen finden Sie unter [Behandlung von TDRs in C\+\+ AMP](http://go.microsoft.com/fwlink/p/?LinkId=249154).  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Debuggen einer C\+\+ AMP\-Anwendung](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md)   
 [Projekteinstellungen für eine C\+\+\-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Starten von GPU\-Debugging in Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=255381)