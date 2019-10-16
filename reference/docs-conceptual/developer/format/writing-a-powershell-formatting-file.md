---
title: Schreiben einer PowerShell-Formatierungs Datei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39acce45-5144-43ba-894d-a4ce782fa67d
caps.latest.revision: 13
ms.openlocfilehash: f89f0009972d5237d71cb8f0d1c53cd0ae614b67
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361409"
---
# <a name="writing-a-powershell-formatting-file"></a><span data-ttu-id="04bff-102">Schreiben einer PowerShell-Formatierungsdatei</span><span class="sxs-lookup"><span data-stu-id="04bff-102">Writing a PowerShell Formatting File</span></span>

<span data-ttu-id="04bff-103">"Schreiben einer PowerShell-Formatierungs Datei" ist für Befehls Entwickler gedacht, die Cmdlets oder Funktionen schreiben, die Objekte in der Befehlszeile ausgeben.</span><span class="sxs-lookup"><span data-stu-id="04bff-103">"Writing a PowerShell Formatting File" is for command developers who are writing cmdlets or functions that output objects to the command line.</span></span> <span data-ttu-id="04bff-104">Formatieren von Dateien definieren Sie, wie diese Objekte von PowerShell in der Befehlszeile angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="04bff-104">Formatting files define how PowerShell displays those objects at the command line.</span></span> <span data-ttu-id="04bff-105">Diese Dokumentation enthält eine Übersicht über die Formatierung von Dateien, eine Erläuterung der Konzepte, die Sie beim Schreiben dieser Dateien verstehen sollten, Beispiele für in diesen Dateien verwendete XML und einen Referenz Abschnitt für die XML-Elemente.</span><span class="sxs-lookup"><span data-stu-id="04bff-105">This documentation provides an overview of formatting files, an explanation of the concepts that you should understand when writing these files, examples of XML used in these files, and a reference section for the XML elements.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="04bff-106">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="04bff-106">In This Section</span></span>

<span data-ttu-id="04bff-107">[Übersicht über Formatierungs Datei](./formatting-file-overview.md) Beschreibt, was eine Format Datei ist, und die allgemeinen Komponenten einer Formatierungs Datei, einschließlich allgemeiner Features, die in der Datei definiert werden können, die unterschiedlichen Typen von Format Ansichten, die für .NET-Objekte definiert werden können, und ein vereinfachtes Beispiel für den XML-Code, der zum Definieren einer Tabelle v verwendet wird. IEW.</span><span class="sxs-lookup"><span data-stu-id="04bff-107">[Formatting File Overview](./formatting-file-overview.md) Describes what a format file is and the general components of a formatting file, including common features that can be defined in the file, the different types of format views that can be defined for .NET objects, and a simplified example of the XML used to define a table view.</span></span>

<span data-ttu-id="04bff-108">[Formatieren von Datei Konzepten](./formatting-file-concepts.md) Enthält Informationen, die Sie möglicherweise kennen müssen, wenn Sie eigene Formatierungs Dateien erstellen, z. b. die verschiedenen Typen von Sichten, die Sie definieren können, und spezielle Komponenten dieser Sichten.</span><span class="sxs-lookup"><span data-stu-id="04bff-108">[Formatting File Concepts](./formatting-file-concepts.md) Includes information that you might need to know when creating your own formatting files, such as the different types of views that you can define and special components of those views.</span></span>

<span data-ttu-id="04bff-109">[Beispiele für das Formatieren von Dateien](./examples-of-formatting-files.md) Bietet XML-Beispiele für verschiedene Formatierungs Dateien, einschließlich Beispielen für eine Tabellenansicht, eine Listenansicht und eine breite Ansicht sowie Beispiele, die zeigen, wie Funktionen wie Auswahl Sätze, Auswahl Bedingungen und allgemeine Steuerelemente definiert werden.</span><span class="sxs-lookup"><span data-stu-id="04bff-109">[Examples of Formatting Files](./examples-of-formatting-files.md) Provides XML examples of several formatting files, including examples of a table view, a list view, and a wide view, as well as examples that show how to define features such as selection sets, selection conditions, and common controls.</span></span>

<span data-ttu-id="04bff-110">[XML-Verweis formatieren](./format-schema-xml-reference.md) Enthält Referenz Themen für die XML-Elemente, die in einer Formatierungs Datei verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="04bff-110">[Format XML Reference](./format-schema-xml-reference.md) Includes reference topics for the XML elements used in a formatting file.</span></span>
