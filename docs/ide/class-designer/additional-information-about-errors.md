---
title: "Zusätzliche Informationen zu Klassen-Designer-Fehlern | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound
- vs.classdesigner.CPlusPlusNoTypeFound
- vs.classdesigner.CannotShowBaseType
- vs.classdesigner.MatchOrphanTypesAtLoad
- vs.classdesigner.CannotShowType
- vs.classdesigner.AssociationTypeNotFoundError
- vs.classdesigner.ViewInDiagramNoTypesFound
- vs.classdesigner.CannotImplementInterface
- vs.classdesigner.CannotShowImplementedInterface
- vs.classdesigner.ViewInDiagramUnparsableTypeFound
- vs.classdesigner.AssociationTypeNotFound
- vs.classdesigner.CPlusPlusTypeCannotBeAdded
helpviewer_keywords:
- errors, class diagrams
- errors, Class Designer
- error messages, Class Designer
- Class Designer [Visual Studio], errors
- error messages, class diagrams
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 53b61b1fa49ffcbc047d47dd26586b45ae883c5f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="additional-information-about-class-designer-errors"></a>Zusätzliche Informationen zu Klassen-Designer-Fehlern
Klassen-Designer verfolgt nicht den Speicherort der Quelldateien, so dass die Änderung der Projektstruktur oder verschobenen Quelldateien im Projekt dazu führen kann, dass der Klassen-Designer den Typ, insbesondere den Quelltyp eines TypeDef-, Basisklassen oder Zuordnungstypen verliert. Es wird möglicherweise ein Fehler angezeigt, z.B. **Dieser Typ kann im Klassen-Designer nicht angezeigt werden**. In diesem Fall ziehen Sie den geänderten oder verschobenen Quellcode in das Klassendiagramm, um ihn erneut anzuzeigen.  
  
Hilfe zu anderen Fehlern und Warnungen finden Sie in den folgenden Ressourcen:  
  
[Arbeiten mit Visual C++-Code](working-with-visual-cpp-code.md)  
Enthält Informationen zur Problembehandlung in Bezug auf das Anzeigen von C++ in einem Klassendiagramm.  
  
[Forum von Visual Studio-Klassen-Designer](http://go.microsoft.com/fwlink/?LinkId=160754)  
Bietet ein Forum für Fragen zum Klassen-Designer.  
  
## <a name="see-also"></a>Siehe auch
[Entwerfen und Anzeigen von Klassen und Typen](designing-and-viewing-classes-and-types.md)