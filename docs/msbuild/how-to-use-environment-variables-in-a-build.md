---
title: 'Vorgehensweise: Verwenden von Umgebungsvariablen in einem Build | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
caps.latest.revision: 15
author: kempb
ms.author: kempb
manager: ghogen
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
translationtype: Human Translation
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: 352950f52c335be52b1765a6008c26db1550a5b0
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-use-environment-variables-in-a-build"></a>Gewusst wie: Verwenden von Umgebungsvariablen in einem Build
Wenn Sie Projekte erstellen, ist es oft erforderlich, Buildoptionen mithilfe der Informationen festzulegen, die sich nicht in der Projektdatei oder in den Dateien befinden, aus denen Ihr Projekt besteht. Diese Informationen werden normalerweise in Umgebungsvariablen gespeichert.  
  
## <a name="referencing-environment-variables"></a>Verweisen auf Umgebungsvariablen  
 Alle Umgebungsvariablen stehen der [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)])-Projektdatei als Eigenschaften zur Verfügung.  
  
> [!NOTE]
>  Wenn das Projekt eine Eigenschaftsdefinition enthält, die denselben Namen wie eine Umgebungsvariable hat, wird der Wert der Umgebungsvariablen von der Eigenschaft im Projekt überschrieben.  
  
#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>Verwenden einer Umgebungsvariable in einem MSBuild-Projekt  
  
-   Verweisen Sie auf die gleiche Art auf Umgebungsvariablen wie auf eine Variable, die in der Projektdatei deklariert ist. Beispielsweise verweist der folgende Code auf die Umgebungsvariable BIN_PATH:  
  
     `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`  
  
 Sie können ein `Condition`-Attribut verwenden, um einen Standardwert für eine Eigenschaft anzugeben, wenn die Umgebungsvariable nicht festgelegt wurde.  
  
#### <a name="to-provide-a-default-value-for-a-property"></a>Gibt den Standardwert für eine Eigenschaft an  
  
-   Verwenden eines `Condition`-Attributs für eine Eigenschaft, um einen Wert festzulegen, nur wenn die Eigenschaft keinen Wert hat. Im folgenden Code wird z.B. die `ToolsPath`-Eigenschaft nur auf c:\tools festgelegt, wenn die `ToolsPath`-Umgebungsvariable nicht festgelegt ist:  
  
     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`  
  
    > [!NOTE]
    >  Eigenschaftennamen unterscheiden keine Groß-/Kleinschreibung, sodass jeweils `$(ToolsPath)` und `$(TOOLSPATH)` auf die gleiche Eigenschaft oder Umgebungsvariable verweisen.  
  
## <a name="example"></a>Beispiel  
 Die folgende Projektdatei verwendet Umgebungsvariablen, um den Speicherort von Verzeichnissen anzugeben.  
  
```xml  
<Project DefaultTargets="FakeBuild">  
    <PropertyGroup>  
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>  
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">  
            C:\Tools  
        </ToolsPath>  
    </PropertyGroup>  
    <Target Name="FakeBuild">  
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
    [MSBuild ](../msbuild/msbuild.md)
    [MSBuild Properties](../msbuild/msbuild-properties.md)
 [Gewusst wie: Erstellen identischer Quelldateien mit unterschiedlichen Optionen](../msbuild/how-to-build-the-same-source-files-with-different-options.md)