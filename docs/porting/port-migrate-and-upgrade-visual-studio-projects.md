---
title: "Übertragung, Migration und Upgrade der Visual Studio-Projekte | Microsoft-Dokumentation"
ms.custom: 
ms.date: 04/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
author: kraigb
ms.author: kraigb
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
ms.sourcegitcommit: bd2199e68bf23a191efe624da311dd11217028a8
ms.openlocfilehash: 77042a35175aa13d27ed31d1562198e800e065ae
ms.contentlocale: de-de
ms.lasthandoff: 05/15/2017

---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Übertragung, Migration und Upgrade der Visual Studio-Projekte

Jede neue Version von Visual Studio unterstützt im Allgemeinen die meisten vorherigen Typen von Projekten, Dateien und anderen Objekten. Sie können wie gewohnt mit ihnen arbeiten, vorausgesetzt, Sie sind nicht von neueren Features abhängig. Visual Studio behält die Abwärtskompatibilität mit vorherigen Versionen wie Visual Studio 2015, Visual Studio 2013 und Visual Studio 2012 bei. Informationen dazu, welche Features für welche Versionen spezifisch sind, finden Sie in den [Anmerkungen zu dieser Version](https://www.visualstudio.com/vs/release-notes/). Die Unterstützung für einige Typen ändert sich jedoch im Laufe der Zeit. Eine neuere Version von Visual Studio unterstützt möglicherweise bestimmte Typen nicht länger oder setzt voraus, dass sie so migriert und aktualisiert werden, sodass sie nicht länger abwärtskompatibel sind. Dieses Thema enthält Details zu betroffenen Projekttypen in Visual Studio 2017. Eine Liste der unterstützten Typen für Visual Studio 2017 finden Sie im Thema [Visual Studio 2017 – Zielplattformen und Kompatibilität](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs).

> [!Note]
> Zum Öffnen bestimmter Projekttypen benötigen Sie die erforderliche Workload durch den Visual Studio-Installer.


## <a name="projects"></a>Projekte

In der folgenden Liste wird die Unterstützung in Visual Studio 2017 für Projekte beschrieben, die in früheren Versionen erstellt wurden. Wenn ein Projekt oder Dateityp hier nicht angezeigt wird, den Sie eigentlich sehen sollten, gehen Sie unter [Portieren, Migrieren und Aktualisieren von Visual Studio-Projekten](https://msdn.microsoft.com/library/hh266747.aspx), und hinterlassen Sie einen Hinweis in den Kommentaren.

| Projekttyp | Unterstützung |
| --- | --- |
| .NET Core-Projekte (.xproj) | Mit Visual Studio 2015 erstellte Projekte nutzten die Preview-Tools, die eine XPROJ-Projektdatei enthalten. Wenn Sie eine XPROJ-Datei mit Visual Studio 2017 öffnen, werden Sie aufgefordert, die Datei ins CSPROJ-Format zu migrieren. Dabei wird eine Sicherung der XPROJ-Datei erstellt. Das CSPROJ-Format für .NET Core-Projekte wird in Visual Studio 2015 und früher nicht unterstützt.  Das XPROJ-Format wird in Visual Studio 2017 nur für die Migration zu .csproj unterstützt. Weitere Informationen finden Sie unter [Migrieren von .NET Core-Projekten in das .csproj-Format](https://docs.microsoft.com/dotnet/articles/core/migration/#visual-studio-2017).|
| ASP.NET-Webanwendung und ASP.NET Core-Webanwendung mit Application Insights aktiviert | Für jeden Visual Studio-Benutzer wird die Ressourceninformation pro Benutzerinstanz in der Registrierung gespeichert. Dies wird verwendet, wenn Benutzer kein Projekt geöffnet haben und Azure Application Insights-Daten durchsuchen möchten. Visual Studio 2015 verwendet andere Registrierungsorte als Visual Studio 2017 und führt so zu keinem Konflikt.<br/><br/>Sobald ein Benutzer eine ASP.NET-Webanwendung oder eine ASP.NET Core-Webanwendung erstellt, wird die Ressource in der SUO-Datei gespeichert. Der Benutzer kann das Projekt in Visual Studio 2015 oder 2017 öffnen. Die Ressourceninformation wird solange verwendet, wie Visual Studio Projekte unterstützt und wie Projektmappen in beiden Versionen verwendet werden. Benutzer müssen sich einmal für jedes Produkt authentifizieren. Wenn z.B. ein Projekt mit Visual Studio 2015 erstellt und in Visual Studio 2017 geöffnet wird, muss sich der Benutzer für Visual Studio 2017 authentifizieren. |
| C#/Visual Basic Webform oder Windows Form | Sie können das Projekt in Visual Studio 2017 und Visual Studio 2015 öffnen. |
| Datenbankkomponententest-Projekte (.csproj, .vbproj)    | Ältere Dateneinheit-Testprojekte werden in Visual Studio 2017 geladen, verwenden jedoch die GAC-Version der Abhängigkeiten. Um das Komponententestprojekt upzugraden, um die neuesten Abhängigkeiten zu verwenden, klicken Sie mit der rechten Maustaste auf das Projekt im Projektmappen-Explorer, und wählen Sie **In SQL Server-Komponententestprojekt konvertieren...** aus. |
| F# | Visual Studio 2017 kann Projekte öffnen, die in Visual Studio 2013 und 2015 erstellt wurden. Um jedoch Visual Studio 2017-Features in diesen Projekten zu aktivieren, öffnen Sie die Projekteigenschaften, und ändern Sie das Ziel „fsharp.core“ zu „F# 4.1“. Beachten Sie auch, dass die **Sprachunterstützung für F#** im Visual Studio-Installationsprogramm für .NET-Arbeitsauslastungen nicht standardmäßig ausgewählt ist. Sie müssen diese Option für jede Arbeitslast oder unter **Entwicklungsaktivitäten** auf der Registerkarte **Einzelne Komponenten** auswählen. |
| InstallShield<br/>MSI-Setup | In Visual Studio 2010 erstellte Installer-Projekte können mithilfe der [Visual Studio Installer Projects-Erweiterung](https://marketplace.visualstudio.com/items?itemName=UnniRavindranathan-MSFT.MicrosoftVisualStudio2013InstallerProjects) in höheren Versionen geöffnet werden. Sie können solche Projekte auch mit der [InstallShield Limited Edition](https://blogs.msdn.microsoft.com/visualstudio/2013/08/15/whats-new-in-visual-studio-2013-and-installshield-limited-edition/) beibehalten. |
| LightSwitch | LightSwitch wird in Visual Studio 2017 nicht mehr unterstützt. Projekte, die mit Visual Studio 2012 und früher erstellt und in Visual Studio 2013 oder 2015 geöffnet wurden, erhalten ein Upgrade und können von da an nur in Visual Studio 2013 oder Visual Studio 2015 geöffnet werden. |
| Microsoft Azure-Tools für Visual Studio | Um diese Projekttypen zu öffnen, müssen Sie zunächst das [Azure SDK für .NET](http://azure.microsoft.com/downloads/)installieren. Danach können Sie das Projekt öffnen. Ihr Projekt wird aktualisiert, falls dies erforderlich ist. |
| Model View Controller-Framework (ASP.NET MVC) | Unterstützung für MVC-Versionen und Visual Studio:<ul><li>Visual Studio 2010 SP1 unterstützt MVC 2 und MVC 3. Die MVC 4-Unterstützung wird durch den [Download von ASP.NET 4 MVC 4 für Visual Studio 2010 SP1](https://www.microsoft.com/download/details.aspx?id=30683) hinzugefügt.</li><li>Visual Studio 2012 unterstützt nur MVC 3 und MVC 4</li><li>Visual Studio 2013 unterstützt nur MVC 4 und MVC 5</li><li>Visual Studio 2017 und Visual Studio 2015 unterstützen MVC 4 (Sie können vorhandene Projekte öffnen, jedoch keine neuen erstellen) und MVC 5</li></ul><br/><br/>Upgraden der MVC-Versionen:<ul><li>Informationen über das automatische Upgrade von MVC 2 auf MCV 3 finden Sie unter [ASP.NET MVC 3-Anwendung Upgrader](http://go.microsoft.com/fwlink/?LinkID=238178).</li><li>Informationen über das manuelle Upgrade von MVC 2 auf MVC 3 finden Sie unter [Aktualisieren eines ASP.NET MVC 2-Projekts zum ASP.NET MVC 3-Tool-Update](http://go.microsoft.com/fwlink/?linkid=238178).</li><li>Informationen über das manuelle Upgrade von MVC3 auf MVC 4 finden Sie unter [Aktualisieren eines ASP.NET MVC 3-Projekts zu ASP.NET MVC 4](http://www.asp.net/whitepapers/mvc4-release-notes). Wenn das Projekt .NET Framework 3.5 SP1 verwendet, müssen Sie es auf .NET Framework 4. umleiten.</li><li>Informationen über das manuelle Upgrade von MVC 4 auf MVC 5 finden Sie unter [How to Upgrade an ASP.NET MVC 4 and Web API Project to ASP.NET MVC 5 and Web API 2 (Vorgehensweise: Upgraden eines ASP.NET MVC 4- und Web-API-Projekts zu ASP.NET MVC 5 und Web-API 2)](https://www.asp.net/mvc/overview/releases/how-to-upgrade-an-aspnet-mvc-4-and-web-api-project-to-aspnet-mvc-5-and-web-api-2).</li></ul> |
| Modellierung | Wenn Sie zulassen, dass Visual Studio das Projekt automatisch aktualisiert, können Sie es in Visual Studio 2015, Visual Studio 2013 oder Visual Studio 2012 öffnen.<br/><br/>Das Format des Modellierungsprojekts hat sich zwischen Visual Studio 2015 und Visual Studio 2017 nicht verändert. Das Projekt kann in beiden Versionen geöffnet und verändert werden. Es gibt jedoch Unterschiede im Verhalten in Visual Studio 2017:<ul><li>Modellierungsprojekte werden jetzt in den Menüs und Vorlagen als „Abhängigkeitsüberprüfungsprojekte“ bezeichnet.</li><li>UML-Diagramme werden in Visual Studio 2017 nicht mehr unterstützt. UML-Dateien sind wie zuvor im Projektmappen-Explorer aufgelistet, werden jedoch als XML-Dateien geöffnet. Verwenden Sie Visual Studio 2015, um UML-Diagramme anzuzeigen, zu erstellen oder zu bearbeiten.</li><li>In Visual Studio 2017 wird die Überprüfung der Architekturabhängigkeiten nicht länger durchgeführt, wenn das Modellierungsprojekt erstellt wird. Stattdessen wird die Überprüfung ausgeführt, wenn jedes Codeprojekt erstellt wird. Diese Änderung wirkt sich nicht auf das Modellierungsprojekt aus, es erfordert jedoch, dass die Änderungen an den Codeprojekten überprüft werden. Visual Studio 2017 kann automatisch die nötigen Änderungen an den Codeprojekten vornehmen ([weitere Informationen](http://go.microsoft.com/fwlink/?LinkId=827800)).</li></ul> |
| MSI-Setup (.vdproj) | Siehe InstallShield-Projekte oben. | 
| Office 2007 VSTO | Ein unidirektionales Upgrade für Visual Studio 2017 ist erforderlich. |
| Office 2010 VSTO | Wenn das Projekt auf .NET Framework 4 abzielt, können Sie es in Visual Studio 2010 SP1 und höher öffnen. Alle anderen Projekte erfordern ein unidirektionales Upgrade. |
| SharePoint 2010 | Wenn ein SharePoint-Projektmappenprojekt mit Visual Studio 2017 geöffnet wird, wird es entweder auf SharePoint 2013 oder SharePoint 2016 aktualisiert. Die Arbeitsauslastung „.NET-Desktopentwicklung“ muss für das Upgrade in Visual Studio 2017 installiert werden.<br/><br/>Weitere Informationen zum Aktualisieren von SharePoint-Projekten finden Sie unter [Upgrade auf SharePoint 2013](https://technet.microsoft.com/library/cc303420.aspx), [Aktualisieren von Workflows in SharePoint Server 2013](https://technet.microsoft.com/library/dn133867.aspx) und [Erstellen einer SharePoint 2016-Farm für ein Upgrade einer Datenbankanfügung](https://technet.microsoft.com/library/cc263026(v=office.16).aspx). |
| SharePoint 2016 | In Office Developer Tools Preview 2 erstellte SharePoint-Add-In-Projekte können nicht in Visual Studio 2017 geöffnet werden. Um dieses Problem zu umgehen, müssen Sie in der `.csproj`- oder `.vbproj`-Datei `MinimumVisualStudioVersion` auf 12.0 und `MinimumOfficeToolsVersion` auf 12.2 aktualisieren. |
| Silverlight | Silverlight-Projekte werden in Visual Studio 2017 nicht unterstützt. Um Silverlight-Anwendungen zu verwalten, verwenden Sie weiterhin Visual Studio 2015. |
| SQL Server Reporting Services, SQL Server Analysis Services (SSDT, SSAS, MSAS, SSDT) | Unterstützung für diese Projekttypen wird über zwei Erweiterungen in der Visual Studio Gallery bereitgestellt: [Microsoft Analysis Services-Modellierungsprojekte](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects) und [Microsoft-Berichtsprojekte für Visual Studio](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio). |
| Visual C++ | Sie können Visual Studio 2017 verwenden, um Projektmappen und Projekte zu öffnen, die unverändert in Visual Studio 2015 erstellt wurden. Projekte, die in älteren Versionen von Visual Studio erstellt wurden, benötigen möglicherweise ein Upgrade des Projekts oder die Neuausrichtung an ein neueres Toolset zum Erstellen mit Visual Studio 2017. Weitere Informationen finden Sie unter [Visual C++-Handbuch: Portieren und Aktualisieren](https://docs.microsoft.com/cpp/porting/visual-cpp-porting-and-upgrading-guide). |
| Visual Studio-Erweiterbarkeit/VSIX | Projekte mit dem Element MinimumVersion 14.0 oder weniger werden aktualisiert, um das Element MinimumVersion 15.0 zu deklarieren. Dadurch wird verhindert, dass das Projekt in früheren Versionen von Visual Studio geöffnet werden kann. Damit Sie ein Projekt in früheren Versionen öffnen können, legen Sie MinimumVersion auf `$(VisualStudioVersion)` fest. Weitere Informationen finden Sie unter [Vorgehensweise: Migrieren von Erweiterungsprojekten zu Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md). |
| Visual Studio Lab Management | Sie können Microsoft Test Manager oder Visual Studio 2010 SP1 und höher verwenden, Umgebungen zu öffnen, die in einer dieser Versionen erstellt wurden. Allerdings muss die Version für Visual Studio 2010 SP1 von Microsoft Test Manager mit der Version von Team Foundation Server übereinstimmen, bevor Sie Umgebungen erstellen können. |
| Visual Studio-Tools für Apache Cordova |Dieses Projekt kann in Visual Studio 2017 geöffnet werden, es ist jedoch nicht abwärtskompatibel. Beim Öffnen eines Projekts von Visual Studio 2015 werden Sie aufgefordert, Änderungen an Ihrem Projekt zuzulassen. Dadurch erhält das Projekt ein Upgrade, damit es Toolsets statt einer `taco.json`-Datei verwenden kann, um die Versionskontrolle der Cordova-Bibliothek, die Plattformen und Plug-Ins sowie den Knoten / die NPM-Abhängigkeiten zu verwalten. Weitere Informationen finden Sie im [Migrationshandbuch](https://docs.microsoft.com/visualstudio/cross-platform/tools-for-cordova/first-steps/migrate-from-visual-studio-2015). |
| Windows Communication Foundation und Windows Workflow Foundation | Sie können dieses Projekt in Visual Studio 2017, Visual Studio 2015, Visual Studio 2013 und Visual Studio 2012 öffnen. |
| Windows Presentation Foundation | Sie können dieses Projekt in Visual Studio 2013, Visual Studio 2012 und Visual Studio 2010 SP1 öffnen. |
| Windows Store/Phone-Apps | Projekte für Windows Store 8.1 und 8.0 sowie für Windows Phone 8.1 und 8.0 werden in Visual Studio 2017 nicht unterstützt. Um diese Apps zu verwalten, verwenden Sie weiterhin Visual Studio 2015. Zum Verwalten von Windows Phone 7.x-Projekten verwenden Sie Visual Studio 2012. |
