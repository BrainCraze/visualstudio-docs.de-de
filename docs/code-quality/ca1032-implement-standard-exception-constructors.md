---
title: 'CA1032: Standardausnahmekonstruktoren implementieren | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f2cb2cd82eb776c536b4b54f6861e9b4c825ecbe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Standardausnahmekonstruktoren implementieren
|||  
|-|-|  
|TypeName|ImplementStandardExceptionConstructors|  
|CheckId|CA1032|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Ein Typ erweitert <xref:System.Exception?displayProperty=fullName> und nicht alle erforderlichen Konstruktoren deklariert.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Ausnahmetypen müssen die folgenden Konstruktoren implementieren:  
  
-   Öffentliche NewException()  
  
-   Öffentliche NewException(string)  
  
-   Öffentliche NewException (String, Ausnahme)  
  
-   geschützt oder privat NewException (SerializationInfo, StreamingContext)  
  
 Falls nicht der vollständige Satz von Konstruktoren angegeben wird, wird eine ordnungsgemäße Behandlung von Ausnahmen unter Umständen erschwert. Z. B. des Konstruktors, der die Signatur hat `NewException(string, Exception)` wird verwendet, um Ausnahmen zu erstellen, die von anderen Ausnahmen verursacht werden. Ohne diesen Konstruktor, Sie können nicht erstellt und lösen eine Instanz der benutzerdefinierten Ausnahme, die eine interne (geschachtelte) Ausnahme enthält, wird der verwalteten Codes in einer solchen Situation ausführen soll. Die ersten drei Standardausnahmekonstruktoren sind gemäß der Konvention öffentlich. Der vierte Konstruktor ist in nicht versiegelten Klassen geschützt und privat in versiegelten Klassen. Weitere Informationen finden Sie unter [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie die fehlenden Konstruktoren auf die Ausnahme, und stellen Sie sicher, dass sie die richtige Zugriffsebene aufweisen.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig auf eine Warnung dieser Regel zu unterdrücken, wenn die Verletzung verursacht wird, eine andere Zugriffsebene für die öffentlichen Konstruktoren mit.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel enthält einen Ausnahmetyp, der mit dieser Regel verletzt und einen Ausnahmetyp, der ordnungsgemäß implementiert ist.  
  
 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]