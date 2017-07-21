---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Verwalten von Diensten
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: 9fd6c8bcfecc99756188409629ddf94b880aab91
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="managing-services"></a><span data-ttu-id="a4338-103">Verwalten von Diensten</span><span class="sxs-lookup"><span data-stu-id="a4338-103">Managing Services</span></span>
<span data-ttu-id="a4338-104">Es gibt acht dienstbezogene Kern-Cmdlets („Service“-Cmdlets), die für eine Vielzahl von Dienstaufgaben konzipiert sind.</span><span class="sxs-lookup"><span data-stu-id="a4338-104">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="a4338-105">Hier geht es nur um das Auflisten von Diensten und das Ändern des Ausführungsstatus für Dienste, Sie können aber eine Liste der „Service“-Cmdlets abrufen, indem Sie **Get-Help \&#42;-Service** verwenden, und Sie finden Informationen zu jedem „Service“-Cmdlet, indem Sie **Get-Help <Cmdlet-Name>** verwenden, z.B. **Get-Help New-Service**.</span><span class="sxs-lookup"><span data-stu-id="a4338-105">We will look only at listing and changing running state for services, but you can get a list Service cmdlets by using **Get-Help \&#42;-Service**, and you can find information about each Service cmdlet by using **Get-Help<Cmdlet-Name>**, such as **Get-Help New-Service**.</span></span>

## <a name="getting-services"></a><span data-ttu-id="a4338-106">Abrufen von Diensten</span><span class="sxs-lookup"><span data-stu-id="a4338-106">Getting Services</span></span>
<span data-ttu-id="a4338-107">Sie können die Dienste auf einem lokalen oder Remotecomputer abrufen, indem Sie das Cmdlet **Get-Service** verwenden.</span><span class="sxs-lookup"><span data-stu-id="a4338-107">You can get the services on a local or remote computer by using the **Get-Service** cmdlet.</span></span> <span data-ttu-id="a4338-108">Wie bei **Get-Process** werden alle Dienste zurückgegeben, wenn Sie den Befehl **Get-Service** ohne Parameter verwenden.</span><span class="sxs-lookup"><span data-stu-id="a4338-108">As with **Get-Process**, using the **Get-Service** command without parameters returns all services.</span></span> <span data-ttu-id="a4338-109">Sie können nach Name filtern, und Sie können sogar ein Sternchen als Platzhalterzeichen verwenden:</span><span class="sxs-lookup"><span data-stu-id="a4338-109">You can filter by name, even using an asterisk as a wildcard:</span></span>

```
PS> Get-Service -Name se*
Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="a4338-110">Weil nicht immer offensichtlich ist, welcher Name der echte Name für einen Dienst ist, möchten Sie möglicherweise über den Anzeigenamen nach Diensten suchen.</span><span class="sxs-lookup"><span data-stu-id="a4338-110">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="a4338-111">Dazu können Sie nach einem bestimmten Namen, mit Platzhaltern oder mit einer Liste von Anzeigenamen suchen:</span><span class="sxs-lookup"><span data-stu-id="a4338-111">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

```
PS> Get-Service -DisplayName se*
Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center
PS> Get-Service -DisplayName ServiceLayer,Server
Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="a4338-112">Sie können den „ComputerName“-Parameter des „Get-Service“-Cmdlets verwenden, um die Dienste auf Remotecomputern abzurufen.</span><span class="sxs-lookup"><span data-stu-id="a4338-112">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="a4338-113">Der „ComputerName“-Parameter akzeptiert mehrere Werte sowie Platzhalterzeichen, sodass Sie die Dienste auf mehreren Computern mit einem einzigen Befehl abrufen können.</span><span class="sxs-lookup"><span data-stu-id="a4338-113">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="a4338-114">Beispielsweise ruft der folgende Befehl die Dienste auf dem Remotecomputer „Server01“ ab.</span><span class="sxs-lookup"><span data-stu-id="a4338-114">For example, the following command gets the services on the Server01 remote computer.</span></span>

```
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="a4338-115">Abrufen von erforderlichen und abhängigen Diensten</span><span class="sxs-lookup"><span data-stu-id="a4338-115">Getting Required and Dependent Services</span></span>
<span data-ttu-id="a4338-116">Das „Get-Service“-Cmdlet hat zwei Parameter, die bei der Verwaltung von Diensten sehr hilfreich sind.</span><span class="sxs-lookup"><span data-stu-id="a4338-116">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="a4338-117">Der „DependentServices“-Parameter bewirkt, dass Dienste abgerufen werden, die vom angegebenen Dienst abhängen.</span><span class="sxs-lookup"><span data-stu-id="a4338-117">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="a4338-118">Der „RequiredServices“-Parameter bewirkt, dass Dienste abgerufen, von denen der angegebene Dienst abhängt.</span><span class="sxs-lookup"><span data-stu-id="a4338-118">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="a4338-119">Diese Parameter bewirken lediglich, dass die Werte der Eigenschaften „DependentServices und „ServicesDependedOn“ (Alias = „RequiredServices“) des von „Get-Service“ zurückgegebenen „System.ServiceProcess.ServiceController“-Objekts angezeigt werden, aber sie vereinfachen Befehle und machen das Abrufen dieser Informationen viel einfacher.</span><span class="sxs-lookup"><span data-stu-id="a4338-119">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="a4338-120">Der folgende Befehl ruft die Dienste ab, die für den „LanmanWorkstation“-Dienst erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="a4338-120">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```
PS> Get-Service -Name LanmanWorkstation -RequiredServices
Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="a4338-121">Der folgende Befehl ruft die Dienste ab, für die der „LanmanWorkstation“-Dienst erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="a4338-121">The following command gets the services that require the LanmanWorkstation service.</span></span>

```
PS> Get-Service -Name LanmanWorkstation -DependentServices
Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="a4338-122">Sie können sogar alle Dienste abrufen, für die es Abhängigkeiten gibt.</span><span class="sxs-lookup"><span data-stu-id="a4338-122">You can even get all services that have dependencies.</span></span> <span data-ttu-id="a4338-123">Im folgenden Befehl wird genau das getan und anschließend das Cmdlet „Format-Table“ verwendet, um für die Dienste auf dem Computer die Eigenschaften „Status“, „Name“, „RequiredServices“ und „DependentServices“ anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a4338-123">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```
Get-Service -Name * | where {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="a4338-124">Beenden, Starten, Anhalten und Neustarten von Diensten</span><span class="sxs-lookup"><span data-stu-id="a4338-124">Stopping, Starting, Suspending, and Restarting Services</span></span>
<span data-ttu-id="a4338-125">Die „Service“-Cmdlets die alle haben dieselbe allgemeine Form.</span><span class="sxs-lookup"><span data-stu-id="a4338-125">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="a4338-126">Dienste können als allgemeine Namen oder Anzeigenamen angegeben werden, und es können Listen sowie Platzhalter als Werte angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="a4338-126">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="a4338-127">Um den Druckspooler zu beenden, verwenden Sie folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="a4338-127">To stop the print spooler, use:</span></span>

```
Stop-Service -Name spooler
```

<span data-ttu-id="a4338-128">Um den Druckspooler zu starten, nachdem er beendet wurde, verwenden Sie folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="a4338-128">To start the print spooler after it is stopped, use:</span></span>

```
Start-Service -Name spooler
```

<span data-ttu-id="a4338-129">Um den Druckspooler anzuhalten, verwenden Sie folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="a4338-129">To suspend the print spooler, use:</span></span>

```
Suspend-Service -Name spooler
```

<span data-ttu-id="a4338-130">Das **Restart-Service**-Cmdlet funktioniert in gleicher Weise wie die anderen „Service“-Cmdlets, aber es werden einige komplexere Beispiele für dieses Cmdlet erläutert.</span><span class="sxs-lookup"><span data-stu-id="a4338-130">The **Restart-Service** cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="a4338-131">Bei der einfachsten Verwendung geben Sie den Namen des Diensts an:</span><span class="sxs-lookup"><span data-stu-id="a4338-131">In the simplest use, you specify the name of the service:</span></span>

```
PS> Restart-Service -Name spooler
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="a4338-132">Sie werden feststellen, dass eine wiederholte Warnmeldung zum Startvorgang des Druckspoolers angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a4338-132">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="a4338-133">Wenn Sie einen Dienstvorgang ausführen, der einige Zeit dauert, werden Sie von Windows PowerShell benachrichtigt, dass weiterhin versucht wird, die Aufgabe auszuführen.</span><span class="sxs-lookup"><span data-stu-id="a4338-133">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="a4338-134">Wenn Sie mehrere Dienste neu starten möchten, können Sie eine Liste der Dienste abrufen, diese Liste filtern und dann den Neustart ausführen:</span><span class="sxs-lookup"><span data-stu-id="a4338-134">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

```
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

<span data-ttu-id="a4338-135">Diese „Service“-Cmdlets haben keinen „ComputerName“-Parameter, Sie können sie aber auf einem Remotecomputer ausführen, indem Sie das „Invoke-Command“-Cmdlet verwenden.</span><span class="sxs-lookup"><span data-stu-id="a4338-135">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="a4338-136">Beispielsweise startet der folgende Befehl den „Spooler“-Dienst auf dem Remotecomputer „Server01“ neu.</span><span class="sxs-lookup"><span data-stu-id="a4338-136">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="a4338-137">Festlegen von Diensteigenschaften</span><span class="sxs-lookup"><span data-stu-id="a4338-137">Setting Service Properties</span></span>
<span data-ttu-id="a4338-138">Das Cmdlet „Set-Service“ ändert die Eigenschaften eines Diensts auf einem lokalen Computer oder Remotecomputer.</span><span class="sxs-lookup"><span data-stu-id="a4338-138">The Set-Service cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="a4338-139">Weil der Dienststatus eine Eigenschaft ist, können Sie dieses Cmdlet verwenden, um einen Dienst zu starten, zu beenden und anzuhalten.</span><span class="sxs-lookup"><span data-stu-id="a4338-139">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span> <span data-ttu-id="a4338-140">Das Cmdlet „Set-Service“ hat außerdem einen „StartupType“-Parameter, über den Sie den Starttyp des Diensts ändern können.</span><span class="sxs-lookup"><span data-stu-id="a4338-140">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="a4338-141">Wenn Sie „Set-Service“ unter Windows Vista und höheren Versionen von Windows verwenden möchten, öffnen Sie Windows PowerShell mit der Option „Als Administrator ausführen“.</span><span class="sxs-lookup"><span data-stu-id="a4338-141">To use Set-Service on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="a4338-142">Weitere Informationen hierzu finden Sie unter [Set-Service [m2]](https://technet.microsoft.com/en-us/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3).</span><span class="sxs-lookup"><span data-stu-id="a4338-142">For more information, see [Set-Service [m2]](https://technet.microsoft.com/en-us/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>

## <a name="see-also"></a><span data-ttu-id="a4338-143">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a4338-143">See Also</span></span>
- [<span data-ttu-id="a4338-144">Get-Service [m2]</span><span class="sxs-lookup"><span data-stu-id="a4338-144">Get-Service [m2]</span></span>](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)
- [<span data-ttu-id="a4338-145">Set-Service [m2]</span><span class="sxs-lookup"><span data-stu-id="a4338-145">Set-Service [m2]</span></span>](https://technet.microsoft.com/en-us/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)
- [<span data-ttu-id="a4338-146">Restart-Service [m2]</span><span class="sxs-lookup"><span data-stu-id="a4338-146">Restart-Service [m2]</span></span>](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)
- [<span data-ttu-id="a4338-147">Suspend-Service [m2]</span><span class="sxs-lookup"><span data-stu-id="a4338-147">Suspend-Service [m2]</span></span>](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)

