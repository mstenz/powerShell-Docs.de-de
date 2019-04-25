---
title: 'Vorgehensweise: erstellen eine HelpInfo-XML-Datei | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082412"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="b819c-102">Erstellen einer XML-Datei HelpInfo</span><span class="sxs-lookup"><span data-stu-id="b819c-102">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="b819c-103">Die Themen in diesem Abschnitt wird erläutert, wie zum Erstellen und Auffüllen einer hilfeinformationsdatei, häufig als "HelpInfo XML-Datei" für die Windows PowerShell aktualisierbare Hilfefunktion bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="b819c-103">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the Windows PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="b819c-104">Übersicht über die HelpInfo-XML-Datei</span><span class="sxs-lookup"><span data-stu-id="b819c-104">HelpInfo XML File Overview</span></span>

<span data-ttu-id="b819c-105">Die HelpInfo XML-Datei ist die Hauptquelle für Informationen zur aktualisierbaren Hilfe für das Modul.</span><span class="sxs-lookup"><span data-stu-id="b819c-105">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="b819c-106">Es enthält den Speicherort der Hilfedateien für Module, die unterstützten Benutzeroberflächenkulturen und die Versionsnummern, die aktualisierbare Hilfe verwendet, um zu bestimmen, ob der Benutzer die neuesten Hilfedateien.</span><span class="sxs-lookup"><span data-stu-id="b819c-106">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="b819c-107">Jedes Modul besitzt nur eine HelpInfo XML-Datei, selbst wenn das Modul mehrere Hilfedateien für mehrere UI-Kulturen enthält.</span><span class="sxs-lookup"><span data-stu-id="b819c-107">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="b819c-108">Autor des Moduls die HelpInfo XML-Datei erstellt und platziert sie in dem Speicherort im Internet, die angegeben wird die **HelpInfoUri** -Schlüssels im modulmanifest.</span><span class="sxs-lookup"><span data-stu-id="b819c-108">The module author creates the HelpInfo XML file and places it in the Internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="b819c-109">Wenn die Hilfedateien für Module aktualisiert und hochgeladen werden, wird den Autor des Moduls die HelpInfo XML-Datei aktualisiert und ersetzt die ursprüngliche HelpInfo XML-Datei mit der neuen Version.</span><span class="sxs-lookup"><span data-stu-id="b819c-109">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="b819c-110">Es ist wichtig, dass die HelpInfo XML-Datei sorgfältig beibehalten wird.</span><span class="sxs-lookup"><span data-stu-id="b819c-110">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="b819c-111">Wenn Sie neue Dateien hochladen, aber vergessen, die Versionsnummern erhöht werden, werden aktualisierbare Hilfe nicht die neuen Dateien auf Computern der Benutzer heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="b819c-111">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="b819c-112">Wenn Sie Hilfedateien für eine neue UI-Kultur, hinzufügen, aber nicht aktualisieren Sie die HelpInfo XML-Datei oder an der richtigen Speicherort zu platzieren, werden die neuen Dateien aktualisierbare Hilfe nicht herunterladen.</span><span class="sxs-lookup"><span data-stu-id="b819c-112">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b819c-113">Inhalt dieses Abschnitts</span><span class="sxs-lookup"><span data-stu-id="b819c-113">In this section</span></span>

<span data-ttu-id="b819c-114">In diesem Abschnitt werden folgende Themen behandelt.</span><span class="sxs-lookup"><span data-stu-id="b819c-114">This section includes the following topics.</span></span>

- [<span data-ttu-id="b819c-115">HelpInfo-XML-Schema</span><span class="sxs-lookup"><span data-stu-id="b819c-115">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="b819c-116">HelpInfo-XML-Beispieldatei</span><span class="sxs-lookup"><span data-stu-id="b819c-116">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="b819c-117">Wie Sie eine HelpInfo-XML-Datei benennen</span><span class="sxs-lookup"><span data-stu-id="b819c-117">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="b819c-118">Gewusst wie HelpInfo-XML-Versionsnummern</span><span class="sxs-lookup"><span data-stu-id="b819c-118">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="b819c-119">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b819c-119">See Also</span></span>

[<span data-ttu-id="b819c-120">Unterstützung für aktualisierbare Hilfe</span><span class="sxs-lookup"><span data-stu-id="b819c-120">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)