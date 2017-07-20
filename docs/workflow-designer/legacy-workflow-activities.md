---
title: "Legacyworkflowaktivit&#228;ten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Aktivitäten"
  - "Workflowaktivitäten"
  - "Workflows, Aktivitäten"
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Legacyworkflowaktivit&#228;ten
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] enthält einen Standardsatz von Aktivitäten, die Funktionen für Ablaufsteuerung, Bedingungen, Ereignisbehandlung, Zustandsverwaltung und Kommunikation mit Anwendungen und Diensten bereitstellen.Beim Entwurf von Workflows können Sie die vom System bereitgestellten Aktivitäten verwenden, die von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] bereitgestellt werden, oder eigene benutzerdefinierte Aktivitäten erstellen.  
  
 In der folgenden Tabelle ist der vordefinierte Aktivitätssatz des [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)]\-Framework aufgeführt.Ein Großteil dieser Aktivitäten ist durch Aktivitätsdesigner dargestellt, auf die über die **Toolbox** von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] zugegriffen werden kann.Um eine Aktivität zu erstellen, ziehen Sie ihren Designer aus der **Toolbox**, und legen Sie ihn auf der Entwurfsoberfläche ab.  
  
|Aktivität|Beschreibung|  
|---------------|------------------|  
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|Wird mit der **HandleExternalEventActivity**\-Aktivität für Eingabe\- und Ausgabekommunikation mit einem lokalen Dienst verwendet.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der CallExternalMethodActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65060) \(möglicherweise in englischer Sprache\).|  
|[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|Wird zur Speicherung der Bereinigungslogik für eine zusammengesetzte Aktivität verwendet, die abgebrochen wurde, bevor alle untergeordneten Elemente der zusammengesetzten Aktivität ausgeführt werden konnten.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der CancellationHandlerActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65061) \(möglicherweise in englischer Sprache\).|  
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Ermöglicht das Hinzufügen von Visual Basic\- oder C\#\-Code zu Ihrem Workflow.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der CodeActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65062) \(möglicherweise in englischer Sprache\).|  
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|Eine kompensierbare Version von [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020).[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der CompensatableSequenceActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65002) \(möglicherweise in englischer Sprache\).|  
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|Eine kompensierbare Version von **TransactionScopeActivity**.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der CompensatableTransactionScopeActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65063) \(möglicherweise in englischer Sprache\).|  
|[CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|Hiermit können Sie den Code aufrufen oder Vorgänge kompensieren, die zum Zeitpunkt des Auftretens des Fehlers bereits vom Workflow ausgeführt wurden.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der CompensateActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65064) \(möglicherweise in englischer Sprache\).|  
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|Ein Wrapper für eine oder mehrere Aktivitäten, die eine abgeschlossene TransactionScopeActivity\-Aktivität kompensieren. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der CompensationHandlerActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65065) \(möglicherweise in englischer Sprache\).|  
|[ConditionedActivityGroup  \(Seite ist möglicherweise in englischer Sprache verfügbar.\)](http://go.microsoft.com/fwlink?LinkID=65017)|Führt untergeordnete Aktivitäten auf Grundlage einer Bedingung aus, die für die [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)\-Aktivität selbst gilt, sowie auf Grundlage von Bedingungen, die gesondert für jede untergeordnete Aktivität gelten.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der ConditionedActivityGroup\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65066) \(möglicherweise in englischer Sprache\).|  
|[DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|Ermöglicht das Erstellen von auf einem Timeoutintervall basierenden Verzögerungen in Ihrem Workflow.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der DelayActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65067) \(möglicherweise in englischer Sprache\).|  
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Umschließt eine oder mehrere Aktivitäten, die ausgeführt werden, wenn ein bestimmtes Ereignis eintritt.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der EventDrivenActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65068) \(möglicherweise in englischer Sprache\).|  
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|Stellt ein Framework für einer Aktivität zugewiesene Ereignisse bereit.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der EventHandlersActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65069) \(möglicherweise in englischer Sprache\).|  
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|Führt die wichtigste untergeordnete Aktivität gleichzeitig mit einer [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) aus.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der EventHandlingScopeActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65070) \(möglicherweise in englischer Sprache\).|  
|[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|Wird zur Behandlung einer Ausnahme des von Ihnen angegebenen Typs verwendet.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der FaultHandlerActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65071) \(möglicherweise in englischer Sprache\).|  
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|Stellt eine zusammengesetzte Aktivität dar, die über eine geordnete Liste untergeordneter Aktivitäten vom Typ [FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054) verfügt.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der FaultHandlersActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65072) \(möglicherweise in englischer Sprache\).|  
|[HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|Wird in Verbindung mit der [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)\-Aktivität für Eingabe\- und Ausgabekommunikation mit einem lokalen Dienst verwendet.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der HandleExternalEventActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65073) \(möglicherweise in englischer Sprache\).|  
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|Testet eine Bedingung für jede Verzweigung und führt Aktivitäten für die erste Verzweigung aus, für die die Bedingung **true** ergibt.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der IfElseActivity Aktivität](http://go.microsoft.com/fwlink?LinkID=65074) \(möglicherweise in englischer Sprache\).|  
|[IfElseBranchActivity  \(Seite ist möglicherweise in englischer Sprache verfügbar.\)](http://go.microsoft.com/fwlink?LinkID=65034)|Stellt eine Verzweigung einer [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033) dar.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der IfElseBranchActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65075) \(möglicherweise in englischer Sprache\).|  
|[InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|Unterstützt das Aufrufen eines Webdienstes durch Ihren Workflow.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der InvokeWebServiceActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65076) \(möglicherweise in englischer Sprache\).|  
|[InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|Unterstützt das Aufrufen eines anderen Webdienstes durch Ihren Workflow.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der InvokeWorkflowActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65077) \(möglicherweise in englischer Sprache\).|  
|[ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|Eine zusammengesetzte Aktivität, die nur untergeordnete [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)\-Aktivitäten beinhaltet.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der ListenActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65078) \(möglicherweise in englischer Sprache\).|  
|[ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|Unterstützt die Planung von zwei oder mehr untergeordneten **SequenceActivity**\-Aktivitätsverzweigungen für die gleichzeitige Verarbeitung.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der ParallelActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65079) \(möglicherweise in englischer Sprache\).|  
|[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|Verwendung zur Darstellung einer Auflistung von Regeln.Eine Regel besteht aus Bedingungen und daraus resultierenden Aktionen.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der PolicyActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65004) \(möglicherweise in englischer Sprache\).|  
|[ReplicatorActivity  \(Seite ist möglicherweise in englischer Sprache verfügbar.\)](http://go.microsoft.com/fwlink?LinkID=65039)|Erstellt mehrere Instanzen einer einzelnen untergeordneten Aktivität.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der ReplicatorActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65080) \(möglicherweise in englischer Sprache\).|  
|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|Bietet eine einfache Möglichkeit zur Verknüpfung mehrerer Aktivitäten für die sequenzielle Ausführung.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der SequenceActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65081) \(möglicherweise in englischer Sprache\).|  
|[SetStateActivity  \(Seite ist möglicherweise in englischer Sprache verfügbar.\)](http://go.microsoft.com/fwlink?LinkID=65041)|Gibt einen Übergang zu einem neuen Status an.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der SetStateActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65082) \(möglicherweise in englischer Sprache\).|  
|[StateActivity  \(Seite ist möglicherweise in englischer Sprache verfügbar.\)](http://go.microsoft.com/fwlink?LinkID=65042)|Stellt einen Status in einem Zustandsautomatenworkflow dar.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der StateActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65083) \(möglicherweise in englischer Sprache\).|  
|[StateFinalizationActivity  \(Seite ist möglicherweise in englischer Sprache verfügbar.\)](http://go.microsoft.com/fwlink?LinkID=65043)|Wird in einer [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)\-Aktivität als Container für untergeordnete Aktivitäten verwendet, die beim Beenden der **StateActivity**\-Aktivität ausgeführt werden.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der StateFinalizationActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65008) \(möglicherweise in englischer Sprache\).|  
|[StateInitializationActivity  \(Seite ist möglicherweise in englischer Sprache verfügbar.\)](http://go.microsoft.com/fwlink?LinkID=65044)|Wird in einer [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)\-Aktivität als Container für untergeordnete Aktivitäten verwendet, die bei Eingabe der **StateActivity**\-Aktivität ausgeführt werden.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der StateInitializationActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65006) \(möglicherweise in englischer Sprache\).|  
|[SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|Unterbricht den Vorgang Ihres Workflows zur Aktivierung des Eingriffs in das Ereignis einer Fehlerbedingung, die besonderer Aufmerksamkeit bedarf.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der SuspendActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65084) \(möglicherweise in englischer Sprache\).|  
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|Führt enthaltene Aktivitäten in einer synchronisierten Domäne sequenziell aus.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der SynchronizationScopeActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65085) \(möglicherweise in englischer Sprache\).|  
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|Unterstützt die sofortige Beendigung der Ausführung Ihres Workflows für den Fall, dass eine Fehlerbedingung vorliegt.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der TerminateActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65086) \(möglicherweise in englischer Sprache\).|  
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|Unterstützt die Erfassung von Geschäftsausnahmen, die als Bestandteil der Prozessmetadaten für einen Workflow ausgelöst werden.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der ThrowActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65087) \(möglicherweise in englischer Sprache\).|  
|[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|Stellt ein Framework für Transaktionen und Ausnahmebehandlung bereit.Weitere Informationen finden Sie unter [Verwenden der TransactionScopeActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65088) \(möglicherweise in englischer Sprache\).|  
|[WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Unterstützt die Erstellung des Auftretens eines Webdienstfehlers.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der WebServiceFaultActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65089) \(möglicherweise in englischer Sprache\).|  
|[WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|Empfängt Daten von einem Webdienst.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der WebServiceInputActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65090) \(möglicherweise in englischer Sprache\).|  
|[WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|Antwortet auf eine an einen Workflow ausgegebene Webdienstanforderung.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der WebServiceOutputActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65092) \(möglicherweise in englischer Sprache\).|  
|[WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|Unterstützt das Durchlaufen Ihres Workflows, bis eine Bedingung erfüllt ist.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Verwenden der WhileActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65091) \(möglicherweise in englischer Sprache\).|  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] zum Erstellen benutzerdefinierter Aktivitäten finden Sie unter [Developing Custom Activities](http://go.microsoft.com/fwlink?LinkID=65023) und [Verwenden des Aktivitätsdesigners der Vorgängerversion](../workflow-designer/using-the-legacy-activity-designer.md) \(möglicherweise in englischer Sprache\).  
  
## In diesem Abschnitt  
 [Aktivitätsansichten \(Vorgängerversion\)](../workflow-designer/activity-views-legacy.md)  
 Beschreibt die verschiedenen Entwurfsansichten von Aktivitäten.  
  
 [Vorgehensweise: Hinzufügen von Aktivitäten zur Toolbox \(Vorgängerversion\)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)  
 Veranschaulicht das Hinzufügen von Aktivitäten zur Toolbox.  
  
 [Vorgehensweise: Erstellen einer deklarativen Regelbedingung \(Vorgängerversion\)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)  
 Zeigt die Schritte zum Erstellen einer deklarativen Regelbedingung.  
  
 [Vorgehensweise: Erstellen eines PolicyActivity\-Regelsatzes \(Vorgängerversion\)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)  
 Zeigt die Schritte zum Erstellen eines PolicyActivity\-Regelsatzes.  
  
 [Vorgehensweise: Implementieren eines WCF\-Vertragsvorgangs \(Vorgängerversion\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)  
 Zeigt die Schritte zum Implementieren eines [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)]\-Vertragsvorgang.  
  
 [Vorgehensweise: Aufrufen eines WCF\-Vertragsvorgangs \(Vorgängerversion\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)  
 Zeigt die Schritte zum Aufrufen eines [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)]\-Vertragsvorgang.  
  
## Siehe auch  
 [Windows Workflow Foundation\-Aktivitäten](http://go.microsoft.com/fwlink?LinkID=65005)   
 [Entwickeln von Workflows](http://go.microsoft.com/fwlink?LinkID=65010)   
 [Entwickeln von Workflowaktivitäten](http://go.microsoft.com/fwlink?LinkID=65023)