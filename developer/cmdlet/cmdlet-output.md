---
title: Cmdlet-Ausgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1362f4cd-4e05-4ace-ade6-7128da8ad86c
caps.latest.revision: 10
ms.openlocfilehash: 4c6aacd49b0a87bca6806ba5f08a1b4d48a90959
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068554"
---
# <a name="cmdlet-output"></a><span data-ttu-id="c0f9e-102">Cmdlet-Ausgabe</span><span class="sxs-lookup"><span data-stu-id="c0f9e-102">Cmdlet Output</span></span>

<span data-ttu-id="c0f9e-103">Dieser Abschnitt beschreibt die Arten von Cmdlet-Ausgabe und die Methoden, die Cmdlets aufrufen können, um die Ausgabe, z. B. Fehlermeldungen und Objekte zu generieren.</span><span class="sxs-lookup"><span data-stu-id="c0f9e-103">This section discusses the types of cmdlet output and the methods that cmdlets can call to generate output such as error messages and objects.</span></span> <span data-ttu-id="c0f9e-104">Dieser Abschnitt beschreibt auch, wie Sie .NET Framework-Typen zu definieren, die durch Ihre Cmdlets zurückgegeben werden und wie diese Objekte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c0f9e-104">This section also describes how to define the .NET Framework types that are returned by your cmdlets and how those objects are displayed.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c0f9e-105">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="c0f9e-105">In This Section</span></span>

<span data-ttu-id="c0f9e-106">[Cmdlet-Ausgabetypen](./types-of-cmdlet-output.md) beschreibt die Typen und Ausgabe, die Cmdlets generiert werden können und die Methoden, die Cmdlets aufrufen, um die Ausgabe zu generieren.</span><span class="sxs-lookup"><span data-stu-id="c0f9e-106">[Types of Cmdlet Output](./types-of-cmdlet-output.md) Describes the types and output that cmdlets can generate and the methods that cmdlets call to generate the output.</span></span>

<span data-ttu-id="c0f9e-107">[Cmdlet-Fehlerberichterstattung](./cmdlet-error-reporting.md) Cmdlet-Windows-Fehlerberichterstattung, eine Teilmenge der Ausgabe des Cmdlets erläutert.</span><span class="sxs-lookup"><span data-stu-id="c0f9e-107">[Cmdlet Error Reporting](./cmdlet-error-reporting.md) Discusses cmdlet error reporting, a subset of cmdlet output.</span></span>

<span data-ttu-id="c0f9e-108">[Erweitern von Ausgabeobjekten](./extending-output-objects.md) erläutert, wie die Typdateien (. ps1xml), um die .NET Framework-Objekte zu erweitern, die zurückgegeben werden von Cmdlets, Funktionen und Skripts.</span><span class="sxs-lookup"><span data-stu-id="c0f9e-108">[Extending Output Objects](./extending-output-objects.md) Discusses how to use the types files (.ps1xml) to extend the .NET Framework objects that are returned by cmdlets, functions, and scripts.</span></span>

<span data-ttu-id="c0f9e-109">[Formatieren von PowerShell-Dateien](../format/powershell-formatting-files.md) wird beschrieben, die Formatierungsdateien (. ps1xml) Dateien, die definieren, der Standardwert für einen bestimmten Satz von .NET Framework-Objekten in Windows PowerShell anzeigen.</span><span class="sxs-lookup"><span data-stu-id="c0f9e-109">[PowerShell Formatting Files](../format/powershell-formatting-files.md) Describes the formatting files (.format.ps1xml) files that define the default display for a specific set of .NET Framework objects in Windows PowerShell.</span></span>

<span data-ttu-id="c0f9e-110">[Benutzerdefinierte Formatierung Dateien](./custom-formatting-files.md) beschreibt, wie zum Erstellen eigene benutzerdefinierte Formatierung überschreiben die Standardeinstellung Anzeigeformate oder definieren Sie die Anzeige von Objekten zurückgegeben werden, durch Ihre eigenen Befehle.</span><span class="sxs-lookup"><span data-stu-id="c0f9e-110">[Custom Formatting Files](./custom-formatting-files.md) Describes how to create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0f9e-111">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c0f9e-111">See Also</span></span>

[<span data-ttu-id="c0f9e-112">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="c0f9e-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
