---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC-Ressource „File“"
ms.openlocfilehash: f16bfbc31489ef7d1b0e5e4ec3a4f30069c24c79
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-file-resource"></a><span data-ttu-id="a4ef5-103">DSC-Ressource „File“</span><span class="sxs-lookup"><span data-stu-id="a4ef5-103">DSC File Resource</span></span>

> <span data-ttu-id="a4ef5-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a4ef5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="a4ef5-105">Die Ressource „File“ in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten von Dateien und Verzeichnissen auf einem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span>

><span data-ttu-id="a4ef5-106">**Hinweis:** Wenn die Eigenschaft **MatchSource** auf **$false** festgelegt wurde (der Standardwert), werden die zu kopierenden Inhalte bei der ersten Anwendung der Konfiguration zwischengespeichert.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-106">**Note:** If the **MatchSource** property is set to **$false** (which is the default value), the contents to be copied are cached the first time the configuration is applied.</span></span> 
><span data-ttu-id="a4ef5-107">Darauffolgende Anwendungen der Konfiguration suchen in dem in **SourcePath** angegebenen Pfad nicht nach aktualisierten Dateien bzw. Ordnern.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-107">Subsequent applications of the configuration will not check for updated files and/or folders in the path specified by **SourcePath**.</span></span> <span data-ttu-id="a4ef5-108">Wenn Sie bei jeder Anwendung der Konfiguration nach Updates für die Dateien bzw. Ordner in **SourcePath** suchen möchten, müssen Sie **MatchSource** auf **$true** festlegen.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-108">If you want to check for updates to the files and/or folders in **SourcePath** every time the configuration is applied, set **MatchSource** to **$true**.</span></span> 

## <a name="syntax"></a><span data-ttu-id="a4ef5-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="a4ef5-109">Syntax</span></span>
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ] 
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ] 
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="a4ef5-110">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="a4ef5-110">Properties</span></span>

|  <span data-ttu-id="a4ef5-111">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="a4ef5-111">Property</span></span>  |  <span data-ttu-id="a4ef5-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a4ef5-112">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="a4ef5-113">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="a4ef5-113">DestinationPath</span></span>| <span data-ttu-id="a4ef5-114">Gibt den Speicherort an, an dem Sie den Zustand einer Datei oder eines Verzeichnisses sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-114">Indicates the location where you want to ensure the state for a file or directory.</span></span>| 
| <span data-ttu-id="a4ef5-115">Attributes</span><span class="sxs-lookup"><span data-stu-id="a4ef5-115">Attributes</span></span>| <span data-ttu-id="a4ef5-116">Gibt den gewünschten Status der Attribute der Zieldatei oder des Zielverzeichnisses an.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-116">Specifies the desired state of the attributes for the targeted file or directory.</span></span>| 
| <span data-ttu-id="a4ef5-117">Checksum</span><span class="sxs-lookup"><span data-stu-id="a4ef5-117">Checksum</span></span>| <span data-ttu-id="a4ef5-118">Gibt den zu verwendenden Typ von Prüfsumme an, wenn bestimmt wird, ob zwei Dateien identisch sind.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-118">Indicates the checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="a4ef5-119">Wenn __Checksum__ nicht angegeben ist, wird nur der Datei- oder Verzeichnisname für den Vergleich verwendet.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-119">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="a4ef5-120">Gültige Werte sind: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-120">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>| 
| <span data-ttu-id="a4ef5-121">Contents</span><span class="sxs-lookup"><span data-stu-id="a4ef5-121">Contents</span></span>| <span data-ttu-id="a4ef5-122">Gibt den Inhalt einer Datei an, z. B. eine bestimmte Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-122">Specifies the contents of a file, such as a particular string.</span></span>| 
| <span data-ttu-id="a4ef5-123">Credential</span><span class="sxs-lookup"><span data-stu-id="a4ef5-123">Credential</span></span>| <span data-ttu-id="a4ef5-124">Gibt die Anmeldeinformationen an, die für den Zugriff auf Ressourcen erforderlich sind, wie z. B. Quelldateien, wenn ein solcher Zugriff erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-124">Indicates the credentials that are required to access resources, such as source files, if such access is required.</span></span>| 
| <span data-ttu-id="a4ef5-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="a4ef5-125">Ensure</span></span>| <span data-ttu-id="a4ef5-126">Gibt an, ob die Datei oder das Verzeichnis vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-126">Indicates if the file or directory exists.</span></span> <span data-ttu-id="a4ef5-127">Legen Sie diese Eigenschaft auf „Absent“ fest, um sicherzustellen, dass die Datei oder das Verzeichnis nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-127">Set this property to "Absent" to ensure that the file or directory does not exist.</span></span> <span data-ttu-id="a4ef5-128">Legen Sie sie auf „Present“ fest, um sicherzustellen, dass die Datei oder das Verzeichnis vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-128">Set it to "Present" to ensure that the file or directory does exist.</span></span> <span data-ttu-id="a4ef5-129">Die Standardeinstellung ist „Present“.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-129">The default is "Present".</span></span>| 
| <span data-ttu-id="a4ef5-130">Force</span><span class="sxs-lookup"><span data-stu-id="a4ef5-130">Force</span></span>| <span data-ttu-id="a4ef5-131">Bestimmte Dateioperationen (z. B. das Überschreiben einer Datei oder Löschen eines Verzeichnisses, das nicht leer ist), führen zu einem Fehler.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-131">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="a4ef5-132">Bei Verwenden der „Force“-Eigenschaft werden solche Fehler überschrieben.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-132">Using the Force property overrides such errors.</span></span> <span data-ttu-id="a4ef5-133">Der Standardwert ist __$false__.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-133">The default value is __$false__.</span></span>| 
| <span data-ttu-id="a4ef5-134">Recurse</span><span class="sxs-lookup"><span data-stu-id="a4ef5-134">Recurse</span></span>| <span data-ttu-id="a4ef5-135">Gibt an, ob Unterverzeichnisse enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-135">Indicates if subdirectories are included.</span></span> <span data-ttu-id="a4ef5-136">Legen Sie diese Eigenschaft auf __$true__ fest, um anzugeben, dass Unterverzeichnisse enthalten sein sollen.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-136">Set this property to __$true__ to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="a4ef5-137">Der Standardwert ist __$false__.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-137">The default is __$false__.</span></span> <span data-ttu-id="a4ef5-138">**Hinweis:** Diese Eigenschaft ist nur gültig, wenn die „Type“-Eigenschaft auf „directory“ festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-138">**Note**: This property is only valid when the Type property is set to Directory.</span></span>| 
| <span data-ttu-id="a4ef5-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a4ef5-139">DependsOn</span></span> | <span data-ttu-id="a4ef5-140">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a4ef5-141">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-141">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="a4ef5-142">SourcePath</span><span class="sxs-lookup"><span data-stu-id="a4ef5-142">SourcePath</span></span>| <span data-ttu-id="a4ef5-143">Gibt den Pfad an, aus dem die Datei- oder Ordnerressource kopiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-143">Indicates the path from which to copy the file or folder resource.</span></span>| 
| <span data-ttu-id="a4ef5-144">Typ</span><span class="sxs-lookup"><span data-stu-id="a4ef5-144">Type</span></span>| <span data-ttu-id="a4ef5-145">Gibt an, ob die zu konfigurierende Ressource ein Verzeichnis oder eine Datei ist.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-145">Indicates if the resource being configured is a directory or a file.</span></span> <span data-ttu-id="a4ef5-146">Legen Sie diese Eigenschaft auf „Directory“ fest, um anzugeben, dass die Ressource ein Verzeichnis ist.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-146">Set this property to "Directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="a4ef5-147">Legen Sie sie auf „File“ fest, um anzugeben, dass die Ressource eine Datei ist.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-147">Set it to "File" to indicate that the resource is a file.</span></span> <span data-ttu-id="a4ef5-148">Der Standardwert ist „File“.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-148">The default value is “File”.</span></span>| 
| <span data-ttu-id="a4ef5-149">MatchSource</span><span class="sxs-lookup"><span data-stu-id="a4ef5-149">MatchSource</span></span>| <span data-ttu-id="a4ef5-150">Bei Festlegen auf den Standardwert __$false__ werden beliebige Dateien in der Quelle (z. B. die Dateien A, B und C) dem Ziel hinzugefügt, wenn die Konfiguration zum ersten Mal angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-150">If set to the default value of __$false__, then any files on the source (say, files A, B, and C) will be added to the destination the first time the configuration is applied.</span></span> <span data-ttu-id="a4ef5-151">Wenn eine neue Datei (D) der Quelle hinzugefügt wird, wird sie nicht dem Ziel hinzugefügt, auch wenn die Konfiguration später erneut angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-151">If a new file (D) is added to the source, it will not be added to the destination, even when the configuration is re-applied later.</span></span> <span data-ttu-id="a4ef5-152">Wenn der Wert __$true__ ist, werden bei jedem Anwenden der Konfiguration in der Quelle gefundene neue Dateien (wie z. B. Datei D in diesem Beispiel) dem Ziel hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-152">If the value is __$true__, then each time the configuration is applied, new files subsequently found on the source (such as file D in this example) are added to the destination.</span></span> <span data-ttu-id="a4ef5-153">Der Standardwert ist **$false**.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-153">The default value is **$false**.</span></span>| 

## <a name="example"></a><span data-ttu-id="a4ef5-154">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a4ef5-154">Example</span></span>

<span data-ttu-id="a4ef5-155">Im folgenden Beispiel wird veranschaulicht, wie die Ressource „File“ verwendet wird, um sicherzustellen, dass ein Verzeichnis mit dem Pfad `C:\Users\Public\Documents\DSCDemo\DemoSource` auf einem Quellcomputer (z. B. dem Pullserver) auch auf dem Zielknoten (mit allen Unterverzeichnissen) vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-155">The following example shows how to use the File resource to ensure that a directory with the path `C:\Users\Public\Documents\DSCDemo\DemoSource` on a source computer (such as the “pull” server) is also present (along with all subdirectories) on the target node.</span></span> <span data-ttu-id="a4ef5-156">Außerdem wird nach Abschluss eine Bestätigungsmeldung in das Protokoll geschrieben und eine Anweisung hinzugefügt, um dafür zu sorgen, dass der Dateiprüfvorgang vor dem Protokollierungsvorgang erfolgt.</span><span class="sxs-lookup"><span data-stu-id="a4ef5-156">It also writes a confirmatory message to the log when complete and includes a statement to ensure that the file-checking operation runs prior to the logging operation.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"    
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```

