---
title: User (VSPerfCmd) | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 36d9b6cf0f3b80916b8cc02279c2397f2f3d075b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="user-vsperfcmd"></a>User (VSPerfCmd)
Die **User**-Option gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des profilierten Prozesses ist. Diese Option ist nur erforderlich, wenn der Prozess als Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist. Der Prozessbesitzer ist auf der Registerkarte „Prozesse“ in der Spalte „Benutzername“ des Windows Task-Managers aufgeführt.  
  
 Die **User**-Option kann nur in einer Befehlszeile angegeben werden, die auch die **Start**-Option enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### <a name="parameters"></a>Parameter  
 `Domain`  
 Der Name der Domäne des Benutzers.  
  
 `UserName`  
 Der Name des Benutzers.  
  
## <a name="required-options"></a>Erforderliche Optionen  
 Die Option **User** kann nur mit der Option **Start** verwendet werden.  
  
 **Start:** `Method`  
 Initialisiert den Profiler mit der angegebenen Profilerstellungsmethode.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der **User**-Option gezeigt.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Erstellen von Dienstprofilen](../profiling/command-line-profiling-of-services.md)