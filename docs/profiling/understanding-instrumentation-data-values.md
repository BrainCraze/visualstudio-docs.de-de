---
title: Grundlagen zu Instrumentierungsdatenwerten | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiling Tools,instrumentation
- instrumentation profiling method
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d44e53afbd6c1d3f3ef8aa7fe1546a157f13cd96
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2018
---
# <a name="understanding-instrumentation-data-values"></a>Grundlagen zu Instrumentationsdatenwerten

Die Profilerstellungsmethode *Instrumentierung* von Visual Studio zeichnet detaillierte Informationen zur zeitlichen Steuerung für die Funktionsaufrufe, Zeilen und Anweisungen in der Anwendung auf, für die ein Profil erstellt wurde.

Die Instrumentierungsmethode fügt Code am Anfang und Ende der Zielfunktionen in der profilierten Binärdatei ein sowie vor und nach jedem Aufruf von diesen Funktionen an andere Funktionen. Der eingefügte Code zeichnet Folgendes auf:

- Das Intervall zwischen diesem Auflistungsereignis und dem vorherigen.

- Ob das Betriebssystem während des Intervalls einen Vorgang ausgeführt hat. Das Betriebssystem könnte z.B. von der Festplatte lesen oder auf die Festplatte schreiben oder zwischen dem Zielthread und einem anderen Thread in einem anderen Prozess wechseln.

Für jedes Intervall rekonstruiert die Profileranalyse die Aufrufliste, die am Ende des Intervalls vorhanden war. Eine Aufrufliste ist die Liste der Funktionen, die zu einem bestimmten Zeitpunkt auf einem Prozessor aktiv sind. Nur eine Funktion (die aktuelle Funktion) führt Code aus. Die anderen Funktionen sind die Kette von Funktionsaufrufen, die zum Aufruf der aktuellen Funktion (der Aufrufliste) geführt haben.

Für jede Funktion in der Aufrufliste fügt die Profileranalyse beim Aufzeichnen des Intervalls das Intervall zu einem oder mehreren von vier Datenwerten für die Funktion hinzu. Die Analyse fügt das Intervall einem Datenwert für eine Funktion anhand von zwei Kriterien hinzu:

- Ob das Intervall im Code der Funktion oder in einer *untergeordneten Funktion* (einer durch die Funktion aufgerufenen Funktion) aufgetreten ist.

- Ob ein Betriebssystemereignis im Intervall aufgetreten ist.

Die Datenwerte für ein Intervall einer Funktion oder eines Datenbereichs heißen *Verstrichene inklusive Zeit*, *Verstrichene exklusive Zeit*, *Inklusive Anwendungszeit* und *Exklusive Anwendungszeit*:

- Alle Intervalle einer Funktion werden dem Datenwert „Verstrichene inklusive Zeit“ hinzugefügt.

- Wenn das Intervall im Code der Funktion und nicht in einer untergeordneten Funktion aufgetreten ist, wird das Intervall dem Datenwert „Verstrichene exklusive Zeit“ der Funktion hinzugefügt.

- Wenn im Intervall kein Betriebssystemereignis aufgetreten ist, wird das Intervall dem Datenwert „Inklusive Anwendungszeit“ hinzugefügt.

- Wenn im Intervall kein Betriebssystemereignis aufgetreten ist und das Intervall bei der direkten Ausführung des Funktionscodes (d.h. nicht in einer untergeordneten Funktion) aufgetreten ist, wird das Intervall dem Datenwert „Exklusive Anwendungszeit“ hinzugefügt.

In den Berichten der Profilerstellungstools werden die Gesamtwerte der Funktionen in der Profilerstellungssitzung sowie die Prozesse, Threads und binären Dateien der Sitzung aggregiert.

## <a name="elapsed-inclusive-values"></a>Werte für „Verstrichene inklusive Zeit“

Die Gesamtzeit, die für die Ausführung einer Funktion und deren untergeordneter Funktionen aufgewendet wurde.

Werte für „Verstrichene inklusive Zeit“ umfassen die Intervalle für die direkte Ausführung des Funktionscodes und die Intervalle für die Ausführung der untergeordneten Funktionen der Zielfunktion. Intervalle der Funktion oder deren untergeordneter Funktionen, die Wartezeit für das Betriebssystem umfassen, sind ebenfalls in den Werten für „Verstrichene inklusive Zeit“ enthalten.

## <a name="elapsed-exclusive-values"></a>Werte für „Verstrichene exklusive Zeit“

Die Zeit, die für die Ausführung einer Funktion aufgewendet wurde, ausschließlich der für untergeordnete Funktionen aufgewendeten Zeit.

Werte für „Verstrichene exklusive Zeit“ umfassen die Intervalle für die direkte Ausführung des Funktionscodes unabhängig davon, ob im Intervall ein Betriebssystemereignis aufgetreten ist. Alle Intervalle für untergeordnete Funktionen, die von der Zielfunktion aufgerufen wurden, sind nicht in den Werten für „Verstrichene exklusive Zeit“ enthalten.

## <a name="application-inclusive-values"></a>Werte für „Inklusive Anwendungszeit“

Die Zeit, die für die Ausführung einer Funktion und deren untergeordneter Funktionen aufgewendet wurde, ausschließlich der für Betriebssystemereignisse aufgewendeten Zeit.

Werte für „Inklusive Anwendungszeit“ enthalten keine Intervalle, die Betriebssystemereignisse enthalten. Werte für „Inklusive Anwendungszeit“ umfassen alle anderen Intervalle für die Ausführung einer Funktion unabhängig davon, ob das Intervall für die direkte Ausführung des Funktionscodes oder für untergeordnete Funktionen der Zielfunktion aufgewendet wurde.

## <a name="application-exclusive-values"></a>Werte für „Exklusive Anwendungszeit“

Die Zeit, die für die Ausführung einer Funktion aufgewendet wurde, ausschließlich der für untergeordnete Funktionen und Betriebssystemereignisse aufgewendeten Zeit.

Werte für „Exklusive Anwendungszeit“ umfassen keine Intervalle, die Betriebssystemereignisse enthalten, und keine Intervalle für die Ausführung von Funktionen, die durch die Funktion aufgerufen wurden. Werte für „Exklusive Anwendungszeit“ umfassen nur die Intervalle, die für die direkte Ausführung des Funktionscodes aufgewendet wurden und die kein Betriebssystemereignis enthalten.

## <a name="elapsed-inclusive-percent"></a>„Verstrichene inklusive Zeit“ in Prozent

Der prozentuale Anteil von Werten für „Verstrichene inklusive Zeit“ von Funktion, Modul, Thread oder Prozess an den Gesamtwerten für Verstrichene inklusive Zeit der Profilerstellungssitzung.

100 * Verstrichene inklusive Zeit der Funktion / Verstrichene inklusive Zeit der Sitzung

## <a name="elapsed-exclusive-percent"></a>„Verstrichene exklusive Zeit“ in Prozent

Der prozentuale Anteil von Werten für „Verstrichene exklusive Zeit“ von Funktion, Modul, Thread oder Prozess an den Gesamtwerten für „Verstrichene inklusive Zeit“ der Profilerstellungssitzung.

100 * Verstrichene exklusive Zeit der Funktion / Verstrichene inklusive Zeit der Sitzung

## <a name="application-inclusive-percent"></a>„Inklusive Anwendungszeit“ in Prozent

Der prozentuale Anteil von Werten für „Inklusive Anwendungszeit“ von Funktion, Modul, Thread oder Prozess an den Gesamtwerten für „Inklusive Anwendungszeit“ der Profilerstellungssitzung.

100 * Inklusive Anwendungszeit der Funktion / Inklusive Anwendungszeit der Sitzung

## <a name="application-exclusive-percent"></a>„Exklusive Anwendungszeit“ in Prozent

Der prozentuale Anteil von Werten für „Exklusive Anwendungsintervalle“ von Funktion, Modul, Thread oder Prozess an den Gesamtwerten für „Inklusive Anwendungszeit“ der Profilerstellungssitzung.

100 * Exklusive Anwendungszeit der Funktion / Inklusive Anwendungszeit der Sitzung

## <a name="see-also"></a>Siehe auch

[Analysieren der durch Leistungstools erstellten Daten](../profiling/analyzing-performance-tools-data.md)  
[Vorgehensweise: Auswählen von Sammlungsmethoden](../profiling/how-to-choose-collection-methods.md)