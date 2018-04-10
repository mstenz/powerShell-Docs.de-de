---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: d34a267bae7e48afe4442256d7f112da3a97eb7d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="clipboard-cmdlets"></a>„Clipboard“-Cmdlets
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