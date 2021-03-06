---
title: Haltepunkt ist bei Treffer Dialogfeld | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 627fe393d235f6d0392181cf2370cda71737a4f2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Dialogfeld "Beim Erreichen eines Haltepunktes"
In diesem Dialogfeld können Sie die Aktion anpassen, die beim Erreichen eines Haltepunkts ausgeführt wird.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Meldung drucken**  
 Druckt eine Meldung mithilfe der DebuggerDisplay-Syntax. Weitere Informationen finden Sie unter [mithilfe des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Dieses Textfeld unterstützt auch spezielle Schlüsselwörter (z. B. $ADDRESS), die alleine oder innerhalb der geschweiften Klammern eines DebuggerDisplay-Ausdrucks verwendet werden können. Die verfügbaren Schlüsselwörter werden im Dialogfeld aufgelistet.  
  
 **Fortsetzen der Ausführung**  
 Dieses Steuerelement ist aktiviert. nur wenn **Meldung drucken** ausgewählt ist. Durch Auswählen dieses Steuerelements können Sie einen Haltepunkt als Ablaufverfolgungspunkt verwenden, um die Programmausführung zu verfolgen, statt beim Erreichen des Haltepunkts zu unterbrechen.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)   
 [Verwenden des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md)