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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853046"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>Erstellen eines Workflows mit einem Windows PowerShell-Skript

Sie können einen Workflow erstellen, indem Sie ein Windows PowerShell-Skript zu schreiben. Um einen Workflow zu erstellen, verwenden Sie das Workflow-Schlüsselwort, gefolgt von einem Namen für den Workflow vor dem Hauptteil des Skripts. Beispiel:

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

Finden Sie den Workflow, in der gleichen genauso wie jeden anderen Windows PowerShell-Befehl.

## <a name="implementing-parallel-and-sequence"></a>Implementieren parallele und Sequence

[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) unterstützt die parallele Ausführung von Aktivitäten. Um diese Funktion in einem Windows PowerShell-Skript zu implementieren, verwenden die `parallel` Schlüsselwort vor einen Skriptblock. Sie können auch die `foreach -parallel` Konstruktion, um eine Auflistung von Objekten, die parallel durchlaufen. Um eine Gruppe von Aktivitäten in sequenzieller Reihenfolge in einem parallelen Block auszuführen, schließen Sie diese Gruppe von Aktivitäten in einem Skriptblock aus, und stellen Sie den Block mit dem Tasksequenz-Schlüsselwort voran.

## <a name="joining-computers-to-a-domain"></a>Einbinden von Computern in einer Domäne

Das folgende Skript erstellt einen Workflow, die sie mit einer Domäne verknüpft werden, wenn sie nicht bereits verknüpft sind, und klicken Sie dann erneut den Status überprüft überprüft den Domänenstatus einer Gruppe von Benutzer angegebenen Computer an. Dies ist eine Skriptversion des XAML-Workflows, die in erläutert [Erstellen eines Workflows mit Windows PowerShell-Aktivitäten](./creating-a-workflow-with-windows-powershell-activities.md).

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