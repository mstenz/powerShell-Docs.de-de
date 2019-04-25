---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d5ec95abb1d3160afc4179cff991cb5ef72d85fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057297"
---
# <a name="clipboard-cmdlets"></a><span data-ttu-id="4de59-102">„Clipboard“-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="4de59-102">Clipboard cmdlets</span></span>
<span data-ttu-id="4de59-103">Die Cmdlets **Get-Clipboard** und **Set-Clipboard** vereinfachen das Übertragen von Inhalten in eine und aus einer Windows PowerShell-Sitzung.</span><span class="sxs-lookup"><span data-stu-id="4de59-103">**Get-Clipboard** and **Set-Clipboard** make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="4de59-104">Wenn Sie beispielsweise Windows-Explorer verwenden, um drei Dateien in die Zwischenablage zu kopieren (z.B. indem Sie sie auswählen und `ctrl-c` drücken), können Sie nun einfach auf den Inhalt der Zwischenablage als Liste von Dateien zugreifen:</span><span class="sxs-lookup"><span data-stu-id="4de59-104">For example, if you use Windows Explorer to copy three files to the clipboard (by selecting them and pressing `ctrl-c`, for example), you can then easily access the contents of the clipboard as a list of files:</span></span>

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


<span data-ttu-id="4de59-105">Die „Clipboard“-Cmdlets unterstützen Bilder, Audiodateien, Dateilisten und Text.</span><span class="sxs-lookup"><span data-stu-id="4de59-105">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>
