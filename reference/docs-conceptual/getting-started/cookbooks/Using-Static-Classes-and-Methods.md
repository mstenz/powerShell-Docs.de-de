---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Verwenden von statischen Klassen und Methoden
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: 0f2b02c3a40365ad0335118b057a4e548c9f6535
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="using-static-classes-and-methods"></a><span data-ttu-id="92287-103">Verwenden von statischen Klassen und Methoden</span><span class="sxs-lookup"><span data-stu-id="92287-103">Using Static Classes and Methods</span></span>
<span data-ttu-id="92287-104">Nicht alle .NET Framework-Klassen können mit **New-Object** erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="92287-104">Not all .NET Framework classes can be created by using **New-Object**.</span></span> <span data-ttu-id="92287-105">Wenn Sie beispielsweise versuchen, ein **System.Environment**- oder ein **System.Math**-Objekt mit **New-Object** zu erstellen, erhalten Sie die folgenden Fehlermeldungen:</span><span class="sxs-lookup"><span data-stu-id="92287-105">For example, if you try to create a **System.Environment** or a **System.Math** object with **New-Object**, you will get the following error messages:</span></span>

```
PS> New-Object System.Environment
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Environment.
At line:1 char:11
+ New-Object  <<<< System.Environment

PS> New-Object System.Math
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Math.
At line:1 char:11
+ New-Object  <<<< System.Math
```

<span data-ttu-id="92287-106">Diese Fehler treten auf, weil es keine Möglichkeit gibt, ein neues Objekt aus diesen Klassen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="92287-106">These errors occur because there is no way to create a new object from these classes.</span></span> <span data-ttu-id="92287-107">Diese Klassen sind Verweisbibliotheken von Methoden und Eigenschaften, deren Status nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="92287-107">These classes are reference libraries of methods and properties that do not change state.</span></span> <span data-ttu-id="92287-108">Sie müssen sie nicht erstellen, Sie verwenden sie einfach.</span><span class="sxs-lookup"><span data-stu-id="92287-108">You don't need to create them, you simply use them.</span></span> <span data-ttu-id="92287-109">Klassen und Methoden wie diese werden als *statische Klassen* bezeichnet, weil sie nicht erstellt, gelöscht oder geändert werden.</span><span class="sxs-lookup"><span data-stu-id="92287-109">Classes and methods such as these are called *static classes* because they are not created, destroyed, or changed.</span></span> <span data-ttu-id="92287-110">Um dies zu verdeutlichen, folgen einige Beispiele, in denen statische Klassen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="92287-110">To make this clear we will provide examples that use static classes.</span></span>

### <a name="getting-environment-data-with-systemenvironment"></a><span data-ttu-id="92287-111">Abrufen von Umgebungsdaten mit „System.Environment“</span><span class="sxs-lookup"><span data-stu-id="92287-111">Getting Environment Data with System.Environment</span></span>
<span data-ttu-id="92287-112">Normalerweise besteht der erste Schritt beim Arbeiten mit einem Objekt in Windows PowerShell darin, über „Get-Member“ zu ermitteln, welche Member das Objekt enthält.</span><span class="sxs-lookup"><span data-stu-id="92287-112">Usually, the first step in working with an object in Windows PowerShell is to use Get-Member to find out what members it contains.</span></span> <span data-ttu-id="92287-113">Bei statischen Klassen ist die Vorgehensweise ein wenig anders, weil die jeweilige tatsächliche Klasse kein Objekt ist.</span><span class="sxs-lookup"><span data-stu-id="92287-113">With static classes, the process is a little different because the actual class is not an object.</span></span>

#### <a name="referring-to-the-static-systemenvironment-class"></a><span data-ttu-id="92287-114">Verweisen auf die statische „System.Environment“-Klasse</span><span class="sxs-lookup"><span data-stu-id="92287-114">Referring to the Static System.Environment Class</span></span>
<span data-ttu-id="92287-115">Sie können auf eine statische Klasse verweisen, indem Sie den Klassennamen in rechteckige Klammern setzen.</span><span class="sxs-lookup"><span data-stu-id="92287-115">You can refer to a static class by surrounding the class name with square brackets.</span></span> <span data-ttu-id="92287-116">Beispielsweise können Sie auf **System.Environment** verweisen, indem Sie den Namen in Klammern eingeben.</span><span class="sxs-lookup"><span data-stu-id="92287-116">For example, you can refer to **System.Environment** by typing the name within brackets.</span></span> <span data-ttu-id="92287-117">Wenn Sie dies tun, werden einige allgemeine Informationen angezeigt:</span><span class="sxs-lookup"><span data-stu-id="92287-117">Doing so displays some generic type information:</span></span>

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> <span data-ttu-id="92287-118">Wie bereits erwähnt wurde, setzt Windows PowerShell automatisch **System.**</span><span class="sxs-lookup"><span data-stu-id="92287-118">As we mentioned previously, Windows PowerShell automatically prepends '**System.**'</span></span> <span data-ttu-id="92287-119">vor die Typnamen, wenn Sie **New-Object** verwenden.</span><span class="sxs-lookup"><span data-stu-id="92287-119">to type names when you use **New-Object**.</span></span> <span data-ttu-id="92287-120">Das gleiche passiert, wenn Sie einen in Klammern stehenden Namen verwenden, d.h., Sie können **\[System.Environment]** als **\[Environment]** angeben.</span><span class="sxs-lookup"><span data-stu-id="92287-120">The same thing happens when using a bracketed type name, so you can specify **\[System.Environment]** as **\[Environment]**.</span></span>

<span data-ttu-id="92287-121">Die **System.Environment**-Klasse enthält allgemeine Informationen über die Arbeitsumgebung des aktuellen Prozesses, der „powershell.exe“ ist, wenn Sie in Windows PowerShell arbeiten.</span><span class="sxs-lookup"><span data-stu-id="92287-121">The **System.Environment** class contains general information about the working environment for the current process, which is powershell.exe when working within Windows PowerShell.</span></span>

<span data-ttu-id="92287-122">Wenn Sie versuchen, die Details dieser Klasse anzuzeigen, indem Sie **\[System.Environment] | Get-Member** eingeben, wird der Objekttyp als **System.RuntimeType**, nicht als **System.Environment** mitgeteilt:</span><span class="sxs-lookup"><span data-stu-id="92287-122">If you try to view details of this class by typing **\[System.Environment] | Get-Member**, the object type is reported as being **System.RuntimeType** , not **System.Environment**:</span></span>

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

<span data-ttu-id="92287-123">Wenn Sie statische Member mit „Get-Member“ anzeigen möchten, geben Sie den **Static**-Parameter an:</span><span class="sxs-lookup"><span data-stu-id="92287-123">To view static members with Get-Member, specify the **Static** parameter:</span></span>

```
PS> [System.Environment] | Get-Member -Static

   TypeName: System.Environment

Name                       MemberType Definition
----                       ---------- ----------
Equals                     Method     static System.Boolean Equals(Object ob...
Exit                       Method     static System.Void Exit(Int32 exitCode)
...
CommandLine                Property   static System.String CommandLine {get;}
CurrentDirectory           Property   static System.String CurrentDirectory ...
ExitCode                   Property   static System.Int32 ExitCode {get;set;}
HasShutdownStarted         Property   static System.Boolean HasShutdownStart...
MachineName                Property   static System.String MachineName {get;}
NewLine                    Property   static System.String NewLine {get;}
OSVersion                  Property   static System.OperatingSystem OSVersio...
ProcessorCount             Property   static System.Int32 ProcessorCount {get;}
StackTrace                 Property   static System.String StackTrace {get;}
SystemDirectory            Property   static System.String SystemDirectory {...
TickCount                  Property   static System.Int32 TickCount {get;}
UserDomainName             Property   static System.String UserDomainName {g...
UserInteractive            Property   static System.Boolean UserInteractive ...
UserName                   Property   static System.String UserName {get;}
Version                    Property   static System.Version Version {get;}
WorkingSet                 Property   static System.Int64 WorkingSet {get;}
TickCount                               ExitCode
```

<span data-ttu-id="92287-124">Nun können Sie anzuzeigende Eigenschaften aus „System.Environment“ auswählen.</span><span class="sxs-lookup"><span data-stu-id="92287-124">We can now select properties to view from System.Environment.</span></span>

#### <a name="displaying-static-properties-of-systemenvironment"></a><span data-ttu-id="92287-125">Anzeigen von statischen Eigenschaften von „System.Environment“</span><span class="sxs-lookup"><span data-stu-id="92287-125">Displaying Static Properties of System.Environment</span></span>

<span data-ttu-id="92287-126">Die Eigenschaften von „System.Environment“ sind ebenfalls statisch und müssen auf andere Weise angegeben werden als normale Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="92287-126">The properties of System.Environment are also static, and must be specified in a different way than normal properties.</span></span> <span data-ttu-id="92287-127">Es wird **::** verwendet, um für Windows PowerShell anzugeben, dass mit einer statischen Methode oder Eigenschaft gearbeitet werden soll.</span><span class="sxs-lookup"><span data-stu-id="92287-127">We use **::** to indicate to Windows PowerShell that we want to work with a static method or property.</span></span> <span data-ttu-id="92287-128">Um den Befehl anzuzeigen, mit dem Windows PowerShell gestartet wurde, wird die **CommandLine**-Eigenschaft geprüft, indem Folgendes eingegeben wird:</span><span class="sxs-lookup"><span data-stu-id="92287-128">To see the command that was used to launch Windows PowerShell, we check the **CommandLine** property by typing:</span></span>

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

<span data-ttu-id="92287-129">Um die Version des Betriebssystems zu überprüfen, zeigen Sie die „OSVersion“-Eigenschaft durch folgende Eingabe an:</span><span class="sxs-lookup"><span data-stu-id="92287-129">To check the operating system version, display the OSVersion property by typing:</span></span>

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

<span data-ttu-id="92287-130">Durch Anzeigen der **HasShutdownStarted**-Eigenschaft können Sie überprüfen, ob der Computer momentan heruntergefahren wird:</span><span class="sxs-lookup"><span data-stu-id="92287-130">We can check whether the computer is in the process of shutting down by displaying the **HasShutdownStarted** property:</span></span>

```
PS> [System.Environment]::HasShutdownStarted
False
```

### <a name="doing-math-with-systemmath"></a><span data-ttu-id="92287-131">Ausführen von mathematischen Funktionen mit „System.Math“</span><span class="sxs-lookup"><span data-stu-id="92287-131">Doing Math with System.Math</span></span>

<span data-ttu-id="92287-132">Mit der statischen „System.Math“-Klasse können einige mathematische Operationen ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="92287-132">The System.Math static class is useful for performing some mathematical operations.</span></span> <span data-ttu-id="92287-133">Die wichtigen Member von **System.Math** sind größtenteils Methoden, die mit **Get-Member** angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="92287-133">The important members of **System.Math** are mostly methods, which we can display by using **Get-Member**.</span></span>

> [!NOTE]
> <span data-ttu-id="92287-134">„System.Math“ hat mehrere Methoden mit demselben Namen, diese werden aber durch die Typen ihrer Parameter unterschieden.</span><span class="sxs-lookup"><span data-stu-id="92287-134">System.Math has several methods with the same name, but they are distinguished by the type of their parameters.</span></span>

<span data-ttu-id="92287-135">Geben Sie den folgenden Befehl aus, um die Methoden der **System.Math**-Klasse aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="92287-135">Type the following command to list the methods of the **System.Math** class.</span></span>

```
PS> [System.Math] | Get-Member -Static -MemberType Methods

   TypeName: System.Math

Name            MemberType Definition
----            ---------- ----------
Abs             Method     static System.Single Abs(Single value), static Sy...
Acos            Method     static System.Double Acos(Double d)
Asin            Method     static System.Double Asin(Double d)
Atan            Method     static System.Double Atan(Double d)
Atan2           Method     static System.Double Atan2(Double y, Double x)
BigMul          Method     static System.Int64 BigMul(Int32 a, Int32 b)
Ceiling         Method     static System.Double Ceiling(Double a), static Sy...
Cos             Method     static System.Double Cos(Double d)
Cosh            Method     static System.Double Cosh(Double value)
DivRem          Method     static System.Int32 DivRem(Int32 a, Int32 b, Int3...
Equals          Method     static System.Boolean Equals(Object objA, Object ...
Exp             Method     static System.Double Exp(Double d)
Floor           Method     static System.Double Floor(Double d), static Syst...
IEEERemainder   Method     static System.Double IEEERemainder(Double x, Doub...
Log             Method     static System.Double Log(Double d), static System...
Log10           Method     static System.Double Log10(Double d)
Max             Method     static System.SByte Max(SByte val1, SByte val2), ...
Min             Method     static System.SByte Min(SByte val1, SByte val2), ...
Pow             Method     static System.Double Pow(Double x, Double y)
ReferenceEquals Method     static System.Boolean ReferenceEquals(Object objA...
Round           Method     static System.Double Round(Double a), static Syst...
Sign            Method     static System.Int32 Sign(SByte value), static Sys...
Sin             Method     static System.Double Sin(Double a)
Sinh            Method     static System.Double Sinh(Double value)
Sqrt            Method     static System.Double Sqrt(Double d)
Tan             Method     static System.Double Tan(Double a)
Tanh            Method     static System.Double Tanh(Double value)
Truncate        Method     static System.Decimal Truncate(Decimal d), static...
```

<span data-ttu-id="92287-136">Dadurch werden verschiedene mathematische Methoden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="92287-136">This displays several mathematical methods.</span></span> <span data-ttu-id="92287-137">Es folgt eine Liste von Befehlen, anhand denen veranschaulicht wird, wie einige der üblichen Methoden funktionieren:</span><span class="sxs-lookup"><span data-stu-id="92287-137">Here is a list of commands that demonstrate how some of the common methods work:</span></span>

```
PS> [System.Math]::Sqrt(9)
3
PS> [System.Math]::Pow(2,3)
8
PS> [System.Math]::Floor(3.3)
3
PS> [System.Math]::Floor(-3.3)
-4
PS> [System.Math]::Ceiling(3.3)
4
PS> [System.Math]::Ceiling(-3.3)
-3
PS> [System.Math]::Max(2,7)
7
PS> [System.Math]::Min(2,7)
2
PS> [System.Math]::Truncate(9.3)
9
PS> [System.Math]::Truncate(-9.3)
-9
```