---
title: Abrufen einer Liste der installierten Codeausschnitte (Legacy) | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: d49d5eb1a6a2e045d477dd03fba9372123cae83a
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte (Legacy-Implementierung)
Ein Codeausschnitt ist ein Codeabschnitt, der eingefügt werden können, in der Quellpuffer mit einem Menübefehl (mit dem können eine Liste der installierten Codeausschnitte Auswahl) oder durch die Tastenkombination für einen Ausschnitt aus einer IntelliSense-Vervollständigungsliste auswählen.  
  
 Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A>-Methode ruft alle Codeausschnitte für eine bestimmte Sprache GUID.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> Die Tastenkombinationen für die Ausschnitte können in einer IntelliSense-Vervollständigungsliste eingefügt werden.  
  
 Finden Sie unter [Unterstützung für Codeausschnitte in einem Legacy-Sprachdienst](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) Details zum Implementieren von Codeausschnitten in einem verwalteten Paket Framework (MPF) Sprache-Dienst.  
  
### <a name="to-retrieve-a-list-of-code-snippets"></a>Zum Abrufen einer Liste von Codeausschnitten  
  
1.  Der folgende Code zeigt, wie Sie eine Liste von Codeausschnitten für eine bestimmte Sprache zu erhalten. Die Ergebnisse werden in einem Zeichenfolgenarray gespeichert <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion>Strukturen.</xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> Diese Methode verwendet die statische <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>Methode zum Abrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>-Schnittstelle aus dem <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>Service.</xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> </xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Allerdings Sie können auch den Dienstanbieter erhalten das VSPackage und rufen die <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>-Methode.</xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>  
  
    ```c#  
    using System;  
    using System.Collections;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Package;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    [Guid("00000000-0000-0000-0000-000000000000")] //create a new GUID for the language service  
    namespace TestLanguage  
    {  
        class TestLanguageService : LanguageService  
        {  
            private void GetSnippets(Guid languageGuid,  
                                     ref ArrayList expansionsList)  
            {  
                IVsTextManager textManager = (IVsTextManager)Package.GetGlobalService(typeof(SVsTextManager));  
                if (textManager != null)  
                {  
                    IVsTextManager2 textManager2 = (IVsTextManager2)textManager;  
                    if (textManager2 != null)  
                    {  
                        IVsExpansionManager expansionManager = null;  
                        textManager2.GetExpansionManager(out expansionManager);  
                        if (expansionManager != null)  
                        {  
                            // Tell the environment to fetch all of our snippets.  
                            IVsExpansionEnumeration expansionEnumerator = null;  
                            expansionManager.EnumerateExpansions(languageGuid,  
                            0,     // return all info  
                            null,    // return all types  
                            0,     // return all types  
                            1,     // include snippets without types  
                            0,     // do not include duplicates  
                            out expansionEnumerator);  
                            if (expansionEnumerator != null)  
                            {  
                                // Cache our expansions in a VsExpansion array   
                                uint count   = 0;  
                                uint fetched = 0;  
                                VsExpansion expansionInfo = new VsExpansion();  
                                IntPtr[] pExpansionInfo   = new IntPtr[1];  
  
                                // Allocate enough memory for one VSExpansion structure. This memory is filled in by the Next method.  
                                pExpansionInfo[0] = Marshal.AllocCoTaskMem(Marshal.SizeOf(expansionInfo));  
  
                                expansionEnumerator.GetCount(out count);  
                                for (uint i = 0; i < count; i++)  
                                {  
                                    expansionEnumerator.Next(1, pExpansionInfo, out fetched);  
                                    if (fetched > 0)  
                                    {  
                                        // Convert the returned blob of data into a structure that can be read in managed code.  
                                        expansionInfo = (VsExpansion)Marshal.PtrToStructure(pExpansionInfo[0], typeof(VsExpansion));  
  
                                        if (!String.IsNullOrEmpty(expansionInfo.shortcut))  
                                        {  
                                            expansionsList.Add(expansionInfo);  
                                        }  
                                    }  
                                }  
                                Marshal.FreeCoTaskMem(pExpansionInfo[0]);  
                            }  
                        }  
                    }  
                }  
            }  
        }  
    }  
    ```  
  
### <a name="to-call-the-getsnippets-method"></a>Aufrufen die GetSnippets-Methode  
  
1.  Das folgende Beispiel zeigt das Aufrufen der `GetSnippets` -Methode am Ende einer Analysevorgang. Die <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A>Methode wird aufgerufen, nachdem einem Analysevorgang, der mit dem Grund <xref:Microsoft.VisualStudio.Package.ParseReason>.</xref:Microsoft.VisualStudio.Package.ParseReason> gestartet wurde</xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A>  
  
> [!NOTE]
>  Die `expansionsList` array Listis aus Leistungsgründen zwischengespeichert. Änderungen an die Codeausschnitte sind nicht in der Liste wiedergegeben, bis der Language-Dienst beendet und neu geladen wird (z. B. durch Beenden und Neustarten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).  
  
```c#  
class TestLanguageService : LanguageService  
{  
    private ArrayList expansionsList;  
  
    public override void OnParseComplete(ParseRequest req)  
    {  
        if (this.expansionsList == null)  
        {  
            this.expansionsList = new ArrayList();  
            GetSnippets(this.GetLanguageServiceGuid(),  
                ref this.expansionsList);  
        }  
    }  
}  
```  
  
### <a name="to-use-the-snippet-information"></a>Der Codeausschnitt Informationen  
  
1.  Der folgende Code zeigt, wie Sie die zurückgegebenen Informationen in den Ausschnitt der `GetSnippets` Methode. Die `AddSnippets` Methode wird aufgerufen, vom Parser als Antwort auf irgendwelchen analysieren, die verwendet wird, um eine Liste von Codeausschnitten aufzufüllen. Dies sollte erfolgen, nachdem die vollständige Analyse zum ersten Mal vorgenommen wurde.  
  
     Die `AddDeclaration` Methode erstellt eine Liste der Deklarationen, die später in eine Vervollständigungsliste angezeigt.  
  
     Die `TestDeclaration` Klasse enthält alle Informationen, die in eine Vervollständigungsliste als auch den Typ der Deklaration angezeigt werden kann.  
  
    ```c#  
    class TestAuthoringScope : AuthoringScope  
    {  
        public void AddDeclarations(TestDeclaration declaration)  
        {  
            if (m_declarations == null)  
                m_declarations = new List<TestDeclaration>();  
            m_declarations.Add(declaration);  
         }  
    }  
    class TestDeclaration   
    {  
        private string m_name;  
        private string m_description;  
        private string m_type;  
  
        public TestDeclaration(string name, string desc, string type)  
        {  
            m_name = name;  
            m_description = desc;  
            m_type = type;  
        }  
  
    class TestLanguageService : LanguageService  
    {  
        internal void AddSnippets(ref TestAuthoringScope scope)  
        {  
            if (this.expansionsList != null && this.expansionsList.Count > 0)  
            {  
                int count = this.expansionsList.Count;  
                for (int i = 0; i < count; i++)  
                {  
                    VsExpansion expansionInfo = (VsExpansion)this.expansionsList[i];  
                    scope.AddDeclaration(new TestDeclaration(expansionInfo.title,  
                         expansionInfo.description,  
                         "snippet"));  
                }  
            }  
        }  
    }  
  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützung für Codeausschnitte in einem Legacy-Sprachdienst](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)