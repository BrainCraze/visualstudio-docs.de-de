---
title: Persönliche E-Mail-Nachrichten, die im VLSC angezeigt werden
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/23/2018
ms.topic: Get-Started-Article
description: Visual Studio-Abonnements – Warum sehe ich Hotmail- oder Gmail-Adressen für meine Abonnenten?
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: cfe035d82976e3df683f4e3a35bd9d7f3c8cf9e2
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2018
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Visual Studio-Abonnements – Warum sehe ich Hotmail- oder Gmail-Adressen für meine Abonnenten? 

Wenn Unternehmen vom Volume Licensing Service Center (VLSC) zum neuen [Abonnementverwaltungsportal](https://manage.visualstudio.com) von Visual Studio migrieren, stellen Administratoren möglicherweise überrascht fest, dass als „Anmelde-E-Mail-Adresse“ für manche Abonnenten eine E-Mail-Adresse von Drittanbietern wie Hotmail, Gmail oder Yahoo angezeigt wird.

## <a name="cause"></a>Ursache

Grund für dieses Szenario sind Anmeldeprozesse, die mit dem älteren MSDN-Abonnentenprozess verknüpft waren. Benutzer wurden ohne Änderungen aus dem VLSC zum neuen Portal migriert. Einigen Administratoren war vielleicht nicht bewusst, dass Benutzer persönliche Konten verwendet hatten, um auf Ihre Abonnementvorteile zuzugreifen. Vor den Visual Studio-Abonnentenmigrationen, die 2016 abgeschlossen wurden, waren zur erfolgreichen Verwendung eines Visual Studio-Abonnements zwei Aktionen erforderlich:
1. Der Administrator „wies“ das Abonnement einem einzelnen Abonnenten unter Verwendung seiner Geschäfts- oder Schul-E-Mail-Adresse zu.
2. Der Abonnent „aktivierte“ das Abonnement.

Während des Abonnentenaktivierungsprozesses: Für die Anmeldung war ein Microsoft-Konto (MSA) erforderlich. Wenn der Abonnent nicht versuchte, sein Geschäfts- oder Schulkonto (z.B. John@contoso.com) zu einem MSA zu machen, konnte er ein neues MSA erstellen oder ein vorhandenes nutzen. Dies führte dazu, dass seine „Anmelde-E-Mail-Adresse“ sich von seiner „‘Zugewiesen an‘-E-Mail-Adresse" unterschied.

> [!NOTE] 
> Der neue Abonnentenprozess in [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) unterstützt sowohl Geschäfts-, Uni- und Schulkonto- als auch Microsoft-Kontoidentitätstypen (MSA).

Da die Administratormigration Daten aus dem VLSC bezüglich der „Anmelde-E-Mail-Adresse“ des Abonnenten für den neuen Abonnentenverwaltungsprozess verwendet, können schließlich möglicherweise vor kurzem migrierte Administratoren diese zuvor nicht bemerkten persönlichen Konten aufgrund von Änderungen an der Benutzeroberfläche sehen, die diese Informationen besser sichtbar machen.

## <a name="solution"></a>Lösung

Um das Problem zu beheben, müssen Sie Abonnenteninformationen bearbeiten, um ihre Anmelde-E-Mail-Adressen zu aktualisieren.  Bearbeitungen können für einzelne Abonnenten oder mehrere gleichzeitig vorgenommen werden. Ausführliche Informationen finden Sie unter [Bearbeiten von Visual Studio-Abonnementzuweisungen](/visualstudio/subscriptions/edit-license).  

Nachdem Sie die E-Mail-Adressen der Abonnenten aktualisiert haben, sollten Sie ihnen mitteilen, dass ihre Anmeldeinformationen geändert wurden.  