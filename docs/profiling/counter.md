---
title: Counter | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5974c2f5a1acccebfb9385b91eface6fdc7ba278
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="counter"></a>Zähler
Die Option **Counter** sammelt Daten von Leistungsindikatoren für Prozessoren (Hardware).  
  
-   Wenn Sie die Sampling-Profilerstellung (Methode) verwenden, gibt **Counter** den Chipleistungsindikator und die Anzahl der Zählerereignisse an, die als Samplingintervall verwendet werden sollen. Sie können nur einen Zähler angeben, wenn Sie Sampling verwenden.  
  
-   Bei der Profilerstellung für die Instrumentierung (Methode) wird die Anzahl der Zählerereignisse, die im Intervall zwischen den vorherigen und den aktuellen Auflistungsereignissen aufgetreten sind, als separate Felder in Profiler-Berichten aufgeführt. Mehrere **Counter**-Optionen können angegeben werden, wenn Sie die Instrumentierung verwenden.  
  
 Jeder Prozessortyp hat eigene Hardware-Leistungsindikatoren. Der Profiler definiert mehrere generische Leistungsindikatoren, die für fast alle Prozessoren verwendet werden. Um die generischen und prozessorspezifischen Leistungsindikatoren auf dem Computer aufzulisten, verwenden Sie den VSPerfCmd-Befehl **QueryCounters**.  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]  
```  
  
```  
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]  
```  
  
#### <a name="parameters"></a>Parameter  
 `Name`  
 Der Name des Zählers. Mit dem VSPerfCmd.exe-Befehl **QueryCounters** können Sie den Namen der verfügbaren Leistungsindikatoren auf dem Computer auflisten.  
  
 `Reload`  
 Die Anzahl der Zählerereignisse im Samplingintervall. Verwenden Sie sie nicht mit der Instrumentierungsmethode.  
  
 `FriendlyName`  
 Optional: Die Zeichenfolge, die Sie anstelle von `Name` in den Spaltenüberschriften von Profilerberichten und Ansichten verwenden sollten.  
  
## <a name="required-options"></a>Erforderliche Optionen  
 Die „Counter“-Option kann nur mit einer der folgenden Optionen verwendet werden:  
  
 **Start:** `Trace`  
 Initialisiert den Profiler für die Verwendung der Instrumentierungsmethode  
  
 **Starten:** `AppName`  
 Startet die angegebene Anwendung und den Profiler. Der Profiler muss für die Verwendung der Samplingmethode initialisiert werden.  
  
 **Attach:** `PID`  
 Startet den Profiler und fügt ihn dem von der Prozess-ID angegebenen Prozess an. Der Profiler muss für die Verwendung der Samplingmethode initialisiert werden.  
  
## <a name="example"></a>Beispiel  
 Das Beispiel mit der Samplingmethode veranschaulicht, wie eine Anwendung bei jedem tausendsten Vorkommen des generischen Profilerzählers „NonHaltedCycles“ überprüft wird.  
  
 Die Instrumentierungsmethode veranschaulicht, wie der Profiler für das Sammeln von L2InstructionFetches-Leistungsindikatorereignissen initialisiert wird. Der Name des L2InstructionFetches-Zählers ist für jeden Prozessor eindeutig.  
  
```  
; Sample Method Example  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"  
  
;INSTRUMENTATION METHOD EXAMPLE  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Erstellen von Dienstprofilen](../profiling/command-line-profiling-of-services.md)