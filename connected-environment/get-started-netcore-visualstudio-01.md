---
title: 'Erstellen einer .NET Core-Entwicklungsumgebung mit Containern unter Verwendung von Kubernetes in der Cloud mit Visual Studio, Schritt 1: Installieren von Tools | Microsoft-Dokumentation'
author: johnsta
ms.author: johnsta
ms.date: 04/05/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Schnelle Kubernetes-Entwicklung mit Containern und Microservices in Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, Container
manager: ghogen
ms.openlocfilehash: 64aa0b322c777baa78da5bf86cb1220a47128d93
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Erste Schritte in Connected Environment mit .NET Core und Visual Studio

In diesem Leitfaden lernen Sie Folgendes:

1. Erstellen einer auf Kubernetes basierenden Umgebung in Azure, die für die Entwicklung optimiert ist.
1. Iteratives Entwickeln von Code in Containern mit Visual Studio.
1. Unabhängiges Entwickeln von zwei separaten Diensten und Verwenden von DNS Service Discovery zum Aufrufen eines anderen Diensts.
1. Produktives Entwickeln und Testen Ihres Codes in einer Teamumgebung.

[!INCLUDE[](includes/see-troubleshooting.md)]

## <a name="install-the-connected-environment-cli"></a>Installieren der CLI für Connected Environment
Connected Environment erfordert eine minimale Einrichtung auf lokalen Computern. Der Großteil der Konfigurierung Ihrer Entwicklungsumgebung wird in der Cloud gespeichert und kann für andere Benutzer freigegeben werden.

1. Laden Sie den [Installer für die CLI für Connected Environment](https://aka.ms/get-vsce-windows) herunter, und führen Sie ihn aus. 

## <a name="get-kubernetes-debugging-tools"></a>Abrufen von Kubernetes-Debugtools
Sie können die CLI für Connected Environment zwar als eigenständiges Tool verwenden, aber es gibt umfangreiche Features wie **Kubernetes-Debugging** für .NET Core-Entwickler, die **Visual Studio Code** oder **Visual Studio** verwenden.

### <a name="visual-studio-debugging"></a>Debuggen in Visual Studio 
1. Installieren Sie die aktuelle Version von [Visual Studio 2017](https://www.visualstudio.com/vs/).
1. Stellen Sie sicher, dass die folgende Workload im Visual Studio-Installer ausgewählt ist:
    * ASP.NET und Webentwicklung
1. Installieren Sie die [Visual Studio extension for Connected Environment](https://aka.ms/get-vsce-visualstudio) (Visual Studio-Erweiterung für Connected Environment)

Sie können nun eine ASP.NET-Web-App mit Visual Studio erstellen.

> [!div class="nextstepaction"]
> [Erstellen einer ASP.NET-Web-App](get-started-netcore-visualstudio-02.md)
