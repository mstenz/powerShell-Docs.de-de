---
title: Entdecken von Objekten, Eigenschaften und Methoden
description: Sie müssen kein Entwickler sein, um Objekte, Eigenschaften und Methoden zu verstehen und zu verwenden.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 5ab972755afeba0d94bf6c2debaf84ec84cd9244
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438071"
---
# <a name="chapter-3---discovering-objects-properties-and-methods"></a><span data-ttu-id="8d728-103">Kapitel 3: Entdecken von Objekten, Eigenschaften und Methoden</span><span class="sxs-lookup"><span data-stu-id="8d728-103">Chapter 3 - Discovering objects, properties, and methods</span></span>

<span data-ttu-id="8d728-104">Meine erste Begegnung mit Computern war ein Commodore 64, aber mein erster moderner Computer war ein 286 12-MHz-IBM-Klon mit 1 MB Arbeitsspeicher, einer 40 MB-Festplatte und einem 5-1/4-Zoll-Diskettenlaufwerk mit einem CGA-Monitor, der unter Microsoft DOS 3.3 lief.</span><span class="sxs-lookup"><span data-stu-id="8d728-104">My first introduction to computers was a Commodore 64, but my first modern computer was a 286 12-Mhz IBM clone with 1 megabyte of memory, a 40-megabyte hard drive, and one 5-1/4 inch floppy disk drive with a CGA monitor running Microsoft DOS 3.3.</span></span>

<span data-ttu-id="8d728-105">Viele IT-Profis wie ich selbst kennen sich mit der Befehlszeile aus, doch sobald das Thema „Objekte, Eigenschaften und Methoden“ aufkommt, bekommen sie schreckgeweitete, große Augen und sagen: „Ich bin kein Entwickler.“.</span><span class="sxs-lookup"><span data-stu-id="8d728-105">Many IT Pros, like myself, are no stranger to the command line, but when the subject of objects, properties, and methods comes up, they get the deer in the headlights look and say, "I'm not a developer."</span></span> <span data-ttu-id="8d728-106">Aber wissen Sie was?</span><span class="sxs-lookup"><span data-stu-id="8d728-106">Guess what?</span></span> <span data-ttu-id="8d728-107">Sie müssen kein Entwickler sein, um erfolgreich mit PowerShell zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="8d728-107">You don't have to be a developer to be successful with PowerShell.</span></span> <span data-ttu-id="8d728-108">Verzetteln Sie sich nicht bei der Terminologie.</span><span class="sxs-lookup"><span data-stu-id="8d728-108">Don't get bogged down in the terminology.</span></span> <span data-ttu-id="8d728-109">Nicht alles mag anfänglich Sinn ergeben, aber nach ein wenig praktischer Erfahrung werden Sie immer öfter diese „Mir geht ein Licht auf“-Momente erleben.</span><span class="sxs-lookup"><span data-stu-id="8d728-109">Not everything may make sense initially, but after a little hands-on experience you'll start to have those "light bulb" moments.</span></span> <span data-ttu-id="8d728-110">„Aha!</span><span class="sxs-lookup"><span data-stu-id="8d728-110">"Aha!</span></span> <span data-ttu-id="8d728-111">Also das war im Buch gemeint.“</span><span class="sxs-lookup"><span data-stu-id="8d728-111">So that's what the book was talking about."</span></span>

<span data-ttu-id="8d728-112">Stellen Sie sicher, dass Sie die Beispiele auf Ihrem Computer ausprobieren, um praktische Erfahrung zu sammeln.</span><span class="sxs-lookup"><span data-stu-id="8d728-112">Be sure to try the examples on your computer to gain some of that hands-on experience.</span></span>

## <a name="requirements"></a><span data-ttu-id="8d728-113">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="8d728-113">Requirements</span></span>

<span data-ttu-id="8d728-114">Das Active Directory PowerShell-Modul ist für einige der in diesem Kapitel gezeigten Beispiele erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8d728-114">The Active Directory PowerShell module is required by some of the examples shown in this chapter.</span></span>
<span data-ttu-id="8d728-115">Das Modul ist Bestandteil der Remoteserver-Verwaltungstools (Remote Server Administration Tools, RSAT) für Windows.</span><span class="sxs-lookup"><span data-stu-id="8d728-115">The module is part of the Remote Server Administration Tools (RSAT) for Windows.</span></span> <span data-ttu-id="8d728-116">Für den Build 1809 (oder höher) von Windows werden die RSAT-Tools als Windows-Funktion installiert.</span><span class="sxs-lookup"><span data-stu-id="8d728-116">For the 1809 (or higher) build of Windows, the RSAT tools are installed as a Windows feature.</span></span>

- <span data-ttu-id="8d728-117">Informationen zum Installieren der RSAT-Tools finden Sie unter [Windows-Verwaltungsmodule][].</span><span class="sxs-lookup"><span data-stu-id="8d728-117">For information about installing the RSAT tools, see [Windows Management modules][].</span></span>
- <span data-ttu-id="8d728-118">Informationen zu älteren Versionen von Windows finden Sie unter [RSAT für Windows][].</span><span class="sxs-lookup"><span data-stu-id="8d728-118">For older versions of Windows, see [RSAT for Windows][].</span></span>

## <a name="get-member"></a><span data-ttu-id="8d728-119">Get-Member</span><span class="sxs-lookup"><span data-stu-id="8d728-119">Get-Member</span></span>

<span data-ttu-id="8d728-120">`Get-Member` hilft Ihnen herauszufinden, welche Objekte, Eigenschaften und Methoden für Befehle verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="8d728-120">`Get-Member` helps you discover what objects, properties, and methods are available for commands.</span></span>
<span data-ttu-id="8d728-121">Jeder Befehl, der eine objektbasierte Ausgabe erzeugt, kann per Pipeline an `Get-Member` weitergeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="8d728-121">Any command that produces object-based output can be piped to `Get-Member`.</span></span> <span data-ttu-id="8d728-122">Eine Eigenschaft ist ein Merkmal eines Elements.</span><span class="sxs-lookup"><span data-stu-id="8d728-122">A property is a characteristic about an item.</span></span> <span data-ttu-id="8d728-123">Ihr Führerschein besitzt eine Eigenschaft namens „Augenfarbe“, und die häufigsten Werte für diese Eigenschaft sind „Blau“ und „Braun“.</span><span class="sxs-lookup"><span data-stu-id="8d728-123">Your drivers license has a property called eye color and the most common values for that property are blue and brown.</span></span> <span data-ttu-id="8d728-124">Eine Methode ist eine Aktion, die an einem Objekt vorgenommen werden kann.</span><span class="sxs-lookup"><span data-stu-id="8d728-124">A method is an action that can be taken on an item.</span></span> <span data-ttu-id="8d728-125">Um im Führerscheinbeispiel zu bleiben: Eine der Methoden ist „Entziehen“ (Revoke), weil das Straßenverkehrsamt Ihren Führerschein einziehen kann.</span><span class="sxs-lookup"><span data-stu-id="8d728-125">In staying with the drivers license example, one of the methods is "Revoke" because the department of motor vehicles can revoke your drivers license.</span></span>

### <a name="properties"></a><span data-ttu-id="8d728-126">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="8d728-126">Properties</span></span>

<span data-ttu-id="8d728-127">Im folgenden Beispiel rufe ich Informationen zum Windows-Zeitdienst ab, der auf meinem Computer ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8d728-127">In the following example, I'll retrieve information about the Windows Time service running on my computer.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="8d728-128">**Status**, **Name**und **DisplayName** (Anzeigename) sind Beispiele für Eigenschaften, wie im vorherigen Resultset gezeigt.</span><span class="sxs-lookup"><span data-stu-id="8d728-128">**Status**, **Name**, and **DisplayName** are examples of properties as shown in the previous set of results.</span></span> <span data-ttu-id="8d728-129">Der Wert der Eigenschaft **Status** ist `Running`, der Wert der Eigenschaft **Name** ist `w32time`, und der Wert von **DisplayName** ist `Windows Time`.</span><span class="sxs-lookup"><span data-stu-id="8d728-129">The value for the **Status** property is `Running`, the value for the **Name** property is `w32time`, and the value for **DisplayName** is `Windows Time`.</span></span>

<span data-ttu-id="8d728-130">Nun leite ich denselben Befehl per Pipeline an `Get-Member` weiter:</span><span class="sxs-lookup"><span data-stu-id="8d728-130">Now I'll pipe that same command to `Get-Member`:</span></span>

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, Sy...
Close                     Method        void Close()
Continue                  Method        void Continue()
CreateObjRef              Method        System.Runtime.Remoting.ObjRef CreateObjRef(ty...
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.Servi...
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DependentServices         Property      System.ServiceProcess.ServiceController[] Depe...
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle Serv...
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] Serv...
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType ...
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartTy...
Status                    Property      System.ServiceProcess.ServiceControllerStatus ...
ToString                  ScriptMethod  System.Object ToString();
```

<span data-ttu-id="8d728-131">Die erste Zeile der Ergebnisse im vorherigen Beispiel enthält eine sehr wichtige Information.</span><span class="sxs-lookup"><span data-stu-id="8d728-131">The first line of the results in the previous example contains one piece of very important information.</span></span> <span data-ttu-id="8d728-132">**TypeName** gibt an, welcher Objekttyp zurückgegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="8d728-132">**TypeName** tells you what type of object was returned.</span></span> <span data-ttu-id="8d728-133">In diesem Beispiel wurde ein **System.ServiceProcess.ServiceController**-Objekt zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8d728-133">In this example, a **System.ServiceProcess.ServiceController** object was returned.</span></span> <span data-ttu-id="8d728-134">Dies wird häufig als der Teil von **TypeName** direkt hinter dem letzten Punkt abgekürzt, in diesem Beispiel also **ServiceController**.</span><span class="sxs-lookup"><span data-stu-id="8d728-134">This is often abbreviated as the portion of the **TypeName** just after the last period; **ServiceController** in this example.</span></span>

<span data-ttu-id="8d728-135">Sobald Sie wissen, welcher Objekttyp von einem Befehl erzeugt wird, können Sie diese Information verwenden, um Befehle zu identifizieren, die diesen Objekttyp als Eingabe akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="8d728-135">Once you know what type of object a command produces, you can use this information to find commands that accept that type of object as input.</span></span>

```powershell
Get-Command -ParameterType ServiceController
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
```

<span data-ttu-id="8d728-136">Alle diese Befehle verfügen über einen Parameter, der einen **ServiceController**-Objekttyp per Pipeline, Parametereingabe oder über beides akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="8d728-136">All of those commands have a parameter that accepts a **ServiceController** object type by pipeline, parameter input, or both.</span></span>

<span data-ttu-id="8d728-137">Beachten Sie, dass es mehr Eigenschaften gibt, als standardmäßig angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8d728-137">Notice that there are more properties than are displayed by default.</span></span> <span data-ttu-id="8d728-138">Obwohl diese zusätzlichen Eigenschaften standardmäßig nicht angezeigt werden, können Sie in der Pipeline ausgewählt werden, indem Sie den Befehl per Pipeline an das Cmdlet `Select-Object` weiterleiten und den Parameter **Property** verwenden.</span><span class="sxs-lookup"><span data-stu-id="8d728-138">Although these additional properties aren't displayed by default, they can be selected from the pipeline by piping the command to the `Select-Object` cmdlet and using the **Property** parameter.</span></span> <span data-ttu-id="8d728-139">Im folgenden Beispiel werden alle Eigenschaften ausgewählt, indem die Ergebnisse von `Get-Service` per Pipeline an `Select-Object` weitergeleitet werden und das Platzhalterzeichen `*` als Wert für den Parameter **Property** angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8d728-139">The following example selects all of the properties by piping the results of `Get-Service` to `Select-Object` and specifying the `*` wildcard character as the value for the **Property** parameter.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

<span data-ttu-id="8d728-140">Bestimmte Eigenschaften lassen sich auch auswählen, indem an den Parameter **Property** eine durch Trennzeichen getrennte Liste als Wert übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="8d728-140">Specific properties can also be selected using a comma-separated list for the value of the **Property** parameter.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, Name, DisplayName, ServiceType
```

```Output
 Status Name    DisplayName        ServiceType
 ------ ----    -----------        -----------
Running w32time Windows Time Win32ShareProcess
```

<span data-ttu-id="8d728-141">Standardmäßig werden vier Eigenschaften in einer Tabelle zurückgegeben und fünf oder mehr in einer Liste.</span><span class="sxs-lookup"><span data-stu-id="8d728-141">By default, four properties are returned in a table and five or more are returned in a list.</span></span> <span data-ttu-id="8d728-142">Einige Befehle verwenden benutzerdefinierte Formatierung, um außer Kraft zu setzen, wie viele Eigenschaften standardmäßig in einer Tabelle angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8d728-142">Some commands use custom formatting to override how many properties are displayed by default in a table.</span></span>
<span data-ttu-id="8d728-143">Es gibt mehrere `Format-*`-Cmdlets, die verwendet werden können, um diese Standardeinstellungen manuell zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="8d728-143">There are several `Format-*` cmdlets that can be used to manually override these defaults.</span></span> <span data-ttu-id="8d728-144">Die gängigsten sind `Format-Table` und `Format-List`, die beide in einem zukünftigen Kapitel behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="8d728-144">The most common ones are `Format-Table` and `Format-List`, both of which will be covered in an upcoming chapter.</span></span>

<span data-ttu-id="8d728-145">Platzhalterzeichen können beim Angeben der Eigenschaftsnamen mit `Select-Object` verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8d728-145">Wildcard characters can be used when specifying the property names with `Select-Object`.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```powershell
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

<span data-ttu-id="8d728-146">Im vorherigen Beispiel wurde `Can*` als einer der Werte für den Parameter **Property** verwendet, um alle Eigenschaften zurückzugeben, die mit `Can` beginnen.</span><span class="sxs-lookup"><span data-stu-id="8d728-146">In the previous example, `Can*` was used as one of the values for the **Property** parameter to return all the properties that start with `Can`.</span></span> <span data-ttu-id="8d728-147">Hierzu gehören **CanPauseAndContinue**, **CanShutdown** und **CanStop**.</span><span class="sxs-lookup"><span data-stu-id="8d728-147">These include **CanPauseAndContinue**, **CanShutdown**, and **CanStop**.</span></span>

### <a name="methods"></a><span data-ttu-id="8d728-148">Methoden</span><span class="sxs-lookup"><span data-stu-id="8d728-148">Methods</span></span>

<span data-ttu-id="8d728-149">Methoden sind Aktionen, die ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="8d728-149">Methods are an action that can be taken.</span></span> <span data-ttu-id="8d728-150">Verwenden Sie den Parameter **MemberType**, um die Ergebnisse von `Get-Member` so einzugrenzen, dass nur die Methoden für `Get-Service` angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8d728-150">Use the **MemberType** parameter to narrow down the results of `Get-Member` to only show the methods for `Get-Service`.</span></span>

```powershell
Get-Service -Name w32time | Get-Member -MemberType Method
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType Definition
----                      ---------- ----------
Close                     Method     void Close()
Continue                  Method     void Continue()
CreateObjRef              Method     System.Runtime.Remoting.ObjRef CreateObjRef(type ...
Dispose                   Method     void Dispose(), void IDisposable.Dispose()
Equals                    Method     bool Equals(System.Object obj)
ExecuteCommand            Method     void ExecuteCommand(int command)
GetHashCode               Method     int GetHashCode()
GetLifetimeService        Method     System.Object GetLifetimeService()
GetType                   Method     type GetType()
InitializeLifetimeService Method     System.Object InitializeLifetimeService()
Pause                     Method     void Pause()
Refresh                   Method     void Refresh()
Start                     Method     void Start(), void Start(string[] args)
Stop                      Method     void Stop()
WaitForStatus             Method     void WaitForStatus(System.ServiceProcess.ServiceC...
```

<span data-ttu-id="8d728-151">Wie sie sehen können, gibt es zahlreiche Methoden.</span><span class="sxs-lookup"><span data-stu-id="8d728-151">As you can see, there are many methods.</span></span> <span data-ttu-id="8d728-152">Mithilfe der **Stop**-Methode können Sie einen Windows-Dienst beenden.</span><span class="sxs-lookup"><span data-stu-id="8d728-152">The **Stop** method can be used to stop a Windows service.</span></span>

```powershell
(Get-Service -Name w32time).Stop()
```

<span data-ttu-id="8d728-153">Nun überprüfen wir, ob der Windows-Zeitdienst tatsächlich beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="8d728-153">Now to verify the Windows time service has indeed been stopped.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  w32time            Windows Time
```

<span data-ttu-id="8d728-154">Ich selbst verwende diese Methoden selten, aber Sie sollten sie dennoch kennen.</span><span class="sxs-lookup"><span data-stu-id="8d728-154">I rarely find myself using methods, but they're something you need to be aware of.</span></span> <span data-ttu-id="8d728-155">Es kann vorkommen, dass Ihnen ein `Get-*`-Befehl begegnet, ohne dass ein entsprechender Befehl zum Ändern des Elements vorhanden wäre.</span><span class="sxs-lookup"><span data-stu-id="8d728-155">There are times that you'll come across a `Get-*` command without a corresponding command to modify that item.</span></span>
<span data-ttu-id="8d728-156">Häufig kann dann eine Methode verwendet werden, um eine Aktion auszuführen, mit der das Element geändert wird.</span><span class="sxs-lookup"><span data-stu-id="8d728-156">Often, a method can be used to perform an action that modifies it.</span></span> <span data-ttu-id="8d728-157">Das Cmdlet `Get-SqlAgentJob` im SqlServer PowerShell-Modul ist ein gutes Beispiel dafür.</span><span class="sxs-lookup"><span data-stu-id="8d728-157">The `Get-SqlAgentJob` cmdlet in the SqlServer PowerShell module is a good example of this.</span></span> <span data-ttu-id="8d728-158">Das Modul wird als Bestandteil von [SQL Server Management Studio (SSMS)][SMSS] installiert.</span><span class="sxs-lookup"><span data-stu-id="8d728-158">The module installs as part of [SQL Server Management Studio (SMSS)][SMSS].</span></span> <span data-ttu-id="8d728-159">Es gibt kein entsprechendes `Set-*`-Cmdlet, aber dieselbe Aufgabe kann mit einer Methode erledigt werden.</span><span class="sxs-lookup"><span data-stu-id="8d728-159">No corresponding `Set-*` cmdlet exists, but a method can be used to complete the same task.</span></span>

<span data-ttu-id="8d728-160">Ein weiterer Grund, Methoden zu kennen, besteht darin, dass viele Einsteiger davon ausgehen, dass mit `Get-*`-Befehlen keine destruktiven Änderungen möglich sind.</span><span class="sxs-lookup"><span data-stu-id="8d728-160">Another reason to be aware of methods is that many beginners assume destructive changes can't be made with `Get-*` commands.</span></span> <span data-ttu-id="8d728-161">Allerdings können sie schwerwiegende Probleme verursachen, wenn Sie nicht ordnungsgemäß verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8d728-161">But they indeed can cause serious problems if used inappropriately.</span></span>

<span data-ttu-id="8d728-162">Eine bessere Option ist es, ein Cmdlet zu verwenden, um die Aktion auszuführen, wenn eins vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="8d728-162">A better option is to use a cmdlet to perform the action if one exists.</span></span> <span data-ttu-id="8d728-163">Fahren Sie fort, und starten Sie den Windows-Zeitdienst, nur diesmal mit dem Unterschied, dass Sie das Cmdlet zum Starten von Diensten verwenden.</span><span class="sxs-lookup"><span data-stu-id="8d728-163">Go ahead and start the Windows Time service, except this time use the cmdlet for starting services.</span></span>

```powershell
Get-Service -Name w32time | Start-Service -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="8d728-164">Standardmäßig gibt `Start-Service` keine Ergebnisse zurück, genau wie die Start-Methode von `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="8d728-164">By default, `Start-Service` doesn't return any results just like the start method of `Get-Service`.</span></span>
<span data-ttu-id="8d728-165">Einer der Vorteile bei der Verwendung eines Cmdlets ist jedoch, dass das Cmdlet oft zusätzliche Funktionen bietet, die mit einer Methode nicht verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="8d728-165">But one of the benefits of using a cmdlet is that many times the cmdlet offers additional functionality that isn't available with a method.</span></span> <span data-ttu-id="8d728-166">Im vorherigen Beispiel wurde der Parameter **PassThru** verwendet.</span><span class="sxs-lookup"><span data-stu-id="8d728-166">In the previous example, the **PassThru** parameter was used.</span></span> <span data-ttu-id="8d728-167">Dieser bewirkt, dass ein Cmdlet, das normalerweise keine Ausgabe erzeugt, Ausgaben erzeugt.</span><span class="sxs-lookup"><span data-stu-id="8d728-167">This causes a cmdlet that doesn't normally produce output, to produce output.</span></span>

<span data-ttu-id="8d728-168">Seien Sie immer vorsichtig mit Annahmen zur Ausgabe eines Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="8d728-168">Be careful with assumptions about the output of a cmdlet.</span></span> <span data-ttu-id="8d728-169">Wir alle wissen, was passiert, wenn man etwas voraussetzt.</span><span class="sxs-lookup"><span data-stu-id="8d728-169">We all know what happens when you assume things.</span></span> <span data-ttu-id="8d728-170">Ich rufe nun Informationen über den PowerShell-Prozess, der auf meinem Computer in der Windows 10-Laborumgebung ausgeführt wird, ab.</span><span class="sxs-lookup"><span data-stu-id="8d728-170">I'll retrieve information about the PowerShell process running on my Windows 10 lab environment computer.</span></span>

```powershell
Get-Process -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    922      48   107984     140552       2.84   9020   1 powershell

```

<span data-ttu-id="8d728-171">Nun leite ich denselben Befehl per Pipeline an „Get-Member“ weiter:</span><span class="sxs-lookup"><span data-stu-id="8d728-171">Now I'll pipe that same command to Get-Member:</span></span>

```powershell
Get-Process -Name PowerShell | Get-Member
```

```Output
   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
NPM                        AliasProperty  NPM = NonpagedSystemMemorySize64
PM                         AliasProperty  PM = PagedMemorySize64
SI                         AliasProperty  SI = SessionId
VM                         AliasProperty  VM = VirtualMemorySize64
WS                         AliasProperty  WS = WorkingSet64
Disposed                   Event          System.EventHandler Disposed(System.Object, ...
ErrorDataReceived          Event          System.Diagnostics.DataReceivedEventHandler ...
Exited                     Event          System.EventHandler Exited(System.Object, Sy...
OutputDataReceived         Event          System.Diagnostics.DataReceivedEventHandler ...
BeginErrorReadLine         Method         void BeginErrorReadLine()
BeginOutputReadLine        Method         void BeginOutputReadLine()
CancelErrorRead            Method         void CancelErrorRead()
CancelOutputRead           Method         void CancelOutputRead()
Close                      Method         void Close()
CloseMainWindow            Method         bool CloseMainWindow()
CreateObjRef               Method         System.Runtime.Remoting.ObjRef CreateObjRef(...
Dispose                    Method         void Dispose(), void IDisposable.Dispose()
Equals                     Method         bool Equals(System.Object obj)
GetHashCode                Method         int GetHashCode()
GetLifetimeService         Method         System.Object GetLifetimeService()
GetType                    Method         type GetType()
InitializeLifetimeService  Method         System.Object InitializeLifetimeService()
Kill                       Method         void Kill()
Refresh                    Method         void Refresh()
Start                      Method         bool Start()
ToString                   Method         string ToString()
WaitForExit                Method         bool WaitForExit(int milliseconds), void Wai...
WaitForInputIdle           Method         bool WaitForInputIdle(int milliseconds), boo...
__NounName                 NoteProperty   string __NounName=Process
BasePriority               Property       int BasePriority {get;}
Container                  Property       System.ComponentModel.IContainer Container {...
EnableRaisingEvents        Property       bool EnableRaisingEvents {get;set;}
ExitCode                   Property       int ExitCode {get;}
ExitTime                   Property       datetime ExitTime {get;}
Handle                     Property       System.IntPtr Handle {get;}
HandleCount                Property       int HandleCount {get;}
HasExited                  Property       bool HasExited {get;}
Id                         Property       int Id {get;}
MachineName                Property       string MachineName {get;}
MainModule                 Property       System.Diagnostics.ProcessModule MainModule ...
MainWindowHandle           Property       System.IntPtr MainWindowHandle {get;}
MainWindowTitle            Property       string MainWindowTitle {get;}
MaxWorkingSet              Property       System.IntPtr MaxWorkingSet {get;set;}
MinWorkingSet              Property       System.IntPtr MinWorkingSet {get;set;}
Modules                    Property       System.Diagnostics.ProcessModuleCollection M...
NonpagedSystemMemorySize   Property       int NonpagedSystemMemorySize {get;}
NonpagedSystemMemorySize64 Property       long NonpagedSystemMemorySize64 {get;}
PagedMemorySize            Property       int PagedMemorySize {get;}
PagedMemorySize64          Property       long PagedMemorySize64 {get;}
PagedSystemMemorySize      Property       int PagedSystemMemorySize {get;}
PagedSystemMemorySize64    Property       long PagedSystemMemorySize64 {get;}
PeakPagedMemorySize        Property       int PeakPagedMemorySize {get;}
PeakPagedMemorySize64      Property       long PeakPagedMemorySize64 {get;}
PeakVirtualMemorySize      Property       int PeakVirtualMemorySize {get;}
PeakVirtualMemorySize64    Property       long PeakVirtualMemorySize64 {get;}
PeakWorkingSet             Property       int PeakWorkingSet {get;}
PeakWorkingSet64           Property       long PeakWorkingSet64 {get;}
PriorityBoostEnabled       Property       bool PriorityBoostEnabled {get;set;}
PriorityClass              Property       System.Diagnostics.ProcessPriorityClass Prio...
PrivateMemorySize          Property       int PrivateMemorySize {get;}
PrivateMemorySize64        Property       long PrivateMemorySize64 {get;}
PrivilegedProcessorTime    Property       timespan PrivilegedProcessorTime {get;}
ProcessName                Property       string ProcessName {get;}
ProcessorAffinity          Property       System.IntPtr ProcessorAffinity {get;set;}
Responding                 Property       bool Responding {get;}
SafeHandle                 Property       Microsoft.Win32.SafeHandles.SafeProcessHandl...
SessionId                  Property       int SessionId {get;}
Site                       Property       System.ComponentModel.ISite Site {get;set;}
StandardError              Property       System.IO.StreamReader StandardError {get;}
StandardInput              Property       System.IO.StreamWriter StandardInput {get;}
StandardOutput             Property       System.IO.StreamReader StandardOutput {get;}
StartInfo                  Property       System.Diagnostics.ProcessStartInfo StartInf...
StartTime                  Property       datetime StartTime {get;}
SynchronizingObject        Property       System.ComponentModel.ISynchronizeInvoke Syn...
Threads                    Property       System.Diagnostics.ProcessThreadCollection T...
TotalProcessorTime         Property       timespan TotalProcessorTime {get;}
UserProcessorTime          Property       timespan UserProcessorTime {get;}
VirtualMemorySize          Property       int VirtualMemorySize {get;}
VirtualMemorySize64        Property       long VirtualMemorySize64 {get;}
WorkingSet                 Property       int WorkingSet {get;}
WorkingSet64               Property       long WorkingSet64 {get;}
PSConfiguration            PropertySet    PSConfiguration {Name, Id, PriorityClass, Fi...
PSResources                PropertySet    PSResources {Name, Id, Handlecount, WorkingS...
Company                    ScriptProperty System.Object Company {get=$this.Mainmodule....
CPU                        ScriptProperty System.Object CPU {get=$this.TotalProcessorT...
Description                ScriptProperty System.Object Description {get=$this.Mainmod...
FileVersion                ScriptProperty System.Object FileVersion {get=$this.Mainmod...
Path                       ScriptProperty System.Object Path {get=$this.Mainmodule.Fil...
Product                    ScriptProperty System.Object Product {get=$this.Mainmodule....
ProductVersion             ScriptProperty System.Object ProductVersion {get=$this.Main...
```

<span data-ttu-id="8d728-172">Beachten Sie, dass mehr Eigenschaften aufgelistet werden, als standardmäßig angezeigt würden.</span><span class="sxs-lookup"><span data-stu-id="8d728-172">Notice that there are more properties listed than are displayed by default.</span></span> <span data-ttu-id="8d728-173">Eine Reihe der angezeigten Standardeigenschaften wird nicht als Eigenschaften angezeigt, wenn die Ergebnisse von `Get-Member` angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8d728-173">A number of the default properties displayed don't show up as properties when viewing the results of `Get-Member`.</span></span> <span data-ttu-id="8d728-174">Dies liegt daran, dass viele der angezeigten Werte, z. B. `NPM(K)`, `PM(K)`, `WS(K)` und `CPU(s)` berechnete Eigenschaften sind.</span><span class="sxs-lookup"><span data-stu-id="8d728-174">This is because many of the displayed values, such as `NPM(K)`, `PM(K)`, `WS(K)`, and `CPU(s)`, are calculated properties.</span></span> <span data-ttu-id="8d728-175">Um die tatsächlichen Eigenschaftsnamen zu bestimmen, muss der Befehl per Pipeline an `Get-Member` weitergeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="8d728-175">To determine the actual property names, the command must be piped to `Get-Member`.</span></span>

<span data-ttu-id="8d728-176">Wenn ein Befehl keine Ausgabe erzeugt, kann er nicht per Pipeline an `Get-Member` weitergeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="8d728-176">If a command does not produce output, it can't be piped to `Get-Member`.</span></span> <span data-ttu-id="8d728-177">Da `Start-Service` standardmäßig keine Ausgabe erzeugt, wird ein Fehler generiert, wenn Sie versuchen, ihn per Pipeline an `Get-Member` weiterzuleiten.</span><span class="sxs-lookup"><span data-stu-id="8d728-177">Since `Start-Service` doesn't produce any output by default, it generates an error when you try to pipe it to `Get-Member`.</span></span>

```powershell
Start-Service -Name w32time | Get-Member
```

```Output
Get-Member : You must specify an object for the Get-Member cmdlet.
At line:1 char:31
+ Start-Service -Name w32time | Get-Member
+
    + CategoryInfo          : CloseError: (:) [Get-Member], InvalidOperationException
    + FullyQualifiedErrorId : NoObjectInGetMember,Microsoft.PowerShell.Commands.GetMembe
   rCommand
```

<span data-ttu-id="8d728-178">Der Parameter **PassThru** kann mit dem Cmdlet `Start-Service` angegeben werden, damit eine Ausgabe erzeugt wird, die dann ohne einen Fehler per Pipeline an `Get-Member` weitergeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="8d728-178">The **PassThru** parameter can be specified with the `Start-Service` cmdlet make it produce output, which is then piped to `Get-Member` without error.</span></span>

```powershell
Start-Service -Name w32time -PassThru | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, Sy...
Close                     Method        void Close()
Continue                  Method        void Continue()
CreateObjRef              Method        System.Runtime.Remoting.ObjRef CreateObjRef(ty...
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.Servi...
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DependentServices         Property      System.ServiceProcess.ServiceController[] Depe...
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle Serv...
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] Serv...
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType ...
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartTy...
Status                    Property      System.ServiceProcess.ServiceControllerStatus ...
ToString                  ScriptMethod  System.Object ToString();
```

<span data-ttu-id="8d728-179">Damit ein Befehl per Pipeline an `Get-Member` weitergeleitet werden kann, muss er eine objektbasierte Ausgabe erzeugen.</span><span class="sxs-lookup"><span data-stu-id="8d728-179">To be piped to `Get-Member`, a command must produce object-based output.</span></span>

```powershell
Get-Service -Name w32time | Out-Host | Get-Member
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time

Get-Member : You must specify an object for the Get-Member cmdlet.
At line:1 char:40
+ Get-Service -Name w32time | Out-Host | Get-Member
+
    + CategoryInfo          : CloseError: (:) [Get-Member], InvalidOperationException
    + FullyQualifiedErrorId : NoObjectInGetMember,Microsoft.PowerShell.Commands.GetMemberCommand
```

<span data-ttu-id="8d728-180">`Out-Host` schreibt direkt in den PowerShell-Host, aber es erzeugt keine objektbasierte Ausgabe für die Pipeline.</span><span class="sxs-lookup"><span data-stu-id="8d728-180">`Out-Host` writes directly to the PowerShell host, but it doesn't produce object-based output for the pipeline.</span></span> <span data-ttu-id="8d728-181">Somit kann es nicht per Pipeline an `Get-Member` weitergeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="8d728-181">So it can't be piped to `Get-Member`.</span></span>

## <a name="active-directory"></a><span data-ttu-id="8d728-182">Active Directory</span><span class="sxs-lookup"><span data-stu-id="8d728-182">Active Directory</span></span>

> [!NOTE]
> <span data-ttu-id="8d728-183">Die im Abschnitt „Anforderungen“ dieses Kapitels aufgeführten Remoteserver-Verwaltungstools, sind erforderlich, um diesen Abschnitt abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="8d728-183">The Remote Server Administration Tools listed in the requirements section of this chapter are required to complete this section.</span></span> <span data-ttu-id="8d728-184">Außerdem, wie in der Einführung dieses Buchs erwähnt, muss Ihr Computer in der Windows 10-Laborumgebung Mitglied der Domäne der Laborumgebung sein.</span><span class="sxs-lookup"><span data-stu-id="8d728-184">Also, as mentioned in the introduction to this book, your Windows 10 lab environment computer must be a member of the lab environment domain.</span></span>

<span data-ttu-id="8d728-185">Verwenden Sie `Get-Command` mit dem Parameter **Module**, um zu bestimmen, welche Befehle als Teil des ActiveDirectory PowerShell-Moduls bei der Installation der Remoteserver-Verwaltungstools hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="8d728-185">Use `Get-Command` with the **Module** parameter to determine what commands were added as part of the ActiveDirectory PowerShell module when the remote server administration tools were installed.</span></span>

```powershell
Get-Command -Module ActiveDirectory
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Add-ADCentralAccessPolicyMember                    1.0.0.0    ActiveDi...
Cmdlet          Add-ADComputerServiceAccount                       1.0.0.0    ActiveDi...
Cmdlet          Add-ADDomainControllerPasswordReplicationPolicy    1.0.0.0    ActiveDi...
Cmdlet          Add-ADFineGrainedPasswordPolicySubject             1.0.0.0    ActiveDi...
Cmdlet          Add-ADGroupMember                                  1.0.0.0    ActiveDi...
Cmdlet          Add-ADPrincipalGroupMembership                     1.0.0.0    ActiveDi...
Cmdlet          Add-ADResourcePropertyListMember                   1.0.0.0    ActiveDi...
Cmdlet          Clear-ADAccountExpiration                          1.0.0.0    ActiveDi...
Cmdlet          Clear-ADClaimTransformLink                         1.0.0.0    ActiveDi...
Cmdlet          Disable-ADAccount                                  1.0.0.0    ActiveDi...
...
```

<span data-ttu-id="8d728-186">Insgesamt wurden 147 Befehle als Teil des ActiveDirectory PowerShell-Moduls hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8d728-186">A total of 147 commands were added as part of the ActiveDirectory PowerShell module.</span></span> <span data-ttu-id="8d728-187">Einige von diesen Befehlen geben standardmäßig nur einen Teil der verfügbaren Eigenschaften zurück.</span><span class="sxs-lookup"><span data-stu-id="8d728-187">Some commands of these commands only return a portion of the available properties by default.</span></span>

<span data-ttu-id="8d728-188">Haben Sie einen Unterschied bei den Namen der Befehle in diesem Modul bemerkt?</span><span class="sxs-lookup"><span data-stu-id="8d728-188">Did you notice anything different about the names of the commands in this module?</span></span> <span data-ttu-id="8d728-189">Der Nomen-Teil der Befehle besitzt ein AD-Präfix.</span><span class="sxs-lookup"><span data-stu-id="8d728-189">The noun portion of the commands has an AD prefix.</span></span> <span data-ttu-id="8d728-190">Dies finden Sie häufig bei den Befehlen der meisten Module.</span><span class="sxs-lookup"><span data-stu-id="8d728-190">This is common to see on the commands of most modules.</span></span> <span data-ttu-id="8d728-191">Das Präfix dient der Vermeidung von Benennungskonflikten.</span><span class="sxs-lookup"><span data-stu-id="8d728-191">The prefix is designed to help prevent naming conflicts.</span></span>

```powershell
Get-ADUser -Identity mike | Get-Member
```

```Output
   TypeName: Microsoft.ActiveDirectory.Management.ADUser

Name              MemberType            Definition
----              ----------            ----------
Contains          Method                bool Contains(string propertyName)
Equals            Method                bool Equals(System.Object obj)
GetEnumerator     Method                System.Collections.IDictionaryEnumerator GetEn...
GetHashCode       Method                int GetHashCode()
GetType           Method                type GetType()
ToString          Method                string ToString()
Item              ParameterizedProperty Microsoft.ActiveDirectory.Management.ADPropert...
DistinguishedName Property              System.String DistinguishedName {get;set;}
Enabled           Property              System.Boolean Enabled {get;set;}
GivenName         Property              System.String GivenName {get;set;}
Name              Property              System.String Name {get;}
ObjectClass       Property              System.String ObjectClass {get;set;}
ObjectGUID        Property              System.Nullable`1[[System.Guid, mscorlib, Vers...
SamAccountName    Property              System.String SamAccountName {get;set;}
SID               Property              System.Security.Principal.SecurityIdentifier S...
Surname           Property              System.String Surname {get;set;}
UserPrincipalName Property              System.String UserPrincipalName {get;set;}
```

<span data-ttu-id="8d728-192">Selbst wenn Sie nur entfernt mit Active Directory vertraut sind, wissen Sie wahrscheinlich, dass ein Benutzerkonto über mehr Eigenschaften verfügt, als in diesem Beispiel gezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8d728-192">Even if you're only vaguely familiar with Active Directory, you're probably aware that a user account has more properties than are shown in this example.</span></span>

<span data-ttu-id="8d728-193">Das Cmdlet `Get-ADUser` verfügt über einen Parameter **Properties**, der verwendet wird, um die zusätzlichen (nicht standardmäßigen) Eigenschaften anzugeben, die Sie zurückgegeben haben möchten.</span><span class="sxs-lookup"><span data-stu-id="8d728-193">The `Get-ADUser` cmdlet has a **Properties** parameter that is used to specify the additional (non-default) properties you want to return.</span></span> <span data-ttu-id="8d728-194">Wenn Sie das Platzhalterzeichen `*` angeben, werden alle zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8d728-194">Specifying the `*` wildcard character returns all of them.</span></span>

```powershell
Get-ADUser -Identity mike -Properties * | Get-Member
```

```Output
   TypeName: Microsoft.ActiveDirectory.Management.ADUser

Name                                 MemberType            Definition
----                                 ----------            ----------
Contains                             Method                bool Contains(string proper...
Equals                               Method                bool Equals(System.Object obj)
GetEnumerator                        Method                System.Collections.IDiction...
GetHashCode                          Method                int GetHashCode()
GetType                              Method                type GetType()
ToString                             Method                string ToString()
Item                                 ParameterizedProperty Microsoft.ActiveDirectory.M...
AccountExpirationDate                Property              System.DateTime AccountExpi...
accountExpires                       Property              System.Int64 accountExpires...
AccountLockoutTime                   Property              System.DateTime AccountLock...
AccountNotDelegated                  Property              System.Boolean AccountNotDe...
AllowReversiblePasswordEncryption    Property              System.Boolean AllowReversi...
AuthenticationPolicy                 Property              Microsoft.ActiveDirectory.M...
AuthenticationPolicySilo             Property              Microsoft.ActiveDirectory.M...
BadLogonCount                        Property              System.Int32 BadLogonCount ...
badPasswordTime                      Property              System.Int64 badPasswordTim...
badPwdCount                          Property              System.Int32 badPwdCount {g...
CannotChangePassword                 Property              System.Boolean CannotChange...
CanonicalName                        Property              System.String CanonicalName...
Certificates                         Property              Microsoft.ActiveDirectory.M...
City                                 Property              System.String City {get;set;}
CN                                   Property              System.String CN {get;}
codePage                             Property              System.Int32 codePage {get;...
Company                              Property              System.String Company {get;...
CompoundIdentitySupported            Property              Microsoft.ActiveDirectory.M...
Country                              Property              System.String Country {get;...
countryCode                          Property              System.Int32 countryCode {g...
Created                              Property              System.DateTime Created {get;}
createTimeStamp                      Property              System.DateTime createTimeS...
Deleted                              Property              System.Boolean Deleted {get;}
Department                           Property              System.String Department {g...
Description                          Property              System.String Description {...
DisplayName                          Property              System.String DisplayName {...
DistinguishedName                    Property              System.String Distinguished...
Division                             Property              System.String Division {get...
DoesNotRequirePreAuth                Property              System.Boolean DoesNotRequi...
dSCorePropagationData                Property              Microsoft.ActiveDirectory.M...
EmailAddress                         Property              System.String EmailAddress ...
EmployeeID                           Property              System.String EmployeeID {g...
EmployeeNumber                       Property              System.String EmployeeNumbe...
Enabled                              Property              System.Boolean Enabled {get...
Fax                                  Property              System.String Fax {get;set;}
GivenName                            Property              System.String GivenName {ge...
HomeDirectory                        Property              System.String HomeDirectory...
HomedirRequired                      Property              System.Boolean HomedirRequi...
HomeDrive                            Property              System.String HomeDrive {ge...
HomePage                             Property              System.String HomePage {get...
HomePhone                            Property              System.String HomePhone {ge...
Initials                             Property              System.String Initials {get...
instanceType                         Property              System.Int32 instanceType {...
isDeleted                            Property              System.Boolean isDeleted {g...
KerberosEncryptionType               Property              Microsoft.ActiveDirectory.M...
LastBadPasswordAttempt               Property              System.DateTime LastBadPass...
LastKnownParent                      Property              System.String LastKnownPare...
lastLogoff                           Property              System.Int64 lastLogoff {ge...
lastLogon                            Property              System.Int64 lastLogon {get...
LastLogonDate                        Property              System.DateTime LastLogonDa...
lastLogonTimestamp                   Property              System.Int64 lastLogonTimes...
LockedOut                            Property              System.Boolean LockedOut {g...
logonCount                           Property              System.Int32 logonCount {ge...
LogonWorkstations                    Property              System.String LogonWorkstat...
Manager                              Property              System.String Manager {get;...
MemberOf                             Property              Microsoft.ActiveDirectory.M...
MNSLogonAccount                      Property              System.Boolean MNSLogonAcco...
MobilePhone                          Property              System.String MobilePhone {...
Modified                             Property              System.DateTime Modified {g...
modifyTimeStamp                      Property              System.DateTime modifyTimeS...
msDS-User-Account-Control-Computed   Property              System.Int32 msDS-User-Acco...
Name                                 Property              System.String Name {get;}
nTSecurityDescriptor                 Property              System.DirectoryServices.Ac...
ObjectCategory                       Property              System.String ObjectCategor...
ObjectClass                          Property              System.String ObjectClass {...
ObjectGUID                           Property              System.Nullable`1[[System.G...
objectSid                            Property              System.Security.Principal.S...
Office                               Property              System.String Office {get;s...
OfficePhone                          Property              System.String OfficePhone {...
Organization                         Property              System.String Organization ...
OtherName                            Property              System.String OtherName {ge...
PasswordExpired                      Property              System.Boolean PasswordExpi...
PasswordLastSet                      Property              System.DateTime PasswordLas...
PasswordNeverExpires                 Property              System.Boolean PasswordNeve...
PasswordNotRequired                  Property              System.Boolean PasswordNotR...
POBox                                Property              System.String POBox {get;set;}
PostalCode                           Property              System.String PostalCode {g...
PrimaryGroup                         Property              System.String PrimaryGroup ...
primaryGroupID                       Property              System.Int32 primaryGroupID...
PrincipalsAllowedToDelegateToAccount Property              Microsoft.ActiveDirectory.M...
ProfilePath                          Property              System.String ProfilePath {...
ProtectedFromAccidentalDeletion      Property              System.Boolean ProtectedFro...
pwdAnswer                            Property              System.String pwdAnswer {ge...
pwdLastSet                           Property              System.Int64 pwdLastSet {ge...
pwdQuestion                          Property              System.String pwdQuestion {...
SamAccountName                       Property              System.String SamAccountNam...
sAMAccountType                       Property              System.Int32 sAMAccountType...
ScriptPath                           Property              System.String ScriptPath {g...
sDRightsEffective                    Property              System.Int32 sDRightsEffect...
ServicePrincipalNames                Property              Microsoft.ActiveDirectory.M...
SID                                  Property              System.Security.Principal.S...
SIDHistory                           Property              Microsoft.ActiveDirectory.M...
SmartcardLogonRequired               Property              System.Boolean SmartcardLog...
sn                                   Property              System.String sn {get;set;}
State                                Property              System.String State {get;set;}
StreetAddress                        Property              System.String StreetAddress...
Surname                              Property              System.String Surname {get;...
Title                                Property              System.String Title {get;set;}
TrustedForDelegation                 Property              System.Boolean TrustedForDe...
TrustedToAuthForDelegation           Property              System.Boolean TrustedToAut...
UseDESKeyOnly                        Property              System.Boolean UseDESKeyOnl...
userAccountControl                   Property              System.Int32 userAccountCon...
userCertificate                      Property              Microsoft.ActiveDirectory.M...
UserPrincipalName                    Property              System.String UserPrincipal...
uSNChanged                           Property              System.Int64 uSNChanged {get;}
uSNCreated                           Property              System.Int64 uSNCreated {get;}
whenChanged                          Property              System.DateTime whenChanged...
whenCreated                          Property              System.DateTime whenCreated...
```

<span data-ttu-id="8d728-195">Jetzt sieht es schon eher so aus.</span><span class="sxs-lookup"><span data-stu-id="8d728-195">Now that looks more like it.</span></span>

<span data-ttu-id="8d728-196">Können Sie sich einen Grund vorstellen, warum die Eigenschaften eines Active Directory-Benutzerkontos standardmäßig so eingeschränkt sein sollten?</span><span class="sxs-lookup"><span data-stu-id="8d728-196">Can you think of a reason why the properties of an Active Directory user account would be so limited by default?</span></span> <span data-ttu-id="8d728-197">Stellen Sie sich vor, wenn Sie jede Eigenschaft für jedes Benutzerkonto in Ihrer Active Directory-Produktionsumgebung zurückgäben.</span><span class="sxs-lookup"><span data-stu-id="8d728-197">Imagine if you returned every property for every user account in your production Active Directory environment.</span></span> <span data-ttu-id="8d728-198">Stellen Sie sich die Leistungsbeeinträchtigung vor, die Sie verursachen könnten, nicht nur bei den Domänencontrollern selbst, sondern auch in Ihrem Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="8d728-198">Think of the performance degradation that you could cause, not only to the domain controllers themselves, but also to your network.</span></span> <span data-ttu-id="8d728-199">Es ist außerdem zweifelhaft, ob Sie tatsächlich jede Eigenschaft benötigen.</span><span class="sxs-lookup"><span data-stu-id="8d728-199">It's doubtful that you'll actually need every property anyway.</span></span> <span data-ttu-id="8d728-200">Das Zurückgeben aller Eigenschaften für ein einzelnes Benutzerkonto ist absolut akzeptabel, wenn Sie feststellen möchten, welche Eigenschaften vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="8d728-200">Returning all of the properties for a single user account is perfectly acceptable when you're trying to determine what properties exist.</span></span>

<span data-ttu-id="8d728-201">Es ist nicht ungewöhnlich, einen Befehl bei der Prototypenerstellung mehrmals auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8d728-201">It's not uncommon to run a command many times when prototyping it.</span></span> <span data-ttu-id="8d728-202">Wenn Sie eine sehr große Abfrage ausführen möchten, fragen Sie sie einmal ab, und speichern Sie die Ergebnisse in einer Variablen.</span><span class="sxs-lookup"><span data-stu-id="8d728-202">If you're going to perform some huge query, query it once and store the results in a variable.</span></span> <span data-ttu-id="8d728-203">Arbeiten Sie dann mit dem Inhalt der Variablen, anstatt wiederholt eine aufwändige Abfrage zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="8d728-203">Then work with the contents of the variable instead of repeatedly using some expensive query.</span></span>

```powershell
$Users = Get-ADUser -Identity mike -Properties *
```

<span data-ttu-id="8d728-204">Verwenden Sie den Inhalt der Variablen `$Users`, anstatt den vorherigen Befehl mehrmals auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8d728-204">Use the contents of the `$Users` variable instead of running the previous command numerous times.</span></span>
<span data-ttu-id="8d728-205">Denken Sie daran, dass der Inhalt der Variablen nicht aktualisiert wird, wenn Änderungen an diesem Benutzer in Active Directory vorgenommen werden.</span><span class="sxs-lookup"><span data-stu-id="8d728-205">Keep in mind that the contents of the variable aren't updated when changes are made to that user in Active Directory.</span></span>

<span data-ttu-id="8d728-206">Sie könnten die Variable `$Users` per Pipeline an `Get-Member` weiterleiten, um die verfügbaren Eigenschaften zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="8d728-206">You could pipe the `$Users` variable to `Get-Member` to discover the available properties.</span></span>

```powershell
$Users | Get-Member
```

<span data-ttu-id="8d728-207">Wählen Sie dann die einzelnen Eigenschaften aus, indem Sie `$Users` per Pipeline an `Select-Object` weiterleiten, ohne dabei Active Directory jemals mehr als einmal abfragen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="8d728-207">Then select the individual properties by piping `$Users` to `Select-Object`, all without ever having to query Active Directory more than one time.</span></span>

```powershell
$Users | Select-Object -Property Name, LastLogonDate, LastBadPasswordAttempt
```

<span data-ttu-id="8d728-208">Wenn Sie Active Directory mehr als einmal Abfragen möchten, verwenden Sie den Parameter **Properties**, um alle nicht standardmäßigen Eigenschaften anzugeben, die Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="8d728-208">If you are going to query Active Directory more than once, use the **Properties** parameter to specify any non-default properties you want.</span></span>

```powershell
Get-ADUser -Identity mike -Properties LastLogonDate, LastBadPasswordAttempt
```

```Output
DistinguishedName      : CN=Mike F. Robbins,OU=Sales,DC=mikefrobbins,DC=com
Enabled                : True
GivenName              : Mike
LastBadPasswordAttempt : 2/4/2017 10:46:15 AM
LastLogonDate          : 2/18/2017 12:45:14 AM
Name                   : Mike F. Robbins
ObjectClass            : user
ObjectGUID             : a82a8c58-1332-4a57-a6e2-68e0c750ea56
SamAccountName         : mike
SID                    : S-1-5-21-2989741381-570885089-3319121794-1108
Surname                : Robbins
UserPrincipalName      : miker@mikefrobbins.com
```

## <a name="summary"></a><span data-ttu-id="8d728-209">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="8d728-209">Summary</span></span>

<span data-ttu-id="8d728-210">In diesem Kapitel haben Sie erfahren, wie Sie bestimmen, welchen Objekttyp ein Befehl erzeugt, wie Sie bestimmen, welche Eigenschaften und Methoden für einen Befehl verfügbar sind, und wie Sie mit Befehlen arbeiten, die die Eigenschaften begrenzen, die standardmäßig zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="8d728-210">In this chapter, you've learned how to determine what type of object a command produces, how to determine what properties and methods are available for a command, and how to work with commands that limit the properties that are returned by default.</span></span>

## <a name="review"></a><span data-ttu-id="8d728-211">Überprüfung</span><span class="sxs-lookup"><span data-stu-id="8d728-211">Review</span></span>

1. <span data-ttu-id="8d728-212">Welchen Objekttyp erzeugt das Cmdlet `Get-Process`?</span><span class="sxs-lookup"><span data-stu-id="8d728-212">What type of object does the `Get-Process` cmdlet produce?</span></span>
1. <span data-ttu-id="8d728-213">Wie bestimmen Sie die für einen Befehl verfügbaren Eigenschaften?</span><span class="sxs-lookup"><span data-stu-id="8d728-213">How do you determine what the available properties are for a command?</span></span>
1. <span data-ttu-id="8d728-214">Wenn es einen Befehl für das Abrufen, nicht aber für das Festlegen derselben Sache gibt, auf was sollten Sie überprüfen?</span><span class="sxs-lookup"><span data-stu-id="8d728-214">If a command exists for getting something but not for setting the same thing, what should you check for?</span></span>
1. <span data-ttu-id="8d728-215">Wie können Sie dafür sorgen, dass bestimmte Befehle, die standardmäßig keine Ausgabe erzeugen, eine Ausgabe erzeugen?</span><span class="sxs-lookup"><span data-stu-id="8d728-215">How can certain commands that don't produce output by default be made to produce output?</span></span>
1. <span data-ttu-id="8d728-216">Wenn Sie mit den Ergebnissen eines Befehls arbeiten möchten, der eine sehr große Menge an Ausgaben erzeugt, welche Aktion sollten Sie in Erwägung ziehen?</span><span class="sxs-lookup"><span data-stu-id="8d728-216">If you're going to be working with the results of a command that produces an enormous amount of output, what should you consider doing?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="8d728-217">Empfohlene Lektüre</span><span class="sxs-lookup"><span data-stu-id="8d728-217">Recommended Reading</span></span>

- <span data-ttu-id="8d728-218">[Get-Member][]</span><span class="sxs-lookup"><span data-stu-id="8d728-218">[Get-Member][]</span></span>
- <span data-ttu-id="8d728-219">[Anzeigen einer Objektstruktur (Get-Member)][]</span><span class="sxs-lookup"><span data-stu-id="8d728-219">[Viewing Object Structure (Get-Member)][]</span></span>
- <span data-ttu-id="8d728-220">[about_Objects][]</span><span class="sxs-lookup"><span data-stu-id="8d728-220">[about_Objects][]</span></span>
- <span data-ttu-id="8d728-221">[about_Properties][]</span><span class="sxs-lookup"><span data-stu-id="8d728-221">[about_Properties][]</span></span>
- <span data-ttu-id="8d728-222">[about_Methods][]</span><span class="sxs-lookup"><span data-stu-id="8d728-222">[about_Methods][]</span></span>
- <span data-ttu-id="8d728-223">[Kein PowerShell-Cmdlet zum Starten oder Beenden einer Aktion? Vergessen Sie nicht, auf Methoden des „Get-Cmdlets“ zu überprüfen][use-methods].</span><span class="sxs-lookup"><span data-stu-id="8d728-223">[No PowerShell Cmdlet to Start or Stop Something? Don’t Forget to Check for Methods on the Get Cmdlets][use-methods]</span></span>

<!-- link references -->
[RSAT für Windows]: https://support.microsoft.com/help/2693643
[RSAT for Windows]: https://support.microsoft.com/help/2693643
[Windows-Verwaltungsmodule]: /powershell/scripting/whats-new/module-compatibility#windows-management-modules
[Windows Management modules]: /powershell/scripting/whats-new/module-compatibility#windows-management-modules
[Get-Member]: /powershell/module/microsoft.powershell.utility/get-member
[Anzeigen einer Objektstruktur (Get-Member)]: /powershell/scripting/samples/viewing-object-structure--get-member-
[Viewing Object Structure (Get-Member)]: /powershell/scripting/samples/viewing-object-structure--get-member-
[about_Objects]: /powershell/module/microsoft.powershell.core/about/about_objects
[about_Properties]: /powershell/module/microsoft.powershell.core/about/about_properties
[about_Methods]: /powershell/module/microsoft.powershell.core/about/about_methods
[use-methods]: https://mikefrobbins.com/2016/12/15/no-powershell-cmdlet-to-start-or-stop-something-dont-forget-to-check-for-methods-on-the-get-cmdlets/
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
