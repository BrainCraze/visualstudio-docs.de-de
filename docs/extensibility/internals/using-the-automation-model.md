---
title: Über das Automatisierungsmodell | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 679e9966e66de1c79cb3c6394f1d80ab6d6733bb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-automation-model"></a>Mithilfe des Automatisierungsmodells
Nachdem Sie Ihr VSPackage für die Automatisierung verbunden haben, erhalten Sie die Eigenschaften und Methoden durch Aufrufen der <xref:EnvDTE.DTEClass.GetObject%2A> Methode für die <xref:EnvDTE._DTE> Objekt auf und übergibt eine Zeichenfolge, die das Objekt, das Sie abrufen möchten.  
  
## <a name="obtaining-project-objects"></a>Abrufen von Project-Objekte  
 Es folgen zwei Codebeispielen, die veranschaulichen, wie ein Consumer Automatisierung des Projekts Automatisierungsobjekte erhält. Informationen zum Abrufen des DTE-Objekts, finden Sie unter [Vorgehensweise: Abrufen der Verweise auf den DTE und DTE2-Objekten](http://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).  
  
```vb  
Sub DoAutomation()  
    Dim MyProjects As Projects  
    MyProjects = DTE.GetObject("AcmeProject")  
End Sub  
```  
  
```cpp  
void DoAutomation(void)  
{  
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.  
    pMyPkg = pDTE->GetObject("AcmeProjects");   
  
   // The '=' performs a Query Interface.  
   // Assumes pDTE is already available as a global.  
   // Use pMyPkg to access your projects object's properties and methods.  
}  
  
```  
  
 An diesem Punkt können Sie die standard-Projekt-Objekte, die Teil eines bestimmten VSPackage, um das Hierarchiemodell zu verschieben.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie ein benutzerdefiniertes Objekt abgerufen, die eine Eigenschaft eines benutzerdefinierten Projekttyps.:  
  
```vb  
Dim MyPrj As Project  
Dim MyPrjItem As ProjectItem  
Dim objMyObject as MyExtendedObject  
  
MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project  
objMyObject = MyPrj.Object 'You call .Object to get to special Project  
                           'implementation  
objMyObject.MySpecialMethodOrProperty  
```  
  
 Der folgende Code Listet die Namen aller Eigenschaften in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung **allgemeine** option die **Tools** Menü:  
  
```vb  
dim objDTE  
dim objEnv  
set objDTE = CreateObject("VisualStudio.DTE")  
set objEnv = objDTE.Properties("Environment", "General")  
for each obj in ObjEnv  
MsgBox obj.Name  
Next  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:EnvDTE.DTEClass.GetObject%2A>