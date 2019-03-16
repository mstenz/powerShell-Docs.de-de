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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058775"
---
# <a name="interpreting-errorrecord-objects"></a>Interpretieren von ErrorRecord-Objekten

In den meisten Fällen eine [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) Objekt darstellt, einen Fehler ohne Abbruch von eines Befehls oder Skripts generiert. Beenden die Fehler kann auch die zusätzliche Informationen in einer ErrorRecord über angeben der [System.Management.Automation.Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) Schnittstelle.

Wenn Sie einen Fehlerhandler in das Skript oder einen Host zum Verarbeiten von Fehlermeldungen, die während der Ausführung Befehls oder Skripts auftreten, müssen Sie zu interpretieren schreiben möchten die [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) Objekt, um zu bestimmen, ob es Stellt die Klasse der Fehler, die Sie behandeln möchten.

Wenn ein Cmdlet erkennt einen Abbruch oder Fehler ohne Abbruch, sollten sie einen Fehlerdatensatz erstellen, der den Fehlerzustand beschreibt. Die hostanwendung muss untersuchen diese Fehlerdatensätze und führen Sie jede beliebige Aktion den Fehler mindert. Die hostanwendung muss auch Fehlerdatensätze für Fehler ohne Abbruch, die Fehler bei der Verarbeitung eines Datensatzes, aber weiterhin wurden untersuchen und es muss untersuchen, Error-Datensätze für Fehler mit Abbruch, die die Pipeline beendet verursacht hat.

> [!NOTE]
> Für Fehler mit Abbruch, das Cmdlet Ruft die [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) Methode. Für Fehler ohne Abbruch, das Cmdlet Ruft die [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) Methode.

## <a name="error-record-design"></a>Fehler beim Aufzeichnen Entwurf

Fehlerdatensätze sollen zusätzliche Informationen bereitzustellen, die nicht in Ausnahmen verfügbar ist, und gleichzeitig sicherstellen, dass die kombinierte Informationen in jedem Fehlerdatensatz eindeutig ist. Diese Eindeutigkeit ermöglicht die hostanwendung, die verschiedenen Teile des Error-Datensatzes zu überprüfen, damit die fehlerbedingung identifiziert können und die Aktion der Host muss auszuführen.

## <a name="interpreting-error-records"></a>Interpretieren von Datensätzen

Sie können verschiedene Teile des Error-Datensatzes zur Identifikation des Fehlers überprüfen. Diese Komponenten umfassen Folgendes:

- Die Fehlerkategorie

- Die Fehlerausnahme

- Der Bezeichner für den vollqualifizierten Fehler (FQID)

- Weitere Informationen

### <a name="the-error-category"></a>Die Fehlerkategorie

Die Fehlerkategorie des Error-Datensatzes ist eine der vordefinierten Konstanten gebotenen die [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) Enumeration. Diese Informationen sind verfügbar, über die [System.Management.Automation.ErrorRecord.CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) Eigenschaft der [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) Objekt.

Das-Cmdlet kann die Kategorien CloseError, OpenError, Ungültiger Typ, ReadError und WriteError und andere Fehlerkategorien angeben. Die hostanwendung kann die Fehlerkategorie verwenden, um Gruppen von Fehlern zu erfassen.

### <a name="the-exception"></a>Die Ausnahme

Die Ausnahme, die in der Error-Datensatz enthalten wird vom Cmdlet bereitgestellt und kann zugegriffen werden, über die [System.Management.Automation.ErrorRecord.Exception*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) Eigenschaft der [ System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) Objekt.

Hosten von Anwendungen können die `is` Schlüsselwort, um anzugeben, dass die Ausnahme einer bestimmten Klasse oder einer abgeleiteten Klasse ist. Es ist besser,-Branch in den Typ der Ausnahme, wie im folgenden Beispiel gezeigt.

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

Auf diese Weise fangen Sie die abgeleiteten Klassen. Es gibt jedoch Probleme, wenn die Ausnahme deserialisiert wird.

### <a name="the-fqid"></a>Die FQID

Die FQID ist die spezifischste Informationen, die Sie verwenden können, um den Fehler zu ermitteln. Es ist eine Zeichenfolge, die enthält ein Cmdlet definierten Bezeichner, der Name des der Cmdlet-Klasse, und die Quelle, die der Fehler gemeldet. Ein Fehlerdatensatz entspricht im Allgemeinen einen Ereignisdatensatz von einem Windows-Ereignisprotokoll. Die FQID entspricht das folgende Tupel, die die Klasse des Datensatzes identifiziert: (*Protokollname*, *Quelle*, *Ereignis-ID*).

Die FQID dient als einzelne Zeichenfolge überprüft werden soll. Es gibt jedoch Fälle in denen der Fehler-ID von der hostanwendung analysiert werden soll. Im folgende Beispiel wird eine wohlgeformte vollqualifizierten Fehler-ID an.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

Im vorherigen Beispiel ist das erste Token die Fehler-ID, gefolgt von den Namen der Cmdlet-Klasse. Fehler-ID kann ein einzelnes Token, oder es kann sein, einen Punkt getrennte Bezeichner, der mit der Untersuchung des Bezeichners Verzweigungen ermöglicht. Verwenden Sie nicht leer- oder Interpunktionszeichen in der fehlerbezeichner. Es ist besonders wichtig, nicht um ein Komma verwenden; ein Komma wird von Windows PowerShell verwendet, um den Bezeichner und den Cmdlet-Klassennamen zu trennen.

### <a name="other-information"></a>Weitere Informationen

Die [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) Objekt gewährleistet außerdem Informationen, die die Umgebung zu beschreiben, in dem der Fehler aufgetreten ist. Diese Informationen umfassen Elemente wie z. B. Fehlerdetails und Informationen zum Aufruf der Zielobjekt, das beim Auftreten des Fehlers verarbeitet wurde. Obwohl diese Informationen an die hostanwendung sein kann, wird sie nicht in der Regel verwendet, den Fehler zu ermitteln. Diese Informationen sind über die folgenden Eigenschaften verfügbar:

[System.Management.Automation.ErrorRecord.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System.Management.Automation.ErrorRecord.InvocationInfo](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System.Management.Automation.ErrorRecord.TargetObject](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[Hinzufügen von nicht endenden Fehlerberichte an Ihr Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell-Fehlerberichterstattung](./error-reporting-concepts.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
