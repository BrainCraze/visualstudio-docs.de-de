---
ms.technology: vs-ai-tools
ms.openlocfilehash: 73292b9e0c7df23db839a7a13f70dbc2432d564f
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2018
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Klonen eines Repositorys in Python-Code in Visual Studio

Sobald Sie [die Visual Studio-Tools für KI installiert haben](installation.md), können Sie ganz leicht ein Repository mit Python-Code klonen und daraus ein Projekt erstellen.

1. Um die Verbindung mit GitHub-Repositorys herzustellen, führen Sie den Visual Studio-Installer aus. Klicken Sie auf **Ändern**, und wählen Sie dann die Registerkarte **Einzelne Komponenten** aus. Scrollen Sie runter zum Bereich **Codetools**, klicken Sie auf **GitHub-Erweiterung für Visual Studio** und dann auf **Ändern**.

    ![Auswählen der Erweiterung „GitHub“ im Visual Studio-Installer](media\create-project-repo\installation-github-extension.png)

2. Starten Sie Visual Studio.

3. Klicken Sie auf **Ansicht > Team Explorer…**, um das Fenster **Team Explorer** zu öffnen. Dort können Sie eine Verbindung mit GitHub oder Visual Studio Team Services herstellen oder ein Repository klonen.

    ![Das Team Explorer-Fenster zeigt Visual Studio Team Services, GitHub und das Klonen eines Repositorys](media\create-project-repo\team-explorer.png)

4. Geben Sie `https://github.com/Microsoft/samples-for-ai` im Feld „URL“ unter **Lokale Git-Repositorys** ein. Geben Sie einen Ordner für die geklonten Dateien an, und klicken Sie auf **Klonen**.

    > [!Tip]
    > Der Ordner, den Sie in Team Explorer angeben, empfängt die geklonten Dateien. Im Gegensatz zum Befehl `git clone` wird beim Erstellen eines Klons in Team Explorer nicht automatisch ein Unterordner mit dem Namen des Repositorys erstellt.

5. Wenn der Klonvorgang abgeschlossen ist, doppelklicken Sie auf den Repositoryordner im unteren Bereich von Team Explorer, um zum Repositorydashboard zu navigieren. Klicken Sie unter **Projektmappen** auf **Neu...**.

    ![Das Fenster „Team Explorer“, in dem ein neues Projekt aus einem Klon erstellt wird](media\create-project-repo\team-explorer-new-project.png)

6. Klicken Sie in dem Dialogfeld **Neues Projekt** auf **Aus vorhandenem Python-Code**. Geben Sie einen Namen für das Projekt an, legen Sie für **Speicherort** denselben Ordner fest, in dem auch das Repository gespeichert ist, und klicken Sie auf **OK**. Klicken Sie in dem sich öffnenden Assistenten auf **Fertig stellen**.

7. Klicken Sie im Menü auf **Ansicht > Projektmappen-Explorer**.

8. Erweitern Sie im Projektmappen-Explorer den Knoten `TensorFlow Examples> MNIST`. Klicken Sie mit der rechten Maustaste zunächst auf `convolutional.py`, und klicken Sie anschließend auf **Als Startdatei festlegen**. Bei diesem Schritt meldet Visual Studio, welche Datei beim Ausführen des Projekts verwendet werden soll.

10. Drücken Sie STRG+F5, oder klicken Sie auf **Debuggen > Ohne Debuggen starten**, um das Programm auszuführen. Wenn Ihnen ein ` angezeigt wird, prüfen Sie die Einstellungen für das Arbeitsverzeichnis im nächsten Schritt erneut.


11. Wenn das Programm erfolgreich ausgeführt wird, beginnt es mit dem Herunterladen des Trainings- und Testdatasets. Anschließend wird das Modell trainiert und die Fehlerquote ausgegeben. Sie möchten, dass die Fehlerquote mit der Zeit abnimmt.

    ![Erste Ausgabe des Python MNIST-Programms](media\create-project-repo\tensorflow-mnist-running.png)

> Wenn Sie Anaconda verwenden und eine Fehlermeldung über fehlendes „numpy“ erhalten, müssen Sie möglicherweise [Ihre Python-Umgebung auf die Verwendung von Anaconda umstellen](../python/selecting-a-python-environment-for-a-project.md).

11. Sie können den Fortschritt mit TensorBoard verfolgen. Klicken Sie mit der rechten Maustaste auf Ihr Projekt, und klicken Sie dann auf **Run TensorBoard**. Wählen Sie das Verzeichnis der ausgegebenen TensorBoard-Protokolle aus.

    ![Ausführen von TensorBoard](media\create-project-repo\run-tensorboard.png)

11. Beachten Sie, dass Fehler mit der Zeit abnehmen, was bedeutet, dass sich die Qualität verbessert.

    ![Ausführen von TensorBoard](media\create-project-repo\tensorboard.png)