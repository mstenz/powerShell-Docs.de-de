---
title: GetProc Tutorial | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068095"
---
# <a name="getproc-tutorial"></a>GetProc-Tutorial

Dieser Abschnitt enthält ein Tutorial für eine Get-Proc-Cmdlet erstellen, ähnelt die [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet von Windows PowerShell. Dieses Tutorial bietet Codefragmente, die veranschaulichen, wie die Cmdlets implementiert werden, sowie eine Erläuterung des Codes.

## <a name="topics-in-this-tutorial"></a>Die Themen in diesem Tutorial

Die Themen in diesem Tutorial dienen, die sequenziell gelesen werden, mit jedem Thema erstellen auf die in vorherigen Thema behandelt wurde.

[Erstellen ein Cmdlet ohne Parameter](./creating-a-cmdlet-without-parameters.md) in diesem Abschnitt wird beschrieben, wie ein Cmdlet zu erstellen, ruft Informationen aus dem lokalen Computer, ohne die Verwendung von Parametern ab, und schreibt dann die Informationen in der Pipeline.

[Hinzufügen von Parametern, die diesem Prozess Command-Line-Eingabe](./adding-parameters-that-process-command-line-input.md) in diesem Abschnitt wird beschrieben, wie das Cmdlet "Get-Proc" einen Parameter hinzugefügt werden, damit das Cmdlet die Eingabe, die auf der Grundlage explizite Objekte, die an das Cmdlet übergeben verarbeiten kann. Die beschriebenen Implementierung hier ruft Prozesse, die basierend auf ihren Namen und schreibt dann die Informationen in der Pipeline.

[Hinzufügen von Parametern, Prozess-Pipelineeingabe](./adding-parameters-that-process-pipeline-input.md) in diesem Abschnitt wird beschrieben, wie das Cmdlet "Get-Proc" einen Parameter hinzugefügt werden, damit das Cmdlet über die Pipeline übergebenen Objekte verarbeiten kann. Beschriebenen Cmdlets für die Implementierung hier ruft werden auf Grundlage von Objekten, die an das Cmdlet übergeben und schreibt dann die Informationen in der Pipeline.

[Ihr Cmdlet hinzugefügt ohne Abbruch Fehlerberichterstattung](./adding-non-terminating-error-reporting-to-your-cmdlet.md) in diesem Abschnitt wird beschrieben, wie ohne Abbruch Fehlerberichte, die an ein Cmdlet hinzufügen. Die hier beschriebene Implementierung erkennt Fehler ohne Abbruch, die auftreten, wenn die Eingabe verarbeitet und einen Fehlerdatensatz in den fehlerdatenstrom geschrieben.

## <a name="see-also"></a>Weitere Informationen

[Erstellen ein Cmdlet ohne Parameter](./creating-a-cmdlet-without-parameters.md)

[Hinzufügen von Parametern, die Befehlszeileneingabe verarbeiten](./adding-parameters-that-process-command-line-input.md)

[Hinzufügen von Parametern, die Eingabe der Prozesspipeline](./adding-parameters-that-process-pipeline-input.md)

[Ohne Abbruch Fehlerberichte, die an Ihr Cmdlet hinzufügen](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
