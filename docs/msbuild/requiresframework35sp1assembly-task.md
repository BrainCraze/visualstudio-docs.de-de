---
title: RequiresFramework35SP1Assembly-Aufgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RequiresFramework35SP1Assembly task [MSBuild]
- MSBuild, RequiresFramework35SP1Assembly task
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
caps.latest.revision: 6
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e95632e1b339e7b86253763fa65237165eb05618
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/10/2018
---
# <a name="requiresframework35sp1assembly-task"></a>RequiresFramework35SP1Assembly-Aufgabe
Bestimmt, ob die Anwendung .NET Framework 3.5 SP1 erfordert  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `RequiresFramework35SP1Assembly` -Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`Assemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die Assemblys an, auf die in der Anwendung verwiesen wird.|  
|`CreateDesktopShortcut`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true` wird bei der Installation ein Verknüpfungssymbol auf dem Desktop erstellt.|  
|`DeploymentManifestEntryPoint`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt den Namen der Manifestdatei für die Anwendung an.|  
|`EntryPoint`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt die Assembly an, die ausgeführt werden soll, wenn die Anwendung ausgeführt wird.|  
|`ErrorReportUrl`|Optionaler `String` -Parameter.<br /><br /> Gibt die URL der Website an, die in Dialogfeldern angezeigt wird, die bei den ClickOnce-Installationen auftreten.|  
|`Files`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die Liste der Dateien an, die bereitgestellt werden, wenn die Anwendung veröffentlicht wird.|  
|`ReferencedAssemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die Assemblys an, auf die in dem Projekt verwiesen wird.|  
|`RequiresMinimumFramework35SP1`|Optionaler `Boolean`-Ausgabeparameter.<br /><br /> Wenn `true`, erfordert die Anwendung .NET Framework 3.5 SP1.|  
|`SigningManifests`|Optionaler `Boolean`-Ausgabeparameter.<br /><br /> Wenn `true`, werden die ClickOnce-Manifeste signiert.|  
|`SuiteName`|Optionaler `String` -Parameter.<br /><br /> Gibt den Namen des Ordners im Menü **Start** an, in dem die Anwendung installiert wird.|  
|`TargetFrameworkVersion`|Optionaler `String` -Parameter.<br /><br /> Gibt die .NET Framework-Version an, auf die diese Anwendung ausgerichtet ist.|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)