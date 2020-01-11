---
title: Erstellen eines Workflows mithilfe eines Windows PowerShell-Skripts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5720200ce32f114cd4965d961b9e2804bd154b2e
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870845"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>Erstellen eines Workflows mit einem Windows PowerShell-Skript

Sie können einen Workflow erstellen, indem Sie ein Windows PowerShell-Skript schreiben. Um einen Workflow zu erstellen, verwenden Sie das Workflow Schlüsselwort, gefolgt von einem Namen für den Workflow vor dem Text des Skripts. Zum Beispiel:

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

Sie finden den Workflow genauso wie jeden anderen Windows PowerShell-Befehl.

## <a name="implementing-parallel-and-sequence"></a>Implementieren von parallel und Sequence

[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90)) unterstützt die parallele Ausführung von Aktivitäten. Um diese Funktion in einem Windows PowerShell-Skript zu implementieren, verwenden Sie das `parallel`-Schlüsselwort vor einem Skriptblock. Sie können auch die `foreach -parallel` Erstellung verwenden, um eine Auflistung von-Objekten parallel zu durchlaufen. Um eine Gruppe von Aktivitäten in sequenzieller Reihenfolge innerhalb eines parallelen Blocks auszuführen, schließen Sie diese Gruppe von Aktivitäten in einen Skriptblock ein, und stellen Sie dem Block das Sequence-Schlüsselwort voran.

## <a name="joining-computers-to-a-domain"></a>Hinzufügen von Computern zu einer Domäne

Mit dem folgenden Skript wird ein Workflow erstellt, der den Domänen Status einer Gruppe von benutzerdefinierten Computern überprüft, Sie mit einer Domäne verknüpft, wenn Sie noch nicht verknüpft sind, und den Status dann erneut überprüft.
Dies ist eine Skript Version des XAML-Workflows, die unter [Erstellen eines Workflows mit Windows PowerShell-Aktivitäten](./creating-a-workflow-with-windows-powershell-activities.md)erläutert wird.

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
}
```