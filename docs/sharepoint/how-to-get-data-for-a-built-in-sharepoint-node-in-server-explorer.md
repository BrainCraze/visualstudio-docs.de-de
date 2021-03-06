---
title: 'Vorgehensweise: Abrufen von Daten für einen integrierten SharePoint-Knotens im Server-Explorer | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f448ec8d7cfe22495aa3f7b2ce9191f106205c33
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Gewusst wie: Abrufen von Daten für einen integrierten SharePoint-Knoten im Server-Explorer
  Für jeden integrierten SharePoint-Knoten im **Server-Explorer**, Abrufen von Daten für die zugrunde liegende SharePoint-Komponente, die der Knoten darstellt. Weitere Informationen finden Sie unter [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie zum Abrufen von Daten für die zugrunde liegende SharePoint-Liste, das in ein Knoten repräsentiert **Server-Explorer**. Standardmäßig Listenknoten verfügen über eine **in Browser anzeigen** Kontextmenüelement, die Sie klicken können, um die Listen in einem Webbrowser zu öffnen. In diesem Beispiel erweitert Listenknoten durch Hinzufügen einer **in Visual Studio anzeigen** Kontextmenüelement, das die Listen direkt in Visual Studio geöffnet wird. Der Code greift auf die Daten für den Knoten, um die URL der Liste aus, öffnen in Visual Studio abzurufen.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]  
  
 In diesem Beispiel verwendet die SharePoint-Projektdienst zum Abrufen der <xref:EnvDTE.DTE> -Objekt, das verwendet wird, öffnen Sie in Visual Studio aufgelistet. Weitere Informationen zu den SharePoint-Projektdienst, finden Sie unter [Verwenden des SharePoint-Projektdiensts](../sharepoint/using-the-sharepoint-project-service.md).  
  
 Weitere Informationen zu den grundlegenden Aufgaben zum Erstellen einer Erweiterung für einen SharePoint-Knoten finden Sie unter [wie: Erweitern eines SharePoint-Knotens im Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Bereitstellen der Erweiterung  
 Bereitstellen der **Server-Explorer** Erweiterung erstellen Sie eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Vorgehensweise: Erweitern eines SharePoint-Knotens im Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Verwenden des SharePoint-Projektdiensts](../sharepoint/using-the-sharepoint-project-service.md)   
 [Bereitstellen von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  