---
title: '&lt;Zeitpläne&gt; Element (Bootstrapper) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 2b3cba1fcb5ac2d38b08383c8906adb2037e9651
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Zeitpläne&gt; Element (Bootstrapper)
Die `Schedules` Element enthält `Schedule` Elementen, die bestimmte Zeitpunkten, an welche Befehle definiert, indem Sie definieren die `Command` Element ausgeführt werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Die `Schedules` Element ist ein untergeordnetes Element von der `Product` Element. Jede `Product` Element möglicherweise höchstens ein `Schedules` Element. Die `Schedules` -Element weist keine Attribute.  
  
## <a name="schedule"></a>Zeitplan  
 Die `Schedule` Element ist ein untergeordnetes Element von der `Schedules` Element. Ein `Schedules` -Element muss mindestens eine aufweisen `Schedule` Element.  
  
 `Schedule` hat das folgende Attribut.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Name`|Erforderlich. Der Name des Zeitplanelements. Dies entspricht der `ScheduleName` Eigenschaft von der `Command` Element. Wenn eine `Command` verweist auf den benannten Zeitplan wird nur die zum Zeitpunkt der erkennbar, die ausgeführt werden `Schedule` Element. Zeitpläne können auch zugeordnete der `FailIf` und `BypassIf` -Elemente, die diese bedingten Tests zu beschränken, auf dem angegebenen Zeitplan ausgeführt. Weitere Informationen finden Sie unter [ \<Befehle >-Element](../deployment/commands-element-bootstrapper.md).|  
  
 Ein angegebener `Schedule` Element möglicherweise genau eines der folgenden untergeordneten Elemente.  
  
## <a name="buildlist"></a>BuildList  
 Die `BuildList` -Element weist das Installationsprogramm zur Ausführung eines Befehls unmittelbar nach die bootstrapping-Anwendung gestartet wird.  
  
## <a name="beforepackage"></a>BeforePackage  
 Die `BeforePackage` Element weist den Installer, um einen Befehl ausführen, bevor das angegebene Paket installiert wird.  
  
## <a name="afterpackage"></a>AfterPackage  
 Die `AfterPackage` Element weist den Installer, um einen Befehl ausführen, nachdem das angegebene Paket installiert ist.  
  
## <a name="see-also"></a>Siehe auch  
 [\<Product >-Element](../deployment/product-element-bootstrapper.md)   
 [Referenz zum Produkt- und Paketschema](../deployment/product-and-package-schema-reference.md)