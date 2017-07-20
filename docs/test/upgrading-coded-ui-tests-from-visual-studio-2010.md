---
title: Upgrade der Tests der programmierten UI von Visual Studio 2010 | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11232a83-73ea-46bd-bc0c-46f74f6e3a42
caps.latest.revision: 33
ms.author: douge
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: d3936d44f8591753df102cf65c15d9199a679316
ms.contentlocale: de-de
ms.lasthandoff: 05/13/2017

---
# <a name="upgrading-coded-ui-tests-from-visual-studio-2010"></a>Upgrade der Tests der programmierten UI von Visual Studio 2010
Tests der programmierten UI enthaltende Testprojekte, die in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] erstellt wurden, werden unbeaufsichtigt repariert, wenn sie in Visual Studio 2012 geöffnet werden. Wenn Testprojekte in das Quellsteuerelement eingecheckt werden, werden die Projektdateien für diese Reparatur ausgecheckt. Nach der Reparatur können die Tests der programmierten UI enthaltende Testprojekte sowohl in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 als auch in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]verwendet werden.  
  
 **Anforderungen**  
  
-   Visual Studio Enterprise  
  
> [!NOTE]
>  Visual Studio enthält mehr als ein Typ des Testprojekts. Wenn Sie einen neuen Test der programmierten UI erstellen, wird er in einem Projekttyp für den Test der programmierten UI erstellt. Weitere Informationen finden Sie unter [Upgrade der Tests von früheren Visual Studio-Versionen](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).  
  
> [!WARNING]
> Tests der programmierten UI enthaltende [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] -Testprojekte müssen neu erstellt werden, wenn Sie das Testprojekt in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] oder [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] oder zusammen mit [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]öffnen.  
  
> [!WARNING]
>  Wenn ein in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] erstelltes Testprojekt, das nur Komponententests enthält, in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]geöffnet wird, ist es nicht möglich, Tests der programmierten UI hinzuzufügen. Auf ähnliche Weise können Sie einem in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]erstellten Komponententestprojekt keinen Test der programmierten UI hinzufügen.  
  
## <a name="compatibility-issues-between-visual-studio-2010-and-visual-studio-2012"></a>Kompatibilitätsprobleme mit Visual Studio 2010 und Visual Studio 2012  
 In der folgenden Tabelle werden Probleme aufgeführt, die beim Migrieren von Tests der programmierten UI zwischen [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] und [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]beachtet werden sollten.  
  
> [!CAUTION]
>  Es ist ein bekanntes Problem, dass Verweise in Projekten für Tests der programmierten UI im Projektmappen-Explorer nicht angezeigt werden. Weitere Informationen finden Sie in der auf den [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] -Installationsmedien enthaltenen Infodatei.  
  
|Funktionalität der programmierten UI|Problem|Lösung|  
|----------------------------|-----------|--------------|  
|Testen der Benutzeroberfläche von Silverlight wird in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]nicht unterstützt.|**Fehlerhafter Build.**<br /><br /> Wenn Sie über [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Feature Pack 2 verfügen und Projekte für den Test der programmierten UI für Silverlight-Anwendungen erstellt haben, können diese Projekte in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]nicht geöffnet werden.|Es wird empfohlen, dass Sie diese Projekte nur in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Feature Pack 2 verwalten.|  
|Testen der Benutzeroberfläche von Firefox wird in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]nicht unterstützt.|**Build wurde erfolgreich erstellt, fehlerhafter Testlauf**<br /><br /> Wenn Sie über [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Feature Pack 2 verfügen und Projekte für den Test der programmierten UI für Webanwendungen in Firefox erstellt haben, können diese Projekte in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]nicht geöffnet werden.|Es wird empfohlen, dass Sie diese Projekte nur in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Feature Pack 2 verwalten.|  
|Neue APIs zum Testen des Benutzeroberflächencodes wurden in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]hinzugefügt.|**Fehlerhafter Build.**<br /><br /> Wenn Sie Tests der programmierten UI mithilfe der neuen API zum Testen der Benutzeroberfläche in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]erstellen, können diese Projekte in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]nicht geöffnet werden.|Projekte mit der neuen API sollten nur in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] verwaltet werden.|  
|In [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] wurden Verweise innerhalb einer „Choose“-Anweisung in der CSPROJ-Datei hinzugefügt. In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]verwenden wir eine Feedbackzieldatei zum Einbeziehen der Assemblyverweise für Tests der programmierten UI.|In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]kann einem in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] (oder SP1) erstellten Testprojekt kein Test der programmierten UI hinzugefügt werden, der keinen Test der programmierten UI enthielt.<br /><br /> Der Reparaturvorgang fügt die Zieldatei und die „Choose“-Anweisung hinzu. Wenn sich ein Test der programmierten UI nicht im Testprojekt befindet, wird das Projekt als repariert markiert, und die entsprechenden Verweise werden nicht hinzugefügt, wenn der Test der programmierten UI in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]hinzugefügt wird.|Sie müssen mithilfe von [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] ein neues Testprojekt in derselben Projektmappe erstellen und Ihren neuen Test der programmierten UI darin hinzufügen. Alternativ können Sie Tests der programmierten UI in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 hinzufügen und dieses Projekt in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]öffnen.|  
  
##  <a name="UpgradingCodedUIFromVS2010_Update"></a> Visual Studio 2010 SP1 Update  
 Ein Update für [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] SP1 mit Kompatibilitätsunterstützung für Visual Studio 2012 und Windows 8 steht als Download im [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=34677) und als Visual Studio-Update bereit.  
  
 Nach dem Anwenden des Updates werden die folgenden [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] SP1-Toolfeatures für den Test der programmierten UI für Windows 8 verbessert:  
  
-   Sie können einen Test der programmierten UI für die Microsoft .NET Framework 4.5-basierten Windows Presentation Foundation-Steuerelemente (WPF) auf einem Computer unter Windows 8 ausführen.  
  
-   Sie können einen Test der programmierten UI für Internet Explorer 10 (64 Bit, x64) auf einem Computer unter Windows 8 ausführen.  
  
 Das Update enthält zudem Fixes für die folgenden Probleme:  
  
-   **Codeabdeckung:** Unfähigkeit eine durch Visual Studio 2012 in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] SP1 erstellte Codeabdeckungsdatei (.coverage) zu öffnen.  
  
-   **Isolierte Testartefakte:** Ihr Team verfügt über ein Testartefakt, das in TFS 2010 (Team Foundation Server) einem ungültigen Benutzer zugewiesen ist. Dies ist beispielsweise der Fall, wenn ein Benutzer das Unternehmen verlassen hat, diesem jedoch weiterhin ein Testfall zugewiesen ist. Sie aktualisieren TFS 2010 auf TFS 2012. Sie verwenden [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 2010, um eine Verbindung zum aktualisierten TFS-Server herzustellen. Sie können das Testartefakt mithilfe von [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 2010 anderen TFS-Benutzern nicht zuweisen.  
  
-   **Auslastungstest:** Wenn Sie einen Auslastungstest zusammen mit einem Netzwerktyp ausführen, der nicht dem LAN-Profil auf einem Computer unter Windows 8 entspricht, führt der Netzwerkemulatortreiber dazu, dass das Betriebssystem abstürzt. Weitere Informationen finden Sie unter [KB-Artikel 2736182](http://support.microsoft.com/kb/2736182).  
  
## <a name="see-also"></a>Siehe auch  
 [Portieren, Migrieren und Upgraden von Visual Studio-Projekten](../porting/port-migrate-and-upgrade-visual-studio-projects.md)   
 [Upgrading Tests from Earlier Versions of Visual Studio (Upgrade der Tests von früheren Visual Studio-Versionen)](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)   
 [Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)   
 [Generieren eines Tests der programmierten UI aus einer vorhandenen Aktionsaufzeichnung](/devops-test-docs/test/generating-a-coded-ui-test-from-an-existing-action-recording)   
 [Unterstützte Konfigurationen und Plattformen für Tests der programmierten UI und Aktionsaufzeichnungen](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
