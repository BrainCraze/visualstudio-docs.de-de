---
title: Refactoring des Umbenennens in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: bd15d1b59eb5d593fe2b069c2b6721ca623ae99c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="rename-a-code-symbol-refactoring"></a>Refactoring des Umbenennens eines Codesymbols

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung**: Hiermit können Sie Bezeichner für Codesymbole (z.B. Felder, lokale Variablen, Methoden, Namespaces, Eigenschaften und Typen) umbenennen.

**Hintergrund**: Sie möchten ein Element sicher umbenennen, ohne alle Instanzen suchen und den neuen Namen kopieren und einfügen zu müssen.

**Vorteile**: Das Kopieren und Einfügen des neuen Namens in ein ganzes Projekt würde aller Wahrscheinlichkeit nach zu Fehlern führen. Dieses Refactoringtool führt die Umbenennungsaktion ordnungsgemäß durch.

## <a name="how-to"></a>Vorgehensweise

1. Markieren Sie den Namen des umzubenennenden Elements, oder platzieren Sie den Textcursor in das Element:

   - C#:

    ![Hervorgehobener Code – C#](media/rename-highlight-cs.png)

   - Visual Basic:

    ![Hervorgehobener Code – Visual Basic](media/rename-highlight-vb.png)

1. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
     - Drücken Sie **STRG+R** und dann **STRG+R**. (Beachten Sie, dass Ihre Tastenkombination je nach dem gewählten Profil möglicherweise abweicht.)
   - **Maus**
     - Wählen Sie **Bearbeiten > Umgestalten > Umbenennen** aus.
     - Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie **Umbenennen** aus.

1. Benennen Sie das Element einfach um, indem Sie den neuen Namen eingeben.

   - C#:

    ![Animation des Umbenennungsvorgangs – C#](media/rename-animated-cs.gif)

   - Visual Basic:

    ![Umbenennung – Visual Basic](media/rename-rename-vb.png)

   > [!TIP]
   > Sie können Kommentare und andere Zeichenfolgen vor dem Speichern mit diesem neuen Namen aktualisieren sowie eine [Vorschau der Änderungen](../../ide/preview-changes.md) anzeigen, indem Sie oben rechts im Editor die jeweiligen Kontrollkästchen im Feld **Umbenennen** aktivieren.

1. Wenn Sie mit der Änderung zufrieden sind, klicken Sie auf die Schaltfläche **Übernehmen**, oder drücken Sie die **EINGABETASTE**. Die Änderungen werden angewendet.

> [!NOTE]
> Wenn Sie einen bereits vorhandenen Namen verwenden, der zu einem Konflikt führen würde, werden Sie durch das Feld **Umbenennen** darüber informiert.
>
> ![Umbenennungskonflikt](media/rename-conflict-cs.png)

## <a name="see-also"></a>Siehe auch

[Refactoring](../refactoring-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)
