---
title: Eigenschaftenfunktionen| Microsoft-Dokumentation
ms.custom: 
ms.date: 02/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
caps.latest.revision: 33
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
ms.sourcegitcommit: 203e1e27cc892e96b103fc6cb22a73672a8e16af
ms.openlocfilehash: f351952a256679ec2d6c9dc2daa5288ca7214ad0
ms.lasthandoff: 03/01/2017

---
# <a name="property-functions"></a>Eigenschaftenfunktionen
In .NET Framework, Versionen 4 und 4.5, können Eigenschaftenfunktionen zur Auswertung von MSBuild-Skripts verwendet werden. Eigenschaftenfunktionen können immer dann verwendet werden, wenn Eigenschaften vorhanden sind. Im Gegensatz zu Aufgaben können Eigenschaftenfunktionen außerhalb von Zielen verwendet werden, und sie werden ausgewertet, bevor Ziele ausgeführt werden.  

 Sie können die Systemzeit lesen, Zeichenfolgen vergleichen, reguläre Ausdrücke abgleichen und viele weitere Aktionen im Buildskript ausführen, ohne MSBuild-Aufgaben zu verwenden. MSBuild versucht, eine Zeichenfolge in eine Zahl und eine Zahl in eine Zeichenfolge zu konvertieren und nimmt je nach Bedarf andere Konvertierungen vor.  

## <a name="property-function-syntax"></a>Syntax einer Eigenschaftenfunktion  
 Nachfolgend sehen Sie drei Arten von Eigenschaftenfunktionen; jede Funktion hat eine andere Syntax:  

-   Zeichenfolgen-(Instanz-)Eigenschaftenfunktionen  

-   Statische Eigenschaftenfunktionen  

-   MSBuild-Eigenschaftenfunktionen  

### <a name="string-property-functions"></a>Zeichenfolgen-Eigenschaftenfunktionen  
 Alle Buildeigenschaftswerte sind lediglich Zeichenfolgenwerte. Sie können Zeichenfolgen-(Instanz-)Methoden für beliebige Eigenschaftswerte verwenden. Sie können beispielsweise mithilfe des folgendes Codes den Laufwerksnamen (die ersten drei Buchstaben) aus einer Buildeigenschaft extrahieren, die einen vollständigen Pfad darstellt:  

 `$(ProjectOutputFolder.Substring(0,3))`  

### <a name="static-property-functions"></a>Statische Eigenschaftenfunktionen  
 In Ihrem Buildskript können Sie auf die statischen Eigenschaften und Methoden vieler Systemklassen zugreifen. Um den Wert einer statischen Eigenschaft abzurufen, verwenden Sie die folgende Syntax, wobei *Class* der Name der Systemklasse und *Property* der Name der Eigenschaft ist.  

 `$([Class]::Property)`  

 Sie können beispielsweise den folgenden Code verwenden, um eine Buildeigenschaft auf das aktuelle Datum und die aktuelle Uhrzeit festzulegen.  

 `<Today>$([System.DateTime]::Now)</Today>`  

 Um eine statische Methode aufzurufen, verwenden Sie die folgende Syntax, wobei *Class* der Name der Systemklasse, *Method* der Name der Methode und *(Parameter)* die Parameterliste für die Methode ist:  

 `$([Class]::Method(Parameters))`  

 Verwenden Sie beispielsweise das folgende Skript, um eine Buildeigenschaft auf eine neu GUID festzulegen:  

 `<NewGuid>$([System.Guid]::NewGuid())</NewGuid>`  

 In statischen Eigenschaftenfunktionen können Sie eine beliebige statische Methode oder Eigenschaft der folgenden Systemklassen verwenden:  

-   System.Byte  

-   System.Char  

-   System.Convert  

-   System.DateTime  

-   System.Decimal  

-   System.Double  

-   System.Enum  

-   System.Guid  

-   System.Int16  

-   System.Int32  

-   System.Int64  

-   System.IO.Path  

-   System.Math  

-   System.UInt16  

-   System.UInt32  

-   System.UInt64  

-   System.SByte  

-   System.Single  

-   System.String  

-   System.StringComparer  

-   System.TimeSpan  

-   System.Text.RegularExpressions.Regex  

-   Microsoft.Build.Utilities.ToolLocationHelper  

 Außerdem können Sie die folgenden statischen Methoden und Eigenschaften verwenden:  

-   System.Environment::CommandLine  

-   System.Environment::ExpandEnvironmentVariables  

-   System.Environment::GetEnvironmentVariable  

-   System.Environment::GetEnvironmentVariables  

-   System.Environment::GetFolderPath  

-   System.Environment::GetLogicalDrives  

-   System.IO.Directory::GetDirectories  

-   System.IO.Directory::GetFiles  

-   System.IO.Directory::GetLastAccessTime  

-   System.IO.Directory::GetLastWriteTime  

-   System.IO.Directory::GetParent  

-   System.IO.File::Exists  

-   System.IO.File::GetCreationTime  

-   System.IO.File::GetAttributes  

-   System.IO.File::GetLastAccessTime  

-   System.IO.File::GetLastWriteTime  

-   System.IO.File::ReadAllText  

### <a name="calling-instance-methods-on-static-properties"></a>Aufrufen von Instanzmethoden für statische Eigenschaften  
 Wenn Sie auf eine statische Eigenschaft zugreifen, die eine Objektinstanz zurückgibt, können Sie die Instanzmethoden dieses Objekts aufrufen. Um eine statische Methode aufzurufen, verwenden Sie die folgende Syntax, wobei *Class* der Name der Systemklasse, *Property* der Name der Eigenschaft, *Method* der Name der Methode und *(Parameter)* die Parameterliste für die Methode ist:  

 `$([Class]::Property.Method(Parameters))`  

 Der Name der Klasse muss mit dem Namespace vollqualifiziert sein.  

 Sie können beispielsweise den folgenden Code verwenden, um eine Buildeigenschaft auf das heutige Datum festzulegen.  

 `<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>`  

### <a name="msbuild-property-functions"></a>MSBuild-Eigenschaftenfunktionen  
 In Ihrem Build kann auf mehrere statische Methoden zugegriffen werden, um Unterstützung für arithmetische, bitweise logische und Escapezeichen bereitzustellen. Um eine statische Methode aufzurufen, verwenden Sie die folgende Syntax, wobei *Method* der Name der Methode und *Parameter* die Parameterliste für die Methode ist.  

 `$([MSBuild]::Method(Parameters))`  

 Um beispielsweise zwei Eigenschaften mit numerischen Werten zu addieren, verwenden Sie den folgenden Code.  

 `$([MSBuild]::Add($(NumberOne), $(NumberTwo))`  

 Nachfolgend finden Sie eine Liste mit MSBuild-Eigenschaftenfunktionen:  

|Funktionssignatur|Beschreibung|  
|------------------------|-----------------|  
|double Add(double a, double b)|Addiert zwei double-Werte.|  
|long Add(long a, long b)|Addiert zwei long-Werte.|  
|double Subtract(double a, double b)|Subtrahiert zwei double-Werte.|  
|long Subtract(long a, long b)|Subtrahiert zwei long-Werte.|  
|double Multiply(double a, double b)|Multipliziert zwei double-Werte.|  
|long Multiply(long a, long b)|Multipliziert zwei long-Werte.|  
|double Divide(double a, double b)|Dividiert zwei double-Werte.|  
|long Divide(long a, long b)|Dividiert zwei long-Werte.|  
|double Modulo(double a, double b)|Modulo-Berechnung für zwei double-Werte.|  
|long Modulo(long a, long b)|Modulo-Berechnung für zwei long-Werte.|  
|string Escape(string unescaped)|Setzt gemäß den MSBuild-Escape-Regeln ein Escapezeichen vor die Zeichenfolge.|  
|string Unescape(string escaped)|Entfernt gemäß den MSBuild-Escape-Regeln ein Escapezeichen vor der Zeichenfolge.|  
|int BitwiseOr(int first, int second)|Führt einen bitweisen `OR`-Vorgang für das erste und zweite Element aus (first &#124; second).|  
|int BitwiseAnd(int first, int second)|Führt einen bitweisen `AND`-Vorgang für das erste und zweite Element aus (first & second).|  
|int BitwiseXor(int first, int second)|Führt einen bitweisen `XOR`-Vorgang für das erste und zweite Element aus (first ^ second).|  
|int BitwiseNot(int first)|Führt einen bitweisen `NOT`-Vorgang aus (~first).|  

##  <a name="nested-property-functions"></a>Geschachtelte Eigenschaftenfunktionen  
 Sie können Eigenschaftenfunktionen kombinieren, um komplexere Funktionen zu erstellen, wie das folgende Beispiel zeigt.  

 `$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))`  

 In diesem Beispiel wird der Wert der <xref:System.IO.FileAttributes>`Archive`-Bit (32 oder 0) der Datei zurückgegeben, die durch den Pfad `tempFile` angegeben wird. Beachten Sie, dass Enumerationsdatenwerte innerhalb von Eigenschaftenfunktionen nicht nach Name angezeigt werden können. Stattdessen muss der numerische Wert (32) verwendet werden.  

 Metadaten können auch in geschachtelten Eigenschaftenfunktionen angezeigt werden. Weitere Informationen finden Sie unter [MSBuild Batching (Batchverarbeitung)](../msbuild/msbuild-batching.md).  

##  <a name="msbuild-doestaskhostexist"></a>MSBuild DoesTaskHostExist  
 Die `DoesTaskHostExist`-Eigenschaftenfunktion in MSBuild gibt zurück, ob derzeit ein Aufgabenhost für die angegebenen Laufzeit- und Architekturwerte installiert wird.  

 Diese Eigenschaftenfunktion hat die folgende Syntax:  

```  
$[MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture)  
```  

##  <a name="msbuild-ensuretrailingslash"></a>MSBuild EnsureTrailingSlash  
 Die `EnsureTrailingSlash`-Eigenschaftenfunktion in MSBuild fügt einen nachgestellten Schrägstrich hinzu, wenn noch keiner vorhanden ist.  

 Diese Eigenschaftenfunktion hat die folgende Syntax:  

```  
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)')  
```  

##  <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild GetDirectoryNameOfFileAbove  
 Die `GetDirectoryNameOfFileAbove`-Eigenschaftenfunktion in MSBuild sucht in den Verzeichnissen über dem aktuellen Verzeichnis im Pfad nach einer Datei.  

 Diese Eigenschaftenfunktion hat die folgende Syntax:  

```  
$[MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile)  
```  

 Der folgende Code veranschaulicht diese Syntax beispielhaft.  

```xml  
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />  
```  

##  <a name="msbuild-getpathoffileabove"></a>MSBuild GetPathOfFileAbove  
 Die `GetPathOfFileAbove`-Eigenschaftenfunktion in MSBuild gibt den Pfad der Datei unmittelbar vor diesem zurück. Sie ist zum Aufruf funktional äquivalent.

 ```<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />```

 Diese Eigenschaftenfunktion hat die folgende Syntax:  

```  
$([MSBuild]::GetPathOfFileAbove(dir.props)  
```  

##  <a name="msbuild-getregistryvalue"></a>MSBuild GetRegistryValue  
 Die `GetRegistryValue`-Eigenschaftenfunktion in MSBuild gibt den Wert eines Registrierungsschlüssels zurück. Diese Funktion weist zwei Argumente auf, den Schlüsselnamen und den Wertnamen, und gibt den Wert aus der Registrierung zurück. Wenn Sie keinen Wertnamen angeben, wird der Standardwert zurückgegeben.  

 In den folgenden Beispielen wird veranschaulicht, wie diese Funktion verwendet wird:  

```  
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value  
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))  
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value  

```  

##  <a name="msbuild-getregistryvaluefromview"></a>MSBuild GetRegistryValueFromView  
 Die `GetRegistryValueFromView`-Eigenschaftenfunktion in MSBuild ruft Systemregistrierungsdaten anhand des Registrierungsschlüssels, des Werts und einer oder mehrerer geordneter Registrierungsansichten ab. Der Wert und der Schlüssel werden der Reihe nach in jeder Registrierungsansicht gesucht, bis sie gefunden wurden.  

 Die Syntax für diese Eigenschaftenfunktion ist wie folgt:  

 [MSBuild\]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)  

 Das Windows-Betriebssystem mit 64 Bit speichert einen HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node-Registrierungsschlüssel, der eine HKEY_LOCAL_MACHINE\SOFTWARE-Registrierungsansicht für 32-Bit-Anwendungen darstellt.  

 Eine 32-Bit-Anwendung, die unter WOW64 ausgeführt wird, greift standardmäßig auf die 32-Bit-Registrierungsansicht zu, und eine 64-Bit-Anwendung greift auf die 64-Bit-Registrierungsansicht zu.  

 Die folgenden Registrierungsansichten sind verfügbar:  

|Registrierungsansicht|Definition|  
|-------------------|----------------|  
|RegistryView.Registry32|Die Registrierungsansicht für 32-Bit-Anwendungen.|  
|RegistryView.Registry64|Die Registrierungsansicht für 64-Bit-Anwendungen.|  
|RegistryView.Default|Die Registrierungsansicht, die mit dem Prozess übereinstimmt, auf dem die Anwendung ausgeführt wird.|  

 Nachfolgend finden Sie ein Beispiel:  

 `$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))`  

 ruft die SLRuntimeInstallPath-Daten des ReferenceAssemblies-Schlüssels ab und such zuerst in der 64-Bit-Registrierungsansicht und dann in der 32-Bit-Registrierungsansicht.  

##  <a name="msbuild-makerelative"></a>MSBuild MakeRelative  
 Die `MakeRelative`-Eigenschaftenfunktion in MSBuild gibt den relativen Pfad des zweiten Pfads relativ zum ersten Pfad an. Jeder Pfad kann eine Datei oder ein Ordner sein.  

 Diese Eigenschaftenfunktion hat die folgende Syntax:  

```  
$[MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2))  
```  

 Der folgende Code veranschaulicht diese Syntax beispielhaft.  

```xml  
<PropertyGroup>  
    <Path1>c:\users\</Path1>  
    <Path2>c:\users\username\</Path2>  
</PropertyGroup>  

<Target Name = "Go">  
    <Message Text ="$([MSBuild]::MakeRelative($(Path1), $(Path2)))" />  
    <Message Text ="$([MSBuild]::MakeRelative($(Path2), $(Path1)))" />  
</Target>  

<!--  
Output:  
   username\  
   ..\  
-->  
```  

##  <a name="msbuild-valueordefault"></a>MSBuild ValueOrDefault  
 Die `ValueOrDefault`-Eigenschaftenfunktion in MSBuild gibt das erste Argumente zurück, sofern dieses nicht Null oder leer ist. Wenn das erste Argument Null oder leer ist, gibt die Funktion das zweite Argument zurück.  

 In dem folgenden Beispiel wird veranschaulicht, wie diese Funktion verwendet wird.  

```xml  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  

    <PropertyGroup>  
        <Value1>$([MSBuild]::ValueOrDefault(`$(UndefinedValue)`, `a`))</Value1>  
        <Value2>$([MSBuild]::ValueOrDefault(`b`, `$(Value1)`))</Value2>  
    </PropertyGroup>  

    <Target Name="MyTarget">  
        <Message Text="Value1 = $(Value1)" />  
        <Message Text="Value2 = $(Value2)" />  
    </Target>  
</Project>  

<!--  
Output:   
  Value1 = a  
  Value2 = b  
-->  
```

## <a name="see-also"></a>Siehe auch
[MSBuild-Eigenschaften](../msbuild/msbuild-properties.md)   
[Übersicht über MSBuild](../msbuild/msbuild.md)
