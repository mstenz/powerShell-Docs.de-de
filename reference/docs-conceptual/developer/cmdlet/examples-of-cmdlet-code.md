---
title: Beispiele für Cmdlet-Code | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364499"
---
# <a name="examples-of-cmdlet-code"></a>Cmdlet-Codebeispiele

Dieser Abschnitt enthält Beispiele für Cmdlet-Code, den Sie verwenden können, um mit dem Schreiben Ihrer eigenen Cmdlets zu beginnen.

> [!IMPORTANT]
> Eine schrittweise Anleitung zum Schreiben von Cmdlets finden Sie in den [Tutorials zum Schreiben von Cmdlets](./tutorials-for-writing-cmdlets.md).

## <a name="in-this-section"></a>In diesem Abschnitt

[Schreiben eines einfachen Cmdlets](./how-to-write-a-simple-cmdlet.md) Dieses Beispiel zeigt die grundlegende Struktur des Cmdlet-Codes.

[Deklarieren von Cmdlet-Parametern](./how-to-declare-cmdlet-parameters.md) In diesem Beispiel wird gezeigt, wie die verschiedenen Typen von Parametern deklariert werden.

[Deklarieren von Parameter Sätzen](./how-to-declare-parameter-sets.md) Dieses Beispiel zeigt, wie Sie Sätze von Parametern deklarieren können, die die Aktion ändern können, die ein Cmdlet ausführt.

[Validieren von Parameter Eingaben](./how-to-validate-parameter-input.md) In diesen Beispielen wird gezeigt, wie Parameter Eingaben überprüft werden.

[Deklarieren dynamischer Parameter](./how-to-declare-dynamic-parameters.md) Dieses Beispiel zeigt, wie ein Parameter deklariert wird, der zur Laufzeit hinzugefügt wird.

[Aufrufen von Skripts in einem Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) Dieses Beispiel zeigt, wie ein Skript aufgerufen wird, das für ein Cmdlet bereitgestellt wird.

[Überschreiben von Eingabe Verarbeitungsmethoden](./how-to-override-input-processing-methods.md) Diese Beispiele zeigen die grundlegende Struktur, die zum Überschreiben der BeginProcessing-, ProcessRecord-und EndProcessing-Methode verwendet wird.

Vorgehens [Weise bei der Unterstützung von "schuldprocess](./how-to-request-confirmations.md) " Dieses Beispiel zeigt, wie die Methoden " [System. Management. Automation. Cmdlet. Schulter dprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) " und " [System. Management. Automation. Cmdlet. daudcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) " innerhalb eines Cmdlets aufgerufen werden sollten.

[Unterstützung von Transaktionen](./how-to-support-transactions.md) Dieses Beispiel zeigt, wie Sie angeben, dass das Cmdlet Transaktionen unterstützt und wie Sie die Aktion implementieren, die durchgeführt wird, wenn das Cmdlet innerhalb einer Transaktion verwendet wird.

Vorgehens [Weise beim unterstützen von Aufträgen](./how-to-support-jobs.md) In diesem Beispiel wird gezeigt, wie Aufträge beim Schreiben von Cmdlets unterstützt werden.

[Aufrufen eines Cmdlets innerhalb eines Cmdlets](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) In diesem Beispiel wird gezeigt, wie ein Cmdlet aus einem anderen Cmdlet aufgerufen wird, mit dem Sie die Funktionalität des aufgerufenen Cmdlets zum Cmdlet hinzufügen können, das Sie entwickeln.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
