---
title: "IEEVisualizerService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerService"
helpviewer_keywords: 
  - "IEEVisualizerService-Schnittstelle"
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IEEVisualizerService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle implementiert Methoden, die Funktionen zum Angeben der [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) und [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) Schnittstellen.  
  
## Syntax  
  
```  
IEEVisualizerService : IUnknown  
```  
  
## Hinweise für Implementierer  
 Visual Studio implementiert diese Schnittstelle, um eine Auswertung eines Ausdrucks \(EE\) Typ Schnellansichten unterstützen können.  
  
## Hinweise für Aufrufer  
 Die Aufrufe EE [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) dieser Schnittstelle als Bestandteil der Unterstützung für Typ Schnellansichten abgerufen.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Ruft die Anzahl der benutzerdefinierten Viewer diesen Dienst kennt ab.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Ruft die Liste der benutzerdefinierten Viewer.|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Ein Proxyobjekt für eine Eigenschaft zurückgegeben.|  
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Ruft die Anzahl der Wertzeichenfolgen für die angegebene Eigenschaft oder das Feld angezeigt.|  
  
## Hinweise  
 Die IDE verwendet die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) Schnittstelle, um zu bestimmen, ob alle benutzerdefinierten Viewer, oder geben Sie Schnellansichten für die Eigenschaft. Durch Erstellen eines Schnellansicht\-Diensts \(mit [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)\), die EE kann die Funktionen zum Angeben der `IDebugProperty3` und [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) \(dem unterstützt anzeigen und ändern den Wert einer Eigenschaft\) Schnittstellen, und somit Typ Schnellansichten.  
  
 Verfügt ein EE benutzerdefinierten Viewer, die selbst implementiert wird, kann die EE Anfügen der `CLSID`s von diesen benutzerdefinierten Viewer an das Ende der Liste von zurückgegebenen [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). Dies ermöglicht eine EE Typ Schnellansichten und einen eigenen benutzerdefinierten Viewer unterstützt. Nur darauf achten, [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) zusätzlich alle benutzerdefinierten Viewer widerspiegelt.  
  
 Finden Sie unter [Typ\-Schnellansicht und benutzerdefinierten Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) eine Erläuterung des Unterschieds zwischen Schnellansichten und Viewer.  
  
## Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Ausdruck Evaluation\-Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [Typ\-Schnellansicht und benutzerdefinierten Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)