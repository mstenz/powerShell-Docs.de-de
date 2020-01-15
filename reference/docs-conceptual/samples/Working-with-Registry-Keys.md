---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Arbeiten mit Registrierungsschlüsseln
ms.openlocfilehash: 3feaf6d26db51a507434a6cec1f1095c9013efc8
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736844"
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="61d2e-103">Arbeiten mit Registrierungsschlüsseln</span><span class="sxs-lookup"><span data-stu-id="61d2e-103">Working with Registry Keys</span></span>

<span data-ttu-id="61d2e-104">Registrierungsschlüssel sind Elemente auf PowerShell-Laufwerken, deshalb gleicht deren Verwendung der Arbeit mit Dateien und Ordnern.</span><span class="sxs-lookup"><span data-stu-id="61d2e-104">Because registry keys are items on PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="61d2e-105">Ein wichtiger Unterschied besteht darin, dass jedes Element auf einem registrierungsbasierten PowerShell-Laufwerk ein Container ist, genau wie ein Ordner auf einem Dateisystemlaufwerk.</span><span class="sxs-lookup"><span data-stu-id="61d2e-105">One critical difference is that every item on a registry-based PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="61d2e-106">Registrierungseinträge und deren zugehörige Werte sind jedoch Eigenschaften der Elemente, nicht unterschiedliche Elemente.</span><span class="sxs-lookup"><span data-stu-id="61d2e-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

## <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="61d2e-107">Auflisten aller Unterschlüssel eines Registrierungsschlüssels</span><span class="sxs-lookup"><span data-stu-id="61d2e-107">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="61d2e-108">Mit `Get-ChildItem` können Sie alle Elemente anzeigen, die sich direkt in einem Registrierungsschlüssel befinden.</span><span class="sxs-lookup"><span data-stu-id="61d2e-108">You can show all items directly within a registry key by using `Get-ChildItem`.</span></span> <span data-ttu-id="61d2e-109">Fügen Sie den optionalen Parameter **Force** hinzu, um ausgeblendete oder Systemelemente anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="61d2e-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="61d2e-110">Dieser Befehl zeigt z. B. die Elemente an, die sich direkt auf dem PowerShell-Laufwerk `HKCU:` befinden, das der Registrierungsstruktur `HKEY_CURRENT_USER` entspricht:</span><span class="sxs-lookup"><span data-stu-id="61d2e-110">For example, this command displays the items directly within PowerShell drive `HKCU:`, which corresponds to the `HKEY_CURRENT_USER` registry hive:</span></span>

```powershell
Get-ChildItem -Path HKCU:\ | Select-Object Name
```

```Output
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

Name
----
HKEY_CURRENT_USER\AppEvents
HKEY_CURRENT_USER\Console
HKEY_CURRENT_USER\Control Panel
HKEY_CURRENT_USER\DirectShow
HKEY_CURRENT_USER\dummy
HKEY_CURRENT_USER\Environment
HKEY_CURRENT_USER\EUDC
HKEY_CURRENT_USER\Keyboard Layout
HKEY_CURRENT_USER\MediaFoundation
HKEY_CURRENT_USER\Microsoft
HKEY_CURRENT_USER\Network
HKEY_CURRENT_USER\Printers
HKEY_CURRENT_USER\Software
HKEY_CURRENT_USER\System
HKEY_CURRENT_USER\Uninstall
HKEY_CURRENT_USER\WXP
HKEY_CURRENT_USER\Volatile Environment
```

<span data-ttu-id="61d2e-111">Dies sind die im Registrierungs-Editor (Regedit.exe) unter `HKEY_CURRENT_USER` angezeigten Schlüssel der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="61d2e-111">These are the top-level keys visible under `HKEY_CURRENT_USER` in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="61d2e-112">Sie können diesen Registrierungspfad auch anhand des Namens des Registrierungsanbieters gefolgt von `::` angeben.</span><span class="sxs-lookup"><span data-stu-id="61d2e-112">You can also specify this registry path by specifying the registry provider's name, followed by `::`.</span></span> <span data-ttu-id="61d2e-113">Der vollständige Name des Registrierungsanbieters lautet `Microsoft.PowerShell.Core\Registry`, aber dieser kann auf `Registry` verkürzt werden.</span><span class="sxs-lookup"><span data-stu-id="61d2e-113">The registry provider's full name is `Microsoft.PowerShell.Core\Registry`, but this can be shortened to just `Registry`.</span></span> <span data-ttu-id="61d2e-114">Jeder der folgenden Befehle listet die Inhalte direkt unter `HKCU:` auf.</span><span class="sxs-lookup"><span data-stu-id="61d2e-114">Any of the following commands will list the contents directly under `HKCU:`.</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="61d2e-115">Diese Befehle listen nur die direkt enthaltenen Elemente auf, ähnlich dem Befehl `DIR` in **Cmd.exe** oder `ls` in einer UNIX-Shell.</span><span class="sxs-lookup"><span data-stu-id="61d2e-115">These commands list only the directly contained items, much like using `DIR` in **Cmd.exe** or `ls` in a UNIX shell.</span></span> <span data-ttu-id="61d2e-116">Um enthaltene Elemente anzuzeigen, müssen Sie den Parameter **Recurse** angeben.</span><span class="sxs-lookup"><span data-stu-id="61d2e-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="61d2e-117">Um alle Registrierungsschlüssel in `HKCU:` aufzulisten, verwenden Sie den folgenden Befehl.</span><span class="sxs-lookup"><span data-stu-id="61d2e-117">To list all registry keys in `HKCU:`, use the following command.</span></span>

```powershell
Get-ChildItem -Path HKCU:\ -Recurse
```

<span data-ttu-id="61d2e-118">`Get-ChildItem` stellt mit den Parametern **Path**, **Filter**, **Include** und **Exclude** komplexe Filterfunktionen zur Verfügung, die allerdings typischerweise nur auf Namen basieren.</span><span class="sxs-lookup"><span data-stu-id="61d2e-118">`Get-ChildItem` can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="61d2e-119">Zum Durchführen einer komplexen Filterung basierend auf anderen Eigenschaften von Elementen können Sie das Cmdlet `Where-Object` verwenden.</span><span class="sxs-lookup"><span data-stu-id="61d2e-119">You can perform complex filtering based on other properties of items by using the `Where-Object` cmdlet.</span></span> <span data-ttu-id="61d2e-120">Der folgende Befehl sucht alle Schlüssel in `HKCU:\Software`, die nicht mehr als einen Unterschlüssel und zudem genau vier Werte enthalten:</span><span class="sxs-lookup"><span data-stu-id="61d2e-120">The following command finds all keys within `HKCU:\Software` that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse |
  Where-Object {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a><span data-ttu-id="61d2e-121">Kopieren von Schlüsseln</span><span class="sxs-lookup"><span data-stu-id="61d2e-121">Copying Keys</span></span>

<span data-ttu-id="61d2e-122">Das Kopieren erfolgt mit `Copy-Item`.</span><span class="sxs-lookup"><span data-stu-id="61d2e-122">Copying is done with `Copy-Item`.</span></span> <span data-ttu-id="61d2e-123">Das folgende Beispiel kopiert den `CurrentVersion`-Unterschlüssel von `HKLM:\SOFTWARE\Microsoft\Windows\` und alle zugehörigen Eigenschaften nach `HKCU:\`.</span><span class="sxs-lookup"><span data-stu-id="61d2e-123">The following example copies the `CurrentVersion` subkey of `HKLM:\SOFTWARE\Microsoft\Windows\` and all of its properties to `HKCU:\`.</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU:
```

<span data-ttu-id="61d2e-124">Wenn Sie diesen neuen Schlüssel im Registrierungs-Editor oder über `Get-ChildItem` untersuchen, stellen Sie fest, dass am neuen Speicherort keine Kopien der enthaltenen Unterschlüssel vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="61d2e-124">If you examine this new key in the registry editor or by using `Get-ChildItem`, you notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="61d2e-125">Um den gesamten Inhalt eines Containers zu kopieren, müssen Sie den Parameter **Recurse** angeben.</span><span class="sxs-lookup"><span data-stu-id="61d2e-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="61d2e-126">Um den vorherigen Kopierbefehl rekursiv zu machen, verwenden Sie diesen Befehl:</span><span class="sxs-lookup"><span data-stu-id="61d2e-126">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU: -Recurse
```

<span data-ttu-id="61d2e-127">Sie können auch weiterhin andere bereits verfügbare Tools verwenden, um Dateisystemkopien auszuführen.</span><span class="sxs-lookup"><span data-stu-id="61d2e-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="61d2e-128">Alle Tools zur Bearbeitung der Registrierung – darunter **reg.exe**, **regini.exe**, **regedit.exe** – sowie COM-Objekte, die die Bearbeitung der Registrierung unterstützen (z. B. **WScript.Shell** und die WMI-Klasse **StdRegProv**) können in Windows PowerShell verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="61d2e-128">Any registry editing tools—including **reg.exe**, **regini.exe**, **regedit.exe**, and COM objects that support registry editing, such as **WScript.Shell** and WMI's **StdRegProv** class can be used from within Windows PowerShell.</span></span>

## <a name="creating-keys"></a><span data-ttu-id="61d2e-129">Erstellen von Schlüsseln</span><span class="sxs-lookup"><span data-stu-id="61d2e-129">Creating Keys</span></span>

<span data-ttu-id="61d2e-130">Das Erstellen neuer Schlüssel in der Registrierung ist einfacher als das Erstellen eines neuen Elements in einem Dateisystem.</span><span class="sxs-lookup"><span data-stu-id="61d2e-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="61d2e-131">Da alle Registrierungsschlüssel Container sind, müssen Sie keinen Elementtyp, sondern einfach einen expliziten Pfad angeben, z. B.:</span><span class="sxs-lookup"><span data-stu-id="61d2e-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path HKCU:\Software_DeleteMe
```

<span data-ttu-id="61d2e-132">Sie können auch einen anbieterbasierten Pfad verwenden, um einen Schlüssel anzugeben:</span><span class="sxs-lookup"><span data-stu-id="61d2e-132">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU\Software_DeleteMe
```

## <a name="deleting-keys"></a><span data-ttu-id="61d2e-133">Löschen von Schlüsseln</span><span class="sxs-lookup"><span data-stu-id="61d2e-133">Deleting Keys</span></span>

<span data-ttu-id="61d2e-134">Das Löschen von Elementen funktioniert im Wesentlichen für alle Anbieter gleich.</span><span class="sxs-lookup"><span data-stu-id="61d2e-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="61d2e-135">Die folgenden Befehle entfernen Elemente automatisch ohne Benutzereingriff:</span><span class="sxs-lookup"><span data-stu-id="61d2e-135">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path HKCU:\Software_DeleteMe
Remove-Item -Path 'HKCU:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="61d2e-136">Entfernen aller Schlüssel unter einem bestimmten Schlüssel</span><span class="sxs-lookup"><span data-stu-id="61d2e-136">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="61d2e-137">Mit `Remove-Item` können Sie enthaltene Elemente entfernen. Sie werden jedoch aufgefordert, das Entfernen zu bestätigen, wenn ein Element weitere Elemente enthält.</span><span class="sxs-lookup"><span data-stu-id="61d2e-137">You can remove contained items by using `Remove-Item`, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="61d2e-138">Wenn Sie beispielsweise versuchen, den erstellten Unterschlüssel `HKCU:\CurrentVersion` zu löschen, wird Folgendes angezeigt:</span><span class="sxs-lookup"><span data-stu-id="61d2e-138">For example, if we attempt to delete the `HKCU:\CurrentVersion` subkey we created, we see this:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion
```

```Output
Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="61d2e-139">Um enthaltene Elemente ohne Rückfrage zu löschen, geben Sie den Parameter **Recurse** an:</span><span class="sxs-lookup"><span data-stu-id="61d2e-139">To delete contained items without prompting, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="61d2e-140">Wenn Sie alle Elemente in `HKCU:\CurrentVersion`, aber `HKCU:\CurrentVersion` selbst nicht löschen möchten, verwenden Sie stattdessen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="61d2e-140">If you wanted to remove all items within `HKCU:\CurrentVersion` but not `HKCU:\CurrentVersion` itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
