---
title: Bereitstellen der erforderlichen Komponenten für 64-Bit-Anwendungen | Microsoft Docs
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
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 5efadda5db025e6229fbebd252ff34bf3fa1fe17
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="deploying-prerequisites-for-64-bit-applications"></a>Bereitstellen der erforderlichen Komponenten für 64-Bit-Anwendungen
Die ClickOnce-Bereitstellung unterstützt die Installation von Anwendungen auf 64-Bit-Plattformen. Die Zielplattformen sind **X86** für 32-Bit-Plattformen **X64** für Computer, die die Anweisungssets AMD64 und EM64T unterstützen und **Itanium** für die 64-Bit-Itanium-Prozessor.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 In der folgenden Tabelle sind die verteilbaren Komponenten aufgeführt, die Sie als erforderliche Komponenten für die Installation Ihrer 64-Bit-Anwendung verwenden können.  
  
 Wenn Sie eine erforderliche Komponente auswählen, für die keine 64-Bit-Komponenten vorhanden sind, wird möglicherweise eine Warnung angezeigt, die darauf hinweist, dass die ausgewählten Pakete für die 64-Bit-Plattform nicht verfügbar sind.  
  
|Verteilbare Komponente|x64-Unterstützung|IA64-Unterstützung|  
|---------------------|-----------------|------------------|  
|[!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)]|Ja|Nein|  
|Visual C++ 2010-Laufzeitbibliotheken (IA64)|Nein|Ja|  
|Visual C++ 2010-Laufzeitbibliotheken (x64)|Ja|Nein|  
|Microsoft .NET Framework 4 (x86 und x64)|Ja||  
|Microsoft .NET Framework 4 Client Profile (x86 und x64)|Ja||  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von Anwendungen, Diensten und Komponenten](../deployment/deploying-applications-services-and-components.md)   
 [Vorgehensweise: Installieren von erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [64-Bit-Anwendungen](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)