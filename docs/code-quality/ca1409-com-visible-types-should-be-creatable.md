---
title: 'CA1409: Für Com sichtbare Typen sollten erstellbar sein | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f8ddd3d9a1a239f19758f1bdb9ab289bee3a8f6d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: Für COM sichtbare Typen müssen erstellt werden können
|||  
|-|-|  
|TypeName|ComVisibleTypesShouldBeCreatable|  
|CheckId|CA1409|  
|Kategorie|Microsoft.Interoperability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Ein Verweistyp, der speziell für Component Object Model (COM) als sichtbar markiert ist, enthält einen öffentlichen parametrisierten Konstruktor jedoch enthält keinen öffentlichen (parameterlosen) Standardkonstruktor.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Ein Typ ohne einen öffentlichen Standardkonstruktor kann nicht durch COM-Clients erstellt werden. Der Typ kann jedoch immer noch durch COM-Clients zugegriffen werden, wenn andere Weise erstellen Sie den Typ und übergibt ihn dann an dem Client (z. B. durch den Rückgabewert eines Methodenaufrufs) verfügbar ist.  
  
 Die Regel ignoriert die von der abgeleiteten Typen <xref:System.Delegate?displayProperty=fullName>.  
  
 Standardmäßig sind die folgenden für COM sichtbar: Assemblys, öffentliche Typen, öffentliche Instanzmember in öffentlichen Typen und alle Member von öffentlichen Werttypen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie einen öffentlichen Standardkonstruktor hinzu, oder entfernen Sie die <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> vom Typ.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn andere Möglichkeiten zum Erstellen und übergeben das Objekt an dem COM-Client bereitgestellt werden.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Qualifizieren von .NET-Typen für die Interoperation](/dotnet/framework/interop/qualifying-net-types-for-interoperation)   
 [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)