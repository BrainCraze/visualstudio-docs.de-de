---
title: CV_access_e | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1cd11b7d72e84eb773a833414bb6c14716827cf9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="cvaccesse"></a>CV_access_e
Gibt den Bereich der Sichtbarkeit (Zugriffsebene) von Memberfunktionen und-Variablen.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>Elements  
 CV_private  
 Element verfügt über privaten Zugriff.  
  
 CV_protected  
 Member hat den Zugriff geschützt werden.  
  
 CV_public  
 Element verfügt über öffentlichen Zugriff.  
  
## <a name="remarks"></a>Hinweise  
 Die `friend` Zugriffsspezifizierer ist hier nicht eingeschlossen, da sie in der Regel von nicht-Memberfunktionen verwendet wird, die Zugriff auf private und geschützte Elemente der Klasse haben. Verwenden der [idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) Methode zum Suchen von Symbolen mit `SymTagFriend` Zugriff.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasymbol:: Get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)