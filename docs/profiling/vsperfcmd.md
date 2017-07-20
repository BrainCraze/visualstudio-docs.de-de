---
title: "VSPerfCmd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Befehlszeile, Tools"
  - "Befehlszeilentools, VSPerfCmd-Tool"
  - "Leistungstools, VSPerfCmd-Tool"
  - "Profilerstellungstools, VSPerfCmd"
  - "VSPerfCmd-Tool"
ms.assetid: 778bc105-7643-46c4-a338-f3620e31125a
caps.latest.revision: 49
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 49
---
# VSPerfCmd
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit dem Tool **VSPerfCmd.exe** wird die Sammlung von Leistungsdaten gestartet und beendet.  Es verwendet die folgende Syntax:  
  
```  
VSPerfCmd [/U] [/options]  
```  
  
 In der folgenden Tabelle werden die Optionen des Tools **VSPerfCmd.exe** beschrieben:  
  
|Option|**Beschreibung**|  
|------------|----------------------|  
|**U**|Umgeleitete Konsolenausgaben sind als Unicode geschrieben.  Muss die erste angegebene Option sein.|  
|[Starten](../profiling/start.md) **:** `mode`|Startet den Profilerstellungsdienst im angegebenen Modus.|  
|[Ausgabe](../profiling/output.md) **:** `filename`|Gibt den Ausgabedateinamen an.  Nur zusammen mit **Start**.|  
|[CrossSession&#124;CS](../profiling/crosssession.md)|Aktiviert die Profilerstellung über Windows\-Sitzungen hinweg.  Nur zusammen mit **Start**, **Attach**, **or Launch**.|  
|[Benutzer](../profiling/user-vsperfcmd.md) **:**\[`domain\`\]`username`|Gewährt dem angegebenen Konto Zugriff auf den Profilerdienst.  Nur zusammen mit **Start**.|  
|[WaitStart](../profiling/waitstart.md)\[**:**`n`\]|Wartet darauf, dass die Protokollierung für die Datenerfassung initialisiert wird.  Wenn `n` angegeben ist, wartet **VSPerfCmd** höchstens `n` Sekunden.  Wenn `n` nicht angegeben wird, wartet **VSPerfCmd** unendlich lange.  Dies vereinfacht die Verwendung von **VSPerfCmd** in einem Batchprozess.|  
|[Zähler](../profiling/counter.md) **:** `cfg`|Wenn die Samplingmethode für die Profilerstellung verwendet wird, wird ein CPU\-Indikator angegeben sowie die Anzahl der als Samplingintervall zu verwendenden Ereignisse.  Sie können nur für einen Zählerwert ein Sampling ausführen.<br /><br /> Wenn die Instrumentationsmethode für die Profilerstellung verwendet wird, gibt diese einen CPU\-Indikator an, der an jedem Instrumentationspunkt aufzulisten ist.  Nur zusammen mit **Start:**`Trace`, **Attach** oder **Launch**.|  
|[QueryCounters](../profiling/querycounters.md)|Zeigt eine Liste gültiger CPU\-Leistungsindikatoren für den aktuellen Computer an.|  
|[WinCounter](../profiling/wincounter.md) **:** *path*|Gibt ein Windows\-Leistungsindikatorereignis an, das in die Profilmarkierungsdaten aufgenommen werden soll.  Nur zusammen mit **Start**.|  
|[AutoMark](../profiling/automark.md) **:** *n*|Gibt das Zeitintervall \(in Millisekunden\) für die Sammlung der Werte von Windows\-Leistungsindikatordaten an.  Mit **WinCounter** zu verwenden.|  
|[Ereignisse](../profiling/events-vsperfcmd.md) **:** `option`|Steuert die Sammlung der angegebenen Ereignisse der Ereignisablaufverfolgung für Windows \(ETW\).  ETW\-Daten werden in einer ITL\-Datei getrennt von der Profilerstellungs\-Datendatei \(.vsp\) gesammelt.|  
|[Status](../profiling/status.md)|Zeigt den Zustand des Profilers, Informationen zu Prozessen, für die gerade ein Profil erstellt wird, und die Konten an, die berechtigt sind, den Profiler zu steuern.|  
|[Shutdown](../profiling/shutdown.md)\[**:**`n`\]|Schließt die Profilerstellungs\-Datendatei und deaktiviert den Profiler.|  
|[GlobalOn](../profiling/globalon-and-globaloff.md)|Setzt nach einem Aufruf von **VSPerfCmdGlobalOff** die Datensammlung fort.|  
|[GlobalOff](../profiling/globalon-and-globaloff.md)|Beendet die gesamte Datensammlung, beendet aber nicht die Profilerstellungssitzung.|  
|[ProcessOn](../profiling/processon-and-processoff.md) **:** `pid`|Setzt die Datensammlung für den angegebenen Prozess fort, nachdem die Profilerstellung durch einen Aufruf von **VSPerfCmdProcessOff** angehalten wurde.|  
|[ProcessOff](../profiling/processon-and-processoff.md) **:** `pid`|Beendet die Datensammlung für den angegebenen Prozess.|  
|[ThreadOn und ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Setzt Profilerstellung für den angegebenen Prozess fort, nachdem die Profilerstellung durch einen Aufruf von **VSPerfCmdThreadOff** angehalten wurde.  Verwenden Sie **ThreadOn** nur, wenn Sie Profile mit der Instrumentationsmethode erstellen.|  
|[ThreadOn und ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Hält die Profilerstellung für den angegebenen Thread an.  Verwenden Sie **ThreadOff** nur, wenn Sie Profile mit der Instrumentationsmethode erstellen.|  
|[Mark](../profiling/mark.md) **:** *MarkNum*\[**,***MarkText***\]**|Fügt eine Markierung mit einem optionalen Text in die Profilerstellungs\-Datendatei ein.|  
  
## Optionen der Samplingmethode  
 Die folgenden Optionen sind nur beim Verwenden der Samplingmethode für die Profilerstellung verfügbar.  
  
|Option|**Beschreibung**|  
|------------|----------------------|  
|[Starten](../profiling/launch.md) **:** *Executable*|Startet die angegebene Anwendung und beginnt mit der Profilerstellung.|  
|[Args](../profiling/args.md) **:** *Arguments*|Gibt Befehlszeilenargumente an, die an die Anwendung übergeben werden sollen.|  
|[Konsole](../profiling/console.md)|Startet den angegebenen Befehl in einem neuen Eingabeaufforderungsfenster.|  
|[Attach](../profiling/attach.md) **:** *PID*\[**,***PID*\]|Startet die Profilerstellung für die angegebenen Prozesse.  Prozesse können über die Prozess\-ID oder den Prozessnamen identifiziert werden.|  
|[Detach](../profiling/detach.md)\[**:***PID*\[,*PID*\]\]|Beendet die Profilerstellung für die angegebenen Prozesse.  Prozesse können über die Prozess\-ID oder den Prozessnamen identifiziert werden.  Wenn kein Prozess angegeben wird, wird die Profilerstellung für alle Prozesse angehalten.|  
|[GC](../profiling/gc-vsperfcmd.md)\[**:**{**Allocation** `&#124;` **Lifetime**}\]|Sammelt .NET\-Speicherbelegungsinformationen und Daten zur Objektlebensdauer.  Nur zusammen mit der **VSPerfCmd Launch**\-Option verwenden.|  
  
### Samplingintervalloptionen  
 Die folgenden Optionen geben den Typ und die Dauer von Samplingintervallen an.  Die Standardeinstellung ist **Timer**.  Mit der **Counter**\-Option können Sie auch einen CPU\-Leistungsindikator als Intervall angeben.  Diese Optionen können nur mit **Launch** oder dem ersten **Attach** einer Profilerstellungssitzung angegeben werden.  
  
|Option|**Beschreibung**|  
|------------|----------------------|  
|[PF](../profiling/pf.md)\[**:***n*\]|Führt ein Sampling bei jedem x\-ten Seitenfehler durch \(Standard\=10\).|  
|[Sys](../profiling/sys-vsperfcmd.md)\[**:***n*\]|Führt ein Sampling bei jedem x\-ten Systemaufruf durch \(Standard\=10\).|  
|[Zeitgeber](../profiling/timer.md)\[**:***n*\]|Führt ein Sampling bei jedem n\-ten Prozessorzyklus durch \(Standard\=10000000\).|  
  
## Optionen der Dienstkomponente und Gerätetreiber für den Kernelmodus  
 Die folgenden Administratoroptionen unterstützen Komponenten für Profilerstellungsdienste oder Gerätetreiber für den Kernelmodus.  Die Administratoroptionen legen Profilerstellungsberechtigungen fest und steuern den Dienst für die Profilerstellung oder den Gerätetreiber.  
  
 Administratoroptionen müssen an einer Eingabeaufforderung ausgeführt werden, die mit Administratorrechten ausgeführt wird.  
  
|Option|**Beschreibung**|  
|------------|----------------------|  
|**Admin:Security** \<**ALLOW&#124;DENY**\> *Right*\[ *Right*\] \<*User*&#124;*Group*\>|Gewährt oder verweigert dem angegebenen Benutzer oder der angegebenen Gruppe den Zugriff auf die Profilerstellungsdienste.<br /><br /> `Right` kann Folgendes sein:<br /><br /> CrossSession: Gewährt dem Benutzer Zugriff auf den Dienst für die sitzungsübergreifende Profilerstellung.<br /><br /> SampleProfiling: Gewährt dem Benutzer Zugriff auf den Treiber für die Sampling\-Profilerstellung.  Wird auch für den Zugriff auf Kernelübergangsinformationen während der Erstellung von Ablaufverfolgungsprofilen verwendet.<br /><br /> FullAccess: Gewährt dem Benutzer Zugriff sowohl auf CrossSession als auch auf SampleProfiling.|  
|**Admin:Security, List**|Listet den aktuellen Zustand von Profilerstellungsdiensten und Benutzerberechtigungen auf.|  
|**Admin:**  `` \<*Service*&#124;*Driver*\>\<**START**&#124;**STOP**&#124;**INSTALL**&#124;**UNINSTALL**\>|Startet, beendet, installiert oder deinstalliert die Komponente \(Dienst\) für den Profilerstellungsdienst oder den Gerätetreiber \(Treiber\) für den Kernelmodus.|  
|**Admin:**  `` \<*Service*&#124;*Driver*\>**AutoStart** `` \<**ON**&#124;**OFF**\>|Aktiviert oder deaktiviert den automatischen Start des Profilerstellungsdienstes \(Dienst\) oder des Gerätetreibers \(Treiber\) für den Kernelmodus nach einem Neustart.|  
  
## VSPerfCmd \/Driver  
 Die **VSPerfCmd \/Driver**\-Option ist veraltet.  Verwenden Sie die **Admin**\-Optionen von **VsPerfCmd** für diese Funktionalität.  
  
## Siehe auch  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfReport](../profiling/vsperfreport.md)