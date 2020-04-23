---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Das ISESnippetCollection-Objekt
ms.openlocfilehash: 6cdc43dd1d82e94f66122d7f7b313c02e755fed7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736044"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="a1f1f-103">Das ISESnippetCollection-Objekt</span><span class="sxs-lookup"><span data-stu-id="a1f1f-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="a1f1f-104">Das **ISESnippetCollection**-Objekt ist eine Sammlung von **ISESnippet**-Objekten.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="a1f1f-105">Die einem **PowerShellTab**-Objekt zugeordnete Dateisammlung ist ein Member dieser Klasse.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="a1f1f-106">Ein Beispiel ist die `$psISE.CurrentPowerShellTab.Files`-Auflistung.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-106">An example is the `$psISE.CurrentPowerShellTab.Files` collection.</span></span>

## <a name="methods"></a><span data-ttu-id="a1f1f-107">Methoden</span><span class="sxs-lookup"><span data-stu-id="a1f1f-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="a1f1f-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="a1f1f-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="a1f1f-109">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="a1f1f-110">Lädt eine `.snippets.ps1xml`-Datei mit benutzerdefinierten Codeausschnitten.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-110">Loads a `.snippets.ps1xml` file that contains user-defined snippets.</span></span> <span data-ttu-id="a1f1f-111">Die einfachste Möglichkeit zum Erstellen von Codeausschnitten ist das `New-IseSnippet`-Cmdlet, das die Ausschnitte automatisch im Profilordner speichert, sodass sie bei jedem Start der Windows PowerShell ISE geladen werden.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-111">The easiest way to create snippets is to use the `New-IseSnippet` cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="a1f1f-112">**FilePathName** – Zeichenfolge – der Pfad und der Dateiname für eine Datei mit der Erweiterung „.snippets.ps1xml“, die Codeausschnittdefinitionen enthält.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="a1f1f-113">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a1f1f-113">See Also</span></span>

- [<span data-ttu-id="a1f1f-114">Das ISESnippet-Objekt</span><span class="sxs-lookup"><span data-stu-id="a1f1f-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="a1f1f-115">Zweck des Windows PowerShell ISE-Skriptobjektmodells</span><span class="sxs-lookup"><span data-stu-id="a1f1f-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="a1f1f-116">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="a1f1f-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
