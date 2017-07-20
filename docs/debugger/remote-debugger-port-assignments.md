---
title: "Remotedebugger - Portzuweisungen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Remotedebugger - Portzuweisungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Visual Studio\-Remotedebugger kann als Anwendung oder als Hintergrunddienst ausgeführt werden. Bei der Ausführung als Anwendung wird standardmäßig der folgende Port zugewiesen:  
  
-   Visual Studio 2015: 4020  
  
-   Visual Studio 2013: 4018  
  
-   Visual Studio 2012: 4016  
  
 Die Nummer des Ports, der dem Remotedebugger zugewiesen ist, wird also für jede Version um 2 erhöht. Sie können bei Bedarf eine andere Portnummer festlegen. Das Festlegen von Portnummern wird in einem späteren Abschnitt erläutert.  
  
## Remotedebugger\-Port bei 32\-Bit\-Betriebssystemen  
 TCP 4020 \(Visual Studio 2015\) ist der Hauptport und für alle Szenarien erforderlich. Sie können ihn über die Befehlszeile oder das Fenster "Remotedebugger" konfigurieren.  
  
 Klicken Sie im Fenster "Remotedebugger" auf **Extras \/ Optionen**, und legen Sie die Nummer für den TCP\/IP\-Port fest.  
  
 Starten Sie von der Befehlszeile aus den Remotedebugger über die Option **\/port**: **msvsmon \/port \<Portnummer\>**.  
  
 Alle Remotedebugger\-Befehlszeilenoptionen finden Sie in der Hilfe zum Remotedebugging \(drücken Sie **F1**, oder klicken Sie im Fenster "Remotedebugger" auf **Hilfe \/ Verwendung**\).  
  
## Remotedebugger\-Port bei 64\-Bit\-Betriebssystemen  
 Beim Starten der 64\-Bit\-Version des Remotedebuggers wird standardmäßig Port 4020 verwendet.  Wenn Sie einen 32\-Bit\-Prozess debuggen, startet die 64\-Bit\-Version des Remotedebuggers eine 32\-Bit\-Remotedebuggerversion auf Port 4021. Wenn Sie den 32\-Bit\-Remotedebugger ausführen, wird Port 4020 und nicht Port 4021 verwendet.  
  
 Dieser Port ist über die Befehlszeile konfigurierbar: **msvsmon \/wow64port \<Portnummer\>**.  
  
## Port für die Ermittlung  
 UDP 3702 wird für die Suche nach ausgeführten Instanzen des Remotedebuggers im Netzwerk verwendet \(z. B. bei **Suchen** im Dialogfeld **An den Prozess anhängen**\). Er wird nur für die Ermittlung von Computern verwendet, auf denen der Remotedebugger ausgeführt wird, und ist daher optional, wenn Sie den Computernamen oder die IP\-Adresse des Zielcomputers auf andere Weise ermitteln können. Da dies der Standardport für die Ermittlung ist, kann die Portnummer nicht konfiguriert werden.  
  
 Wenn Sie die Ermittlung nicht aktivieren möchten, können Sie msvsmon von der Befehlszeile aus mit deaktivierter Ermittlung starten: **msvsmon \/nodiscovery**.  
  
## Remotedebugger\-Ports in Azure  
 Die folgenden Ports werden vom Remotedebugger in Azure verwendet. Die Ports im Clouddienst werden den Ports auf den einzelnen virtuellen Computern zugeordnet. Bei allen Ports handelt es sich um TCP\-Ports.  
  
||||  
|-|-|-|  
|**Verbindung**|**Port im Clouddienst**|**Port auf virtuellem Computer**|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## Siehe auch  
 [Remotedebugging](../debugger/remote-debugging.md)