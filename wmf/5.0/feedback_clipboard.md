---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: e6b54519d878ab572662075709beb4cf4454b0c6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188056"
---
# <a name="clipboard-cmdlets"></a><span data-ttu-id="04908-102">„Clipboard“-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="04908-102">Clipboard cmdlets</span></span>
<span data-ttu-id="04908-103">Die Cmdlets **Get-Clipboard** und **Set-Clipboard** vereinfachen das Übertragen von Inhalten in eine und aus einer Windows PowerShell-Sitzung.</span><span class="sxs-lookup"><span data-stu-id="04908-103">**Get-Clipboard** and **Set-Clipboard** make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="04908-104">Wenn Sie beispielsweise Windows-Explorer verwenden, um drei Dateien in die Zwischenablage zu kopieren (z.B. indem Sie sie auswählen und `ctrl-c` drücken), können Sie nun einfach auf den Inhalt der Zwischenablage als Liste von Dateien zugreifen:</span><span class="sxs-lookup"><span data-stu-id="04908-104">For example, if you use Windows Explorer to copy three files to the clipboard (by selecting them and pressing `ctrl-c`, for example), you can then easily access the contents of the clipboard as a list of files:</span></span>

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


<span data-ttu-id="04908-105">Die „Clipboard“-Cmdlets unterstützen Bilder, Audiodateien, Dateilisten und Text.</span><span class="sxs-lookup"><span data-stu-id="04908-105">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>
