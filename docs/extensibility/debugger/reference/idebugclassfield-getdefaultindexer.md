---
title: IDebugClassField::GetDefaultIndexer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f16f4dc94a5019fa66425f55c8f7706db566db9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
Ruft den Namen der Standardindexer ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetDefaultIndexer(   
   BSTR* pbstrIndexer  
);  
```  
  
```csharp  
int GetDefaultIndexer(  
   out string pbstrIndexer  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrIndexer`  
 [out] Gibt eine Zeichenfolge, die mit dem Namen des der Standardindexer zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Bei Erfolg S_OK zurück oder gibt S_FALSE zurück, wenn keine Standardindexer vorhanden ist. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der Standardindexer einer Klasse ist die Eigenschaft mit der Kennzeichnung der `Default` -Eigenschaft für das Array greift auf. Dies bezieht sich auf [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]. Hier ist ein Beispiel für einen Standardindexer deklariert [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] und wie diese verwendet werden.  
  
```vb  
Imports System.Collections;  
  
Public Class Class1  
    Private myList as Hashtable  
  
    Default Public Property Item(ByVal Index As Integer) As Integer  
        Get  
            Return CType(List(Index), Integer)  
        End Get  
        Set(ByVal Value As Integer)  
            List(Index) = Value  
        End Set  
    End Property  
End Class  
  
Function GetItem(Index as Integer) as Integer  
    Dim classList as Class1 = new Class1  
    Dim value as Integer  
  
    ' Access array through default indexer  
    value = classList(2)  
  
    ' Access array through explicit property  
    value = classList.Item(2)  
  
    Return value  
End Function  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)