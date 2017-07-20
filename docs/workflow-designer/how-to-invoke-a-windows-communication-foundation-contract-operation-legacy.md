---
title: "Vorgehensweise: Aufrufen eines Windows Communication Foundation-Vertragsvorgangs (Vorg&#228;ngerversion) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Vorgehensweise: Aufrufen eines Windows Communication Foundation-Vertragsvorgangs (Vorg&#228;ngerversion)
In diesem Thema wird der Aufruf eines [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)]\-Vertragsvorgangs mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] beschrieben, die auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielt.  
  
 Nach dem Ziehen einer **SendActivity**\-Aktivität aus der Toolbox zur Workflowentwurfsoberfläche müssen Sie einen vorhandenen Vertrag importieren und festlegen, welcher Vorgang aus dieser **SendActivity**\-Aktivität aufgerufen wird.Sie wählen den Vertrag und seine Vorgänge über das [Dialogfeld "Vorgang auswählen" \(Vorgängerversion\)](../workflow-designer/choose-operation-dialog-box-legacy.md) aus.  
  
 Beim Verwenden einer Konfigurationsdatei mit dem Dienst müssen Sie auch ein <xref:System.Workflow.Activities.ChannelToken> angeben.Das <xref:System.Workflow.Activities.ChannelToken> identifiziert die Endpunktkonfiguration, die die Sendeaktivität für die Verbindung zum Workflowdienst verwendet.  
  
### So rufen Sie einen WCF\-Vertragsvorgang aus einer SendActivity\-Aktivität auf  
  
1.  Doppelklicken Sie auf die **SendActivity**\-Aktivität im Designer oder klicken Sie auf die Ellipse neben der **ServiceOperationInfo**\-Eigenschaft im Bereich **Eigenschaften**.  
  
2.  Wenn das Dialogfeld **Vorgang auswählen** geöffnet wird, klicken  in der oberen rechten Ecke des Dialogfelds auf **Importieren**.  
  
     Das [Dialogfeld '.NET\-Typ suchen und auswählen' \(Vorgängerversion\)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) wird geöffnet.  
  
3.  Suchen Sie eine Assembly oder ein Projekt, das den gewünschten Vertrag enthält.  
  
4.  Wählen Sie den Vertrag aus, und klicken Sie auf **OK**.  
  
5.  Wählen Sie unter **Verfügbare Vorgänge** den Vorgang aus, der aufgerufen werden soll, und klicken Sie auf **OK**.  
  
### So geben Sie ein Kanaltoken an  
  
1.  Wählen Sie die <xref:System.Workflow.Activities.SendActivity>\-Aktivität im Designer aus.  
  
2.  Geben Sie im Bereich **Eigenschaften** einen Namen für das <xref:System.Workflow.Activities.ChannelToken> an.Dieser Name identifiziert das Kanaltoken eindeutig.  
  
3.  Erweitern Sie den Kanaltokenknoten, und geben Sie einen Namen für den Clientendpunkt an, den Sie im <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>\-Feld verwenden.Die Endpunktkonfiguration mit dem gleichen Namen in der Konfigurationsdatei wird zum Konfigurieren des Kanals verwendet.  
  
4.  Erstellen Sie die Endpunktkonfiguration in der Konfigurationsdatei, wenn noch nicht vorhanden.Weitere Informationen zum Konfigurieren des Clients finden Sie unter [Übersicht über den WCF\-Client](../Topic/WCF%20Client%20Overview.md).  
  
## Siehe auch  
 [Dialogfeld "Vorgang auswählen" \(Vorgängerversion\)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Vorgehensweise: Implementieren eines WCF\-Vertragsvorgangs \(Vorgängerversion\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)