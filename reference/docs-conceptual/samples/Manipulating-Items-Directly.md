---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Direktes Verarbeiten von Elementen
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: 4caa7d2e0eecff9783556062d8503fe10e616fe5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086220"
---
# <a name="manipulating-items-directly"></a><span data-ttu-id="d3021-103">Direktes Verarbeiten von Elementen</span><span class="sxs-lookup"><span data-stu-id="d3021-103">Manipulating Items Directly</span></span>

<span data-ttu-id="d3021-104">Die Elemente, die Sie in Windows PowerShell-Laufwerken sehen, z. B. Dateien und Ordner auf den Dateisystemlaufwerken, sowie die Registrierungsschlüssel in den Windows PowerShell-Registrierungslaufwerken werden in Windows PowerShell als *Elemente* (Items) bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="d3021-104">The elements that you see in Windows PowerShell drives, such as the files and folders in the file system drives, and the registry keys in the Windows PowerShell registry drives, are called *items* in Windows PowerShell.</span></span> <span data-ttu-id="d3021-105">Die Cmdlets zum Arbeiten mit diesen Elementen haben das Substantiv **Item** in ihren Namen.</span><span class="sxs-lookup"><span data-stu-id="d3021-105">The cmdlets for working with them item have the noun **Item** in their names.</span></span>

<span data-ttu-id="d3021-106">Die Ausgabe des Befehls **Get-Command -Noun Item** zeigt, dass es neun Windows PowerShell-Item-Cmdlets gibt.</span><span class="sxs-lookup"><span data-stu-id="d3021-106">The output of the **Get-Command -Noun Item** command shows that there are nine Windows PowerShell item cmdlets.</span></span>

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

## <a name="creating-new-items-new-item"></a><span data-ttu-id="d3021-107">Erstellen von neuen Elementen (New-Item)</span><span class="sxs-lookup"><span data-stu-id="d3021-107">Creating New Items (New-Item)</span></span>

<span data-ttu-id="d3021-108">Um ein neues Element im Dateisystem zu erstellen, verwenden Sie das Cmdlet **New-Item**.</span><span class="sxs-lookup"><span data-stu-id="d3021-108">To create a new item in the file system, use the **New-Item** cmdlet.</span></span> <span data-ttu-id="d3021-109">Fügen Sie den **Path**-Parameter mit dem Pfad zum Element und den **ItemType**-Parameter mit dem Wert „file“ oder „directory“ ein.</span><span class="sxs-lookup"><span data-stu-id="d3021-109">Include the **Path** parameter with path to the item, and the **ItemType** parameter with a value of "file" or "directory".</span></span>

<span data-ttu-id="d3021-110">Wenn Sie beispielsweise ein neues Verzeichnis namens „New.Directory“ im Verzeichnis „C:\\Temp“ erstellen möchten, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="d3021-110">For example, to create a new directory named "New.Directory"in the C:\\Temp directory,  type:</span></span>

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

<span data-ttu-id="d3021-111">Um eine Datei zu erstellen, ändern Sie den Wert des **ItemType**-Parameters in „file“.</span><span class="sxs-lookup"><span data-stu-id="d3021-111">To create a file, change the value of the **ItemType** parameter to "file".</span></span> <span data-ttu-id="d3021-112">Möchten Sie z. B. eine Datei namens „file1.txt“ im Verzeichnis „New.Directory“ erstellen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="d3021-112">For example, to create a file named "file1.txt" in the New.Directory directory, type:</span></span>

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

<span data-ttu-id="d3021-113">Auf gleiche Weise können Sie einen neuen Registrierungsschlüssel erstellen.</span><span class="sxs-lookup"><span data-stu-id="d3021-113">You can use the same technique to create a new registry key.</span></span> <span data-ttu-id="d3021-114">Tatsächlich ist ein Registrierungsschlüssel einfacher zu erstellen, weil der einzige Elementtyp in der Windows-Registrierung ein Schlüssel ist.</span><span class="sxs-lookup"><span data-stu-id="d3021-114">In fact, a registry key is easier to create because the only item type in the Windows registry is a key.</span></span> <span data-ttu-id="d3021-115">(Registrierungseinträge sind Element-*Eigenschaften*.) Wenn Sie beispielsweise einen Schlüssel namens „_Test“ im „CurrentVersion“-Unterschlüssel erstellen möchten, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="d3021-115">(Registry entries are item *properties*.) For example, to create a key named "_Test" in the CurrentVersion subkey, type:</span></span>

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

<span data-ttu-id="d3021-116">Wenn Sie einen Registrierungspfad eingeben, müssen Sie den Doppelpunkt (**:**) in die Windows PowerShell-Laufwerksnamen, „HKLM:“ und „HKCU:“, einfügen.</span><span class="sxs-lookup"><span data-stu-id="d3021-116">When typing a registry path, be sure to include the colon (**:**) in the Windows PowerShell drive names, HKLM: and HKCU:.</span></span> <span data-ttu-id="d3021-117">Ohne den Doppelpunkt erkennt Windows PowerShell den Laufwerksnamen im Pfad nicht.</span><span class="sxs-lookup"><span data-stu-id="d3021-117">Without the colon, Windows PowerShell does not recognize the drive name in the path.</span></span>

## <a name="why-registry-values-are-not-items"></a><span data-ttu-id="d3021-118">Warum Registrierungswerte keine Elemente</span><span class="sxs-lookup"><span data-stu-id="d3021-118">Why Registry Values are not Items</span></span>

<span data-ttu-id="d3021-119">Wenn Sie mit dem Cmdlet **Get-ChildItem** nach den Elemente in einem Registrierungsschlüssel suchen, werden weder die tatsächlichen Registrierungseinträge noch deren Werte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d3021-119">When you use the **Get-ChildItem** cmdlet to find the items in a registry key, you will never see actual registry entries or their values.</span></span>

<span data-ttu-id="d3021-120">Beispielsweise enthält der Registrierungsschlüssel **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** in der Regel mehrere Registrierungseinträge, die den Anwendungen entsprechen, die beim Systemstart ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="d3021-120">For example, the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** usually contains several registry entries that represent applications that run when the system starts.</span></span>

<span data-ttu-id="d3021-121">Wenn Sie **Get-ChildItem** verwenden, um nach untergeordnete Elementen im Schlüssel zu suchen, wird nur der **OptionalComponents**-Unterschlüssel des Schlüssels angezeigt:</span><span class="sxs-lookup"><span data-stu-id="d3021-121">However, when you use **Get-ChildItem** to look for child items in the key, all you will see is the **OptionalComponents** subkey of the key:</span></span>

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

<span data-ttu-id="d3021-122">Zwar wäre es praktisch, wenn Registrierungseinträge wie Elemente behandelt werden könnten, es ist aber nicht möglich, einen Pfad zu einem Registrierungseintrag so anzugeben, dass seine Eindeutigkeit sicherstellt ist.</span><span class="sxs-lookup"><span data-stu-id="d3021-122">Although it would be convenient to treat registry entries as items, you cannot specify a path to a registry entry in a way that ensures that it is unique.</span></span> <span data-ttu-id="d3021-123">In der Pfadnotation wird nicht zwischen dem Registrierungsunterschlüssel namens **Run** und dem **(Standard)** Registrierungseintrag im **Run**-Unterschlüssel unterschieden.</span><span class="sxs-lookup"><span data-stu-id="d3021-123">The path notation does not distinguish between the registry subkey named **Run** and the **(Default)** registry entry in the **Run** subkey.</span></span> <span data-ttu-id="d3021-124">Darüber hinaus könnten Sie – wenn Registrierungseinträge Elemente wären – die Pfadnotation nicht dazu verwenden, einen Registrierungseintrag namens **Windows\\CurrentVersion\\Run** von dem Unterschlüssel zu unterscheiden, der sich in diesem Pfad befindet, denn Registrierungseintragsnamen können den umgekehrten Schrägstrich (**\\**) enthalten.</span><span class="sxs-lookup"><span data-stu-id="d3021-124">Furthermore, because registry entry names can contain the backslash character (**\\**), if registry entries were items, then you could not use the path notation to distinguish a registry entry named **Windows\\CurrentVersion\\Run** from the subkey that is located in that path.</span></span>

## <a name="renaming-existing-items-rename-item"></a><span data-ttu-id="d3021-125">Umbenennen von vorhandenen Elementen (Rename-Item)</span><span class="sxs-lookup"><span data-stu-id="d3021-125">Renaming Existing Items (Rename-Item)</span></span>

<span data-ttu-id="d3021-126">Um den Namen einer Datei oder eines Ordners zu ändern, verwenden Sie das Cmdlet **Rename-Item**.</span><span class="sxs-lookup"><span data-stu-id="d3021-126">To change the name of a file or folder, use the **Rename-Item** cmdlet.</span></span> <span data-ttu-id="d3021-127">Der folgende Befehl ändert den Namen der Datei **file1.txt** in **fileOne.txt**.</span><span class="sxs-lookup"><span data-stu-id="d3021-127">The following command changes the name of the **file1.txt** file to **fileOne.txt**.</span></span>

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

<span data-ttu-id="d3021-128">Das Cmdlet **Rename-Item** kann den Namen einer Datei oder eines Ordners ändern, kann aber kein Element verschieben.</span><span class="sxs-lookup"><span data-stu-id="d3021-128">The **Rename-Item** cmdlet can change the name of a file or a folder, but it cannot move an item.</span></span> <span data-ttu-id="d3021-129">Der folgende Befehl schlägt fehl, weil er versucht, die Datei aus dem Verzeichnis „New.Directory“ in das Verzeichnis „Temp“ zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="d3021-129">The following command fails because it attempts to move the file from the New.Directory directory to the Temp directory.</span></span>

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

## <a name="moving-items-move-item"></a><span data-ttu-id="d3021-130">Verschieben von Elementen (Move-Item)</span><span class="sxs-lookup"><span data-stu-id="d3021-130">Moving Items (Move-Item)</span></span>

<span data-ttu-id="d3021-131">Um eine Datei oder einen Ordner zu verschieben, verwenden Sie das Cmdlet **Move-Item**.</span><span class="sxs-lookup"><span data-stu-id="d3021-131">To move a file or folder, use the **Move-Item** cmdlet.</span></span>

<span data-ttu-id="d3021-132">Der folgende Befehl verschiebt z.B. das Verzeichnis „New.Directory“ aus dem Verzeichnis „C:\\temp“ in das Stammverzeichnis von Laufwerk C:.</span><span class="sxs-lookup"><span data-stu-id="d3021-132">For example, the following command moves the New.Directory directory from the C:\\temp directory to the root of the C: drive.</span></span> <span data-ttu-id="d3021-133">Wenn Sie überprüfen möchten, ob das Element verschoben wurde, fügen Sie den **PassThru**-Parameter des **Move-Item**-Cmdlets ein.</span><span class="sxs-lookup"><span data-stu-id="d3021-133">To verify that the item was moved, include the **PassThru** parameter of the **Move-Item** cmdlet.</span></span> <span data-ttu-id="d3021-134">Ohne **Passthru** zeigt das Cmdlet **Move-Item** keine Ergebnisse an.</span><span class="sxs-lookup"><span data-stu-id="d3021-134">Without **Passthru**, the **Move-Item** cmdlet does not display any results.</span></span>

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

## <a name="copying-items-copy-item"></a><span data-ttu-id="d3021-135">Kopieren von Elementen (Copy-Item)</span><span class="sxs-lookup"><span data-stu-id="d3021-135">Copying Items (Copy-Item)</span></span>

<span data-ttu-id="d3021-136">Wenn Sie mit den Kopiervorgänge in anderen Shells vertraut sind, finden Sie das Verhalten des Cmdlets **Copy-Item** in Windows PowerShell möglicherweise ungewöhnlich.</span><span class="sxs-lookup"><span data-stu-id="d3021-136">If you are familiar with the copy operations in other shells, you might find the behavior of the **Copy-Item** cmdlet in Windows PowerShell to be unusual.</span></span> <span data-ttu-id="d3021-137">Wenn Sie ein Element aus einem Speicherort in einen anderen kopieren, kopiert „Copy-Item“ den Inhalt des Elements nicht standardmäßig.</span><span class="sxs-lookup"><span data-stu-id="d3021-137">When you copy an item from one location to another, Copy-Item does not copy its contents by default.</span></span>

<span data-ttu-id="d3021-138">Angenommen, Sie kopieren das Verzeichnis **New.Directory** von Laufwerk C: in das Verzeichnis „C:\\temp“, dann wird der Befehl erfolgreich ausgeführt, aber die Dateien im Verzeichnis „New.Directory“ werden nicht kopiert.</span><span class="sxs-lookup"><span data-stu-id="d3021-138">For example, if you copy the **New.Directory** directory from the C: drive to the C:\\temp directory, the command succeeds, but the files in the New.Directory directory are not copied.</span></span>

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

<span data-ttu-id="d3021-139">Wenn Sie den Inhalt von **C:\\temp\\New.Directory** anzeigen, stellen Sie fest, dass es keine Dateien enthält:</span><span class="sxs-lookup"><span data-stu-id="d3021-139">If you display the contents of **C:\\temp\\New.Directory**, you will find that it contains no files:</span></span>

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

<span data-ttu-id="d3021-140">Warum kopiert das Cmdlet **Copy-Item** den Inhalt nicht in den neuen Speicherort?</span><span class="sxs-lookup"><span data-stu-id="d3021-140">Why doesn't the **Copy-Item** cmdlet copy the contents to the new location?</span></span>

<span data-ttu-id="d3021-141">Das Cmdlet **Copy-Item** wurde als generisches Cmdlet entworfen, d.h., es ist nicht nur zum Kopieren von Dateien und Ordnern vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="d3021-141">The **Copy-Item** cmdlet was designed to be generic; it is not just for copying files and folders.</span></span> <span data-ttu-id="d3021-142">Außerdem könnte es sein, auch wenn Dateien und Ordner kopiert werden, dass Sie nur den Container und nicht die Elemente im Container kopieren möchten.</span><span class="sxs-lookup"><span data-stu-id="d3021-142">Also, even when copying files and folders, you might want to copy only the container and not the items within it.</span></span>

<span data-ttu-id="d3021-143">Wenn Sie den gesamten Inhalt eines Ordners kopieren möchten, fügen Sie den **Recurse**-Parameter des **Copy-Item**-Cmdlets in den Befehl ein.</span><span class="sxs-lookup"><span data-stu-id="d3021-143">To copy all of the contents of a folder, include the **Recurse** parameter of the **Copy-Item** cmdlet in the command.</span></span> <span data-ttu-id="d3021-144">Wenn Sie das Verzeichnis bereits ohne Inhalt kopiert haben, fügen Sie den **Force**-Parameter ein, der es ermöglicht, dass der leere Ordner überschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="d3021-144">If you have already copied the directory without its contents, add the **Force** parameter, which allows you to overwrite the empty folder.</span></span>

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

## <a name="deleting-items-remove-item"></a><span data-ttu-id="d3021-145">Löschen von Elementen (Remove-Item)</span><span class="sxs-lookup"><span data-stu-id="d3021-145">Deleting Items (Remove-Item)</span></span>

<span data-ttu-id="d3021-146">Um Dateien und Ordner zu löschen, verwenden Sie das Cmdlet **Remove-Item**.</span><span class="sxs-lookup"><span data-stu-id="d3021-146">To delete files and folders, use the **Remove-Item** cmdlet.</span></span> <span data-ttu-id="d3021-147">Windows PowerShell-Cmdlets, etwa **Remove-Item**, die erhebliche, nicht rückgängig zu machende Änderungen vornehmen, fordern häufig zu einer Bestätigung auf, wenn Sie deren Befehle eingeben.</span><span class="sxs-lookup"><span data-stu-id="d3021-147">Windows PowerShell cmdlets, such as **Remove-Item**, that can make significant, irreversible changes will often prompt for confirmation when you enter its commands.</span></span> <span data-ttu-id="d3021-148">Wenn Sie beispielsweise versuchen, den Ordner **New.Directory** zu entfernen, werden Sie aufgefordert, den Befehl zu bestätigen, da der Ordner Dateien enthält:</span><span class="sxs-lookup"><span data-stu-id="d3021-148">For example, if you try to remove the **New.Directory** folder, you will be prompted to confirm the command, because the folder contains files:</span></span>

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="d3021-149">Da **Ja** die Standardantwort ist, drücken Sie die **EINGABETASTE**, um den Ordner und alle in ihm enthaltenen Dateien zu löschen.</span><span class="sxs-lookup"><span data-stu-id="d3021-149">Because **Yes** is the default response, to delete the folder and its files, press the **Enter** key.</span></span> <span data-ttu-id="d3021-150">Um den Ordner ohne Bestätigung zu löschen, verwenden Sie den **-Recurse**-Parameter.</span><span class="sxs-lookup"><span data-stu-id="d3021-150">To remove the folder without confirming, use the **-Recurse** parameter.</span></span>

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

## <a name="executing-items-invoke-item"></a><span data-ttu-id="d3021-151">Ausführen von Elementen (Invoke-Item)</span><span class="sxs-lookup"><span data-stu-id="d3021-151">Executing Items (Invoke-Item)</span></span>

<span data-ttu-id="d3021-152">Windows PowerShell verwendet das **Invoke-Item**-Cmdlet, um eine Standardaktion für eine Datei oder einen Ordner auszuführen.</span><span class="sxs-lookup"><span data-stu-id="d3021-152">Windows PowerShell uses the **Invoke-Item** cmdlet to perform a default action for a file or folder.</span></span> <span data-ttu-id="d3021-153">Diese Standardaktion ist durch den Standardanwendungshandler in der Registrierung festgelegt. Der Effekt ist derselbe, als würden Sie im Datei-Explorer auf das Element doppelklicken.</span><span class="sxs-lookup"><span data-stu-id="d3021-153">This default action is determined by the default application handler in the registry; the effect is the same as if you double-click the item in File Explorer.</span></span>

<span data-ttu-id="d3021-154">Nehmen Sie an, Sie führen den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="d3021-154">For example, suppose you run the following command:</span></span>

```powershell
Invoke-Item C:\WINDOWS
```

<span data-ttu-id="d3021-155">Ein Explorer-Fenster, das sich in „C:\\Windows“ befindet, wird angezeigt, genau so, als hätten Sie auf den Ordner „C:\\Windows“ doppelgeklickt.</span><span class="sxs-lookup"><span data-stu-id="d3021-155">An Explorer window that is located in C:\\Windows appears, just as if you had double-clicked the C:\\Windows folder.</span></span>

<span data-ttu-id="d3021-156">Wenn Sie die Datei **Boot.ini** auf einem System vor Windows Vista aufrufen:</span><span class="sxs-lookup"><span data-stu-id="d3021-156">If you invoke the **Boot.ini** file on a system prior to Windows Vista:</span></span>

```powershell
Invoke-Item C:\boot.ini
```

<span data-ttu-id="d3021-157">Ist der INI-Dateityp mit Editor verknüpft ist, wird die Datei „boot.ini“ in Editor geöffnet.</span><span class="sxs-lookup"><span data-stu-id="d3021-157">If the .ini file type is associated with Notepad, the boot.ini file opens in Notepad.</span></span>
