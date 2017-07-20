---
title: "Building Multiple Projects in Parallel with MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "parallel project builds"
  - "building multiple projects in parallel"
  - "msbuild, building projects in parallel"
ms.assetid: c8c9aadc-33ad-4aa1-b07d-b879e9eabda0
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Building Multiple Projects in Parallel with MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können MSBuild verwenden, um mehrere Projekte schneller zu erstellen, indem Sie sie parallel ausführen.  Um Builds parallel auszuführen, verwenden Sie die folgenden Einstellungen auf einem Mehrkern\- oder Mehrprozessorcomputer:  
  
-   den Schalter `/maxcpucount` in einer Eingabeaufforderung  
  
-   den <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A>\-Aufgabenparameter in einer MSBuild\-Aufgabe  
  
> [!NOTE]
>  Der Schalter **\/verbosity** \(**\/v**\) in einer Befehlszeile kann die Buildleistung ebenfalls beeinflussen.  Die Buildleistung verringert sich möglicherweise, wenn die Ausführlichkeit der Buildprotokollinformationen auf die Einstellung "Detailliert" oder "Diagnose" festgelegt ist, die beide für die Problembehandlung verwendet werden.  Weitere Informationen finden Sie unter [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md) und [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md).  
  
## Schalter "\/maxcpucount"  
 Wenn Sie den Schalter `/maxcpucount` oder die kurze Form `/m` verwenden, kann MSBuild die angegebene Anzahl von MSBuild.exe\-Prozessen erstellen, die parallel ausgeführt werden können.  Diese Prozesse werden auch als "Arbeitsprozesse" bezeichnet. Jeder Arbeitsprozess verwendet einen anderen Kern oder Prozessor, soweit verfügbar, um ein Projekt zu der gleichen Zeit zu erstellen wie andere verfügbare Prozessoren.  Wenn Sie zum Beispiel diesen Schalter auf den Wert "4" festlegen, erstellt MSBuild vier Arbeitsprozesse zum Erstellen des Projekts.  
  
 Wenn Sie den Schalter `/maxcpucount` verwenden, ohne einen Wert anzugeben, verwendet MSBuild alle Prozessoren des Computers.  
  
 Weitere Informationen über diesen Schalter, der in MSBuild 3.5 eingeführt wurde, finden Sie unter [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md).  
  
 Das folgende Beispiel weist MSBuild an, drei Arbeitsprozesse zu verwenden.  Wenn Sie diese Konfiguration verwenden, kann MSBuild drei Projekte gleichzeitig erstellen.  
  
```  
msbuild.exe myproj.proj /maxcpucount:3  
```  
  
## BuildInParallel\-Aufgabenparameter  
 `BuildInParallel` ist ein optionaler boolescher Parameter für eine [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Aufgabe.  Wenn `BuildInParallel` auf `true` \(der Standardwert\) festgelegt ist, werden mehrere Arbeitsprozesse zum gleichzeitigen Erstellen so vieler Projekte wie möglich erzeugt.  Damit dies ordnungsgemäß funktioniert, muss der `/maxcpucount`\-Schalter auf einen Wert größer 1 festgelegt sein, und das System muss mindestens ein Dualcore\-System sein oder über mindestens zwei Prozessoren verfügen.  
  
 Nachfolgend ist ein Beispiel aus microsoft.common.targets aufgeführt, das veranschaulicht, wie der `BuildInParallel`\-Parameter festgelegt wird.  
  
```  
<PropertyGroup>  
    <BuildInParallel Condition="'$(BuildInParallel)' ==   
        ''">true</BuildInParallel>  
</PropertyGroup>  
<MSBuild  
    Projects="@(_MSBuildProjectReferenceExistent)"  
    Targets="GetTargetPath"  
    BuildInParallel="$(BuildInParallel)"  
    Properties="%(_MSBuildProjectReferenceExistent.SetConfiguration);   
        %(_MSBuildProjectReferenceExistent.SetPlatform)"  
    Condition="'@(NonVCProjectReference)'!='' and   
        ('$(BuildingSolutionFile)' == 'true' or   
        '$(BuildingInsideVisualStudio)' == 'true' or   
        '$(BuildProjectReferences)' != 'true') and     
        '@(_MSBuildProjectReferenceExistent)' != ''"  
    ContinueOnError="!$(BuildingProject)">  
    <Output TaskParameter="TargetOutputs"   
        ItemName="_ResolvedProjectReferencePaths"/>  
</MSBuild>  
```  
  
## Siehe auch  
 [Using Multiple Processors to Build Projects](../msbuild/using-multiple-processors-to-build-projects.md)   
 [Writing Multi\-Processor\-Aware Loggers](../msbuild/writing-multi-processor-aware-loggers.md)   
 [Blog zum Optimieren der C\+\+\-Buildparallelität](http://go.microsoft.com/fwlink/?LinkId=251457)