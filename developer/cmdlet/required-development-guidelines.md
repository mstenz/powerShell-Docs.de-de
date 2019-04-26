---
title: Richtlinien für die Entwicklung erforderlichen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: 3f6bcd2e4ef4d9c404b3a5deeaa9f25d3fa42ec1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067466"
---
# <a name="required-development-guidelines"></a>Erforderliche Entwicklungsrichtlinien

Wenn Sie Ihre Cmdlets schreiben, müssen die folgenden Richtlinien folgen. Sie werden in den Richtlinien zum Entwerfen von Cmdlets und Richtlinien zum Schreiben von Cmdlet-Code getrennt. Wenn Sie nicht diese Richtlinien befolgen, Ihre Cmdlets kann fehlschlagen, und Ihre Benutzer möglicherweise eine schlechte benutzererfahrung, wenn sie Ihre Cmdlets verwenden.

## <a name="in-this-topic"></a>In diesem Thema

### <a name="design-guidelines"></a>Richtlinien für den Entwurf

- [Ausschließliches Verwenden von genehmigten Verben (RD01)](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Cmdlet-Namen: Zeichen, die nicht verwendet werden können (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [Parameternamen, die nicht verwendet werden können (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [Supportanfragen Sie bei der Bestätigung (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Unterstützung von "Force"-Parameter für interaktive Sitzungen (RD05)](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [Ausgabe-Dokumentobjekte (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>Coderichtlinien

- [Leiten Sie von dem-Cmdlet oder PSCmdlet-Klassen (RC01)](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Geben Sie das Cmdlet-Attribut (RC02)](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [Überschreiben einer Eingabeverarbeitungsmethode (RC03)](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [Geben Sie das OutputType-Attribut (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [Behalten Sie nicht-Handles zu Ausgabeobjekten (RC05)](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [Behandeln von Fehlern robust (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Verwenden Sie ein Windows PowerShell-Modul, um Ihre Cmdlets (RC07) bereitstellen](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>Richtlinien für den Entwurf

Beim Entwerfen von Cmdlets, um sicherzustellen, dass eine konsistente benutzererfahrung zwischen der Verwendung, Ihre Cmdlets und andere Cmdlets, müssen die folgenden Richtlinien eingehalten werden. Wenn Sie eine designrichtlinie, die auf Ihren Fall zutrifft finden, achten Sie darauf, dass Sie betrachten, die Code-Richtlinien für ähnliche Richtlinien.

### <a name="use-only-approved-verbs-rd01"></a>Ausschließliches Verwenden von genehmigten Verben (RD01)

Das Verb in der Cmdlet-Attribut angegebene muss aus der bekannte Gruppe von Verben, die von Windows PowerShell bereitgestellte stammen. Es muss nicht von den unzulässigen Synonymen sein. Verwenden Sie die Konstanten Zeichenfolgen, die vom Cmdlet-Verbs an die folgenden Enumerationen definiert werden:

- [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

Weitere Informationen zu den genehmigtes Verb-Namen finden Sie unter [Cmdlet-Verbs](./approved-verbs-for-windows-powershell-commands.md).

Benutzer benötigen einen Satz von ermittelbar und erwartete Cmdlet-Namen. Verwenden Sie das entsprechende Verb, damit der Benutzer eine schnelle Bewertung, was ein Cmdlet bewirkt und leicht erkennen, das die Funktionen des Systems vornehmen kann. Die folgende Befehlszeile ruft z. B. eine Liste aller Befehle ab, auf dem System, deren Namen mit "Start beginnen": `get-command start-*`. Verwenden Sie die Substantiven in Ihre Cmdlets, um Ihre Cmdlets von anderen Cmdlets unterscheiden. Das Nomen "" gibt an, die Ressource, auf der der Vorgang ausgeführt wird. Der Vorgang selbst wird durch das Verb repräsentiert.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Cmdlet-Namen: Zeichen, die nicht verwendet werden können (RD02)

Wenn Sie Cmdlets Namen verwenden, verwenden Sie eine der folgenden Sonderzeichen bestehen nicht.

|Zeichen|Name|
|---------------|----------|
|#|Nummernzeichen|
|,|Durch Kommas|
|()|Klammern|
|{}|geschweifte Klammern|
|[]|eckige Klammern|
|&|kaufmännisches und-Zeichen|
|-|Bindestrich **beachten:**  Der Bindestrich kann verwendet werden, um das aus dem Substantiv-Verb zu trennen, aber nicht in die das Nomen oder in das Verb verwendet werden.|
|/|Schrägstrich|
|\|backslash|
|$|Dollarzeichen|
|^|caret|
|;|Durch Semikolons|
|:|Doppelpunkt|
|"|Doppeltes Anführungszeichen|
|'|einfaches Anführungszeichen|
|<>|Spitze Klammern|
|&#124;|senkrechter Strich|
|?|Fragezeichen|
|@|at-Zeichen|
|"| Sichern Tick (Graviszeichen)|
|*|Sternchen|
|%|Prozentzeichen|
|+|Pluszeichen (+)|
|=|Gleichheitszeichen|
|~|Tilde|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>Parameternamen, die nicht verwendet werden können (RD03)

Windows PowerShell bietet einem gemeinsamen Satz an, einen Parameter für alle Cmdlets sowie zusätzliche Parameter, die in bestimmten Situationen hinzugefügt werden. Beim Entwerfen eigener Cmdlets können Sie die folgenden Namen keine: Vergewissern Sie sich, Debug, ErrorAction, ErrorVariable, OutVariable OutBuffer, -WarningAction, WarningVariable, "WhatIf", UseTransaction, und ausführlich. Weitere Informationen zu diesen Parametern finden Sie unter [allgemeine Parameternamen](./common-parameter-names.md).

### <a name="support-confirmation-requests-rd04"></a>Supportanfragen Sie bei der Bestätigung (RD04)

Für Cmdlets, die einen Vorgang auszuführen, die das System geändert wird, rufen sie die [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Methode, um die Bestätigung anfordern, und rufen Sie in besonderen Fällen die [ System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methode. (Die [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methode sollte aufgerufen werden, erst nach der [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Methode wird aufgerufen.)

Diese Aufrufe mit dem Cmdlet muss angeben, dass sie die Anforderungen der Bestätigung durch Festlegen von unterstützt die `SupportsShouldProcess` Schlüsselwort mit dem Cmdlet-Attribut. Weitere Informationen zum Festlegen dieses Attributs finden Sie unter [Cmdlet Attributdeklaration](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Wenn von der Cmdlet-Klasse die Cmdlet-Attribut gibt an, dass das Cmdlet Aufrufe unterstützt die [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode, und das Cmdlet ein Fehler auftritt, für den Aufruf an die [ System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode, konnte der Benutzer des Systems unerwartet geändert.

Verwenden der [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode für jede System-Änderung. Eine benutzereinstellung und `WhatIf` parametersteuerung der [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Methode. Im Gegensatz dazu die [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Aufruf führt eine zusätzliche Überprüfung auf potenziell gefährliche Änderungen. Diese Methode wird nicht durch alle benutzereinstellung gesteuert oder `WhatIf` Parameter. Wenn Ihr Cmdlet Ruft die [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Methode, sie müssen eine `Force` -Parameter, der die Aufrufe an diese zwei Methoden umgangen und, die der Vorgang wird fortgesetzt. Dies ist wichtig, da Ihr Cmdlet in nicht-interaktive Skripts und -Hosts verwendet werden können.

Wenn Ihre Cmdlets diese Aufrufe unterstützt, kann der Benutzer bestimmen, ob die Aktion tatsächlich durchgeführt werden soll. Z. B. die [Stop-Process](/powershell/module/microsoft.powershell.management/stop-process) Cmdlet Ruft die [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Methode auf, bevor es eine Reihe von wichtigen Prozessen, einschließlich des Systems, Windows-Anmeldung, beendet und Spoolsv verarbeitet.

Weitere Informationen zur Unterstützung dieser Methoden finden Sie unter [Bestätigung anfordern](./requesting-confirmation-from-cmdlets.md).

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Unterstützung von "Force"-Parameter für interaktive Sitzungen (RD05)

Wenn Ihr Cmdlet interaktiv verwendet wird, immer Bereitstellen eines Force-Parameters, um die interaktive Aktionen, z. B. eingabeaufforderungen oder lesen die Zeilen der Eingabe überschreiben). Dies ist wichtig, da Ihr Cmdlet in nicht-interaktive Skripts und -Hosts verwendet werden können. Die folgenden Methoden können von einem interaktiven Host implementiert werden.

- [System.Management.Automation.Host.PSHostUserInterface.Prompt*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection.PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForCredential*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLine*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLineAsSecureString*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>Ausgabe-Dokumentobjekte (RD06)

Windows PowerShell verwendet die Objekte, die an die Pipeline geschrieben werden. Damit Benutzer die Objekte nutzen, die von jedem Cmdlet zurückgegeben werden, müssen Sie dokumentieren, die Objekte, die zurückgegeben werden, und müssen Sie dokumentieren, was die Mitglieder der zurückgegebenen Objekte für verwendet werden.

## <a name="code-guidelines"></a>Coderichtlinien

Beim Schreiben von Cmdlet-Code, müssen die folgenden Richtlinien eingehalten werden. Wenn Sie eine Richtlinie Code, die auf Ihren Fall zutrifft finden, achten Sie darauf, dass Sie die Entwurfsrichtlinien für ähnliche Richtlinien ansehen.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Leiten Sie von dem-Cmdlet oder PSCmdlet-Klassen (RC01)

Ein Cmdlet muss abgeleitet werden, entweder die [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) oder [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) Basisklasse. Cmdlets, die Ableitung der [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) Klasse hängen nicht von der Windows PowerShell-Laufzeit. Sie können direkt aus einer beliebigen Microsoft .NET Framework-Sprache aufgerufen werden. Cmdlets, die Ableitung der [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) Klasse hängt von der Windows PowerShell-Laufzeit. Führen Sie sie in einem Runspace.

Alle Cmdlet-Klassen, die Sie implementieren, müssen es sich um öffentliche Klassen sein. Weitere Informationen zu diesen Cmdlets-Klassen finden Sie unter [Übersicht über Cmdlets](./cmdlet-overview.md).

### <a name="specify-the-cmdlet-attribute-rc02"></a>Geben Sie das Cmdlet-Attribut (RC02)

Für das Cmdlet von Windows PowerShell erkannt werden muss die .NET Framework-Klasse mit dem Cmdlet-Attribut versehen werden. Dieses Attribut gibt an, die folgenden Features des-Cmdlets.

- Der Verb-Substantiv-Paar, die das Cmdlet bezeichnet.

- Der Satz der Standard-Parameter, der verwendet wird, wenn mehrere Parametersätze angegeben werden. Der Standardsatz der Parameter wird verwendet, wenn Windows PowerShell nicht, dass genügend Informationen verfügt, um zu bestimmen, welcher Parametersatz um zu verwenden.

- Gibt an, ob das Cmdlet Aufrufe unterstützt die [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Methode. Diese Methode zeigt eine bestätigungsmeldung an den Benutzer, bevor das Cmdlet eine Änderung an das System ausführt. Weitere Informationen dazu, wie die Bestätigung angefordert werden, finden Sie unter [Bestätigung anfordern](./requesting-confirmation-from-cmdlets.md).

- Geben Sie an das Impact-Level (oder Schweregrad) der Aktion zugeordnete die bestätigungsmeldung angezeigt. In den meisten Fällen sollte der Standardwert des Mediums verwendet werden. Weitere Informationen dazu, wie das Impact-Level die Bestätigung Anforderungen auswirkt, die dem Benutzer angezeigt werden, finden Sie unter [Bestätigung anfordern](./requesting-confirmation-from-cmdlets.md).

Weitere Informationen dazu, wie Sie die Cmdlet-Attribut zu deklarieren, finden Sie unter [CmdletAttribute-Deklaration](./cmdlet-attribute-declaration.md).

### <a name="override-an-input-processing-method-rc03"></a>Überschreiben einer Eingabeverarbeitungsmethode (RC03)

Für das Cmdlet zur Teilnahme an der Windows PowerShell-Umgebung, müssen sie mindestens eine der folgenden überschreiben *Methoden zum Verarbeiten von Eingabe*.

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) diese Methode wird einmal aufgerufen, und es wird verwendet, um die vorverarbeitung Funktionalität bereitzustellen.

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) diese Methode mehrmals aufgerufen wird, und es wird verwendet, um von Datensätzen Funktionalität bereitzustellen.

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) diese Methode wird einmal aufgerufen, und es wird verwendet, um die Nachbearbeitung Funktionalität bereitzustellen.

### <a name="specify-the-outputtype-attribute-rc04"></a>Geben Sie das OutputType-Attribut (RC04)

Die OutputType-Attribut (eingeführt in Windows PowerShell 2.0) gibt an, die .NET Framework-Typ, den Ihr Cmdlet gibt, an die Pipeline zurück. Durch Angabe des Ausgabetyps des Ihre Cmdlets stellen Sie die zurückgegebenen Objekte durch Ihr Cmdlet Auffindbarkeit von anderen Cmdlets. Weitere Informationen zu den Cmdlet-Klasse mit diesem Attribut versehen, finden Sie unter [OutputType Attributdeklaration](./outputtype-attribute-declaration.md).

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>Behalten Sie nicht-Handles zu Ausgabeobjekten (RC05)

Ihr Cmdlet sollten alle Handles an den Objekten, die übergeben werden, nicht beibehalten der [System.Management.Automation.Cmdlet.WriteObject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) Methode. Diese Objekte an das nächste Cmdlet in der Pipeline übergeben werden, oder sie werden von einem Skript verwendet. Wenn Sie die Ziehpunkte an den Objekten beibehalten, werden zwei Entitäten jedes Objekt besitzen, die Fehler verursacht.

### <a name="handle-errors-robustly-rc06"></a>Behandeln von Fehlern robust (RC06)

Eine verwaltungsumgebung ist grundsätzlich erkennt und wird auf dem System, das Sie verwalten. Aus diesem Grund ist es wichtig, dass Cmdlets Fehler ordnungsgemäß behandeln. Weitere Informationen zu Datensätzen, finden Sie unter [Windows PowerShell-Fehlerberichterstattung](./error-reporting-concepts.md).

- Wenn ein Fehler ein Cmdlet verhindert, nicht fortgesetzt werden kann, um weitere Datensätze zu verarbeiten, ist es ein Fehler mit Abbruch. Das-Cmdlet aufrufen, muss die [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) -Methode, die verweist auf eine [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) Objekt. Wenn eine Ausnahme vom Cmdlet nicht abgefangen wird, löst die Windows PowerShell-Laufzeit selbst einen Fehler mit Abbruch, der weniger Informationen enthält.

- Für einen Fehler ohne Abbruch, die nicht-Vorgang für den nächsten beendet wird Datensatz, der von der Pipeline (z. B. in ein Datensatz erstellt, die von einem anderen Prozess), mit dem Cmdlet stammt aufrufen, muss die [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode, die verweist auf eine [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) Objekt. Ein Beispiel für einen Fehler ohne Abbruch wird der Fehler, der auftritt, wenn ein bestimmter Prozess nicht beenden. Aufrufen der [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) Methode ermöglicht dem Benutzer, die angeforderten Aktionen konsistent funktionieren und die Informationen für bestimmte Aktionen beibehalten werden sollen, bei denen bei. Jeder Datensatz sollte Ihr Cmdlet so unabhängig wie möglich verarbeiten können.

- Die [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -Objekt, das verweist die [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) und [ System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) Methoden erfordert eine Ausnahme im Kern. Führen Sie die .NET Framework-Entwurfsrichtlinien, wenn Sie feststellen, dass die Ausnahme zu verwenden. Wenn der Fehler semantisch identisch mit einer vorhandenen Ausnahme ist, verwenden Sie diese Ausnahme aus, oder leiten Sie von dieser Ausnahme. Andernfalls abgeleitet werden, eine neue Ausnahme oder ausnahmenhierarchie direkt aus der ["System.Exception"](/dotnet/api/System.Exception) Typ.

Ein [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -Objekt erfordert ebenfalls eine Fehlerkategorie, die Fehler für den Benutzer gruppiert. Der Benutzer kann basierend auf der Kategorie durch Festlegen des Werts der Fehler anzeigen der `$ErrorView` Shellvariable, CategoryView. Die möglichen Kategorien definieren, indem die [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) Enumeration.

- Wenn ein Cmdlet einen neuen Thread erstellt, und wenn der Code, der in diesem Thread ausgeführt wird, eine nicht behandelte Ausnahme auslöst, wird Windows PowerShell wird den Fehler nicht abgefangen und wird den Prozess beendet.

- Wenn ein Objekt Code in seinem Destruktor, die eine nicht behandelte Ausnahme auslöst verfügt, wird Windows PowerShell fängt keine Fehler und der Prozess beendet wird. Dies tritt auf, wenn ein Objekt Dispose-Methoden aufruft, die dazu führen, eine nicht behandelte Ausnahme dass.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Verwenden Sie ein Windows PowerShell-Modul, um Ihre Cmdlets (RC07) bereitstellen

Erstellen Sie ein Windows PowerShell-Modul zum Packen und Bereitstellen Ihrer Cmdlets. Unterstützung für Module ist in Windows PowerShell 2.0 eingeführt. Können Sie die Assemblys, die Cmdlet-Klassen direkt als binäre Moduldateien enthalten (Dies ist hilfreich beim Testen Ihre Cmdlets), oder erstellen kann ein modulmanifest, die auf die Cmdlet-Assemblys verweist. (Sie können auch vorhandene-Snap-in-Assemblys hinzufügen, wenn Sie Module verwenden.) Weitere Informationen zu Modulen finden Sie unter [Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Weitere Informationen

[Richtlinien für die Entwicklung von dringend empfohlen](./strongly-encouraged-development-guidelines.md)

[Richtlinien für die Advise-Entwicklung](./advisory-development-guidelines.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
