---
title: 'CA2238: Serialisierungsmethoden korrekt implementieren | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 615d465ad6e8846c1960c45b0a60e99f5a7f9bfd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238: Serialisierungsmethoden korrekt implementieren
|||  
|-|-|  
|TypeName|ImplementSerializationMethodsCorrectly|  
|CheckId|CA2238|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Unterbrechend – Wenn die Methode außerhalb der Assembly sichtbar ist.<br /><br /> Nicht unterbrechend – Wenn die Methode nicht außerhalb der Assembly sichtbar ist.|  
  
## <a name="cause"></a>Ursache  
 Eine Methode, die ein Serialisierungsereignis behandelt, verfügt nicht über die richtige Signatur, den richtigen Rückgabetyp oder die richtige Sichtbarkeit.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Eine Methode ist einen Ereignishandler für die Serialisierung gekennzeichnet, indem Sie eine der folgenden Ereignis-Serialisierungsattribute anwenden:  
  
-   <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>  
  
 Ereignishandler für die Serialisierung nehmen einen einzelnen Parameter vom Typ <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, den Rückgabetyp `void`, und `private` Sichtbarkeit.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Signatur, den Rückgabetyp oder die Sichtbarkeit der Ereignishandler für die Serialisierung.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt ordnungsgemäß deklarierte Serialisierung Ereignishandler.  
  
 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/VisualBasic/ca2238-implement-serialization-methods-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/CSharp/ca2238-implement-serialization-methods-correctly_1.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA2236: Basisklassenmethoden auf ISerializable-Typen aufrufen](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: ISerializable ordnungsgemäß implementieren](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2235: Alle nicht serialisierbaren Felder markieren](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Markieren von ISerializable-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Deserialisierungsmethoden für optionale Felder angeben](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)