---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Arbeiten mit Registrierungsschlüsseln
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: e7b497ec2fccf9ba3934439a9c1e9be3cf70a705
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293196"
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="6f82f-103">Arbeiten mit Registrierungsschlüsseln</span><span class="sxs-lookup"><span data-stu-id="6f82f-103">Working with Registry Keys</span></span>

<span data-ttu-id="6f82f-104">Da Registrierungsschlüssel Elemente auf Windows PowerShell-Laufwerken sind, gleicht deren Verwendung der Arbeit mit Dateien und Ordnern.</span><span class="sxs-lookup"><span data-stu-id="6f82f-104">Because registry keys are items on Windows PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="6f82f-105">Ein wichtiger Unterschied besteht darin, dass jedes Element auf einem registrierungsbasierten Windows PowerShell-Laufwerk ein Container ist, genau wie ein Ordner auf einem Dateisystemlaufwerk.</span><span class="sxs-lookup"><span data-stu-id="6f82f-105">One critical difference is that every item on a registry-based Windows PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="6f82f-106">Registrierungseinträge und deren zugehörige Werte sind jedoch Eigenschaften der Elemente, nicht unterschiedliche Elemente.</span><span class="sxs-lookup"><span data-stu-id="6f82f-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

## <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="6f82f-107">Auflisten aller Unterschlüssel eines Registrierungsschlüssels</span><span class="sxs-lookup"><span data-stu-id="6f82f-107">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="6f82f-108">Mit **Get-ChildItem** können Sie alle Elemente anzeigen, die sich unmittelbar in einem Registrierungsschlüssel befinden.</span><span class="sxs-lookup"><span data-stu-id="6f82f-108">You can show all items directly within a registry key by using **Get-ChildItem**.</span></span> <span data-ttu-id="6f82f-109">Fügen Sie den optionalen Parameter **Force** hinzu, um ausgeblendete oder Systemelemente anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="6f82f-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="6f82f-110">Dieser Befehl zeigt z.B. die Elemente an, die sich direkt auf dem Windows PowerShell-Laufwerk HKCU: befinden, das der Registrierungsstruktur HKEY_CURRENT_USER entspricht:</span><span class="sxs-lookup"><span data-stu-id="6f82f-110">For example, this command displays the items directly within Windows PowerShell drive HKCU:, which corresponds to the HKEY_CURRENT_USER registry hive:</span></span>

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

<span data-ttu-id="6f82f-111">Dies sind die im Registrierungs-Editor (Regedit.exe) unter HKEY_CURRENT_USER angezeigten Schlüssel der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="6f82f-111">These are the top-level keys visible under HKEY_CURRENT_USER in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="6f82f-112">Sie können diesen Registrierungspfad auch anhand des Namens des Registrierungsanbieters, gefolgt von „**::**“ angeben.</span><span class="sxs-lookup"><span data-stu-id="6f82f-112">You can also specify this registry path by specifying the registry provider's name, followed by "**::**".</span></span> <span data-ttu-id="6f82f-113">Der vollständige Name des Registrierungsanbieters lautet **Microsoft.PowerShell.Core\\Registry**, aber er kann auf **Registry** verkürzt werden.</span><span class="sxs-lookup"><span data-stu-id="6f82f-113">The registry provider's full name is **Microsoft.PowerShell.Core\\Registry**, but this can be shortened to just **Registry**.</span></span> <span data-ttu-id="6f82f-114">Jeder der folgenden Befehle listet die Inhalte direkt unter HKCU auf:</span><span class="sxs-lookup"><span data-stu-id="6f82f-114">Any of the following commands will list the contents directly under HKCU:</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="6f82f-115">Diese Befehle listen nur die Elemente auf, die sich unmittelbar unter HKCU: befinden, ähnlich dem „Cmd.exe“-Befehl **DIR** oder **ls** in einer UNIX-Shell.</span><span class="sxs-lookup"><span data-stu-id="6f82f-115">These commands list only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="6f82f-116">Um enthaltene Elemente anzuzeigen, müssen Sie den Parameter **Recurse** angeben.</span><span class="sxs-lookup"><span data-stu-id="6f82f-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="6f82f-117">Um alle Registrierungsschlüssel in HKCU aufzulisten, verwenden Sie den folgenden Befehl (dieser Vorgang kann extrem lange dauern):</span><span class="sxs-lookup"><span data-stu-id="6f82f-117">To list all registry keys in HKCU, use the following command (This operation can take an extremely long time.):</span></span>

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

<span data-ttu-id="6f82f-118">**Get-ChildItem** stellt mit den Parametern **Path**, **Filter**, **Include** und **Exclude** komplexe Filterfunktionen zur Verfügung, die allerdings nur auf Namen basieren.</span><span class="sxs-lookup"><span data-stu-id="6f82f-118">**Get-ChildItem** can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="6f82f-119">Zum Durchführen einer komplexen Filterung basierend auf anderen Eigenschaften verwenden Sie das Cmdlet **Where-Object**.</span><span class="sxs-lookup"><span data-stu-id="6f82f-119">You can perform complex filtering based on other properties of items by using the **Where-Object** cmdlet.</span></span> <span data-ttu-id="6f82f-120">Der folgende Befehl sucht alle Schlüssel in „HKCU:\\Software“, die nicht mehr als einen Unterschlüssel und zudem genau vier Werte enthalten:</span><span class="sxs-lookup"><span data-stu-id="6f82f-120">The following command finds all keys within HKCU:\\Software that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a><span data-ttu-id="6f82f-121">Kopieren von Schlüsseln</span><span class="sxs-lookup"><span data-stu-id="6f82f-121">Copying Keys</span></span>

<span data-ttu-id="6f82f-122">Das Kopieren erfolgt mit **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="6f82f-122">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="6f82f-123">Der folgende Befehl kopiert „HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion“ und alle zugehörigen Eigenschaften nach „HKCU:\\“ und erstellt dabei einen neuen Schlüssel mit dem Namen „CurrentVersion“:</span><span class="sxs-lookup"><span data-stu-id="6f82f-123">The following command copies HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion and all of its properties to HKCU:\\, creating a new key named "CurrentVersion":</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

<span data-ttu-id="6f82f-124">Wenn Sie diesen neuen Schlüssel im Registrierungs-Editor oder über **Get-ChildItem** untersuchen, stellen Sie fest, dass am neuen Speicherort keine Kopien der enthaltenen Unterschlüssel vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="6f82f-124">If you examine this new key in the registry editor or by using **Get-ChildItem**, you will notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="6f82f-125">Um den gesamten Inhalt eines Containers zu kopieren, müssen Sie den Parameter **Recurse** angeben.</span><span class="sxs-lookup"><span data-stu-id="6f82f-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="6f82f-126">Um den vorherigen Kopierbefehl rekursiv zu machen, verwenden Sie diesen Befehl:</span><span class="sxs-lookup"><span data-stu-id="6f82f-126">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

<span data-ttu-id="6f82f-127">Sie können auch weiterhin andere bereits verfügbare Tools verwenden, um Dateisystemkopien auszuführen.</span><span class="sxs-lookup"><span data-stu-id="6f82f-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="6f82f-128">Alle Tools zur Bearbeitung der Registrierung (z. B. „reg.exe“, „regini.exe“ und „regedit.exe“) sowie COM-Objekte, die die Bearbeitung der Registrierung unterstützen (z. B. „WScript.Shell“ und die WMI-Klasse „StdRegProv“) können in Windows PowerShell verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="6f82f-128">Any registry editing tools—including reg.exe, regini.exe, and regedit.exe—and COM objects that support registry editing (such as WScript.Shell and WMI's StdRegProv class) can be used from within Windows PowerShell.</span></span>

## <a name="creating-keys"></a><span data-ttu-id="6f82f-129">Erstellen von Schlüsseln</span><span class="sxs-lookup"><span data-stu-id="6f82f-129">Creating Keys</span></span>

<span data-ttu-id="6f82f-130">Das Erstellen neuer Schlüssel in der Registrierung ist einfacher als das Erstellen eines neuen Elements in einem Dateisystem.</span><span class="sxs-lookup"><span data-stu-id="6f82f-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="6f82f-131">Da alle Registrierungsschlüssel Container sind, müssen Sie keinen Elementtyp, sondern einfach einen expliziten Pfad angeben, z. B.:</span><span class="sxs-lookup"><span data-stu-id="6f82f-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

<span data-ttu-id="6f82f-132">Sie können auch einen anbieterbasierten Pfad verwenden, um einen Schlüssel anzugeben:</span><span class="sxs-lookup"><span data-stu-id="6f82f-132">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

## <a name="deleting-keys"></a><span data-ttu-id="6f82f-133">Löschen von Schlüsseln</span><span class="sxs-lookup"><span data-stu-id="6f82f-133">Deleting Keys</span></span>

<span data-ttu-id="6f82f-134">Das Löschen von Elementen funktioniert im Wesentlichen für alle Anbieter gleich.</span><span class="sxs-lookup"><span data-stu-id="6f82f-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="6f82f-135">Die folgenden Befehle entfernen Elemente automatisch ohne Benutzereingriff:</span><span class="sxs-lookup"><span data-stu-id="6f82f-135">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="6f82f-136">Entfernen aller Schlüssel unter einem bestimmten Schlüssel</span><span class="sxs-lookup"><span data-stu-id="6f82f-136">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="6f82f-137">Mit **Remove-Item** können Sie enthaltene Elemente entfernen. Wenn ein Element weitere Elemente enthält, werden Sie jedoch aufgefordert, das Entfernen zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="6f82f-137">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="6f82f-138">Wenn Sie z.B. versuchen, den erstellten Unterschlüssel „HKCU:\\CurrentVersion“ zu löschen, wird Folgendes angezeigt:</span><span class="sxs-lookup"><span data-stu-id="6f82f-138">For example, if we attempt to delete the HKCU:\\CurrentVersion subkey we created, we see this:</span></span>

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="6f82f-139">Um enthaltene Elemente ohne Rückfrage zu löschen, geben Sie den Parameter **-Recurse** an:</span><span class="sxs-lookup"><span data-stu-id="6f82f-139">To delete contained items without prompting, specify the **-Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="6f82f-140">Wenn Sie alle Elemente in „HKCU:\\CurrentVersion“ löschen möchten, aber nicht „HKCU:\\CurrentVersion“ selbst, könnten Sie stattdessen Folgenden Befehl verwenden:</span><span class="sxs-lookup"><span data-stu-id="6f82f-140">If you wanted to remove all items within HKCU:\\CurrentVersion but not HKCU:\\CurrentVersion itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```