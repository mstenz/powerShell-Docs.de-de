---
title: Erstellen einer Formatierungs Datei (. Format. ps1xml) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363619"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="b3150-102">Erstellen einer Formatierungsdatei (.format.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="b3150-102">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="b3150-103">In diesem Thema wird beschrieben, wie eine Formatierungs Datei (. Format. ps1xml) erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="b3150-103">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="b3150-104">Sie können auch eine Formatierungs Datei erstellen, indem Sie eine Kopie einer der von Windows PowerShell bereitgestellten Dateien erstellen.</span><span class="sxs-lookup"><span data-stu-id="b3150-104">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="b3150-105">Wenn Sie eine Kopie einer vorhandenen Datei erstellen, löschen Sie die vorhandene digitale Signatur, und fügen Sie der neuen Datei Ihre eigene Signatur hinzu.</span><span class="sxs-lookup"><span data-stu-id="b3150-105">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="b3150-106">Zum Erstellen einer. Format. ps1xml-Datei.</span><span class="sxs-lookup"><span data-stu-id="b3150-106">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="b3150-107">Erstellen Sie eine Textdatei (. txt) mit einem Text-Editor, z. b. Notepad.</span><span class="sxs-lookup"><span data-stu-id="b3150-107">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="b3150-108">Kopieren Sie die folgenden Zeilen in die Formatierungs Datei.</span><span class="sxs-lookup"><span data-stu-id="b3150-108">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="b3150-109">Mit dem \<Konfigurations >\</Konfiguration > Tags wird der Stamm `Configuration` Knoten definiert.</span><span class="sxs-lookup"><span data-stu-id="b3150-109">The \<Configuration>\</Configuration> tags define the root `Configuration` node.</span></span> <span data-ttu-id="b3150-110">Alle zusätzlichen XML-Tags werden in diesen Knoten eingeschlossen.</span><span class="sxs-lookup"><span data-stu-id="b3150-110">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="b3150-111">Die <ViewDefinitions></ViewDefinitions> Tags definieren den `ViewDefinitions` Knoten.</span><span class="sxs-lookup"><span data-stu-id="b3150-111">The <ViewDefinitions></ViewDefinitions> tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="b3150-112">Alle Sichten werden innerhalb dieses Knotens definiert.</span><span class="sxs-lookup"><span data-stu-id="b3150-112">All views are defined within this node.</span></span>

3. <span data-ttu-id="b3150-113">Speichern Sie die Datei im Installationsordner von Windows PowerShell, in Ihrem Modul Ordner oder in einem Unterordner des Modul Ordners.</span><span class="sxs-lookup"><span data-stu-id="b3150-113">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="b3150-114">Verwenden Sie das folgende Namensformat, wenn Sie die Datei speichern: `MyFile.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="b3150-114">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="b3150-115">Beim Formatieren von Dateien muss die `.format.ps1xml` Erweiterung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b3150-115">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="b3150-116">Nun können Sie der Formatierungs Datei Ansichten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b3150-116">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="b3150-117">Es gibt keine Beschränkung für die Anzahl der Sichten, die in einer Formatierungs Datei definiert werden können.</span><span class="sxs-lookup"><span data-stu-id="b3150-117">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="b3150-118">Sie können eine einzelne Ansicht für jedes Objekt, mehrere Ansichten für dasselbe Objekt oder eine einzelne Ansicht hinzufügen, die von mehreren Objekten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b3150-118">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3150-119">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b3150-119">See Also</span></span>

[<span data-ttu-id="b3150-120">Schreiben einer Windows PowerShell-Formatierungs-und-Typen Datei</span><span class="sxs-lookup"><span data-stu-id="b3150-120">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
