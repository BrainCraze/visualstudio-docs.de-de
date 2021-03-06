---
title: VSPackage-Setupszenarien | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b58400330bb2032354d28a7b76729a5d7f85fd3c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="vspackage-setup-scenarios"></a>VSPackage-Setup-Szenarien

Es ist wichtig, um Ihr VSPackage-Installationsprogramm für Flexibilität zu entwerfen. Beispielsweise müssen Sie möglicherweise einen Sicherheitspatch in der Zukunft freigeben oder eine Business-Strategie, die umfassend Seite-an-Seite-versionsunterstützung erfordert unter Umständen ändern.

In [unterstützen mehrere Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), informieren Sie sich über die Vorteile und die Probleme unterstützen Seite-an-Seite-Installationen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mit freigegebenen oder Seite-an-Seite-Installationen von Ihr VSPackage. Kurz gesagt, VSPackages Seite-an-Seite bieten Ihnen die größte Flexibilität zur Unterstützung neuer Features des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

In diesem Thema beschriebenen Szenarien sind nicht nur die Optionen, aber sie als empfohlene bewährte Verfahrensweisen dargestellt sind.

## <a name="components-privacy-and-sharing"></a>Komponenten, Datenschutz und Freigabe

### <a name="make-your-components-independent"></a>Stellen Sie Ihre Komponenten unabhängig

Nachdem Sie identifizieren, und füllen eine Komponente, weisen eine `GUID`, und stellen Sie die Komponente, die Zusammensetzung kann nicht geändert werden. Wenn Sie eine Komponente Komposition ändern, muss die resultierende Komponente eine neue Komponente einer neuen `GUID`. Angesichts dieser Fakten, ist die größte Flexibilität für die versionsverwaltung Authentifizierungsprozesses, indem Sie die Verfügbarkeit der Komponente unabhängige, Dank à. Weitere Informationen zu Regeln, die Komponenten, finden Sie unter [ändern die Komponentencode](http://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) und [was geschieht, wenn die Komponente Regeln sind aufgeteilt?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Mischen Sie freigegebene und private Ressourcen in einer Komponente keine

Verweiszählung tritt auf, auf der Komponentenebene. Daher ist das Mischen von freigegebenen und privaten Ressourcen in einer Komponente es unmöglich, private Ressourcen, z. B. eine ausführbare Datei zu aktualisieren, ohne freigegebene Ressourcen auch überschreiben. Dieses Szenario Abwärtskompatibilität Probleme erstellt und von der Erstellung von Seite-an-Seite-Funktion beschränkt.

Beispielsweise verwendet die Registrierungswerte so registrieren Ihr VSPackage mit der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] sollte in einer Komponente aus einem verwendet, um Ihr VSPackage mit Visual Studio registrieren getrennt gehalten werden. Freigegebene Dateien oder Registrierungswerte wechseln Sie in noch eine andere Komponente.

## <a name="scenario-1-shared-vspackage"></a>Szenario 1: Freigegebene VSPackage

In diesem Szenario wird ein freigegebener VSPackage (einem einzelnen Binärwert, der mehrere Versionen von Visual Studio unterstützt wird in einem Windows Installer-Paket ausgeliefert. Mit jeder Version von Visual Studio registrieren, wird von auswählbaren Features gesteuert. Es bedeutet auch, dass wenn zugewiesen, um Funktionen zu trennen, jede Komponente für die Installation oder Deinstallation, platzieren den Benutzer Kontrolle über das VSPackage in verschiedenen Versionen der Integration kann einzeln ausgewählt werden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. (Siehe [Features von Windows Installer](http://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) für Weitere Informationen zur Verwendung von Funktionen in Windows Installer-Pakete.)

![VS freigegebenem Installer](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Wie in der Abbildung gezeigt, erfolgen freigegebene Komponenten Teil der Feat_Common-Funktion, die immer installiert wird. Durch die Funktionen Feat_VS2002 und Feat_VS2003 sichtbar gemacht wird, können Benutzer zum Zeitpunkt der Installation wählen, in welche Versionen von Visual Studio sie das VSPackage, um integrieren möchten. Benutzer können auch Windows Installer-Wartungsmodus hinzufügen oder Entfernen von Funktionen, die in diesem Fall wird hinzugefügt oder entfernt die VSPackage-Registrierungsinformationen aus verschiedenen Versionen von Visual Studio.

> [!NOTE]
> Eine Funktion Anzeigespalte auf 0 festlegen blendet es aus. Ein niedrige Ebene Spaltenwert, z. B. 1, wird sichergestellt, dass es immer installiert wird. Weitere Informationen finden Sie unter [INSTALLLEVEL Eigenschaft](http://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) und [Funktionstabelle](http://msdn.microsoft.com/library/aa368585.aspx).

## <a name="scenario-2-shared-vspackage-update"></a>Szenario 2: Freigegebene VSPackage-Update

In diesem Szenario wird eine aktualisierte Version des VSPackage-Installationsprogramms in Szenario 1 geliefert. In Diskussion das Update bietet Unterstützung für Visual Studio, aber es kann auch ein einfacher Sicherheitspatch werden oder Fehlerkorrektur Servicepack. Windows Installer Regeln für die Installation neuer Komponenten erfordern, dass unverändert Komponenten bereits auf dem System nicht kopiert werden. In diesem Fall ein System mit Version 1.0, die bereits vorhanden, überschreibt die aktualisierte Komponente Comp_MyVSPackage.dll und Benutzer entscheiden lassen möchten, um das neue Feature Feat_VS2005 mit zugehörigen Comp_VS2005_Reg-Komponente hinzuzufügen.

> [!CAUTION]
> Wenn eine VSPackage für mehrere Versionen eines freigegeben ist [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], es ist wichtig, dass die nachfolgende Versionen des VSPackage Abwärtskompatibilität mit früheren Versionen von Visual Studio zu gewährleisten. Bei der Abwärtskompatibilität beibehalten werden kann, müssen Sie die Seite-an-Seite, private VSPackages verwenden. Weitere Informationen finden Sie unter [unterstützen mehrere Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![VS freigegebene VS-Paket Updateinstallationsprogramm](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Dieses Szenario stellt ein neues VSPackage-Installationsprogramm, profitieren von Windows Installer Unterstützung für kleinere Upgrades. Benutzer installieren einfach Version 1.1, und es wird die Version 1.0 aktualisiert. Allerdings ist es nicht notwendig, dass Version 1.0 auf dem System ist. Das gleiche Installationsprogramm installiert Version 1.1 auf einem System, Version 1.0. Der Vorteil, dass kleinere Upgrades auf diese Weise bereitgestellt wird, dass es nicht notwendig, die Arbeit der Entwicklung einer Aktualisierung Installationsprogramm und eine Vollversion durchlaufen. Ein Installer führt beide Aufträge. Eine Sicherheits-Updates oder Service pack kommt es möglicherweise stattdessen nutzen Windows Installer-Patches. Weitere Informationen finden Sie unter [Patchen und Upgrades](http://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).

## <a name="scenario-3-side-by-side-vspackage"></a>Szenario 3: Seite-an-Seite-VSPackage

Dieses Szenario zeigt zwei VSPackage Installationsprogramme – einer für jede Version von Visual Studio .NET 2003 und Visual Studio. Installationsprogramme für die Installation einer Seite-an-Seite oder "Privat", "VSPackage (derjenige, der speziell erstellt und für eine bestimmte Version von Visual Studio installiert wird). Jedes VSPackage wird in eine eigene Komponente. Folglich jeder kann einzeln verwaltet werden mit Patches oder einer Wartung frei. Da die VSPackage-DLL jetzt versionsspezifische ist, ist es sicher ist, die Registrierungsinformationen in der gleichen Komponente als DLL enthalten.

![VS-Seite-an-Seite-VS-Paket-Installationsprogramm](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Jede Installer enthält auch Code, der die zwei Installationsprogramme gemeinsam verwendet werden. Wenn der gemeinsam verwendeten Code an einem Standort installiert ist, installiert installieren beide MSI-Dateien den gemeinsam verwendeten Code nur einmal. Der zweite Installer inkrementiert nur einen Verweiszähler für die Komponente. Der Verweiszähler wird sichergestellt, wenn eines der VSPackages deinstalliert wird, der gemeinsam verwendeten Code für die anderen VSPackage bleiben. Wenn das zweite VSPackage ebenfalls deinstalliert wird, wird der gemeinsam verwendeten Code entfernt.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Szenario 4: Seite-an-Seite VSPackage-Update

In diesem Szenario das VSPackage für Visual Studio aus eine Sicherheitslücke ist, und müssen Sie ein Update. Wie in Szenario 2 können Sie eine neue MSI-Datei erstellen, die aktualisiert eine vorhandene Installation um enthalten die Korrektur Sicherheit als auch bereitstellen Neuinstallationen Security Update bereits vorhanden.

In diesem Fall ist das VSPackage ein verwaltetes VSPackage im globalen Assemblycache (GAC) installiert. Wenn Sie es, um die Sicherheit Korrektur einzuschließen neu erstellen, müssen Sie die Anzahl Überarbeitungsteil der Versionsnummer der Assembly ändern. Die Registrierungsinformationen für die neue Versionsnummer der Assembly die vorherige Version überschrieben, wodurch [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zum Laden der Assembly festen.

![VS-parallelem VS Paket Updateinstallationsprogramm](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Weitere Informationen zur Bereitstellung von Seite-an-Seite-Assemblys finden Sie unter [Bereitstellung vereinfachen und Behebung von DLL schwerwiegende mit .NET Framework](http://msdn.microsoft.com/library/ms973843.aspx).

## <a name="see-also"></a>Siehe auch

[Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)  
[Unterstützen mehrerer Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)