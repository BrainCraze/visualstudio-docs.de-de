---
title: 'CA1024: Eigenschaften verwenden | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9bf44541c9eca3d2b8027ff1b5811caf0ba6824f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Nach Möglichkeit Eigenschaften verwenden
|||  
|-|-|  
|TypeName|UsePropertiesWhereAppropriate|  
|CheckId|CA1024|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Eine öffentliche oder geschützte Methode hat einen Namen, die mit beginnt `Get`nimmt keine Parameter und gibt einen Wert, der kein Array ist.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 In den meisten Fällen Daten darstellen, Eigenschaften und Methoden Aktionen ausführen. Eigenschaften sind zugegriffen, wie Felder, sodass sie einfacher zu verwenden. Eine Methode ist, eignet sich für eine Eigenschaft zu werden, wenn eine der folgenden Bedingungen vorliegt:  
  
-   Akzeptiert keine Argumente und gibt die Zustandsinformationen eines Objekts zurück.  
  
-   Akzeptiert ein einzelnes Argument, um einen Teil des Zustands eines Objekts festgelegt.  
  
 Eigenschaften sollten so, als ob diese Felder sind; Wenn die Methode nicht möglich ist, sollten sie nicht auf eine Eigenschaft geändert werden. Methoden sind besser als Eigenschaften in den folgenden Situationen:  
  
-   Die Methode ausführt einen zeitaufwändigen Vorgang. Die Methode ist als die Zeit, die erforderlich sind, um festzulegen, oder rufen Sie den Wert eines Felds beansprucht.  
  
-   Die Methode führt eine Konvertierung. Zugriff auf ein Feld zurückgibt keinen konvertierte Version der Daten, in dem es gespeichert.  
  
-   Die Get-Methode hat einen Observable Nebeneffekt. Das Abrufen des Werts eines Felds erzeugt kein keine Nebeneffekte.  
  
-   Die Reihenfolge der Ausführung ist wichtig. Festlegen des Werts eines Felds beruht nicht auf das Vorkommen von anderen Vorgängen.  
  
-   Aufrufen der Methode zweimal hintereinander führt zu unterschiedlichen Ergebnissen.  
  
-   Die Methode ist statisch, aber es gibt ein Objekt, das vom Aufrufer geändert werden kann. Das Abrufen des Werts eines Felds lässt keine Aufrufer zum Ändern der Daten, die nach dem Feld gespeichert wird.  
  
-   Die Methode gibt ein Array zurück.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Methode einer Eigenschaft ein.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, wenn die Methode mindestens eines der zuvor aufgeführten Kriterien erfüllt.  
  
## <a name="controlling-property-expansion-in-the-debugger"></a>Steuern der Erweiterung der Eigenschaft im Debugger  
 Ein Grund, dass Programmierer vermeiden, verwenden eine Eigenschaft ist, da sie nicht, dass den Debugger automatisch erweitert möchten. Beispielsweise die Eigenschaft kann das Zuweisen eines großen Objekts oder P/Invoke aufrufen umfassen, aber es möglicherweise nicht tatsächlich keine Observable Nebeneffekte.  
  
 Sie können verhindern, dass den Debugger automatisch erweitert Eigenschaften durch Anwenden von <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. Das folgende Beispiel zeigt dieses Attribut auf eine Instance-Eigenschaft angewendet wird.  
  
```vb  
Imports System   
Imports System.Diagnostics   
  
Namespace Microsoft.Samples   
  
    Public Class TestClass   
  
        ' [...]   
  
        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _   
        Public ReadOnly Property LargeObject() As LargeObject   
            Get   
                ' Allocate large object   
                ' [...]   
            End Get   
        End Property   
  
    End Class   
  
End Namespace  
```  
  
```csharp  
  
      using System;   
using System.Diagnostics;   
  
namespace Microsoft.Samples   
{   
    publicclass TestClass   
    {   
        // [...]   
  
        [DebuggerBrowsable(DebuggerBrowsableState.Never)]   
        public LargeObject LargeObject   
        {   
            get   
            {   
                // Allocate large object   
                // [...]   
  
        }  
    }  
}  
```  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel enthält mehrere Methoden, die in Eigenschaften konvertiert werden sollte, und mehrere, die nicht verwendet werden, da kein Verhalten wie Felder aufweisen sollte.  
  
 [!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]