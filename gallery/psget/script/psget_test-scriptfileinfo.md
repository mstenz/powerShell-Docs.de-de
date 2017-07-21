---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Test-ScriptFileInfo
ms.openlocfilehash: 0f6951b86bba352e33abe91fc76e000b7df75b49
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="test-scriptfileinfo"></a><span data-ttu-id="6d2b3-103">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="6d2b3-103">Test-ScriptFileInfo</span></span>

<span data-ttu-id="6d2b3-104">Überprüft den Metadaten-Kommentarblock einer Skriptdatei</span><span class="sxs-lookup"><span data-stu-id="6d2b3-104">Validates the metadata comment block of a script file.</span></span>

## <a name="description"></a><span data-ttu-id="6d2b3-105">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6d2b3-105">Description</span></span>

<span data-ttu-id="6d2b3-106">Das Cmdlet „Test-ScriptFileInfo“ überprüft den Kommentarblock am Anfang eines Skripts, das mithilfe des Cmdlets „Publish-Script“ veröffentlicht wird.</span><span class="sxs-lookup"><span data-stu-id="6d2b3-106">The Test-ScriptFileInfo cmdlet validates the comment block at the beginning of a script that will be published with the Publish-Script cmdlet.</span></span>
<span data-ttu-id="6d2b3-107">Wenn der Metadaten-Kommentarblock einen Fehler enthält, gibt dieses Cmdlet Informationen darüber zurück, wo sich der Fehler befindet oder wie er behoben werden kann.</span><span class="sxs-lookup"><span data-stu-id="6d2b3-107">If the metadata comment block has an error, this cmdlet returns information about where the error is located or how to correct it.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="6d2b3-108">Cmdlet-Syntax</span><span class="sxs-lookup"><span data-stu-id="6d2b3-108">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Test-ScriptFileInfo -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="6d2b3-109">Cmdlet-Onlinehilfe</span><span class="sxs-lookup"><span data-stu-id="6d2b3-109">Cmdlet online help reference</span></span>

[<span data-ttu-id="6d2b3-110">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="6d2b3-110">Test-ScriptFileInfo</span></span>](http://go.microsoft.com/fwlink/?LinkId=619791)

## <a name="example-commands"></a><span data-ttu-id="6d2b3-111">Beispiele für Befehle</span><span class="sxs-lookup"><span data-stu-id="6d2b3-111">Example commands</span></span>
```powershell
# Create a new script file with minimum required metadata values
New-ScriptFileInfo -Path C:\ScriptSharingDemo\Demo-Script.ps1 -Description "Script file description goes here"

Get-Content -Path C:\ScriptSharingDemo\Demo-Script.ps1
<#PSScriptInfo
.VERSION 1.0
.GUID 926b47c3-6af2-4b18-b6f5-8b813a9e93ab
.AUTHOR manikb
.COMPANYNAME
.COPYRIGHT
.TAGS
.LICENSEURI
.PROJECTURI
.ICONURI
.EXTERNALMODULEDEPENDENCIES
.REQUIREDSCRIPTS
.EXTERNALSCRIPTDEPENDENCIES
.RELEASENOTES
#>
<#
.DESCRIPTION
Script file description goes here
#>
Param()

# Validate and get the script metadata
Test-ScriptFileInfo -Path C:\ScriptSharingDemo\Demo-Script.ps1
Version Name Author Description
------- ---- ------ -----------
1.0 Demo-Script manikb Script file description goes here

# This command tests the script file Test-Runbook.ps1 and uses the pipeline operator to pass the results to the Format-List cmdlet to format the results.
Test-ScriptFileInfo -Path D:\code\Test-Runbook.ps1 | Format-List *

# This command tests the script file Hello-World.ps1, which has no metadata associated with it.
Test-ScriptFileInfo -Path C:\code\Hello-World.ps1
Test-ScriptFileInfo : PSScriptInfo is not specified in the script file 'C:\code\Hello-World.ps1'. You can use the Update-ScriptFileInfo with -Force or New-ScriptFileInfo cmdlet to add the PSScriptInfo to the script file.
At line:1 char:1
+ Test-ScriptFileInfo -Path C:\code\Hello-World.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (C:\code\Hello-World.ps1:String) [Test-ScriptFileInfo], ArgumentException
    + FullyQualifiedErrorId : MissingPSScriptInfo,Test-ScriptFileInfo

```

