---
title: 'Vorgehensweise: Verweisen auf den Namen oder Speicherort der Projektdatei | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
caps.latest.revision: 13
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
ms.openlocfilehash: cd4ed0d5d7df332bd1f49edd5989f56a09293c44
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Gewusst wie: Verweisen auf den Namen oder Speicherort der Projektdatei
Sie können den Namen oder Speicherort des Projekts in der Projektdatei verwenden, selbst ohne eine eigene Eigenschaft erstellt zu haben. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] stellt reservierte Eigenschaften zur Verfügung, die auf die Projektdateinamen sowie andere Eigenschaften verweisen, die zum Projekt gehören. Weitere Informationen zu reservierten Eigenschaften finden Sie unter [Reservierte und bekannte Eigenschaften für MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="using-the-msbuildprojectname-property"></a>Verwenden der MSBuildProjectName-Eigenschaft  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] stellt einige reservierten Eigenschaften bereit, die Sie in den Projektdateien verwenden können, ohne sie jedes Mal zu definieren. Beispiel: Die reservierte Eigenschaft `MSBuildProjectName` stellt einen Verweis zum Projektdateinamen bereit.  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>So verwenden Sie die MSBuildProjectName-Eigenschaft  
  
-   Verweisen Sie die Eigenschaft in der Projektdatei mit der $()-Notation genau so, wie Sie es mit anderen Eigenschaften machen würden. Zum Beispiel:  
  
    ```xml  
    <CSC Sources = "@(CSFile)"   
        OutputAssembly = "$(MSBuildProjectName).exe"/>  
    </CSC>  
    ```  
  
 Ein Vorteil der Verwendung einer reservierten Eigenschaft ist, dass alle Änderungen am Projektdateinamen automatisch integriert sind. Das nächste Mal, wenn Sie das Projekt erstellen, wird die Ausgabedatei den neuen Namen haben, ohne dass von Ihnen Handlungsbedarf besteht.  
  
> [!NOTE]
>  Reservierte Eigenschaften können nicht in der Projektdatei neu definiert werden.  
  
## <a name="example"></a>Beispiel  
 Die folgende Beispiel-Projektdatei verweist den Projektnamen als reservierte Eigenschaft, um den Namen für die Ausgabe anzugeben.  
  
```xml  
<Project xmlns="http://scheams.microsoft.com/developer/msbuild/2003"   
    DefaultTargets = "Compile">  
  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using  
        input files of type CSFile -->  
        <CSC Sources = "@(CSFile)"  
            OutputAssembly = "$(MSBuildProjectName).exe" >  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the project -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
[MSBuild](../msbuild/msbuild.md)  
 [Reservierte und bekannte Eigenschaften für MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)