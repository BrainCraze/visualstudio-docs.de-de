---
title: "Verwenden von regulären Ausdrücken in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vsregularexpressionhelp
- vs.regularexpressionhelp
- vs.wildcardsbuilder
- vs.netregularexpressionhelp
- vs.wildcards
helpviewer_keywords:
- regular expressions [Visual Studio]
- regular expressions
- Visual Studio, regular expressions
ms.assetid: 718a617d-0e05-47e1-a218-9746971527f4
caps.latest.revision: 53
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 6d7266c35746fa4413ffd4ce058b1acbe9229af2
ms.contentlocale: de-de
ms.lasthandoff: 02/22/2017

---
# <a name="using-regular-expressions-in-visual-studio"></a>Verwenden von regulären Ausdrücken in Visual Studio
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verwendet reguläre Ausdrücke in .NET Framework zum Suchen und Ersetzen von Text. Weitere Informationen zu regulären Ausdrücken von .NET finden Sie unter [Reguläre Ausdrücke von .NET Framework](http://msdn.microsoft.com/Library/521b3f6d-f869-42e1-93e5-158c54a6895d).  
  
 Vor Visual Studio 2012 verwendete Visual Studio benutzerdefinierte Syntax für reguläre Ausdrücke in den Fenstern "Suchen" und "Ersetzen". Unter [Visual Studio Regular Expression Conversions (Visual Studio-Konvertierungen mit regulären Ausdrücken)](https://msdn.microsoft.com/en-us/library/2k3te2cs\(v=vs.110\).aspx) finden Sie eine Erklärung, wie einige der häufiger verwendeten benutzerdefinierten regulären Ausdruckssymbole in die Versionen von .NET konvertiert werden.  
  
> [!TIP]
>  In Windows-Betriebssystemen enden die meisten Zeilen auf "\r\n" (ein Wagenrücklaufzeichen gefolgt von einer neuen Zeile). Diese Zeichen sind nicht sichtbar, aber im Editor vorhanden und werden an den .NET-Dienst regulärer Ausdrücke übergeben.  
  
> [!TIP]
>  Weitere Informationen zu regulären Ausdrücken, die in Ersetzungsmustern verwendet werden, finden Sie unter [Ersetzungen in regulären Ausdrücken](http://msdn.microsoft.com/Library/d1f52431-1c7d-4dc6-8792-6b988256892e). Um eine nummerierte Erfassungsgruppe zu verwenden, lautet die Syntax zum Festlegen der nummerierten Gruppe `$1` und zum Festlegen der betreffenden Gruppe `(x)`. In der folgenden Zeichenfolge findet der gruppierte reguläre Ausdruck `(\d)([a-z])` beispielsweise vier Übereinstimmungen: **1a 2b 3c 4d**. Die Ersetzungszeichenfolge `z$1` konvertiert diese Zeichenfolge in **z1 z2 z3 z4**.  
  
## <a name="regular-expressions-in-visual-studio"></a>Reguläre Ausdrücke in Visual Studio  
 Hier einige Beispiele  
  
|Zweck|Ausdruck|Beispiel|  
|-------------|----------------|-------------|  
|Übereinstimmung mit beliebigem Zeichen (mit Ausnahme des Zeilenumbruchs)|.|`a.o` findet „aro“ in „around“ und „abo“ in „about“, jedoch nicht „acro“ in „across“.|  
|Übereinstimmung mit keinem oder mehreren Vorkommen des vorhergehenden Ausdrucks (wobei die Übereinstimmung möglichst viele Zeichen umfasst).|*|`a*r` findet „r“ in „rack“, „ar“ in „ark“ und „aar“ in „aardvark“.|  
|Keine oder häufigere Übereinstimmung mit beliebigem Zeichen (Platzhalter *)|.*|c.*e findet "cke" in "racket", "comme" in "comment" und "code" in "code"|  
|Übereinstimmung mit einem oder mehreren Vorkommen des vorhergehenden Ausdrucks (wobei die Übereinstimmung möglichst viele Zeichen umfasst).|+|`e.+e` findet „eede“ in „feeder“, jedoch nicht „ee“.|  
|Ein- oder mehrmalige Übereinstimmung mit beliebigem Zeichen (Platzhalter ?)|.+|"e.+e" findet "eede" in "feeder", jedoch nicht "ee".|  
|Übereinstimmung mit keinem oder mehreren Vorkommen des vorhergehenden Ausdrucks (wobei die Übereinstimmung möglichst wenig Zeichen umfasst).|*?|`e.*?e` findet „ee“ in „feeder“, jedoch nicht „eede“.|  
|Übereinstimmung mit einem oder mehreren Vorkommen des vorhergehenden Ausdrucks (wobei die Übereinstimmung möglichst wenig Zeichen umfasst).|+?|`e.+?e` findet „ente“ und „erprise“ in „enterprise“, jedoch nicht das vollständige Wort „enterprise“.|  
|Verankert die übereinstimmende Zeichenfolge am Anfang einer Zeile oder Zeichenfolge.|^|`^car` findet das Wort „car“ nur, wenn es am Anfang einer Zeile angezeigt wird.|  
|Verankert die übereinstimmende Zeichenfolge am Ende einer Zeile|\r?$|`End\r?$` findet „end“ nur, wenn es am Ende einer Zeile angezeigt wird.|  
|Übereinstimmung mit beliebigem Zeichen in einem Satz|[abc]|`b[abc]` findet „ba“, „bb“ und „bc“.|  
|Übereinstimmung mit beliebigem Zeichen in einem Bereich von Zeichen|[a-f]|`be[n-t]` findet „bet“ in „between“, „ben“ in „beneath“ und „bes“ in „beside“, jedoch nicht „bel“ in „below“.|  
|Erfassung und implizite Nummerierung des in Klammern befindlichen Ausdrucks|()|`([a-z])X\1` findet „aXa“ und „bXb“, jedoch nicht „aXb“. ". "\1" bezieht sich auf die erste Ausdrucksgruppe "[a-z]".|  
|Aufheben der Gültigkeit einer Übereinstimmung|(?!abc)|`real (?!ity)` findet „real“ in „realty“ und „really“, jedoch nicht in „reality“. Findet außerdem das zweite "real" (jedoch nicht das erste "real") in "realityreal".|  
|Übereinstimmung mit beliebigem Zeichen, das sich nicht in einem angegebenen Satz von Zeichen befindet|[^abc]|`be[^n-t]` findet „bef“ in „before“, „beh“ in „behind“ und „bel“ in „below“, jedoch nicht „beneath“.|  
|Übereinstimmung mit dem Ausdruck vor oder nach dem Symbol.|&#124;|`(sponge&#124;mud) bath` findet „sponge bath“ und „mud bath“.|  
|Versehen des Zeichens hinter dem umgekehrten Schrägstrich mit Escapezeichen|\|`\^` findet das Zeichen „^“.|  
|Angeben der Anzahl von Vorkommen des vorherigen Zeichens oder der Gruppe|{x}, wobei x die Anzahl von Vorkommen ist|`x(ab){2}x` findet „xababx“ und `x(ab){2,3}x` findet „xababx“ und „xabababx“, jedoch nicht „xababababx“.|  
|Übereinstimmung von Text in einer Unicode-Zeichenklasse, wobei "X" der Unicode-Zahl entspricht. Weitere Informationen zu Unicode-Zeichenklassen finden Sie unter<br /><br /> [Unicode Standard 5.2 Character Properties (Unicode-Standard 5.2-Zeicheneigenschaften)](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}|`\p{Lu}` findet „T“ und „D“ in „Thomas Doe“.|  
|Übereinstimmung mit einer Wortgrenze|`\b` (Außerhalb einer Zeichenklasse gibt „\b“ eine Wortgrenze an und innerhalb einer Zeichenklasse gibt es eine Rücktaste an.)|`\bin` findet „in“ in „inside“, jedoch nicht „pinto“.|  
|Übereinstimmung mit Zeilenumbruch (d. h. ein Wagenrücklaufzeichen gefolgt von einer neuen Zeile).|\r?\n|`End\r?\nBegin` findet „End“ und „Begin“ nur, wenn „End“ als letzte Zeichenfolge in einer Zeile vorkommt und „Begin“ als erste Zeichenfolge in der nächsten Zeile.|  
|Übereinstimmung mit beliebigem alphanumerischen Zeichen|\w|`a\wd` findet „add“ und „a1d“, jedoch nicht „a d“.|  
|Übereinstimmung mit beliebigem Leerzeichen.|(?([^\r\n])\s)|`Public\sInterface` findet den Begriff „Public Interface“.|  
|Übereinstimmung mit beliebigem numerischen Zeichen|\d|`\d` findet „3“ in „3456“, „2“ in „23“ und „1“ in „1“.|  
|Übereinstimmung mit einem Unicode-Zeichen|"\uXXXX", wobei "XXXX"den Unicode-Zeichenwert angibt.|`\u0065` findet das Zeichen „e“.|  
|Übereinstimmung mit einem Bezeichner|\b(_\w+&#124;[\w-[0-9\_]]\w*)\b|Findet "type1", jedoch nicht &type1" oder "#define".|  
|Übereinstimmung mit einer Zeichenfolge in Anführungszeichen|((\\".+?\\")&#124;('.+?'))|Übereinstimmung mit einer beliebigen Zeichenfolge in einfachen oder doppelten Anführungszeichen|  
|Übereinstimmung mit einer Hexadezimalzahl|\b0[xX]([0-9a-fA-F]\)\b|Findet "0xc67f", jedoch nicht "0xc67fc67f".|  
|Übereinstimmung mit ganzen Zahlen und Dezimalzahlen|\b[0-9]*\\.\*[0-9]+\b|Findet "1.333".|  
  
## <a name="see-also"></a>Siehe auch  
 [Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md)