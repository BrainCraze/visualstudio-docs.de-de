---
title: "Codeausschnitte mit R Tools für Visual Studio | Microsoft-Dokumentation"
description: "Codeausschnitte für R in Visual Studio bieten Verknüpfungen zum schnellen Einfügen von Codeblöcken mit beliebiger Länge – so kann das wiederholte Eingeben von ähnlichem Code vermieden werden."
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: d8628b2712c52aae614223b702344bb0b548e306
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="code-snippets"></a>Codeausschnitte

Codeausschnitte in Visual Studio bieten Verknüpfungen zum schnellen Einfügen von Codeblöcken mit beliebiger Länge, und es wird vermieden, dass der gleiche Code immer wieder eingegeben werden muss. Die R Tools für Visual Studio (RTVS) fügen Dutzende nützlicher R-Ausschnitte zur Sammlung von Visual Studio hinzu.

Um einen Ausschnitt einzufügen, geben Sie den abgekürzten Namen des Ausschnitts ein (IntelliSense wird bereitgestellt), und drücken Sie dann die TAB-Taste zum Einfügen.

Hier sind einige einfache Beispiele:

- geben Sie `=` ein, was mithilfe der TAB-Taste und RTVS zum Zuweisungsoperator `<-` erweitert wird.
- geben Sie `>` ein, was mithilfe der TAB-Taste und RTVS zum Pipeoperator `%>%` erweitert wird.

Ausschnitte können viel mehr sein als nur die Zeichenvervollständigung von Zeichen. Durch einen Ausschnitt zum Lesen einer CSV-Datei mit der `read.csv`-Funktion müssen Sie sich zum Beispiel nicht mehr die Namen und Parameter merken:

![Animation der Verwendung eines Codeausschnitts zum Einfügen eines Aufrufs von „read.csv“](media/code-snippet-expansion.gif)

In diesem Fall zeigt IntelliSense eine Vervollständigungsliste an, wenn Sie `readc` eintippen. Wenn Sie die Vervollständigung in der Dropdownliste auswählen und die TAB-Taste drücken, wird `readc` ausgewählt. Wenn Sie erneut die TAB-Taste drücken, wird der Ausschnitt erweitert. (Aus diesem Grund wird die Ausschnitterweiterung oft mit „den Ausschnitt eintippen und die TAB-Taste zweimal drücken“ gleichgesetzt). In den meisten Fällen beendet das erste Drücken der TAB-Taste die IntelliSense-Auswahl, und ein erneutes Drücken der TAB-Taste löst die Erweiterung aus.

Um alle verfügbaren Ausschnitte anzuzeigen, öffnen Sie das Dialogfeld **Extras > Codeausschnitt-Manager...** (STRG+K,B), und wählen Sie für **Sprache** **R** aus. Erweitern Sie die Gruppen, und wählen Sie einzelne Ausschnitte aus, um eine Beschreibung sowie den Verknüpfungstext anzuzeigen:

![Dialogfeld „Codeausschnitt-Manager“ für R](media/code-snippet-dialog.png)

Um benutzerdefinierte Codeausschnitte zu erstellen, befolgen Sie die Anweisungen unter [Exemplarische Vorgehensweise: Erstellen eines Codeausschnitts](../ide/walkthrough-creating-a-code-snippet.md). Letztendlich ist ein Codeausschnitt nur eine XML-Datei. Der folgende Code stellt beispielsweise den Ausschnitt für einen Pipevorgang dar (Verknüpfung `>`):

```xml
<?xml version="1.0" encoding="utf-8" ?>
<CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>Dplyr pipe</Title>
      <Shortcut>&gt;</Shortcut>
      <Description>Code snippet for '%&gt;%' operator</Description>
      <Author>Microsoft Corporation</Author>
      <SnippetTypes>
        <SnippetType>Expansion</SnippetType>
       </SnippetTypes>
    </Header>
    <Snippet>
      <Code Language="R">
        <![CDATA[ %>% $end$]]>
      </Code>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

Die XML-Dateien für alle Codeausschnitte werden mit RTVS installiert, und das Feld **Speicherort** im **Codeausschnitt-Manager** stellt den Pfad bereit. Sie können sie auch im RTVS-Quellcode auf GitHub unter [src/Package/Impl/Snippets](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets) finden.
