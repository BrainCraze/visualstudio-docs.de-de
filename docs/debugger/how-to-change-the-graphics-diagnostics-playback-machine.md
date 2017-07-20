---
title: "Gewusst wie: &#196;ndern des Grafikdiagnose-Wiedergabecomputers | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: &#196;ndern des Grafikdiagnose-Wiedergabecomputers
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Grafikinformationen über Ihren lokalen Computer oder einen Remotecomputer bzw. ein Remotegerät wiedergeben.  
  
## Auswählen eines Wiedergabecomputers  
 Der Wiedergabecomputer ist ein Computer oder ein Gerät zur Wiedergabe von Grafikereignissen aus einem Grafikprotokoll.  Normalerweise ist der lokale Computer die zweckmäßigste Option, jedoch kann ein Renderingproblem möglicherweise nicht auf einem Computer reproduziert werden, der über unterschiedliche Hardware\- oder Treiberversionen als der Computer verfügt, der zur Aufzeichnung verwendet wurde. Ist dies der Fall, können Sie einen Remotewiedergabecomputer auswählen, der das Problem besser reproduziert, und trotzdem Ihren Entwicklungscomputer zur Diagnose verwenden.  
  
#### So verwenden Sie den lokalen Computer, um Grafikinformationen wiederzugeben  
  
1.  Klicken Sie im Dokumentfenster "Grafikprotokolle" auf den Link **Wiedergabecomputer**.  Das Dialogfeld **Verbindungen des Remotedebuggers** wird angezeigt.  
  
2.  Geben Sie in der Eigenschaft **Adresse** unter **Manuelle Konfiguration** die Zeichenfolge `localhost` ein.  
  
3.  Setzen Sie die Eigenschaft **Authentifizierungsmodus** auf **Keine**.  
  
4.  Klicken Sie auf die Schaltfläche **Auswählen**.  
  
#### So verwenden Sie einen Remotecomputer zur Wiedergabe von Grafikinformationen  
  
1.  Klicken Sie im Dokumentfenster "Grafikprotokolle" auf den Link **Wiedergabecomputer**.  Das Dialogfeld **Verbindungen des Remotedebuggers** wird angezeigt.  
  
2.  Geben Sie in der Eigenschaft **Adresse** unter **Manuelle Konfiguration** den Windows\-Domänennamen oder die IP\-Adresse des Computers oder Geräts ein, das Sie zur Wiedergabe von Grafikinformationen verwenden möchten.  
  
3.  Geben Sie die Art der Autorisierung an, die Sie verwenden möchten, um die Verbindung mit dem Wiedergabecomputer zu sichern.  
  
    -   Setzen Sie den **Authentifizierungsmodus** zur Windows\-Authentifizierung auf **Windows**.  
  
    -   Wenn keine Authentifizierung erfolgen soll, legen Sie die Eigenschaft **Authentifizierungsmodus** auf **Keine** fest.  
  
4.  Klicken Sie auf die Schaltfläche **Auswählen**.  
  
> [!NOTE]
>  Im Dialogfeld **Verbindungen des Remotedebuggers** können auch Remotedebuggingziele angezeigt werden, die direkt mit Ihrem Entwicklungscomputer verbunden sind oder sich auf dem gleichen Subnetz befinden.  Sie können eines dieser Remotedebuggingziele als Grafikdiagnose\-Wiedergabecomputer verwenden, ohne diesen manuell zu konfigurieren.  Wählen Sie im Dialogfeld **Verbindungen des Remotedebuggers** das gewünschte Ziel aus, und klicken Sie dann auf die Schaltfläche **Auswählen**.  
  
## Siehe auch  
 [Grafikprotokolldokument](../debugger/graphics-log-document.md)