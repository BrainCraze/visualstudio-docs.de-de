---
title: "Capability Flags | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Source Control-Plug-ins Capability flags"
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Capability Flags
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die SCC\_CAP\_*Xxx* Flags Bitflags an, das die Funktionen des ein Quellcodeverwaltungs\-Plug\-in verwendet werden. Die SCC\_EXCAP\_*Xxx* Flags sind inkrementelle Flags, die erweiterten Funktionen und Ganzzahlwerte beheben.  
  
|Capability\-Code|Wert|Beschreibung|  
|----------------------|----------|------------------|  
|`SCC_CAP_REMOVE`|0x00000001L|Unterstützt die [SccRemove](../extensibility/sccremove-function.md) und Befehl.|  
|`SCC_CAP_RENAME`|0x00000002L|Unterstützt die [SccRename](../extensibility/sccrename-function.md) und Befehl.|  
|`SCC_CAP_DIFF`|0x00000004L|Unterstützt die [SccDiff](../extensibility/sccdiff-function.md) und Befehl.|  
|`SCC_CAP_HISTORY`|0x00000008L|Unterstützt die [SccHistory](../extensibility/scchistory-function.md) und Befehl.|  
|`SCC_CAP_PROPERTIES`|0x00000010L|Unterstützt die [SccProperties](../extensibility/sccproperties-function.md) und Befehl.|  
|`SCC_CAP_RUNSCC`|0x00000020L|Unterstützt die [SccRunScc](../extensibility/sccrunscc-function.md) und Befehl.|  
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Unterstützt die [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) und Befehl.|  
|`SCC_CAP_QUERYINFO`|0x00000080L|Unterstützt die [SccQueryInfo](../extensibility/sccqueryinfo-function.md) und Befehl.|  
|`SCC_CAP_GETEVENTS`|0x00000100L|Unterstützt die [SccGetEvents](../extensibility/sccgetevents-function.md) und Befehl.|  
|`SCC_CAP_GETPROJPATH`|0x00000200L|Unterstützt die [SccGetProjPath](../extensibility/sccgetprojpath-function.md) und Befehl.|  
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Unterstützt die [SccAddFromScc](../extensibility/sccaddfromscc-function.md) und Befehl.|  
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Unterstützt einen Kommentar auf Auschecken.|  
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Unterstützt einen Kommentar beim Einchecken.|  
|`SCC_CAP_COMMENTADD`|0x00002000L|Unterstützt einen Kommentar hinzufügen.|  
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Unterstützt einen Kommentar auf Entfernen.|  
|`SCC_CAP_TEXTOUT`|0x00008000L|Schreibt Text in einer bereitgestellten IDE Ausgabefunktion.|  
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Unterstützt das Speichern von Dateien ohne Deltas.|  
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Unterstützt mehrere Dateiversionsverlauf.|  
|`SCC_CAP_IGNORECASE`|0x00800000L|Unterstützt die Groß\-\/Kleinschreibung Dateivergleich.|  
|`SCC_CAP_IGNORESPACE`|0x01000000L|Unterstützt die Datei Vergleich, der Leerzeichen ignoriert.|  
|`SCC_CAP_POPULATELIST`|0x02000000L|Unterstützt das Suchen von zusätzlichen Dateien.|  
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Unterstützt die Kommentare zu erstellen\-Projekt.|  
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Unterstützt die Unterschiede in allen Zuständen Wenn gesteuert.|  
|`SCC_CAP_GET_NOUI`|0x20000000L|\-Plug\-in unterstützt keine Benutzeroberfläche für Get jedoch IDE möglicherweise weiterhin aufrufen [SccGet](../extensibility/sccget-function.md).|  
|`SCC_CAP_REENTRANT`|0x40000000L|Plug\-in ist reentrant und threadsicher. In Version 1.0 wurden keine Plug\-Ins davon ausgegangen, dass reentrant und threadsicher ist. Ein plug\-in 1.1 dieses Bit festgelegt, kann der Host mehrere Projekte gleichzeitig öffnen.|  
  
## In Version 1.2 hinzugefügt Funktionsbits  
  
|Capability\-Code|Wert|Beschreibung|  
|----------------------|----------|------------------|  
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Unterstützt die [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|  
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Unterstützt die [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|  
|`SCC_CAP_BATCH`|0x00040000L|Unterstützt die [SccBeginBatch](../extensibility/sccbeginbatch-function.md) und [SccEndBatch](../extensibility/sccendbatch-function.md).|  
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Unterstützt die [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|  
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Unterstützt die [SccDirDiff](../extensibility/sccdirdiff-function.md).|  
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Mehrfaches Auschecken einer Datei unterstützt und die [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|  
|`SCC_CAP_SCCFILE`|0x80000000L|Unterstützt die MSSCCPRJ. SCC\-Datei \(gemäß den Benutzer und Administratoren überschreiben\) und die [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|  
  
## In Version 1.3 hinzugefügte Funktionsbits  
 Diese Flags werden jeweils einzeln zu übergeben der [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) Funktion, um zu bestimmen, ob die Funktion unterstützt wird.  
  
|Code für erweiterte Funktionen|Wert|Beschreibung|  
|------------------------------------|----------|------------------|  
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Unterstützt die `SCC_CHECKOUT_LOCALVER` \-Option für das Auschecken.|  
|`SCC_EXCAP_BACKGROUND_GET`|2|Unterstützt die [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|  
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Unterstützt die [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|  
|`SCC_EXCAP_POPULATELIST_DIR`|4|Unterstützt das Suchen von zusätzlichen Verzeichnisse.|  
|`SCC_EXCAP_QUERYCHANGES`|5|Unterstützt das Aufzählen von geändert.|  
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Unterstützt die [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|  
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Unterstützt die [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|  
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Unterstützt das Aufrufen von SccQueryInfo in mehreren Threads.|  
|`SCC_EXCAP_REMOVE_DIR`|9|Unterstützt die SccRemoveDir\-Funktion.|  
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Ausgecheckte Dateien können gelöscht werden.|  
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Ausgecheckte Dateien können umbenannt werden.|  
  
## Siehe auch  
 [Source Control\-Plug\-ins](../extensibility/source-control-plug-ins.md)