---
title: "IEnumDebugProcesses2::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugProcesses2::Skip"
helpviewer_keywords: 
  - "IEnumDebugProcesses2::Skip"
ms.assetid: b9e9d888-189b-44c4-a65f-e91612458898
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugProcesses2::Skip
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Überspringt die angegebene Anzahl von Elementen.  
  
## Syntax  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```c#  
int Skip(  
   uint celt  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\]  Die Anzahl der zu überspringenden Elemente.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` , wenn `celt` größer als die Anzahl der verbleibenden Elemente zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Wenn `celt` einen Wert angibt, der von verbleibenden Elemente größer als die Anzahl ist, wird die Enumeration auf das Ende festgelegt und `S_FALSE` wird zurückgegeben.  
  
## Siehe auch  
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)