---
title: "Marker für die Nebenläufigkeitsschnellansicht | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: dcabdd5ca1381ec15e66637a35044c456411c8c7
ms.lasthandoff: 04/05/2017

---
# <a name="concurrency-visualizer-markers"></a>Parallelitätsschnellansichtsmarker
Marker sind in der Nebenläufigkeitsschnellansicht Symbole zur Darstellung der Ereignisse in einer App.  In der Regel generiert die App diese Ereignisse, um Phasen oder Vorkommen in einer Anwendung zu bestimmen.  Die Ereignisse können von der App oder von Bibliotheken und Laufzeiten generiert werden, die die App verwendet.  
  
## <a name="kinds-of-markers"></a>Arten von Markern  
 In der Nebenläufigkeitsschnellansicht werden drei Arten von Markern benutzt, um Anwendungsereignisse darzustellen: Kennzeichen, Meldungen und Spannen.  
  
1.  Verwenden Sie ein *Kennzeichen*, um auf einen wichtigen Zeitpunkt in Ihrer App hinzuweisen.  Sie können z.B. ein Kennzeichen verwenden, um darzustellen, dass ein variabler Wert einen bestimmten Schwellenwert erreicht hat oder dass eine Ausnahme ausgelöst wurde.  
  
2.  Eine *Mitteilung* weist ebenfalls auf einen Zeitpunkt hin, den Sie jedoch für eine Ablaufverfolgung in Form eines Protokolls verwenden können.  So können Sie beispielsweise ungeordnete Elemente in der Protokolldatei in einem Meldungsaufruf umschließen und sie dadurch in der Nebenläufigkeitsschnellansicht verfolgen und anzeigen. Mit der Nebenläufigkeitsschnellansicht lassen sich diese Daten außerdem in eine CSV-Datei exportieren.  
  
3.  Eine *Spanne* stelle ein Zeitintervall in Ihrer App dar, z.B. eine ihrer Phasen.  
  
## <a name="marker-linkage-to-threads"></a>Markerverknüpfung mit Threads  
 Jeder Thread, der Marker generiert, verfügt über einen separaten Zeitachsenkanal.  Die ID des Threads, der für das Generieren der Markerereignisse zuständig ist, wird neben der Beschreibung des Markerkanals angezeigt.  Die ID, die auf der linken Seite des Markerkanals angezeigt wird, entspricht der ID eines anderen Threads im aktuellen Prozess.  
  
## <a name="marker-importance"></a>Bedeutung der Marker  
 Marker können vier Bedeutungsebenen aufweisen: niedrig, normal, hoch und kritisch.  Sie können die Quellen der Marker anhand ihrer Wichtigkeitsstufe filtern.  Wenn Sie beispielsweise nur Marker einer bestimmten Quelle anzeigen möchten, die eine normale oder kritische Wichtigkeitsstufe hat, können Sie den Filtern im Dialogfeld [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) konfigurieren. Die Wichtigkeit der Marker wird im Tooltip angezeigt, und zwar im [Markerbericht](../profiling/markers-report.md).  
  
## <a name="marker-category"></a>Markerkategorie  
 Die Markerkategorie weist auf eine Gruppe von Markerereignissen hin, die aus derselben Quelle stammen.  Die Nebenläufigkeitsschnellansicht verwendet Farben, um zwischen unterschiedlichen Kategorien von Kennzeichen und Spannen zu unterscheiden. Konfigurieren Sie die Nebenläufigkeitsschnellansicht so, dass Sie anhand von Kategorien die Marker eines bestimmten Ereignisanbieters herausfiltern können.  Verwenden Sie das Dialogfeld [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md), um den Filter entsprechend zu konfigurieren.  
  
## <a name="known-sources-of-markers"></a>Bekannte Markerquellen  
 Jeder ETW-Anbieter kann Marken generieren, solange der Anbieter bestimmte Einschränkungen berücksichtigt. Konfigurieren Sie die Nebenläufigkeitsschnellansicht entsprechend, um zusätzliche Ereignisquellen für Marker zu überwachen. Standardmäßig werden folgende Ereignisquellen überwacht:  
  
-   [Parallelitätsschnellansichts-SDK](../profiling/concurrency-visualizer-sdk.md)  
  
-   [Task Parallel Library (TPL)](http://msdn.microsoft.com/Library/b8f99f43-9104-45fd-9bff-385a20488a23)  
  
-   [Dataflow (Datenfluss)](http://msdn.microsoft.com/Library/643575d0-d26d-4c35-8de7-a9c403e97dd6)  
  
-   [Parallel LINQ (PLINQ) (Paralleles LINQ (PLINQ))](http://msdn.microsoft.com/Library/3d4d0cd3-bde4-490b-99e7-f4e41be96455)  
  
-   [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime)  
  
-   [Scenario Marker Support (Unterstützung für Szenariomarker)](http://msdn.microsoft.com/en-us/e3b55bc2-b451-4214-ae00-0c7f5a5baec8)  
  
-   [C++ AMP (C++ Accelerated Massive Parallelism)](/cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)  
  
 Über die Registerkarte „Marker“ im Dialogfeld [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) können Sie steuern,, ob Marker aus verschiedenen Quellen in der Nebenläufigkeitsschnellansicht angezeigt werden. Außerdem können Sie nach Markern anhand der Wichtigkeit und der Kategorie filtern.  
  
## <a name="markers-from-eventsource"></a>Marker aus EventSource  
 Die Nebenläufigkeitsschnellansicht zeigt auch EventSource-Ereignisse an.  Weitere Informationen finden Sie unter [Visualizing EventSource Events as Markers (Visualisieren von EventSource-Ereignissen als Marker)](../profiling/visualizing-eventsource-events-as-markers.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Flag Markers (Kennzeichenmarker)](../profiling/flag-markers.md)   
 [Message Marker (Meldungsmarker)](../profiling/message-markers.md)   
 [Span Markers (Spannenmarker)](../profiling/span-markers.md)   
 [Visualisieren von EventSource-Ereignissen als Marker](../profiling/visualizing-eventsource-events-as-markers.md)