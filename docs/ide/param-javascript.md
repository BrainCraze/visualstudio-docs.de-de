---
title: "&lt;param&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<param>-JavaScript-XML-Tag"
  - "param-JavaScript-XML-Tag"
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;param&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt Dokumentationsinformationen für einen Parameter in einer Funktion oder Methode an.  
  
## Syntax  
  
```  
<param name="parameterName" type="ParameterType"  
    integer="true|false" domElement="true|false"  
    mayBeNull="true|false" elementType="ArrayElementType"  
    elementInteger="true|false" elementDomElement="true|false"  
    elementMayBeNull="true|false" locid="descriptionID"  
    parameterArray="true|false" optional="true|false"  
    value="code">description  
</param>  
```  
  
#### Parameter  
 `name`  
 Erforderlich.  Der Name des Parameters.  
  
 `type`  
 Optional.  Der Datentyp des Parameters.  Als Typ kann eines der folgenden Elemente verwendet werden:  
  
-   Ein ECMAScript\-Sprachentyp in der ECMAScript 5\-Spezifikation, wie `Number` und `Object`  
  
-   Ein DOM\-Objekt, wie `HTMLElement`, `Window` und `Document`  
  
-   Eine JavaScript\-Konstruktorfunktion  
  
 `integer`  
 Optional.  Wenn `type` auf `Number` festgelegt ist, wird angegeben, ob der Parameter eine ganze Zahl ist.  Legen Sie das Attribut auf `true` fest, um anzugeben, dass der Parameter eine ganze Zahl ist; andernfalls ist es auf `false` festzulegen.  Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense\-Informationen bereitzustellen.  
  
 `domElement`  
 Optional.  Dieses Attribut ist veraltet; das Attribut `type` hat Vorrang vor diesem Attribut.  Dieses Attribut gibt an, ob der dokumentierte Parameter ein DOM\-Element ist.  Legen Sie es auf `true` fest, um anzugeben, dass der Parameter ein DOM\-Element ist; andernfalls ist es auf `false` festzulegen.  Wenn das `type`\-Attribut nicht festgelegt ist und `domElement` auf `true` festgelegt wurde, behandelt IntelliSense den dokumentierten Parameter bei Ausführung einer Anweisungsvervollständigung als `HTMLElement`.  
  
 `mayBeNull`  
 Optional.  Gibt an, ob der dokumentierte Parameter auf NULL festgelegt werden kann.  Legen Sie das Attribut auf `true` fest, um anzugeben, dass der Parameter auf NULL festgelegt werden kann; andernfalls ist es auf `false` festzulegen.  Der Standardwert ist `false`.  Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense\-Informationen bereitzustellen.  
  
 `elementType`  
 Optional.  Wenn das `type`\-Attribut `Array` lautet, wird der Typ des Elements im Array angegeben.  
  
 `elementInteger`  
 Optional.  Wenn das `type`\-Attribut `Array` und das `elementType`\-Attribut `Number` lautet, wird angegeben, ob die Elemente im Array ganze Zahlen sind.  Wenn Sie das Attribut auf `true` festlegen, wird angegeben, dass die Elemente im Array ganze Zahlen sind; andernfalls ist das Attribut auf `false` festzulegen.  Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense\-Informationen bereitzustellen.  
  
 `elementDomElement`  
 Optional.  Dieses Attribut ist veraltet; das Attribut `elementType` hat Vorrang vor diesem Attribut.  Wenn das `type`\-Attribut `Array` lautet, wird angegeben, ob die Elemente im Array DOM\-Elemente sind.  Wenn Sie Attribut auf `true` festlegen, wird angegeben, dass die Elemente DOM\-Elemente sind; andernfalls ist das Attribut auf `false` festzulegen.  Wenn das `elementType`\-Attribut nicht festgelegt ist und `elementDomElement` auf `true` festgelegt wird, behandelt IntelliSense jedes Element im Array bei Ausführung einer Anweisungsvervollständigung als `HTMLElement`.  
  
 `elementMayBeNull`  
 Optional.  Wenn das `type`\-Attribut `Array` lautet, wird angegeben, ob die Elemente im Array auf NULL festgelegt werden können.  Wenn Sie das Attribut auf `true` festlegen, wird angegeben, dass die Elemente im Array auf NULL festgelegt werden können; andernfalls ist das Attribut auf `false` festzulegen.  Der Standardwert ist `false`.  Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense\-Informationen bereitzustellen.  
  
 `locid`  
 Optional.  Der Bezeichner für Lokalisierungsinformationen über den Parameter.  Der Bezeichner ist entweder eine Member\-ID, oder er entspricht dem `name`\-Attributwert in einem Meldungsbündel, das von OpenAjax\-Metadaten definiert wird.  Der Bezeichnertyp hängt vom Format ab, das im [\<loc\>](../ide/loc-javascript.md)\-Element angegeben ist.  
  
 `parameterArray`  
 Optional.  Gibt an, ob der dokumentierte Parameter im Funktionsaufruf wiederholt werden kann, ähnlich der Wiederholung von Parametern, die in der `String.format`\-Funktion unterstützt werden.  Legen Sie das Attribut auf `true` fest, um anzugeben, dass der Parameter wiederholt werden kann; andernfalls ist es auf `false` festzulegen.  Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense\-Informationen bereitzustellen.  
  
 `optional`  
 Optional.  Gibt an, ob der dokumentierte Parameter in der aufrufenden Funktion optional ist.  Legen Sie das Attribut auf `true` fest, um anzugeben, dass der Parameter optional ist; andernfalls ist es auf `false` festzulegen.  
  
 `value`  
 Optional.  Gibt den Code an, der anstelle des Funktionscodes für die Verwendung mit IntelliSense ausgewertet werden soll.  Sie können dieses Attribut zur Bereitstellung von Typinformationen verwenden, wenn der Parametertyp nicht definiert ist.  Beispielsweise können Sie `value=’1’` verwenden, um den Parametertyp als Zahl zu behandeln.  
  
 `description`  
 Optional.  Eine Beschreibung des Parameters.  
  
## Hinweise  
 Das einzig erforderliche Attribut ist das `name`\-Attribut.  Alle anderen Attribute sind optional.  
  
 Elemente, die verwendet werden, um Funktionen, wie etwa [\<summary\>](../ide/summary-javascript.md), [\<param\>](../ide/param-javascript.md) und [\<returns\>](../ide/returns-javascript.md), mit Anmerkungen zu versehen, müssen vor allen Anweisungen in den Funktionstext eingefügt werden.  
  
 Wenn es mehrere `<param>`\-Elemente gibt, die denselben Namen aufweisen, wird eines der `<param>`\-Elemente verwendet, und die redundanten Elemente werden ignoriert.  Das Verhalten, das bestimmt, welches Element verwendet wird, ist nicht definiert.  Wenn `name` auf einen nicht vorhandenen Parameter verweist, wird das Element ignoriert.  
  
## Beispiel  
 Im folgenden Codebeispiel wird die Verwendung des Elements `<param>` veranschaulicht.  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
// Uses of <param> with the value attribute.  
  
function calculate(a) {  
    /// <param name='a' value='1'/>  
    a.    // Completion list for a Number.  
}  
  
function calculate(a) {  
    /// <param name='a' value='{x:0,y:0}'/>  
    a.    // x and y appear in the completion list.  
}  
  
```  
  
## Siehe auch  
 [XML\-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md)