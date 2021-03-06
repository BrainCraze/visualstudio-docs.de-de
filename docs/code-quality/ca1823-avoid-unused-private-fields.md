---
title: 'CA1823: Nicht verwendete private Felder vermeiden | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa8af282866cd871d2717031091215cb431e1ec0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: Nicht verwendete private Felder vermeiden
|||  
|-|-|  
|TypeName|AvoidUnusedPrivateFields|  
|CheckId|CA1823|  
|Kategorie|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Mit dieser Regel wird gemeldet, wenn ein privates Feld in Ihrem Code vorhanden ist, jedoch nicht von jeder Codepfad verwendet werden.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Es wurden private Felder erkannt, auf die in der Assembly anscheinend kein Zugriff erfolgt.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das Feld aus, oder fügen Sie Code, der verwendet wird.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)  
  
 [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)