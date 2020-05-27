---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC für Linux-Resource „nxArchive“
ms.openlocfilehash: 56f8df65945f16a93c69407ea30f51878a201b63
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560915"
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="72bf8-103">DSC für Linux-Resource „nxArchive“</span><span class="sxs-lookup"><span data-stu-id="72bf8-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="72bf8-104">Die Ressource **nxArchive** in PowerShell DSC bietet einen Mechanismus zum Entpacken von Archivdateien (.tar, .zip) in einem bestimmten Pfad auf einem Linux-Knoten.</span><span class="sxs-lookup"><span data-stu-id="72bf8-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="72bf8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="72bf8-105">Syntax</span></span>

```Syntax
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="72bf8-106">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="72bf8-106">Properties</span></span>

|<span data-ttu-id="72bf8-107">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="72bf8-107">Property</span></span> |<span data-ttu-id="72bf8-108">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="72bf8-108">Description</span></span> |
|---|---|
|<span data-ttu-id="72bf8-109">SourcePath</span><span class="sxs-lookup"><span data-stu-id="72bf8-109">SourcePath</span></span> |<span data-ttu-id="72bf8-110">Gibt den Quellpfad der Archivdatei an.</span><span class="sxs-lookup"><span data-stu-id="72bf8-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="72bf8-111">Dies muss eine Datei des Typs „.tar“, „.zip“ oder „.tar.gz“ sein.</span><span class="sxs-lookup"><span data-stu-id="72bf8-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
|<span data-ttu-id="72bf8-112">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="72bf8-112">DestinationPath</span></span> |<span data-ttu-id="72bf8-113">Gibt den Speicherort an, an dem der Archivinhalt einer Datei extrahiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="72bf8-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
|<span data-ttu-id="72bf8-114">Checksum</span><span class="sxs-lookup"><span data-stu-id="72bf8-114">Checksum</span></span> |<span data-ttu-id="72bf8-115">Definiert den zu verwendenden Typ, wenn bestimmt wird, ob das Quellarchiv aktualisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="72bf8-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="72bf8-116">Werte sind: **ctime**, **mtime** oder **md5**.</span><span class="sxs-lookup"><span data-stu-id="72bf8-116">Values are: **ctime**, **mtime**, or **md5**.</span></span> <span data-ttu-id="72bf8-117">Der Standardwert ist **md5**.</span><span class="sxs-lookup"><span data-stu-id="72bf8-117">The default value is **md5**.</span></span> |
|<span data-ttu-id="72bf8-118">Force</span><span class="sxs-lookup"><span data-stu-id="72bf8-118">Force</span></span> |<span data-ttu-id="72bf8-119">Bestimmte Dateioperationen (z. B. das Überschreiben einer Datei oder Löschen eines Verzeichnisses, das nicht leer ist), führen zu einem Fehler.</span><span class="sxs-lookup"><span data-stu-id="72bf8-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="72bf8-120">Bei Verwenden der **Force**-Eigenschaft werden solche Fehler überschrieben.</span><span class="sxs-lookup"><span data-stu-id="72bf8-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="72bf8-121">Standardwert: `$false`.</span><span class="sxs-lookup"><span data-stu-id="72bf8-121">The default value is `$false`.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="72bf8-122">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="72bf8-122">Common properties</span></span>

|<span data-ttu-id="72bf8-123">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="72bf8-123">Property</span></span> |<span data-ttu-id="72bf8-124">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="72bf8-124">Description</span></span> |
|---|---|
|<span data-ttu-id="72bf8-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="72bf8-125">DependsOn</span></span> |<span data-ttu-id="72bf8-126">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="72bf8-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="72bf8-127">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="72bf8-127">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="72bf8-128">Ensure</span><span class="sxs-lookup"><span data-stu-id="72bf8-128">Ensure</span></span> |<span data-ttu-id="72bf8-129">Bestimmt, ob geprüft wird, ob der Inhalt der Archivdatei am **Ziel** vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="72bf8-129">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="72bf8-130">Legen Sie diese Eigenschaft auf **Present** fest, um sicherzustellen, dass der Inhalt vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="72bf8-130">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="72bf8-131">Legen Sie sie auf **Absent** fest, um sicherzustellen, dass der Inhalt nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="72bf8-131">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="72bf8-132">Der Standardwert ist **Present**.</span><span class="sxs-lookup"><span data-stu-id="72bf8-132">The default value is **Present**.</span></span> |

## <a name="example"></a><span data-ttu-id="72bf8-133">Beispiel</span><span class="sxs-lookup"><span data-stu-id="72bf8-133">Example</span></span>

<span data-ttu-id="72bf8-134">Im folgenden Beispiel wird veranschaulicht, wie Sie die Ressource **nxArchive** verwenden, um sicherzustellen, dass der Inhalt einer Archivdatei mit dem Namen `website.tar` vorhanden ist und an ein bestimmtes Ziel extrahiert wird.</span><span class="sxs-lookup"><span data-stu-id="72bf8-134">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

```powershell
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = "http://release.contoso.com/releases/website.tar"
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = "mtime"
}

nxArchive SyncWebDir
{
   SourcePath = "/usr/release/staging/website.tar"
   DestinationPath = "/usr/local/apache2/htdocs/"
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```
