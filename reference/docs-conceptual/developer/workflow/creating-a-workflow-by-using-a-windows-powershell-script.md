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
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366029"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>Erstellen eines Workflows mit einem Windows PowerShell-Skript

Sie können einen Workflow erstellen, indem Sie ein Windows PowerShell-Skript schreiben. Um einen Workflow zu erstellen, verwenden Sie das Workflow Schlüsselwort, gefolgt von einem Namen für den Workflow vor dem Text des Skripts. Beispiel:

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

Sie finden den Workflow genauso wie jeden anderen Windows PowerShell-Befehl.

## <a name="implementing-parallel-and-sequence"></a>Implementieren von parallel und Sequence

[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) unterstützt die parallele Ausführung von Aktivitäten. Um diese Funktion in einem Windows PowerShell-Skript zu implementieren, verwenden Sie das `parallel`-Schlüsselwort vor einem Skriptblock. Sie können auch die `foreach -parallel` Erstellung verwenden, um eine Auflistung von-Objekten parallel zu durchlaufen. Um eine Gruppe von Aktivitäten in sequenzieller Reihenfolge innerhalb eines parallelen Blocks auszuführen, schließen Sie diese Gruppe von Aktivitäten in einen Skriptblock ein, und stellen Sie dem Block das Sequence-Schlüsselwort voran.

## <a name="joining-computers-to-a-domain"></a>Hinzufügen von Computern zu einer Domäne

Mit dem folgenden Skript wird ein Workflow erstellt, der den Domänen Status einer Gruppe von benutzerdefinierten Computern überprüft, Sie mit einer Domäne verknüpft, wenn Sie noch nicht verknüpft sind, und den Status dann erneut überprüft. Dies ist eine Skript Version des XAML-Workflows, die unter [Erstellen eines Workflows mit Windows PowerShell-Aktivitäten](./creating-a-workflow-with-windows-powershell-activities.md)erläutert wird.

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