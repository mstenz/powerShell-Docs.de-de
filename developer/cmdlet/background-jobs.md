---
title: Hintergrundaufträge | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794704"
---
# <a name="background-jobs"></a>Hintergrundaufträge

Cmdlets können ihre Aktion ausführen, intern oder als ein Windows PowerShell*Hintergrundauftrag*. Wenn ein Cmdlet als Hintergrundauftrag ausgeführt wird, wird die Arbeit asynchron in einem eigenen Thread getrennt von der Pipeline-Thread durchgeführt, die mit dem-Cmdlet verwendet wird. Aus der Perspektive des Benutzers Wenn ein Cmdlet als Hintergrundauftrag ausgeführt wird die Eingabeaufforderung wird sofort zurückgegeben auch, wenn der Auftrag einen erweiterten Zeitraum nimmt abgeschlossen und der Benutzer ohne Unterbrechung weiterhin während der Auftrag ausgeführt wird.

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>Hintergrundaufträge, untergeordneten Aufträge und die Auftragsrepository

Das Objekt, das von den Cmdlets zurückgegeben wird, die Unterstützung von Hintergrundaufträgen definiert den Auftrag. (Die [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) Cmdlet gibt auch ein Auftragsobjekt zurück.) Der Name des Auftrags und ein Bezeichner, der verwendet wird, um den Auftrag, Informationen über den Zustand und die untergeordneten Aufträge angeben, sind in dieser Definition enthalten. Der Auftrag führt keiner arbeiten. Jeden Hintergrundauftrag verfügt über mindestens einen untergeordneten Auftrag aus, da der untergeordnete Auftrag die eigentliche Arbeit ausführt. Wenn Sie ein Cmdlet ausgeführt, sodass die Arbeit als Hintergrundauftrag ausgeführt wird, das Cmdlet muss hinzufügen den Auftrag und die untergeordneten Aufträge auf einem gemeinsamen Repository, um genannte der *auftragsrepository*.

Weitere Informationen zur Behandlung von Hintergrundaufträgen in der Befehlszeile finden Sie hier:

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>Schreiben eines Cmdlets, die als Hintergrundauftrag ausgeführt wird.

Um ein Cmdlet zu schreiben, die als Hintergrundauftrag ausgeführt werden können, müssen Sie die folgenden Aufgaben ausführen:

- Definieren einer `asJob` switch-Parameter, damit der Benutzer entscheiden, ob das Cmdlet als Hintergrundauftrag ausführen kann.

- Erstellen Sie ein Objekt, das von abgeleitet ist die [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Klasse. Dieses Objekt kann sein, ein benutzerdefiniertes Job-Objekt oder ein Job-Objekt, das von Windows PowerShell bereitgestellt wurde, z. B. eine [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) Objekt.

- Fügen Sie in einem Datensatz Verarbeitungsmethode ein `if` -Anweisung, die erkennt, ob das Cmdlet als Hintergrundauftrag ausgeführt werden soll.

- Implementieren Sie für benutzerdefinierte Auftragstypen-Objekte die Auftragsklasse.

- Zurückgeben der entsprechenden Objekte, abhängig davon, ob das Cmdlet als Hintergrundauftrag ausgeführt wird.

Ein Codebeispiel finden Sie unter [wie Unterstützung Aufträge](./how-to-support-jobs.md).

## <a name="background-job-related-apis"></a>Auftragsbezogene Hintergrund-APIs

Die folgenden APIs werden von Windows PowerShell zum Verwalten von Hintergrundaufträgen bereitgestellt.

[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) benutzerdefinierte Auftragsobjekte abgeleitet. Dies ist eine abstrakte Klasse.

[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) verwaltet und bietet Informationen zum aktuellen aktiven Hintergrundaufträge.

[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) definiert den Status des Hintergrundauftrags. Der Zustände enthalten, gestartet, ausgeführt und beendet.

[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) enthält Informationen zum Status eines Auftrags im Hintergrund und, wenn der letzte Zustand geändert wurde aufgrund eines Fehlers, der Grund, die der Auftrag angenommen hat, den aktuellen Zustand verursacht.

[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) stellt die Argumente für ein Ereignis, das ausgelöst wird, wenn ein Hintergrundauftrag Zustand ändert.

## <a name="windows-powershell-job-cmdlets"></a>Windows PowerShell-Job-Cmdlets

Die folgenden Cmdlets werden von Windows PowerShell zum Verwalten von Hintergrundaufträgen bereitgestellt.

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
