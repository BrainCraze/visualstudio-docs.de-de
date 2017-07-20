---
title: "Schemareferenz zu Visual Studio-Vorlagen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".vstemplate-Dateien"
  - "Visual Studio-Vorlagen, Schema"
  - "VSTEMPLATE-Dateien"
ms.assetid: 6f74a2d5-3811-43d6-8b10-eb5823ad8995
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Schemareferenz zu Visual Studio-Vorlagen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieser Abschnitt enthält Informationen zu XML\-Elementen in VSTEMPLATE\-Dateien. Dies sind Dateien, in denen Metadaten für Projektvorlagen, Elementvorlagen und Starter Kits gespeichert werden.  
  
 Sie können vstemplate.xsd zur Überprüfung benutzerdefinierter VSTEMPLATE\-Dateien verwenden.  Diese Datei ist verfügbar in ..\\*Visual Studio installation folder*\\Xml\\Schemas\\1033\\vstemplate.xsd.  
  
|Element|Untergeordnete Elemente|Attribute|  
|-------------|-----------------------------|---------------|  
|[AppliesTo](../extensibility/appliesto-element-visual-studio-templates.md)|Kein|Kein|  
|[Assembly \(Vorlage\)](../extensibility/assembly-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Assembly \(Assistentenerweiterung\)](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|\-\-|\-\-|  
|[BuildProjectOnload](../extensibility/buildprojectonload-element-visual-studio-templates.md)|\-\-|\-\-|  
|[CreateInPlace](../extensibility/createinplace-visual-studio-templates.md)|\-\-|\-\-|  
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|\-\-|\-\-|  
|[CustomDataSignature](../extensibility/customdatasignature-element-visual-studio-templates.md)|\-\-|\-\-|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|\-\-|Name<br /><br /> Wert|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|CustomParameter|\-\-|  
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Beschreibung](../extensibility/description-element-visual-studio-templates.md)|\-\-|Package<br /><br /> ID|  
|[EnableEditOfLocationField](../extensibility/enableeditoflocationfield-element-visual-studio-templates.md)|\-\-|\-\-|  
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Ordner](../extensibility/folder-element-visual-studio-project-templates.md)|ProjectItem<br /><br /> Ordner|Name|  
||\[veraltet\]|\-\-|  
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|\-\-|\-\-|  
|[Hidden](../extensibility/hidden-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Symbol](../extensibility/icon-element-visual-studio-templates.md)|\-\-|Package<br /><br /> ID|  
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|\-\-|\-\-|  
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|\-\-|\-\-|  
|[MaxFrameworkVersion](../extensibility/maxframeworkversion-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Name](../extensibility/name-element-visual-studio-templates.md)|\-\-|Package<br /><br /> ID|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|\-\-|\-\-|  
|[PreviewImage](../extensibility/previewimage-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|Ordner<br /><br /> ProjectItem|Datei<br /><br /> TargetFileName<br /><br /> ReplaceParameters|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|\-\-|  
|[ProjectItem \(Elementvorlagen\)](../extensibility/projectitem-element-visual-studio-item-templates.md)|\-\-|SubType<br /><br /> CustomTool<br /><br /> ItemType<br /><br /> ReplaceParameters<br /><br /> TargetFileName|  
|[ProjectItem \(Projektvorlagen\)](../extensibility/projectitem-element-visual-studio-project-templates.md)|\-\-|TargetFileName<br /><br /> ReplaceParameters<br /><br /> OpenInEditor<br /><br /> OpenOrder<br /><br /> OpenInWebBrowser<br /><br /> OpenInHelpBrowser|  
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|\-\-|\-\-|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|\-\-|ProjectName|  
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|\-\-|\-\-|  
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|\-\-|\-\-|  
|[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Verweis](../extensibility/reference-element-visual-studio-templates.md)|Assembly|\-\-|  
|[Verweise](../extensibility/references-element-visual-studio-templates.md)|Verweis|\-\-|  
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|\-\-|\-\-|  
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|\-\-|Version|  
|[SDKReferenz](72c8b352-0b7a-42b3-ba5d-2a2d1e90c3)|\-\-|Package|  
|[ShowByDefault](../extensibility/showbydefault-visual-studio-templates.md)|\-\-|\-\-|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|Name|  
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|\-\-|\-\-|  
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|\-\-|\-\-|  
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|\-\-|\-\-|  
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|\-\-|\-\-|  
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|RequiredPlatformVersion|\-\-|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|ProjectCollection<br /><br /> Project<br /><br /> Verweise<br /><br /> ProjectItem<br /><br /> CustomParameters|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Name<br /><br /> Beschreibung<br /><br /> Symbol<br /><br /> PreviewImage<br /><br /> ProjectType<br /><br /> ProjectSubType<br /><br /> TemplateID<br /><br /> TemplateGroupID<br /><br /> SortOrder<br /><br /> CreateNewFolder<br /><br /> DefaultName<br /><br /> ProvideDefaultName<br /><br /> PromptForSaveOnCreation<br /><br /> EnableLocationBrowseButton<br /><br /> EnableEditOfLocationField<br /><br /> Hidden<br /><br /> DisplayInParentCategories<br /><br /> LocationFieldMRUPrefix<br /><br /> NumberOfParentCategoriesToRollUp<br /><br /> CreateInPlace<br /><br /> BuildOnLoad<br /><br /> BuildProjectOnload<br /><br /> ShowByDefault<br /><br /> LocationField<br /><br /> SupportsMasterPage<br /><br /> SupportsCodeSeparation<br /><br /> SupportsLanguageDropDown<br /><br /> RequiredFrameworkVersion<br /><br /> FrameworkVersion<br /><br /> MaxFrameworkVersion<br /><br /> CustomDataSignature<br /><br /> TargetPlatformName|\-\-|  
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|\-\-|\-\-|  
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|\-\-|\-\-|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|TemplateData<br /><br /> TemplateContent<br /><br /> WizardExtension<br /><br /> WizardData|Typ<br /><br /> Version|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|\-\-|Name|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Assembly<br /><br /> FullClassName|\-\-|  
  
## Siehe auch  
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Gewusst wie: Erstellen von Starter Kits](../ide/how-to-create-starter-kits.md)