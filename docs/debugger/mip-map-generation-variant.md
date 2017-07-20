---
title: "Mipmap-Generierungsvariante | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b4b3583-0b01-4f5d-aacb-3f96d19111d9
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Mipmap-Generierungsvariante
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aktiviert Mipmaps auf Texturen, die keine Renderziele sind.  
  
## Interpretation  
 Mipmaps werden hauptsächlich zur Eliminierung von Aliasing\-Artefakten in Texturen verwendet, die gerade verkleinert werden, indem Sie kleinere Versionen der Textur vorausberechnen.  Obwohl diese zusätzlichen Texturen GPU\-Speicher verbrauchen – ca. 33 % mehr als die Originaltextur –, sind sie effizienter, da mehr von ihrem Oberflächenbereich in den GPU\-Texturcache passt und ihre Inhalte eine höhere Verwendung erreichen.  
  
 Für 3D\-Szenen empfehlen wir Mipmaps, wenn Speicher verfügbar ist, um die zusätzlichen Texturen zu speichern, da sie sowohl die Renderingleistung als auch die Bildqualität erhöhen.  
  
 Wenn diese Variante zu einer deutlichen Leistungssteigerung führt, zeigt dies an, dass Sie Texturen ohne Aktivierung von Mipmaps verwenden und deshalb den Texturcache nicht optimal nutzen.  
  
## Hinweise  
 Die Mipmap\-Erzeugung wird bei jedem Aufruf von `ID3D11Device::CreateTexture2D` erzwungen, der eine Quelltextur erstellt.  Die Mipmap\-Erzeugung wird insbesondere dann erzwungen, wenn das in `pDesc` übergebene Objekt D3D11\_TEXTUR2D\_DESC eine nicht geänderte Shaderressource beschreibt. Das bedeutet:  
  
-   Für das BindFlags\-Member ist nur das Flag D3D11\_BIND\_SHADER\_RESOURCE gesetzt.  
  
-   Das Usage\-Member ist entweder auf D3D11\_USAGE\_DEFAULT oder auf D3D11\_USAGE\_IMMUTABLE gesetzt.  
  
-   Das CPUAccessFlags\-Member ist auf 0 \(kein Zugriff auf die CPU\) gesetzt.  
  
-   Das Count\-Member des SampleDesc\-Members ist auf 1 \(kein Multi\-Sample Anti\-Aliasing \(MSAA\)\) gesetzt.  
  
-   Das MipLevels\-Member ist auf 1 \(keine existierende Mipmap\) gesetzt.  
  
 Wenn die Anwendung die ursprünglichen Daten ausgibt, muss das Texturformat – wie durch D3D11\_FORMAT\_SUPPORT\_MIP\_AUTOGEN festgelegt – die automatische Mipmap\-Erzeugung unterstützen, außer wenn das Format BC1, BC2 oder BC3 ist; andernfalls wird die Textur nicht verändert, und bei Ausgabe der ursprünglichen Daten werden keine Mipmaps erzeugt.  
  
 Wenn Mipmaps für eine Textur automatisch erzeugt worden sind, werden Aufrufe von `ID3D11Device::CreateShaderResourceView` während der Wiedergabe modifiziert, um während des Textursamplings die Mip\-Kette zu verwenden.  
  
## Beispiel  
 Die Variante **Mipmap\-.Erzeugung** kann durch Verwendung eines Codes reproduziert werden, der dem folgenden ähnlich ist:  
  
```  
D3D11_TEXTURE2D_DESC texture_description;  
  
// ...  
  
texture_description.MipLevels = 0; // generate a full mipchain  
  
std::vector<D3D11_SUBRESOURCE_DATA> initial_data(num_mips);  
  
for (auto&& mip_level : initial_data)  
{  
    // fill mip_level with the application-supplied initial data  
}  
  
d3d_device->CreateTexture2D(&texture_description, initial_data.data(), &texture)  
```  
  
 Wenn Sie eine Textur mit einer vollständigen Mip\-Kette erstellen möchten, setzen Sie `D3D11_TEXTURE2D_DESC::MipLevels` auf 0.  Die Anzahl der Mip\-Ebenen in einer vollständigen Mip\-Kette ist floor\(log2\(n\) \+ 1\), wobei n die größte Dimension der Textur ist.  
  
 Bitte bedenken Sie, dass bei einer Bereitstellung der ursprünglichen Daten auf `CreateTexture2D` ein D3D11\_SUBRESOURCE\_DATA\-Objekt für jede Mip\-Ebene erstellt werden muss.  
  
> [!NOTE]
>  Wenn Sie Ihre eigenen Inhalte auf Mip\-Ebene bereitstellen möchten, anstatt sie automatisch zu erzeugen, müssen Sie Ihre Texturen mithilfe eines Bildeditors erstellen, der Mipmap\-Texturen unterstützt, und dann die Datei laden und die Mip\-Ebenen an `CreateTexture2D` übergeben.  
  
## Siehe auch  
 [Halb\-\/Viertel\-Texturdimensionsvariante](../debugger/half-quarter-texture-dimensions-variant.md)