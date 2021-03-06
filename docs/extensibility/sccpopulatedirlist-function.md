---
title: SccPopulateDirList Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5315f3156f71310c92069ec3743232e98818b9a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList-Funktion
Diese Funktion wird bestimmt, welche Verzeichnisse und Dateien (optional), in der quellcodeverwaltung gespeichert sind, ist eine Liste von Verzeichnissen, um zu überprüfen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 "pContext"  
 [in] Der Datenquellen-Steuerelement-Plug-in Kontextzeiger.  
  
 nDirs  
 [in] Anzahl der Verzeichnispfade, in der `lpDirPaths` Array.  
  
 lpDirPaths  
 [in] Array der Verzeichnispfade, um zu überprüfen.  
  
 pfnPopulate  
 [in] Rückruffunktion für jedes Verzeichnispfad und (optional) Name der Datei im `lpDirPaths` (finden Sie unter [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Einzelheiten).  
  
 pvCallerData  
 [in] Wert, der unverändert an die Rückruffunktion übergeben werden.  
  
 fOptions  
 [in] Eine Kombination von Werten, die steuern, wie die Verzeichnisse verarbeitet werden (siehe Abschnitt "PopulateDirList Flags" [Bitflags, die von bestimmten Befehlen verwendet](../extensibility/bitflags-used-by-specific-commands.md) mögliche Werte).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Der Vorgang erfolgreich abgeschlossen.|  
|SCC_E_UNKNOWNERROR|Es ist ein Fehler aufgetreten.|  
  
## <a name="remarks"></a>Hinweise  
 Nur die Verzeichnisse und (optional) Dateinamen, die tatsächlich in den Quellcodeverwaltungs-Repository befinden, werden an die Rückruffunktion übergeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [Bitflags, die von bestimmten Befehlen verwendet](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Fehlercodes](../extensibility/error-codes.md)