---
title: "Gewusst wie: Verwenden von Haltepunkten bei XSLT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Gewusst wie: Verwenden von Haltepunkten bei XSLT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Haltepunkte in einem XSLT\-Stylesheet oder im XML\-Quelldokument festlegen.Wenn Sie einen Haltepunkt für ein Tag festlegen, wird der Haltepunkt beim Starten der Ausführung zur nächsten Anweisung verschoben, die über Quellzeileninformationen verfügt.  
  
 Weitere Informationen finden Sie unter [Debugging Basics: Breakpoints](http://msdn.microsoft.com/de-de/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e).  
  
## Festlegen eines Haltepunkts in einem Stylesheet  
 Haltepunkte können für Starttags, Endtags und Textknoten eines XSLT\-Stylesheets festgelegt werden.Haltepunkte können auch für Code in einem Skriptblock festgelegt werden.  
  
#### So legen Sie einen Haltepunkt in einem Stylesheet fest  
  
1.  Öffnen Sie ein Stylesheet im XML\-Editor.  
  
2.  Positionieren Sie den Cursor auf der Position des Haltepunkts, klicken Sie mit der rechten Maustaste, zeigen Sie auf **Haltepunkt**, und klicken Sie auf **Haltepunkt einfügen**.  
  
3.  Klicken Sie im Eigenschaftenfenster des Dokuments auf die Durchsuchen\-Schaltfläche \(**...**\) für das Feld **Eingabe**.  
  
4.  Suchen Sie das XML\-Quelldokument, und klicken Sie auf **Öffnen**.  
  
     Damit legen Sie die Quelldokumentdatei fest, die für die XSLT\-Transformation verwendet wird.  
  
5.  Klicken Sie auf der XML\-Editor\-Symbolleiste auf **XSLT debuggen**.  
  
## Festlegen eines Haltepunkts in einem XML\-Quelldokument  
 Haltepunkte können für Elemente, Attribute, Namespaceknoten, Kommentare, Verarbeitungsanweisungen und Textknoten eines XML\-Quelldokuments festgelegt werden.Für den Dokumentknoten oder einen Namespaceknoten, der vom übergeordneten Element erbt, kann kein Haltepunkt festgelegt werden.  
  
#### So legen Sie einen Haltepunkt in einem XML\-Quelldokument fest  
  
1.  Öffnen Sie das XML\-Dokument im XML\-Editor.  
  
2.  Positionieren Sie den Cursor auf der Position des Haltepunkts, klicken Sie mit der rechten Maustaste, zeigen Sie auf **Haltepunkt**, und klicken Sie auf **Haltepunkt einfügen**.  
  
3.  Klicken Sie im Eigenschaftenfenster des Dokuments auf die Durchsuchen\-Schaltfläche \(**...**\) für das Feld **Stylesheet**.  
  
4.  Suchen Sie das XML\-Quelldokument, und klicken Sie auf **Öffnen**.  
  
     Damit legen Sie die Quelldokumentdatei fest, die für die XSLT\-Transformation verwendet wird.  
  
5.  Klicken Sie auf der XML\-Editor\-Symbolleiste auf **XSLT debuggen**.  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Debuggen eines XSLT\-Stylesheets](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)