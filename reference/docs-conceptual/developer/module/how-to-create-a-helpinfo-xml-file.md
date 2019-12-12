---
title: Erstellen einer helpinfo-XML-Datei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367319"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="1a85d-102">Erstellen einer XML-Datei HelpInfo</span><span class="sxs-lookup"><span data-stu-id="1a85d-102">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="1a85d-103">In diesen Themen in diesem Abschnitt wird erläutert, wie Sie eine Hilfe Informationsdatei erstellen und Auffüllen, die im Allgemeinen als "helpinfo-XML-Datei" bezeichnet wird, für das Windows PowerShell-Feature zur aktualisierbaren Hilfe.</span><span class="sxs-lookup"><span data-stu-id="1a85d-103">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the Windows PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="1a85d-104">Hilfe zur helpinfo-XML-Datei</span><span class="sxs-lookup"><span data-stu-id="1a85d-104">HelpInfo XML File Overview</span></span>

<span data-ttu-id="1a85d-105">Die helpinfo-XML-Datei ist die primäre Quelle von Informationen über die aktualisierbare Hilfe für das Modul.</span><span class="sxs-lookup"><span data-stu-id="1a85d-105">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="1a85d-106">Sie enthält den Speicherort der Hilfedateien für die Module, die unterstützten Benutzeroberflächen Kulturen und die Versionsnummern, die von der aktualisierbaren Hilfe verwendet werden, um zu bestimmen, ob der Benutzer über die neuesten Hilfedateien verfügt.</span><span class="sxs-lookup"><span data-stu-id="1a85d-106">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="1a85d-107">Jedes Modul verfügt nur über eine helpinfo-XML-Datei, auch wenn das Modul mehrere Hilfedateien für mehrere Benutzeroberflächen Kulturen enthält.</span><span class="sxs-lookup"><span data-stu-id="1a85d-107">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="1a85d-108">Der Modul Autor erstellt die helpinfo-XML-Datei und legt Sie an dem Internet Speicherort ab, der durch den **helpinfouri** -Schlüssel im Modul Manifest angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="1a85d-108">The module author creates the HelpInfo XML file and places it in the Internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="1a85d-109">Wenn die Modul Hilfedateien aktualisiert und hochgeladen werden, aktualisiert der Modul Autor die helpinfo-XML-Datei und ersetzt die ursprüngliche helpinfo-XML-Datei durch die neue Version.</span><span class="sxs-lookup"><span data-stu-id="1a85d-109">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="1a85d-110">Es ist wichtig, dass die helpinfo-XML-Datei sorgfältig verwaltet wird.</span><span class="sxs-lookup"><span data-stu-id="1a85d-110">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="1a85d-111">Wenn Sie neue Dateien hochladen, aber vergessen, die Versionsnummern zu erhöhen, werden die neuen Dateien von der aktualisierbaren Hilfe nicht auf die Benutzer Computer heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="1a85d-111">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="1a85d-112">Wenn Sie Hilfedateien für eine neue Benutzeroberflächen Kultur hinzufügen, aber die helpinfo-XML-Datei nicht aktualisieren oder am richtigen Speicherort platzieren, werden die neuen Dateien durch die aktualisierbare Hilfe nicht heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="1a85d-112">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1a85d-113">Inhalt dieses Abschnitts</span><span class="sxs-lookup"><span data-stu-id="1a85d-113">In this section</span></span>

<span data-ttu-id="1a85d-114">In diesem Abschnitt werden folgende Themen behandelt.</span><span class="sxs-lookup"><span data-stu-id="1a85d-114">This section includes the following topics.</span></span>

- [<span data-ttu-id="1a85d-115">Helpinfo-XML-Schema</span><span class="sxs-lookup"><span data-stu-id="1a85d-115">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="1a85d-116">Helpinfo-XML-Beispieldatei</span><span class="sxs-lookup"><span data-stu-id="1a85d-116">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="1a85d-117">Benennen einer helpinfo-XML-Datei</span><span class="sxs-lookup"><span data-stu-id="1a85d-117">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="1a85d-118">Festlegen der helpinfo-XML-Versionsnummern</span><span class="sxs-lookup"><span data-stu-id="1a85d-118">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="1a85d-119">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1a85d-119">See Also</span></span>

[<span data-ttu-id="1a85d-120">Unterstützen aktualisierbarer Hilfe</span><span class="sxs-lookup"><span data-stu-id="1a85d-120">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)