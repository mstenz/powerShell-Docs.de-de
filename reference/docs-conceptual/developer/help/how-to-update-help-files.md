---
title: Vorgehensweise beim Aktualisieren von Hilfedateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 35b3fd696419d0135fd6f662223e6c8586df443a
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811649"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="fa795-102">Aktualisieren von Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="fa795-102">How to Update Help Files</span></span>

<span data-ttu-id="fa795-103">In diesem Thema wird erläutert, wie Sie Hilfedateien für ein Modul aktualisieren, das aktualisierbare Hilfe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="fa795-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="fa795-104">Aktualisieren von Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="fa795-104">Updating Help Files</span></span>

<span data-ttu-id="fa795-105">Es gibt viele Gründe, Hilfedateien zu aktualisieren, wie z. b. das Beheben von Fehlern, das verdeutlichen eines Konzepts, das Beantworten einer häufig gestellten Frage, das Hinzufügen neuer Dateien oder das Hinzufügen neuer und besserer Beispiele.</span><span class="sxs-lookup"><span data-stu-id="fa795-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="fa795-106">So aktualisieren Sie eine Hilfedatei:</span><span class="sxs-lookup"><span data-stu-id="fa795-106">To update a help file:</span></span>

1. <span data-ttu-id="fa795-107">Ändern Sie die Dateien.</span><span class="sxs-lookup"><span data-stu-id="fa795-107">Change the files.</span></span>

2. <span data-ttu-id="fa795-108">Übersetzen Sie die Dateien in andere Benutzeroberflächen Kulturen.</span><span class="sxs-lookup"><span data-stu-id="fa795-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="fa795-109">Sammeln Sie alle Hilfedateien (neu, geändert und unverändert) für das Modul in jeder Benutzeroberflächen Kultur.</span><span class="sxs-lookup"><span data-stu-id="fa795-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="fa795-110">Überprüfen Sie die Dateien anhand des XML-Schemas.</span><span class="sxs-lookup"><span data-stu-id="fa795-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="fa795-111">Erstellen Sie die CAB-Dateien für jede Benutzeroberflächen Kultur neu.</span><span class="sxs-lookup"><span data-stu-id="fa795-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="fa795-112">Erhöhen Sie in der helpinfo-XML-Datei die Versionsnummern der CAB-Datei für jede Benutzeroberflächen Kultur.</span><span class="sxs-lookup"><span data-stu-id="fa795-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="fa795-113">Laden Sie die neuen CAB-Dateien an den Speicherort hoch, der durch den Wert des **helpcontenturi** -Elements in der helpinfo-XML-Datei angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="fa795-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="fa795-114">Ersetzen Sie die älteren CAB-Dateien durch die neuen CAB-Dateien.</span><span class="sxs-lookup"><span data-stu-id="fa795-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="fa795-115">Laden Sie die aktualisierte helpinfo-XML-Datei an den Speicherort hoch, der durch den **helpinfouri** -Schlüssel im Modul Manifest angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="fa795-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="fa795-116">Ersetzen Sie die ältere helpinfo-XML-Datei durch die neue Datei.</span><span class="sxs-lookup"><span data-stu-id="fa795-116">Replace the older HelpInfo XML file with the new file.</span></span>
