---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Ändern des Computerstatus
ms.openlocfilehash: de3e31e358548943a015b7bba275c4461202b20f
ms.sourcegitcommit: d1ba596f9e0d4df9565601a70687a126d535c917
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2019
ms.locfileid: "70386285"
---
# <a name="changing-computer-state"></a><span data-ttu-id="a12b0-103">Ändern des Computerstatus</span><span class="sxs-lookup"><span data-stu-id="a12b0-103">Changing Computer State</span></span>

<span data-ttu-id="a12b0-104">Verwenden Sie zum Zurücksetzen eines Computers in Windows PowerShell entweder ein Standardbefehlszeilentool, WMI- oder CIM-Klasse.</span><span class="sxs-lookup"><span data-stu-id="a12b0-104">To reset a computer in Windows PowerShell, use either a standard command-line tool, WMI or CIM class.</span></span> <span data-ttu-id="a12b0-105">Sie verwenden Windows PowerShell zwar nur zum Ausführen des Tools, dennoch erfahren Sie einige wichtige Details über die Arbeit mit externen Tools in Windows PowerShell, indem Sie lernen, wie Sie den Energiezustand eines Computers in Windows PowerShell ändern.</span><span class="sxs-lookup"><span data-stu-id="a12b0-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="a12b0-106">Sperren eines Computers</span><span class="sxs-lookup"><span data-stu-id="a12b0-106">Locking a Computer</span></span>

<span data-ttu-id="a12b0-107">Die einzige Möglichkeit, einen Computer unmittelbar mit den standardmäßig verfügbaren Tools zu sperren, besteht im Aufrufen der Funktion **LockWorkstation()** in **user32.dll**:</span><span class="sxs-lookup"><span data-stu-id="a12b0-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="a12b0-108">Mit diesem Befehl wird die Arbeitsstation sofort gesperrt.</span><span class="sxs-lookup"><span data-stu-id="a12b0-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="a12b0-109">Hierbei wird *rundll32.exe* zum Ausführen von Windows-DLLs (und Speichern ihrer Bibliotheken für die wiederholte Verwendung) verwendet, um „user32.dll“, eine Bibliothek von Windows-Verwaltungsfunktionen, auszuführen.</span><span class="sxs-lookup"><span data-stu-id="a12b0-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="a12b0-110">Wenn Sie eine Arbeitsstation sperren, während die schnelle Benutzerumschaltung aktiviert ist, z. B. bei Computern unter Windows XP, wird der Benutzeranmeldebildschirm anstelle des Bildschirmschoners des aktuellen Benutzers angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a12b0-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="a12b0-111">Um bestimmte Sitzungen auf einem Terminalserver herunterzufahren, verwenden Sie das Befehlszeilentool **tsshutdn.exe**.</span><span class="sxs-lookup"><span data-stu-id="a12b0-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="a12b0-112">Abmelden der aktuellen Sitzung</span><span class="sxs-lookup"><span data-stu-id="a12b0-112">Logging Off the Current Session</span></span>

<span data-ttu-id="a12b0-113">Es sind mehrere verschiedene Verfahren verfügbar, um eine Sitzung auf dem lokalen System abzumelden.</span><span class="sxs-lookup"><span data-stu-id="a12b0-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="a12b0-114">Die einfachste Möglichkeit besteht in der Verwendung des Remotedesktop-/Terminaldienste-Befehlszeilentools **logoff.exe**. (Weitere Informationen erhalten Sie, indem Sie an der Windows PowerShell-Eingabeaufforderung **logoff /?** eingeben).</span><span class="sxs-lookup"><span data-stu-id="a12b0-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="a12b0-115">Zum Abmelden der aktuellen aktiven Sitzung geben Sie **logoff** ohne Argumente ein.</span><span class="sxs-lookup"><span data-stu-id="a12b0-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="a12b0-116">Sie können auch das Tool **shutdown.exe** mit der zugehörigen Abmeldeoption verwenden:</span><span class="sxs-lookup"><span data-stu-id="a12b0-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="a12b0-117">Eine weitere Möglichkeit ist die Verwendung von WMI.</span><span class="sxs-lookup"><span data-stu-id="a12b0-117">Another option is to use WMI.</span></span> <span data-ttu-id="a12b0-118">Die Klasse „Win32_OperatingSystem“ besitzt eine Win32Shutdown-Methode.</span><span class="sxs-lookup"><span data-stu-id="a12b0-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="a12b0-119">Durch Aufrufen der Methode mit dem 0-Flag wird die Abmeldung initiiert:</span><span class="sxs-lookup"><span data-stu-id="a12b0-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="a12b0-120">Weitere Informationen und andere Funktionen der Win32Shutdown-Methode finden Sie unter „Win32Shutdown-Methode der Win32_OperatingSystem-Klasse“ in MSDN.</span><span class="sxs-lookup"><span data-stu-id="a12b0-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

<span data-ttu-id="a12b0-121">Schließlich können Sie CIM mit der gleichen Win32_OperatingSystem-Klasse verwenden, wie oben bei der WMI-Methode beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a12b0-121">Finally you can use CIM with the same Win32_OperatingSystem class as described above in the WMI method.</span></span>

```powershell
Get-CIMInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="a12b0-122">Herunterfahren oder Neustarten eines Computers</span><span class="sxs-lookup"><span data-stu-id="a12b0-122">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="a12b0-123">Das Herunterfahren und Neustarten von Computern wird im Allgemeinen vom gleichen Tasktyp ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="a12b0-123">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="a12b0-124">Mit Tools, die einen Computer herunterfahren, kann normalerweise auch ein Neustart ausgeführt werden, und umgekehrt.</span><span class="sxs-lookup"><span data-stu-id="a12b0-124">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="a12b0-125">Es gibt zwei einfache Optionen für den Neustart eines Computers aus Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a12b0-125">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="a12b0-126">Verwenden Sie entweder „Tsshutdn.exe“ oder „Shutdown.exe“ mit den entsprechenden Argumenten.</span><span class="sxs-lookup"><span data-stu-id="a12b0-126">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="a12b0-127">Ausführliche Informationen zur Verwendung erhalten Sie mit **tsshutdn.exe /?**</span><span class="sxs-lookup"><span data-stu-id="a12b0-127">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="a12b0-128">oder **shutdown.exe /?** .</span><span class="sxs-lookup"><span data-stu-id="a12b0-128">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="a12b0-129">Sie können Ihren Computer auch direkt über Windows PowerShell herunterfahren und neu starten.</span><span class="sxs-lookup"><span data-stu-id="a12b0-129">You can also perform shutdown and restart operations directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="a12b0-130">Verwenden Sie den Befehl „Stop-Computer“, um den Computer herunterzufahren.</span><span class="sxs-lookup"><span data-stu-id="a12b0-130">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="a12b0-131">Verwenden Sie den Befehl „Restart-Computer“, um das Betriebssystem neu zu starten.</span><span class="sxs-lookup"><span data-stu-id="a12b0-131">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="a12b0-132">Um einen sofortigen Neustart des Computers zu erzwingen, verwenden Sie den -Force-Parameter.</span><span class="sxs-lookup"><span data-stu-id="a12b0-132">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
