---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC für Linux-Resource „nxFile“
ms.openlocfilehash: be5f098d2fe1c8b354c07e6a8f882b8fdf00e1db
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954827"
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="e177f-103">DSC für Linux-Resource „nxFile“</span><span class="sxs-lookup"><span data-stu-id="e177f-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="e177f-104">Die Ressource **nxFile** in PowerShell DSC (Desired State Configuration) bietet einen Mechanismus zum Verwalten von Dateien und Verzeichnissen auf einem Linux-Knoten.</span><span class="sxs-lookup"><span data-stu-id="e177f-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="e177f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e177f-105">Syntax</span></span>

```Syntax
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage | ignore } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="e177f-106">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="e177f-106">Properties</span></span>

|<span data-ttu-id="e177f-107">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="e177f-107">Property</span></span> |<span data-ttu-id="e177f-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e177f-108">Description</span></span> |
|---|---|
|<span data-ttu-id="e177f-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="e177f-109">DestinationPath</span></span> |<span data-ttu-id="e177f-110">Gibt den Speicherort an, an dem Sie den Zustand einer Datei oder eines Verzeichnisses sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="e177f-110">Specifies the location where you want to ensure the state for a file or directory.</span></span> |
|<span data-ttu-id="e177f-111">SourcePath</span><span class="sxs-lookup"><span data-stu-id="e177f-111">SourcePath</span></span> |<span data-ttu-id="e177f-112">Gibt den Pfad an, aus dem die Datei- oder Ordnerressource kopiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="e177f-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="e177f-113">Dieser Pfad kann ein lokaler Pfad oder eine URL des Typs `http/https/ftp` sein.</span><span class="sxs-lookup"><span data-stu-id="e177f-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="e177f-114">Remote-URLs des Typs `http/https/ftp` werden nur unterstützt, wenn der Wert der **Type**-Eigenschaft **file** ist.</span><span class="sxs-lookup"><span data-stu-id="e177f-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is **file**.</span></span> |
|<span data-ttu-id="e177f-115">Type</span><span class="sxs-lookup"><span data-stu-id="e177f-115">Type</span></span> |<span data-ttu-id="e177f-116">Gibt an, ob die zu konfigurierende Ressource ein Verzeichnis oder eine Datei ist.</span><span class="sxs-lookup"><span data-stu-id="e177f-116">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="e177f-117">Legen Sie diese Eigenschaft auf **directory** fest, um anzugeben, dass die Ressource ein Verzeichnis ist.</span><span class="sxs-lookup"><span data-stu-id="e177f-117">Set this property to **directory** to indicate that the resource is a directory.</span></span> <span data-ttu-id="e177f-118">Legen Sie sie auf **file** fest, um anzugeben, dass die Ressource eine Datei ist.</span><span class="sxs-lookup"><span data-stu-id="e177f-118">Set it to **file** to indicate that the resource is a file.</span></span> <span data-ttu-id="e177f-119">Der Standardwert ist **file**.</span><span class="sxs-lookup"><span data-stu-id="e177f-119">The default value is **file**.</span></span> |
|<span data-ttu-id="e177f-120">Contents</span><span class="sxs-lookup"><span data-stu-id="e177f-120">Contents</span></span> |<span data-ttu-id="e177f-121">Gibt den Inhalt einer Datei an, z. B. eine bestimmte Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="e177f-121">Specifies the contents of a file, such as a particular string.</span></span> |
|<span data-ttu-id="e177f-122">Checksum</span><span class="sxs-lookup"><span data-stu-id="e177f-122">Checksum</span></span> |<span data-ttu-id="e177f-123">Definiert den zu verwendenden Typ, wenn bestimmt wird, ob zwei Dateien identisch sind.</span><span class="sxs-lookup"><span data-stu-id="e177f-123">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="e177f-124">Wenn **Checksum** nicht angegeben ist, wird nur der Datei- oder Verzeichnisnamen für den Vergleich verwendet.</span><span class="sxs-lookup"><span data-stu-id="e177f-124">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="e177f-125">Werte sind: **ctime**, **mtime** oder **md5**.</span><span class="sxs-lookup"><span data-stu-id="e177f-125">Values are: **ctime**, **mtime**, or **md5**.</span></span> |
|<span data-ttu-id="e177f-126">Recurse</span><span class="sxs-lookup"><span data-stu-id="e177f-126">Recurse</span></span> |<span data-ttu-id="e177f-127">Gibt an, ob Unterverzeichnisse enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="e177f-127">Indicates if subdirectories are included.</span></span> <span data-ttu-id="e177f-128">Legen Sie diese Eigenschaft auf `$true` fest, um anzugeben, dass Unterverzeichnisse enthalten sein sollen.</span><span class="sxs-lookup"><span data-stu-id="e177f-128">Set this property to `$true` to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="e177f-129">Der Standardwert ist `$false`.</span><span class="sxs-lookup"><span data-stu-id="e177f-129">The default is `$false`.</span></span> <span data-ttu-id="e177f-130">Diese Eigenschaft ist nur gültig, wenn die **Type**-Eigenschaft auf **directory** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="e177f-130">This property is only valid when the **Type** property is set to **directory**.</span></span> |
|<span data-ttu-id="e177f-131">Force</span><span class="sxs-lookup"><span data-stu-id="e177f-131">Force</span></span> |<span data-ttu-id="e177f-132">Bestimmte Dateioperationen (z. B. das Überschreiben einer Datei oder Löschen eines Verzeichnisses, das nicht leer ist), führen zu einem Fehler.</span><span class="sxs-lookup"><span data-stu-id="e177f-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="e177f-133">Bei Verwenden der **Force**-Eigenschaft werden solche Fehler überschrieben.</span><span class="sxs-lookup"><span data-stu-id="e177f-133">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="e177f-134">Der Standardwert ist `$false`.</span><span class="sxs-lookup"><span data-stu-id="e177f-134">The default value is `$false`.</span></span> |
|<span data-ttu-id="e177f-135">Links</span><span class="sxs-lookup"><span data-stu-id="e177f-135">Links</span></span> |<span data-ttu-id="e177f-136">Gibt das gewünschte Verhalten für symbolische Verknüpfungen an.</span><span class="sxs-lookup"><span data-stu-id="e177f-136">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="e177f-137">Legen Sie diese Eigenschaft auf **follow** fest, um symbolischen Verknüpfungen zu folgen und Aktionen auf das Ziel der Verknüpfung anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="e177f-137">Set this property to **follow** to follow symbolic links and act on the links target.</span></span> <span data-ttu-id="e177f-138">Ein Beispiel ist das Kopieren der Datei anstatt der Verknüpfung.</span><span class="sxs-lookup"><span data-stu-id="e177f-138">For example, copy the file instead of the link.</span></span> <span data-ttu-id="e177f-139">Legen Sie diese Eigenschaft auf **manage** fest, um eine Aktion auf die Verknüpfung anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="e177f-139">Set this property to **manage** to act on the link.</span></span> <span data-ttu-id="e177f-140">Ein Beispiel ist das Kopieren der Verknüpfung selbst.</span><span class="sxs-lookup"><span data-stu-id="e177f-140">For example, copy the link itself.</span></span> <span data-ttu-id="e177f-141">Legen Sie diese Eigenschaft auf **ignore** fest, um symbolische Verknüpfungen zu ignorieren.</span><span class="sxs-lookup"><span data-stu-id="e177f-141">Set this property to **ignore** to ignore symbolic links.</span></span> |
|<span data-ttu-id="e177f-142">Group</span><span class="sxs-lookup"><span data-stu-id="e177f-142">Group</span></span> |<span data-ttu-id="e177f-143">Der Name der **Gruppe**, die über Zugriffsberechtigungen auf die Datei oder das Verzeichnis besitzen soll.</span><span class="sxs-lookup"><span data-stu-id="e177f-143">The name of the **Group** to have permissions to the file or directory.</span></span> |
|<span data-ttu-id="e177f-144">Mode</span><span class="sxs-lookup"><span data-stu-id="e177f-144">Mode</span></span> |<span data-ttu-id="e177f-145">Gibt die gewünschten Berechtigungen für die Ressource in der Oktal- oder symbolischen Schreibweise an.</span><span class="sxs-lookup"><span data-stu-id="e177f-145">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="e177f-146">Beispiele hierfür sind **777** oder **rwxrwxrwx**.</span><span class="sxs-lookup"><span data-stu-id="e177f-146">For example, **777** or **rwxrwxrwx**.</span></span> <span data-ttu-id="e177f-147">Geben Sie bei Verwenden der symbolischen Schreibweise nicht das erste Zeichen an, welches Verzeichnis oder Datei angibt.</span><span class="sxs-lookup"><span data-stu-id="e177f-147">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span> |
|<span data-ttu-id="e177f-148">Besitzer</span><span class="sxs-lookup"><span data-stu-id="e177f-148">Owner</span></span> |<span data-ttu-id="e177f-149">Der Name der Gruppe, die die Datei oder das Verzeichnis besitzen soll.</span><span class="sxs-lookup"><span data-stu-id="e177f-149">The name of the group to own the file or directory.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="e177f-150">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="e177f-150">Common properties</span></span>

|<span data-ttu-id="e177f-151">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="e177f-151">Property</span></span> |<span data-ttu-id="e177f-152">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e177f-152">Description</span></span> |
|---|---|
|<span data-ttu-id="e177f-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e177f-153">DependsOn</span></span> |<span data-ttu-id="e177f-154">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="e177f-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e177f-155">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="e177f-155">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="e177f-156">Ensure</span><span class="sxs-lookup"><span data-stu-id="e177f-156">Ensure</span></span> |<span data-ttu-id="e177f-157">Bestimmt, ob das Vorhandensein der Datei geprüft werden soll.</span><span class="sxs-lookup"><span data-stu-id="e177f-157">Determines whether to check if the file exists.</span></span> <span data-ttu-id="e177f-158">Legen Sie diese Eigenschaft auf **Present** fest, um sicherzustellen, dass die Datei vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="e177f-158">Set this property to **Present** to ensure the file exists.</span></span> <span data-ttu-id="e177f-159">Legen Sie sie auf **Absent** fest, um sicherzustellen, dass die Datei nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="e177f-159">Set it to **Absent** to ensure the file does not exist.</span></span> <span data-ttu-id="e177f-160">Der Standardwert ist **Present**.</span><span class="sxs-lookup"><span data-stu-id="e177f-160">The default value is **Present**.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="e177f-161">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e177f-161">Additional Information</span></span>

<span data-ttu-id="e177f-162">Linux und Windows verwenden in Textdateien standardmäßig unterschiedliche Zeilenumbruchzeichen. Diese kann zu unerwarteten Ergebnissen führen, wenn einige Dateien mit **nxFile** auf einem Linux-Computer konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="e177f-162">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with **nxFile**.</span></span> <span data-ttu-id="e177f-163">Es gibt mehrere Möglichkeiten, den Inhalt einer Linux-Datei zu verwalten, um durch unerwartete Zeilenumbruchzeichen verursachte Probleme zu vermeiden:</span><span class="sxs-lookup"><span data-stu-id="e177f-163">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

1. <span data-ttu-id="e177f-164">Kopieren der Datei aus einer Remotequelle (HTTP, HTTPS oder FTP)</span><span class="sxs-lookup"><span data-stu-id="e177f-164">Copy the file from a remote source (http, https, or ftp)</span></span>

   <span data-ttu-id="e177f-165">Erstellen Sie eine Datei unter Linux mit dem gewünschten Inhalt, und stellen Sie sie auf einem Web- oder FTP-Server bereit, auf den die Knoten zugreifen können, die Sie konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="e177f-165">Create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="e177f-166">Legen Sie die **SourcePath**-Eigenschaft in der Ressource **nxFile** auf die Web- oder FTP-URL zur Datei fest.</span><span class="sxs-lookup"><span data-stu-id="e177f-166">Define the **SourcePath** property in the **nxFile** resource with the web or ftp URL to the file.</span></span>

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      nxFile resolvConf
      {
         SourcePath = "http://10.185.85.11/conf/resolv.conf"
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
      }
   }
   ```

1. <span data-ttu-id="e177f-167">Lesen Sie den Inhalt der Datei im PowerShell-Skript mit [Get-Content](https://technet.microsoft.com/library/hh849787.aspx), nachdem Sie die **$OFS**-Eigenschaft auf das Verwenden des Linux-Zeilenumbruchzeichens festgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="e177f-167">Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the **$OFS** property to use the Linux line-break character.</span></span>

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      $OFS = "`n"
      $Contents = Get-Content C:\temp\resolv.conf

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = "$Contents"
      }
   }
   ```

1. <span data-ttu-id="e177f-168">Verwenden Sie eine PowerShell-Funktion, um Windows-Zeilenumbrüche durch Linux-Zeilenumbruchzeichen zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="e177f-168">Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

   ```powershell
   Function LinuxString($inputStr){
      $outputStr = $inputStr.Replace("`r`n","`n")
      $outputStr += "`n"
      Return $outputStr
   }

   Import-DSCResource -Module nx

   Node $Node
   {
      $Contents = @'
   search contoso.com
   domain contoso.com
   nameserver 10.185.85.11
   '@
       $Contents = LinuxString $Contents

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = $Contents
      }
   }
   ```

## <a name="example"></a><span data-ttu-id="e177f-169">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e177f-169">Example</span></span>

<span data-ttu-id="e177f-170">Im folgende Beispiel wird sichergestellt, dass das Verzeichnis `/opt/mydir` vorhanden ist und dass eine Datei mit dem angegebenen Inhalt in diesem Verzeichnis vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="e177f-170">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    nxFile DirectoryExample
    {
        Ensure = "Present"
        DestinationPath = "/opt/mydir"
        Type = "Directory"
    }

    nxFile FileExample
    {
        Ensure = "Present"
        Destinationpath = "/opt/mydir/myfile"
        Contents=@"
#!/bin/bash`necho "hello world"`n
"@
        Mode = "755"
        DependsOn = "[nxFile]DirectoryExample"
    }
}
```