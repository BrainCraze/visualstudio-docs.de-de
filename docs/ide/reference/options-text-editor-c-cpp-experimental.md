---
title: Optionen, Text-Editor, C/C++, Experimentell | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 47c39bd711b69efdb863d71f11e3e472054a3ce3
ms.openlocfilehash: 889d538b732b360b475788ec6d67b47920703c73
ms.lasthandoff: 04/06/2017

---
# <a name="options-text-editor-cc-experimental"></a>Optionen, Text-Editor, C/C++, Experimentell
Wenn Sie diese Optionen ändern, können Sie beim Programmieren in C oder C++ das Verhalten ändern, das mit IntelliSense und der Suchdatenbank zusammenhängt. Diese Features sind rein experimentell und werden möglicherweise in einer zukünftigen Version geändert oder komplett aus Visual Studio entfernt. In diesem Thema werden die Optionen in Visual Studio 2017 beschrieben. Informationen zu Visual Studio 2015 finden Sie unter [Optionen, Text-Editor, C/C++, Experimentell](https://msdn.microsoft.com/library/mt591979.aspx) 
  
 Drücken Sie **STRG + Q**, um `Quick Launch` zu aktivieren, und geben Sie anschließend „experimentell“ ein, um auf diese Eigenschaftenseite zuzugreifen. Der Schnellstart findet die Seite nach den ersten Buchstaben. Sie können auch darauf zugreifen, indem Sie **Tool | Optionen** auswählen, den **Text-Editor** und **C/C++** erweitern und anschließend **Experimentell** auswählen.  

 Diese Features sind mit einer Visual Studio 2017-Installation verfügbar.  
  
> [!NOTE]
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Informationen hierzu finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio)](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="enable-predictive-intellisense"></a>Predictive IntelliSense aktivieren
Predictive IntelliSense beschränkt die Anzahl von angezeigten Ergebnissen in der Dropdownliste in IntelliSense, sodass nur für Ihren Kontext relevante Ergebnisse angezeigt werden. Wenn Sie <code>int x =</code> eingeben und das Dropdownmenü in IntelliSense aufrufen, werden Ihnen nur ganze Zahlen oder Funktionen, die ganze Zahlen zurückgeben, angezeigt. Standardmäßig ist Predictive IntelliSense deaktiviert.

## <a name="enable-faster-project-load"></a>„Schnelleres Laden von Projekten“ aktivieren
Durch diese Option kann Visual Studio Projektdaten zwischenspeichern, damit es, wenn Sie die Projekte das nächste Mal öffnen, die zwischengespeicherten Daten abrufen kann, statt sie erneut aus den Projektdateien berechnen zu müssen. Durch zwischengespeicherte Daten kann die Projektladezeit deutlich verringert werden.  

## <a name="additional-features-in-the-visual-studio-gallery"></a>Zusätzliche Features in der Visual Studio Gallery
Weitere Text-Editor-Features für die Visual Studio Gallery finden Sie in [dieser Liste](http://go.microsoft.com/fwlink/?LinkId=692016). Ein Beispiel ist [C++ Quick Fixes](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f), das Folgendes unterstützt:  
  
-   **Add missing #include** - Schlägt zutreffende #include-Anweisungen für unbekannte Symbole in Ihrem Code vor.  
  
-   **Add using namespace/Fully qualify symbol** - Wie die vorherige Option, aber für Namespaces.  
  
-   **Fehlendes Semikolon hinzufügen**  
  
-   **MSDN Help** - In MSDN nach Fehlermeldungen suchen.  
  
 Sie können entweder mit dem Mauszeiger auf eine Wellenlinie zeigen, um eine Glühbirne anzuzeigen, oder die Standardtastenkombination Strg + Punkt (STRG + .) verwenden. Für die Tastenkombination muss die Einfügemarke nicht auf dem speziellen Fehler oder Token positioniert werden. Es genügt, wenn Sie sich in der Zeile befinden, in der der Fehler auftritt, um Vorschläge für alle Elemente in dieser Zeile aufzurufen.  
  
## <a name="see-also"></a>Siehe auch  
 [Festlegen von sprachspezifischen Editor-Optionen](../../ide/reference/setting-language-specific-editor-options.md)   
 [Umgestaltung in C++ (VC-Blog)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)
