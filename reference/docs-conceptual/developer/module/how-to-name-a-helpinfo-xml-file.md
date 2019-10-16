---
title: Benennen einer helpinfo-XML-Datei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367199"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="8bdab-102">Benennen einer XML-Datei HelpInfo</span><span class="sxs-lookup"><span data-stu-id="8bdab-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="8bdab-103">In diesem Thema wird das erforderliche Namensformat für die aktualisierbaren Hilfe Informationsdateien erläutert, die häufig als helpinfo-XML-Dateien bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="8bdab-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="8bdab-104">Benennen einer XML-Datei HelpInfo</span><span class="sxs-lookup"><span data-stu-id="8bdab-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="8bdab-105">Eine helpinfo-XML-Datei muss einen Namen haben, der das folgende Format hat.</span><span class="sxs-lookup"><span data-stu-id="8bdab-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="8bdab-106">Die Elemente des Namens lauten wie folgt.</span><span class="sxs-lookup"><span data-stu-id="8bdab-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="8bdab-107">ModuleName der Wert der **Name** -Eigenschaft des **ModuleInfo** -Objekts, das vom [Get-Module-](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8bdab-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="8bdab-108">ModuleGUID der Wert des **GUID** -Schlüssels im Modul Manifest.</span><span class="sxs-lookup"><span data-stu-id="8bdab-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="8bdab-109">Wenn der Modulname beispielsweise "Testmodule" und die Modul-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 ist, lautet der Name der helpinfo-XML-Datei für das Modul wie folgt:</span><span class="sxs-lookup"><span data-stu-id="8bdab-109">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`