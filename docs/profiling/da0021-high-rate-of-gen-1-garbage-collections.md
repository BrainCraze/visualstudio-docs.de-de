---
title: "DA0021: Hohes Maß an Garbage Collections der Generation 1 | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.21
- vs.performance.DA0021
- vs.performance.rules.DA0021
ms.assetid: ebf5d9b3-a1ac-4688-8f0f-39a85f4dd15f
caps.latest.revision: 9
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: e666eb5fab2ed4d9d8903f1801c606cd879c9a62
ms.contentlocale: de-de
ms.lasthandoff: 05/13/2017

---
# <a name="da0021-high-rate-of-gen-1-garbage-collections"></a>DA0021: Hohes Maß an Garbage Collections der Generation 1
|||  
|-|-|  
|Regel-ID|DA0021|  
|Kategorie|.NET Framework-Verwendung|  
|Profilerstellungsmethoden|Alle|  
|Meldung|Ein relativ hohes Maß an Garbage Collections der Generation 1 wurde festgestellt. Ist ein Großteil der Programmdatenstrukturen entwurfsbedingt zugeordnet und für einen längeren Zeitraum gespeichert, stellt dies üblicherweise kein Problem dar. Ist dieses Verhalten jedoch nicht beabsichtigt, werden von der Anwendung unter Umständen Objekte festgehalten. Sollten Sie nicht sicher sein, sammeln Sie die .NET-Speicherbelegungsdaten und die Informationen zur Objektlebensdauer, um nachvollziehen zu können, welches Speicherbelegungsmuster von der Anwendung verwendet wird.|  
|Regeltyp|Information|  
  
 Wenn Sie Profile mithilfe der Sampling-, .NET-Arbeitsspeicher- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## <a name="cause"></a>Ursache  
 Die bei der Profilerstellung erfassten Systemleistungsdaten deuten darauf hin, dass bei der Garbage Collection der Generation 1 (im Vergleich zur Datensammlung der Generation 0) ein großer Teil des Arbeitsspeichers für .NET Framework-Objekte freigegeben wurde.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Die Microsoft .NET-CLR (Common Language Runtime) verfügt über einen automatischen Speicherverwaltungsmechanismus, durch den der Speicher von Objekten, die von der Anwendung nicht mehr verwendet werden, mithilfe eines Garbage Collectors freigegeben wird. Der Garbage Collector ist generationsorientiert, da angenommen wird, dass viele Speicherbelegungen kurzlebig sind. Lokale Variablen müssen beispielsweise kurzlebig sein. Neu erstellte Objekte beginnen in Generation 0 (gen 0) und werden zu Generation 1, wenn sie nach einer Ausführung der Garbage Collection noch vorhanden sind, und schließlich zu Generation 2, wenn sie von der Anwendung auch weiterhin verwendet werden.  
  
 Objekte in der Generation 0 werden häufig und i. d. R. äußerst effizient gesammelt. Objekte in der Generation 1 werden nicht so häufig und weniger effizient gesammelt. Und langlebige Objekte in der Generation 2 werden schließlich noch seltener gesammelt. Die Collection der Generation 2, bei der es sich um eine vollständige Ausführung der Garbage Collection handelt, ist zudem der aufwändigste Vorgang.  
  
 Diese Regel wird ausgelöst, wenn anteilsmäßig zu viele Garbage Collections der Generation 1 aufgetreten sind. Sind nach der Collection der Generation 0 zu viele relativ kurzlebige Objekte vorhanden, die dann aber im Rahmen einer Collection der Generation 1 gesammelt werden können, wird der Aufwand für die Speicherverwaltung unter Umständen zu groß. Weitere Informationen finden Sie im Beitrag [Mid-life crisis (Mid­life-Cri­sis)](http://go.microsoft.com/fwlink/?LinkId=177835) unter „Rico Mariani's Performance Tidbits“ (Schmankerln zum Thema Leistung von Rico Mariani) auf der MSDN-Website.  
  
## <a name="how-to-investigate-a-warning"></a>Vorgehensweise bei der Überprüfung einer Warnung  
 Doppelklicken Sie auf die Meldung im Fenster „Fehlerliste“, um zur Ansicht [Markierungen](../profiling/marks-view.md) der Profilerstellungsdaten zu navigieren. Suchen Sie die Spalten **.NET CLR-Speicher\\Auflistungsanzahl der Generation 0** und **.NET CLR-Speicher\\Auflistungsanzahl der Generation 1**. Überprüfen Sie, ob die Garbage Collection in bestimmten Phasen der Programmausführung besonders häufig auftritt. Vergleichen Sie diese Werte mit den Werten der Spalte **GC-Zeitdauer in Prozent**, um zu überprüfen, ob das Muster für verwaltete Speicherbelegungen einen übermäßig hohen Speicherverwaltungsaufwand verursacht.  
  
 Führen Sie die Profilerstellung mithilfe eines .NET-Speicherbelegungsprofils erneut aus, und rufen Sie Informationen zur Objektlebensdauer ab, damit Sie das Muster für die verwaltete Speicherauslastung der Anwendung nachvollziehen können.  
  
 Informationen zur Verbesserung der Garbage Collection-Leistung finden Sie unter [Garbage Collector-Grundlagen und Tipps zur Leistung](http://go.microsoft.com/fwlink/?LinkId=148226) auf der Microsoft-Website. Informationen zum Mehraufwand der automatischen Garbage Collection finden Sie unter [Large Object Heap Uncovered (Informationen zum Heap für große Objekte)](http://go.microsoft.com/fwlink/?LinkId=177836).