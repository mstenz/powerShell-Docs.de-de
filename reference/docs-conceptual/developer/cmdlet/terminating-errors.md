---
title: Fehler beim Beenden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b804e738-aefa-41bb-9649-f9ed897fd96c
caps.latest.revision: 8
ms.openlocfilehash: d1967fe7996f75ec5229920f7ec49aa5ff6bdbfd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369329"
---
# <a name="terminating-errors"></a>Fehler mit Abbruch

In diesem Thema wird die Methode erläutert, die zum Melden von Abbruch Fehlern verwendet wird Außerdem wird erläutert, wie die-Methode innerhalb des Cmdlets aufgerufen wird, und es werden die Ausnahmen erläutert, die von der Windows PowerShell-Laufzeit zurückgegeben werden können, wenn die-Methode aufgerufen wird.

Wenn ein Abbruch Fehler auftritt, sollte das Cmdlet den Fehler durch Aufrufen der [System. Management. Automation. Cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) -Methode melden. Diese Methode ermöglicht es dem Cmdlet, einen Fehler Daten Satz zu senden, der die Bedingung beschreibt, die den abschließenden Fehler verursacht hat. Weitere Informationen zu Fehler Datensätzen finden Sie unter [Windows PowerShell-Fehler Datensätze](./windows-powershell-error-records.md).

Wenn die [System. Management. Automation. Cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) -Methode aufgerufen wird, beendet die Windows PowerShell-Laufzeit die Ausführung der Pipeline dauerhaft und löst eine [System. Management. Automation. pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) -Ausnahme aus. Alle nachfolgenden Versuche, [System. Management. Automation. Cmdlet. Write-Object](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), [System. Management. Automation. Cmdlet. Write Test Error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)oder mehrere andere APIs aufzurufen, lösen diese Aufrufe eine [System. Management. Automation. pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) -Ausnahme aus.

Die [System. Management. Automation. pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) -Ausnahme kann auch auftreten, wenn ein anderes Cmdlet in der Pipeline einen Abbruch Fehler meldet, wenn der Benutzer aufgefordert wurde, die Pipeline zu beenden, oder wenn die Pipeline aus irgendeinem Grund vor dem Abschluss angehalten wurde. Das Cmdlet muss die [System. Management. Automation. pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) -Ausnahme nicht abfangen, es sei denn, es muss offene Ressourcen oder den internen Zustand bereinigen.

Cmdlets können eine beliebige Anzahl von Ausgabe Objekten oder nicht Beendigungs Fehlern schreiben, bevor ein Abbruch Fehler gemeldet wird. Allerdings wird die Pipeline durch den abschließenden Fehler permanent beendet, und es können keine weiteren Ausgaben, Abbruch Fehler oder Fehler ohne Abbruch gemeldet werden.

Cmdlets können [System. Management. Automation. Cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) nur aus dem Thread aufrufen, der die Eingabe Verarbeitungsmethode [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)oder [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) aufgerufen hat. Versuchen Sie nicht, " [System. Management. Automation. Cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) " oder " [System. Management. Automation. Cmdlet. Write-error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) " aus einem anderen Thread aufzurufen. Stattdessen müssen Fehler an den Haupt Thread übermittelt werden.

Es ist möglich, dass ein Cmdlet in der Implementierung der [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)-, [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)-Methode oder der [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode eine Ausnahme auslöst. Jede Ausnahme, die von diesen Methoden ausgelöst wird (mit Ausnahme einiger schwerwiegender Fehlerbedingungen zum Beenden des Windows PowerShell-Hosts), wird als Beendigungs Fehler interpretiert, der die Pipeline, aber nicht als Ganzes als Windows PowerShell stoppt. (Dies gilt nur für den Haupt-Cmdlet-Thread. Nicht abgefangene Ausnahmen in Threads, die durch das Cmdlet erzeugt werden, stoppen den Windows PowerShell-Host im Allgemeinen.) Es wird empfohlen, dass Sie [System. Management. Automation. Cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) verwenden, anstatt eine Ausnahme auszulösen, da der Fehler Daten Satz zusätzliche Informationen über die Fehlerbedingung bereitstellt, die für den Endbenutzer nützlich ist. Cmdlets sollten die Richtlinie für verwalteten Code beachten, um alle Ausnahmen abzufangen und zu behandeln (`catch (Exception e)`). Konvertieren Sie nur Ausnahmen bekannter und erwarteter Typen in Fehler Datensätze.

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[System. Management. Automation. Cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System. Management. Automation. Cmdlet. Write error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell-Fehler Datensätze](./windows-powershell-error-records.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
