---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressourcen „Archive“
ms.openlocfilehash: 458b4f0f20dc96dab62e709183c25ff57d971aae
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="fbf59-103">DSC-Ressourcen „Archive“</span><span class="sxs-lookup"><span data-stu-id="fbf59-103">DSC Archive Resource</span></span>

> <span data-ttu-id="fbf59-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fbf59-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="fbf59-105">Die Ressource „Archive“ in Windows PowerShell DSC bietet einen Mechanismus zum Entpacken von Archivdateien (.zip).</span><span class="sxs-lookup"><span data-stu-id="fbf59-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="fbf59-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="fbf59-106">Syntax</span></span>
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="fbf59-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="fbf59-107">Properties</span></span>

|  <span data-ttu-id="fbf59-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="fbf59-108">Property</span></span>  |  <span data-ttu-id="fbf59-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="fbf59-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="fbf59-110">Ziel</span><span class="sxs-lookup"><span data-stu-id="fbf59-110">Destination</span></span>| <span data-ttu-id="fbf59-111">Gibt den Speicherort an, an dem der Archivinhalt einer Datei extrahiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="fbf59-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="fbf59-112">Pfad</span><span class="sxs-lookup"><span data-stu-id="fbf59-112">Path</span></span>| <span data-ttu-id="fbf59-113">Gibt den Quellpfad der Archivdatei an.</span><span class="sxs-lookup"><span data-stu-id="fbf59-113">Specifies the source path of the archive file.</span></span>|
| <span data-ttu-id="fbf59-114">__Checksum__</span><span class="sxs-lookup"><span data-stu-id="fbf59-114">__Checksum__</span></span>| <span data-ttu-id="fbf59-115">Definiert den zu verwendenden Typ, wenn bestimmt wird, ob zwei Dateien identisch sind.</span><span class="sxs-lookup"><span data-stu-id="fbf59-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="fbf59-116">Wenn __Checksum__ nicht angegeben ist, wird nur der Datei- oder Verzeichnisnamen für den Vergleich verwendet.</span><span class="sxs-lookup"><span data-stu-id="fbf59-116">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="fbf59-117">Gültige Werte sind: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, keine (Standard).</span><span class="sxs-lookup"><span data-stu-id="fbf59-117">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (default).</span></span> <span data-ttu-id="fbf59-118">Wenn Sie __Checksum__ ohne __Validate__ angeben, schlägt die Konfiguration fehl.</span><span class="sxs-lookup"><span data-stu-id="fbf59-118">If you specify __Checksum__ without __Validate__, the configuration will fail.</span></span>|
| <span data-ttu-id="fbf59-119">Ensure</span><span class="sxs-lookup"><span data-stu-id="fbf59-119">Ensure</span></span>| <span data-ttu-id="fbf59-120">Bestimmt, ob geprüft wird, ob der Inhalt der Archivdatei am __Ziel__ vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="fbf59-120">Determines whether to check if the content of the archive exists at the __Destination__.</span></span> <span data-ttu-id="fbf59-121">Legen Sie diese Eigenschaft auf __Present__ fest, um sicherzustellen, dass der Inhalt vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="fbf59-121">Set this property to __Present__ to ensure the contents exist.</span></span> <span data-ttu-id="fbf59-122">Legen Sie sie auf __Absent__ fest, um sicherzustellen, dass der Inhalt nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="fbf59-122">Set it to __Absent__ to ensure they do not exist.</span></span> <span data-ttu-id="fbf59-123">Der Standardwert ist __Present__.</span><span class="sxs-lookup"><span data-stu-id="fbf59-123">The default value is __Present__.</span></span>|
| <span data-ttu-id="fbf59-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="fbf59-124">DependsOn</span></span> | <span data-ttu-id="fbf59-125">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="fbf59-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="fbf59-126">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="fbf59-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="fbf59-127">Überprüfen</span><span class="sxs-lookup"><span data-stu-id="fbf59-127">Validate</span></span>| <span data-ttu-id="fbf59-128">Verwendet die Eigenschaft „Checksum“, um zu bestimmen, ob das Archiv der Signatur entspricht.</span><span class="sxs-lookup"><span data-stu-id="fbf59-128">Uses the Checksum property to determine if the archive matches the signature.</span></span> <span data-ttu-id="fbf59-129">Wenn Sie „Checksum“ ohne „Validate“ angeben, schlägt die Konfiguration fehl.</span><span class="sxs-lookup"><span data-stu-id="fbf59-129">If you specify Checksum without Validate, the configuration will fail.</span></span> <span data-ttu-id="fbf59-130">Wenn Sie „Validate“ ohne „Checksum“ angeben, wird standardmäßig eine SHA-256-Prüfsumme verwendet.</span><span class="sxs-lookup"><span data-stu-id="fbf59-130">If you specify Validate without Checksum, a SHA-256 checksum is used by default.</span></span>|
| <span data-ttu-id="fbf59-131">Force</span><span class="sxs-lookup"><span data-stu-id="fbf59-131">Force</span></span>| <span data-ttu-id="fbf59-132">Bestimmte Dateioperationen (z. B. das Überschreiben einer Datei oder Löschen eines Verzeichnisses, das nicht leer ist), führen zu einem Fehler.</span><span class="sxs-lookup"><span data-stu-id="fbf59-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="fbf59-133">Bei Verwenden der Eigenschaften „Force“ werden solche Fehler überschrieben.</span><span class="sxs-lookup"><span data-stu-id="fbf59-133">Using the Force property overrides such errors.</span></span> <span data-ttu-id="fbf59-134">Der Standardwert ist „False“.</span><span class="sxs-lookup"><span data-stu-id="fbf59-134">The default value is False.</span></span>|

## <a name="example"></a><span data-ttu-id="fbf59-135">Beispiel</span><span class="sxs-lookup"><span data-stu-id="fbf59-135">Example</span></span>

<span data-ttu-id="fbf59-136">Im folgenden Beispiel wird veranschaulicht, wie Sie die Ressource „Archive“ verwenden, um sicherzustellen, dass der Inhalt einer Archivdatei mit dem Namen „Test.zip“ vorhanden ist und an ein bestimmtes Ziel extrahiert wird.</span><span class="sxs-lookup"><span data-stu-id="fbf59-136">The following example shows how to use the Archive resource to ensure that the contents of an archive file called Test.zip exist and are extracted at a given destination.</span></span>

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```