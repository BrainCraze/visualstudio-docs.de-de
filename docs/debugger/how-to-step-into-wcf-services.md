---
title: 'Vorgehensweise: Schritt in WCF-Dienste | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e8b915401832887414985fcddd0581e01d9fb481
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-step-into-wcf-services"></a>Gewusst wie: Ausführen eines Einzelschritts in WCF-Dienste
In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] können Sie einen Einzelschritt in einen WCF-Dienst ausführen. Wenn sich der WCF-Dienst in derselben [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projektmappe wie der Client befindet, erreichen Sie Haltepunkte innerhalb des WCF-Dienstes.  
  
 Damit dies funktioniert, müssen Sie das Debuggen in der Datei app.config oder Web.config aktivieren. Informationen zum Aktivieren des Debuggens und Informationen zu Einschränkungen bei der schrittweisen WCF-Diensten finden Sie unter [Einschränkungen beim WCF-Debugging](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-step-into-a-wcf-service"></a>So führen Sie einen Einzelschritt in einen WCF-Dienst aus  
  
1.  Erstellen Sie eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projektmappe, die sowohl den WCF-Client als auch WCF-Dienstprojekte enthält.  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste des WCF-Clientprojekts, und klicken Sie dann auf **als Startprojekt festlegen**.  
  
3.  Aktivieren Sie das Debuggen in der Datei app.config oder web.config. Weitere Informationen finden Sie unter [Einschränkungen beim WCF-Debugging](../debugger/limitations-on-wcf-debugging.md).  
  
4.  Setzen Sie an der Stelle im Clientprojekt, an der Sie die schrittweise Ausführung beginnen möchten, einen Haltepunkt. Üblicherweise wird dies vor dem Aufruf des WCF-Diensts sein.  
  
5.  Ausführen bis zum Haltepunkt, dann Beginnen der schrittweisen Ausführung. Der Debugger führt die schrittweise Ausführung des Diensts automatisch durch.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von WCF-Diensten](../debugger/debugging-wcf-services.md)   
 [Einschränkungen beim WCF-Debugging](../debugger/limitations-on-wcf-debugging.md)   
 [Gewusst wie: Debuggen eines lokal gehosteten WCF-Diensts](../debugger/how-to-debug-a-self-hosted-wcf-service.md)