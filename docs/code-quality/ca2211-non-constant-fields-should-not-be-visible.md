---
title: 'CA2211: Nicht konstante Felder sollten nicht sichtbar sein | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9d2e91cce74877a4160646db829ba9208410b403
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: Nicht konstante Felder sollten nicht sichtbar sein
|||  
|-|-|  
|TypeName|NonConstantFieldsShouldNotBeVisible|  
|CheckId|CA2211|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein öffentlicher oder geschütztes statisches Feld ist nicht konstant noch schreibgeschützt ist.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Statische Felder, die weder konstant noch schreibgeschützt sind, sind nicht threadsicher. Zugriff auf ein solches Feld muss sorgfältig kontrolliert werden und erfordert fortgeschrittene Programmiertechniken zur Synchronisierung des Zugriffs auf das Klassenobjekt. Da hierbei handelt es sich nur schwer Fähigkeiten, um weitere Informationen und Master "und" Testen ein solches Objekt stellt eine eigene Herausforderungen, werden am besten statische Felder verwendet, zum Speichern von Daten, die nicht geändert wird. Diese Regel gilt für Bibliotheken; Anwendungen sollten keine Felder verfügbar machen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie das statische Feld konstant oder schreibgeschützt. Wenn dies nicht möglich ist, gestalten Sie den Typ um einen alternativen Mechanismus wie z. B. eine Thread-sichere-Eigenschaft verwenden, die threadsicheren Zugriff auf das zugrunde liegende Feld verwaltet. Beachten Sie, dass Probleme, z. B. Sperrungskonflikte und Deadlocks die Leistung und das Verhalten der Bibliothek auswirken können.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig auf eine Warnung dieser Regel zu unterdrücken, wenn Sie eine Anwendung entwickeln und haben daher Vollzugriff auf den Zugriff auf den Typ, der das statische Feld enthält. Bibliothek-Designer sollte eine Warnung dieser Regel nicht unterdrückt werden; nicht konstante statische Felder verwenden, kann die Bibliothek, die für Entwickler schwer ordnungsgemäße Verwendung vornehmen.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ, der mit dieser Regel verletzt.  
  
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]