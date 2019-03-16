---
title: Nicht endenden Fehler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054356"
---
# <a name="non-terminating-errors"></a>Fehler ohne Abbruch

In diesem Thema wird erläutert, die Methode verwendet, um Fehler ohne Abbruch zu melden. Es wird erläutert, wie die Methode aus, in dem-Cmdlet aufrufen.

Tritt ein Fehler ohne Abbruch, das Cmdlet sollte melden Sie diesen Fehler durch Aufrufen der [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) Methode. Wenn das Cmdlet einen Fehler ohne Abbruch meldet, kann das Cmdlet funktioniert auf diesem Eingabeobjekt und weiteren eingehenden weiterhin pipeline Objekte. Wenn Sie das Cmdlet Ruft die [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode, schreibt das Cmdlet kann ein Error-Datensatzes, der die Bedingung beschreibt, die den Fehler ohne Abbruch verursacht hat. Weitere Informationen zu Datensätzen, finden Sie unter [Windows PowerShell-Fehlerdatensätze](./windows-powershell-error-records.md).

Cmdlets aufrufen können [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aus innerhalb ihrer eingabeverarbeitungsmethoden nach Bedarf. Allerdings Cmdlets aufrufen können [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) nur aus dem Thread, der Namen der [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), oder [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Geben Sie die Verarbeitungsmethode aus. Rufen Sie keine [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aus einem anderen Thread. Kommunizieren Sie stattdessen Fehlern zurück an den primären Thread.

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Windows PowerShell-Error-Datensätze](./windows-powershell-error-records.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
