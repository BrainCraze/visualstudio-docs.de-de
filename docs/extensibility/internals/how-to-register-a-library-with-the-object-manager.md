---
title: 'Vorgehensweise: Registrieren Sie eine Bibliothek mit dem Objekt-Manager | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 30bf2775c358b107fe299f0d60bc00a2030465e4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Vorgehensweise: Registrieren Sie eine Bibliothek mit dem Objekt-Manager
Tools zum Durchsuchen von Symbolen, z. B. **Klassenansicht**, **Objektkatalog**, **Aufrufbrowser** und **Ergebnisse der Symbolsuche**, ermöglichen es Ihnen, anzeigen Symbole im Projekt oder in externen Komponenten. Die Symbole enthalten Namespaces, Klassen, Schnittstellen, Methoden und anderen Sprachelemente. Die Bibliotheken diese Symbole nachverfolgen und verfügbar zu machen, damit die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Objekt-Manager, die die Tools mit den Daten auffüllt.  
  
 Der Objekt-Manager der nachverfolgt aller verfügbare Bibliotheken. Jede Bibliothek muss mit dem Objektmanager registrieren, bevor Sie die Symbole für die Tools zum Durchsuchen des Symbols bereitstellt.  
  
 In der Regel, registrieren Sie eine Bibliothek aus, wenn eine VSPackage lädt. Allerdings kann es zu einem späteren Zeitpunkt erfolgen nach Bedarf. Sie Registrierung die Bibliothek aufzuheben, wenn das VSPackage wird heruntergefahren.  
  
 Um eine Bibliothek zu registrieren, verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> Methode. Im Fall von verwaltetem Code-Bibliothek, verwenden die <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> Methode.  
  
 Verwenden Sie zum Aufheben der Registrierung einer Bibliotheks die <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> Methode.  
  
 Um einen Verweis auf den Objekt-Manager erhalten <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, übergeben die <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> Dienst-ID zu `GetService` Methode.  
  
## <a name="registering-and-unregistering-a-library-with-the-object-manager"></a>Registrieren und Aufheben der Registrierung einer Bibliothek mit dem Objekt-Manager  
  
#### <a name="to-register-a-library-with-the-object-manager"></a>So registrieren eine Bibliothek mit dem Objektmanager  
  
1.  Erstellen Sie eine Bibliothek.  
  
    ```vb  
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing  
    Private m_nLibraryCookie As UInteger = 0  
    ' Create Library.  
    m_CallBrowserLibrary = New CallBrowser.Library()  
    ```  
  
    ```csharp  
    private CallBrowser.Library m_CallBrowserLibrary = null;  
    private uint m_nLibraryCookie = 0;  
    // Create Library.  
    m_CallBrowserLibrary = new CallBrowser.Library();  
  
    ```  
  
2.  Rufen Sie einen Verweis auf ein Objekt des der <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> geben, und rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> Methode.  
  
    ```vb  
    Private Sub RegisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            Throw New Exception("Library already registered with Object Manager")  
        End If  
  
        ' Obtain a reference to IVsObjectManager2 type object.  
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
        If objManager Is Nothing Then  
            Throw New NullReferenceException("GetService failed for SVsObjectManager")  
        End If  
  
        Try  
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)  
        Catch e As Exception  
            ' Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message)  
            Throw  
        End Try  
    End Sub  
    ```  
  
    ```csharp  
    private void RegisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
            throw new Exception("Library already registered with Object Manager");  
  
        // Obtain a reference to IVsObjectManager2 type object.  
        IVsObjectManager2 objManager =   
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
        if (objManager == null)  
            throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
        try  
        {  
            int hr =   
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,   
                                                 out m_nLibraryCookie);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
        }  
        catch (Exception e)  
        {  
            // Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message);  
            throw;  
        }  
    }  
  
    ```  
  
#### <a name="to-unregister-a-library-with-the-object-manager"></a>Beim Aufheben der Registrierung einer Bibliotheks mit dem Objektmanager  
  
1.  Rufen Sie einen Verweis auf ein Objekt des der <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> geben, und rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> Methode.  
  
    ```vb  
    Private Sub UnregisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            ' Obtain a reference to IVsObjectManager2 type object.  
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
            If objManager Is Nothing Then  
                Throw New NullReferenceException("GetService failed for SVsObjectManager")  
            End If  
  
            Try  
                objManager.UnregisterLibrary(m_nLibraryCookie)  
            Catch e As Exception  
                ' Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message)  
                Throw  
            Finally  
                m_nLibraryCookie = 0  
            End Try  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UnregisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
        {  
            // Obtain a reference to IVsObjectManager2 type object.  
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
            if (objManager == null)  
                throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
            try  
            {  
                objManager.UnregisterLibrary(m_nLibraryCookie);  
            }  
            catch (Exception e)  
            {  
                // Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message);  
                throw;  
            }  
            finally  
            {  
                m_nLibraryCookie = 0;  
            }  
        }  
    }  
  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Ältere Language Service-Erweiterbarkeit](../../extensibility/internals/legacy-language-service-extensibility.md)   
 [Unterstützung von Tools zum Durchsuchen des Symbols](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Gewusst wie: Verfügbarmachen der Listen von Symbolen, die von der Bibliothek für den Objekt-Manager bereitgestellt werden](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)