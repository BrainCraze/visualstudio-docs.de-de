---
title: ToggleHUD | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8839e41048a68adf09380e6fa428087299a12801
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="togglehud"></a>ToggleHUD
Schaltet die Grafikdiagnose *HUD* (Head-Up-Display) überlagern, ein- oder ausschalten.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Hinweise  
 Das Grafikdiagnose-HUD wird in der linken oberen Ecke der App angezeigt, die unter der Grafikdiagnose ausgeführt wird. Es zeigt Laufzeitinformationen über die app und zur Erfassung von Grafikinformationen sowie Meldungen, die durch den Aufruf hinzugefügt werden die [AddMessage](addmessage.md) Memberfunktion.  
  
 Um die HUD ein-oder auszuschalten, müssen Sie nicht aktiv Grafikinformationen erfasst werden – d. h., es kann ein-/ausgeschaltet werden durch eine Instanz von der `VsgDbg` -Klasse, aber die [Init](init.md) keinen Member-Funktion zuerst aufgerufen werden.