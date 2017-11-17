---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Save-Script
ms.openlocfilehash: 7b692d33e3f86a89505b8d37c0da4177f3dff2c2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="save-script"></a><span data-ttu-id="ae02a-103">Save-Script</span><span class="sxs-lookup"><span data-stu-id="ae02a-103">Save-Script</span></span>

<span data-ttu-id="ae02a-104">Mit dem Cmdlet „Save-Script“ können Sie die Skriptdatei überprüfen, indem Sie sie an einem angegebenen Speicherort speichern.</span><span class="sxs-lookup"><span data-stu-id="ae02a-104">Save-Script cmdlet lets you to review the script file by saving it to a specified location.</span></span>

## <a name="description"></a><span data-ttu-id="ae02a-105">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ae02a-105">Description</span></span>

<span data-ttu-id="ae02a-106">Das Cmdlet „Save-Script“ speichert das angegebene Skript.</span><span class="sxs-lookup"><span data-stu-id="ae02a-106">The Save-Script cmdlet saves the specified script.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="ae02a-107">Cmdlet-Syntax</span><span class="sxs-lookup"><span data-stu-id="ae02a-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="ae02a-108">Cmdlet-Onlinehilfe</span><span class="sxs-lookup"><span data-stu-id="ae02a-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="ae02a-109">Save-Script</span><span class="sxs-lookup"><span data-stu-id="ae02a-109">Save-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a><span data-ttu-id="ae02a-110">Beispiele für Befehle</span><span class="sxs-lookup"><span data-stu-id="ae02a-110">Example commands</span></span>

### <a name="example-1-save-a-script-from-a-repository"></a><span data-ttu-id="ae02a-111">Beispiel 1: Speichern eines Skripts aus einem Repository</span><span class="sxs-lookup"><span data-stu-id="ae02a-111">Example 1: Save a script from a repository</span></span>
<span data-ttu-id="ae02a-112">Dieser Befehl speichert die neueste Version des Skripts „Fabrikam-ClientScript“ aus dem Repository „GalleryINT“ im lokalen Ordner „C:\ScriptSharingDemo“.</span><span class="sxs-lookup"><span data-stu-id="ae02a-112">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a><span data-ttu-id="ae02a-113">Beispiel 2: Speichern einer Version eines Skripts durch Weiterreichen vom Cmdlet „Find-Script“</span><span class="sxs-lookup"><span data-stu-id="ae02a-113">Example 2: Save a version of a script by piping from the Find-Script cmdlet</span></span>

<span data-ttu-id="ae02a-114">Der erste Befehl sucht nach Version 1.5 von „Fabrikam-ClientScript“ vom Repository „GalleryINT“ und speichert sie im Ordner „C:\ScriptSharingDemo“.</span><span class="sxs-lookup"><span data-stu-id="ae02a-114">The first command finds version 1.5 of Fabrikam-ClientScript from the repository GalleryINT and saves it to the folder C:\ScriptSharingDemo</span></span>

<span data-ttu-id="ae02a-115">Der zweite Befehl überprüft die Metadaten des gespeicherten Skripts.</span><span class="sxs-lookup"><span data-stu-id="ae02a-115">The second command validates the saved script metadata.</span></span>

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

