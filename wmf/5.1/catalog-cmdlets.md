---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Katalog-Cmdlets
ms.openlocfilehash: 7eaca09667af0eb5d719f23e987bb112e8514978
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189066"
---
# <a name="catalog-cmdlets"></a><span data-ttu-id="03384-103">Katalog-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="03384-103">Catalog Cmdlets</span></span>

<span data-ttu-id="03384-104">Dem [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx)-Modul wurden zwei neue Cmdlets hinzugefügt. Sie generieren und überprüfen Windows-Katalogdateien.</span><span class="sxs-lookup"><span data-stu-id="03384-104">We have added two new cmdlets in [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) module to generate and validate windows catalog files.</span></span>

## <a name="new-filecatalog"></a><span data-ttu-id="03384-105">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="03384-105">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="03384-106">`New-FileCatalog` erstellt eine Windows-Katalogdatei für eine Gruppe von Ordnern und Dateien.</span><span class="sxs-lookup"><span data-stu-id="03384-106">`New-FileCatalog` creates a windows catalog file for set of folders and files.</span></span> <span data-ttu-id="03384-107">Eine Katalogdatei enthält die Hashes aller Dateien in bestimmten Pfaden.</span><span class="sxs-lookup"><span data-stu-id="03384-107">A catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="03384-108">Benutzer können den Satz von Ordnern zusammen mit den entsprechenden Katalogdateien verteilen, die diese Ordner darstellen.</span><span class="sxs-lookup"><span data-stu-id="03384-108">Users can distribute the set of folders along with corresponding the catalog file that represents those folders.</span></span> <span data-ttu-id="03384-109">Eine Katalogdatei kann vom Empfänger des Inhalts verwendet werden, um zu überprüfen, ob an den Ordnern Änderungen vorgenommen wurden, nachdem der Katalog erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="03384-109">A catalog file can be used by the recipient of content to validate whether any changes were made to the folders after the catalog was created.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="03384-110">Unterstützt wird die Erstellung von Katalogversion 1 und 2.</span><span class="sxs-lookup"><span data-stu-id="03384-110">We support creating catalog version 1 and 2.</span></span> <span data-ttu-id="03384-111">Version 1 verwendet den SHA1-Hashalgorithmus, um Dateihashes zu erstellen, Version 2 verwendet SHA256.</span><span class="sxs-lookup"><span data-stu-id="03384-111">Version 1 uses SHA1 hashing algorithm to create file hashes and version 2 uses SHA256.</span></span> <span data-ttu-id="03384-112">Katalogversion 2 wird weder auf *Windows Server 2008 R2* noch auf *Windows 7* unterstützt.</span><span class="sxs-lookup"><span data-stu-id="03384-112">Catalog version 2 is not supported on *Windows Server 2008 R2* and *Windows 7*.</span></span> <span data-ttu-id="03384-113">Es wird empfohlen, Katalogversion 2 zu verwenden, wenn Sie Plattformen wie *Windows 8*, *Windows Server 2012* und höher nutzen.</span><span class="sxs-lookup"><span data-stu-id="03384-113">It is recommended to use catalog version 2 if using platforms *Windows 8*, *Windows Server 2012* and above.</span></span>

<span data-ttu-id="03384-114">Wenn Sie diesen Befehl auf ein bestehendes Modul anwenden möchten, müssen Sie die Variablen CatalogFilePath und Path gemäß des Speicherorts des Modulmanifests angeben.</span><span class="sxs-lookup"><span data-stu-id="03384-114">To use this command on an existing module, specify the CatalogFilePath and Path variables to match the location of the module manifest.</span></span> <span data-ttu-id="03384-115">Im nachstehenden Beispiel ist das Modulmanifest unter „C:\Program Files\Windows PowerShell\Modules\Pester“ gespeichert.</span><span class="sxs-lookup"><span data-stu-id="03384-115">In the example below, the module manifest is in C:\Program Files\Windows PowerShell\Modules\Pester.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="03384-116">Dadurch wird die Katalogdatei erstellt.</span><span class="sxs-lookup"><span data-stu-id="03384-116">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="03384-117">Die Katalogdatei (im obigen Beispiel: „pester.cat“) muss mit dem Cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) signiert werden, um ihre Integrität zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="03384-117">To verify the integrity of a catalog file (Pester.cat in above exmaple) it should be signed using the [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>


## <a name="test-filecatalog"></a><span data-ttu-id="03384-118">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="03384-118">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="03384-119">`Test-FileCatalog` überprüft den Katalog, der einen Satz von Ordnern darstellt.</span><span class="sxs-lookup"><span data-stu-id="03384-119">`Test-FileCatalog` validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="03384-120">Dieses Cmdlet vergleicht die Hashes aller Dateien und deren relative Pfade in der Katalogdatei mit denen, die auf dem Datenträger gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="03384-120">This cmdlet compares the hashes of all files and their relative paths found in the catalog file with ones saved to disk.</span></span> <span data-ttu-id="03384-121">Wenn das Cmdlet eine Unstimmigkeit zwischen den Dateihashes und den Pfaden entdeckt, gibt es den Status `ValidationFailed` zurück.</span><span class="sxs-lookup"><span data-stu-id="03384-121">If it detects any mismatch between file hashes and paths it returns a status of `ValidationFailed`.</span></span>
<span data-ttu-id="03384-122">Benutzer können alle diese Informationen mithilfe des Schalters `Detailed` abrufen.</span><span class="sxs-lookup"><span data-stu-id="03384-122">Users can retrieve all this information using the `Detailed` switch.</span></span> <span data-ttu-id="03384-123">Der Signierstatus des Katalogs wird im Feld `Signature` angezeigt, was dem Aufrufen des Cmdlets [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) für die Katalogdatei entspricht.</span><span class="sxs-lookup"><span data-stu-id="03384-123">The signing status of the catalog is displayed as the `Signature` field, which is same as calling the [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet on the catalog file.</span></span>
<span data-ttu-id="03384-124">Benutzer können außerdem jede Datei während der Überprüfung mithilfe des Parameters `FilesToSkip` überspringen.</span><span class="sxs-lookup"><span data-stu-id="03384-124">Users can also skip any file during validation by using the `FilesToSkip` parameter.</span></span>
