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
ms.openlocfilehash: d69e8a734aa96ff9b7911815fb43b81103548b59
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794347"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="c369d-102">Festlegen von XML-Versionsnummern für HelpInfo</span><span class="sxs-lookup"><span data-stu-id="c369d-102">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="c369d-103">In diesem Thema wird erläutert, wie Sie festlegen, und erhöhen die Versionsnummern in einer aktualisierbaren Hilfe-Informationen-Datei, die häufig als "HelpInfo XML-Datei." bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="c369d-103">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="c369d-104">Festlegen von XML-Versionsnummern für HelpInfo</span><span class="sxs-lookup"><span data-stu-id="c369d-104">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="c369d-105">Die Versionsnummern in einer HelpInfo XML-Datei sind entscheidend für die Verwendung der aktualisierbaren Hilfe.</span><span class="sxs-lookup"><span data-stu-id="c369d-105">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span> <span data-ttu-id="c369d-106">Die [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) und [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlets Herunterladen neuer Hilfedateien nur, wenn die Versionsnummer für eine UI-Kultur in der remote HelpInfo-XML-Datendatei größer als die Versionsnummer für die jeweilige UI-Kultur in ist die lokale HelpInfo XML, oder es ist keine lokale HelpInfo XML-Datei.</span><span class="sxs-lookup"><span data-stu-id="c369d-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="c369d-107">Die HelpInfo XML-Datei verwendet, die 4-Teil Versionsnummer, die in definiert ist die **System.Version** Klasse von Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c369d-107">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="c369d-108">Das Format ist `N1.N2.N3.N4`.</span><span class="sxs-lookup"><span data-stu-id="c369d-108">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="c369d-109">Modulautoren können eine beliebige Version Nummerierungsschema, die zulässig ist die **System.Version** Klasse.</span><span class="sxs-lookup"><span data-stu-id="c369d-109">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="c369d-110">Aktualisierbare Hilfe erfordert nur, dass die Versionsnummer für eine Erhöhung des UI-Kultur, wenn eine neue Version der CAB-Datei für diese Benutzeroberflächenkultur an den Speicherort hochgeladen wird, die angegeben wird die **HelpContentURI** Element in der HelpInfo XML-Datei.</span><span class="sxs-lookup"><span data-stu-id="c369d-110">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="c369d-111">Das folgende Beispiel zeigt die Elemente der HelpInfo XML-Datei für Deutsch (de-DE) Benutzeroberfläche Kultur, wenn die Version 2.15.0.10 ist.</span><span class="sxs-lookup"><span data-stu-id="c369d-111">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="c369d-112">Die Versionsnummer für eine Benutzeroberflächenkultur gibt die Version der CAB-Datei für die jeweilige UI-Kultur wieder.</span><span class="sxs-lookup"><span data-stu-id="c369d-112">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="c369d-113">Die Versionsnummer, die auf die gesamte CAB-Datei angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="c369d-113">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="c369d-114">Sie können nicht unterschiedliche Versionsnummern für verschiedene Dateien in die CAB-Datei festlegen.</span><span class="sxs-lookup"><span data-stu-id="c369d-114">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="c369d-115">Die Versionsnummer für jede Benutzeroberflächenkultur unabhängig ausgewertet, und es muss keine Beziehung zu den Versionsnummern für andere UI-Kulturen, die das Modul unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c369d-115">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>