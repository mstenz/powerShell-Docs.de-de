---
title: Hintergrund Aufträge | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363559"
---
# <a name="background-jobs"></a>Hintergrundaufträge

Cmdlets können Ihre Aktion intern oder als Windows PowerShell-*Hintergrund Auftrag*ausführen. Wenn ein Cmdlet als Hintergrund Auftrag ausgeführt wird, wird die Arbeit asynchron in einem eigenen Thread ausgeführt, getrennt vom Pipeline Thread, der vom Cmdlet verwendet wird. Aus Sicht des Benutzers, wenn ein Cmdlet als Hintergrund Auftrag ausgeführt wird, wird die Eingabeaufforderung sofort zurückgegeben, auch wenn die Ausführung des Auftrags längere Zeit in Anspruch nimmt und der Benutzer ohne Unterbrechung fortfahren kann, während der Auftrag ausgeführt wird.

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>Hintergrund Aufträge, untergeordnete Aufträge und das auftragsrepository

Das Auftrags Objekt, das von den Cmdlets zurückgegeben wird, die Hintergrund Aufträge unterstützen, definiert den Auftrag. (Das [Start-Job-](/powershell/module/Microsoft.PowerShell.Core/Start-Job) Cmdlet gibt auch ein Auftrags Objekt zurück.) Der Name des Auftrags, ein Bezeichner, der verwendet wird, um den Auftrag, die Zustandsinformationen und die untergeordneten Aufträge anzugeben, sind in dieser Definition enthalten. Der Auftrag führt keine der Arbeit aus. Jeder Hintergrund Auftrag hat mindestens einen untergeordneten Auftrag, da der untergeordnete Auftrag die tatsächliche Arbeit ausführt. Wenn Sie ein Cmdlet ausführen, sodass die Arbeit als Hintergrund Auftrag ausgeführt wird, muss das Cmdlet den Auftrag und die untergeordneten Aufträge einem gemeinsamen Repository hinzufügen, das als *auftragsrepository*bezeichnet wird.

Weitere Informationen zur Verarbeitung von Hintergrund Aufträgen in der Befehlszeile finden Sie in den folgenden Bereichen:

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>Schreiben eines Cmdlets, das als Hintergrund Auftrag ausgeführt wird

Zum Schreiben eines Cmdlets, das als Hintergrund Auftrag ausgeführt werden kann, müssen Sie die folgenden Aufgaben ausführen:

- Definieren Sie einen `asJob`-Schalter Parameter, sodass der Benutzer entscheiden kann, ob das Cmdlet als Hintergrund Auftrag ausgeführt werden soll.

- Erstellen Sie ein Objekt, das von der [System. Management. Automation. Job](/dotnet/api/System.Management.Automation.Job) -Klasse abgeleitet wird. Bei diesem Objekt kann es sich um ein benutzerdefiniertes Auftrags Objekt oder ein von Windows PowerShell bereitgestelltes Auftrags Objekt handeln, z. b. ein [System. Management. Automation. psiebziger Job](/dotnet/api/System.Management.Automation.PSEventJob) -Objekt.

- Fügen Sie in einer Daten Satz Verarbeitungsmethode eine `if`-Anweisung hinzu, die erkennt, ob das Cmdlet als Hintergrund Auftrag ausgeführt werden soll.

- Implementieren Sie für benutzerdefinierte Auftrags Objekte die Job-Klasse.

- Gibt die entsprechenden Objekte zurück, je nachdem, ob das Cmdlet als Hintergrund Auftrag ausgeführt wird.

Ein Codebeispiel finden [Sie unter How to Support Jobs](./how-to-support-jobs.md).

## <a name="background-job-related-apis"></a>Im Hintergrund für Aufträge relevante APIs

Die folgenden APIs werden von Windows PowerShell zur Verwaltung von Hintergrund Aufträgen bereitgestellt.

[System. Management. Automation. Job](/dotnet/api/System.Management.Automation.Job) leitet benutzerdefinierte Auftrags Objekte ab. Dies ist eine abstrakte Klasse.

[System. Management. Automation. jobrepository](/dotnet/api/System.Management.Automation.JobRepository) verwaltet und stellt Informationen über die aktuellen aktiven Hintergrund Aufträge bereit.

[System. Management. Automation. jobstate](/dotnet/api/System.Management.Automation.JobState) definiert den Status des Hintergrund Auftrags. Zu den Zuständen zählen Started, Running und beendet.

[System. Management. Automation. jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) stellt Informationen über den Status eines Hintergrund Auftrags bereit und, wenn die letzte Zustandsänderung durch einen Fehler verursacht wurde, den Grund für den aktuellen Status des Auftrags.

[System. Management. Automation. jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) stellt die Argumente für ein Ereignis bereit, das ausgelöst wird, wenn sich der Zustand eines Hintergrund Auftrags ändert.

## <a name="windows-powershell-job-cmdlets"></a>Windows PowerShell-Auftrags-Cmdlets

Die folgenden Cmdlets werden von Windows PowerShell zur Verwaltung von Hintergrund Aufträgen bereitgestellt.

[Get-Job](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

Ruft Windows PowerShell-Hintergrundaufträge ab, die in der aktuellen Sitzung ausgeführt werden.

[Receive-Job](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

Ruft die Ergebnisse der Windows PowerShell-Hintergrundaufträge in der aktuellen Sitzung ab.

[Remove-Job](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

Löscht einen Windows PowerShell-Hintergrundauftrag.

[Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

Startet einen Windows PowerShell-Hintergrundauftrag.

[Stop-Job](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

Beendet einen Windows PowerShell-Hintergrundauftrag.

[Wait-Job](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

Unterdrückt die Eingabeaufforderung, bis ein oder alle der in der Sitzung ausgeführten Windows PowerShell-Hintergrundaufträge abgeschlossen sind.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
