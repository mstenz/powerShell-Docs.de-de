---
title: Cmdlet-Ausgabetypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.assetid: 547e6695-e936-4cac-a90b-417d0dab393d
caps.latest.revision: 12
ms.openlocfilehash: 3efa98c7aa22fdaee8042bae99282aea0618ef5f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853926"
---
# <a name="types-of-cmdlet-output"></a>Typen von Cmdlet-Ausgabe

PowerShell bietet mehrere Methoden, die mithilfe von Cmdlets, die zum Generieren einer Ausgabe aufgerufen werden können. Diese Methoden verwenden einen bestimmten Vorgang in einen Stream mit bestimmten Daten, z. B. den Datenstrom für den Erfolg oder den fehlerdatenstrom ihre Ausgabe schreiben. Dieser Artikel beschreibt die Arten von Ausgabe und die Methoden, die mit dem sie generiert.

## <a name="types-of-output"></a>Arten von Ausgaben.

### <a name="success-output"></a>Erfolgs-Ausgabe

-Cmdlets können Erfolg melden, durch Zurückgeben eines Objekts, das mit dem nächsten Befehl in der Pipeline verarbeitet werden kann. Nachdem Sie das Cmdlet die Aktion erfolgreich ausgeführt hat, das Cmdlet Ruft die [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) Methode. Es wird empfohlen, dass Sie diese Methode anstelle von Aufrufen der [System.Console.WriteLine](/dotnet/api/System.Console.WriteLine) oder [System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) Methoden.

Sie können angeben, ein **PassThru** switch-Parameter für Cmdlets, die in der Regel keine Objekte zurückgeben.
Wenn die **PassThru** Switch-Parameter in der Befehlszeile angegeben ist, mit dem-Cmdlet wird aufgefordert, ein Objekt zurück. Ein Beispiel für ein Cmdlet aus, die eine **PassThru** Parameter finden Sie unter [Add-History](/powershell/module/Microsoft.PowerShell.Core/Add-History).

### <a name="error-output"></a>Fehler bei der Ausgabe

Cmdlets können Fehler gemeldet. Tritt ein Fehler mit Abbruch, löst das Cmdlet eine Ausnahme aus. Tritt ein Fehler ohne Abbruch, das Cmdlet Ruft die [System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) Methode, um einen Fehlerdatensatz in den fehlerdatenstrom für die Daten zu senden. Weitere Informationen zur Fehlerberichterstattung finden Sie unter [Konzepte von Reporting Fehler](./error-reporting-concepts.md).

### <a name="verbose-output"></a>Ausführliche Ausgabe

Cmdlets können nützliche Informationen für Sie bereitstellen, während das Cmdlet ordnungsgemäß Datensätze durch den Aufruf verarbeitet die [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) Methode. Ausführliche Meldungen, die angeben, wie die Aktion ist, generiert die Methode.

Standardmäßig werden ausführliche Meldungen nicht angezeigt. Sie können angeben, die **ausführlich** Parameter an, wenn das Cmdlet ausgeführt wird, um diese Meldungen anzuzeigen. **Ausführliche** ist ein allgemeiner Parameter, die für alle Cmdlets verfügbar ist.

### <a name="progress-output"></a>Status-Ausgabe

Cmdlets können Statusinformationen für Sie bereitstellen, wenn das Cmdlet Aufgaben, die sehr lange durchführt dauern – beispielsweise ein Verzeichnis rekursiv zu kopieren, nutzen. Zum Anzeigen von Statusinformationen mit dem-Cmdlet Ruft die [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) Methode.

### <a name="debug-output"></a>Debug-Ausgabe

-Cmdlets können Debugmeldungen bieten, die Sie bei der Problembehandlung des Cmdlet-Codes. Zum Anzeigen von Informationen zum Debuggen mit dem-Cmdlet Ruft die [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) Methode.

Debugmeldungen werden in der Standardeinstellung nicht angezeigt. Sie können angeben, die **Debuggen** Parameter an, wenn das Cmdlet ausgeführt wird, um diese Meldungen anzuzeigen. **Debuggen von** ist ein allgemeiner Parameter, die für alle Cmdlets verfügbar ist.

### <a name="warning-output"></a>Warnung-Ausgabe

Cmdlets können Warnmeldungen anzeigen, durch den Aufruf der [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) Methode.

Standardmäßig werden Warnmeldungen angezeigt. Allerdings können Sie Warnmeldungen konfigurieren, mit der `$WarningPreference` Variable oder mithilfe der **ausführlich** und **Debuggen** Parameter, wenn das-Cmdlet aufgerufen wird.

## <a name="displaying-output"></a>Anzeigen der Ausgabe

Für alle Write-Methode Aufrufe wird die Inhaltsanzeige durch eine spezifische Runtime Variablen bestimmt. Die Ausnahme ist die [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) Methode. Mithilfe dieser Variablen können Sie machen die entsprechenden Aufruf an die richtige Stelle im Code zu schreiben und sich keine Gedanken über wann oder ob die Ausgabe angezeigt werden soll.

## <a name="accessing-the-output-functionality-of-a-host-application"></a>Zugreifen auf die Funktionalität der Ausgabe einer hostanwendung

Sie können auch ein Cmdlet aus, um direkt die Ausgabe-Funktionen einer hostanwendung zuzugreifen, über die PowerShell-Laufzeit entwerfen. Mithilfe des Hosts mithilfe von PowerShell anstelle der bereitgestellten APIs ["System.Console"](/dotnet/api/System.Console) oder ["System.Windows.Forms"](/dotnet/api/System.Windows.Forms) wird sichergestellt, dass Ihr Cmdlet mit einer Vielzahl von Hosts verwendet wird. Zum Beispiel: die **powershell.exe** Konsolenhost, die **powershell_ise.exe** grafischer Host, der PowerShell-Remoting-Host und Drittanbieter-Hosts.

## <a name="see-also"></a>Siehe auch

[Konzepte von Reporting Fehler](./error-reporting-concepts.md)

[Übersicht über Cmdlets](./cmdlet-overview.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)