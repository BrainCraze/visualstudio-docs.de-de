---
title: Keine Quelle verfügbar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 022b629076e79dea679541ed301b0a7ff0c7d876
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="no-source-available"></a>Keine Quelle verfügbar
Das Projekt enthält keinen Quellcode für den Code, den Sie anzeigen möchten. Die übliche Ursache ist Doppelklicken ein Modul, das nicht Quellcode, in verfügt der **Aufruflistenfenster** oder **Fensters "Threads"**. Sie können das Debuggen fortsetzen, jedoch das Quellcodefenster nicht zum Festlegen von Haltepunkten und zum Durchführen anderer Aktionen an dieser Position verwenden. Wenn Sie einen Haltepunkt festzulegen, verwenden die **Disassemblyfenster** stattdessen.  
  
 Auf den Eigenschaftenseiten für Projektmappen können Sie die Verzeichnisse ändern, in denen der Debugger nach Quelldateien sucht, und den Debugger anweisen, die ausgewählten Quelldateien zu ignorieren. Finden Sie unter [Debuggen Quelle Dateien, allgemeine Eigenschaften Lösung Property Pages Dialog Box](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Navigieren Sie zum Quellcode**  
 Klicken Sie auf diesen Link, um ein Dialogfeld zu öffnen, in dem Sie nach dem Quellcode suchen können.  
  
 **Disassembly anzeigen**  
 Startet die **Disassemblyfenster**.  
  
 **Zeigen Sie Disassembly für fehlende Quelldateien immer an**  
 Wählen Sie diese Option zum Anzeigen der **Disassemblyfenster** automatisch Wenn kein Quellcode verfügbar ist. Diese Einstellung kann auch geändert werden, der **Optionen** Dialogfeld **Debuggen** Kategorie **allgemeine** Seite, indem aktivieren bzw. deaktivieren **Disassembly anzeigen, wenn Quelle ist nicht verfügbar**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Quelle Dateien, allgemeine Eigenschaften Lösung Property Pages Dialog Box](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (SOS-Debugerweiterung)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)