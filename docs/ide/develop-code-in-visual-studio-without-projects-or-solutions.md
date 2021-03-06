---
title: Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen | Microsoft-Dokumentation
ms.date: 02/21/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
helpviewer_keywords:
- open folder [Visual Studio]
- anycode [Visual Studio]
- projects and solutions, develop code without
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 08c50a07992a1856ad0d5f45c0200e0b8a232cb7
ms.sourcegitcommit: 3abca1c733af876c8146daa43a62e829833be280
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/23/2018
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen

In Visual Studio 2017 können Sie Code von Directory-basierten Projekten nahezu jeder Art öffnen, ohne dass eine Projektmappen- oder Projektdatei erforderlich ist. Das bedeutet, dass Sie z.B. ein Repository in GitHub klonen, es direkt in Visual Studio öffnen und mit der Entwicklung beginnen können, ohne eine Projektmappe oder ein Projekt erstellen zu müssen. Bei Bedarf können Sie mithilfe einfacher JSON-Dateien benutzerdefinierte Buildtasks und Startparameter angeben.

Nach dem Öffnen der Codedateien in Visual Studio zeigt der Projektmappen-Explorer alle Dateien im Ordner an. Sie können auf eine beliebige Datei klicken, um mit der Bearbeitung zu beginnen. Visual Studio beginnt im Hintergrund damit, die Dateien zu indizieren, um IntelliSense, Navigation und Refactoringfunktionen zu ermöglichen. Während Sie Dateien bearbeiten, erstellen, verschieben und löschen, verfolgt Visual Studio die Änderungen automatisch nach und aktualisiert den IntelliSense-Index kontinuierlich. Der Code wird mit Syntaxfarbgebung angezeigt und beinhaltet in vielen Fällen eine grundlegende Anweisungsvervollständigung per IntelliSense.

## <a name="open-any-code"></a>Öffnen von beliebigem Code

Sie können Code in Visual Studio auf eine der folgenden Arten öffnen:

- Wählen Sie in der Visual Studio-Menüleiste die Einträge **Datei** > **Öffnen** > **Ordner**, und navigieren Sie zum Codespeicherort.
- Wählen Sie im Kontextmenü (Rechtsklick) eines Ordners, der Code enthält, den Befehl **In Visual Studio öffnen** .
- Wählen Sie den Link **Ordner öffnen** auf der Visual Studio-Startseite.
- Wenn Sie eine Tastatur verwenden, drücken Sie in Visual Studio die Tasten **STRG**+**UMSCHALT**+**ALT**+**O**.
- Öffnen Sie Code aus einem geklonten GitHub-Repository.

### <a name="to-open-code-from-a-cloned-github-repo"></a>So öffnen Sie Code aus einem geklonten GitHub-Repository

Das folgende Beispiel zeigt, wie ein GitHub-Repository geklont und dann sein Code in Visual Studio geöffnet wird. Um diese Schritte auszuführen, müssen ein GitHub-Konto und Git für Windows auf Ihrem System installiert sein. Unter [Signing up for a new GitHub account](https://help.github.com/articles/signing-up-for-a-new-github-account/) (Registrieren für ein neues GitHub-Konto) und [Git for Windows](https://git-for-windows.github.io/) (Git für Windows) finden Sie weitere Informationen.

1. Wechseln Sie zu dem Repository auf GitHub, das Sie klonen möchten.

1. Klicken Sie auf die Schaltfläche **Clone or Download** (Klonen oder herunterladen), und klicken Sie dann auf die Schaltfläche **Copy to Clipboard** (In Zwischenablage kopieren) im Dropdownmenü, um die sichere URL für das GitHub-Repository zu kopieren.

   ![Klonenschaltfläche in GitHub](./media/VSIDE_Code_Clone.png)

1. Wählen Sie in Visual Studio die Registerkarte **Team Explorer**, um Team Explorer zu öffnen. Wenn die Registerkarte nicht angezeigt wird, öffnen Sie sie über **Ansicht** > **Team Explorer**.

1. Wählen Sie in Team Explorer im Abschnitt **Lokale Git-Repositorys** den Befehl **Klonen** aus, und fügen Sie die URL der GitHub-Seite in das Textfeld ein.

   ![Klonen des Projekts](./media/VSIDE_Code_Clone2.png)

1. Wählen Sie die Schaltfläche **Klonen**, um die Dateien des Projekts in einem lokalen Git-Repository zu klonen. Dies kann je nach Größe des Repositorys einige Minuten dauern.

1. Wählen Sie nach dem Klonen des Repositorys auf Ihrem System in Team Explorer den Befehl **Öffnen** im Kontextmenü (Rechtsklick) des neu geklonten Repositorys.

   ![Geklontes Repository](./media/VSIDE_Code_Clone3.png)

1. Wählen Sie den Befehl **Ordneransicht anzeigen** aus, um die Dateien im Projektmappen-Explorer anzuzeigen.

   ![Ordneransicht anzeigen](./media/VSIDE_Code_Clone3_show.png)

   Jetzt können Sie Ordner und Dateien im geklonten Repository durchsuchen und den Code im Code-Editor von Visual Studio anzeigen und durchsuchen, wobei die farbliche Syntaxhervorhebung und andere Funktionen zur Verfügung stehen.

|         |         |
|---------|---------|
|  ![Kamerasymbol für video](../install/media/video-icon.png "Video ansehen")|    [Sehen Sie sich dieses Video an](https://mva.microsoft.com/en-us/training-courses/getting-started-with-visual-studio-2017-17798?l=lp3TOKD6D_6711787171), um zu erfahren, wie Sie Code aus einem GitHub-Repository in Visual Studio klonen und öffnen. |

## <a name="run-and-debug-your-code"></a>Ausführen und Debuggen Ihres Codes

Sie können Ihren Code in Visual Studio ohne ein Projekt oder eine Projektmappe debuggen! Zum Debuggen bestimmter Sprachen benötigen Sie möglicherweise eine gültige *Startdatei* in der Codebasis, z.B. ein Skript, eine ausführbare Datei oder eine Projektdatei. Auf der Symbolleiste werden im Dropdown-Listenfeld neben der Schaltfläche **Start** sowohl alle Startelemente aufgelistet, die Visual Studio erkennt, als auch die Elemente, die Sie speziell bestimmen. Visual Studio führt diesen Code zuerst aus, wenn Sie den Code debuggen.

Die Konfiguration Ihres Codes zur Ausführung in Visual Studio ist unterschiedlich, je nachdem, um welche Art Code es sich handelt und welche Buildtools verwendet werden.

### <a name="codebases-that-use-msbuild"></a>Codebasen mit MSBuild

Für MSBuild-basierte Codebasen können mehrere Buildkonfigurationen existieren, die in der Dropdownliste neben der Schaltfläche **Start** angezeigt werden. Wählen Sie die Datei aus, die Sie als Startelement verwenden möchten, und klicken Sie dann auf die Schaltfläche **Start**, um mit dem Debuggen zu beginnen.

> [!NOTE]
> Bei C#- und Visual Basic-Codebasen muss die Arbeitsauslastung **.NET-Desktopentwicklung** installiert sein. Bei C++-Codebasen muss die Arbeitsauslastung **Desktopentwicklung mit C++** installiert sein.

### <a name="codebases-that-use-custom-build-tools"></a>Codebasen mit benutzerdefinierten Buildtools

Wenn Ihre Codebasis benutzerdefinierte Buildtools verwendet, müssen Sie Visual Studio mithilfe von in einer *JSON*-Datei definierten *Buildtasks* mitteilen, wie der Code kompiliert werden soll. Weitere Informationen finden Sie unter [Anpassen von Build- und Debugtasks](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

### <a name="codebases-that-contain-python-or-javascript-code"></a>Codebasen mit Python- oder JavaScript-Code

Wenn Ihre Codebasis Python- oder JavaScript-Code enthält, müssen Sie keine *JSON*-Dateien konfigurieren, aber Sie müssen die entsprechende Arbeitsauslastung installieren. Sie müssen auch das Startskript konfigurieren:

1. Installieren Sie die Arbeitsauslastung [Node.js-Entwicklung](https://www.visualstudio.com/vs/node-js/) oder [Python-Entwicklung](https://www.visualstudio.com/vs/python/), indem Sie **Tools** > **Tools und Features abrufen...** auswählen oder indem Sie Visual Studio schließen und das Visual Studio-Installationsprogramm ausführen.

   ![Arbeitsauslastungen für die Entwicklung mit Node.js und Python](media/python_nodejs_workloads.png)

1. Wählen Sie im **Projektmappen-Explorer**-Kontextmenü einer JavaScript- oder Python-Datei den Befehl **Als Startelement festlegen**.

1. Klicken Sie auf die Schaltfläche **Start**, um mit dem Debuggen zu beginnen.

### <a name="codebases-that-contain-c-code"></a>Codebasen mit C++-Code

Informationen zum Öffnen von C++-Code ohne Projektmappen oder Projekte in Visual Studio finden Sie unter [Open Folder-Projekte für C++](/cpp/ide/non-msbuild-projects).

### <a name="codebases-that-contain-a-visual-studio-project"></a>Codebasen mit einem Visual Studio-Projekt

Wenn Ihr Codeordner ein Visual Studio-Projekt enthält, können Sie dieses Projekt als Startelement festlegen.

![Projekt als Startelement festlegen](media/customize-set-project-as-startup-item.png)

Der Text der Schaltfläche **Start** ändert sich und zeigt an, dass das Projekt das Startelement ist.

![Schaltfläche „Start“ mit Projekt](media/customize-start-button-project.png)

## <a name="see-also"></a>Siehe auch

- [Anpassen von Build- und Debugtasks](../ide/customize-build-and-debug-tasks-in-visual-studio.md)
- [Open Folder-Projekte für C++](/cpp/ide/non-msbuild-projects)
- [CMake-Projekte in C++](/cpp/ide/cmake-tools-for-visual-cpp)
- [Writing code in the code and text editor (Schreiben von Code im Code- und Text-Editor)](../ide/writing-code-in-the-code-and-text-editor.md)