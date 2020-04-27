---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC-Ressourcen „Archive“
ms.openlocfilehash: ddabe1a623783fe213b8059f47851184d5253fc5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954767"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="a0f54-103">DSC-Ressourcen „Archive“</span><span class="sxs-lookup"><span data-stu-id="a0f54-103">DSC Archive Resource</span></span>

> <span data-ttu-id="a0f54-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="a0f54-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="a0f54-105">Die Ressource „Archive“ in Windows PowerShell DSC bietet einen Mechanismus zum Entpacken von Archivdateien (.zip).</span><span class="sxs-lookup"><span data-stu-id="a0f54-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="a0f54-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a0f54-106">Syntax</span></span>

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="a0f54-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="a0f54-107">Properties</span></span>

|<span data-ttu-id="a0f54-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="a0f54-108">Property</span></span> |<span data-ttu-id="a0f54-109">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="a0f54-109">Description</span></span> |
|---|---|
|<span data-ttu-id="a0f54-110">Destination</span><span class="sxs-lookup"><span data-stu-id="a0f54-110">Destination</span></span> |<span data-ttu-id="a0f54-111">Gibt den Speicherort an, an dem der Archivinhalt einer Datei extrahiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="a0f54-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
|<span data-ttu-id="a0f54-112">`Path`</span><span class="sxs-lookup"><span data-stu-id="a0f54-112">Path</span></span> |<span data-ttu-id="a0f54-113">Gibt den Quellpfad der Archivdatei an.</span><span class="sxs-lookup"><span data-stu-id="a0f54-113">Specifies the source path of the archive file.</span></span> |
|<span data-ttu-id="a0f54-114">Checksum</span><span class="sxs-lookup"><span data-stu-id="a0f54-114">Checksum</span></span> |<span data-ttu-id="a0f54-115">Definiert den zu verwendenden Typ, wenn bestimmt wird, ob zwei Dateien identisch sind.</span><span class="sxs-lookup"><span data-stu-id="a0f54-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="a0f54-116">Wenn **Checksum** nicht angegeben ist, wird nur der Datei- oder Verzeichnisnamen für den Vergleich verwendet.</span><span class="sxs-lookup"><span data-stu-id="a0f54-116">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="a0f54-117">Gültige Werte: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span><span class="sxs-lookup"><span data-stu-id="a0f54-117">Valid values include: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span></span> <span data-ttu-id="a0f54-118">Wenn Sie **Checksum** ohne **Validate** angeben, schlägt die Konfiguration fehl.</span><span class="sxs-lookup"><span data-stu-id="a0f54-118">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> |
|<span data-ttu-id="a0f54-119">Force</span><span class="sxs-lookup"><span data-stu-id="a0f54-119">Force</span></span> |<span data-ttu-id="a0f54-120">Bestimmte Dateioperationen (z. B. das Überschreiben einer Datei oder Löschen eines Verzeichnisses, das nicht leer ist), führen zu einem Fehler.</span><span class="sxs-lookup"><span data-stu-id="a0f54-120">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="a0f54-121">Bei Verwenden der **Force**-Eigenschaft werden solche Fehler überschrieben.</span><span class="sxs-lookup"><span data-stu-id="a0f54-121">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="a0f54-122">Der Standardwert ist **False**.</span><span class="sxs-lookup"><span data-stu-id="a0f54-122">The default value is **False**.</span></span> |
|<span data-ttu-id="a0f54-123">Überprüfen</span><span class="sxs-lookup"><span data-stu-id="a0f54-123">Validate</span></span>| <span data-ttu-id="a0f54-124">Verwendet die Eigenschaft **Checksum**, um zu bestimmen, ob das Archiv der Signatur entspricht.</span><span class="sxs-lookup"><span data-stu-id="a0f54-124">Uses the **Checksum** property to determine if the archive matches the signature.</span></span> <span data-ttu-id="a0f54-125">Wenn Sie **Checksum** ohne **Validate** angeben, schlägt die Konfiguration fehl.</span><span class="sxs-lookup"><span data-stu-id="a0f54-125">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> <span data-ttu-id="a0f54-126">Wenn Sie **Validate** ohne **Checksum** angeben, wird standardmäßig eine _SHA-256_-**Prüfsumme** verwendet.</span><span class="sxs-lookup"><span data-stu-id="a0f54-126">If you specify **Validate** without **Checksum**, a _SHA-256_ **Checksum** is used by default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="a0f54-127">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="a0f54-127">Common properties</span></span>

|<span data-ttu-id="a0f54-128">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="a0f54-128">Property</span></span> |<span data-ttu-id="a0f54-129">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="a0f54-129">Description</span></span> |
|---|---|
|<span data-ttu-id="a0f54-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a0f54-130">DependsOn</span></span> |<span data-ttu-id="a0f54-131">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="a0f54-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a0f54-132">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a0f54-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="a0f54-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="a0f54-133">Ensure</span></span> |<span data-ttu-id="a0f54-134">Bestimmt, ob geprüft wird, ob der Inhalt der Archivdatei am **Ziel** vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="a0f54-134">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="a0f54-135">Legen Sie diese Eigenschaft auf **Present** fest, um sicherzustellen, dass der Inhalt vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="a0f54-135">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="a0f54-136">Legen Sie sie auf **Absent** fest, um sicherzustellen, dass der Inhalt nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="a0f54-136">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="a0f54-137">Der Standardwert ist **Present**.</span><span class="sxs-lookup"><span data-stu-id="a0f54-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="a0f54-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="a0f54-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="a0f54-139">Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest.</span><span class="sxs-lookup"><span data-stu-id="a0f54-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="a0f54-140">Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="a0f54-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="a0f54-141">Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).</span><span class="sxs-lookup"><span data-stu-id="a0f54-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="a0f54-142">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a0f54-142">Example</span></span>

<span data-ttu-id="a0f54-143">Im folgenden Beispiel wird veranschaulicht, wie Sie die Ressource „Archive“ verwenden, um sicherzustellen, dass der Inhalt einer Archivdatei mit dem Namen `Test.zip` vorhanden ist und an einem bestimmten Zielspeicherort extrahiert wird.</span><span class="sxs-lookup"><span data-stu-id="a0f54-143">The following example shows how to use the Archive resource to ensure that the contents of an archive file called `Test.zip` exist and are extracted at a given destination.</span></span>

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```