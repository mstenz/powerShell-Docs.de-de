---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Save-Script
ms.openlocfilehash: 67697fc0e70fb31cad9ad5ae7ce01debef160b81
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="save-script"></a><span data-ttu-id="9afb7-103">Save-Script</span><span class="sxs-lookup"><span data-stu-id="9afb7-103">Save-Script</span></span>

<span data-ttu-id="9afb7-104">Mit dem Cmdlet „Save-Script“ können Sie die Skriptdatei überprüfen, indem Sie sie an einem angegebenen Speicherort speichern.</span><span class="sxs-lookup"><span data-stu-id="9afb7-104">Save-Script cmdlet lets you to review the script file by saving it to a specified location.</span></span>

## <a name="description"></a><span data-ttu-id="9afb7-105">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9afb7-105">Description</span></span>

<span data-ttu-id="9afb7-106">Das Cmdlet „Save-Script“ speichert das angegebene Skript.</span><span class="sxs-lookup"><span data-stu-id="9afb7-106">The Save-Script cmdlet saves the specified script.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="9afb7-107">Cmdlet-Syntax</span><span class="sxs-lookup"><span data-stu-id="9afb7-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="9afb7-108">Cmdlet-Onlinehilfe</span><span class="sxs-lookup"><span data-stu-id="9afb7-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="9afb7-109">Save-Script</span><span class="sxs-lookup"><span data-stu-id="9afb7-109">Save-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a><span data-ttu-id="9afb7-110">Beispiele für Befehle</span><span class="sxs-lookup"><span data-stu-id="9afb7-110">Example commands</span></span>

### <a name="example-1-save-a-script-from-a-repository"></a><span data-ttu-id="9afb7-111">Beispiel 1: Speichern eines Skripts aus einem Repository</span><span class="sxs-lookup"><span data-stu-id="9afb7-111">Example 1: Save a script from a repository</span></span>
<span data-ttu-id="9afb7-112">Dieser Befehl speichert die neueste Version des Skripts „Fabrikam-ClientScript“ aus dem Repository „GalleryINT“ im lokalen Ordner „C:\ScriptSharingDemo“.</span><span class="sxs-lookup"><span data-stu-id="9afb7-112">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a><span data-ttu-id="9afb7-113">Beispiel 2: Speichern einer Version eines Skripts durch Weiterreichen vom Cmdlet „Find-Script“</span><span class="sxs-lookup"><span data-stu-id="9afb7-113">Example 2: Save a version of a script by piping from the Find-Script cmdlet</span></span>

<span data-ttu-id="9afb7-114">Der erste Befehl sucht nach Version 1.5 von „Fabrikam-ClientScript“ vom Repository „GalleryINT“ und speichert sie im Ordner „C:\ScriptSharingDemo“.</span><span class="sxs-lookup"><span data-stu-id="9afb7-114">The first command finds version 1.5 of Fabrikam-ClientScript from the repository GalleryINT and saves it to the folder C:\ScriptSharingDemo</span></span>

<span data-ttu-id="9afb7-115">Der zweite Befehl überprüft die Metadaten des gespeicherten Skripts.</span><span class="sxs-lookup"><span data-stu-id="9afb7-115">The second command validates the saved script metadata.</span></span>

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a><span data-ttu-id="9afb7-116">Beispiel 3: Speichern einer Vorabversion eines Skripts aus einem Repository</span><span class="sxs-lookup"><span data-stu-id="9afb7-116">Example 3: Save a prerelease version of a script from a repository</span></span>
<span data-ttu-id="9afb7-117">Dieser Befehl speichert die neueste Version des Skripts „Fabrikam-ClientScript“ aus dem Repository „GalleryINT“ im lokalen Ordner „C:\ScriptSharingDemo“.</span><span class="sxs-lookup"><span data-stu-id="9afb7-117">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```