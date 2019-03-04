---
title: Schreiben eine PowerShell Formatierungsdatei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39acce45-5144-43ba-894d-a4ce782fa67d
caps.latest.revision: 13
ms.openlocfilehash: f89f0009972d5237d71cb8f0d1c53cd0ae614b67
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857046"
---
# <a name="writing-a-powershell-formatting-file"></a><span data-ttu-id="cae4c-102">Schreiben einer PowerShell-Formatierungsdatei</span><span class="sxs-lookup"><span data-stu-id="cae4c-102">Writing a PowerShell Formatting File</span></span>

<span data-ttu-id="cae4c-103">"Schreiben einer Datei für die PowerShell-Formatierung" ist für Befehl-Entwickler, die-Cmdlets oder Funktionen, die Objekte an die Befehlszeile Ausgabe schreiben.</span><span class="sxs-lookup"><span data-stu-id="cae4c-103">"Writing a PowerShell Formatting File" is for command developers who are writing cmdlets or functions that output objects to the command line.</span></span> <span data-ttu-id="cae4c-104">Formatierungsdateien definieren, wie PowerShell die Objekte in der Befehlszeile angezeigt.</span><span class="sxs-lookup"><span data-stu-id="cae4c-104">Formatting files define how PowerShell displays those objects at the command line.</span></span> <span data-ttu-id="cae4c-105">Diese Dokumentation enthält eine Übersicht über die Formatierungsdateien, eine Erläuterung der Konzepte, die Sie kennen sollten, wenn Sie diese Dateien haben, Beispiele für XML, die in diese Dateien und einen Abschnitt für die XML-Elemente verwendet zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="cae4c-105">This documentation provides an overview of formatting files, an explanation of the concepts that you should understand when writing these files, examples of XML used in these files, and a reference section for the XML elements.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="cae4c-106">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="cae4c-106">In This Section</span></span>

<span data-ttu-id="cae4c-107">[Übersicht über die Datei Formatierung](./formatting-file-overview.md) beschreibt, welche eine Formatdatei ist, und die allgemeine Komponenten eine Formatierungsdatei, einschließlich der allgemeinen Funktionen, die in der Datei, die verschiedenen Typen von Format Sichten definiert werden können, die für .NET Objekte definiert werden können und ein vereinfachtes Beispiel für den XML-Code verwendet, um eine Tabellenansicht zu definieren.</span><span class="sxs-lookup"><span data-stu-id="cae4c-107">[Formatting File Overview](./formatting-file-overview.md) Describes what a format file is and the general components of a formatting file, including common features that can be defined in the file, the different types of format views that can be defined for .NET objects, and a simplified example of the XML used to define a table view.</span></span>

<span data-ttu-id="cae4c-108">[Formatieren Sie die Datei Konzepte](./formatting-file-concepts.md) enthält Informationen, die Sie kennen müssen, wie die verschiedenen Typen von Ansichten, die Sie definieren können und spezielle Komponenten dieser Ansichten beim Dateien erstellen, eine eigene Formatierung,.</span><span class="sxs-lookup"><span data-stu-id="cae4c-108">[Formatting File Concepts](./formatting-file-concepts.md) Includes information that you might need to know when creating your own formatting files, such as the different types of views that you can define and special components of those views.</span></span>

<span data-ttu-id="cae4c-109">[Beispiele für Dateien Formatierung](./examples-of-formatting-files.md) enthält XML-Beispiele für verschiedene Formatierungsdateien, einschließlich Beispiele für eine Tabellenansicht, eine Listenansicht, und eine Breite Ansicht sowie Beispiele, die zeigen, wie Sie Funktionen wie Auswahl Mengen auswahlbedingungen, definieren und Allgemeine Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="cae4c-109">[Examples of Formatting Files](./examples-of-formatting-files.md) Provides XML examples of several formatting files, including examples of a table view, a list view, and a wide view, as well as examples that show how to define features such as selection sets, selection conditions, and common controls.</span></span>

<span data-ttu-id="cae4c-110">[Formatieren von XML-Referenz für](./format-schema-xml-reference.md) enthält Referenzthemen für die XML-Elemente in einer Formatierungsdatei.</span><span class="sxs-lookup"><span data-stu-id="cae4c-110">[Format XML Reference](./format-schema-xml-reference.md) Includes reference topics for the XML elements used in a formatting file.</span></span>
