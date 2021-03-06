---
title: 'Vorgehensweise: Signieren von Office-Projektmappen | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 31b5e1fc3c78aecf518af0941a4a2dd0ab7e57c5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-sign-office-solutions"></a>Gewusst wie: Signieren von Office-Projektmappen
  Wenn Sie eine Projektmappe anmelden, können Sie der Projektmappe mithilfe des Zertifikats als Beweis Vertrauenswürdigkeit zu gewähren. Sie können das gleiche Zertifikat für mehrere Lösungen verwenden, und aller Lösungen werden keine richtlinienupdates Sicherheitsvorkehrungen vertrauenswürdig sein.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Wenn Sie die Anwendung manuell bearbeiten und die Bereitstellungsmanifeste mit dem Manifest Tool zum Generieren und bearbeiten (mage.exe und mageui.exe), müssen Sie das Manifest neu signieren, bevor Sie sie verwenden können. Weitere Informationen finden Sie unter [Gewusst wie: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifesten](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests).  
  
## <a name="signing-by-using-a-certificate"></a>Mit einem Zertifikat signieren  
 Ein Zertifikat ist eine Datei, die einen eindeutigen Schlüssel und die Identität des Lösungsherausgebers enthält. Sie können Zertifikate von einer Zertifizierungsstelle erwerben oder Ihr eigenes Zertifikat erstellen und eine Zertifizierungsstelle signieren.  
  
 Visual Studio signiert die Office-Projektmappen mit einem temporären Zertifikat, um Debuggen zu aktivieren. Sie sollten das temporäre Zertifikat nicht als Beweis in bereitgestellten Lösungen verwenden.  
  
#### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Zum Signieren von Office-Projektmappe mithilfe eines Zertifikats  
  
1.  Auf der **Projekt** Menü klicken Sie auf * SolutionName ***Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Signierung**.  
  
3.  Wählen Sie **ClickOnce-Manifeste signieren**.  
  
4.  Suchen Sie das Zertifikat, indem Sie auf **aus Speicher auswählen** oder **wählen Sie aus der Datei** und das Navigieren zu dem Zertifikat.  
  
5.  Um sicherzustellen, dass das richtige Zertifikat verwendet wird, klicken Sie auf **mehr Details** So zeigen Sie die Zertifikatinformationen an.  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Gewähren von Vertrauenswürdigkeit für Office-Projektmappen](../vsto/granting-trust-to-office-solutions.md)   
 [Seite „Signierung“, Projekt-Designer](/visualstudio/ide/reference/signing-page-project-designer)  
  
  