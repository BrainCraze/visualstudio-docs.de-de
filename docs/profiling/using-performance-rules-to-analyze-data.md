---
title: "Verwenden von Leistungsregeln zur Analyse von Profilerstellungsdaten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Verwenden von Leistungsregeln zur Analyse von Profilerstellungsdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Leistungswarnungen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools deuten auf Probleme in einer profilierten Anwendung hin, die die Programmausführung verlangsamen können.  Warnungen können auch anzeigen, dass Sie möglicherweise die Auflistungsmethoden ändern müssen, um nützlichere Daten zu erfassen.  Leistungswarnungen werden automatisch in einer Profilerstellungssitzung generiert.  Die Warnungen werden im Fenster **Fehlerliste** angezeigt, wenn eine Datei mit Profilerstellungsdaten in Visual Studio geöffnet wird.  Im Fenster **Fehlerliste** können Sie den Quellcode zu dem Problem suchen und ausführliche Informationen zu dem Fehler anzeigen, z. B. Informationen zur Problembehebung.  Sie können außerdem Warnungen deaktivieren, die für Sie nicht relevant sind.  
  
> [!NOTE]
>  Leistungswarnungen des Profilers werden mithilfe der dynamischen Analyse bei der Programmausführung generiert; es besteht kein Zusammenhang mit Codeanalysewarnungen.  Mit der Codeanalyse können auch Leistungswarnungen für verwalteten Code auf Grundlage der statischen Analyse des Quellcodes generiert werden.  Weitere Informationen finden Sie unter [Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) und [Leistungswarnungen](../code-quality/performance-warnings.md).  
  
## In diesem Abschnitt  
 [Gewusst wie: Anzeigen von Leistungswarnungen](../profiling/how-to-view-performance-warnings.md)  
 Enthält Informationen zum Öffnen des Fensters **Fehlerliste**, um Leistungswarnungen des Profilers anzuzeigen.  
  
 [Gewusst wie: Aktivieren und Deaktivieren von Leistungsregeln](../profiling/how-to-configure-performance-rules.md)  
 Enthält Informationen zum Aktivieren und Deaktivieren von einzelnen Leistungswarnungen.  
  
 [Referenz zu den Leistungsregeln](../profiling/performance-rules-reference.md)  
 Enthält ausführliche Informationen zu den Leistungswarnungen des Profilers.