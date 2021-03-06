---
title: 'Vorgehensweise: Öffnen von Office-Projektmappen ohne Ausführen von Code | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 86a44d2a6c82f65d91c558c76743a8fbbd2fa1e8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Gewusst wie: Öffnen von Office-Projektmappen ohne die Ausführung von Code
  Mit Erweiterungen durch verwalteten Code erstellte eine Microsoft Office-Projektmappe ausgeführt wird, auch wenn die Einstellung "Sicherheit" in der Endbenutzer-Office-Anwendung auf "High" festgelegt ist. Dies ist, da die Sicherheit von Microsoft .NET Framework, nicht durch Microsoft Office verwaltet wird.  
  
 Es gibt jedoch Situationen Sie möglicherweise ein Dokument zu öffnen, ohne den Code ausführen. Beispielsweise Code, der ausgeführt wird, wenn das Dokument geöffnet wird, möglicherweise den Inhalt ändern, aber die Möglichkeit des Dokuments sucht vor der Methodencode ändert, aktualisiert werden soll. Oder Sie das Dokument mit bestimmten Informationen darin an eine Person senden möchten, und nicht möchten, dass des Codes zum Ausführen und den Inhalt möglicherweise ändern.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Es gibt mehrere Möglichkeiten, ein Dokument oder eine Arbeitsmappe mit Erweiterungen durch verwalteten Code ohne Ausführung den Assemblycode zu öffnen.  
  
### <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>So umgehen Sie die Assembly mithilfe der UMSCHALTTASTE  
  
-   Öffnen von Dokumenten und Arbeitsmappen aus der **Datei** Menü halten Sie die UMSCHALTTASTE gedrückt, um zu verhindern, dass Word und Excel Initialisierungsereignisse auslösen, während das Dokument geöffnet wird.  
  
    > [!NOTE]  
    >  Wenn Sie ein Dokument oder eine Arbeitsmappe öffnen die **Einstieg** Aufgabenbereich, der Sie die UMSCHALTTASTE gedrückt halten, wird den Code nicht umgangen. Darüber hinaus verhindert die UMSCHALTTASTE gedrückt nicht Ereignisse ausgelöst werden, nachdem das Dokument geöffnet ist.  
  
     Diese Methode ist nützlich, wenn Sie ein Dokument, um Änderungen vorzunehmen, ohne den Code ausführen und ändern das Dokument zuerst öffnen möchten.  
  
### <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Um eine Assembly durch das Umbenennen oder entfernen es umgehen  
  
-   Wenn Sie die erforderlichen Berechtigungen auf dem Computer verfügen, auf dem sich die Assembly befindet, können Sie Sie umbenennen oder entfernen Sie die Assembly, sodass das Dokument oder die Arbeitsmappe gefunden werden kann. Dies führt zu einem Fehler, die ausgelöst wird, jedes Mal, wenn das Office-Dokument geöffnet wird.  
  
     Wenn die Lösung von mehreren Personen verwendet wird, verhindert diese Methode die Projektmappe ausgeführt wird für jede von ihnen. Dies kann nützlich sein, wenn ein Problem im Code oder eine referenzierte Server gefunden wird und Sie alle Benutzer aus der Ausführung beenden möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Bereitstellen einer Office-Lösung](../vsto/deploying-an-office-solution.md)   
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)   
 [Anwendungs- und Bereitstellungsmanifeste in Office-Projektmappen](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  