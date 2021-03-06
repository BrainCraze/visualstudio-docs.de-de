---
title: "/LCID („devenv.exe“) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bdc04655ccfc8ca5f6c1e45e4378f15221b99f4c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
Legt die Standardsprache für Text, Währungen und andere Werte in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
devenv {/LCID|/l} LocaleID  
```  
  
## <a name="arguments"></a>Argumente  
 `LocaleID`  
 Erforderlich. Die LCID (Gebietsschema-ID) der Sprache, die Sie angeben  
  
## <a name="remarks"></a>Hinweise  
 Lädt die IDE und legt die natürliche Standardsprache für die Umgebung fest. Diese Änderung wird zwischen den Sitzungen beibehalten und wird im Bereich **Internationale Einstellungen** der Optionen **Umgebung** im Dialogfeld **Optionen** in der IDE angezeigt.  
  
 Wenn die angegebene Sprache im System des Benutzers nicht vorhanden ist, wird der /LCID-Schalter ignoriert.  
  
 In der folgenden Tabelle sind die LCIDs der von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützten Sprachen aufgeführt.  
  
|Sprache|LCID|  
|--------------|----------|  
|Chinesisch (vereinfacht)|2052|  
|Chinesisch (traditionell)|1028|  
|Englisch|1033|  
|Französisch|1036|  
|Deutsch|1031|  
|Italienisch|1040|  
|Japanisch|1041|  
|Koreanisch|1042|  
|Spanisch|3082|  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird die IDE mit englischen Ressourcenzeichenfolgen geladen.  
  
```  
devenv /LCID 1033  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [Internationale Einstellungen, Umgebung, Dialogfeld „Optionen“](../../ide/reference/international-settings-environment-options-dialog-box.md)   
 [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md)