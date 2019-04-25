---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Das ISESnippetCollection-Objekt
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086668"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="4ce45-103">Das ISESnippetCollection-Objekt</span><span class="sxs-lookup"><span data-stu-id="4ce45-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="4ce45-104">Das **ISESnippetCollection**-Objekt ist eine Sammlung von **ISESnippet**-Objekten.</span><span class="sxs-lookup"><span data-stu-id="4ce45-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="4ce45-105">Die einem **PowerShellTab**-Objekt zugeordnete Dateisammlung ist ein Member dieser Klasse.</span><span class="sxs-lookup"><span data-stu-id="4ce45-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="4ce45-106">Ein Beispiel ist die **$psISE.CurrentPowerShellTab.Files**-Sammlung.</span><span class="sxs-lookup"><span data-stu-id="4ce45-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="4ce45-107">Methoden</span><span class="sxs-lookup"><span data-stu-id="4ce45-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="4ce45-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="4ce45-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="4ce45-109">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="4ce45-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="4ce45-110">Lädt eine .snippets.ps1xml-Datei mit benutzerdefinierten Codeausschnitten.</span><span class="sxs-lookup"><span data-stu-id="4ce45-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="4ce45-111">Die einfachste Möglichkeit zum Erstellen von Codeausschnitten ist das New-IseSnippet-Cmdlet, das sie automatisch im Profilordner speichert, sodass sie bei jedem Start von Windows PowerShell ISE geladen werden.</span><span class="sxs-lookup"><span data-stu-id="4ce45-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="4ce45-112">**FilePathName** – Zeichenfolge – der Pfad und der Dateiname für eine Datei mit der Erweiterung „.snippets.ps1xml“, die Codeausschnittdefinitionen enthält.</span><span class="sxs-lookup"><span data-stu-id="4ce45-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="4ce45-113">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4ce45-113">See Also</span></span>

- [<span data-ttu-id="4ce45-114">Das ISESnippet-Objekt</span><span class="sxs-lookup"><span data-stu-id="4ce45-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="4ce45-115">Zweck des Windows PowerShell ISE-Skriptobjektmodells</span><span class="sxs-lookup"><span data-stu-id="4ce45-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="4ce45-116">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="4ce45-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)