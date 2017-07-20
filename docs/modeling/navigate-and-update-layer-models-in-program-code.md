---
title: Navigieren in und Aktualisieren von Ebenenmodellen im Programmcode | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 20
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 626fc2b217285ae0c79dbd57f925281e10a0efbb
ms.lasthandoff: 02/22/2017

---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Navigieren in und Aktualisieren von Ebenenmodellen im Programmcode
In diesem Thema werden die Elemente und Beziehungen in Ebenenmodellen beschrieben, die Sie mithilfe von Programmcode durchsuchen und aktualisieren können. Weitere Informationen zu Abhängigkeitsdiagramme aus Sicht des Benutzers, finden Sie unter [Abhängigkeitsdiagramme: Verweis](../modeling/layer-diagrams-reference.md) und [Abhängigkeitsdiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md).  
  
 Die <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer>in diesem Thema beschriebenen Modell ist eine Fassade eines allgemeineren <xref:Microsoft.VisualStudio.GraphModel>Modell.</xref:Microsoft.VisualStudio.GraphModel> </xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer> Beim Schreiben einer [Menü Befehls- oder Gestenhandler-Erweiterung](../modeling/add-commands-and-gestures-to-layer-diagrams.md), verwenden Sie die `Layer` Modell. Beim Schreiben einer [layer-validierungserweiterung](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), ist es einfacher zu verwenden die `GraphModel`.  
  
## <a name="transactions"></a>Transaktionen  
 Erwägen Sie beim Aktualisieren eines Modells die Änderungen in eine `ILinkedUndoTransaction` einzuschließen. Auf diese Weise werden die Änderungen zu einer Transaktion gruppiert. Wenn eine der Änderungen fehlschlägt, wird die gesamte Transaktion zurückgesetzt. Wenn der Benutzer eine Änderung rückgängig macht, werden alle Änderungen zusammen rückgängig gemacht.  
  
```  
using (ILinkedUndoTransaction t =  
        LinkedUndoContext.BeginTransaction("a name"))  
{   
    // Make changes here ....  
    t.Commit(); // Don't forget this!  
}  
```  
  
## <a name="containment"></a>Kapselung  
 ![ILayer und ILayerModel können beide ILAYER enthalten. ] (../modeling/media/layerapi_containment.png "LayerApi_Containment")  
  
 Ebenen (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>) und das Ebenenmodell (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>) können Kommentare und Ebenen enthalten.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel> </xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>  
  
 Eine Ebene (`ILayer`) kann in einem Ebenenmodell (`ILayerModel`) enthalten sein oder in einer anderen `ILayer` geschachtelt werden.  
  
 Verwenden Sie die Erstellungsmethoden für den entsprechenden Container, um einen Kommentar oder eine Ebene zu erstellen.  
  
## <a name="dependency-links"></a>Abhängigkeitslinks  
 Ein Abhängigkeitslink wird durch ein Objekt dargestellt. Er kann in beide Richtungen navigiert werden:  
  
 ![Ein ILayerDependencyLink verbindet zwei ILAYER. ] (../modeling/media/layerapi_dependency.png "LayerApi_Dependency")  
  
 Rufen Sie `source.CreateDependencyLink(target)` auf, um einen Abhängigkeitslink zu erstellen.  
  
## <a name="comments"></a>Kommentare  
 Kommentare können auf Ebenen oder im Ebenenmodell enthalten sein. Zudem können sie mit beliebigen anderen Ebenenelementen verknüpft werden:  
  
 ![Kommentare können jedem Ebenenelement hinzugefügt werden. ] (../modeling/media/layerapi_comments.png "LayerApi_Comments")  
  
 Ein Kommentar kann mit einer beliebigen Anzahl von Elementen sowie auch mit keinem Element verknüpft werden.  
  
 Verwenden Sie Folgendes, um die Kommentare abzurufen, die einem Ebenenelement zugeordnet sind:  
  
```c#  
ILayerModel model = diagram.GetLayerModel();   
IEnumerable<ILayerComment> comments =   
   model.Comments.Where(comment =>   
      comment.Links.Any(link => link.Target == layerElement));  
  
```  
  
> [!CAUTION]
>  Die `Comments`-Eigenschaft einer `ILayer` ruft die Kommentare ab, die in `ILayer` enthalten sind. Es werden nicht die mit ihr verknüpften Kommentare abgerufen.  
  
 Erstellen Sie einen Kommentar, indem Sie `CreateComment()` im entsprechenden Container aufrufen.  
  
 Erstellen Sie einen Link, indem Sie `CreateLink()` auf den Kommentar anwenden.  
  
## <a name="layer-elements"></a>Ebenenelemente  
 Alle Elementtypen, die in einem Modell enthalten sein können, sind Ebenenelemente:  
  
 ![Abhängigkeit Diagramm Inhalt sind ILayerElements. ] (../modeling/media/layerapi_layerelements.png "LayerApi_LayerElements")  
  
## <a name="properties"></a>Eigenschaften  
 Jedes `ILayerElement` verfügt über ein Zeichenfolgenwörterbuch namens `Properties`. Über dieses Wörterbuch können Sie willkürliche Informationen an ein beliebiges Ebenenelement anfügen.  
  
## <a name="artifact-references"></a>Artefaktverweise  
 Ein Artefaktverweis (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>) stellt den Link zwischen einer Ebene und einem Projektelement, z. B. eine Datei, die Klasse oder den Ordner.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference> Der Benutzer erstellt Artefakte, beim Erstellen einer Ebene oder durch Ziehen von Elementen aus dem Projektmappen-Explorer, Klassenansicht oder Objektkatalog in ein Abhängigkeitsdiagramm hinzufügen. Mit einer Ebene kann eine beliebige Anzahl von Artefaktverweisen verknüpft werden.  
  
 Jede Zeile im Ebenen-Explorer zeigt einen Artefaktverweis an. Weitere Informationen finden Sie unter [erstellen Sie Abhängigkeitsdiagramme aus dem Code](../modeling/create-layer-diagrams-from-your-code.md).  
  
 Folgende hauptsächliche Typen und Methoden sind von Artefaktverweisen betroffen:  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference> Die Eigenschaft „Kategorien“ gibt an, welche Art von Artefakt referenziert wird, z. B. Klasse, ausführbare Datei oder Assembly. Die Kategorien bestimmen, wie der Bezeichner das Zielartefakt identifiziert.  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A>erstellt einen Artefaktverweis aus einem <xref:EnvDTE.Project>oder <xref:EnvDTE.ProjectItem>.</xref:EnvDTE.ProjectItem> </xref:EnvDTE.Project></xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A> Das ist ein asynchroner Vorgang. Daher stellen Sie normalerweise einen Rückruf bereit, der nach Abschluss der Erstellung aufgerufen wird.  
  
 Ebenenartefaktverweise dürfen nicht mit Artefakten in Anwendungsfalldiagrammen verwechselt werden.  
  
## <a name="shapes-and-diagrams"></a>Formen und Diagramme  
 Zwei Objekte werden verwendet, um jedes Element in einem Ebenenmodell darzustellen: ein <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>, und eine <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> </xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> 
          `IShape` stellt Position und Größe der Form auf dem Diagramm dar. In Ebenenmodellen jedes `ILayerElement` verfügt über ein `IShape`, und jede `IShape` in eine Abhängigkeit besitzt ein `ILayerElement`. `IShape` wird auch für UML-Modelle verwendet. Daher verfügt nicht jedes `IShape` über ein Ebenenelement.  
  
 Auf die gleiche Weise, die <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>auf eine <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram>.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> angezeigt wird</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>  
  
 Im Code eines benutzerdefinierten Befehl- oder Gestenhandlers können Sie das aktuelle Diagramm und die aktuelle Formenauswahl aus dem `DiagramContext`-Import abrufen:  
  
```  
public class ... {  
[Import]  
    public IDiagramContext DiagramContext { get; set; }  
...  
public void ... (...)   
{ IDiagram diagram = this.DiagramContext.CurrentDiagram;  
  ILayerModel model = diagram.GetLayerModel();  
  if (model != null)  
  { foreach (ILayer layer in model.Layers) { ... }}  
  foreach (IShape selected in diagram.SelectedShapes)  
  { ILayerElement element = selected.GetLayerElement();  
    if (element != null) ... }}  
```  
  
 ![Jedes ILayerElement wird durch eine IShape angegeben. ] (../modeling/media/layerapi_shapes.png "LayerApi_Shapes")  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>und <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram>werden auch zum Anzeigen von UML-Modellen verwendet.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram></xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> Weitere Informationen finden Sie unter [anzeigen ein UML-Modells in Diagrammen](../modeling/display-a-uml-model-on-diagrams.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Befehlen und Gesten, Abhängigkeitsdiagramme](../modeling/add-commands-and-gestures-to-layer-diagrams.md)   
 [Hinzufügen von benutzerdefinierten architekturvalidierung Abhängigkeitsdiagramme](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
 [Fügen Sie benutzerdefinierter Eigenschaften zu Abhängigkeitsdiagramme hinzu](../modeling/add-custom-properties-to-layer-diagrams.md)   
 [Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)   
 [Abhängigkeitsdiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)   
