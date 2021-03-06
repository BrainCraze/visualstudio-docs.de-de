---
title: Symbole und Symboltags | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 69d2f5c2182f32a95ca95d24c5319b164f27f1ae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="symbols-and-symbol-tags"></a>Symbole und Symboltags
Debuginformationen zu kompiliertes Programm wird als Symbole, die mithilfe der Debug Interface Access (DIA) SDK-APIs zugegriffen werden kann, in die Programmdatenbankdatei (PDB) gespeichert. Alle Symbole sind eine [idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) und ein [idiasymbol:: Get_symindexid](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) Eigenschaft. Die `symTag` Eigenschaft gibt die Art des Symbols an, gemäß der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Enumeration. Die `symIndexId` Eigenschaft ist ein `DWORD` Wert, der den eindeutigen Bezeichner für jede Instanz eines Symbols enthält.  
  
 Symbole verfügen auch über Eigenschaften, die am häufigsten zusätzliche Informationen über das Symbol sowie Verweise auf andere Symbole angeben, können eine [idiasymbol:: Get_lexicalparent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) oder [idiasymbol:: Get_classparent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Wenn Sie eine Eigenschaft, die einen Verweis enthält Abfragen, wird der Verweis zurückgegeben, als ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt. Diese Eigenschaften werden immer gepaart mit einer anderen Eigenschaft mit dem gleichen Namen, jedoch entsprechend mit "Id", z. B. [idiasymbol:: Get_lexicalparentid](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) und [idiasymbol:: Get_classparentid](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Die Tabellen in [Orte für Symboldateien](../../debugger/debug-interface-access/symbol-locations.md), [lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), und [Hierarchie der Symboltypen Klasse](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) Gliedern Sie die Eigenschaften für jede der verschiedenen Arten von Symbole. Diese Eigenschaften möglicherweise zweckdienliche Informationen oder Verweise auf andere Symbole. Da die `*Id` Eigenschaften sind einfach numerische Ordinalzahl Bezeichner verwandten Eigenschaften, sie über weitere Diskussionen ausgelassen werden. Sie sind bezeichnet nur, um Informationen für Parameter erforderlich.  
  
 Beim Versuch, die Eigenschaft zuzugreifen, wenn kein Fehler auftritt und die Symbols-Eigenschaft einen Wert zugewiesen wurde, der Eigenschaft "get"-Methode zurückkehrt `S_OK`. Ein Rückgabewert von `S_FALSE` gibt an, dass die Eigenschaft für das aktuelle Symbol ungültig ist.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)  
 Beschreibt die verschiedenen Arten von Speicherorten, die ein Symbol enthalten kann.  
  
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Beschreibt die Symboltypen, die lexikalische Hierarchien, z. B. Dateien, Module und Funktionen zu bilden.  
  
 [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Beschreibt die Symboltypen, die auf der anderen Sprachelemente entsprechen, z. B. Klassen, Arrays und Funktion Typen zurückgeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)