---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 8d5f8cc8c85d584b195483e464e878857629a78e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="clipboard-cmdlets" class="xliff"></a>
# „Clipboard“-Cmdlets
Die Cmdlets **Get-Clipboard** und **Set-Clipboard** vereinfachen das Übertragen von Inhalten in eine und aus einer Windows PowerShell-Sitzung. Wenn Sie beispielsweise Windows-Explorer verwenden, um drei Dateien in die Zwischenablage zu kopieren (z.B. indem Sie sie auswählen und `ctrl-c` drücken), können Sie nun einfach auf den Inhalt der Zwischenablage als Liste von Dateien zugreifen:

```powershell 
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


Die „Clipboard“-Cmdlets unterstützen Bilder, Audiodateien, Dateilisten und Text.

