---
title: 'Idialoadcallback2:: Restrictreferencepathaccess | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictReferencePathAccess method
ms.assetid: e20cb45c-0360-4ff0-a92c-b1b6f76d6e85
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2240fe4b0e68007bd298801fc6174d54204ffff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idialoadcallback2restrictreferencepathaccess"></a>IDiaLoadCallback2::RestrictReferencePathAccess
Bestimmt, ob die Suche nach einer PDB-Datei im Pfad zulässig ist, wo sich die .exe-Datei befindet.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT RestrictReferencePathAccess();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Alle Rückgabecode außer `S_OK` um zu verhindern, Suche nach einer PDB-Datei im Pfad, in dem die .exe-Datei befindet.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)