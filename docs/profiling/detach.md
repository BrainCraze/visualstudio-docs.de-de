---
title: Trennen | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 02ff1bd3e3db51a444d371e2e803f77ef1429676
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="detach"></a>Trennen
Die VSPerfCmd.exe-Option **Detach** (Trennen) trennt die Verbindung zwischen dem Profiler und den angegebenen Prozessen oder allen Prozessen, falls keine angegeben sind. Die Profilerstellung muss über die Samplingmethode initialisiert worden sein.  
  
 Die Profilerstellung, die entweder mit der Option **Launch** (Starten) oder **Attach** (Anfügen) gestartet wurde, kann nun mit **Detach** getrennt werden. Der Profiler kann mithilfe nachfolgender **Attach**-Befehle erneut angefügt werden.  
  
 **Detach** schließt die Datendatei der Profilerstellung nicht. Verwenden Sie die Option **Shutdown**, um die Profilerstellung zu beenden und die Datendatei zu schließen.  
  
> [!NOTE]
>  Wenn die Option **CrossSession** für die Option **Start** angegeben wurde, müssen alle Aufrufe von **VSPerfCmd /Attach** oder **VSPerfCmd /Detach** auch **CrossSession** angeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]  
```  
  
#### <a name="parameters"></a>Parameter  
 `PIDs|ProcessNames`  
 `PID`: der numerische Systembezeichner von einem oder mehreren Prozessen  
  
 `ProcessNames`: der Prozessname Wenn mehrere Instanzen des benannten Prozesses ausgeführt werden, sind die Ergebnisse unvorhersehbar.  
  
 Trennt mehrere Prozesse mit Komma voneinander ab.  
  
 Wenn kein Prozess angegeben ist, wird der Profiler von allen Prozessen, für die ein Profil erstellt wird, getrennt.  
  
## <a name="valid-options"></a>Gültige Optionen  
 Die folgenden **VSPerfCmd**-Optionen können mit der Option **Attach** in derselben Befehlszeile kombiniert werden.  
  
 **CrossSession**  
 Aktiviert die Profilerstellung für Anwendungen in Sitzungen, die keine Anmeldesitzungen sind. Diese Option ist erforderlich, wenn die Option **Start** mit der Option **CrossSession** angegeben wurde.  
  
## <a name="example"></a>Beispiel  
 In diesem Fall hält der Befehl **Detach** die Profilerstellung an, und der Befehl **Shutdown** schließt die Profilerdatendatei.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Erstellen von Dienstprofilen](../profiling/command-line-profiling-of-services.md)