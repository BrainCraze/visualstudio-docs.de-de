---
title: "Angeben des Pfads zu den Profilerstellungstools für die Befehlszeile | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b33ee79d51dfcdb3db9021d3613672c44aef8956
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-the-path-to-profiling-tools-command-line-tools"></a>Angeben des Pfads zu den Profilerstellungstools für die Befehlszeile
Der Pfad der Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools wird der PATH-Umgebungsvariablen nicht hinzugefügt. Auf 32-Bit-Computern befinden sich die Tools in einem einzigen Verzeichnis. Es gibt 32-Bit und 64-Bit-Versionen der Profilerstellungstools auf 64-Bit-Computern.  
  
## <a name="32-bit-computers"></a>32-Bit-Computer  
 Auf 32-Bit-Computern ist das Standardverzeichnis für Profilerstellungstools *Laufwerk*\Programme\Microsoft Visual Studio 11.0\Team Tools\Performance Tools.  
  
## <a name="64-bit-computers"></a>64-Bit-Computer  
 Auf 64-Bit-Computern legen Sie den Pfad entsprechend der Zielplattform der profilierten Anwendung fest.  
  
-   Bei 32-Bit-Anwendungen lautet das Standardverzeichnis für Profilerstellungstools:  
  
     *Laufwerk*\Programme (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools  
  
-   Bei 64-Bit-Anwendungen lautet das Standardverzeichnis für Profilerstellungstools:  
  
     *Laufwerk*\Programme (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\x64