---
title: 'CA1300: MessageBoxOptions angeben | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 914654c5e2eee601ee2b314f15f5dfadb686c047
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: MessageBoxOptions angeben
|||  
|-|-|  
|TypeName|SpecifyMessageBoxOptions|  
|CheckId|CA1300|  
|Kategorie|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Eine Methode aufruft, eine Überladung der <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> -Methode, die keine akzeptiert eine <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> Argument.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Zum Anzeigen eines Meldungsfelds ordnungsgemäß für die Kulturen, die ein rechts-nach-Links-Lesefolge verwenden die <xref:System.Windows.Forms.MessageBoxOptions> und <xref:System.Windows.Forms.MessageBoxOptions> Mitglied der <xref:System.Windows.Forms.MessageBoxOptions> Enumeration übergeben werden muss, um die <xref:System.Windows.Forms.MessageBox.Show%2A> Methode. Überprüfen Sie die <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> Eigenschaft des Containersteuerelements, um festzustellen, ob ein rechts-nach-Links-Lesefolge verwendet.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie eine Überladung der <xref:System.Windows.Forms.MessageBox.Show%2A> Methode, eine <xref:System.Windows.Forms.MessageBoxOptions> Argument.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig auf eine Warnung dieser Regel zu unterdrücken, wenn die Codebibliothek nicht für eine Kultur lokalisiert wird, die rechts-nach-Links-Lesefolge verwendet.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Methode, die ein Meldungsfeld angezeigt wird, Optionen enthält, die für die Lesefolge der Kultur geeignet sind. Eine Ressourcendatei, die nicht angezeigt wird, ist erforderlich, um das Beispiel zu erstellen. Führen Sie die Kommentare im Beispiel wird das Beispiel ohne eine Ressourcendatei zu erstellen und die rechts-nach-links-Funktion zu testen.  
  
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [Ressourcen in Desktop-Apps](/dotnet/framework/resources/index)