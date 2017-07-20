---
title: 'Vorgehensweise: Verwenden reservierter XML-Zeichen in Projektdateien | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
caps.latest.revision: 14
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
ms.openlocfilehash: f4b909c055e6ae3734ef8d53717c119c534689df
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Gewusst wie: Verwenden reservierter XML-Zeichen in Projektdateien
Wenn Sie Projektdateien erstellen, müssen Sie reservierte XML-Zeichen verwenden, z.B. in Eigenschaftswerten oder Aufgabenparameterwerten. Einige reservierte Zeichen müssen jedoch durch eine benannte Entität ersetzt werden, sodass die Projektdatei analysiert werden kann.  
  
## <a name="using-reserved-characters"></a>Reservierte Zeichen verwenden  
 Die folgende Tabelle beschreibt die reservierten XML-Zeichen, die durch die entsprechende benannte Entität ersetzt werden müssen, damit die Projektdatei analysiert werden kann.  
  
|Reserviertes Zeichen|Benannte Entität|  
|------------------------|------------------|  
|\<|&lt;|  
|>|&gt;|  
|&|&amp;|  
|"|&quot;|  
|'|&apos;|  
  
#### <a name="to-use-double-quotes-in-a-project-file"></a>Doppelte Anführungszeichen in einer Projektdatei verwenden  
  
-   Ersetzen Sie die doppelten Anführungszeichen durch die entsprechende benannte Entität &quot;. Um beispielsweise doppelte Anführungszeichen um die `EXEFile`-Elementliste zu setzen, geben Sie Folgendes ein:  
  
    ```xml  
    <Message Text="The output file is "@(EXEFile)"."/>  
    ```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel werden doppelte Anführungszeichen zum Markieren des Dateinamens in der Meldung benutzt, die von der Projektdatei ausgegeben wird.  
  
```xml  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>"HelloWorldCS"</appname>  
    </PropertyGroup>  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs" />  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input  
        files of type CSFile -->  
        <Csc Sources = "@(CSFile)">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile"/>  
        </Csc>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is "@(EXEFile)"."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)
 [MSBuild](../msbuild/msbuild.md)