---
title: ClickOnce-Bereitstellungsmanifest | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce, deployment manifests
- deployment manifests [ClickOnce]
ms.assetid: 8457e615-e3b6-4990-8dcf-11bc590e4e9b
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 5664c3505c44cb519365e7f15344d390eeebac0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="clickonce-deployment-manifest"></a>ClickOnce-Bereitstellungsmanifest
Ein Bereitstellungsmanifest ist eine XML-Datei, die eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Bereitstellung beschreibt, einschließlich der Bestimmung der aktuellen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Anwendungsversion für die Bereitstellung.  
  
 Bereitstellungsmanifeste verfügen über die folgenden Elemente und Attribute.  
  
|Element|Beschreibung|Attribute|  
|-------------|-----------------|----------------|  
|[\<Assembly >-Element](../deployment/assembly-element-clickonce-deployment.md)|Erforderlich. Ein Element der obersten Ebene.|`manifestVersion`|  
|[\<AssemblyIdentity >-Element](../deployment/assemblyidentity-element-clickonce-deployment.md)|Erforderlich. Identifiziert das Anwendungsmanifest für die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Bereitstellung.|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `culture`|  
|[\<Description >-Element](../deployment/description-element-clickonce-deployment.md)|Erforderlich. Identifiziert Anwendungsinformationen, die zum Erstellen eines Shell-Eintrags verwendet und die **Software** Element in der Systemsteuerung.|`publisher`<br /><br /> `product`<br /><br /> `supportUrl`|  
|[\<Deployment >-Element](../deployment/deployment-element-clickonce-deployment.md)|Dies ist optional. Identifiziert die Attribute, die für die Bereitstellung von Updates und zum Verfügbarmachen für das System verwendet werden.|`install`<br /><br /> `minimumRequiredVersion`<br /><br /> `mapFileExtensions`<br /><br /> `disallowUrlActivation`<br /><br /> `trustUrlParameters`|  
|[\<CompatibleFrameworks >-Element](../deployment/compatibleframeworks-element-clickonce-deployment.md)|Erforderlich. Identifiziert die Versionen von .NET Framework, mit denen diese Anwendung installiert und ausgeführt werden kann.|`SupportUrl`|  
|[\<Dependency >-Element](../deployment/dependency-element-clickonce-deployment.md)|Erforderlich. Identifiziert die Version der Anwendung, die für die Bereitstellung installiert werden soll, und den Speicherort des Anwendungsmanifests.|`preRequisite`<br /><br /> `visible`<br /><br /> `dependencyType`<br /><br /> `codebase`<br /><br /> `size`|  
|[\<PublisherIdentity >-Element](../deployment/publisheridentity-element-clickonce-deployment.md)|Für signierte Manifeste erforderlich. Enthält Informationen zum Herausgeber, der dieses Bereitstellungsmanifest signiert hat.|`Name`<br /><br /> `issuerKeyHash`|  
|[\<Signatur >-Element](../deployment/signature-element-clickonce-deployment.md)|Dies ist optional. Enthält die notwendigen Informationen, um dieses Bereitstellungsmanifest digital zu signieren.|Keiner|  
|[\<CustomErrorReporting >-Element](../deployment/customerrorreporting-element-clickonce-deployment.md)|Dies ist optional. Gibt einen URI an, der bei einem Fehler angezeigt wird.|URI|  
  
## <a name="remarks"></a>Hinweise  
 Die Bereitstellungsmanifestdatei identifiziert eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Anwendungsbereitstellung einschließlich der aktuellen Version und anderer Bereitstellungseinstellungen. Sie verweist auf das Anwendungsmanifest, in dem die aktuelle Version der Anwendung und alle in der Bereitstellung enthaltenen Dateien beschrieben werden.  
  
 Weitere Informationen finden Sie unter [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).  
  
## <a name="file-location"></a>Dateiort  
 Die Bereitstellungsmanifestdatei verweist auf das richtige Anwendungsmanifest für die aktuelle Version der Anwendung. Wenn Sie eine neue Version einer Anwendungsbereitstellung verfügbar machen, müssen Sie das Bereitstellungsmanifest zum Verweisen auf das neue Anwendungsmanifest aktualisieren.  
  
 Die Bereitstellungsmanifestdatei muss über einen starken Namen verfügen und kann auch Zertifikate für die Herausgeberüberprüfung enthalten.  
  
## <a name="file-name-syntax"></a>Dateinamensyntax  
 Der Name einer Bereitstellungsmanifestdatei muss mit der Erweiterung .application enden.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Codebeispiel veranschaulicht ein Bereitstellungsmanifest.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <assemblyIdentity   
    name="My Application Deployment.app"  
    version="1.0.0.0"  
    publicKeyToken="43cb1e8e7a352766"  
    language="neutral"  
    processorArchitecture="x86"  
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <description  
    asmv2:publisher="My Company Name"  
    asmv2:product="My Application"  
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <deployment install="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="0" unit="days" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="\\myServer\sampleDeployment\MyApplicationDeployment.application" />  
  </deployment>  
  <compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
    <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.20506" />  
    <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.20506" />  
  </compatibleFrameworks>  
  <dependency>  
    <dependentAssembly  
      dependencyType="install"  
      codebase="1.0.0.0\My Application Deployment.exe.manifest"  
      size="6756">  
      <assemblyIdentity  
        name="My Application Deployment.exe"  
        version="1.0.0.0"  
        publicKeyToken="43cb1e8e7a352766"  
        language="neutral"  
        processorArchitecture="x86"  
        type="win32" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>E506x9FwNauks7UjQywmzgtd3FE=</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
<publisherIdentity name="CN=DOMAIN\MyUsername" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">  
...  
</Signature></asmv1:assembly>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)