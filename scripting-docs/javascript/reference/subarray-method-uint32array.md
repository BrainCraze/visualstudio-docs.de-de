---
title: Subarray-Methode (Uint32Array) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4c183208-12ec-4051-bf0f-a4f7c112cea1
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1c76c5c83bcb1e43b51b4f49618e72311d5df86
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-uint32array"></a>subarray-Methode (Uint32Array)
Ruft eine neue Uint32Array-Ansicht des der [ArrayBuffer-Objekt](../../javascript/reference/arraybuffer-object.md) -Speichers für dieses Array ab und gibt die erste und letzte Member des Unterarrays.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
var newUint32Array = uint32Array.subarray(begin, end);  
```  
  
## <a name="parameters"></a>Parameter  
 `newUint32Array`  
 Das von dieser Methode zurückgegebene Unterarray.  
  
 `begin`  
 Der Index des Anfangs des Arrays.  
  
 `end`  
 Der Index des Endes des Arrays. Dies ist nicht eindeutig.  
  
## <a name="remarks"></a>Hinweise  
 Wenn entweder der `begin` oder das `end` negativ ist, wird auf einen Index am Ende statt am Beginn des Arrays verwiesen. Wenn `end` nicht angegeben wird, enthält das Unterarray alle Elemente vom `begin` bis zum Ende des typisierten Arrays. Der durch die `begin`s- und `end`werte festgelegte Bereich wird für das aktuelle Array an den gültigen Indexbereich geklammert. Wenn die berechnete Länge des neuen TypedArrays negativ ist, wird sie an Null geklammert. Das zurückgegebene Array hat denselben Typ wie das Array, auf dem diese Methode aufgerufen wird.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie ein Subarray mit der Länge von zwei Elementen abgerufen wird, beginnend mit dem ersten Element des Arrays.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var intArr = new Uint32Array(buffer.byteLength / 4);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]