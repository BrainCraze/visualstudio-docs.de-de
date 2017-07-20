---
title: Modellieren von benutzeranforderungen | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- requirements
- stories
ms.assetid: 359900f8-6d69-493d-bfdf-2c9069c74a26
caps.latest.revision: 28
author: alexhomer1
ms.author: ahomer
manager: douge
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
translationtype: Machine Translation
ms.sourcegitcommit: 08aabdfe0e268f93ef7723076375b7f65b15ccf3
ms.openlocfilehash: 60866c46920bb85927498992082763f9e34b4137
ms.lasthandoff: 02/22/2017

---
# <a name="model-user-requirements"></a>Modellieren von Benutzeranforderungen
Visual Studio hilft Ihnen dabei, die Anforderungen der Benutzer zu verstehen, zu besprechen und zu kommunizieren, indem Diagramme über ihre Aktivitäten und die Rolle Ihres System bei der Erreichung ihrer Ziele gezeichnet werden. Ein Anforderungsmodell ist ein Satz dieser Diagramme, von denen sich jedes auf einen anderen Aspekt der Benutzeranforderungen konzentriert. Eine Videodemo finden Sie unter: [Modeling the Business Domain](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/)(Modellieren der Geschäftsdomäne) .  
  
 Welche Versionen von Visual Studio jeden Typ von Modell unterstützen, finden Sie unter [versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Ein Anforderungsmodell hilft Ihnen bei Folgendem:  
  
-   Konzentration auf das externe Verhalten des Systems, unabhängig von seinem internen Entwurf.  
  
-   Beschreiben der Anforderungen von Benutzern und Projektbeteiligten mit deutlich weniger Mehrdeutigkeiten als in der natürlichen Sprache.  
  
-   Definieren eines konsistenten Glossars von Begriffen, das von Benutzern, Entwicklern und Testern verwendet werden kann.  
  
-   Reduzieren von Lücken und Inkonsistenzen hinsichtlich der Anforderungen.  
  
-   Reduzieren der für die Reaktion auf Anforderungsänderungen notwendigen Arbeit.  
  
-   Planen der Reihenfolge, in der Funktionen entwickelt werden.  
  
-   Verwenden der Modelle als Grundlage für Systemtests, um eine klare Beziehung zwischen den Tests und den Anforderungen herzustellen. Wenn sich die Anforderungen ändern, hilft Ihnen diese Beziehung beim ordnungsgemäßen Aktualisieren der Tests. Dadurch wird sichergestellt, dass das System die neuen Anforderungen erfüllt.  
  
 Ein Anforderungsmodell bietet den größten Vorteil, wenn Sie es für die Ausrichtung von Besprechungen mit den Benutzern oder ihren Vertretern einsetzen und es am Anfang jeder Iteration überdenken. Sie müssen es nicht im Detail fertigstellen, bevor Sie Code schreiben. Eine teilweise funktionierende Anwendung bildet in der Regel, auch wenn sie sehr vereinfacht ist, die anregendste Grundlage für die Besprechung der Anforderungen mit den Benutzern. Das Modell ist eine effektive Methode, um die Ergebnisse solcher Diskussionen zusammenzufassen. Weitere Informationen finden Sie unter [Verwenden von Modellen im Entwicklungsprozess](../modeling/use-models-in-your-development-process.md).  
  
> [!NOTE]
>  In diesen Themen meint „System“ das System oder die Anwendung, das bzw. die Sie entwickeln. Es kann sich um eine umfangreiche Sammlung von vielen Software- und Hardwarekomponenten, eine einzelne Anwendung oder eine Softwarekomponente in einem größeren System handeln. In jedem Fall beschreibt das Anforderungsmodell das Verhalten, das über eine Benutzeroberfläche oder eine API von außerhalb Ihres Systems sichtbar ist.  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
 Sie können verschiedene Ansichten der Benutzeranforderungen erstellen.  Jede Ansicht bietet eine bestimmte Art von Informationen.  Wenn Sie diese Ansichten erstellen, empfiehlt es sich, häufig zwischen ihnen zu wechseln. Sie können bei jeder Ansicht starten.  
  
|Diagramm oder Dokument|Was es in einem Anforderungsmodell beschreibt|Abschnitt|  
|-------------------------|-----------------------------------------------|-------------|  
|Konzeptionelles Klassendiagramm|Glossar von Typen, die zum Beschreiben der Anforderungen verwendet werden; die auf der Benutzeroberfläche des Systems sichtbaren Typen.||  
|Zusätzliche Dokumente oder Arbeitsaufgaben|Kriterien für die Leistung, Sicherheit, Nutzbarkeit und Zuverlässigkeit|[Beschreiben von servicequalitätsanforderungen](#QoSRequirements)|  
|Zusätzliche Dokumente oder Arbeitsaufgaben|Einschränkungen und Regeln, die nicht spezifisch für einen bestimmten Anwendungsfall sind|[Anzeigen von Geschäftsregeln](#BusinessRules)|  
  
 Beachten Sie, dass die meisten Diagrammtypen für andere Zwecke verwendet werden können. Eine Übersicht über die Diagrammtypen finden Sie unter [Erstellen von Modellen für Ihre app](../modeling/create-models-for-your-app.md).
  
##  <a name="a-namebusinessrulesa-showing-business-rules"></a><a name="BusinessRules"></a>Anzeigen von Geschäftsregeln  
 Eine Geschäftsregel ist eine Anforderung, die mit keinem speziellen Anwendungsfall verknüpft ist und im ganzen System zu beachten ist.  
  
 Viele Geschäftsregeln sind Einschränkungen der Beziehungen zwischen den konzeptionellen Klassen. Sie können diese *statischen**Geschäftsregeln* als Kommentare schreiben, die mit den entsprechenden Klassen in einem konzeptionellen Diagramm verknüpft sind. Zum Beispiel:  
  
 ![Regel in an Order-Klasse angefügtem Kommentar. ] (../modeling/media/uml_reqmcd2.png "UML_ReqmCD2")  
  
 *Dynamische Geschäftsregeln* schränken die zulässigen Sequenzen von Ereignissen ein. Beispielsweise verwenden Sie ein Sequenz- oder Aktivitätsdiagramm, um zu zeigen, dass sich ein Benutzer anmelden muss, bevor er andere Vorgänge im System durchführen kann.  
  
 Allerdings können viele dynamische Regeln effektiver und allgemeiner durch Ersetzung durch statische Regeln angegeben werden. Beispielsweise können Sie einer Klasse im konzeptionellen Klassenmodell ein boolesches Attribut „Angemeldet“ hinzufügen. Sie würden „Angemeldet“ als Nachbedingung des Anwendungsfalls für das Anmelden hinzufügen und als Vorbedingung für die meisten der anderen Anwendungsfälle. Mit diesem Ansatz können Sie vermeiden, alle möglichen Kombinationen von Ereignissequenzen definieren zu müssen. Zudem ist dieses Vorgehen flexibler, wenn Sie dem Model neue Anwendungsfälle hinzufügen müssen.  
  
 Beachten Sie, dass hier zu entscheiden ist, wie Sie die Anforderungen definieren, und dass dies unabhängig von der Implementierung der Anforderungen im Programmcode ist.  
  
 Weitere Informationen finden Sie in den folgenden Themen:  
  
|Thema|Lesen|  
|--------------------|----------|  
|Entwickeln von Code, der Geschäftsregeln entspricht|[Modellieren der Architektur Ihrer App](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="a-nameqosrequirementsa-describing-quality-of-service-requirements"></a><a name="QoSRequirements"></a>Beschreiben von Servicequalitätsanforderungen  
 Es gibt mehrere Kategorien von Servicequalitätsanforderungen. Hierzu gehören Folgende:  
  
-   Leistung  
  
-   Sicherheit  
  
-   Verwendbarkeit  
  
-   Zuverlässigkeit  
  
-   Stabilität  
  
 Sie können einige dieser Anforderungen in die Beschreibungen bestimmter Anwendungsfälle einschließen. Andere Anforderungen sind nicht spezifisch für Anwendungsfälle und werden am effektivsten in ein separates Dokument geschrieben. Es ist nützlich, nach Möglichkeit das von den Anforderungsmodellen definierte Vokabular einzuhalten. Beachten Sie im nächsten Beispiel, dass die in der Anforderung verwendeten Hauptwörter den Titeln von Akteuren, Anwendungsfällen und Klassen in den vorangehenden Abbildungen entsprechen:  
  
 Wenn ein Restaurant ein Gericht löscht, während ein Kunde eine Mahlzeit bestellt, werden Bestellpositionen, die sich auf dieses Gericht beziehen, rot angezeigt.  
  
 Weitere Informationen finden Sie in den folgenden Themen:  
  
|Thema|Lesen|  
|--------------------|----------|  
|Genauere Informationen zum Aufzeichnen von Servicequalitätsanforderungen|[Richtlinien zum Definieren von Servicequalitätsanforderungen](http://msdn.microsoft.com/en-us/9677a437-c2cb-4ac4-8c2d-4e3350005f06)|  
|Entwickeln von Code, der Servicequalitätsanforderungen entspricht|[Modellieren der Architektur Ihrer App](../modeling/model-your-app-s-architecture.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Modellen im Entwicklungsprozess](../modeling/use-models-in-your-development-process.md)   
 [Modellieren der Architektur Ihrer App](../modeling/model-your-app-s-architecture.md)   
