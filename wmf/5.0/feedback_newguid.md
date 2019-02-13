---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678137"
---
# <a name="new-guid"></a>New-Guid
Bei Schreiben von Skripts (oder einer DSC-Ressource) benötigen Sie oft einen eindeutigen Bezeichner. GUIDs funktionieren gut und können durch Aufrufen der .NET Framework-Klasse „Guid“ einfach generiert werden. Doch mit einem Cmdlet können GUIDs auch von Endbenutzern einfacher gefunden werden, die mit der .NET Framework-Klasse noch nicht vertraut sind:

PS C:\\&gt; New-Guid

Guid

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
