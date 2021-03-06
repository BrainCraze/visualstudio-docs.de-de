---
title: 'Vorgehensweise: Programmgesteuertes Öffnen von Visio-Dokumenten | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b5a837b4b12420c65817b6dfb156e0fe47fcdba6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-open-visio-documents"></a>Gewusst wie: Programmgesteuertes Öffnen von Visio-Dokumenten
  Es gibt zwei Methoden zum Öffnen vorhandener Microsoft Office Visio-Dokumente: Öffnen und OpenEx. Die OpenEx-Methode ist identisch mit der Open-Methode, außer dass sie Argumente bereitstellt, in denen der Aufrufer angeben kann, wie das Dokument geöffnet wird.  
  
 Ausführliche Informationen zum Objektmodell finden Sie in der VBA-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Documents.Open](https://msdn.microsoft.com/library/office/ff765240.aspx) - und [Microsoft.Office.Interop.Visio.Documents.OpenEx](https://msdn.microsoft.com/library/office/ff767229.aspx) -Methode.  
  
## <a name="opening-a-visio-document"></a>Öffnen von Visio-Dokumenten  
  
#### <a name="to-open-a-visio-document"></a>So öffnen Sie ein Visio-Dokument  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Documents.Open-Methode, und geben Sie den vollqualifizierten Pfad des Visio-Dokuments.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="opening-a-visio-document-with-specified-arguments"></a>Öffnen eines Visio-Dokuments mit angegebenen Argumenten  
  
#### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>So öffnen Sie ein Visio-Dokument schreibgeschützt und angedockt  
  
-   Die Microsoft.Office.Interop.Visio.Documents.OpenEx-Methode aufrufen, geben Sie den vollqualifizierten Pfad des Visio-Dokuments und schließen Sie die Argumente, die Sie verwenden möchten – in diesem Fall "gedockt" und schreibgeschützt.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Für dieses Codebeispiel benötigen Sie Folgendes:  
  
-   Ein Visio-Dokument namens `myDrawing.vsd` muss sich in einem Verzeichnis namens `Test` im Ordner „Eigene Dateien“ (Windows XP und ältere Versionen) bzw. im Ordner „Dokumente“ (Windows Vista) befinden.  
  
## <a name="see-also"></a>Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Visio-Objektmodellübersicht](../vsto/visio-object-model-overview.md)   
 [Vorgehensweise: Programmgesteuertes Erstellen neuer Visio-Dokumente](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Vorgehensweise: Programmgesteuertes Schließen von Visio-Dokumenten](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Vorgehensweise: Programmgesteuertes Speichern von Visio-Dokumenten](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Vorgehensweise: Programmgesteuertes Drucken von Visio-Dokumenten](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  