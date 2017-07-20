---
title: "Dialogfeld Erweiterte Einstellungen für Dienste | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
caps.latest.revision: 14
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: af39a14f54ff5e68ff16b29833546f266f4be962
ms.lasthandoff: 02/22/2017

---
# <a name="advanced-settings-for-services-dialog-box"></a>Dialogfeld "Erweiterte Einstellungen für Dienste"
Clientanwendungsdienste ermöglichen vereinfachten Zugriff auf [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)]-Anmeldung, Rollen und Profildienste von Windows Forms- und Windows Presentation Foundation-Anwendungen (WPF). Sie können die Seite **Dienste** im **Projekt-Designer** verwenden, um Clientanwendungsdienste zu konfigurieren. Weitere Informationen zur Seite **Dienste** finden Sie unter [Services-Seite, Projekt-Designer](../../ide/reference/services-page-project-designer.md).  
  
 Verwenden Sie das Dialogfeld **Erweiterte Einstellungen für Dienste** auf der Seite **Dienste** im **Projekt-Designer**, um erweiterte Einstellungen für Clientanwendungsdienste zu konfigurieren. Mithilfe dieser Einstellungen können sie das Standardverhalten der Anwendungsdienste außer Kraft setzen, um seltenere Szenarios zu ermöglichen. Weitere Informationen finden Sie unter [Clientanwendungsdienste](http://msdn.microsoft.com/Library/1487d8df-089e-4f21-abfb-a791a652b58e).  
  
 Wählen Sie zum Aufrufen des Dialogfelds **Erweiterte Einstellungen für Dienste** im **Projektmappenexplorer** einen Projektknoten aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**. Wenn der **Projekt-Designer** geöffnet wurde, klicken Sie auf die Registerkarte **Dienste** und anschließend auf die Schaltfläche **Erweitert**. Diese Schaltfläche ist solange deaktiviert, bis Sie Clientanwendungsdienste aktivieren.  
  
## <a name="task-list"></a>Aufgabenliste  
 [Vorgehensweise: Konfigurieren von Clientanwendungsdiensten](http://msdn.microsoft.com/Library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)  
  
 [Vorgehensweise: Offline arbeiten mit Clientanwendungsdiensten](http://msdn.microsoft.com/en-us/f792cb16-8520-4a0f-9dc9-07bfbc454e38)  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Kennworthash lokal &speichern, um Offlineanmeldung zu ermöglichen**  
 Gibt an, ob ein verschlüsseltes Formular des Benutzerkennworts lokal zwischengespeichert wird, damit sich der Benutzer auch anmelden kann, wenn sich die Anwendung im Offlinemodus befindet. Weitere Informationen finden Sie unter [Vorgehensweise: Offline arbeiten mit Clientanwendungsdiensten](http://msdn.microsoft.com/en-us/f792cb16-8520-4a0f-9dc9-07bfbc454e38). Diese Option ist standardmäßig ausgewählt.  
  
 **Erneute Benutzeranmeldung bei Ablauf des Cookies anfordern**  
 Gibt an, ob bereits authentifizierte Benutzer automatisch wieder authentifiziert werden, wenn Ihre Anwendung auf Rollen- oder Profildienste zugreift und der Serverauthentifizierungscookie abgelaufen ist. Wählen Sie diese Option aus, um den Zugriff auf Anwendungsdienste zu verweigern und eine erneute Authentifizierung zu verlangen, nachdem das Cookie abgelaufen ist. Diese Option ist nützlich für Anwendungen, die an öffentlichen Speicherorten bereitgestellt werden, um sicherzustellen, dass Benutzer, die die Anwendung nach Gebrauch weiterhin ausführen, nicht auf unbestimmte Zeit authentifiziert bleiben. Diese Option ist standardmäßig deaktiviert.  
  
 **Cachetimeout des Rollendiensts**  
 Gibt die Zeit an, für die der Clientrollenanbieter zwischengespeicherte Rollenwerte verwendet, statt auf den Rollendienst zuzugreifen. Legen Sie dieses Zeitintervall auf einen kleinen Wert fest, wenn Rollen häufig aktualisiert werden, oder auf einen höheren Wert, wenn Rollen seltener aktualisiert werden. Der Standardwert ist ein Tag.  
  
 Der Rollenanbieter greift auf die zwischengespeicherten Rollenwerte oder den Rollendienst zu, wenn Sie die Methode <xref:System.Web.Security.RolePrincipal.IsInRole%2A> aufrufen. Um den Cache programmgesteuert zu leeren und diese Methode zu zwingen, auf den Remotedienst zuzugreifen, rufen Sie die Methode <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> auf.  
  
 **Verwenden einer benutzerdefinierten Verbindungszeichenfolge**  
 Gibt an, ob der Clientdienstanbieter benutzerdefinierte Datenspeicher für den lokalen Cache verwendet. Die Dienstanbieter verwenden standardmäßig das lokale Dateisystem für den Cache. Wenn Sie diese Option auswählen, wird das Textfeld automatisch mit einer Standardverbindungszeichenfolge gefüllt. Sie können beibehalten, dass die Standardverbindungszeichenfolge automatisch eine SQL Server Compact Edition-Datenbank generiert und verwendet, Sie können aber auch eine Verbindungszeichenfolge für eine vorhandene SQL Server-Datenbank festlegen. Weitere Informationen finden Sie unter [Vorgehensweise: Konfigurieren von Clientanwendungsdiensten](http://msdn.microsoft.com/Library/34a8688a-a32c-40d3-94be-c8e610c6a4e8). Diese Option ist standardmäßig deaktiviert.  
  
## <a name="see-also"></a>Siehe auch  
 [Clientanwendungsdienste](http://msdn.microsoft.com/Library/1487d8df-089e-4f21-abfb-a791a652b58e)   
 [Services-Seite, Projekt-Designer](../../ide/reference/services-page-project-designer.md)   
 [Vorgehensweise: Konfigurieren von Clientanwendungsdiensten](http://msdn.microsoft.com/Library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)   
 [Vorgehensweise: Offline arbeiten mit Clientanwendungsdiensten](http://msdn.microsoft.com/en-us/f792cb16-8520-4a0f-9dc9-07bfbc454e38)