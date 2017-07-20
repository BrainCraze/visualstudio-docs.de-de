---
title: "Assertionen in verwaltetem Code | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Assertionen, Verwalteter Code"
  - "Assertionen, Nebeneffekte"
  - "Debug.Assert-Methode"
  - "Debug.Listeners-Eigenschaft"
  - "Debuggen [Visual Studio], Assertionen in verwaltetem Code"
  - "Debuggen von verwaltetem Code, Assertionen"
  - "Trace.Assert-Methode"
  - "Trace.Listeners-Eigenschaft"
ms.assetid: 70ab2522-6486-4076-a1a9-e0f11cd0f3a1
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Assertionen in verwaltetem Code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mithilfe einer Assertion oder einer `Assert`\-Anweisung wird eine Bedingung überprüft, die Sie als Argument der `Assert`\-Anweisung angeben.  Wenn die Bedingung als "Tue" ausgewertet wird, erfolgt keine Aktion.  Wenn die Bedingung auf "False" ausgewertet wird, schlägt die Assertion fehl.  Wenn das Programm mit einem Debugbuild ausgeführt wird, wechselt es in den Unterbrechungsmodus.  
  
##  <a name="BKMK_In_this_topic"></a> In diesem Thema  
 [Assertionen im System.Diagnostics-Namespace](#BKMK_Asserts_in_the_System_Diagnostics_Namespace)  
  
 [Die Debug.Assert-Methode](#BKMK_The_Debug_Assert_method)  
  
 [Nebeneffekte der Debug.Assert-Methode](#BKMK_Side_effects_of_Debug_Assert)  
  
 [Voraussetzungen für Ablaufverfolgung und Debug](#BKMK_Trace_and_Debug_Requirements)  
  
 [Assert-Argumente](#BKMK_Assert_arguments)  
  
 [Anpassen des Assert-Verhaltens](#BKMK_Customizing_Assert_behavior)  
  
 [Festlegen von Assertionen in Konfigurationsdateien](#BKMK_Setting_assertions_in_configuration_files)  
  
##  <a name="BKMK_Asserts_in_the_System_Diagnostics_Namespace"></a> Assertionen im System.Diagnostics\-Namespace  
 In Visual Basic und Visual C\# können Sie die `Assert`\-Methode von <xref:System.Diagnostics.Debug> oder <xref:System.Diagnostics.Trace> verwenden, die sich im <xref:System.Diagnostics>\-Namespace befinden.  <xref:System.Diagnostics.Debug>\-Klassenmethoden sind nicht in einer Releaseversion des Programms enthalten, deshalb vergrößern sie nicht den Versionscode oder reduzieren dessen Geschwindigkeit.  
  
 C\+\+ unterstützt nicht die <xref:System.Diagnostics.Debug>\-Klassenmethoden.  Sie können dieselbe Wirkung durch Verwenden der <xref:System.Diagnostics.Trace>\-Klasse mit bedingter Kompilierung erzielen, z. B. `#ifdef DEBUG`...  `#endif`.  
  
 [In diesem Thema](#BKMK_In_this_topic)  
  
##  <a name="BKMK_The_Debug_Assert_method"></a> Die Debug.Assert\-Methode  
 Sie können die <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>\-Methode beliebig verwenden, um Bedingungen zu überprüfen, die bei fehlerfreiem Code "True" ergeben sollten.  Angenommen, Sie haben eine Funktion zum Dividieren von ganzen Zahlen geschrieben.  Gemäß den Regeln der Mathematik kann der Divisor niemals 0 sein.  Sie könnten diese Bedingung mithilfe einer Assertion testen:  
  
```vb  
Function IntegerDivide(ByVal dividend As Integer, ByVal divisor As Integer) As Integer  
    Debug.Assert(divisor <> 0)  
    Return CInt(dividend / divisor)  
End Function  
```  
  
```c#  
int IntegerDivide ( int dividend , int divisor )  
    { Debug.Assert ( divisor != 0 );  
        return ( dividend / divisor ); }  
```  
  
 Wenn Sie diesen Code im Debugger ausführen, wird die Assertionsanweisung ausgewertet. In der Releaseversion findet der Vergleich jedoch nicht statt, sodass kein Mehraufwand entsteht.  
  
 Im Folgenden ist ein weiteres Beispiel angegeben.  Sie verfügen über eine Klasse, mit der ein Girokonto wie folgt implementiert wird:  
  
```vb  
Dim amount, balance As Double  
balance = savingsAccount.balance  
Debug.Assert(amount <= balance)  
SavingsAccount.Withdraw(amount)  
```  
  
```c#  
float balance = savingsAccount.Balance;  
Debug.Assert ( amount <= balance );  
savingsAccount.Withdraw ( amount );  
```  
  
 Bevor Sie Geld von diesem Konto abheben, müssen Sie sicherstellen, dass das Konto genügend Deckung für den abzuhebenden Betrag aufweist.  Sie können eine Assertion schreiben, um den Saldo zu überprüfen:  
  
```vb  
Dim amount, balance As Double  
balance = savingsAccount.balance  
Trace.Assert(amount <= balance)  
SavingsAccount.Withdraw(amount)  
```  
  
```c#  
float balance = savingsAccount.Balance;  
Trace.Assert ( amount <= balance );  
savingsAccount.Withdraw ( amount );  
```  
  
 Bedenken Sie, dass Aufrufe der <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>\-Methode nicht mehr verfügbar sind, wenn Sie eine Releaseversion des Codes erstellen.  Dies bedeutet, dass der Aufruf zum Überprüfen des Kontosaldos in der Releaseversion nicht mehr vorhanden ist.  Um dieses Problem zu beheben, ersetzen Sie <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> durch <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, denn diese Methode ist in der Releaseversion weiterhin vorhanden.  
  
 Aufrufe von <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> verursachen jedoch im Gegensatz zu Aufrufen von <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> in der Releaseversion einen Mehraufwand.  
  
 [In diesem Thema](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Side_effects_of_Debug_Assert"></a> Nebeneffekte der Debug.Assert\-Methode  
 Stellen Sie bei Verwendung der <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>\-Methode sicher, dass die Programmergebnisse nicht vom Code innerhalb der `Assert`\-Methode beeinflusst werden, wenn `Assert` entfernt wurde.  Andernfalls kann dies zu einem Fehler führen, der lediglich in der Releaseversion des Programms auftritt.  Auch bei Assertionen, die Funktions\- oder Prozeduraufrufe enthalten, sollte besonders sorgfältig vorgegangen werden, wie im folgenden Beispiel:  
  
```vb  
' unsafe code  
Debug.Assert (meas(i) <> 0 )  
```  
  
```c#  
// unsafe code  
Debug.Assert (meas(i) != 0 );  
```  
  
 Diese Verwendung der <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>\-Methode mag auf den ersten Blick sicher erscheinen. Was geschieht jedoch, wenn die Funktion "meas" bei jedem Aufruf einen Zähler aktualisiert?  Bei der Erstellung der Releaseversion wird dieser Aufruf der Funktion "meas" entfernt, sodass der Zähler nicht mehr aktualisiert wird.  Dies ist ein Beispiel für eine Funktion mit einem Nebeneffekt.  Durch das Entfernen eines Funktionsaufrufs, der Nebeneffekte hat, kann ein Fehler verursacht werden, der ausschließlich in der Releaseversion auftritt.  Um derartige Probleme zu vermeiden, sollten Sie keine Funktionsaufrufe in eine <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>\-Anweisung einfügen.  Verwenden Sie stattdessen eine temporäre Variable:  
  
```vb  
temp = meas( i )  
Debug.Assert (temp <> 0)  
```  
  
```c#  
temp = meas( i );  
Debug.Assert ( temp != 0 );  
```  
  
 Auch wenn Sie die <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>\-Methode verwenden, möchten Sie möglicherweise Funktionsaufrufe innerhalb einer `Assert`\-Anweisung vermeiden.  Solche Aufrufe sollten kein Risiko darstellen, da <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>\-Anweisungen nicht aus einem Releasebuild entfernt werden.  Wenn Sie es sich jedoch zur Gewohnheit machen, solche Konstrukte zu vermeiden, können Sie Fehlern bei Verwendung der <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>\-Methode vorbeugen.  
  
 [In diesem Thema](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Trace_and_Debug_Requirements"></a> Voraussetzungen für Ablaufverfolgung und Debug  
 Wenn Sie das Projekt mithilfe der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Assistenten erstellen, wird das TRACE\-Symbol sowohl in der Release\- als auch in der Debugkonfiguration automatisch definiert.  Das DEBUG\-Symbol ist standardmäßig nur im Debugbuild definiert.  
  
 Andernfalls funktionieren die <xref:System.Diagnostics.Trace>\-Methoden nur dann, wenn im Programm am Anfang der Quelldatei Folgendes steht:  
  
-   `#Const TRACE = True` in Visual Basic  
  
-   `#define TRACE` in Visual C\# und C\+\+  
  
 Oder das Programm muss mit der TRACE\-Option erstellt werden:  
  
-   `/d:TRACE=True` in Visual Basic  
  
-   `/d:TRACE` in Visual C\# und C\+\+  
  
 Wenn Debug\-Methoden in einem C\#\- oder Visual Basic\-Releasebuild verwendet werden sollen, müssen Sie das DEBUG\-Symbol in der Releasekonfiguration definieren.  
  
 C\+\+ unterstützt nicht die <xref:System.Diagnostics.Debug>\-Klassenmethoden.  Sie können dieselbe Wirkung durch Verwenden der <xref:System.Diagnostics.Trace>\-Klasse mit bedingter Kompilierung erzielen, z. B. `#ifdef DEBUG`...  `#endif`.  Diese Symbole können im Dialogfeld für die **\<Projekt\>\-Eigenschaftenseiten** definiert werden.  Weitere Informationen finden Sie unter [Ändern von Projekteinstellungen für eine Visual Basic\-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) oder [Ändern von Projekteinstellungen für eine C\- oder C\+\+\-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
##  <a name="BKMK_Assert_arguments"></a> Assert\-Argumente  
 Die <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>\- und <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>\-Methoden nehmen bis zu drei Argumente an.  Das erste Argument, das obligatorisch ist, bezieht sich auf die zu überprüfende Bedingung.  Bei einem Aufruf der <xref:System.Diagnostics.Trace.Assert%28System.Boolean%29?displayProperty=fullName>\- oder <xref:System.Diagnostics.Debug.Assert%28System.Boolean%29?displayProperty=fullName>\-Methode mit nur einem Argument wird die Bedingung von der `Assert`\-Methode überprüft. Wenn das Ergebnis "False" lautet, wird der Inhalt der Aufrufliste im **Ausgabefenster** angezeigt.  Im folgenden Beispiel werden die <xref:System.Diagnostics.Trace.Assert%28System.Boolean%29?displayProperty=fullName>\- und <xref:System.Diagnostics.Debug.Assert%28System.Boolean%29?displayProperty=fullName>\-Methoden veranschaulicht:  
  
```vb  
Debug.Assert(stacksize > 0)  
Trace.Assert(stacksize > 0)  
```  
  
```c#  
Debug.Assert ( stacksize > 0 );  
Trace.Assert ( stacksize > 0 );   
```  
  
 Beim zweiten und dritten Argument \(sofern vorhanden\) muss es sich um Zeichenfolgen handeln.  Wenn Sie die <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>\- oder <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>\-Methode mit zwei oder drei Argumenten aufrufen, ist das erste Argument eine Bedingung.  Die Methode überprüft die Bedingung und gibt die als zweites und drittes Argument übergebenen Zeichenfolgen zurück, wenn das Ergebnis "False" lautet.  Im folgenden Beispiel wird die Verwendung der <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%29?displayProperty=fullName>\- und <xref:System.Diagnostics.Trace.Assert%28System.Boolean%2CSystem.String%29?displayProperty=fullName>\-Methoden mit zwei Argumenten veranschaulicht:  
  
```vb  
Debug.Assert(stacksize > 0, "Out of stack space")  
Trace.Assert(stacksize > 0, "Out of stack space")  
```  
  
```c#  
Debug.Assert ( stacksize > 0, "Out of stack space" );  
Trace.Assert ( stacksize > 0, "Out of stack space" );  
```  
  
 Im folgenden Beispiel werden die <xref:System.Diagnostics.Debug.Assert%2A>\- und <xref:System.Diagnostics.Trace.Assert%2A>\-Methoden veranschaulicht:  
  
```vb  
Debug.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))  
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))  
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:", "inctemp failed on third call" )  
```  
  
```c#  
Debug.Assert ( stacksize > 100, "Out of stack space" , "Failed in inctemp" );  
Trace.Assert ( stacksize > 0, "Out of stack space", "Failed in inctemp" );   
```  
  
 [In diesem Thema](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Customizing_Assert_behavior"></a> Anpassen des Assert\-Verhaltens  
 Wenn Sie die Anwendung im Benutzeroberflächenmodus ausführen, wird durch die `Assert`\-Methode das Dialogfeld **Assertionsfehler** angezeigt, falls die Bedingung nicht erfüllt wird.  Die Aktionen, die beim Fehlschlagen einer Assertion auszuführen sind, werden von der <xref:System.Diagnostics.Debug.Listeners%2A>\-Eigenschaft oder der <xref:System.Diagnostics.Trace.Listeners%2A>\-Eigenschaft gesteuert.  
  
 Das Ausgabeverhalten kann wie folgt angepasst werden: durch Hinzufügen eines <xref:System.Diagnostics.TraceListener>\-Objekts zur `Listeners`\-Auflistung, durch Entfernen eines <xref:System.Diagnostics.TraceListener>\-Objekts aus der `Listeners`\-Auflistung oder durch Überschreiben der <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName>\-Methode eines vorhandenen `TraceListener`\-Objekts, um sein Verhalten zu ändern.  
  
 Sie können beispielsweise die <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName>\-Methode überschreiben, um die Ausgabe in ein Ereignisprotokoll zu schreiben, anstatt das Dialogfeld **Assertionsfehler** anzuzeigen.  
  
 Damit die Ausgabe auf diese Weise angepasst werden kann, muss das Programm über einen Listener verfügen, der von <xref:System.Diagnostics.TraceListener> erbt und dessen <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName>\-Methode überschrieben wird.  
  
 Weitere Informationen finden Sie unter [Trace Listeners](../Topic/Trace%20Listeners.md).  
  
 [In diesem Thema](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Setting_assertions_in_configuration_files"></a> Festlegen von Assertionen in Konfigurationsdateien  
 Sie können Assertionen sowohl in der Programmkonfigurationsdatei als auch im Code festlegen.  Weitere Informationen finden Sie unter <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> oder <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.  
  
## Siehe auch  
 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>   
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>   
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Tracing and Instrumenting Applications](../Topic/Tracing%20and%20Instrumenting%20Applications.md)   
 [How to: Compile Conditionally with Trace and Debug](../Topic/How%20to:%20Compile%20Conditionally%20with%20Trace%20and%20Debug.md)   
 [C\#\-, F\#\- und Visual Basic\-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)