---
title: "Standardmäßige und benutzerdefinierte Toolsetkonfigurationen | Microsoft-Dokumentation"
ms.custom: 
ms.date: 01/31/2018
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 19e01346c8af84faad2ac1877091a395db3fd3ce
ms.sourcegitcommit: f219ef323b8e1c9b61f2bfd4d3fad7e3d5fb3561
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="standard-and-custom-toolset-configurations"></a>Standardmäßige und benutzerdefinierte Toolsetkonfigurationen
Ein MSBuild-Toolset enthält Verweise auf Aufgaben, Zielen und Tools, die Sie verwenden können, um ein Anwendungsprojekt zu erstellen. MSBuild umfasst ein Standardtoolset, Sie können jedoch auch benutzerdefinierte Toolsets erstellen. Informationen zum Angeben eines Toolsets finden Sie unter [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).  
  
## <a name="standard-toolset-configurations"></a>Standard-Toolsetkonfigurationen  
 MSBuild 15.0 umfasst die folgenden Standardtoolsets:  
  
|ToolsVersion|Toolsetpfad (wie in der MSBuildToolsPath- oder MSBuildBinPath-Eigenschaft des Builds angegeben)|  
|------------------|--------------------------------------------------------------------------------------------|  
|2.0|*Windows-Installationspfad*\Microsoft.Net\Framework\v2.0.50727\|  
|3.5|*Windows-Installationspfad*\Microsoft.NET\Framework\v3.5\|  
|4.0|*Windows-Installationspfad*\Microsoft.NET\Framework\v4.0.30319\|  
|15.0|*Visual Studio-Installationspfad*\MSBuild\15.0\bin|  
  
 Der `ToolsVersion`-Wert bestimmt, welches Toolset von einem Projekt verwendet wird, das von Visual Studio generiert wird. In Visual Studio 2017 ist der Standardwert unabhängig von der in der Projektdatei angegebenen Version immer „15.0“. Sie können dieses Attribut jedoch mit der Option **/toolsversion** in einer Eingabeaufforderung überschreiben. Weitere Informationen über dieses Attribut und andere Methoden, `ToolsVersion` anzugeben, finden Sie unter [Überschreiben von ToolsVersion-Einstellungen](../msbuild/overriding-toolsversion-settings.md).  
  
 Visual Studio 2017 verwendet keinen Registrierungsschlüssel für den Pfad zu MSBuild. In den MSBuild-Versionen vor Version 15.0, die zusammen mit Visual Studio 2017 installiert werden, geben die folgenden Registrierungsschlüssel den Installationspfad von „MSBuild.exe“ an.  
  
|-Registrierungsschlüssel|Schlüsselname|Zeichenfolgen-Schlüsselwert|  
|------------------|--------------|----------------------|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\2.0\|MSBuildToolsPath|.NET Framework 2.0-Installationspfad|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\|MSBuildToolsPath|.NET Framework 3.5-Installationspfad|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\|MSBuildToolsPath|.NET Framework 4-Installationspfad|  
  
### <a name="sub-toolsets"></a>Unter-Toolsets  
 Wenn der Registrierungsschlüssel in der vorherigen Tabelle über einen Unterschlüssel verfügt, verwendet MSBuild diesen, um den Pfad eines Untertoolsets zu bestimmen, der den Pfad im übergeordneten Toolset überschreibt. Der folgende Unterschlüssel ist ein Beispiel:  
  
 \HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0  
  
 Falls Eigenschaften sowohl im Basistoolset als auch in den ausgewählten Unter-Toolsets definiert sind, werden die Eigenschaftendefinitionen im Unter-Toolset verwendet. Beispielsweise definiert das Toolset MSBuild 4.0 `SDK40ToolsPath` so, dass es auf das 7.0A SDK verweist, aber das Toolset MSBuild 4.0\11.0 definiert die gleiche Eigenschaft so, dass sie auf das 8.0A SDK verweist. Wenn `VisualStudioVersion` nicht festgelegt ist, verweist `SDK40ToolsPath` auf 7.0A, aber wenn `VisualStudioVersion` auf 11.0 festgelegt ist, verweist die Eigenschaft stattdessen auf 8.0A.  
  
 Die `VisualStudioVersion`-Buildeigenschaft gibt an, ob ein Unter-Toolset aktiv wird. Beispielsweise gibt der `VisualStudioVersion`-Wert "12.0" das MSBuild 12.0-Unter-Toolset an. Weitere Informationen finden Sie im Abschnitt zu Unter-Toolsets unter [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).  
  
> [!NOTE]
>  Es wird empfohlen, diese Einstellungen nicht zu ändern. Sie können jedoch auch eigene Einstellungen hinzufügen und computerübergreifende benutzerdefinierte Toolsetdefinitionen festlegen, wie im nächsten Abschnitt beschrieben.  
  
## <a name="custom-toolset-definitions"></a>Benutzerdefinierte Toolsetdefinitionen  
 Wenn ein Standardtoolset die Buildanforderungen nicht erfüllt, können Sie ein benutzerdefiniertes Toolset erstellen. Angenommen, Sie haben ein Buildlaborszenario, in dem Sie ein eigenes System zum Erstellen von [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]-Projekten benötigen. Mit einem benutzerdefinierten Toolset können Sie dem `ToolsVersion`-Attribut beim Erstellen von Projekten oder Ausführen von „MSBuild.exe“ benutzerdefinierte Werte zuweisen. Auf diese Weise können Sie die `$(MSBuildToolsPath)`-Eigenschaft verwenden, um TARGETS-Dateien von diesem Verzeichnis zu importieren, sowie benutzerdefinierte Toolseteigenschaften definieren, die für jedes Projekt verwendet werden können, das dieses Toolset verwendet.  
  
 Geben Sie ein benutzerdefiniertes Toolset in der Konfigurationsdatei für MSBuild.exe an (oder für das benutzerdefinierte Tool, das die MSBuild-Engine hostet, wenn dies bei Ihnen zutrifft). Beispielsweise kann die Konfigurationsdatei für „MSBuild.exe“ die folgende Toolsetdefinition enthalten, wenn Sie das Standardverhalten von ToolsVersion 15.0 überschreiben möchten.  
  
```xml  
<msbuildToolsets default="15.0">  
   <toolset toolsVersion="15.0">  
      <property name="MSBuildToolsPath"   
        value="C:\SpecialPath" />  
   </toolset>  
</msbuildToolsets>  
```  
  
 `<msbuildToolsets>` muss auch wie folgt in der Konfigurationsdatei definiert werden.  
  
```xml  
<configSections>  
   <section name="msbuildToolsets"         
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,   
       Microsoft.Build.Engine, Version=15.1.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a"  
   </section>  
</configSections>  
```  
  
> [!NOTE]
>  Richtig gelesen ist `<configSections>` der erste Unterabschnitt im Abschnitt `<configuration>`.  
  
 `ToolsetConfigurationSection` ist ein benutzerdefinierter Konfigurationsabschnitt, der von jedem MSBuild-Host für die benutzerdefinierte Konfiguration verwendet werden kann. Wenn Sie ein benutzerdefiniertes Toolset verwenden, muss ein Host keine Aktionen durchführen, um das Buildmodul zu initialisieren, sondern nur die Einträge in der Konfigurationsdatei zur Verfügung stellen. Indem Sie Einträge in der Registrierung definieren, können Sie computerübergreifende Toolsets angeben, die für MSBuild.exe, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und alle Hosts von MSBuild angewendet werden können.  
  
> [!NOTE]
>  Wenn in einer Konfigurationsdatei die Einstellungen für eine `ToolsVersion` definiert werden, die bereits in der Registrierung definiert ist, werden diese beiden Definitionen nicht zusammengeführt. Die Definition in der Konfigurationsdatei hat Priorität, und die Einstellungen in der Registrierung für diese `ToolsVersion` werden ignoriert.  
  
 Die folgenden Eigenschaften sind für den Wert der `ToolsVersion`, die in Projekten verwendet wird, spezifisch:  
  
-   **$(MSBuildBinPath)** ist auf den `ToolsPath`-Wert festgelegt, der entweder in der Registrierung oder in der Konfigurationsdatei festgelegt ist, in der `ToolsVersion` definiert ist. Die `$(MSBuildToolsPath)`-Einstellung in der Registrierung oder die Konfigurationsdatei gibt den Speicherort der Kernaufgaben und Ziele an. In der Projektdatei wird dies der $(MSBuildBinPath)-Eigenschaft sowie der $(MSBuildToolsPath)-Eigenschaft zugeordnet.  
  
-   `$(MSBuildToolsPath)` ist eine reservierte Eigenschaft von der MSBuildToolsPath-Eigenschaft, die in der Konfigurationsdatei festgelegt ist. (Diese Eigenschaft ersetzt `$(MSBuildBinPath)`. `$(MSBuildBinPath)` steht aus Kompatibilitätsgründen weiterhin zur Verfügung.) Ein benutzerdefiniertes Toolset muss entweder `$(MSBuildToolsPath)` oder `$(MSBuildBinPath)` definieren, jedoch nicht beides, es sei denn, beide haben denselben Wert.  
  
 Sie können auch benutzerdefinierte, Toolsversion-spezifische Eigenschaften zur Konfigurationsdatei hinzufügen, indem Sie die gleiche Syntax verwenden wie zum Hinzufügen der MSBuildToolsPath-Eigenschaft. Damit diese benutzerdefinierten Eigenschaften der Projektdatei zur Verfügung stehen, müssen Sie den gleichen Namen wie der des in der Konfigurationsdatei angegebenen Werts verwenden. In der Konfigurationsdatei können Sie Toolsets, nicht jedoch Unter-Toolsets definieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)