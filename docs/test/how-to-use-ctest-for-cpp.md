---
title: "Verwenden von CTest für C++ in Visual Studio | Microsoft-Dokumentation"
ms.date: 11/07/2017
ms.technology: vs-ide-test
ms.topic: article
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 602240df366d9ee978f632a8693bae3de21fcedf
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Verwenden von CTest für C++ in Visual Studio

CMake (schließt CTest mit ein) ist standardmäßig als Komponente der Workload **Desktopentwicklung mit C++** in die Visual Studio-IDE integriert. Wenn Sie diese auf Ihrem Computer installieren müssen, öffnen Sie den Visual Studio-Installer, klicken auf die Schaltfläche **Ändern** und suchen nach [CMake Tools für Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) in der Liste der Workloadkomponenten.

## <a name="to-write-tests"></a>Schreiben von Tests

Die CMake-Unterstützung in Visual Studio umfasst nicht das Visual Studio-Projektsystem. Aus diesem Grund können Sie CTest-Tests auf dieselbe Weise wie in einer CMake-Umgebung schreiben und konfigurieren. Weitere Informationen zu CMake in Visual Studio finden Sie unter [CMake Tools für Visual C++](/cpp/ide/cmake-tools-for-visual-cpp).

## <a name="to-run-tests-visual-studio-2017-version-156"></a>Ausführen von Tests (Visual Studio 2017 Version 15.6)

In Visual Studio 2017 Version 15.6 ist CTest vollständig im **Test-Explorer** integriert und unterstützt außerdem die Komponententestframeworks von Google und Boost. Diese Frameworks sind standardmäßig als Komponenten in der Workload **Desktopentwicklung mit C++** enthalten. Wenn Sie jedoch ein Projekt aus einer älteren Version von Visual Studio aktualisieren, müssen Sie diese Frameworks möglicherweise mithilfe des Visual Studio-Installer installieren.

Die folgende Abbildung zeigt die Ergebnisse eines CTest-Durchlaufs, der mit einem Google-Testframework ausgeführt wurde:

![CTest mit Google-Testframework in VS2017 15.6](media/ctest-test-explorer.png "CTest und Google-Test im Test-Explorer")

Wenn Sie CTest, aber nicht die Google- oder Boost-Adapter verwenden, sehen Sie die Ergebnisse auf der CTest-Ebene statt auf der Ebene der einzelnen Testmethoden. Sie können ausführbare CTest-Dateien debuggen und diese durchlaufen, aber Stapelüberwachungen für einzelne Tests werden nicht unterstützt.

## <a name="to-run-tests-visual-studio-2017-version-155"></a>Ausführen von Tests (Visual Studio 2017 Version 15.5)

In **Visual Studio 2017 Version 15.5** ist CTest nicht in den **Test-Explorer** integriert. Sie können Ihre Tests über das CMake-Hauptmenü oder über das Kontextmenü in einer **CMakeLists.txt**-Datei im **Projektmappen-Explorer** ausführen. Die Testergebnisse werden an das Visual Studio-**Ausgabefenster** weitergeleitet.

![Ausführen von CTest-Tests in VS2017 15.5](media/cpp-cmake-run-tests.png "Ausführen von CTest-Tests in 15.5")

## <a name="see-also"></a>Siehe auch

[Schreiben von Komponententests für C/C++](writing-unit-tests-for-c-cpp.md)