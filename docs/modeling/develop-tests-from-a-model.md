---
title: Entwickeln von Tests aus einem Modell | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tests and requirements
ms.assetid: 40f87192-ba85-4552-8804-314a678261ae
caps.latest.revision: 20
author: alexhomer1
ms.author: ahomer
manager: douge
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 08aabdfe0e268f93ef7723076375b7f65b15ccf3
ms.openlocfilehash: b7cb109d11669f411b5ca3bdf3c4c32a63ac53a1
ms.contentlocale: de-de
ms.lasthandoff: 02/22/2017

---
# <a name="develop-tests-from-a-model"></a>Entwickeln von Tests aus einem Modell
Sie können Anforderungen und architektonische Modelle verwenden, um die Tests des Systems und seiner Komponenten zu organisieren. Hierdurch wird sichergestellt, dass Sie die für die Benutzer und anderen Projektbeteiligten wichtigen Anforderungen testen, und es hilft Ihnen, die Tests schnell zu aktualisieren, wenn sich die Anforderungen ändern. Bei Verwendung von [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] können Sie auch Verknüpfungen zwischen den Modellen und den Tests verwalten.  
  
 Welche Versionen von Visual Studio diese Features unterstützen, finden Sie unter [versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="system-and-subsystem-testing"></a>Testen von System und Subsystemen  
 *Systemtests,* auch bekannt als *Akzeptanztests*, wird überprüft, ob die Anforderungen der Benutzer erfüllt werden. Diese Tests beziehen sich auf das nach außen hin sichtbare Verhalten des Systems und nicht auf den internen Entwurf.  
  
 Systemtests sind sehr wertvoll, wenn Sie ein System erweitern oder neu entwerfen. Sie unterstützen Sie dabei, bei der Änderung des Codes Fehler zu vermeiden.  
  
 Wenn Sie eine Änderung oder Erweiterung eines Systems planen, ist es hilfreich, mit einer Reihe von Systemtests zu beginnen, die auf dem vorhandenen System ausgeführt werden. Dann können Sie die Tests erweitern oder anpassen, um die neuen Anforderungen zu testen, die Änderungen am Code vornehmen und den vollständigen Satz von Tests erneut ausführen.  
  
 Wenn Sie ein neues System entwickeln, können Sie direkt zu Beginn der Entwicklung anfangen, Tests zu erstellen. Indem Sie Tests definieren, bevor die einzelnen Funktionen entwickelt werden, können Sie die Besprechungen der Anforderungen auf sehr spezifische Weise erfassen.  
  
 Beim Testen von Subsystemen werden dieselben Prinzipien auf die Hauptkomponenten eines Systems angewendet. Jede Komponente wird getrennt von den anderen Komponenten getestet. Subsystemtests konzentrieren sich auf das Verhalten, das auf den Benutzeroberflächen oder der API der Komponente sichtbar ist.  
  
## <a name="deriving-system-tests-from-a-requirements-model"></a>Ableiten von Systemtests aus einem Anforderungsmodell  
 Sie können eine Beziehung zwischen Systemtests und einem Anforderungsmodell erstellen und verwalten. Um diese Beziehung zu erstellen, schreiben Sie Tests, die den wichtigsten Elementen des Anforderungsmodells entsprechen. Visual Studio hilft Ihnen, diese Beziehung zu verwalten, indem es Ihnen ermöglicht, Verknüpfungen zwischen den Tests und Teilen des Modells zu erstellen. Weitere Informationen über Anforderungsmodelle finden Sie unter [Modellieren von benutzeranforderungen](../modeling/model-user-requirements.md).  
  
### <a name="write-tests-for-each-use-case"></a>Schreiben von Tests für jeden Anwendungsfall  
 Bei Verwendung von [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] können Sie eine Gruppe von Tests für jeden Anwendungsfall erstellen, den Sie im Anforderungsmodell definiert haben. Wenn Sie beispielsweise einen Anwendungsfall zur Bestellung einer Mahlzeit haben, der das Erstellen der Bestellung und das Hinzufügen des Position zur Bestellung umfasst, können Sie Tests für den allgemeinen und den ausführlicheren Anwendungsfall erstellen. 
  
 Diese Richtlinien können hilfreich sein:  
  
-   Für jeden Anwendungsfall sollte es mehrere Tests geben, für Hauptpfade und außergewöhnliche Ergebnisse.  
  
-   Wenn Sie einen Anwendungsfall im Anforderungsmodell beschreiben, ist es wichtiger, seine Nachbedingung zu definieren, das heißt das erreichte Ziel, anstatt die Verfahren, die der Benutzer zum Erreichen des Ziels befolgt, detailliert zu beschreiben. Die Nachbedingung für die Bestellung einer Mahlzeit beispielsweise kann sein, dass ein Restaurant eine Mahlzeit für einen Kunden zubereitet und der Kunde bezahlt hat. Die Nachbedingung ist das Kriterium, das durch Ihre Tests überprüft werden sollte.  
  
-   Lassen Sie verschiedene Tests auf den unterschiedlichen Klauseln der Nachbedingung basieren. Erstellen Sie beispielsweise separate Tests für die Benachrichtigung des Restaurants über die Bestellung und für das Empfangen der Zahlung vom Kunden. Diese Trennung bietet folgende Vorteile:  
  
    -   Änderungen verschiedener Aspekte der Anforderungen treten häufig unabhängig voneinander auf. Durch ein derartiges Aufteilen der Tests in verschiedene Aspekte ist es einfacher, die Tests zu aktualisieren, wenn sich Anforderungen ändern.  
  
    -   Wenn laut Entwicklungsplan ein Aspekt des Anwendungsfalls vor einem anderen implementiert wird, können Sie die Tests im Verlauf der Entwicklung getrennt aktivieren.  
  
-   Wenn Sie die Tests entwerfen, trennen Sie die Auswahl der Testdaten vom Code oder Skript, das bestimmt, ob die Nachbedingung erreicht wurde. Beispielsweise kann ein Test einer einfachen arithmetischen Funktion folgendermaßen aussehen: Eingabe ist 4. Prüfen Sie, ob die Ausgabe 2 ist. Entwerfen Sie das Skript stattdessen folgendermaßen: Wählen Sie eine Eingabe. Multiplizieren Sie die Ausgabe mit sich selbst, und prüfen Sie, ob das Ergebnis der ursprünglichen Eingabe entspricht. Durch dieses Format können Sie die Testeingaben variieren, ohne den Hauptteil des Tests zu ändern.  
  
#### <a name="linking-tests-to-use-cases"></a>Verknüpfen von Tests mit Anwendungsfällen  
 Bei Verwendung von [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] zum Entwerfen und die Tests ausführen, können Sie die Tests unter der Voraussetzung, Anwendungsfall- oder User Story-Arbeitsaufgaben organisieren. Sie können diese Arbeitsaufgaben mit Anwendungsfällen im Modell verknüpfen. Auf diese Weise können Sie Änderungen der Anforderungen für die Tests schnell nachverfolgen und den Fortschritt der einzelnen Anwendungsfälle prüfen.  
  
###### <a name="to-link-tests-to-a-use-case"></a>So verknüpfen Sie Tests mit einem Anwendungsfall  
  
1.  Erstellen Sie in [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] eine Anforderung, und lassen Sie eine Testsammlung auf dieser basieren.
  
     Die von Ihnen erstellte Anforderung ist eine Arbeitsaufgabe in [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. In Abhängigkeit von der Prozessvorlage, die Ihr Projekt mit [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] verwendet, kann es sich um eine User Story-, Anforderungs- oder Anwendungsfall-Arbeitsaufgabe handeln. Weitere Informationen finden Sie unter [Nachverfolgen von Arbeit mit Visual Studio Team Services oder Team Foundation Server](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503).  
  
2.  Verknüpfen Sie die Anforderungsarbeitsaufgabe mit einem oder mehreren Anwendungsfällen im Modell.  
  
     In einem Anwendungsfalldiagramm mit der rechten Maustaste eines Anwendungsfalls, und klicken Sie dann auf **mit Arbeitsaufgabe verknüpfen**. Weitere Informationen finden Sie unter [Verknüpfen von Modellelementen und Arbeitsaufgaben](../modeling/link-model-elements-and-work-items.md).  
  
3.  Fügen Sie der Testsammlung Testfälle hinzu, die die Anwendungsfälle überprüfen.  
  
 In der Regel ist jede User Story- oder Anforderungsarbeitsaufgabe mit mehreren Anwendungsfällen im Modell verknüpft, und jeder Anwendungsfall ist mit mehreren User Storys oder Anforderungen verknüpft. Das liegt daran, dass jede User Story oder Anforderung eine Reihe von Aufgaben abdeckt, die mehrere Anwendungsfälle entwickeln. In einer frühen Iteration des Projekts beispielsweise könnten Sie die grundlegende User Story entwickeln, in der ein Kunde Positionen aus einem Katalog auswählen und bestellen kann. In einer späteren Iteration könnte die Story so aussehen, dass der Benutzer beim Abschließen der Bestellung zahlt und der Lieferant das Geld erhält, nachdem er die Waren versendet hat.  Jede Story fügt der Nachbedingung des Anwendungsfalls zur Bestellung von Waren eine Klausel hinzu.  
  
 Sie können separate Verknüpfungen von Anforderungen Kommentare zu den Klauseln der Nachbedingung erstellen, indem Sie diese Klauseln im Anwendungsfalldiagramm in separate Kommentare schreiben. Sie können jeden Kommentar mit einer Anforderungsarbeitsaufgabe und den Kommentar mit dem Anwendungsfall im Diagramm verknüpfen.  
  
### <a name="base-tests-on-the-requirements-types"></a>Basieren von Tests auf den Anforderungstypen  
 Die Typen, das heißt die Klassen, Schnittstellen und Enumerationen, eines Anforderungsmodells beschreiben die Konzepte und Beziehungen im Hinblick darauf, wie Benutzer über ihr Geschäft denken und kommunizieren. Es schließt Typen aus, die sich nur mit dem internen Entwurf des Systems befassen.  
  
 Entwerfen Sie die Tests im Hinblick auf diese Anforderungstypen. Dieses Verfahren hilft Ihnen dabei, sicherzustellen, dass sie die Änderungen bei der Besprechung von Anforderungsänderungen einfach mit den erforderlichen Änderungen in den Tests in Beziehung setzen können. Es ermöglicht, die Tests und ihre beabsichtigten Ergebnisse direkt mit Endbenutzern und anderen Projektbeteiligten zu besprechen. Dies bedeutet, dass die Anforderungen des Benutzers aus dem Entwicklungsprozess herausgehalten werden, und es wird vermieden, dass Fehler im Entwurf beim Testentwurf übersehen werden.  
  
 Bei manuellen Tests umfasst dieses Verfahren die Einhaltung des Vokabulars des Anforderungsmodells in den Testskripts. Bei automatisierten Tests umfasst dieses Verfahren die Verwendung der Anforderungsklassendiagramme als Grundlage für den Testcode sowie das Erstellen von Accessor- und Aktualisierungsfunktionen, um das Anforderungsmodell mit dem Code zu verknüpfen.  
  
 Beispielsweise kann ein Anforderungsmodell die Typen Speisekarte, Gericht, Bestellung und Zuordnungen zwischen diesen Typen umfassen. Dieses Modell stellt die Informationen dar, die vom Bestellsystem gespeichert und behandelt werden, aber nicht die Komplexität seiner Implementierung. Im Arbeitssystem gibt es möglicherweise mehrere unterschiedliche Umsetzungen jedes Typs, in Datenbanken, in Benutzeroberflächen und in APIs. In einem verteilten System gibt es möglicherweise mehrere Varianten der einzelnen Instanzen, die gleichzeitig in verschiedenen Teilen des Systems gespeichert werden.  
  
 Um einen Anwendungsfall wie das Hinzufügen einer Position zur Bestellung zu testen, kann eine Testmethode Code enthalten, der dem folgenden ähnelt:  
  
```  
Order order = ... ; // set up an order  
// Store prior state:  
int countBefore = order.MenuItems.Count;   
// Perform use case:  
MenuItem chosenItem = ...; // choose an item  
AddItemToOrder (chosenItem, order);   
// Verify part of postcondition:  
int countAfter = order.MenuItems.Count;  
Assert (countAfter == countBefore = 1);   
```  
  
 Beachten Sie, dass diese Testmethode die Klassen des Anforderungsmodells verwendet. Zuordnungen und Attribute werden als Eigenschaften von .NET realisiert.  
  
 Damit dies funktioniert, müssen die Eigenschaften der Klassen als schreibgeschützte Funktionen oder Accessoren definiert werden, die auf das System zugreifen, um Informationen zu dessen aktuellem Status abzurufen. Methoden, die Anwendungsfälle simulieren, wie „AddItemToOrder“, müssen das System durch seine API oder durch eine Ebene unterhalb der Benutzeroberfläche steuern. Die Konstruktoren von Testobjekten wie „Order“ und „MenuItem“ müssen außerdem dafür sorgen, dass die entsprechenden Positionen im System erstellt werden.  
  
 Viele der Accessoren und Aktualisierungen werden bereits durch die normale API der Anwendung verfügbar sein. Einige zusätzliche Funktionen müssen jedoch möglicherweise geschrieben werden, um die Tests zu ermöglichen. Diese zusätzlichen Accessoren und Aktualisierungen werden manchmal als „Testinstrumentation“ bezeichnet. Da sie vom inneren Entwurf des Systems abhängen, müssen sie von den Entwicklern des Systems bereitgestellt werden, wohingegen die Tester den Code für die Tests im Hinblick auf das Anforderungsmodell schreiben.  
  
 Wenn Sie automatisierte Tests schreiben, können Sie generische Tests verwenden, um Accessoren und Aktualisierungen zu umschließen.
  
### <a name="tests-for-business-rules"></a>Tests für Geschäftsregeln  
 Einige Anforderungen beziehen sich nicht direkt auf einen bestimmten Anwendungsfall. Das Unternehmen DinnerNow beispielsweise ermöglicht es Kunden, aus zahlreichen Speisekarten zu wählen, schreibt jedoch vor, dass die in einer Bestellung ausgewählten Positionen aus einer einzigen Speisekarte stammen müssen. Diese Geschäftsregel kann als Invariant hinsichtlich der Zuordnungen zwischen Bestellungen, Speisekarten und Positionen im Anforderungsklassenmodell ausgedrückt werden.  
  
 Eine invariante Regel dieser Art regelt nicht nur alle aktuell definierten Anwendungsfälle, sondern auch alle anderen Anwendungsfälle, die später definiert werden. Daher ist es nützlich, sie unabhängig von Anwendungsfällen zu schreiben und getrennt von ihnen zu testen.  
  
## <a name="deriving-subsystem-tests-from-models"></a>Ableiten von Subsystemtests aus Modellen  
 Im allgemeinen Entwurf eines großen Systems können Sie Komponenten oder Subsysteme identifizieren. Diese stellen Teile dar, die getrennt voneinander entworfen werden können oder sich auf verschiedenen Computern befinden oder bei denen es sich um wiederverwendbare Module handelt, die auf verschiedene Weise kombiniert werden können. 
  
 Sie können auf jede Hauptkomponente die gleichen Grundsätze wie auf das gesamte System anwenden. In einem großen Projekt kann jede Komponente über ein eigenes Anforderungsmodell verfügen. In kleineren Projekten kann ein Architekturmodell oder ein allgemeiner Entwurf erstellt werden, um die Hauptkomponenten und ihre Interaktionen zu zeigen. Weitere Informationen finden Sie unter [Modellieren der Architektur Ihrer app](../modeling/model-your-app-s-architecture.md).  
  
 In beiden Fällen können Sie eine Beziehung zwischen den Modellelementen und den Subsystemtests auf die gleiche Weise herstellen, wie Sie dies zwischen dem Anforderungsmodell und den Systemtests tun würden.  
  
### <a name="isolate-components-with-provided-and-required-interfaces"></a>Isolieren von Komponenten mit bereitgestellten und erforderlichen Schnittstellen  
 Es ist nützlich, alle Abhängigkeiten einer Komponente von anderen Teilen Ihres Systems oder von externen Diensten zu identifizieren und diese als erforderliche Schnittstellen darzustellen. Diese Übung führt normalerweise zu Umgestaltungen, durch die die Komponente deutlich entkoppelt wird und einfach vom Rest des Entwurfs getrennt werden kann.  
  
 Ein Vorteil dieser Entkopplung ist, dass die Komponente für die Tests ausgeführt werden kann, indem die normalerweise verwendeten Dienste durch Pseudoobjekte ersetzt werden. Dies sind Komponenten, die zu Testzwecken erstellt werden. Eine Pseudokomponente stellt die von Ihrer Komponente benötigte Schnittstelle bereit, und Abfragen werden mit simulierten Daten beantwortet. Die Pseudokomponenten sind einer vollständigen Testumgebung, die Sie mit allen Schnittstellen der Komponente verbinden können.  
  
 Ein Vorteil der Pseudotests besteht darin, dass Sie die Komponente entwickeln können, während sich die anderen Komponenten, deren Dienste sie verwenden wird, immer noch in der Entwicklungsphase befinden.  
  
## <a name="maintain-the-relationships-between-tests-and-model"></a>Beibehalten der Beziehungen zwischen Tests und Modell  
 Bei einem typischen Projekt, bei dem alle paar Wochen eine Iteration ausgeführt wird, wird am Anfang jeder Iteration eine Anforderungsüberprüfung durchgeführt. Dabei werden die Features besprochen, die in der nächsten Iteration bereitzustellen sind. Anhand eines Anforderungsmodells können die Konzepte, Szenarien und Sequenzen von Aktionen besprochen werden, die entwickelt werden. Die Projektbeteiligten legen Prioritäten fest, die Entwickler nehmen Schätzungen vor, und die Tester stellen sicher, dass das erwartete Verhalten jedes Features ordnungsgemäß erfasst wird.  
  
 Das Schreiben von Tests ist die effektivste Möglichkeit, eine Anforderung zu definieren, und es ist auch eine effektive Methode, um sicherzustellen, dass eine Person eine klare Vorstellung von den Anforderungen hat. Während jedoch das Schreiben von Tests zu lange dauert, um im Rahmen eines spezifikationsbezogenen Workshops vorgenommen zu werden, ist das Erstellen von Modellen sehr viel schneller möglich.  
  
 Aus Testsicht kann ein Anforderungsmodell als eine Kurzschreibweise für die Tests betrachtet werden. Folglich ist es wichtig, die Beziehung zwischen Tests und Modell über das gesamte Projekt hinweg aufrechtzuerhalten.  
  
##  <a name="Attaching"></a>Anfügen von Testsituationen an Modellelemente  
 Wenn das Projekt [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] verwendet, können Sie Tests mit den Elementen im Modell verknüpfen. Dadurch können Sie schnell die Tests finden, die von einer Änderung der Anforderungen betroffen sind, und nachverfolgen, in welchem Umfang eine Anforderung erfüllt wurde.  
  
 Sie können Tests mit allen Arten von Elementen verknüpfen. Hier einige Beispiele:  
  
-   Verknüpfen Sie einen Anwendungsfall mit den Tests, die ihn ausführen.  
  
-   Schreiben Sie die Klauseln einer Anwendungsfall-Nachbedingung oder eines Ziels in Kommentare, die mit dem Anwendungsfall verknüpft sind, und verknüpfen Sie dann Tests mit den einzelnen Kommentaren.  
  
-   Schreiben Sie invariante Regeln in Kommentare in Klassendiagrammen oder Aktivitätsdiagrammen, und verknüpfen Sie sie mit Tests.  
  
-   Verknüpfen Sie Tests mit einem Aktivitätsdiagramm oder mit einzelnen Aktivitäten.  
  
-   Verknüpfen Sie eine Testsammlung mit der Komponente oder dem Subsystem, die von ihr getestet werden.  
  
#### <a name="to-link-tests-to-a-model-element-or-relationship"></a>So verknüpfen Sie Tests mit einem Modellelement oder einer Beziehung  
  
1.  Erstellen Sie in [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] eine Anforderung, und lassen Sie eine Testsammlung auf dieser basieren. 
  
     Die von Ihnen erstellte Anforderung ist eine Arbeitsaufgabe in [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. In Abhängigkeit von der Prozessvorlage, die Ihr Projekt mit [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] verwendet, kann es sich um eine User Story-, Anforderungs- oder Anwendungsfall-Arbeitsaufgabe handeln. Weitere Informationen finden Sie unter [Nachverfolgen von Arbeit mit Visual Studio Team Services oder Team Foundation Server](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503).  
  
2.  Verknüpfen Sie die Anforderungsarbeitsaufgabe mit einem oder mehreren Elementen im Modell.  
  
     Klicken Sie in einem Modellierungsdiagramm mit der rechten Maustaste eine Element, Kommentar oder eine Beziehung, und klicken Sie dann auf **mit Arbeitsaufgabe verknüpfen**. Weitere Informationen finden Sie unter [Verknüpfen von Modellelementen und Arbeitsaufgaben](../modeling/link-model-elements-and-work-items.md).  
  
3.  Fügen Sie der Testsammlung Testfälle hinzu, die die im Modellelement ausgedrückte Anforderung überprüfen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Modellen für Ihre app](../modeling/create-models-for-your-app.md)   
 [Modellanforderungen](../modeling/model-user-requirements.md)   
 [Modellieren der Architektur Ihrer app](../modeling/model-your-app-s-architecture.md)   
 [Analysieren und Modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md)
