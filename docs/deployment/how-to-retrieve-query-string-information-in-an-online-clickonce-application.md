---
title: "Gewusst wie: Abrufen von Abfragezeichenfolgen-Informationen in einer Online-ClickOnce-Anwendung | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce-Bereitstellung, Abfragezeichenfolgen"
  - "Abfragezeichenfolgen, Abrufen von Informationen"
ms.assetid: 48ce098a-a075-481b-a5f5-c8ba11f63120
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Gewusst wie: Abrufen von Abfragezeichenfolgen-Informationen in einer Online-ClickOnce-Anwendung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die *Abfragezeichenfolge* ist der Teil einer URL, die mit einem Fragezeichen \(?\) beginnt und die willkürliche Informationen im Format *name\=value* enthält. Angenommen, Sie verfügen über eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung mit dem Namen `WindowsApp1`, die Sie auf `servername` hosten, und Sie möchten einen Wert für die Variable `username` bei Anwendungsstart übergeben. Die URL könnte folgendermaßen aussehen:  
  
 `http://servername/WindowsApp1.application?username=joeuser`  
  
 Die folgenden zwei Vorgehensweisen zeigen, wie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung verwendet wird, um Informationen über Abfragezeichenfolgen abzurufen.  
  
> [!NOTE]
>  Sie können nur Informationen in einer Abfragezeichenfolge übergeben, wenn Ihre Anwendung über HTTP gestartet wird und nicht über eine Dateifreigabe oder das lokale Dateisystem.  
  
 Das erste Verfahren zeigt, wie Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung einen kleinen Codeabschnitt verwenden kann, um diese Werte bei Anwendungsstart zu lesen.  
  
 Das nächste Verfahren zeigt, wie Sie Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung mithilfe MageUI.exe so konfigurieren, dass sie Abfragezeichenfolgen\-Parameter akzeptieren kann. Sie müssen dieses Verfahren bei jeder Veröffentlichung der Anwendung durchführen.  
  
> [!NOTE]
>  Bevor Sie eine Entscheidung zur Aktivierung dieser Funktion treffen, lesen Sie zuerst den Abschnitt „Sicherheit“ weiter unten in diesem Thema.  
  
 Weitere Informationen zum Erstellen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung mit Mage.exe oder MageUI.exe finden Sie unter [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
> [!NOTE]
>  Ab .NET Framework 3.5 SP1 ist es möglich, Befehlszeilenargumente an eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Offlineanwendung zu übergeben. Wenn Sie der Anwendung Argumente bereitstellen möchten, können Sie der Verknüpfungsdatei In\-Parameter mit der Erweiterung APPREF\-MS übergeben.  
  
### So rufen Sie Abfragezeichenfolgen\-Informationen in einer ClickOnce\-Anwendung ab  
  
1.  Platzieren Sie folgenden Code in Ihrem Projekt. Damit dieser Code funktioniert, müssen Sie über einen Verweis auf System.Web verfügen und `using`\- oder `Imports`\-Anweisungen für System.Web, System.Collections.Specialized und System.Deployment.Application hinzufügen.  
  
     [!code-cs[ClickOnceQueryString#1](../deployment/codesnippet/CSharp/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.cs)]
     [!code-vb[ClickOnceQueryString#1](../deployment/codesnippet/VisualBasic/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.vb)]  
  
2.  Rufen Sie die zuvor definierte Funktion ab, um ein nach Namen indexiertes <xref:System.Collections.DictionaryBase.Dictionary%2A> der Abfragezeichenfolgenparameter abzurufen.  
  
### So aktivieren Sie die Übergabe der Abfragezeichenfolge in einer ClickOnce\-Anwendung mit MageUI.exe  
  
1.  Öffnen Sie die Eingabeaufforderung .NET und geben Sie Folgendes ein:  
  
    ```  
    MageUI  
    ```  
  
2.  Wählen Sie im Menü **Datei** die Option **Öffnen** aus, und öffnen Sie das Bereitstellungsmanifest für Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung, die die Dateiendung `.application` aufweist.  
  
3.  Wählen Sie den Bereich **Bereitstellungsoptionen** im linken Navigationsfenster aus, und wählen Sie das Kontrollkästchen **Übergeben von URL\-Parametern an die Anwendung zulassen** aus.  
  
4.  Wählen Sie im Menü **Datei** die Option **Speichern** aus.  
  
> [!NOTE]
>  Sie können alternativ die Übergabe der Abfragezeichenfolge in [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] aktivieren. Wählen Sie das Kontrollkästchen **Übergeben von URL\-Parametern an die Anwendung zulassen** aus. Dieses Kontrollkästchen finden Sie, indem Sie die **Projekteigenschaften** öffnen und die Schaltfläche **Veröffentlichen** auswählen. Anschließend klicken Sie auf die Schaltfläche **Optionen** und wählen **Manifeste** aus.  
  
## Robuste Programmierung  
 Wenn Sie Abfragezeichenfolgen\-Parameter verwenden, überlegen Sie genau, wie Ihre Anwendung installiert und aktiviert wird. Wenn Ihre Anwendung so konfiguriert ist, dass Sie auf dem Computer des Nutzers aus dem Web oder einer Netzwerkfreigabe installiert wird, dann ist es wahrscheinlich, dass der Benutzer die Anwendung nur einmal über die URL aktivieren wird. Danach aktiviert der Benutzer Ihre Anwendung normalerweise über die Verknüpfung im Menü **Start**. Deshalb ist gewährleistet, dass Ihre Anwendung Argumente für Abfragezeichenfolgen nur einmal im Laufe ihrer Lebensdauer erhält. Wenn Sie diese Argumente auf dem Computer des Benutzers für den zukünftigen Gebrauch speichern möchten, sind Sie dafür verantwortlich, sie auf sichere Weise zu speichern.  
  
 Wenn Ihre Anwendung nur online ist, wird sie immer durch eine URL aktiviert. Allerdings muss Ihre Anwendung auch in diesem Fall so geschrieben werden, dass sie ordnungsgemäß funktioniert, wenn die Abfragezeichenfolgen\-Parameter fehlen oder beschädigt sind.  
  
## .NET Framework-Sicherheit  
 Lassen Sie die Übergabe von URL\-Parametern an Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung nur zu, wenn Sie beabsichtigen, die Eingabe von böswilligen Zeichen vor der Verwendung zu bereinigen. Eine Zeichenfolge, die z.B. mit Anführungszeichen, Schrägstrichen oder Semikola als Trennzeichen eingebettet ist, kann möglicherweise willkürliche Datenvorgänge durchführen, wenn sie ungefiltert in einer SQL\-Abfrage für eine Datenbank verwendet wird. Weitere Informationen zur Sicherheit von Abfragezeichenfolgen finden Sie unter [Script Exploits Overview](../Topic/Script%20Exploits%20Overview.md).  
  
## Siehe auch  
 [Sichern von ClickOnce\-Anwendungen](../deployment/securing-clickonce-applications.md)