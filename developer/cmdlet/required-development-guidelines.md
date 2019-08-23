---
title: Erforderliche Entwicklungs Richtlinien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: e68e43a91f9139e8d3dc636b5740121515aab2e6
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986676"
---
# <a name="required-development-guidelines"></a>Erforderliche Entwicklungsrichtlinien

Die folgenden Richtlinien müssen befolgt werden, wenn Sie die Cmdlets schreiben. Sie sind in Richtlinien zum Entwerfen von Cmdlets und Richtlinien zum Schreiben des Cmdlet-Codes unterteilt. Wenn Sie diese Richtlinien nicht befolgen, können Ihre Cmdlets fehlschlagen, und die Benutzer haben möglicherweise eine schlechte Benutzer Leistung, wenn Sie Ihre Cmdlets verwenden.

## <a name="in-this-topic"></a>In diesem Thema

### <a name="design-guidelines"></a>Entwurfs Richtlinien

- [Nur genehmigte Verben verwenden (RD01)](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Cmdlet-Namen: Zeichen, die nicht verwendet werden können (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [Parameternamen, die nicht verwendet werden können (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [Unterstützung von Bestätigungs Anforderungen (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Unterstützung des Force-Parameters für interaktive Sitzungen (RD05)](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [Dokument Ausgabe Objekte (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>Code Richtlinien

- [Ableiten von Cmdlets oder PSCmdlet-Klassen (RC01)](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Angeben des Cmdlet-Attributs (RC02)](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [Überschreiben einer Eingabe Verarbeitungsmethode (RC03)](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [Angeben des OutputType-Attributs (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [Handles für Ausgabe Objekte nicht beibehalten (RC05)](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [Fehler robuster behandeln (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Verwenden eines Windows PowerShell-Moduls zum Bereitstellen von Cmdlets (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>Entwurfs Richtlinien

Beim Entwerfen von Cmdlets müssen die folgenden Richtlinien befolgt werden, um eine konsistente Benutzer Darstellung zwischen der Verwendung ihrer Cmdlets und anderer Cmdlets sicherzustellen. Wenn Sie eine Entwurfsrichtlinie finden, die für Ihre Situation gilt, sollten Sie sich die Code Richtlinien für ähnliche Richtlinien ansehen.

### <a name="use-only-approved-verbs-rd01"></a>Nur genehmigte Verben verwenden (RD01)

Das im Cmdlet-Attribut angegebene Verb muss aus dem erkannten Satz von Verben stammen, die von Windows PowerShell bereitgestellt werden. Es darf sich nicht um eines der unzulässigen Synonyme handeln. Verwenden Sie die Konstanten Zeichen folgen, die durch die folgenden Enumerationen definiert werden, um Cmdlet-Verben anzugeben:

- [System. Management. Automation. verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System. Management. Automation. verbscommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System. Management. Automation. verbsdata](/dotnet/api/System.Management.Automation.VerbsData)

- [System. Management. Automation. verbsdiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System. Management. Automation. verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System. Management. Automation. verbssecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System. Management. Automation. verbsother](/dotnet/api/System.Management.Automation.VerbsOther)

Weitere Informationen zu den genehmigten Verb Namen finden Sie unter [Cmdlet-Verben](./approved-verbs-for-windows-powershell-commands.md).

Benutzer benötigen einen Satz erkennbarer und erwarteter Cmdlet-Namen. Verwenden Sie das geeignete Verb, damit der Benutzer eine schnelle Bewertung der Funktionsweise eines Cmdlets durchführen und die Funktionen des Systems problemlos ermitteln kann. Beispielsweise wird mit dem folgenden Befehlszeilen Befehl eine Liste aller Befehle auf dem System abgerufen, deren Namen mit "Start" beginnen: `get-command start-*`. Verwenden Sie die Substantiven in ihren Cmdlets, um ihre Cmdlets von anderen Cmdlets zu unterscheiden. Das Substantiv gibt die Ressource an, für die der Vorgang ausgeführt wird. Der Vorgang selbst wird durch das Verb dargestellt.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Cmdlet-Namen: Zeichen, die nicht verwendet werden können (RD02)

Wenn Sie Cmdlets benennen, dürfen Sie keines der folgenden Sonderzeichen verwenden.

|Zeichen|Name|
|---------------|----------|
|#|Nummern Zeichen|
|,|Komma|
|()|Klammern|
|{}|Klammern|
|[]|angegeben|
|&|kaufmännisches und|
|-|Bindestrich **Hinweis:**  Der Bindestrich kann verwendet werden, um das Verb vom Substantiv zu trennen, aber es kann nicht innerhalb des Substantiv oder innerhalb des Verbs verwendet werden.|
|/|Schrägstrich|
|\\| umgekehrter Schrägstrich|
|$|Dollarzeichen|
|^|Einfügemarke|
|;|Semikolon|
|:|Doppelpunkt|
|"|doppeltes Anführungszeichen|
|'|einfache Anführungszeichen|
|<>|spitzen Klammern|
|&#124;|senkrechter Strich|
|?|Fragezeichen|
|@|at-Zeichen|
|`|Backtick (großes Akzent)|
|*|gekennzeichneten|
|%|Prozentzeichen|
|+|Pluszeichen|
|=|Gleichheitszeichen|
|~|Tilde|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>Parameternamen, die nicht verwendet werden können (RD03)

Windows PowerShell bietet einen gemeinsamen Satz von Parametern für alle Cmdlets sowie zusätzliche Parameter, die in bestimmten Situationen hinzugefügt werden. Beim Entwerfen Ihrer eigenen Cmdlets können Sie die folgenden Namen nicht verwenden: Confirm, Debug, ErrorAction, ErrorVariable, OutBuffer, OutVariable, WarningAction, WarningVariable, WhatIf, UseTransaction und Verbose. Weitere Informationen zu diesen Parametern finden Sie unter [Allgemeine Parameternamen](./common-parameter-names.md).

### <a name="support-confirmation-requests-rd04"></a>Unterstützung von Bestätigungs Anforderungen (RD04)

Für Cmdlets, die einen Vorgang ausführen, der das System ändert, sollten Sie die [System. Management. Automation. Cmdlet. Schulter dprocess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode zum Anfordern der Bestätigung und in besonderen Fällen das [ System. Management. Automation. Cmdlet. schuldcontinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Methode. (Die [System. Management. Automation. Cmdlet. schuldcontinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Methode sollte nur aufgerufen werden, nachdem die [System. Management. Automation. Cmdlet. Schulter Name Process *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode aufgerufen wurde.)

Um diese Aufrufe vorzunehmen, muss das Cmdlet angeben, dass es Bestätigungs Anforderungen unterstützt `SupportsShouldProcess` , indem das-Schlüsselwort des Cmdlet-Attributs festgelegt wird. Weitere Informationen zum Festlegen dieses Attributs finden [Sie unter Cmdlet-Attribut Deklaration](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Wenn das Cmdlet-Attribut der Cmdlet-Klasse anzeigt, dass das Cmdlet Aufrufe der [System. Management. Automation. Cmdlet. Schulter dprocess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode unterstützt, und das Cmdlet den Aufruf von [nicht durchführen kann. System. Management. Automation. Cmdlet. schuldprocess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode, kann der Benutzer das System unerwartet ändern.

Verwenden Sie die [System. Management. Automation. Cmdlet. Schulter dprocess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode für jede System Änderung. Eine Benutzereinstellung und der `WhatIf` Parameter steuern die [System. Management. Automation. Cmdlet. schuldprocess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode. Im Gegensatz dazu führt der [System. Management. Automation. Cmdlet. schuldcontinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Befehl eine zusätzliche Überprüfung auf potenziell gefährliche Änderungen aus. Diese Methode wird nicht von einer Benutzereinstellung oder dem `WhatIf` -Parameter gesteuert. Wenn das Cmdlet die [System. Management. Automation. Cmdlet. tiondcontinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Methode aufruft, muss es über `Force` einen Parameter verfügen, der die Aufrufe an diese beiden Methoden umgeht und den Vorgang fortsetzt. Dies ist wichtig, da das Cmdlet in nicht interaktiven Skripts und Hosts verwendet werden kann.

Wenn die Cmdlets diese Aufrufe unterstützen, kann der Benutzer bestimmen, ob die Aktion tatsächlich ausgeführt werden soll. Beispielsweise ruft das Cmdlet " [Stopp-Process](/powershell/module/microsoft.powershell.management/stop-process) " die [System. Management. Automation. Cmdlet. tiondcontinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Methode auf, bevor es eine Reihe kritischer Prozesse stoppt, einschließlich der System-, Winlogon-und spoolsv-Prozesse.

Weitere Informationen zur Unterstützung dieser Methoden finden Sie unter [Anfordern einer Bestätigung](./requesting-confirmation-from-cmdlets.md).

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Unterstützung des Force-Parameters für interaktive Sitzungen (RD05)

Wenn das Cmdlet interaktiv verwendet wird, stellen Sie immer einen Force-Parameter bereit, um die interaktiven Aktionen außer Kraft zu setzen, z. b. Eingabe Aufforderungen oder Lesen von Eingabezeilen. Dies ist wichtig, da das Cmdlet in nicht interaktiven Skripts und Hosts verwendet werden kann. Die folgenden Methoden können von einem interaktiven Host implementiert werden.

- [System. Management. Automation. Host. pshostuserinterface. prompt *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System. Management. Automation. Host. pshostuserinterface. promptforchoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System. Management. Automation. Host. ihostuisupportsmultiplechoiceselection. promptforchoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System. Management. Automation. Host. pshostuserinterface. promptforcredential *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System. Management. Automation. Host. pshostuserinterface. read line *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System. Management. Automation. Host. pshostuserinterface. Read lineassecurestring *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>Dokument Ausgabe Objekte (RD06)

Windows PowerShell verwendet die Objekte, die in die Pipeline geschrieben werden. Damit Benutzer die von jedem Cmdlet zurückgegebenen Objekte nutzen können, müssen Sie die zurückgegebenen Objekte dokumentieren, und Sie müssen dokumentieren, wofür die Member dieser zurückgegebenen Objekte verwendet werden.

## <a name="code-guidelines"></a>Code Richtlinien

Die folgenden Richtlinien müssen befolgt werden, wenn der Cmdlet-Code geschrieben wird. Wenn Sie eine Code Richtlinie finden, die für Ihre Situation gilt, achten Sie darauf, dass Sie die Entwurfs Richtlinien für ähnliche Richtlinien untersuchen.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Ableiten von Cmdlets oder PSCmdlet-Klassen (RC01)

Ein Cmdlet muss entweder von der [System. Management. Automation. Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) -oder der [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) -Basisklasse abgeleitet werden. Cmdlets, die von der [System. Management. Automation. Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) -Klasse abgeleitet sind, sind nicht von der Windows PowerShell-Laufzeit abhängig. Sie können direkt von jeder beliebigen Microsoft .NET Framework-Sprache aufgerufen werden. Cmdlets, die von der [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) -Klasse abgeleitet sind, hängen von der Windows PowerShell-Laufzeit ab. Aus diesem Grund werden Sie innerhalb eines Runspace ausgeführt.

Alle von Ihnen implementierten Cmdlet-Klassen müssen öffentliche Klassen sein. Weitere Informationen zu diesen Cmdlet-Klassen finden Sie in der [Cmdlet-Übersicht](./cmdlet-overview.md).

### <a name="specify-the-cmdlet-attribute-rc02"></a>Angeben des Cmdlet-Attributs (RC02)

Damit ein Cmdlet von Windows PowerShell erkannt wird, muss die .NET Framework Klasse mit dem Cmdlet-Attribut versehen werden. Dieses Attribut gibt die folgenden Features des Cmdlets an.

- Das Verb-und-Substantiv-Paar, das das Cmdlet identifiziert.

- Der Standardparameter Satz, der verwendet wird, wenn mehrere Parametersätze angegeben werden. Der Standardparameter Satz wird verwendet, wenn Windows PowerShell nicht über genügend Informationen verfügt, um zu bestimmen, welcher Parameter verwendet werden soll.

- Gibt an, ob das Cmdlet Aufrufe der [System. Management. Automation. Cmdlet. Schulter dprocess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode unterstützt. Diese Methode zeigt dem Benutzer eine Bestätigungsmeldung an, bevor das Cmdlet eine Änderung am System vornimmt. Weitere Informationen zur Vorgehensweise bei Bestätigungs Anforderungen finden Sie unter [Anfordern einer Bestätigung](./requesting-confirmation-from-cmdlets.md).

- Geben Sie die Auswirkungs Stufe (oder den Schweregrad) der Aktion an, die der Bestätigungsmeldung zugeordnet ist. In den meisten Fällen sollte der Standardwert Mittel verwendet werden. Weitere Informationen darüber, wie sich die Auswirkung auf die Bestätigungs Anforderungen auswirkt, die dem Benutzer angezeigt werden, finden Sie unter [Anfordern einer Bestätigung](./requesting-confirmation-from-cmdlets.md).

Weitere Informationen zum Deklarieren des Cmdlet-Attributs finden Sie unter [CmdletAttribute-Deklaration](./cmdlet-attribute-declaration.md).

### <a name="override-an-input-processing-method-rc03"></a>Überschreiben einer Eingabe Verarbeitungsmethode (RC03)

Damit das Cmdlet an der Windows PowerShell-Umgebung teilnimmt, muss es mindestens eine der folgenden *Eingabe Verarbeitungsmethoden*überschreiben.

[System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) diese Methode wird einmal aufgerufen und wird verwendet, um Vorverarbeitungs Funktionen bereitzustellen.

[System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) diese Methode wird mehrmals aufgerufen und dient zur Bereitstellung von Daten Satz Funktionen.

[System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) diese Methode wird einmal aufgerufen, und Sie wird verwendet, um nach Verarbeitungsfunktionen bereitzustellen.

### <a name="specify-the-outputtype-attribute-rc04"></a>Angeben des OutputType-Attributs (RC04)

Das OutputType-Attribut (eingeführt in Windows PowerShell 2,0) gibt den .NET Framework Typ an, den das Cmdlet an die Pipeline zurückgibt. Indem Sie den Ausgabetyp ihrer Cmdlets angeben, machen Sie fest, dass die von Ihrem Cmdlet zurückgegebenen Objekte durch andere Cmdlets leichter erkennbar sind. Weitere Informationen zum zieren der Cmdlet-Klasse mit diesem Attribut finden Sie unter [OutputType-Attribut Deklaration](./outputtype-attribute-declaration.md).

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>Handles für Ausgabe Objekte nicht beibehalten (RC05)

Ihr Cmdlet sollte keine Handles an den Objekten aufbewahren, die an die [System. Management. Automation. Cmdlet. Write Team Object *](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) -Methode übergeben werden. Diese Objekte werden an das nächste Cmdlet in der Pipeline übergeben, oder Sie werden von einem Skript verwendet. Wenn Sie die Handles für die Objekte beibehalten, werden die einzelnen Objekte von zwei Entitäten übernommen, was zu Fehlern führt.

### <a name="handle-errors-robustly-rc06"></a>Fehler robuster behandeln (RC06)

Eine Verwaltungs Umgebung erkennt von Natur aus wichtige Änderungen am System, das Sie verwalten. Daher ist es wichtig, dass Cmdlets Fehler ordnungsgemäß behandeln. Weitere Informationen zu Fehler Datensätzen finden Sie unter [Windows PowerShell-Fehlerberichterstattung](./error-reporting-concepts.md).

- Wenn ein Fehler verhindert, dass ein Cmdlet die Verarbeitung von weiteren Datensätzen fortsetzt, ist dies ein Abbruch Fehler. Das Cmdlet muss die [System. Management. Automation. Cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) -Methode, die auf ein [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -Objekt verweist, aufruft. Wenn eine Ausnahme vom Cmdlet nicht abgefangen wird, löst die Windows PowerShell-Laufzeit selbst einen Abbruch Fehler aus, der weniger Informationen enthält.

- Bei einem Fehler ohne Abbruch, bei dem der Vorgang für den nächsten Datensatz, der aus der Pipeline stammt (z. b. ein von einem anderen Prozess generierender Datensatz), nicht beendet wird, muss das Cmdlet die [System. Management. Automation. Cmdlet. Write error *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode aufrufen, die verweist auf ein [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -Objekt. Ein Beispiel für einen Fehler ohne Abbruch ist der Fehler, der auftritt, wenn ein bestimmter Prozess nicht beendet wird. Durch Aufrufen der [System. Management. Automation. Cmdlet. Write-error *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode kann der Benutzer die angeforderten Aktionen konsistent ausführen und die Informationen für bestimmte Aktionen beibehalten, die fehlschlagen. Ihr Cmdlet sollte jeden Datensatz so unabhängig wie möglich verarbeiten.

- Das [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -Objekt, auf das von der [System. Management. Automation. Cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) -und der [System. Management. Automation. Cmdlet. Write-error *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode verwiesen wird, erfordert ein Ausnahme im Kern. Befolgen Sie die Entwurfs Richtlinien für .NET Framework, wenn Sie die zu verwendende Ausnahme bestimmen. Wenn der Fehler semantisch identisch mit einer vorhandenen Ausnahme ist, verwenden Sie diese Ausnahme oder leiten Sie von dieser Ausnahme ab. Leiten Sie andernfalls eine neue Ausnahme-oder eine Ausnahme Hierarchie direkt vom [System. Exception](/dotnet/api/System.Exception) -Typ ab.

Ein [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -Objekt benötigt außerdem eine Fehler Kategorie, in der Fehler für den Benutzer gruppiert werden. Der Benutzer kann Fehler basierend auf der Kategorie anzeigen, indem er den Wert der `$ErrorView` Shellvariablen auf categoryview festlegt. Die möglichen Kategorien werden von der [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) -Enumeration definiert.

- Wenn ein Cmdlet einen neuen Thread erstellt und der Code, der in diesem Thread ausgeführt wird, eine nicht behandelte Ausnahme auslöst, wird der Fehler von Windows PowerShell nicht abgefangen, und der Prozess wird beendet.

- Wenn ein Objekt über Code in seinem Debuggen verfügt, der zu einer nicht behandelten Ausnahme führt, wird der Fehler von Windows PowerShell nicht abgefangen, und der Prozess wird beendet. Dies tritt auch auf, wenn ein Objektmethoden zum Verwerfen von Methoden aufruft, die zu einer nicht behandelten Ausnahme führen.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Verwenden eines Windows PowerShell-Moduls zum Bereitstellen von Cmdlets (RC07)

Erstellen Sie ein Windows PowerShell-Modul, um die Cmdlets zu verpacken und bereitzustellen. Die Unterstützung für Module wird in Windows PowerShell 2,0 eingeführt. Sie können die Assemblys, die ihre Cmdlet-Klassen enthalten, direkt als binäre Moduldateien verwenden (Dies ist sehr nützlich, wenn Sie die Cmdlets testen), oder Sie können ein Modul Manifest erstellen, das auf die Cmdlet-Assemblys verweist. (Sie können auch vorhandene Snap-in-Assemblys hinzufügen, wenn Sie Module verwenden.) Weitere Informationen zu Modulen finden Sie unter [Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Weitere Informationen

[Stark unterstützt Entwicklungs Richtlinien](./strongly-encouraged-development-guidelines.md)

[Leitlinien für die Beratung](./advisory-development-guidelines.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
