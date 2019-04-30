---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressourcen „Archive“
ms.openlocfilehash: d5ccd242d000a0907c6768f30923764be6bf20a3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077550"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="e651e-103">DSC-Ressourcen „Archive“</span><span class="sxs-lookup"><span data-stu-id="e651e-103">DSC Archive Resource</span></span>

> <span data-ttu-id="e651e-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e651e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e651e-105">Die Ressource „Archive“ in Windows PowerShell DSC bietet einen Mechanismus zum Entpacken von Archivdateien (.zip).</span><span class="sxs-lookup"><span data-stu-id="e651e-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="e651e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e651e-106">Syntax</span></span>
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

## <a name="properties"></a><span data-ttu-id="e651e-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="e651e-107">Properties</span></span>

|  <span data-ttu-id="e651e-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="e651e-108">Property</span></span>  |  <span data-ttu-id="e651e-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e651e-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="e651e-110">Ziel</span><span class="sxs-lookup"><span data-stu-id="e651e-110">Destination</span></span>| <span data-ttu-id="e651e-111">Gibt den Speicherort an, an dem der Archivinhalt einer Datei extrahiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="e651e-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="e651e-112">Pfad</span><span class="sxs-lookup"><span data-stu-id="e651e-112">Path</span></span>| <span data-ttu-id="e651e-113">Gibt den Quellpfad der Archivdatei an.</span><span class="sxs-lookup"><span data-stu-id="e651e-113">Specifies the source path of the archive file.</span></span>|
| <span data-ttu-id="e651e-114">__Checksum__</span><span class="sxs-lookup"><span data-stu-id="e651e-114">__Checksum__</span></span>| <span data-ttu-id="e651e-115">Definiert den zu verwendenden Typ, wenn bestimmt wird, ob zwei Dateien identisch sind.</span><span class="sxs-lookup"><span data-stu-id="e651e-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="e651e-116">Wenn __Checksum__ nicht angegeben ist, wird nur der Datei- oder Verzeichnisnamen für den Vergleich verwendet.</span><span class="sxs-lookup"><span data-stu-id="e651e-116">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="e651e-117">Gültige Werte: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, keine (Standard).</span><span class="sxs-lookup"><span data-stu-id="e651e-117">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (default).</span></span> <span data-ttu-id="e651e-118">Wenn Sie __Checksum__ ohne __Validate__ angeben, schlägt die Konfiguration fehl.</span><span class="sxs-lookup"><span data-stu-id="e651e-118">If you specify __Checksum__ without __Validate__, the configuration will fail.</span></span>|
| <span data-ttu-id="e651e-119">Ensure</span><span class="sxs-lookup"><span data-stu-id="e651e-119">Ensure</span></span>| <span data-ttu-id="e651e-120">Bestimmt, ob geprüft wird, ob der Inhalt der Archivdatei am __Ziel__ vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="e651e-120">Determines whether to check if the content of the archive exists at the __Destination__.</span></span> <span data-ttu-id="e651e-121">Legen Sie diese Eigenschaft auf __Present__ fest, um sicherzustellen, dass der Inhalt vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="e651e-121">Set this property to __Present__ to ensure the contents exist.</span></span> <span data-ttu-id="e651e-122">Legen Sie sie auf __Absent__ fest, um sicherzustellen, dass der Inhalt nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="e651e-122">Set it to __Absent__ to ensure they do not exist.</span></span> <span data-ttu-id="e651e-123">Der Standardwert ist __Present__.</span><span class="sxs-lookup"><span data-stu-id="e651e-123">The default value is __Present__.</span></span>|
| <span data-ttu-id="e651e-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e651e-124">DependsOn</span></span> | <span data-ttu-id="e651e-125">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="e651e-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e651e-126">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="e651e-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="e651e-127">Überprüfen</span><span class="sxs-lookup"><span data-stu-id="e651e-127">Validate</span></span>| <span data-ttu-id="e651e-128">Verwendet die Eigenschaft „Checksum“, um zu bestimmen, ob das Archiv der Signatur entspricht.</span><span class="sxs-lookup"><span data-stu-id="e651e-128">Uses the Checksum property to determine if the archive matches the signature.</span></span> <span data-ttu-id="e651e-129">Wenn Sie „Checksum“ ohne „Validate“ angeben, schlägt die Konfiguration fehl.</span><span class="sxs-lookup"><span data-stu-id="e651e-129">If you specify Checksum without Validate, the configuration will fail.</span></span> <span data-ttu-id="e651e-130">Wenn Sie „Validate“ ohne „Checksum“ angeben, wird standardmäßig eine SHA-256-Prüfsumme verwendet.</span><span class="sxs-lookup"><span data-stu-id="e651e-130">If you specify Validate without Checksum, a SHA-256 checksum is used by default.</span></span>|
| <span data-ttu-id="e651e-131">Force</span><span class="sxs-lookup"><span data-stu-id="e651e-131">Force</span></span>| <span data-ttu-id="e651e-132">Bestimmte Dateioperationen (z. B. das Überschreiben einer Datei oder Löschen eines Verzeichnisses, das nicht leer ist), führen zu einem Fehler.</span><span class="sxs-lookup"><span data-stu-id="e651e-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="e651e-133">Bei Verwenden der Eigenschaften „Force“ werden solche Fehler überschrieben.</span><span class="sxs-lookup"><span data-stu-id="e651e-133">Using the Force property overrides such errors.</span></span> <span data-ttu-id="e651e-134">Der Standardwert ist „False“.</span><span class="sxs-lookup"><span data-stu-id="e651e-134">The default value is False.</span></span>|

## <a name="example"></a><span data-ttu-id="e651e-135">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e651e-135">Example</span></span>

<span data-ttu-id="e651e-136">Im folgenden Beispiel wird veranschaulicht, wie Sie die Ressource „Archive“ verwenden, um sicherzustellen, dass der Inhalt einer Archivdatei mit dem Namen „Test.zip“ vorhanden ist und an ein bestimmtes Ziel extrahiert wird.</span><span class="sxs-lookup"><span data-stu-id="e651e-136">The following example shows how to use the Archive resource to ensure that the contents of an archive file called Test.zip exist and are extracted at a given destination.</span></span>

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```