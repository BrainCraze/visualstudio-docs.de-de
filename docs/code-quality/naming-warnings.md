---
title: "Benennungswarnungen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.namingrules"
helpviewer_keywords: 
  - "Analysen für verwalteten Code (Warnungen), Benennungswarnungen"
  - "Benennungswarnungen"
  - "Warnungen, Benennung"
ms.assetid: f97223ce-1d39-4134-81c9-fff2c75d979b
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# Benennungswarnungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Namenswarnungen unterstützen die Einhaltung der Namenskonventionen der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Entwurfsrichtlinien.  
  
## In diesem Abschnitt  
  
|Regel|**Beschreibung**|  
|-----------|----------------------|  
|[CA1700: Enumerationswerte nicht mit "Reserviert" benennen](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Bei dieser Regel wird vorausgesetzt, dass Enumerationsmember mit einem Namen, der "reserved" enthält, derzeit nicht verwendet werden, sondern Platzhalter sind, die in einer künftigen Version umbenannt oder entfernt werden sollen.  Das Umbenennen oder Entfernen eines Members ist eine unterbrechende Änderung.|  
|[CA1713: Ereignisse sollten kein Before\- oder After\-Präfix aufweisen](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|Der Name eines Ereignisses beginnt mit "Before" oder "After".  Um verwandte Ereignisse zu benennen, die in einer bestimmten Reihenfolge ausgelöst werden, verwenden Sie die Gegenwarts\- oder Vergangenheitsform, um ihre relative Position in der Aktionsfolge anzugeben.|  
|[CA1714: Flags\-Enumerationen sollten Pluralnamen aufweisen](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Eine öffentliche Enumeration verfügt über das System.FlagsAttribute\-Attribut, und der Name endet nicht in der Pluralform \("s"\).  Die Namen von mit FlagsAttribute markierten Typen stehen im Plural, da das Attribut angibt, dass mehr als ein Wert festgelegt werden kann.|  
|[CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|Der Name eines extern sichtbaren Bezeichners enthält mindestens ein Wort, das von der Rechtschreibprüfung aus der Microsoft\-Bibliothek nicht erkannt wird.|  
|[CA1708: Bezeichner sollten sich nicht nur durch die Groß\-\/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Bezeichner für Namespaces, Typen, Member und Parameter dürfen sich nicht nur durch die Groß\-\/Kleinschreibung unterscheiden, weil Sprachen, die auf die Common Language Runtime abzielen, nicht zwischen Groß\- und Kleinschreibung unterscheiden müssen.|  
|[CA1715: Bezeichner sollten ein korrektes Präfix aufweisen](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|Der Name einer extern sichtbaren Schnittstelle beginnt nicht mit dem Großbuchstaben "I".  Der Name eines generischen Typparameters für einen extern sichtbaren Typ oder eine extern sichtbare Methode beginnt nicht mit dem Großbuchstaben "T".|  
|[CA1720: Bezeichner dürfen keine Typnamen enthalten](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|Der Name eines Parameters in einem extern sichtbaren Member enthält einen Datentypnamen, oder der Name eines extern sichtbaren Members enthält einen sprachspezifischen Datentypnamen.|  
|[CA1722: Bezeichner sollten kein falsches Präfix aufweisen](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Gemäß der Konvention verfügen nur bestimmte Programmierelemente über Namen, die mit einem bestimmten Präfix anfangen.|  
|[CA1711: Bezeichner sollten kein falsches Suffix aufweisen](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Nur die Namen von Typen, die bestimmte Basistypen erweitern oder bestimmte Schnittstellen bzw. Typen implementieren, die von diesen Typen abgeleitet werden, sollten stets mit bestimmten reservierten Suffixen enden.  Für andere Typnamen sollten diese reservierten Suffixe nicht verwendet werden.|  
|[CA1717: Nur FlagsAttribute\-Enumerationen sollten Pluralnamen aufweisen](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|Gemäß den Benennungskonventionen gibt ein Pluralname für eine Enumeration an, dass für die Enumeration mehrere Werte gleichzeitig angegeben werden können.|  
|[CA1725: Parameternamen sollten mit der Basisdeklaration übereinstimmen](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|Die konsistente Benennung von Parametern in einer Überschreibungshierarchie erhöht die Verwendbarkeit von Methodenüberschreibungen.  Ein Parametername in einer abgeleiteten Methode, der vom Namen in der Basisdeklaration abweicht, kann zu Unklarheiten dahingehend führen, ob es sich bei der Methode um eine Überschreibung der Basismethode oder eine neue Überladung der Methode handelt.|  
|[CA1719: Parameternamen sollten nicht mit Membernamen übereinstimmen](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Ein Parametername sollte die Bedeutung eines Parameters vermitteln, und ein Membername sollte die Bedeutung eines Members vermitteln.  Diese stimmen in der Regel nicht überein.  Wenn ein Parameter mit dem Namen des zugehörigen Members benannt wird, ist dies nicht intuitiv, und es erschwert die Verwendung der Bibliothek.|  
|[CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|Jeder Begriff in der Ressourcenzeichenfolge wird anhand der Groß\-\/Kleinschreibung in einzelne Token unterteilt.  Jede zusammenhängende Kombination aus zwei Token wird durch die Rechtschreibprüfung aus der Microsoft\-Bibliothek überprüft.  Wenn der Begriff erkannt wird, erzeugt er einen Regelverstoß.|  
|[CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Eine Ressourcenzeichenfolge enthält mindestens ein Wort, das von der Rechtschreibprüfung aus der Microsoft\-Bibliothek nicht erkannt wird.|  
|[CA1724: Typnamen sollten nicht mit Namespaces übereinstimmen](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|Typnamen dürfen nicht mit den Namen von in der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Klassenbibliothek definierten Namespaces übereinstimmen.  Durch einen Verstoß gegen diese Regel kann die Verwendbarkeit der Bibliothek eingeschränkt werden.|  
|[CA1707: Bezeichner sollten keine Unterstriche enthalten](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Bezeichnernamen dürfen keinen Unterstrich \(\_\) enthalten.  Namespaces, Typen, Member und Parameter werden von dieser Regel überprüft.|  
|[CA1721: Eigenschaftennamen sollten nicht mit Get\-Methoden übereinstimmen](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|Der Name eines öffentlichen oder geschützten Members beginnt mit "Get" und stimmt in anderer Hinsicht mit dem Namen einer öffentlichen oder geschützten Eigenschaft überein. "Get" \- Methoden und \- Eigenschaften sollten über Namen verfügen, aus denen ihre Funktion eindeutig hervorgeht.|  
|[CA1716: Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Ein Namespacename oder ein Typname stimmt mit einem reservierten Schlüsselwort in einer Programmiersprache überein.  Bezeichner für Namespaces und Typen dürfen nicht mit Schlüsselwörtern übereinstimmen, die in Programmiersprachen für die Common Language Runtime definiert sind.|  
|[CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md)|Der Name eines extern sichtbaren Bezeichners schließt einen Begriff ein, für den ein alternativer, bevorzugter Begriff vorhanden ist.  Der Name kann auch den Begriff "Flag" oder "Flags" enthalten.|  
|[CA1709: Bei Bezeichnern sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Gemäß der Konvention werden Parameternamen in Kamel\-Schreibweise verfasst, für Namespace\-, Typ\- und Membernamen wird die Pascal\-Schreibweise verwendet.|  
|[CA1702: Bei zusammengesetzten Begriffen sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|Der Name eines Bezeichners enthält mehrere Begriffe, und mindestens einer der Begriffe ist anscheinend ein zusammengesetztes Wort mit falscher Groß\-\/Kleinschreibung.|  
|[CA1712: Keine Typnamen als Präfixe für Enumerationswerte verwenden](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|Den Namen von Enumationsmembern wird der Typname nicht als Präfix vorangestellt, weil die Typinformationen von den Entwicklungswerkzeugen bereitgestellt werden sollen.|  
|[CA1710: Bezeichner sollten ein richtiges Suffix aufweisen](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|Die Namen von Typen, die bestimmte Basistypen erweitern oder bestimmte Schnittstellen implementieren, bzw. von diesen Typen abgeleitete Typen weisen stets ein Suffix auf, das mit dem Basistyp oder der Schnittstelle verknüpft ist.|