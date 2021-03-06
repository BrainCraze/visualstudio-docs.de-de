---
title: 'CA2123: Überschreibungslinkaufrufe sollten mit der Basis identisch sein | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c23bdf9246855fc4a91d5cd5f748f8f8fb17a67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: Überschreibungslinkaufrufe sollten mit der Basis identisch sein
|||  
|-|-|  
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|  
|CheckId|CA2123|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ eine Methode überschreibt bzw. implementiert eine Schnittstelle und verfügt nicht über die gleichen [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands) wie die Schnittstelle oder eine virtuelle Methode.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Durch diese Regel wird eine Methode mit ihrer Basismethode verglichen. Bei dieser handelt es sich entweder um eine Schnittstelle oder um eine virtuelle Methode in einem anderen Typ. Anschließend werden die Linkaufruf mit denen der Schnittstelle bzw. virtuellen Methode verglichen. Ein Verstoß wird gemeldet, wenn die Methode einen Linkaufruf, die Basismethode besitzt und die andere nicht aber.  
  
 Wenn diese Regel verletzt wird, kann ein böswilliger Aufrufer den Linkaufruf umgehen, einfach durch Aufruf der ungesicherten Methode.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, wenden Sie den gleichen Linkaufruf auf die Überschreibungsmethode oder -Implementierung. Wenn dies nicht möglich ist, markieren Sie die Methode mit einer vollständigen Anforderung oder entfernen Sie das Attribut vollständig.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt verschiedene Verstöße gegen diese Regel.  
  
 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben von sicherem Richtlinien](/dotnet/standard/security/secure-coding-guidelines)   
 [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands)