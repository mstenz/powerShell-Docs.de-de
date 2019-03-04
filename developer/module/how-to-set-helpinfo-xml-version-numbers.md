---
title: Festlegen der HelpInfo-XML-Versionsnummern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: 4929a5b1c9f73bb12b6df975e03fc529db3565ef
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863316"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="1daa2-102">Festlegen von XML-Versionsnummern für HelpInfo</span><span class="sxs-lookup"><span data-stu-id="1daa2-102">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="1daa2-103">In diesem Thema wird erläutert, wie Sie festlegen, und erhöhen die Versionsnummern in einer aktualisierbaren Hilfe-Informationen-Datei, die häufig als "HelpInfo XML-Datei." bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="1daa2-103">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="1daa2-104">Festlegen von XML-Versionsnummern für HelpInfo</span><span class="sxs-lookup"><span data-stu-id="1daa2-104">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="1daa2-105">Die Versionsnummern in einer HelpInfo XML-Datei sind entscheidend für die Verwendung der aktualisierbaren Hilfe.</span><span class="sxs-lookup"><span data-stu-id="1daa2-105">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span> <span data-ttu-id="1daa2-106">Die [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) und [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlets Herunterladen neuer Hilfedateien nur, wenn die Versionsnummer für eine UI-Kultur in der remote HelpInfo-XML-Datendatei größer als die Versionsnummer für die jeweilige UI-Kultur in ist die lokale HelpInfo XML, oder es ist keine lokale HelpInfo XML-Datei.</span><span class="sxs-lookup"><span data-stu-id="1daa2-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>
<span data-ttu-id="1daa2-107">Die Versionsnummern in einer HelpInfo XML-Datei sind entscheidend für die Verwendung der aktualisierbaren Hilfe.</span><span class="sxs-lookup"><span data-stu-id="1daa2-107">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span> <span data-ttu-id="1daa2-108">Die [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) und [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlets Herunterladen neuer Hilfedateien nur, wenn die Versionsnummer für eine UI-Kultur in der remote HelpInfo-XML-Datendatei größer als die Versionsnummer für die jeweilige UI-Kultur in ist die lokale HelpInfo XML, oder es ist keine lokale HelpInfo XML-Datei.</span><span class="sxs-lookup"><span data-stu-id="1daa2-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="1daa2-109">Die HelpInfo XML-Datei verwendet, die 4-Teil Versionsnummer, die in definiert ist die **System.Version** Klasse von Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1daa2-109">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="1daa2-110">Das Format ist `N1.N2.N3.N4`.</span><span class="sxs-lookup"><span data-stu-id="1daa2-110">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="1daa2-111">Modulautoren können eine beliebige Version Nummerierungsschema, die zulässig ist die **System.Version** Klasse.</span><span class="sxs-lookup"><span data-stu-id="1daa2-111">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="1daa2-112">Aktualisierbare Hilfe erfordert nur, dass die Versionsnummer für eine Erhöhung des UI-Kultur, wenn eine neue Version der CAB-Datei für diese Benutzeroberflächenkultur an den Speicherort hochgeladen wird, die angegeben wird die **HelpContentURI** Element in der HelpInfo XML-Datei.</span><span class="sxs-lookup"><span data-stu-id="1daa2-112">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="1daa2-113">Das folgende Beispiel zeigt die Elemente der HelpInfo XML-Datei für Deutsch (de-DE) Benutzeroberfläche Kultur, wenn die Version 2.15.0.10 ist.</span><span class="sxs-lookup"><span data-stu-id="1daa2-113">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="1daa2-114">Die Versionsnummer für eine Benutzeroberflächenkultur gibt die Version der CAB-Datei für die jeweilige UI-Kultur wieder.</span><span class="sxs-lookup"><span data-stu-id="1daa2-114">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="1daa2-115">Die Versionsnummer, die auf die gesamte CAB-Datei angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="1daa2-115">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="1daa2-116">Sie können nicht unterschiedliche Versionsnummern für verschiedene Dateien in die CAB-Datei festlegen.</span><span class="sxs-lookup"><span data-stu-id="1daa2-116">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="1daa2-117">Die Versionsnummer für jede Benutzeroberflächenkultur unabhängig ausgewertet, und es muss keine Beziehung zu den Versionsnummern für andere UI-Kulturen, die das Modul unterstützt.</span><span class="sxs-lookup"><span data-stu-id="1daa2-117">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>