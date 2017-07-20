---
title: "Gewusst wie: Ändern des Buildausgabeverzeichnisses | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 14
author: kempb
ms.author: kempb
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
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 14be502abb42d6bb9637e7394ec8bf20b50c4231
ms.lasthandoff: 04/05/2017

---
# <a name="how-to-change-the-build-output-directory"></a>Gewusst wie: Ändern des Buildausgabeverzeichnisses
Sie können den Speicherort der vom das Projekt generierten Ausgabe auf Basis der Konfiguration („Debug“, „Release“ oder beides) angeben.  
  
> [!NOTE]
>  Wenn Sie über ein **Setup** -Projekt verfügen, beachten Sie den Hinweis am Ende dieses Artikels.  
  
## <a name="changing-the-build-output-directory"></a>Ändern des Buildausgabeverzeichnisses  
  
#### <a name="to-change-the-build-output-directory"></a>So ändern Sie das Buildausgabeverzeichnis  
  
1.  Wählen Sie in der Menüleiste **Projekt**und die Option *App-Name* **Eigenschaften**aus. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eigenschaften**aus.  
  
2.  Wenn Sie ein Visual Basic-Projekt haben, wählen Sie die Registerkarte **Kompilieren** . Wenn Sie ein Visual C#-Projekt haben, wählen Sie die Registerkarte **Build** . Wenn Sie ein C++-Projekt oder ein JavaScript-Projekt haben, wählen Sie die Registerkarte **Allgemein** .  
  
3.  Wählen Sie in der Konfigurationen-Dropdownliste am oberen Rand die Konfiguration aus, deren Speicherort der Ausgabedatei Sie ändern möchten („Debug“, „Release“ oder beides).  
  
     Suchen Sie den Eintrag des Ausgabe-Pfads (**Buildausgabepfad** in Visual Basic **Ausgabeverzeichnis** in Visual C++ **Ausgabepfad** in JavaScript und C#). Geben Sie ein neues Buildausgabeverzeichnis relativ zum Projektverzeichnis an.  
  
> [!NOTE]
>  In einem Setup-Projekt wird durch das Feld **Ausgabedateiname** lediglich der Speicherort der Datei „Setup.exe“ und nicht der Speicherort der Projektdateien geändert. Weitere Informationen finden Sie unter **Erstellen, Konfigurationseigenschaften, Bereitstellungsprojekt-Eigenschaften (Dialogfeld)**.  
  
## <a name="see-also"></a>Siehe auch  
 [Seite „Erstellen“, Projekt-Designer (C#)](../ide/reference/build-page-project-designer-csharp.md)   
 [Eigenschaftenseite „Allgemein“ (Projekt)](/cpp/ide/general-property-page-project)   
 [Kompilieren und Erstellen](../ide/compiling-and-building-in-visual-studio.md)