---
title: "Grafikzustand | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.graphics.statewindow"
ms.assetid: 97e7757e-c372-4626-8149-99a81367a0e1
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Grafikzustand
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im Statusfenster der Visual Studio\-Grafikdiagnose sehen Sie den Grafikstatus, der zum Zeitpunkt des aktuellen Ereignisses aktiv ist, wie z. B. bei einem Zeichnen\-Befehl.  
  
## Grundlegendes zum Statusfenster  
 Das Statusfenster fasst die Zustände zusammen, die sich auf das Rendering auswirken, und stellt sie an einem zentralen Ort hierarchisch dar.  Abhängig von der Direct3D\-Version, die Ihre App verwendet, können sich die im Statusfenster angezeigten Informationen unterscheiden.  
  
### Statusansichten  
 Sie können die Statustabelle auf verschiedene Art und Weise anzeigen:  
  
|Ansicht|Beschreibung|  
|-------------|------------------|  
|API\-Eingabestatusansicht|Diese Ansicht zeigt den Status in einem ähnlichen Layout wie die Direct3D\-Objekte an, die den Status bilden.|  
|Logische Eingabestatusansicht|Diese Ansicht stellt den Status in einer logischen Ansicht dar, die nicht das Layout der Direct3D\-Objekte widerspiegelt, die den Status bilden.|  
|Angeheftete Statusansicht|Anstelle einer Hierarchie stellt die angeheftete Statusansicht angeheftete Statuselemente in einer flachen Liste mit vollqualifizierten Namen dar.  In dieser Ansicht können zahlreiche Statuselemente aus verschiedenen Statusbündeln in nur wenigen Zeilen angezeigt werden.|  
  
##### So ändern Sie die Statusansicht  
  
-   Klicken Sie im Statusfenster in der oberen linken Ecke direkt unterhalb der Titelleiste auf die Schaltfläche, die dem gewünschten Statusansichtsstil entspricht.  
  
    -   **API\-Eingabestatusansicht anzeigen**  
  
    -   **Logische Statusansicht anzeigen**  
  
    -   **Angeheftete Statusansicht anzeigen**  
  
> [!IMPORTANT]
>  Sie müssen den Status in den Ansichten **API\-Eingabestatus anzeigen** oder **Logischen Status anzeigen** anheften, damit er in der Ansicht **Angeheftete Statusansicht anzeigen** angezeigt wird.  
  
### Format der Statustabelle  
 Das Statusfenster enthält mehrere Spalten mit Informationen.  
  
|Spalte|Beschreibung|  
|------------|------------------|  
|Name|Der Name des Statuselements.  Wenn dieses Element Statusbündel darstellt, kann das Element erweitert werden, um es anzuzeigen.<br /><br /> In der **API\-Eingabestatusansicht** und **logischen Statusansicht** geben Namen die hierarchische Beziehung zwischen den Zuständen an.<br /><br /> In der **angehefteten Statusansicht** werden vollqualifizierte Namen in einer flachen Liste angezeigt.|  
|Wert|Der Wert des Statuselements.|  
|Typ|Der Typ des Statuselements.|  
  
### Geänderter Status  
 Der Grafikstatus ändert sich in der Regel inkrementell zwischen nachfolgende Zeichnen\-Befehlen, und viele Arten von Renderingprobleme treten auf, wenn der Status nicht ordnungsgemäß geändert wird.  Um Sie dabei zu unterstützen, zu ermitteln, welcher Status sich seit dem letzten Zeichnen\-Befehl geändert hat, wird ein geänderter Status durch ein rotes Sternchensymbol \(\*\) markiert. Dies bezieht sich nicht nur auf den Status selbst, sondern auch auf den übergeordneten Status, sodass Sie Änderungen sofort auf der obersten Ebene erkennen und dann zu den Details vordringen können.  
  
### Angehefteter Status  
 Da viele Apps ähnliche Objekte nacheinander rendern und dabei einen Satz bekannter Status ändern, ist es manchmal sinnvoll, die veränderlichen Status anzuheften, sodass Sie die Änderungen von Zeichen\-Befehl zu Zeichen\-Befehl sehen können.  
  
 Dies kann auch nützlich sein, wenn Sie die Änderung eines bestimmten Zustands als Ursache eines Problems ermittelt haben.  
  
##### So heften Sie einen Status an  
  
1.  Suchen Sie den gewünschten Status im Statusfenster.  Sie müssen möglicherweise einen Status auf höherer Ebene erweitern, um die Details zum gewünschten Status anzuzeigen.  
  
2.  Platzieren Sie den Cursor auf dem gewünschten Status.  Eine Pinsymbol wird auf der linken Seite des Statuselements angezeigt.  
  
3.  Klicken Sie auf das Pinsymbol, um das Statuselement anzuheften.