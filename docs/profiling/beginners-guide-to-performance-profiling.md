---
title: "Einführung in die Leistungsprofilerstellung in Visual Studio | Microsoft-Dokumentation"
ms.custom: H1Hack27Feb2017
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
- CPU Usage
- Diagnostics Tools
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
caps.latest.revision: 45
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 90b2481b0ec4f9387fe3a2c0b733a103e8c03845
ms.openlocfilehash: 36770fe6fad52e33144f382446d7e851734f87c5
ms.contentlocale: de-de
ms.lasthandoff: 05/23/2017

---
# <a name="beginners-guide-to-performance-profiling"></a>Einführung in die Leistungsprofilerstellung
Sie können Visual Studio-Profilerstellungstools verwenden, um Leistungsprobleme in der Anwendung zu analysieren. Dieses Verfahren veranschaulicht die Verwendung der Registerkarte **CPU-Auslastung** der Diagnosetools, um Leistungsdaten Ihrer App zu erhalten. Die Diagnosetools werden für die .NET-Entwicklung in Visual Studio, darunter ASP.NET, sowie für die native/C++-Entwicklung unterstützt.
  
Wenn der Debugger angehalten wird, sammelt das Tool **CPU-Auslastung** Informationen zu den in der Anwendung ausgeführten Funktionen. Das Tool listet auch die Funktionen auf, die Aufgaben ausgeführt haben. Außerdem wird ein Zeitachsendiagramm zur Verfügung gestellt, das Sie verwenden können, um sich auf bestimmte Segmente der Samplingsitzung zu konzentrieren.

Der Diagnosehub bietet Ihnen viele weitere Optionen zum Ausführen und Verwalten Ihrer Diagnosesitzung. Wenn Sie von **CPU-Auslastung** nicht die benötigten Daten erhalten, stehen andere [Profiling Tools (Profilerstellungstools)](../profiling/Profiling-Tools.md) zur Verfügung, um andere Arten von hilfreichen Informationen zu erhalten. In vielen Fällen kann der Leistungsengpass Ihrer Anwendung durch etwas anderes als die CPU ausgelöst werden, z.B. durch den Speicher, das Rendern der Benutzeroberfläche oder die Anforderungszeit des Netzwerks. Der Diagnosehub bietet Ihnen viele andere Optionen zum Aufzeichnen und Analysieren dieser Art von Daten.

Dieses Thema behandelt die Analyse der CPU-Auslastung in einem normalen Debuggingworkflow. Sie können die CPU-Auslastung auch ohne Debugger analysieren, oder indem Sie eine ausgeführte App als Ziel setzen. Weitere Informationen finden Sie unter [Run profiling tools without debugging (Profilerstellungstools ohne Debuggen ausführen)](../profiling/running-profiling-tools-with-or-without-the-debugger.md).
  
##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Schritt 1: Sammeln von Profilerstellungsdaten 
  
1.  Öffnen Sie das Projekt, das Sie in Visual Studio debuggen möchten, und legen Sie in Ihrer App einen Haltepunkt an dem Punkt fest, an dem Sie die CPU-Auslastung untersuchen möchten.

2.  Legen Sie einen zweiten Haltepunkt am Ende der Funktion oder des Codebereichs an, den Sie analysieren möchten.

    > [!TIP]
    > Durch das Festlegen von zwei Haltepunkten können Sie die Datensammlung auf die Teile des Code begrenzen, die Sie analysieren möchten.
  
3.  Das Fenster **Diagnosetools** wird automatisch angezeigt, es sei denn, Sie haben es deaktiviert. Klicken Sie auf **Debuggen / Windows / Diagnosetools anzeigen**, um das Fenster erneut aufzurufen.

4.  Mithilfe der Einstellung **Auswahltools** auf der Symbolleiste können Sie auswählen, ob Sie die **CPU-Auslastung**, [Speicherauslastung](../profiling/Memory-Usage.md) oder beides anzeigen möchten. Wenn Sie Visual Studio Enterprise ausführen, können Sie auch IntelliTrace unter **Extras / Optionen / IntelliTrace** aktivieren oder deaktivieren.

     ![Anzeigen von Diagnosetools](../profiling/media/DiagToolsSelectTool.png "DiagToolsSelectTool")

     Wir werden hauptsächlich die CPU-Auslastung betrachten, stellen Sie also sicher, dass **CPU-Auslastung** aktiviert ist (ist standardmäßig aktiviert).

5.  Klicken Sie auf **Debuggen / Debugging starten** (oder auf **Start** auf der Symbolleiste oder auf **F5**).

     Wenn das Laden der Anwendung abgeschlossen ist, wird die Zusammenfassungsansicht der Diagnosetools angezeigt.

     ![Zusammenfassung Diagnosetools](../profiling/media/DiagToolsSummaryTab.png "DiagToolsSummaryTab")

     Weitere Informationen zu den Ereignissen finden Sie unter [Start Debugging (Suchen und Filtern auf der Registerkarte „Ereignisse“ im Fenster „Diagnosetools“)](http://blogs.msdn.com/b/visualstudioalm/archive/2015/11/12/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window.aspx).

6.  Führen Sie das Szenario aus, bei dem Ihr erster Haltepunkt erreicht wird.

7.  Aktivieren Sie während der Debugger angehalten wird die Sammlung von CPU-Auslastungsdaten, und öffnen Sie anschließend die Registerkarte **CPU-Auslastung**.

     ![Diagnosetool CPU-Profilerstellung aktivieren](../profiling/media/DiagToolsEnableCPUProfiling.png "DiagToolsEnableCPUProfiling")

     Wenn Sie **CPU-Profilerstellung aktivieren** auswählen, beginnt Visual Studio, Ihre Funktionen und die für die Ausführung benötigte Zeit aufzuzeichnen. Sie können diese gesammelten Daten nur anzeigen lassen, wenn Ihre Anwendung an einem Haltepunkt angehalten wird.

8.  Drücken Sie F5, um die App bis zum zweiten Haltepunkt auszuführen.

     Jetzt verfügen Sie über Leistungsdaten für Ihre Anwendung, die speziell für den Codebereich gelten, der zwischen den beiden Haltepunkten liegt.

9.  Wählen Sie die Region aus, die Sie in der CPU-Zeitachse analysieren möchten (es muss sich um eine Region handeln, die Profilerstellungsdaten anzeigt).

     ![Diagnosetools Auswahl eines Zeitsegments](../profiling/media/DiagToolsSelectTimeSegment.png "DiagToolsSelectTimeSegment")

     Der Profiler beginnt, Threaddaten vorzubereiten. Warten Sie, bis dieser Vorgang abgeschlossen ist.

     ![Diagnosetools Threads Vorbereiten](../profiling/media/DiagToolsPreparingThreads.png "DiagToolsPreparingThreads")
  
     Das CPU-Auslastungstool zeigt den Bericht unter der Registerkarte **CPU-Auslastung** an.
  
     ![Diagnosetools Registerkarte CPU-Auslastung](../profiling/media/DiagToolsCPUUsageTab.png "DiagToolsCPUUsageTab")

     An diesem Punkt können Sie beginnen, die Daten zu analysieren.

## <a name="Step2"></a> Schritt 2: Analysieren der CPU-Auslastungsdaten

Beginnen Sie bei der Datenanalyse am besten mit der Liste der Funktionen unter „CPU-Auslastung“, stellen Sie fest welche Funktionen die meisten Aufgaben ausführen, und betrachten Sie die einzelnen Funktionen näher.

1. Untersuchen Sie in der Liste der Funktionen die Funktionen, die am meisten Aufgaben ausführen.

    ![Diagnosetools CPU-Auslastung Liste der Funktionen](../profiling/media/DiagToolsCPUUsageFunctionList.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > Die Auflistung der Funktionen beginnt mit der Funktion, die die meisten Aufgaben ausführt (sie sind nicht in der Reihenfolge der Aufrufe gelistet). Dadurch können Sie schnell feststellen, welche Funktionen am längsten ausgeführt werden.

2. Doppelklicken Sie in der Liste der Funktionen auf eine der Funktionen Ihrer App, die viele Aufgaben ausführt.

    Wenn Sie auf eine Funktion doppelklicken, öffnet sich die Ansicht **Aufrufer/Aufgerufener** im linken Bereich. 

    ![Diagnosetools Ansicht Aufrufer-Aufgerufener](../profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")

    In dieser Ansicht erscheint die ausgewählte Funktion in der Überschrift und im Feld **Aktuelle Funktion** ( in diesem Beispiel „GetNumber“). Die Funktion, die die aktuelle Funktion aufgerufen hat, wird links unter **Calling Function** (Aufrufende Funktion) angezeigt, und alle Funktionen, die von der aktuellen Funktion aufgerufen wurden werden im Feld **Called Functions** (Aufgerufene Funktionen) auf der rechten Seite angezeigt. (Sie können beide Felder auswählen, um die aktuelle Funktion zu ändern.)

    In dieser Ansicht wird Ihnen die Gesamtzeit (ms) und der Prozentsatz der gesamten Ausführungszeit der App angezeigt, den die Funktion bis zum Abschluss eingenommen hat.

    Unter **Funktionsrumpf** wird ebenso die Gesamtzeit (und der Prozentsatz der Zeit) angezeigt, die im Funktionsrumpf aufgewendet wurde. Die Zeit, die in aufrufenden und aufgerufenen Funktionen aufgewendet wurde, ist nicht enthalten. (In diesem Beispiel wurden 3713 von 3729 ms im Funktionsrumpf aufgewendet, und die verbleibenden 16 ms wurden im von dieser Funktion aufgerufenen externen Code aufgewendet).

    > [!TIP]
    > Hohe Werte unter **Funktionsrumpf** deuten auf einen Leistungsengpass in der Funktion selbst hin.

3. Wenn Sie eine allgemeinere Übersicht anzeigen möchten, in der die Reihenfolge, in der die Funktionen aufgerufen werden, dargestellt wird, wählen Sie aus der Dropdownliste am oberen Rand des Bereichs **Aufrufstruktur** aus.
 
    Jeder nummerierte Bereich in der Abbildung bezieht sich auf einen Schritt in der Prozedur.
  
    ![Diagnosetools Aufrufstruktur](../profiling/media/DiagToolsCallTree.png "DiagToolsCallTree")
  
|||
|-|-|
|![Schritt 1](../profiling/media/ProcGuid_1.png "ProcGuid_1")|Der oberste Knoten in CPU-Auslastungsaufrufstrukturen ist ein Pseudoknoten.|  
|![Schritt 2](../profiling/media/ProcGuid_2.png "ProcGuid_2")|Wenn die Option [Externen Code anzeigen](#BKMK_External_Code) deaktiviert ist, ist in den meisten Apps der Knoten der zweiten Ebene ein **[External Code]** -Knoten, der den System- und Frameworkcode enthält, der die App startet und beendet, die Benutzeroberfläche zeichnet, die Threadplanung steuert und andere Dienste der unteren Ebene für die App bereitstellt.|  
|![Schritt 3](../profiling/media/ProcGuid_3.png "ProcGuid_3")|Die untergeordneten Elemente des Knotens der zweiten Ebene sind die Benutzercodemethoden und asynchronen Routinen, die vom System- und Frameworkcode der zweiten Ebene aufgerufen oder erstellt werden.|
|![Schritt 4](../profiling/media/ProcGuid_4.png "ProcGuid_4")|Untergeordnete Knoten einer Methode enthalten Daten nur für die Aufrufe der übergeordneten Methode. Wenn **Externen Code anzeigen** deaktiviert ist, können App-Methoden auch den Knoten **[Externer Code]** enthalten.|

Hier finden Sie weitere Informationen zu den Spaltenwerten:

- Mit dem Wert **Gesamt-CPU** wird das Pensum angegeben, das von der Funktion und den von der Funktion aufgerufenen Funktionen bewältigt wurde. Hohe Werte bei „Gesamt-CPU“ deuten auf die insgesamt aufwändigsten Funktionen hin.
  
- Mit dem Wert **Eigen-CPU** wird das bewältigte Pensum des Codes im Funktionsrumpf angegeben. Das Pensum der Funktionen, die durch den Code aufgerufen wurden, ist nicht enthalten. Hohe Werte bei **Eigen-CPU** deuten auf einen Leistungsengpass in der Funktion selbst hin.

- **Module** Der Name des Moduls mit der Funktion oder die Anzahl der Module, die die Funktionen in einem Knoten vom Typ [Externer Code] enthalten.

## <a name="BKMK_External_Code"></a> Externen Code anzeigen

Externer Code umfasst Funktionen in System- und Frameworkkomponenten, die vom Code ausgeführt werden, den Sie schreiben. Externer Code umfasst Funktionen, die die App starten und beenden, die Benutzeroberfläche zeichnen, das Threading steuern und der App andere hardwarenahe Dienste bereitstellen. In den meisten Fällen sind Sie nicht an externem Code interessiert, weshalb das CPU-Auslastungstool die externen Funktionen einer Benutzermethode im Knoten **[Externer Code]** sammelt.
  
Wenn Sie die Aufrufpfade von externem Code anzeigen möchten, wählen Sie aus der Liste **Filteransicht** die Option **Externen Code anzeigen** und dann **Übernehmen**aus.  
  
![Filteransicht auswählen, dann Externen Code anzeigen](../profiling/media/DiagToolsShowExternalCode.png "DiagToolsShowExternalCode")  
  
Achten Sie darauf, dass viele externe Codeaufrufketten tief verschachtelt sind, sodass die Breite der Spalte mit dem Funktionsnamen die Anzeigebreite aller außer sehr großer Computerbildschirme überschreiten kann. In diesem Fall werden Funktionsnamen als **[…]** angezeigt.
  
Verwenden Sie das Suchfeld, um nach einem gewünschten Knoten zu suchen, und verwenden Sie dann die horizontale Bildlaufleiste, um die Daten sichtbar zu machen.

> [!TIP]
> Vergewissern Sie sich bei der Profilerstellung für externen Code, von dem Windows-Funktionen aufgerufen werden, dass Sie über die neuesten .pdb-Dateien verfügen. Ohne diese Dateien werden in den Berichtsansichten kryptische und schwer verständliche Namen von Windows-Funktionen aufgeführt. Weitere Informationen zum Sicherstellen, dass Sie über die erforderlichen Dateien verfügen, finden Sie unter [Specify Symbol (.pdb) and Source Files in the Debugger (Symbol- (.pdb) und Quelldateien im Debugger angeben)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  
## <a name="see-also"></a>Siehe auch  
 [[Speicherauslastung](../profiling/memory-usage.md)
</ph> [CPU-Auslastung](../profiling/cpu-usage.md)
<ph id=" [Profilerstellungstools](../profiling/profiling-tools.md)