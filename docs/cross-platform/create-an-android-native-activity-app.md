---
title: Erstellen einer Android Native Activity-App | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 884014b1-5208-45ec-b0da-ad0070d2c24d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: e03fb8fd62e7f9b2e37dfc2efe8f02580c7b32f5
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="create-an-android-native-activity-app"></a>Erstellen einer Android Native Activity-App
Bei der Installation der Option "Visual C++ für plattformübergreifende Mobile-Entwicklung" kann Visual Studio 2015 verwendet werden, um voll funktionsfähige Android Native Activity-Apps zu erstellen. Das Android Native Development Kit (NDK) ist ein Toolset, mit dem Sie die überwiegende Anzahl von Android-Apps mit reinem C/C++-Code implementieren können. Mancher Java-JNI-Code fungiert als Verbindungscode, der dem C/C++-Code die Interaktion mit Android ermöglicht. Mit dem Android NDK wurde die Fähigkeit zum Erstellen von Native Activity-Apps mit Android-API Level 9 eingeführt. Native Activity-Code wird häufig zum Erstellen von Spielen und grafikintensiven Apps verwendet, die auf Unreal Engine oder OpenGL basieren. Dieses Thema führt Sie durch Erstellung einer einfachen Native Activity-App, die OpenGL verwendet. Zusätzliche Themen führen Sie durch den Entwicklerlebenszyklus bestehend aus dem Bearbeiten, Erstellen, Debuggen und Bereitstellen von Native Activity-Code.  
  
 [Anforderungen](#req)   
 [Erstellen eines neuen Native Activity-Projekts](#Create)   
 [Generieren und Ausführen der standardmäßigen Android Native Activity-App](#BuildHello)  
  
##  <a name="req"></a> Anforderungen  
 Vor der Erstellung einer Android Native Activity-App müssen Sie sicherstellen, dass Sie alle Systemvoraussetzungen erfüllen und die Option "Visual C++ Mobile-Entwicklung" in Visual Studio 2015 installiert haben. Weitere Informationen finden Sie unter [Install Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Stellen Sie sicher, dass die erforderlichen Drittanbietertools und -SDKs in der Installation enthalten sind und dass der Microsoft Visual Studio-Emulator für Android installiert ist.  
  
##  <a name="Create"></a> Erstellen eines neuen Native Activity-Projekts  
 In diesem Tutorial erstellen Sie zunächst ein neues Android Native Activity-Projekt. Anschließend erstellen und führen Sie die Standard-App im Visual Studio-Emulator für Android aus.  
  
#### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Öffnen Sie Visual Studio. Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.  
  
2.  Wählen Sie im Dialogfeld **Neues Projekt** unter **Vorlagen**die Option **Visual C++**, **Plattformübergreifend**und dann die Vorlage **Native-Activity Application (Android)** aus.  
  
3.  Vergeben Sie an die App einen Namen wie etwa `MyAndroidApp`(ohne Leerzeichen), und wählen Sie dann **OK**.  
  
     ![Erstellen eines Native Activity-Projekts](../cross-platform/media/cppmdd_newproject.PNG "CppMDD_NewProject")  
  
     Visual Studio erstellt die neue Projektmappe und öffnet den Projektmappen-Explorer.  
  
     ![Native Activity-Projekt im Projektmappen-Explorer](../cross-platform/media/cppmdd_rc_na_solutionexp.PNG "CPPMDD_RC_NA_SolutionExp")  
  
 Die neue Android Native Activity-App-Projektmappe enthält zwei Projekte:  
  
-   **MyAndroidApp.NativeActivity** enthält die Verweise und den Verbindungscode, damit Ihre App als eine systemeigene Aktivität auf Android ausgeführt werden kann. Die Implementierung der Einstiegspunkte aus dem Verbindungscode befindet sich in "main.cpp". Vorkompilierte Header befinden sich in "pch.h". Das Native Activity-App-Projekt wird in eine freigegebene Bibliotheksdatei (SO) kompiliert, die durch das Paketprojekt ausgewählt wird.  
  
-   **MyAndroidApp.Packaging** erstellt die APK-Datei für die Entwicklung auf einem Android-Gerät oder -Emulator. Dieses enthält die Ressourcen und die Datei "AndroidManifest.xml", wo Sie Manifesteigenschaften festlegen. Es enthält zudem die Datei "build.xml", die den Ant-Buildprozess steuert. Es ist standardmäßig als Startprojekt festgelegt, sodass es bereitgestellt und direkt in Visual Studio ausgeführt werden kann.  
  
##  <a name="BuildHello"></a> Generieren und Ausführen der standardmäßigen Android Native Activity-App  
 Erstellen und führen Sie die App aus, die durch die Vorlage generiert wurde, um Ihre Installation und Einrichtung zu überprüfen. Führen Sie die App in diesem ersten Test unter einem der Geräteprofile aus, die vom Visual Studio-Emulator für Android installiert werden. Wenn Sie Ihre App auf einem anderen Ziel testen möchten, können Sie den Zielemulator laden oder das Gerät mit Ihrem Computer verbinden.  
  
#### <a name="to-build-and-run-the-default-native-activity-app"></a>So erstellen Sie die standardmäßige Native Activity-App und führen diese aus  
  
1.  Falls die Plattform noch nicht ausgewählt ist, wählen Sie **x86** aus der Dropdownliste **Projektmappenplattformen** aus.  
  
     ![Dropdownliste für Lösungsplattformen mit x86-Auswahl](../cross-platform/media/cppmdd_rc_na_solution_x86.png "CPPMDD_RC_NA_Solution_x86")  
  
     Wenn die Liste **Projektmappenplattformen** nicht angezeigt wird, wählen Sie **Projektmappenplattformen** aus der Liste **Schaltflächen hinzufügen/entfernen** aus, und wählen Sie dann Ihre Plattform.  
  
2.  Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
     Das Fenster "Ausgabe" zeigt die Ausgabe des Buildprozesses für die zwei Projekte in der Projektmappe an.  
  
3.  Wählen Sie eines der VS-Emulator Android Phone (x86)-Profile als Bereitstellungsziel aus.  
  
     Wenn Sie andere Emulatoren installiert oder mit einem Android-Gerät verbunden haben, können Sie sie aus der Bereitstellungsziel-Dropdownliste auswählen.  
  
4.  Drücken Sie F5, um mit dem Debuggen zu beginnen, oder UMSCHALT+F5, um ohne Debuggen zu beginnen.  
  
     So in etwa sieht die Standard-App im Visual Studio-Emulator für Android aus.  
  
     ![Der Emulator, der Ihre App ausführt](../cross-platform/media/cppmdd_emulator_running_app.PNG "CppMDD_Emulator_Running_App")  
  
     Visual Studio startet den Emulator, wobei das Laden und Bereitstellen Ihres Codes einige Sekunden in Anspruch nimmt. Nachdem Ihre App gestartet wurde, können Sie Haltepunkte festlegen und den Debugger verwenden, um den Code schrittweise zu durchlaufen, lokale Variablen zu prüfen und Werte anzuzeigen.  
  
5.  Drücken Sie UMSCHALTTASTE+F5, um das Debuggen zu beenden.  
  
     Der Emulator ist ein separater Prozess, der weiterhin ausgeführt wird. Sie können Ihren Code mehrfach auf demselben Emulator bearbeiten, kompilieren und bereitstellen.