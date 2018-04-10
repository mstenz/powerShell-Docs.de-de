---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Arbeiten mit Registrierungseinträge
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="cfc36-103">Arbeiten mit Registrierungseinträge</span><span class="sxs-lookup"><span data-stu-id="cfc36-103">Working with Registry Entries</span></span>

<span data-ttu-id="cfc36-104">Da Registrierungseinträge Eigenschaften von Schlüsseln sind und daher nicht direkt gesucht werden können, muss für die Arbeit mit diesen ein etwas anderer Ansatz gewählt werden.</span><span class="sxs-lookup"><span data-stu-id="cfc36-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

### <a name="listing-registry-entries"></a><span data-ttu-id="cfc36-105">Auflisten von Registrierungseinträgen</span><span class="sxs-lookup"><span data-stu-id="cfc36-105">Listing Registry Entries</span></span>

<span data-ttu-id="cfc36-106">Es gibt viele verschiedene Möglichkeiten zum Untersuchen von Registrierungseinträgen.</span><span class="sxs-lookup"><span data-stu-id="cfc36-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="cfc36-107">Am einfachsten ist es, die Eigenschaftennamen mit einem Schlüssel zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="cfc36-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="cfc36-108">Um beispielsweise die Namen der Einträge im Registrierungsschlüssel **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion** anzuzeigen, verwenden Sie **Get-Item**.</span><span class="sxs-lookup"><span data-stu-id="cfc36-108">For example, to see the names of the entries in the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, use **Get-Item**.</span></span> <span data-ttu-id="cfc36-109">Registrierungsschlüssel verfügen über eine Eigenschaft mit dem generischen Namen „Property“, die eine Liste der Registrierungseinträge im Schlüssel ist.</span><span class="sxs-lookup"><span data-stu-id="cfc36-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span> <span data-ttu-id="cfc36-110">Der folgende Befehl wählt die Eigenschaft „Property“ aus und erweitert die Elemente so, dass sie in einer Liste angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="cfc36-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="cfc36-111">Um die Registrierungseinträge in einer besser lesbaren Form anzuzeigen, verwenden Sie **Get-ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="cfc36-111">To view the registry entries in a more readable form, use **Get-ItemProperty**:</span></span>

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

<span data-ttu-id="cfc36-112">Die Windows PowerShell-bezogenen Eigenschaften für den Schüssel verfügen alle über das Präfix „PS“, z.B. **PSPath**, **PSParentPath**, **PSChildName** und **PSProvider**.</span><span class="sxs-lookup"><span data-stu-id="cfc36-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="cfc36-113">Sie können die Notation „**.**“ zum Verweisen auf den aktuellen Speicherort verwenden.</span><span class="sxs-lookup"><span data-stu-id="cfc36-113">You can use the "**.**" notation for referring to the current location.</span></span> <span data-ttu-id="cfc36-114">Sie können **Set-Location** verwenden, um zuerst in den Registrierungscontainer **CurrentVersion** zu wechseln:</span><span class="sxs-lookup"><span data-stu-id="cfc36-114">You can use **Set-Location** to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="cfc36-115">Alternativ dazu können Sie das integrierte HKLM PSDrive mit **Set-Location** verwenden:</span><span class="sxs-lookup"><span data-stu-id="cfc36-115">Alternatively, you can use the built-in HKLM PSDrive with **Set-Location**:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="cfc36-116">Anschließend können Sie die Notation „**.**“ für den aktuellen Speicherort verwenden, um die Eigenschaften aufzulisten, ohne einen vollständigen Pfad anzugeben:</span><span class="sxs-lookup"><span data-stu-id="cfc36-116">You can then use the "**.**" notation for the current location to list the properties without specifying a full path:</span></span>

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="cfc36-117">Die Pfaderweiterung funktioniert in derselben Weise wie innerhalb des Dateisystem. Von diesem Speicherort aus können Sie die Auflistung **ItemProperty** für **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** abrufen, indem Sie **Get-ItemProperty -Path ..\\Help** verwenden.</span><span class="sxs-lookup"><span data-stu-id="cfc36-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** by using **Get-ItemProperty -Path ..\\Help**.</span></span>

### <a name="getting-a-single-registry-entry"></a><span data-ttu-id="cfc36-118">Abrufen eines einzelnen Registrierungseintrags</span><span class="sxs-lookup"><span data-stu-id="cfc36-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="cfc36-119">Wenn Sie einen bestimmten Eintrag in einem Registrierungsschlüssel abrufen möchten, stehen verschiedene Möglichkeiten zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="cfc36-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="cfc36-120">In diesem Beispiel wird der Wert von **DevicePath** in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion** abgerufen.</span><span class="sxs-lookup"><span data-stu-id="cfc36-120">This example finds the value of **DevicePath** in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span>

<span data-ttu-id="cfc36-121">Verwenden Sie mit **Get-ItemProperty** den Parameter **Path**, um den Namen des Schlüssels anzugeben, und den Parameter **Name**, um den Namen des Eintrags **DevicePath** anzugeben.</span><span class="sxs-lookup"><span data-stu-id="cfc36-121">Using **Get-ItemProperty**, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="cfc36-122">Dieser Befehl gibt die standardmäßigen Windows PowerShell-Eigenschaften sowie die Eigenschaft **DevicePath** aus.</span><span class="sxs-lookup"><span data-stu-id="cfc36-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="cfc36-123">Obwohl **Get-ItemProperty** die Parameter **Filter**, **Include** und **Exclude** aufweist, können diese nicht zum Filtern nach dem Namen der Eigenschaft verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="cfc36-123">Although **Get-ItemProperty** has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="cfc36-124">Diese Parameter verweisen auf Registrierungsschlüssel (das sind Elementpfade und keine Registrierungseinträge), die Elementeigenschaften sind.</span><span class="sxs-lookup"><span data-stu-id="cfc36-124">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="cfc36-125">Eine weitere Option ist die Verwendung des Befehlszeilentools „Reg.exe“.</span><span class="sxs-lookup"><span data-stu-id="cfc36-125">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="cfc36-126">Um Hilfe zu „reg.exe“ zu erhalten, geben Sie **reg.exe /?** an einer Eingabeaufforderung ein.</span><span class="sxs-lookup"><span data-stu-id="cfc36-126">For help with reg.exe, type **reg.exe /?**</span></span> <span data-ttu-id="cfc36-127">an einer Eingabeaufforderung.</span><span class="sxs-lookup"><span data-stu-id="cfc36-127">at a command prompt.</span></span> <span data-ttu-id="cfc36-128">Mithilfe von „reg.exe“ finden Sie den Eintrag „DevicePath“, wie im folgenden Befehl gezeigt:</span><span class="sxs-lookup"><span data-stu-id="cfc36-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="cfc36-129">Sie können das Objekt **WshShell COM** auch zum Suchen bestimmter Registrierungseinträge verwenden, obwohl diese Methode mit großen Binärdaten oder mit Registrierungseintragsnamen, die Zeichen wie „\\“ enthalten, nicht funktioniert.</span><span class="sxs-lookup"><span data-stu-id="cfc36-129">You can also use the **WshShell COM** object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="cfc36-130">Fügen Sie den Namen der Eigenschaft mit einem \\-Trennzeichen zum Elementpfad hinzu:</span><span class="sxs-lookup"><span data-stu-id="cfc36-130">Append the property name to the item path with a \\ separator:</span></span>

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a><span data-ttu-id="cfc36-131">Erstellen neuer Registrierungseinträge</span><span class="sxs-lookup"><span data-stu-id="cfc36-131">Creating New Registry Entries</span></span>

<span data-ttu-id="cfc36-132">Um einen neuen Eintrag namens „PowerShellPath“ zum Schlüssel **CurrentVersion** hinzuzufügen, verwenden Sie **New-ItemProperty** mit dem Pfad zum Schüssel, dem Eintragsnamen und dem Wert des Eintrags.</span><span class="sxs-lookup"><span data-stu-id="cfc36-132">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use **New-ItemProperty** with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="cfc36-133">In diesem Beispiel wird der Wert der Windows PowerShell-Variablen **$PSHome** verwendet, in der der Pfad zum Installationsverzeichnis für Windows PowerShell gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="cfc36-133">For this example, we will take the value of the Windows PowerShell variable **$PSHome**, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="cfc36-134">Sie können dem Schlüssel mit Hilfe des folgenden Befehls den neuen Eintrag hinzufügen, und der Befehl gibt auch Informationen zu dem neuen Eintrag zurück:</span><span class="sxs-lookup"><span data-stu-id="cfc36-134">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="cfc36-135">**PropertyType** muss der Namen eines **Microsoft.Win32.RegistryValueKind**-Aufzählungselements aus der folgenden Tabelle sein:</span><span class="sxs-lookup"><span data-stu-id="cfc36-135">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="cfc36-136">PropertyType-Wert</span><span class="sxs-lookup"><span data-stu-id="cfc36-136">PropertyType Value</span></span>|<span data-ttu-id="cfc36-137">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="cfc36-137">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="cfc36-138">Binär</span><span class="sxs-lookup"><span data-stu-id="cfc36-138">Binary</span></span>|<span data-ttu-id="cfc36-139">Binärdaten</span><span class="sxs-lookup"><span data-stu-id="cfc36-139">Binary data</span></span>|
|<span data-ttu-id="cfc36-140">DWord</span><span class="sxs-lookup"><span data-stu-id="cfc36-140">DWord</span></span>|<span data-ttu-id="cfc36-141">Eine Zahl, die eine gültige UInt32 ist</span><span class="sxs-lookup"><span data-stu-id="cfc36-141">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="cfc36-142">ExpandString</span><span class="sxs-lookup"><span data-stu-id="cfc36-142">ExpandString</span></span>|<span data-ttu-id="cfc36-143">Eine Zeichenfolge, die Umgebungsvariablen enthalten kann, die dynamisch erweitert werden</span><span class="sxs-lookup"><span data-stu-id="cfc36-143">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="cfc36-144">MultiString</span><span class="sxs-lookup"><span data-stu-id="cfc36-144">MultiString</span></span>|<span data-ttu-id="cfc36-145">Eine mehrzeilige Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="cfc36-145">A multiline string</span></span>|
|<span data-ttu-id="cfc36-146">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="cfc36-146">String</span></span>|<span data-ttu-id="cfc36-147">Ein beliebiger Zeichenfolgenwert</span><span class="sxs-lookup"><span data-stu-id="cfc36-147">Any string value</span></span>|
|<span data-ttu-id="cfc36-148">QWord</span><span class="sxs-lookup"><span data-stu-id="cfc36-148">QWord</span></span>|<span data-ttu-id="cfc36-149">8 Byte Binärdaten</span><span class="sxs-lookup"><span data-stu-id="cfc36-149">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="cfc36-150">Sie können einen Registrierungseintrag zu mehreren Speicherorten hinzufügen, indem Sie ein Array von Werten für den Parameter **Path** angeben:</span><span class="sxs-lookup"><span data-stu-id="cfc36-150">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

<span data-ttu-id="cfc36-151">Sie können auch einen bereits vorhandenen Registrierungseintragswert überschreiben, indem Sie den Parameter **Force** an einen beliebigen **New-ItemProperty**-Befehl anfügen.</span><span class="sxs-lookup"><span data-stu-id="cfc36-151">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any **New-ItemProperty** command.</span></span>

### <a name="renaming-registry-entries"></a><span data-ttu-id="cfc36-152">Umbenennen von Registrierungseinträgen</span><span class="sxs-lookup"><span data-stu-id="cfc36-152">Renaming Registry Entries</span></span>

<span data-ttu-id="cfc36-153">Um den Eintrag **PowerShellPath** in „PSHome“ umzubenennen, verwenden Sie **Rename-ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="cfc36-153">To rename the **PowerShellPath** entry to "PSHome," use **Rename-ItemProperty**:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="cfc36-154">Um den umbenannten Wert anzuzeigen, fügen Sie dem Befehl den Parameter **PassThru** hinzu.</span><span class="sxs-lookup"><span data-stu-id="cfc36-154">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a><span data-ttu-id="cfc36-155">Löschen von Registrierungseinträgen</span><span class="sxs-lookup"><span data-stu-id="cfc36-155">Deleting Registry Entries</span></span>

<span data-ttu-id="cfc36-156">Um die Registrierungseinträge „PSHome“ und „PowerShellPath“ zu löschen, verwenden Sie **Remove-ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="cfc36-156">To delete both the PSHome and PowerShellPath registry entries, use **Remove-ItemProperty**:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```