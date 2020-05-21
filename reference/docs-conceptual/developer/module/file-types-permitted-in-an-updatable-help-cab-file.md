---
title: In einer aktualisierbaren Hilfe-CAB-Datei zulässige Dateitypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 6e9e51a50226430465726d27874e02e98ee67672
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560983"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="5581c-102">Zulässige Dateitypen in aktualisierbaren CAB-Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="5581c-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="5581c-103">In diesem Thema werden die Inhalts Anforderungen für die aktualisierbaren Hilfe-CAB-Dateien aufgelistet und beschrieben.</span><span class="sxs-lookup"><span data-stu-id="5581c-103">This topics lists and describes the content requirements for Updatable Help CAB files.</span></span>

## <a name="updatable-help-cab-file-requirements"></a><span data-ttu-id="5581c-104">Aktualisierbare Hilfe-CAB-Datei Anforderungen</span><span class="sxs-lookup"><span data-stu-id="5581c-104">Updatable Help CAB File Requirements</span></span>

<span data-ttu-id="5581c-105">Der Inhalt nicht komprimierter CAB-Dateien ist standardmäßig auf 1 GB beschränkt.</span><span class="sxs-lookup"><span data-stu-id="5581c-105">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="5581c-106">Um diese Beschränkung zu umgehen, müssen die Benutzer den **Force** -Parameter der Cmdlets " [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) " und " [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) " verwenden.</span><span class="sxs-lookup"><span data-stu-id="5581c-106">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="5581c-107">Um die Sicherheit von Hilfedateien sicherzustellen, die aus dem Internet heruntergeladen werden, kann eine aktualisierbare CAB-Hilfedatei nur die unten aufgeführten Dateitypen enthalten.</span><span class="sxs-lookup"><span data-stu-id="5581c-107">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="5581c-108">Das [Update-Help-](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlet überprüft alle Dateien anhand der Hilfe Themen Schemas.</span><span class="sxs-lookup"><span data-stu-id="5581c-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="5581c-109">Wenn das `Update-Help` Cmdlet auf eine Datei trifft, die ungültig ist oder kein zulässiger Typ ist, wird die ungültige Datei nicht installiert, und die Installation von Dateien aus dem CAB auf dem Computer des Benutzers wird beendet.</span><span class="sxs-lookup"><span data-stu-id="5581c-109">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="5581c-110">XML-basierte Hilfe Themen für Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="5581c-110">XML-based help topics for cmdlets.</span></span>

- <span data-ttu-id="5581c-111">XML-basierte Hilfe Themen für Skripts und Funktionen.</span><span class="sxs-lookup"><span data-stu-id="5581c-111">XML-based help topics for scripts and functions.</span></span>

- <span data-ttu-id="5581c-112">XML-basierte Hilfe Themen für Windows PowerShell-Anbieter.</span><span class="sxs-lookup"><span data-stu-id="5581c-112">XML-based help topics for Windows PowerShell providers.</span></span>

- <span data-ttu-id="5581c-113">Text basierte Hilfe Themen, z. b. Informationen zu Themen.</span><span class="sxs-lookup"><span data-stu-id="5581c-113">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="5581c-114">Mit [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) werden die CAB-Inhalte überprüft, wenn die CAB-Datei entpackt wird.</span><span class="sxs-lookup"><span data-stu-id="5581c-114">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="5581c-115">Wenn `Update-Help` nicht kompatible Dateitypen in einer aktualisierbaren Hilfe-CAB-Datei findet, wird ein Beendigungs Fehler generiert und der Vorgang beendet.</span><span class="sxs-lookup"><span data-stu-id="5581c-115">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="5581c-116">Er installiert keine Hilfedateien aus dem CAB, auch die von kompatiblen Dateitypen.</span><span class="sxs-lookup"><span data-stu-id="5581c-116">It does not install any help files from the CAB, even those of compliant file types.</span></span>
