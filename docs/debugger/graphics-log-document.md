---
title: "Grafikprotokolldokument | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.graphics.vsglog.error"
  - "vs.graphics.experiment"
  - "vs.graphics.vsglog"
ms.assetid: 6ccb1269-d55f-49c4-920d-baedf7de2888
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Grafikprotokolldokument
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Grafikprotokolldokument enthält die beim Ausführen Ihrer App in einer Grafikdiagnosesitzung aufgetretenen Grafikereignisse.  Wenn das Prokotoll erstellt wurde, können Sie es in der Visual Studio\-Grafikanalyse auf Renderings\- und Leistungsprobleme durchsuchen.  
  
 So sieht ein Grafikprotokolldokument in der Grafikanalyse aus:  
  
 ![Diagrammprotokoll mit zwei erfassten Rahmen](../debugger/media/gfx_diag_demo_graphics_log_orientation.png "gfx\_diag\_demo\_graphics\_log\_orientation")  
  
## Grundlegendes zu Grafikprotokolldokumenten  
 Wenn Sie das Grafikprotokolldokument mithilfe der Grafikanalyse überprüfen, können Sie die erfassten Auswirkungen von Direct3D\-Ereignissen auf das Renderziel visuell darstellen.  Sie können Bereiche des Renderziels festlegen, die unerwartete Ausgabe enthalten.  Wenn Sie ein Pixel im betroffenen Bereich auswählen, können Sie dieses, seine Shader, die Direct3D\-Ereignisse, die Auswirkungen auf das Pixel hatten, die Anwendungsaufrufliste, die zu diesen Ereignissen führte, sowie die DirectX\-Objekte, die diese Ereignisse unterstützen, mit der Grafikdiagnose überprüfen.  Sie können diese Informationen verwenden, um Renderingprobleme im Spiel oder in der App zu bestimmen.  
  
 Im oberen Teil des Fensters \(**Graphics Experiment.vsglog**\) wird die aktuelle Renderzielausgabe der ausgewählten Frames angezeigt, und im unteren Teil wird eine **Frameliste** angezeigt, die Miniaturbilder der aufgezeichneten Frames enthält.  
  
#### So überprüfen einen Frame  
  
-   Wählen Sie in der **Frameliste** den Frame aus, den Sie überprüfen möchten.  Die Renderzielausgabe im obersten Abschnitt des Grafikprotokolldokuments wird aktualisiert und zeigt den ausgewählten Frame an.  
  
#### So überprüfen Sie ein Pixel  
  
-   Wählen Sie das gewünschte Pixel im obersten Abschnitt des Grafikprotokolldokuments aus der Renderzielausgabe aus.  Wenn ein Pixel aktiviert ist, können Sie im Fenster **Grafikpixelverlauf** ausführliche Informationen über das ausgewählte Pixel anzeigen.  Weitere Informationen finden Sie unter [Pixelverlauf](../debugger/graphics-pixel-history.md).  
  
## Wiedergabecomputer  
 In der rechten oberen Ecke der **Frameliste** wird auch der **Wiedergabecomputer** angezeigt.  Der Wiedergabecomputer ist ein Computer oder ein Gerät, das Grafikereignisse aus einer Grafikprotokolldatei während einer späteren Grafikdiagnosesitzung wiedergibt.  Wenn Sie ein anderes Gerät als Ihren Entwicklungscomputer zur Wiedergabe der aufgezeichneten Ereignisse verwenden, können Sie die Ausführungsumgebung genauer reproduzieren, in der das Problem aufgetreten ist – Sie können beispielsweise einen Computer mit anderer Grafikhardware oder anderen Treibern als Ihr Entwicklungscomputer oder andere Arten von Geräten verwenden, z. B. ein ARM\-basiertes Windows RT\-Tablet oder ein Gerät mit Windows Phone.  
  
 Informationen zum Angeben eines Wiedergabecomputers finden Sie unter [Gewusst wie: Ändern des Grafikdiagnose\-Wiedergabecomputers](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## Kurzinformationen zum Grafikprotokoll  
 Wenn das aktive Dokument eine Graphikprotokolldatei ist, werden im Fenster **Eigenschaften** Informationen zur Umgebung angezeigt, in der die Grafikdiagnose\-Erfassungssitzung gehostet wird.  Es werden verschiedene Kategorien von Informationen angezeigt.  
  
 **Direct3D\-Informationen**  
 Führt Informationen über die Hardwarekonfiguration und Treiberfunktionen der Grafikkarte auf, die während der Erfassungssitzung verwendet wurde.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|**10\-Bit XR\-Format mit hoher Farbtiefe**|**True**, wenn das 10\-Bit XR\-Format mit hoher Farbtiefe unterstützt wird; andernfalls **False**.|  
|**DirectCompute CS 4.x**|**True**, wenn der Compute\-Shader 4.0 unterstützt wird; anderenfalls **False**.|  
|**Shader mit doppelter Genauigkeit**|**True**, wenn die Grafikkarte Gleitkommawerte mit doppelter Genauigkeit \(64 Bit\) unterstützt; andernfalls **False**.|  
|**Treiber \- Befehlslisten**|**True**, wenn der Treiber Befehlslisten unterstützt; andernfalls **False**.|  
|**Treiber \- Simultanerstellungen**|**True**, wenn der Treiber die gleichzeitige \(asynchrone\) Erstellung unterstützt; andernfalls **False**.|  
|**Erweiterte Formate \(BGRA usw.\)**|**True**, wenn erweiterte Formate wie BGRA unterstützt werden; andernfalls **False**.|  
|**Maximale Hardwarefunktionsebene**|Zeigt die höchste Funktionsebene an, die über die Grafikkarte unterstützt wird.|  
  
 **Anzeigeinformationen**  
 Führt Informationen über die Grafikkarte auf, die während der Erfassungssitzung verwendet wurde.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|**Beschreibung**|Die Zeichenfolge für die Grafikkartenbeschreibung.|  
|**Anzeigespeicher**|Der Speicherplatz, der auf der Grafikkarte installiert ist.|  
|**Treibername**|Der Name des Grafikkartentreibers.|  
|**Treiberversion**|Die Version des Grafikkartentreibers.|  
|**Name**|Der Name der Grafikkarte.|  
  
 **Experimentedatei**  
 Listet Informationen über die Experimentedatei auf, die mit dieser Erfassungssitzung verknüpft ist.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|**Pfad**|Der Pfad der .vsglog\-Datei. **Note:**  In früheren Erfassungen wird die Eigenschaft nicht verwendet.|  
  
 **Modulinformationen**  
 Führt den Namen und die Version der Dynamic Link Librarys \(DLL\) auf, die während der Erfassungssitzung durch die App geladen wurden.  
  
 **Systeminformationen**  
 Führt Informationen über die Hardware und das Betriebssystem auf, die die App während der Erfassungssitzung gehostet haben.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|**Arbeitsspeicher**|Der Speicher, der auf dem Computer installiert ist.|  
|**BS\-Architektur**|Die CPU\-Architektur des Betriebssystems des Zielcomputers.|  
|**Betriebssystemversion**|Die Version des Betriebssystems.|  
|**Prozessor**|Der Prozessor, der auf dem Computer installiert ist.|  
|**Architektur der Zielanwendung**|Die CPU\-Architektur der App auf dem Zielcomputer.  Diese kann sich von der **BS\-Architektur** unterscheiden.|  
  
 **Zielanwendung**  
 Führt Informationen über die App auf, die von der Erfassungssitzung erfasst wird.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|**Datum\/Uhrzeit der letzten Änderung**|Datum und Uhrzeit der Erstellung der App.|  
|**Pfad**|Der Pfad der App.|  
|**Prozess\-ID**|Die Prozess\-ID, die zur App angegeben wurde.|  
|**Version**|Die App\-Version.|  
  
 **VSG\-Protokolldatei**  
 Führt Informationen über das Grafikprotokolldokument auf.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|**Erstellt von**|Der Name der App, die das Grafikprotokolldokument erstellt hat.  Wenn die Erfassungssitzung z. B. von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] initiiert wurde \(manuelle Erfassung\) ist der Wert dieser Eigenschaft [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|**Startzeit der Sitzung**|Das Datum und die Uhrzeit, zu der die Erfassungssitzung begann.|  
|**Größe**|Die Größe des Grafikprotokolldokuments.|  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Fehlende Objekte durch Vertexschattierung](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Exemplarische Vorgehensweise: Debuggen von Renderingfehlern, die durch Schattierungen entstanden sind](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)