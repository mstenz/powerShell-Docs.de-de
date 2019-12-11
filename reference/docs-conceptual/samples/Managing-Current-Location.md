---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Verwalten des aktuellen Speicherorts
ms.openlocfilehash: 42ab56759dec882d140f813c8614e578957722b3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030206"
---
# <a name="managing-current-location"></a><span data-ttu-id="1331d-103">Verwalten des aktuellen Speicherorts</span><span class="sxs-lookup"><span data-stu-id="1331d-103">Managing Current Location</span></span>

<span data-ttu-id="1331d-104">Wenn Sie in Verzeichnissystemen im Datei-Explorer navigieren, haben Sie in der Regel einen bestimmten Arbeitsspeicherort, nämlich den aktuell geöffneten Ordner.</span><span class="sxs-lookup"><span data-stu-id="1331d-104">When navigating folder systems in File Explorer, you usually have a specific working location - namely, the current open folder.</span></span> <span data-ttu-id="1331d-105">Elemente im aktuellen Ordner können problemlos verarbeitet werden, indem auf sie geklickt wird.</span><span class="sxs-lookup"><span data-stu-id="1331d-105">Items in the current folder can be manipulated easily by clicking them.</span></span> <span data-ttu-id="1331d-106">In Befehlszeilenschnittstellen wie z.B. „Cmd.exe“ gilt: Wenn Sie sich im selben Ordner wie eine bestimmte Datei befinden, können Sie darauf zugreifen, indem Sie einen relativ kurzen Namen angeben. Es ist nicht erforderlich, dass Sie den vollständigen Pfad zu der Datei angeben.</span><span class="sxs-lookup"><span data-stu-id="1331d-106">For command-line interfaces such as Cmd.exe, when you are in the same folder as a particular file, you can access it by specifying a relatively short name, rather than needing to specify the entire path to the file.</span></span> <span data-ttu-id="1331d-107">Das aktuelle Verzeichnis wird als Arbeitsverzeichnis bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="1331d-107">The current directory is called the working directory.</span></span>

<span data-ttu-id="1331d-108">In Windows PowerShell wird das Substantiv **Location** verwendet, um auf das Arbeitsverzeichnis zu verweisen, und es sind einige Cmdlets implementiert, mit denen der Speicherort überprüft und geändert werden kann.</span><span class="sxs-lookup"><span data-stu-id="1331d-108">Windows PowerShell uses the noun **Location** to refer to the working directory, and implements a family of cmdlets to examine and manipulate your location.</span></span>

## <a name="getting-your-current-location-get-location"></a><span data-ttu-id="1331d-109">Abrufen Ihres aktuellen Speicherorts (Get-Location)</span><span class="sxs-lookup"><span data-stu-id="1331d-109">Getting Your Current Location (Get-Location)</span></span>

<span data-ttu-id="1331d-110">Um den Pfad zu Ihrem aktuellen Verzeichnis zu ermitteln, geben Sie den Befehl **Get-Location** ein:</span><span class="sxs-lookup"><span data-stu-id="1331d-110">To determine the path of your current directory location, enter the **Get-Location** command:</span></span>

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="1331d-111">Das Cdmlet „Get-Location“ ähnelt dem Befehl **pwd** in der BASH-Shell.</span><span class="sxs-lookup"><span data-stu-id="1331d-111">The Get-Location cmdlet is similar to the **pwd** command in the BASH shell.</span></span> <span data-ttu-id="1331d-112">Das Cdmlet „Set-Location“ ähnelt dem Befehl **cd** in „Cmd.exe“.</span><span class="sxs-lookup"><span data-stu-id="1331d-112">The Set-Location cmdlet is similar to the **cd** command in Cmd.exe.</span></span>

## <a name="setting-your-current-location-set-location"></a><span data-ttu-id="1331d-113">Festlegen Ihres aktuellen Speicherorts (Set-Location)</span><span class="sxs-lookup"><span data-stu-id="1331d-113">Setting Your Current Location (Set-Location)</span></span>

<span data-ttu-id="1331d-114">Der Befehl **Get-Location** wird mit dem Befehl **Set-Location** verwendet.</span><span class="sxs-lookup"><span data-stu-id="1331d-114">The **Get-Location** command is used with the **Set-Location** command.</span></span> <span data-ttu-id="1331d-115">Der Befehl **Set-Location** ermöglicht es Ihnen, das aktuelle Verzeichnis anzugeben.</span><span class="sxs-lookup"><span data-stu-id="1331d-115">The **Set-Location** command allows you to specify your current directory location.</span></span>

```powershell
Set-Location -Path C:\Windows
```

<span data-ttu-id="1331d-116">Nachdem Sie den Befehl eingegeben haben, erhalten Sie kein direktes Feedback zu den Auswirkungen des Befehls.</span><span class="sxs-lookup"><span data-stu-id="1331d-116">After you enter the command, you will notice that you do not receive any direct feedback about the effect of the command.</span></span> <span data-ttu-id="1331d-117">Die meisten Windows PowerShell-Befehle, die eine Aktion ausführen, erzeugen nur wenig oder keine Ausgabe, da die Ausgabe nicht immer hilfreich ist.</span><span class="sxs-lookup"><span data-stu-id="1331d-117">Most Windows PowerShell commands that perform an action produce little or no output because the output is not always useful.</span></span> <span data-ttu-id="1331d-118">Um sich zu vergewissern, dass das Verzeichnis nach der Eingabe des Befehls **Set-Location** erfolgreich geändert wurde, fügen Sie den Parameter **-PassThru** ein, wenn Sie den Befehl **Set-Location** eingeben:</span><span class="sxs-lookup"><span data-stu-id="1331d-118">To verify that a successful directory change has occurred when you enter the **Set-Location** command, include the **-PassThru** parameter when you enter the **Set-Location** command:</span></span>

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

<span data-ttu-id="1331d-119">Der Parameter **-PassThru** kann mit vielen „Set“-Befehlen in Windows PowerShell verwendet werden, um Informationen über das Ergebnis in Fällen zurückzugeben, in denen keine Standardausgabe vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="1331d-119">The **-PassThru** parameter can be used with many Set commands in Windows PowerShell to return information about the result in cases in which there is no default output.</span></span>

<span data-ttu-id="1331d-120">Sie können Pfade, die relativ zu Ihrem aktuellen Speicherort sind, auf die gleiche Weise angeben, wie Sie dies in den meisten UNIX- und Windows-Befehlsshells tun würden.</span><span class="sxs-lookup"><span data-stu-id="1331d-120">You can specify paths relative to your current location in the same way as you would in most UNIX and Windows command shells.</span></span> <span data-ttu-id="1331d-121">In der Standardschreibweise für relative Pfade stellt ein Punkt ( **.** ) Ihren aktuellen Ordner dar, und zwei Punkte ( **..** ) stellen das übergeordnete Verzeichnis Ihres aktuellen Speicherorts dar.</span><span class="sxs-lookup"><span data-stu-id="1331d-121">In standard notation for relative paths, a period (**.**)represents your current folder, and a doubled period (**..**) represents the parent directory of your current location.</span></span>

<span data-ttu-id="1331d-122">Wenn Sie sich beispielsweise im Ordner **C:\\Windows** befinden, stellt ein Punkt ( **.** ) **C:\\Windows** dar, während zwei Punkte ( **..** ) **C:** darstellen.</span><span class="sxs-lookup"><span data-stu-id="1331d-122">For example, if you are in the **C:\\Windows** folder, a period (**.**)represents **C:\\Windows** and double periods (**..**) represent **C:**.</span></span> <span data-ttu-id="1331d-123">Sie können aus Ihrem aktuellen Speicherort in das Stammverzeichnis des Laufwerks C: wechseln, indem Sie Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="1331d-123">You can change from your current location to the root of the C: drive by typing:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

<span data-ttu-id="1331d-124">Dieselbe Vorgehensweise funktioniert für Windows PowerShell-Laufwerke, die keine Dateisystemlaufwerke sind, etwa **HKLM:** .</span><span class="sxs-lookup"><span data-stu-id="1331d-124">The same technique works on Windows PowerShell drives that are not file system drives, such as **HKLM:**.</span></span> <span data-ttu-id="1331d-125">Sie können Ihren Speicherort auf den Schlüssel „HKLM\\Software“ in der Registrierung festlegen, indem Sie Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="1331d-125">You can set your location to the HKLM\\Software key in the registry by typing:</span></span>

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

<span data-ttu-id="1331d-126">Anschließend können Sie das Verzeichnis in das übergeordnete Verzeichnis ändern, das das Stammverzeichnis des Windows PowerShell-Laufwerks HKLM: ist, indem Sie einen relativen Pfad angeben:</span><span class="sxs-lookup"><span data-stu-id="1331d-126">You can then change the directory location to the parent directory, which is the root of the Windows PowerShell HKLM: drive, by using a relative path:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

<span data-ttu-id="1331d-127">Sie können „Set-Location“ eingeben oder einen der integrierten Windows PowerShell-Aliase für „Set-Location“ verwenden („cd“, „chdir“, „sl“).</span><span class="sxs-lookup"><span data-stu-id="1331d-127">You can type Set-Location or use any of the built-in Windows PowerShell aliases for Set-Location (cd, chdir, sl).</span></span> <span data-ttu-id="1331d-128">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="1331d-128">For example:</span></span>

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

## <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a><span data-ttu-id="1331d-129">Speichern und Abrufen von zuletzt verwendeten Speicherorten („Push-Location“ und „Pop-Location“)</span><span class="sxs-lookup"><span data-stu-id="1331d-129">Saving and Recalling Recent Locations (Push-Location and Pop-Location)</span></span>

<span data-ttu-id="1331d-130">Wenn Sie Speicherorte wechseln, ist es sinnvoll, zu verfolgen, wo Sie waren, und in der Lage zu sein, zu Ihrem vorherigen Speicherort zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="1331d-130">When changing locations, it is helpful to keep track of where you have been and to be able to return to your previous location.</span></span> <span data-ttu-id="1331d-131">Das Cmdlet **Push-Location** in Windows PowerShell erstellt einen geordneten Verlauf (einen „Stapel“) der Verzeichnispfade, in denen Sie waren, und Sie können mithilfe des komplementären Cmdlets **Pop-Location** durch den Verlauf der Verzeichnispfade zurückgehen.</span><span class="sxs-lookup"><span data-stu-id="1331d-131">The **Push-Location** cmdlet in Windows PowerShell creates a ordered history (a "stack") of directory paths where you have been, and you can step back through the history of directory paths by using the complementary **Pop-Location** cmdlet.</span></span>

<span data-ttu-id="1331d-132">Beispielsweise startet Windows PowerShell üblicherweise im Basisverzeichnis des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="1331d-132">For example, Windows PowerShell typically starts in the user's home directory.</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="1331d-133">Das Wort *Stapel* hat in vielen Programmiereinstellungen eine besondere Bedeutung, so auch in NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1331d-133">The word *stack* has a special meaning in many programming settings, including .NET Framework.</span></span> <span data-ttu-id="1331d-134">Wie bei einem physischen Stapel von Elementen ist das letzte Elemente, das Sie auf dem Stapel ablegen, das erste Element, das Sie von dem Stapel herunternehmen können.</span><span class="sxs-lookup"><span data-stu-id="1331d-134">Like a physical stack of items, the last item you put onto the stack is the first item that you can pull off the stack.</span></span> <span data-ttu-id="1331d-135">Das Hinzufügen eines Elements zu einem Stapel wird gelegentlich als „Element mit Push auf dem Stapel ablegen“ bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="1331d-135">Adding an item to a stack is colloquially known as "pushing" the item onto the stack.</span></span> <span data-ttu-id="1331d-136">Das Herunternehmen eines Elements vom Stapel wird gelegentlich als „Element mit Pop aus dem Stapel entfernen“ bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="1331d-136">Pulling an item off the stack is colloquially known as "popping" the item off the stack.</span></span>

<span data-ttu-id="1331d-137">Um den aktuellen Speicherort auf dem Stapel abzulegen und dann zum Ordner „Local Settings“ zu wechseln, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="1331d-137">To push the current location onto the stack, and then move to the Local Settings folder, type:</span></span>

```powershell
Push-Location -Path "Local Settings"
```

<span data-ttu-id="1331d-138">Sie können dann das Verzeichnis „Local Settings“ auf dem Stapel ablegen und zum Ordner „Temp“ wechseln, indem Sie Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="1331d-138">You can then push the Local Settings location onto the stack and move to the Temp folder by typing:</span></span>

```powershell
Push-Location -Path Temp
```

<span data-ttu-id="1331d-139">Sie können sich vergewissern, dass Sie die Verzeichnisse geändert haben, indem Sie den Befehl **Get-Location** eingeben:</span><span class="sxs-lookup"><span data-stu-id="1331d-139">You can verify that you changed directories by entering the **Get-Location** command:</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

<span data-ttu-id="1331d-140">Sie können dann zurück zum zuletzt besuchten Verzeichnis wechseln, indem Sie den Befehl **Pop-Location** eingeben, und die Änderung überprüfen, indem Sie den Befehl **Get-Location** eingeben:</span><span class="sxs-lookup"><span data-stu-id="1331d-140">You can then pop back into the most recently visited directory by entering the **Pop-Location** command, and verify the change by entering the **Get-Location** command:</span></span>

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

<span data-ttu-id="1331d-141">Wie beim Cdmlet **Set-Location** können Sie den Parameter **-PassThru** bei der Eingabe des Cdmlets **Pop-Location** einfügen, damit das Verzeichnis angezeigt wird, das Sie eingegeben haben:</span><span class="sxs-lookup"><span data-stu-id="1331d-141">Just as with the **Set-Location** cmdlet, you can include the **-PassThru** parameter when you enter the **Pop-Location** cmdlet to display the directory that you entered:</span></span>

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

<span data-ttu-id="1331d-142">Sie können die „Location“-Cdmlets auch mit Netzwerkpfaden verwenden.</span><span class="sxs-lookup"><span data-stu-id="1331d-142">You can also use the Location cmdlets with network paths.</span></span> <span data-ttu-id="1331d-143">Wenn Sie einen Server namens „FS01“ mit einer Freigabe namens „Public“ haben, können Sie den Speicherort ändern, indem Sie Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="1331d-143">If you have a server named FS01 with an share named Public, you can change your location by typing</span></span>

```powershell
Set-Location \\FS01\Public
```

<span data-ttu-id="1331d-144">oder</span><span class="sxs-lookup"><span data-stu-id="1331d-144">or</span></span>

```powershell
Push-Location \\FS01\Public
```

<span data-ttu-id="1331d-145">Sie können die Befehle **Push-Location** und **Set-Location** verwenden, um den Speicherort in jedes verfügbare Laufwerk zu ändern.</span><span class="sxs-lookup"><span data-stu-id="1331d-145">You can use the **Push-Location** and **Set-Location** commands to change the location to any available drive.</span></span> <span data-ttu-id="1331d-146">Wenn Sie z.B. ein lokales CD-ROM-Laufwerk mit dem Laufwerksbuchstaben D haben, das eine Daten-CD enthält, können Sie den Speicherort in das CD-Laufwerk ändern, indem Sie den Befehl **Set-Location D:** eingeben.</span><span class="sxs-lookup"><span data-stu-id="1331d-146">For example, if you have a local CD-ROM drive with drive letter D that contains a data CD, you can change the location to the CD drive by entering the **Set-Location D:** command.</span></span>

<span data-ttu-id="1331d-147">Ist das Laufwerk leer, wird die folgende Fehlermeldung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="1331d-147">If the drive is empty, you will get the following error message:</span></span>

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

<span data-ttu-id="1331d-148">Wenn Sie eine Befehlszeilenschnittstelle verwenden, ist es nicht praktisch, den Datei-Explorer zu verwenden, um die verfügbaren physischen Laufwerken zu prüfen.</span><span class="sxs-lookup"><span data-stu-id="1331d-148">When you are using a command-line interface, it is not convenient to use File Explorer to examine the available physical drives.</span></span> <span data-ttu-id="1331d-149">Der Datei-Explorer zeigt darüber hinaus nicht alle Windows PowerShell-Laufwerke an.</span><span class="sxs-lookup"><span data-stu-id="1331d-149">Also, File Explorer would not show you the all of the Windows PowerShell drives.</span></span> <span data-ttu-id="1331d-150">Windows PowerShell stellt eine Reihe von Befehlen zum Handhaben von Windows PowerShell-Laufwerken bereit, die im nächsten Abschnitt vorgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="1331d-150">Windows PowerShell provides a set of commands for manipulating Windows PowerShell drives, and we will talk about these next.</span></span>
