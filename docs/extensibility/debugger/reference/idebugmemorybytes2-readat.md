---
title: IDebugMemoryBytes2::ReadAt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 612a065286723e3c2b68a9ce5bd31c850d030959
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Liest eine Folge von Bytes, beginnend an einer angegebenen Position.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```csharp  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pStartContext`  
 [in] Die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Objekt, das angibt, wo Sie beginnen, Lesen von Bytes.  
  
 `dwCount`  
 [in] Die Anzahl der zu lesenden Bytes. Außerdem gibt die Länge des der `rgbMemory` Array.  
  
 `rgbMemory`  
 [in, out] Array mit der Bytes gefüllt, die tatsächlich gelesen werden.  
  
 `pdwRead`  
 [out] Gibt die Anzahl der tatsächlich gelesenen zusammenhängenden Bytes zurück.  
  
 `pdwUnreadable`  
 [in, out] Gibt die Anzahl von Bytes nicht gelesen werden. Möglicherweise ein null-Wert, wenn der Client die Anzahl der Bytes unlesbar lehnt weitere Benachrichtigungsaufrufe ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn 100 Byte angefordert werden und die ersten 50 lesbar sind, die nächste 20 nicht lesbar sind und die verbleibenden 30 lesbar sind, gibt diese Methode zurück:  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 In diesem Fall da `*pdwRead + *pdwUnreadable < dwCount`, der Aufrufer muss einen zusätzlichen Aufruf, lesen die verbleibenden 30 Byte ist der ursprüngliche 100 angefordert, und die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Objekt übergeben, der `pStartContext` Parameter erweitert werden muss von 70.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)