---
title: 'Vorgehensweise: Erstellen Sie eine Formatierungsdatei (. ps1xml) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065500"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="f23d6-102">Erstellen einer Formatierungsdatei (.format.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="f23d6-102">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="f23d6-103">In diesem Thema wird beschrieben, wie eine Formatierungsdatei zu erstellen (. ps1xml).</span><span class="sxs-lookup"><span data-stu-id="f23d6-103">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="f23d6-104">Sie können auch eine Formatierungsdatei erstellen, indem eine Kopie von einer der Dateien von Windows PowerShell bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="f23d6-104">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="f23d6-105">Wenn Sie eine Kopie einer vorhandenen Datei vornehmen, löschen Sie die vorhandene digitale Signatur, und fügen Sie eigene Signatur in die neue Datei hinzu.</span><span class="sxs-lookup"><span data-stu-id="f23d6-105">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="f23d6-106">Zum Erstellen einer. ps1xml-Datei.</span><span class="sxs-lookup"><span data-stu-id="f23d6-106">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="f23d6-107">Erstellen Sie eine Textdatei (.txt), die mit einem Text-Editor wie Editor.</span><span class="sxs-lookup"><span data-stu-id="f23d6-107">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="f23d6-108">Kopieren Sie die folgenden Zeilen in die Formatierungsdatei.</span><span class="sxs-lookup"><span data-stu-id="f23d6-108">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="f23d6-109">Die \<Configuration >\</Configuration > Tags definieren den Stamm `Configuration` Knoten.</span><span class="sxs-lookup"><span data-stu-id="f23d6-109">The \<Configuration>\</Configuration> tags define the root `Configuration` node.</span></span> <span data-ttu-id="f23d6-110">Alle zusätzlichen XML-Tags werden in diesem Knoten eingeschlossen sein.</span><span class="sxs-lookup"><span data-stu-id="f23d6-110">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="f23d6-111">Die <ViewDefinitions> </ViewDefinitions> Tags definieren die `ViewDefinitions` Knoten.</span><span class="sxs-lookup"><span data-stu-id="f23d6-111">The <ViewDefinitions></ViewDefinitions> tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="f23d6-112">Alle Ansichten werden in diesem Knoten definiert.</span><span class="sxs-lookup"><span data-stu-id="f23d6-112">All views are defined within this node.</span></span>

3. <span data-ttu-id="f23d6-113">Speichern Sie die Datei, in den Installationsordner der Windows PowerShell, um Ihrem Ordner "Module" oder in einem Unterordner des Ordner "Module".</span><span class="sxs-lookup"><span data-stu-id="f23d6-113">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="f23d6-114">Verwenden Sie das folgende Namensformat aus, wenn Sie die Datei speichern: `MyFile.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="f23d6-114">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="f23d6-115">Formatierungsdateien verwenden, müssen die `.format.ps1xml` Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="f23d6-115">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="f23d6-116">Sie können jetzt die Formatierungsdatei Ansichten hinzu.</span><span class="sxs-lookup"><span data-stu-id="f23d6-116">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="f23d6-117">Es gibt keine Beschränkung für die Anzahl der Aufrufe, die in einer Formatierungsdatei definiert werden können.</span><span class="sxs-lookup"><span data-stu-id="f23d6-117">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="f23d6-118">Sie können eine einzelne Ansicht für jedes Objekt, mehrere Ansichten für das gleiche Objekt oder eine Ansicht, die von mehreren Objekten verwendet wird, hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f23d6-118">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="f23d6-119">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f23d6-119">See Also</span></span>

[<span data-ttu-id="f23d6-120">Schreiben Sie eine Windows PowerShell, die Formatierung und Typen, Datei</span><span class="sxs-lookup"><span data-stu-id="f23d6-120">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
