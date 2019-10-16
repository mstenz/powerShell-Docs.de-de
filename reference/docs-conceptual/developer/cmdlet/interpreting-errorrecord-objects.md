---
title: Interpretieren von ErrorRecord-Objekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: 32ebf2531237bfd1042310ccc4155193a58401fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365419"
---
# <a name="interpreting-errorrecord-objects"></a>Interpretieren von ErrorRecord-Objekten

In den meisten Fällen stellt ein [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -Objekt einen Fehler ohne Abbruch dar, der von einem Befehl oder Skript generiert wird. Durch das Beenden von Fehlern können auch die zusätzlichen Informationen in einem ErrorRecord über die [System. Management. Automation. icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) -Schnittstelle angegeben werden.

Wenn Sie einen Fehlerhandler in das Skript oder einen Host schreiben möchten, um bestimmte Fehler zu behandeln, die während der Ausführung des Befehls oder Skripts auftreten, müssen Sie das [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -Objekt interpretieren, um zu bestimmen, ob es die Klasse von darstellt. der Fehler, den Sie behandeln möchten.

Wenn ein Cmdlet auf einen Fehler beim Beenden oder ohne Abbruch stößt, sollte ein Fehler Daten Satz erstellt werden, der den Fehlerzustand beschreibt. Die Host Anwendung muss diese Fehler Datensätze untersuchen und jede beliebige Aktion ausführen, um den Fehler zu beheben. Die Host Anwendung muss auch Fehler Datensätze für nicht abschließende Fehler untersuchen, die einen Datensatz nicht verarbeiten konnten, aber den Vorgang fortsetzen konnten, und Fehler Datensätze untersuchen, um Fehler zu beenden, die dazu führten, dass die Pipeline beendet wurde.

> [!NOTE]
> Zum Beenden von Fehlern Ruft das Cmdlet die [System. Management. Automation. Cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) -Methode auf. Bei Fehlern ohne Abbruch Ruft das Cmdlet die [System. Management. Automation. Cmdlet. Write-error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode auf.

## <a name="error-record-design"></a>Design des Fehler Datensatzes

Fehler Datensätze sind darauf ausgelegt, zusätzliche Fehlerinformationen bereitzustellen, die in Ausnahmen nicht verfügbar sind, und gleichzeitig sicherzustellen, dass die kombinierten Informationen in jedem Fehler Daten Satz eindeutig sind. Diese Eindeutigkeit ermöglicht der Host Anwendung, die verschiedenen Teile des Fehler Datensatzes zu überprüfen, sodass der Fehlerzustand und die Aktion, die der Host ausführen muss, identifiziert werden kann.

## <a name="interpreting-error-records"></a>Interpretieren von Fehler Datensätzen

Sie können verschiedene Teile des Fehler Datensatzes überprüfen, um den Fehler zu identifizieren. Diese Komponenten umfassen Folgendes:

- Die Fehler Kategorie

- Die Fehler Ausnahme

- Der voll qualifizierte Fehler Bezeichner (fqid)

- Weitere Informationen

### <a name="the-error-category"></a>Die Fehler Kategorie

Die Fehler Kategorie des Fehler Datensatzes ist eine der vordefinierten Konstanten, die von der [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) -Enumeration bereitgestellt werden. Diese Informationen sind über die [System. Management. Automation. ErrorRecord. categoryinfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) -Eigenschaft des [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -Objekts verfügbar.

Mit dem-Cmdlet können die Kategorien closeerror, OpenError, invalidtype, ReadError und beschreiteerror sowie andere Fehlerkategorien angegeben werden. Die Host Anwendung kann die Fehler Kategorie verwenden, um Gruppen von Fehlern zu erfassen.

### <a name="the-exception"></a>Die Ausnahme

Die im Fehler Daten Satz enthaltene Ausnahme wird vom-Cmdlet bereitgestellt. der Zugriff darauf erfolgt über die [System. Management. Automation. ErrorRecord. Exception *](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) -Eigenschaft des [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -Objekts.

Host Anwendungen können das `is`-Schlüsselwort verwenden, um zu ermitteln, dass die Ausnahme eine bestimmte Klasse oder eine abgeleitete Klasse ist. Es ist besser, den Ausnahmetyp zu verzweigen, wie im folgenden Beispiel gezeigt.

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

Auf diese Weise fangen Sie die abgeleiteten Klassen ab. Es treten jedoch Probleme auf, wenn die Ausnahme deserialisiert wird.

### <a name="the-fqid"></a>Die voll qualifizierte Benutzer-ID

Die fqid ist die spezifischsten Informationen, die Sie verwenden können, um den Fehler zu identifizieren. Dabei handelt es sich um eine Zeichenfolge, die einen Cmdlet-definierten Bezeichner, den Namen der Cmdlet-Klasse und die Quelle enthält, die den Fehler gemeldet hat. Im Allgemeinen ist ein Fehler Daten Satz analog zu einem Ereignisdaten Satz eines Windows-Ereignis Protokolls. Die fqid ist analog zum folgenden Tupel, das die Klasse des Ereignisdaten Satzes identifiziert: (*Protokoll Name*, *Quelle*, *Ereignis-ID*).

Die fqid ist so konzipiert, dass Sie als einzelne Zeichenfolge überprüft wird. Es gibt jedoch Fälle, in denen der Fehler Bezeichner von der Host Anwendung analysiert werden soll. Das folgende Beispiel ist eine wohlgeformte voll qualifizierte Fehlerkennung.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

Im vorherigen Beispiel ist das erste Token der Fehler Bezeichner, auf den der Name der Cmdlet-Klasse folgt. Der Fehler Bezeichner kann ein einzelnes Token sein, oder er kann ein durch Punkte getrennter Bezeichner sein, der die Verzweigung bei der Überprüfung des Bezeichners ermöglicht. Verwenden Sie keine Leerzeichen oder Interpunktions Zeichen in der Fehlerkennung. Es ist besonders wichtig, kein Komma zu verwenden. ein Komma wird von Windows PowerShell verwendet, um den Bezeichner und den Cmdlet-Klassennamen zu trennen.

### <a name="other-information"></a>Weitere Informationen

Das [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -Objekt kann auch Informationen bereitstellen, die die Umgebung beschreiben, in der der Fehler aufgetreten ist. Zu diesen Informationen zählen Elemente wie Fehlerdetails, Aufruf Informationen und das Zielobjekt, das beim Auftreten des Fehlers verarbeitet wurde. Obwohl diese Informationen für die Host Anwendung nützlich sein können, wird Sie in der Regel nicht zur Identifizierung des Fehlers verwendet. Diese Informationen sind über die folgenden Eigenschaften verfügbar:

[System. Management. Automation. ErrorRecord. errorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System. Management. Automation. ErrorRecord. invocationinfo](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System. Management. Automation. ErrorRecord. TargetObject](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System. Management. Automation. errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System. Management. Automation. Cmdlet. Write error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System. Management. Automation. Cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[Hinzufügen von Fehlerberichten ohne Abbruch zum Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell-Fehlerberichterstattung](./error-reporting-concepts.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
