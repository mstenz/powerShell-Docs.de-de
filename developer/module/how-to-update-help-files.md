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
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855526"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="abab7-102">Aktualisieren von Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="abab7-102">How to Update Help Files</span></span>

<span data-ttu-id="abab7-103">In diesem Thema wird erläutert, wie Hilfedateien für ein Modul zu aktualisieren, die aktualisierbare Hilfe unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="abab7-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="abab7-104">Aktualisieren von Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="abab7-104">Updating Help Files</span></span>

<span data-ttu-id="abab7-105">Es gibt viele Gründe, um Hilfedateien vorhanden sind, z. B. das Beheben von Fehlern, Klärung ein Konzept, eine häufig gestellte Frage zu beantworten, neue Dateien hinzufügen oder Hinzufügen von neuen, besseren Beispiele zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="abab7-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="abab7-106">So aktualisieren Sie eine Textdatei:</span><span class="sxs-lookup"><span data-stu-id="abab7-106">To update a help file:</span></span>

1. <span data-ttu-id="abab7-107">Ändern Sie die Dateien an.</span><span class="sxs-lookup"><span data-stu-id="abab7-107">Change the files.</span></span>

2. <span data-ttu-id="abab7-108">Die Dateien in anderen UI-Kulturen übersetzt.</span><span class="sxs-lookup"><span data-stu-id="abab7-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="abab7-109">Sammeln Sie alle Hilfedateien (neuer, geänderter und nicht geändert) für das Modul in jede Benutzeroberflächenkultur an.</span><span class="sxs-lookup"><span data-stu-id="abab7-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="abab7-110">Überprüfen Sie die Dateien anhand des XML-Schemas.</span><span class="sxs-lookup"><span data-stu-id="abab7-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="abab7-111">Erstellen Sie die CAB-Dateien für jede Benutzeroberflächenkultur neu.</span><span class="sxs-lookup"><span data-stu-id="abab7-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="abab7-112">Erhöhen Sie in der HelpInfo-XML-Datendatei die Versionsnummern der CAB-Datei für jede Benutzeroberflächenkultur.</span><span class="sxs-lookup"><span data-stu-id="abab7-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="abab7-113">Die neuen CAB-Dateien hochzuladen, zu dem Speicherort, der durch den Wert der angegeben wird die **HelpContentUri** Element in der HelpInfo XML-Datei.</span><span class="sxs-lookup"><span data-stu-id="abab7-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="abab7-114">Ersetzen Sie die ältere CAB-Dateien, durch die neuen CAB-Dateien.</span><span class="sxs-lookup"><span data-stu-id="abab7-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="abab7-115">Die aktualisierte HelpInfo XML-Datei hoch, mit der angegebenen die **HelpInfoUri** -Schlüssels im modulmanifest.</span><span class="sxs-lookup"><span data-stu-id="abab7-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="abab7-116">Ersetzen Sie die ältere HelpInfo XML-Datei mit der neuen Datei ein.</span><span class="sxs-lookup"><span data-stu-id="abab7-116">Replace the older HelpInfo XML file with the new file.</span></span>