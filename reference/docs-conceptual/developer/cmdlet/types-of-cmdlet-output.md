---
title: Typen der Cmdlet-Ausgabe | Microsoft-Dokumentation
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369289"
---
# <a name="types-of-cmdlet-output"></a>Cmdlet-Ausgabetypen

PowerShell bietet mehrere Methoden, die von Cmdlets aufgerufen werden können, um die Ausgabe zu generieren. Diese Methoden verwenden einen bestimmten Vorgang, um Ihre Ausgabe in einen bestimmten Datenstream zu schreiben, z. b. den Success Data Stream oder den Fehler Datenstrom. In diesem Artikel werden die Ausgabetypen und die Methoden beschrieben, die zum Generieren der Ausgabe verwendet werden.

## <a name="types-of-output"></a>Ausgabetypen

### <a name="success-output"></a>Erfolgs Ausgabe

Cmdlets können einen Erfolg melden, indem Sie ein Objekt zurückgeben, das vom nächsten Befehl in der Pipeline verarbeitet werden kann. Nachdem das Cmdlet seine Aktion erfolgreich ausgeführt hat, ruft das Cmdlet die [System. Management. Automation. Cmdlet. Write Object](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) -Methode auf. Es wird empfohlen, diese Methode anstelle der [System. Console. Write teline](/dotnet/api/System.Console.WriteLine) -Methode oder der [System. Management. Automation. Host. pshostuserinterface. Write teline](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) -Methode aufzurufen.

Sie können einen **passthru** -Schalter Parameter für Cmdlets bereitstellen, die in der Regel keine Objekte zurückgeben.
Wenn der **passthru** -Schalter Parameter in der Befehlszeile angegeben ist, wird das Cmdlet aufgefordert, ein Objekt zurückzugeben. Ein Beispiel für ein Cmdlet, das über einen **passthru** -Parameter verfügt, finden [Sie unter Add-History](/powershell/module/Microsoft.PowerShell.Core/Add-History).

### <a name="error-output"></a>Fehlerausgabe

Cmdlets können Fehler melden. Wenn ein Abbruch Fehler auftritt, löst das Cmdlet eine Ausnahme aus. Wenn ein Fehler ohne Abbruch auftritt, ruft das Cmdlet die [System. Management. Automation. Provider. cmdletprovider. Write-error](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) -Methode auf, um einen Fehler Daten Satz an den Fehler Datenstrom zu senden. Weitere Informationen zur Fehlerberichterstattung finden Sie unter [Konzepte für die Fehlerberichterstattung](./error-reporting-concepts.md).

### <a name="verbose-output"></a>Ausführliche Ausgabe

Cmdlets können nützliche Informationen bereitstellen, während das Cmdlet Datensätze ordnungsgemäß verarbeitet, indem Sie die [System. Management. Automation. Cmdlet. Write-Verbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) -Methode aufrufen. Die-Methode generiert ausführliche Meldungen, die angeben, wie die Aktion fortgesetzt wird.

Standardmäßig werden ausführliche Meldungen nicht angezeigt. Sie können den **verbose** -Parameter angeben, wenn das Cmdlet ausgeführt wird, um diese Meldungen anzuzeigen. **Verbose** ist ein allgemeiner Parameter, der für alle Cmdlets verfügbar ist.

### <a name="progress-output"></a>Fortschritts Ausgabe

Cmdlets können Ihnen Fortschrittsinformationen bereitstellen, wenn das Cmdlet Aufgaben ausführt, deren Ausführung viel Zeit in Anspruch nimmt, z. b. das rekursiv Kopieren eines Verzeichnisses. Zum Anzeigen von Statusinformationen Ruft das Cmdlet die [System. Management. Automation. Cmdlet. Write Progress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) -Methode auf.

### <a name="debug-output"></a>Ausgabe Debuggen

Cmdlets können Debugmeldungen bereitstellen, die bei der Problembehandlung für den Cmdlet-Code hilfreich sind. Um Debuginformationen anzuzeigen, ruft das Cmdlet die [System. Management. Automation. Cmdlet. Write Team Debug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) -Methode auf.

Standardmäßig werden keine Debugmeldungen angezeigt. Sie können den **Debug** -Parameter angeben, wenn das Cmdlet ausgeführt wird, um diese Meldungen anzuzeigen. **Debug** ist ein allgemeiner Parameter, der für alle Cmdlets verfügbar ist.

### <a name="warning-output"></a>Warnungs Ausgabe

Cmdlets können Warnmeldungen anzeigen, indem Sie die [System. Management. Automation. Cmdlet. Write Warning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) -Methode aufrufen.

Standardmäßig werden Warnmeldungen angezeigt. Sie können jedoch Warnmeldungen konfigurieren, indem Sie die Variable "`$WarningPreference`" oder die Parameter " **verbose** " und " **Debug** " verwenden, wenn das Cmdlet aufgerufen wird.

## <a name="displaying-output"></a>Anzeigen der Ausgabe

Für alle Aufrufe der Schreibmethode wird die Inhalts Anzeige durch bestimmte Lauf Zeitvariablen bestimmt. Die Ausnahme ist die [System. Management. Automation. Cmdlet. Write Object](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) -Methode. Wenn Sie diese Variablen verwenden, können Sie den entsprechenden Schreibvorgang an der richtigen Stelle im Code vornehmen und sich keine Gedanken darüber machen, wann oder ob die Ausgabe angezeigt werden soll.

## <a name="accessing-the-output-functionality-of-a-host-application"></a>Zugreifen auf die Ausgabefunktionen einer Host Anwendung

Sie können ein Cmdlet auch so entwerfen, dass direkt auf die Ausgabefunktionen einer Host Anwendung über die PowerShell-Laufzeit zugegriffen wird. Durch die Verwendung der von PowerShell bereitgestellten Host-APIs anstelle von [System. Console](/dotnet/api/System.Console) oder [System. Windows. Forms](/dotnet/api/System.Windows.Forms) wird sichergestellt, dass das Cmdlet mit einer Vielzahl von Hosts funktioniert. Beispiel: der Konsolen Host " **PowerShell. exe** ", der grafische Host " **powershell_ise. exe** ", der PowerShell-Remoting-Host und die Drittanbieter Hosts.

## <a name="see-also"></a>Siehe auch

[Konzepte für die Fehlerberichterstattung](./error-reporting-concepts.md)

[Cmdlet-Übersicht](./cmdlet-overview.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)