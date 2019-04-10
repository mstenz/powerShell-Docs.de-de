---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Arbeiten mit Registrierungseinträgen
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 667d17d0d62745a27ffef5f1912336b72f74c2a9
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293077"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="badc2-103">Arbeiten mit Registrierungseinträgen</span><span class="sxs-lookup"><span data-stu-id="badc2-103">Working with Registry Entries</span></span>

<span data-ttu-id="badc2-104">Da Registrierungseinträge Eigenschaften von Schlüsseln sind und daher nicht direkt gesucht werden können, muss für die Arbeit mit diesen ein etwas anderer Ansatz gewählt werden.</span><span class="sxs-lookup"><span data-stu-id="badc2-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

## <a name="listing-registry-entries"></a><span data-ttu-id="badc2-105">Auflisten von Registrierungseinträgen</span><span class="sxs-lookup"><span data-stu-id="badc2-105">Listing Registry Entries</span></span>

<span data-ttu-id="badc2-106">Es gibt viele verschiedene Möglichkeiten zum Untersuchen von Registrierungseinträgen.</span><span class="sxs-lookup"><span data-stu-id="badc2-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="badc2-107">Am einfachsten ist es, die Eigenschaftennamen mit einem Schlüssel zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="badc2-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="badc2-108">Wenn Sie beispielsweise die Namen der Einträge im Registrierungsschlüssel `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion` anzeigen möchten, verwenden Sie `Get-Item`.</span><span class="sxs-lookup"><span data-stu-id="badc2-108">For example, to see the names of the entries in the registry key `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, use `Get-Item`.</span></span> <span data-ttu-id="badc2-109">Registrierungsschlüssel verfügen über eine Eigenschaft mit dem generischen Namen „Property“, die eine Liste der Registrierungseinträge im Schlüssel ist.</span><span class="sxs-lookup"><span data-stu-id="badc2-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span>
<span data-ttu-id="badc2-110">Der folgende Befehl wählt die Eigenschaft „Property“ aus und erweitert die Elemente so, dass sie in einer Liste angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="badc2-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="badc2-111">Wenn Sie die Registrierungseinträge in einer besser lesbaren Form anzeigen möchten, verwenden Sie `Get-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="badc2-111">To view the registry entries in a more readable form, use `Get-ItemProperty`:</span></span>

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
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

<span data-ttu-id="badc2-112">Die Windows PowerShell-bezogenen Eigenschaften für den Schüssel verfügen alle über das Präfix „PS“, z.B. **PSPath**, **PSParentPath**, **PSChildName** und **PSProvider**.</span><span class="sxs-lookup"><span data-stu-id="badc2-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="badc2-113">Sie können die Notation `*.*` zum Verweisen auf den aktuellen Speicherort verwenden.</span><span class="sxs-lookup"><span data-stu-id="badc2-113">You can use the `*.*` notation for referring to the current location.</span></span> <span data-ttu-id="badc2-114">Sie können `Set-Location` verwenden, um zuerst in den Registrierungscontainer **CurrentVersion** zu wechseln:</span><span class="sxs-lookup"><span data-stu-id="badc2-114">You can use `Set-Location` to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="badc2-115">Alternativ dazu können Sie das integrierte HKLM PSDrive mit `Set-Location` verwenden:</span><span class="sxs-lookup"><span data-stu-id="badc2-115">Alternatively, you can use the built-in HKLM PSDrive with `Set-Location`:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="badc2-116">Anschließend können Sie die Notation `*.*` für den aktuellen Speicherort verwenden, um die Eigenschaften aufzulisten, ohne einen vollständigen Pfad anzugeben:</span><span class="sxs-lookup"><span data-stu-id="badc2-116">You can then use the `*.*` notation for the current location to list the properties without specifying a full path:</span></span>

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="badc2-117">Die Pfaderweiterung funktioniert genauso wie innerhalb des Dateisystems. Sie können daher von diesem Speicherort die Auflistung **ItemProperty** für `HKLM:\SOFTWARE\Microsoft\Windows\Help` abrufen, indem Sie `Get-ItemProperty -Path ..\Help` verwenden.</span><span class="sxs-lookup"><span data-stu-id="badc2-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for `HKLM:\SOFTWARE\Microsoft\Windows\Help` by using `Get-ItemProperty -Path ..\Help`.</span></span>

## <a name="getting-a-single-registry-entry"></a><span data-ttu-id="badc2-118">Abrufen eines einzelnen Registrierungseintrags</span><span class="sxs-lookup"><span data-stu-id="badc2-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="badc2-119">Wenn Sie einen bestimmten Eintrag in einem Registrierungsschlüssel abrufen möchten, stehen verschiedene Möglichkeiten zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="badc2-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="badc2-120">In diesem Beispiel wird der Wert von **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion` gesucht.</span><span class="sxs-lookup"><span data-stu-id="badc2-120">This example finds the value of **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

<span data-ttu-id="badc2-121">Verwenden Sie mit `Get-ItemProperty` den Parameter **Path**, um den Namen des Schlüssels anzugeben, und den Parameter **Name**, um den Namen des Eintrags **DevicePath** anzugeben.</span><span class="sxs-lookup"><span data-stu-id="badc2-121">Using `Get-ItemProperty`, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="badc2-122">Dieser Befehl gibt die standardmäßigen Windows PowerShell-Eigenschaften sowie die Eigenschaft **DevicePath** aus.</span><span class="sxs-lookup"><span data-stu-id="badc2-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="badc2-123">Obwohl `Get-ItemProperty` die Parameter **Filter**, **Include** und **Exclude** aufweist, können sie nicht zum Filtern nach dem Namen der Eigenschaft verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="badc2-123">Although `Get-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="badc2-124">Diese Parameter verweisen auf Registrierungsschlüssel, die Elementpfade und keine Registrierungseinträge sind.</span><span class="sxs-lookup"><span data-stu-id="badc2-124">These parameters refer to registry keys, which are item paths and not registry entries.</span></span> <span data-ttu-id="badc2-125">Registrierungseinträge sind Elementeigenschaften.</span><span class="sxs-lookup"><span data-stu-id="badc2-125">Registry entries which are item properties.</span></span>

<span data-ttu-id="badc2-126">Eine weitere Option ist die Verwendung des Befehlszeilentools „Reg.exe“.</span><span class="sxs-lookup"><span data-stu-id="badc2-126">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="badc2-127">Um Hilfe zu „reg.exe“ zu erhalten, geben Sie an einer Eingabeaufforderung `reg.exe /?` ein.</span><span class="sxs-lookup"><span data-stu-id="badc2-127">For help with reg.exe, type `reg.exe /?` at a command prompt.</span></span> <span data-ttu-id="badc2-128">Mithilfe von „reg.exe“ finden Sie den Eintrag „DevicePath“, wie im folgenden Befehl gezeigt:</span><span class="sxs-lookup"><span data-stu-id="badc2-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="badc2-129">(Sie können das COM-Objekt **WshShell** auch zum Suchen bestimmter Registrierungseinträge verwenden, obwohl diese Methode mit großen Binärdaten oder mit Registrierungseintragsnamen, die Zeichen wie „\\“ enthalten, nicht funktioniert.)</span><span class="sxs-lookup"><span data-stu-id="badc2-129">You can also use the **WshShell** COM object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="badc2-130">Fügen Sie den Namen der Eigenschaft mit einem \\-Trennzeichen zum Elementpfad hinzu:</span><span class="sxs-lookup"><span data-stu-id="badc2-130">Append the property name to the item path with a \\ separator:</span></span>

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a><span data-ttu-id="badc2-131">Festlegen eines einzelnen Registrierungseintrags</span><span class="sxs-lookup"><span data-stu-id="badc2-131">Setting a Single Registry Entry</span></span>

<span data-ttu-id="badc2-132">Wenn Sie einen bestimmten Eintrag in einem Registrierungsschlüssel ändern möchten, stehen Ihnen verschiedene Möglichkeiten zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="badc2-132">If you want to change a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="badc2-133">In diesem Beispiel wird der Eintrag **Path** unter `HKEY_CURRENT_USER\Environment` geändert.</span><span class="sxs-lookup"><span data-stu-id="badc2-133">This example modifies the **Path** entry under `HKEY_CURRENT_USER\Environment`.</span></span> <span data-ttu-id="badc2-134">Der Eintrag **Path** gibt an, wo ausführbare Dateien zu finden sind.</span><span class="sxs-lookup"><span data-stu-id="badc2-134">The **Path** entry specifies where to find executable files.</span></span>

1. <span data-ttu-id="badc2-135">Rufen Sie den aktuellen Wert des Eintrags **Path** mit `Get-ItemProperty` ab.</span><span class="sxs-lookup"><span data-stu-id="badc2-135">Retrieve the current value of the **Path** entry using `Get-ItemProperty`.</span></span>
2. <span data-ttu-id="badc2-136">Fügen Sie den neuen Wert hinzu, und trennen Sie ihn mit `;`.</span><span class="sxs-lookup"><span data-stu-id="badc2-136">Add the new value, separating it with a `;`.</span></span>
3. <span data-ttu-id="badc2-137">Verwenden Sie `Set-ItemProperty` mit dem angegebenen Schlüssel, Eintragsnamen und Wert, um den Registrierungseintrag zu ändern.</span><span class="sxs-lookup"><span data-stu-id="badc2-137">Use `Set-ItemProperty` with the specified key, entry name, and value to modify the registry entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> <span data-ttu-id="badc2-138">Obwohl `Set-ItemProperty` die Parameter **Filter**, **Include** und **Exclude** aufweist, können sie nicht zum Filtern nach dem Namen der Eigenschaft verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="badc2-138">Although `Set-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="badc2-139">Diese Parameter verweisen auf Registrierungsschlüssel (das sind Elementpfade und keine Registrierungseinträge), die Elementeigenschaften sind.</span><span class="sxs-lookup"><span data-stu-id="badc2-139">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="badc2-140">Eine weitere Option ist die Verwendung des Befehlszeilentools „Reg.exe“.</span><span class="sxs-lookup"><span data-stu-id="badc2-140">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="badc2-141">Um Hilfe zu „reg.exe“ zu erhalten, geben Sie **reg.exe /?** an einer Eingabeaufforderung ein.</span><span class="sxs-lookup"><span data-stu-id="badc2-141">For help with reg.exe, type **reg.exe /?**</span></span>
<span data-ttu-id="badc2-142">an einer Eingabeaufforderung.</span><span class="sxs-lookup"><span data-stu-id="badc2-142">at a command prompt.</span></span>

<span data-ttu-id="badc2-143">Im folgenden Beispiel wird der Eintrag **Path** geändert, indem der im vorstehenden Beispiel hinzugefügte Pfad entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="badc2-143">The following example changes the **Path** entry by removing the path added in the example above.</span></span>
`Get-ItemProperty` <span data-ttu-id="badc2-144">wird weiterhin zum Abrufen des aktuellen Werts verwendet, um zu vermeiden, dass die aus `reg query` zurückgegebene Zeichenfolge analysiert werden muss.</span><span class="sxs-lookup"><span data-stu-id="badc2-144">is still used to retrieve the current value to avoid having to parse the string returned from `reg query`.</span></span> <span data-ttu-id="badc2-145">Mit den Methoden **SubString** und **LastIndexOf** wird der letzte Pfad abgerufen, der dem Eintrag **Path** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="badc2-145">The **SubString** and **LastIndexOf** methods are used to retrieve the last path added to the **Path** entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a><span data-ttu-id="badc2-146">Erstellen neuer Registrierungseinträge</span><span class="sxs-lookup"><span data-stu-id="badc2-146">Creating New Registry Entries</span></span>

<span data-ttu-id="badc2-147">Verwenden Sie `New-ItemProperty` mit dem Pfad zum Schüssel, dem Eintragsnamen und dem Wert des Eintrags, um einen neuen Eintrag namens „PowerShellPath“ zum Schlüssel **CurrentVersion** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="badc2-147">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use `New-ItemProperty` with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="badc2-148">In diesem Beispiel wird der Wert der Windows PowerShell-Variablen `$PSHome` verwendet, in der der Pfad zum Installationsverzeichnis für Windows PowerShell gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="badc2-148">For this example, we will take the value of the Windows PowerShell variable `$PSHome`, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="badc2-149">Sie können dem Schlüssel mit Hilfe des folgenden Befehls den neuen Eintrag hinzufügen, und der Befehl gibt auch Informationen zu dem neuen Eintrag zurück:</span><span class="sxs-lookup"><span data-stu-id="badc2-149">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="badc2-150">**PropertyType** muss der Namen eines **Microsoft.Win32.RegistryValueKind**-Aufzählungselements aus der folgenden Tabelle sein:</span><span class="sxs-lookup"><span data-stu-id="badc2-150">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="badc2-151">PropertyType-Wert</span><span class="sxs-lookup"><span data-stu-id="badc2-151">PropertyType Value</span></span>|<span data-ttu-id="badc2-152">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="badc2-152">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="badc2-153">Binär</span><span class="sxs-lookup"><span data-stu-id="badc2-153">Binary</span></span>|<span data-ttu-id="badc2-154">Binärdaten</span><span class="sxs-lookup"><span data-stu-id="badc2-154">Binary data</span></span>|
|<span data-ttu-id="badc2-155">DWord</span><span class="sxs-lookup"><span data-stu-id="badc2-155">DWord</span></span>|<span data-ttu-id="badc2-156">Eine Zahl, die eine gültige UInt32 ist</span><span class="sxs-lookup"><span data-stu-id="badc2-156">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="badc2-157">ExpandString</span><span class="sxs-lookup"><span data-stu-id="badc2-157">ExpandString</span></span>|<span data-ttu-id="badc2-158">Eine Zeichenfolge, die Umgebungsvariablen enthalten kann, die dynamisch erweitert werden</span><span class="sxs-lookup"><span data-stu-id="badc2-158">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="badc2-159">MultiString</span><span class="sxs-lookup"><span data-stu-id="badc2-159">MultiString</span></span>|<span data-ttu-id="badc2-160">Eine mehrzeilige Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="badc2-160">A multiline string</span></span>|
|<span data-ttu-id="badc2-161">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="badc2-161">String</span></span>|<span data-ttu-id="badc2-162">Ein beliebiger Zeichenfolgenwert</span><span class="sxs-lookup"><span data-stu-id="badc2-162">Any string value</span></span>|
|<span data-ttu-id="badc2-163">QWord</span><span class="sxs-lookup"><span data-stu-id="badc2-163">QWord</span></span>|<span data-ttu-id="badc2-164">8 Byte Binärdaten</span><span class="sxs-lookup"><span data-stu-id="badc2-164">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="badc2-165">Sie können einen Registrierungseintrag zu mehreren Speicherorten hinzufügen, indem Sie ein Array von Werten für den Parameter **Path** angeben:</span><span class="sxs-lookup"><span data-stu-id="badc2-165">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="badc2-166">Sie können auch einen bereits vorhandenen Registrierungseintragswert überschreiben, indem Sie den Parameter **Force** an einen beliebigen `New-ItemProperty`-Befehl anfügen.</span><span class="sxs-lookup"><span data-stu-id="badc2-166">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any `New-ItemProperty` command.</span></span>

## <a name="renaming-registry-entries"></a><span data-ttu-id="badc2-167">Umbenennen von Registrierungseinträgen</span><span class="sxs-lookup"><span data-stu-id="badc2-167">Renaming Registry Entries</span></span>

<span data-ttu-id="badc2-168">Verwenden Sie `Rename-ItemProperty`, um den Eintrag **PowerShellPath** in „PSHome“ umzubenennen:</span><span class="sxs-lookup"><span data-stu-id="badc2-168">To rename the **PowerShellPath** entry to "PSHome," use `Rename-ItemProperty`:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="badc2-169">Um den umbenannten Wert anzuzeigen, fügen Sie dem Befehl den Parameter **PassThru** hinzu.</span><span class="sxs-lookup"><span data-stu-id="badc2-169">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a><span data-ttu-id="badc2-170">Löschen von Registrierungseinträgen</span><span class="sxs-lookup"><span data-stu-id="badc2-170">Deleting Registry Entries</span></span>

<span data-ttu-id="badc2-171">Verwenden Sie `Remove-ItemProperty`, um die Registrierungseinträge „PSHome“ und „PowerShellPath“ zu löschen:</span><span class="sxs-lookup"><span data-stu-id="badc2-171">To delete both the PSHome and PowerShellPath registry entries, use `Remove-ItemProperty`:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
