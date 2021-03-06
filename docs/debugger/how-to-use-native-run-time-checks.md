---
title: 'Vorgehensweise: Verwenden von systemeigenen Laufzeitfehlerüberprüfungen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.runtime.errorchecks
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- /RTC compiler option [C++], /O compiler option
- run-time checks, native
- stack, pointer corruption
- stack pointers, corruption
- /O compiler option, /RTC option
- run-time errors, error checks
- O compiler option, /RTC option
- debugger, runtime errors
- variables [debugger], loss of data
- runtime_checks pragma
- variables [debugger], catching dependencies on uninitialized local variables
- run-time errors, debugging
- debugger, native run-time checks
- optimized build option
- RTC compiler option, /O compiler option
- native run-time checks
- run-time checks
- debugging arrays
- stack pointers
- arrays [Visual Studio], debugging
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: f7303cdb1138fb95d7c8abdcc1da0929d4ef894d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-native-run-time-checks"></a>Gewusst wie: Verwenden von systemeigenen Laufzeitprüfungen
In Visual C++ können Sie mit systemeigenen [runtime_checks](/cpp/preprocessor/runtime-checks) häufige Laufzeitfehler abfangen. Beispiele:  
  
-   Beschädigung des Stapelzeigers  
  
-   Überläufe lokaler Arrays  
  
-   Beschädigung des Stapels  
  
-   Abhängigkeiten von nicht initialisierten lokalen Variablen  
  
-   Datenverlust nach einer Zuordnung zu einer kürzeren Variablen  
  
 Wenn Sie **/RTC** mit einem optimierten (**/O**) Build verwenden, wird ein Compilerfehler ausgelöst. Wenn Sie in einem optimierten Build ein `runtime_checks` -Pragma verwenden, hat das Pragma keine Auswirkungen.  
  
 Wenn Sie ein Programm mit aktivierten Laufzeitüberprüfungen debuggen, wird das Programm beim Auftreten eines Laufzeitfehlers standardmäßig unterbrochen und wechselt in den Debugger. Sie können dieses Standardverhalten für jede Laufzeitüberprüfung ändern. Weitere Informationen finden Sie unter [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md).  
  
 In den folgenden Prozeduren wird beschrieben, wie Sie in einem Debugbuild systemeigene Laufzeitüberprüfungen aktivieren und das Verhalten systemeigener Laufzeitüberprüfungen ändern.  
  
 Weitere Themen in diesem Abschnitt enthalten Informationen zu folgenden Vorgängen:  
  
-   [Anpassen von Laufzeitüberprüfungen mit der C-Laufzeitbibliothek](../debugger/native-run-time-checks-customization.md)  
  
-   [Verwenden von Laufzeitüberprüfungen ohne die C-Laufzeitbibliothek](../debugger/using-run-time-checks-without-the-c-run-time-library.md)  
  
### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>So aktivieren Sie systemeigene Laufzeitfehlerüberprüfungen in einem Debugbuild  
  
-   Verwenden Sie die Option **/RTC** , und stellen Sie eine Verknüpfung zu der Debugversion einer C-Laufzeitbibliothek (z. B. /MDd) her.  
  
### <a name="to-modify-native-run-time-check-behavior"></a>So ändern Sie das Verhalten von systemeigenen Laufzeitfehlerüberprüfungen  
  
-   Verwenden Sie das `runtime_checks` -Pragma.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/index.md)  
 [Debugger – Featuretour](../debugger/debugger-feature-tour.md)   
 [runtime_checks](/cpp/preprocessor/runtime-checks)   
 [Laufzeitfehlerüberprüfung](/cpp/c-runtime-library/run-time-error-checking)