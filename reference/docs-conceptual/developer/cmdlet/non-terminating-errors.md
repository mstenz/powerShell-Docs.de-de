---
title: Fehler ohne Abbruch | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369599"
---
# <a name="non-terminating-errors"></a>Fehler ohne Abbruch

In diesem Thema wird die Methode erläutert, die zum Melden von Fehlern ohne Abbruch verwendet wird. Außerdem wird erläutert, wie die-Methode innerhalb des Cmdlets aufgerufen wird.

Wenn ein Fehler ohne Abbruch auftritt, sollte das Cmdlet diesen Fehler durch Aufrufen der [System. Management. Automation. Cmdlet. Write-error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode melden. Wenn das Cmdlet einen Fehler ohne Abbruch meldet, kann das Cmdlet weiterhin auf diesem Eingabe Objekt und auf weiteren eingehenden Pipeline Objekten arbeiten. Wenn das Cmdlet die [System. Management. Automation. Cmdlet. Write-error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode aufruft, kann das Cmdlet einen Fehler Daten Satz schreiben, der die Bedingung beschreibt, die den Fehler ohne Abbruch ausgelöst hat. Weitere Informationen zu Fehler Datensätzen finden Sie unter [Windows PowerShell-Fehler Datensätze](./windows-powershell-error-records.md).

Cmdlets können [System. Management. Automation. Cmdlet. Write-error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) nach Bedarf in ihren Eingabe Verarbeitungsmethoden aufgerufen werden. Cmdlets können jedoch [System. Management. Automation. Cmdlet. Write error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) nur von dem Thread aufrufen, der die Eingabe Verarbeitungsmethode [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)oder [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) aufgerufen hat. " [System. Management. Automation. Cmdlet. Write-error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) " kann nicht von einem anderen Thread aufgerufen werden. Stattdessen werden Fehler an den Haupt Thread übermittelt.

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. Cmdlet. Write error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Windows PowerShell-Fehler Datensätze](./windows-powershell-error-records.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
