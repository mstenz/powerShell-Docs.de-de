---
title: Stark unterstützt Entwicklungs Richtlinien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: 0906d0d37c66b8c1538a0b2e9e0f1ff2fba12ac0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369339"
---
# <a name="strongly-encouraged-development-guidelines"></a>Ausdrücklich empfohlene Entwicklungsrichtlinien

In diesem Abschnitt werden Richtlinien beschrieben, die Sie beim Schreiben von Cmdlets befolgen sollten. Sie sind in Richtlinien zum Entwerfen von Cmdlets und Richtlinien zum Schreiben des Cmdlet-Codes unterteilt. Möglicherweise stellen Sie fest, dass diese Richtlinien für jedes Szenario nicht anwendbar sind. Wenn Sie jedoch angewendet werden und diese Richtlinien nicht befolgt werden, können Ihre Benutzer bei der Verwendung ihrer Cmdlets eine schlechte Benutzer Leistung aufweisen.

## <a name="design-guidelines"></a>Entwurfsrichtlinien

- [Verwenden eines bestimmten Substantivs für einen Cmdlet-Namen (SD01)](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [Verwenden der Pascal-Schreibweise für Cmdlet-Namen (SD02)](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [Entwurfs Richtlinien für Parameter (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [Bereitstellen von Feedback für den Benutzer (SD04)](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [Erstellen einer Cmdlet-Hilfedatei (SD05)](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>Code Richtlinien

- [Codierungs Parameter (SC01)](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [Unterstützen wohl definierter Pipeline Eingaben (SC02)](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [Schreiben einzelner Datensätze in die Pipeline (Sc03)](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [Cmdlets ohne Berücksichtigung der Groß-/Kleinschreibung und Groß-/Kleinschreibung (Sc04)](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>Entwurfsrichtlinien

Beachten Sie beim Entwerfen von Cmdlets die folgenden Richtlinien, um eine konsistente Benutzer Darstellung zwischen der Verwendung ihrer Cmdlets und anderer Cmdlets sicherzustellen. Wenn Sie eine Entwurfsrichtlinie finden, die für Ihre Situation gilt, sollten Sie sich die Code Richtlinien für ähnliche Richtlinien ansehen.

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>Verwenden eines bestimmten Substantivs für einen Cmdlet-Namen (SD01)

Nomen, die in der Cmdlet-Benennung verwendet werden, müssen sehr spezifisch sein, damit der Benutzer ihre Cmdlets ermitteln kann. Stellen Sie eine gekürzte Version des Produkt namens als Präfix für generische Nomen wie "Server" dar. Wenn ein Substantiv z. b. auf einen Server verweist, auf dem eine Instanz von Microsoft SQL Server ausgeführt wird, verwenden Sie ein Substantiv wie z. b. "SQLServer". Die Kombination aus bestimmten Substantiven und der kurzen Liste genehmigter Verben ermöglicht dem Benutzer, die Funktionalität schnell zu erkennen und zu antizipieren und gleichzeitig Duplizierungen zwischen Cmdlet-Namen zu vermeiden.

Um die Benutzer Leistung zu verbessern, sollte das Substantiv, das Sie für einen Cmdlet-Namen auswählen, Singular sein. Verwenden Sie z. b. den Namen `Get-Process` anstelle von **Get-Processes**. Es empfiehlt sich, diese Regel für alle Cmdlet-Namen zu befolgen, auch wenn ein Cmdlet wahrscheinlich auf mehr als ein Element reagiert.

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>Verwenden der Pascal-Schreibweise für Cmdlet-Namen (SD02)

Verwenden Sie Pascal Case für Parameternamen. Dies bedeutet, dass der erste Buchstabe des Verbs und alle Begriffe, die im Substantiv verwendet werden, groß geschrieben werden. Beispiel: "`Clear-ItemProperty`“.

### <a name="parameter-design-guidelines-sd03"></a>Entwurfs Richtlinien für Parameter (SD03)

Ein Cmdlet benötigt Parameter, die die Daten empfangen, auf denen er ausgeführt werden muss, und Parameter, die Informationen angeben, die zum Bestimmen der Merkmale des Vorgangs verwendet werden. Ein Cmdlet kann z. b. über einen `Name` Parameter verfügen, der Daten aus der Pipeline empfängt, und das Cmdlet kann einen `Force` Parameter aufweisen, um anzugeben, dass das Cmdlet zum Ausführen des Vorgangs erzwungen werden kann. Es gibt keine Beschränkung für die Anzahl von Parametern, die von einem Cmdlet definiert werden können.

#### <a name="use-standard-parameter-names"></a>Standard Parameter Namen verwenden

Ihr Cmdlet sollte Standardparameter Namen verwenden, damit der Benutzer schnell ermitteln kann, was ein bestimmter Parameter bedeutet. Wenn ein spezifischeren Name erforderlich ist, verwenden Sie einen Standardparameter Namen, und geben Sie dann einen spezifischeren Namen als Alias an. Das `Get-Service`-Cmdlet hat z. b. einen Parameter mit einem generischen Namen (`Name`) und einem spezifischeren Alias (`ServiceName`). Beide Begriffe können zum Angeben des Parameters verwendet werden.

Weitere Informationen zu Parameternamen und deren Datentypen finden Sie unter [Cmdlet-Parameter Name und Funktions Richtlinien](./standard-cmdlet-parameter-names-and-types.md).

#### <a name="use-singular-parameter-names"></a>Verwenden von eindeutigen Parameter Namen

Vermeiden Sie die Verwendung von Plural Namen für Parameter, deren Wert ein einzelnes Element ist. Dies schließt Parameter ein, die Arrays oder Listen annehmen, da der Benutzer möglicherweise ein Array oder eine Liste mit nur einem Element bereitstellt.

Plural Parameternamen sollten nur in den Fällen verwendet werden, in denen der Wert des-Parameters immer ein Mehrfaches Elementwert ist. In diesen Fällen muss das Cmdlet überprüfen, ob mehrere Elemente bereitgestellt werden, und das Cmdlet sollte dem Benutzer eine Warnung anzeigen, wenn mehrere Elemente nicht bereitgestellt werden.

#### <a name="use-pascal-case-for-parameter-names"></a>In Pascal-Case für Parameter Namen verwenden

Verwenden Sie Pascal Case für Parameternamen. Dies bedeutet, dass der erste Buchstabe jedes Worts im Parameternamen, einschließlich des ersten Buchstabens, groß geschrieben werden soll. Beispielsweise verwendet der Parameter Name `ErrorAction` die richtige Groß-/Kleinschreibung. Die folgenden Parameternamen verwenden falsche Groß Schreibung:

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>Parameter, die eine Liste von Optionen annehmen

Es gibt zwei Möglichkeiten, einen Parameter zu erstellen, dessen Wert aus einer Reihe von Optionen ausgewählt werden kann.

- Definieren eines Enumerationstyps (oder Verwenden eines vorhandenen Enumerationstyps), der die gültigen Werte angibt. Verwenden Sie dann den Enumerationstyp, um einen Parameter dieses Typs zu erstellen.

- Fügen Sie das **validateset** -Attribut zur Parameter Deklaration hinzu. Weitere Informationen zu diesem Attribut finden Sie unter [validateset-Attribut Deklaration](./validateset-attribute-declaration.md).

#### <a name="use-standard-types-for-parameters"></a>Standard Typen für Parameter verwenden

Um die Konsistenz mit anderen Cmdlets sicherzustellen, verwenden Sie Standardtypen für Parameter, sofern dies möglich ist. Weitere Informationen zu den Typen, die für verschiedene Parameter verwendet werden sollten, finden Sie unter [Standard-Cmdlet-Parameternamen und-Typen](./standard-cmdlet-parameter-names-and-types.md). Dieses Thema enthält Links zu verschiedenen Themen, in denen die Namen und .NET Framework Typen für Gruppen von Standardparametern beschrieben werden, z. b. "Aktivitäts Parameter".

#### <a name="use-strongly-typed-net-framework-types"></a>Verwenden von stark typisierten .NET Framework Typen

Parameter sollten als .NET Framework Typen definiert werden, um eine bessere Parameter Validierung bereitzustellen. Beispielsweise sollten Parameter, die auf einen Wert aus einer Gruppe von Werten beschränkt sind, als Enumerationstyp definiert werden. Um einen Uniform Resource Identifier (URI)-Wert zu unterstützen, definieren Sie den Parameter als [System. Uri](/dotnet/api/System.Uri) -Typ. Vermeiden Sie grundlegende Zeichen folgen Parameter für alle außer frei Form Texteigenschaften.

#### <a name="use-consistent-parameter-types"></a>Konsistente Parameter Typen verwenden

Wenn derselbe Parameter von mehreren Cmdlets verwendet wird, verwenden Sie immer denselben Parametertyp.  Wenn der `Process`-Parameter z. b [. ein System. Int16](/dotnet/api/System.Int16) -Typ für ein Cmdlet ist, legen Sie den `Process`-Parameter für ein anderes Cmdlet nicht als [System. UInt16](/dotnet/api/System.UInt16) -Typ fest.

#### <a name="parameters-that-take-true-and-false"></a>Parameter mit "true" und "false"

Wenn der Parameter nur `true` und `false`annimmt, definieren Sie den Parameter als Type [System. Management. Automation. Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter). Ein Switch-Parameter wird als `true` behandelt, wenn er in einem Befehl angegeben wird. Wenn der-Parameter nicht in einem Befehl enthalten ist, betrachtet Windows PowerShell den Wert des-Parameters als `false`. Definieren Sie keine booleschen Parameter.

Wenn Ihr Parameter zwischen 3 Werten unterscheiden muss: $true, $false und "nicht angegeben", definieren Sie einen Parameter vom Typ "Nullable"\<booleschen >.  Der Bedarf an einem Dritten, nicht angegebenen Wert tritt normalerweise auf, wenn das Cmdlet eine boolesche Eigenschaft eines Objekts ändern kann. In diesem Fall bedeutet "nicht angegeben", dass der aktuelle Wert der Eigenschaft nicht geändert werden soll.

#### <a name="support-arrays-for-parameters"></a>Unterstützung von Arrays für Parameter

Häufig müssen Benutzer denselben Vorgang für mehrere Argumente ausführen. Für diese Benutzer sollte ein-Cmdlet ein Array als Parameter Eingabe akzeptieren, damit ein Benutzer die Argumente als Windows PowerShell-Variable an den-Parameter übergeben kann. Beispielsweise verwendet das [Get-Process-](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet ein Array für die Zeichen folgen, die die Namen der abzurufenden Prozesse identifizieren.

#### <a name="support-the-passthru-parameter"></a>Unterstützung des passthru-Parameters

Standardmäßig fungieren viele Cmdlets, die das System ändern, z. b. das Cmdlet "End [-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) ", als "senken" für Objekte, und es wird kein Ergebnis zurückgegeben. Dieses Cmdlet muss den `PassThru`-Parameter implementieren, um zu erzwingen, dass das Cmdlet ein Objekt zurückgibt. Wenn der `PassThru`-Parameter angegeben wird, gibt das Cmdlet ein Objekt zurück, indem die [System. Management. Automation. Cmdlet. Write Object](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) -Methode aufgerufen wird. Der folgende Befehl beendet beispielsweise den Calc-Prozess und übergibt den resultierenden Prozess an die Pipeline.

```powershell
Stop-Process calc -passthru
```

In den meisten Fällen sollten Add-, Set-und New-Cmdlets einen `PassThru`-Parameter unterstützen.

#### <a name="support-parameter-sets"></a>Unterstützungs Parameter Sätze

Ein Cmdlet soll einen einzigen Zweck erfüllen. Es gibt jedoch oft mehr als eine Möglichkeit, den Vorgang oder das Vorgangs Ziel zu beschreiben. Beispielsweise kann ein Prozess anhand seines Namens, seines Bezeichners oder eines Prozess Objekts identifiziert werden. Das Cmdlet sollte alle angemessenen Darstellungen seiner Ziele unterstützen. Normalerweise erfüllt das Cmdlet diese Anforderung durch Angeben von Gruppen von Parametern (als Parametersätze bezeichnet), die zusammenarbeiten. Ein einzelner Parameter kann zu einer beliebigen Anzahl von Parametersätzen gehören. Weitere Informationen zu Parametersätzen finden Sie unter [Cmdlet-Parametersätze](./cmdlet-parameter-sets.md).

Wenn Sie Parametersätze angeben, legen Sie nur einen Parameter im Set auf valuefrompipeline fest. Weitere Informationen zum Deklarieren des **Parameter** Attributs finden Sie unter [Parameterattribute Declaration](./parameter-attribute-declaration.md).

Wenn Parametersätze verwendet werden, wird der Standardparameter Satz durch das **Cmdlet** -Attribut definiert. Der Standardparameter Satz sollte die Parameter enthalten, die höchstwahrscheinlich in einer interaktiven Windows PowerShell-Sitzung verwendet werden. Weitere Informationen zum Deklarieren des **Cmdlet** -Attributs finden Sie unter [CmdletAttribute-Deklaration](./cmdlet-attribute-declaration.md).

### <a name="provide-feedback-to-the-user-sd04"></a>Bereitstellen von Feedback für den Benutzer (SD04)

Verwenden Sie die Richtlinien in diesem Abschnitt, um dem Benutzer Feedback zu geben. Dank dieses Feedbacks kann der Benutzer wissen, was im System passiert, und bessere administrative Entscheidungen treffen.

Mithilfe der Windows PowerShell-Laufzeit kann ein Benutzer angeben, wie die Ausgabe der einzelnen Aufrufe der `Write` Methode behandelt werden soll, indem eine Einstellungs Variable festgelegt wird. Der Benutzer kann mehrere Einstellungs Variablen festlegen, einschließlich einer Variablen, die bestimmt, ob das Systeminformationen anzeigen soll, sowie eine Variable, die bestimmt, ob das System den Benutzer vor der weiteren Aktion Abfragen soll.

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>Unterstützung der Methoden "Write Warning", "Write Verbose" und "Write Debug"

Ein Cmdlet muss die [System. Management. Automation. Cmdlet. Write Warning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) -Methode aufgerufen werden, wenn das Cmdlet einen Vorgang ausführt, der möglicherweise ein unbeabsichtigtes Ergebnis hat. Beispielsweise sollte ein Cmdlet diese Methode aufgerufen werden, wenn das Cmdlet im Begriff ist, eine schreibgeschützte Datei zu überschreiben.

Ein Cmdlet muss die [System. Management. Automation. Cmdlet. Write-Verbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) -Methode aufruft, wenn der Benutzer einige Details zu den Aktionen des Cmdlets benötigt. Beispielsweise sollte ein Cmdlet diese Informationen anrufen, wenn der Autor des Cmdlets der Meinung ist, dass es Szenarien gibt, in denen möglicherweise weitere Informationen zum Ausführen des Cmdlets erforderlich sind.

Das Cmdlet muss die [System. Management. Automation. Cmdlet. Write-Debug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) -Methode anrufen, wenn ein Entwickler oder Produktsupport Techniker wissen muss, was den Cmdlet-Vorgang beschädigt hat. Das Cmdlet muss die [System. Management. Automation. Cmdlet. Write Team Debug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) -Methode nicht im gleichen Code aufrufen, der die [System. Management. Automation. Cmdlet. Write](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) Items-Methode aufruft, da der `Debug`-Parameter beide Sätze von Informationen darstellt.

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>Unterstützung von Write Progress bei Vorgängen, die sehr lange dauern

Cmdlet-Vorgänge, deren Ausführung viel Zeit in Anspruch nimmt und die nicht im Hintergrund ausgeführt werden können, sollten die Fortschrittsbericht Erstellung durch regelmäßige Aufrufe der [System. Management. Automation. Cmdlet. Write Progress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) -Methode unterstützen.

#### <a name="use-the-host-interfaces"></a>Verwenden der Host Schnittstellen

Gelegentlich muss ein Cmdlet direkt mit dem Benutzer kommunizieren, anstatt die verschiedenen Write-oder If-Methoden zu verwenden, die von der [System. Management. Automation. Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) -Klasse unterstützt werden. In diesem Fall sollte das Cmdlet von der [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) -Klasse abgeleitet werden und die [System. Management. Automation. PSCmdlet. Host *](/dotnet/api/System.Management.Automation.PSCmdlet.Host) -Eigenschaft verwenden. Diese Eigenschaft unterstützt verschiedene Ebenen des Kommunikations Typs, einschließlich der Typen promptforchoice, prompt und Write teline/read line. Auf der spezifischsten Ebene bietet es auch Möglichkeiten, um einzelne Schlüssel zu lesen und zu schreiben und Puffer zu behandeln.

Wenn ein Cmdlet nicht speziell für die Generierung einer grafischen Benutzeroberfläche (GUI) entwickelt wurde, sollte der Host nicht mithilfe der [System. Management. Automation. PSCmdlet. Host *](/dotnet/api/System.Management.Automation.PSCmdlet.Host) -Eigenschaft umgangen werden. Ein Beispiel für ein Cmdlet, das zum Generieren einer GUI entworfen wurde, ist das [out-GridView](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) -Cmdlet.

> [!NOTE]
> Cmdlets sollten nicht die [System. Console](/dotnet/api/System.Console) -API verwenden.

### <a name="create-a-cmdlet-help-file-sd05"></a>Erstellen einer Cmdlet-Hilfedatei (SD05)

Erstellen Sie für jede Cmdlet-Assembly eine "Help. xml"-Datei, die Informationen über das Cmdlet enthält. Diese Informationen umfassen eine Beschreibung des Cmdlets, Beschreibungen der Cmdlet-Parameter, Beispiele für die Verwendung des Cmdlets und vieles mehr.

## <a name="code-guidelines"></a>Code Richtlinien

Die folgenden Richtlinien sollten beim Codieren von Cmdlets befolgt werden, um eine konsistente Benutzer Darstellung zwischen der Verwendung ihrer Cmdlets und anderer Cmdlets sicherzustellen. Wenn Sie eine Code Richtlinie finden, die für Ihre Situation gilt, achten Sie darauf, dass Sie die Entwurfs Richtlinien für ähnliche Richtlinien untersuchen.

### <a name="coding-parameters-sc01"></a>Codierungs Parameter (SC01)

Definieren Sie einen Parameter, indem Sie eine öffentliche Eigenschaft der Cmdlet-Klasse deklarieren, die mit dem **Parameter** -Attribut ergänzt wird. Parameter müssen keine statischen Member der abgeleiteten .NET Framework Klasse für das Cmdlet sein. Weitere Informationen zum Deklarieren des **Parameter** Attributs finden Sie unter [Parameter Attribut Deklaration](./parameter-attribute-declaration.md).

#### <a name="support-windows-powershell-paths"></a>Unterstützung von Windows PowerShell-Pfaden

Der Windows PowerShell-Pfad ist der Mechanismus, mit dem der Zugriff auf Namespaces normalisiert wird. Wenn Sie einen Windows PowerShell-Pfad einem Parameter im Cmdlet zuweisen, kann der Benutzer ein benutzerdefiniertes "Laufwerk" definieren, das als Verknüpfung zu einem bestimmten Pfad fungiert. Wenn ein Benutzer ein solches Laufwerk festlegt, können gespeicherte Daten, z. b. Daten in der Registrierung, auf konsistente Weise verwendet werden.

Wenn das Cmdlet dem Benutzer ermöglicht, eine Datei oder eine Datenquelle anzugeben, sollte ein Parameter vom Typ " [System. String](/dotnet/api/System.String)" definiert werden. Wenn mehr als ein Laufwerk unterstützt wird, muss es sich bei dem Typ um ein Array handeln. Der Name des Parameters sollte mit dem Alias `PSPath``Path`werden. Außerdem sollte der `Path`-Parameter Platzhalter Zeichen unterstützen. Wenn keine Unterstützung für Platzhalter Zeichen erforderlich ist, definieren Sie einen `LiteralPath` Parameter.

Wenn die vom Cmdlet gelesenen oder geschriebenen Daten eine Datei sein müssen, muss das Cmdlet die Windows PowerShell-Pfad Eingabe akzeptieren, und das Cmdlet muss die [System. Management. Automation. SessionState. Path](/dotnet/api/System.Management.Automation.SessionState.Path) -Eigenschaft verwenden, um die Windows PowerShell-Pfade in Pfade zu übersetzen, die vom Datei System erkannt werden. Zu den spezifischen Mechanismen gehören die folgenden Methoden:

- [System. Management. Automation. PSCmdlet. getresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System. Management. Automation. PSCmdlet. getunresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System. Management. Automation. pathintrinsics. getresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System. Management. Automation. pathintrinsics. getunresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

Wenn die vom Cmdlet gelesenen oder geschriebenen Daten nur eine Reihe von Zeichen folgen anstelle einer Datei sind, sollte das Cmdlet die Anbieter Inhaltsinformationen (`Content` Member) zum Lesen und Schreiben verwenden. Diese Informationen werden aus der [System. Management. Automation. Provider. cmdletprovider. invokeprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider) -Eigenschaft abgerufen. Mit diesen Mechanismen können andere Datenspeicher an dem Lesen und Schreiben von Daten teilnehmen.

#### <a name="support-wildcard-characters"></a>Platzhalter Zeichen unterstützen

Ein Cmdlet sollte nach Möglichkeit Platzhalter Zeichen unterstützen. Die Unterstützung von Platzhalter Zeichen tritt an vielen Stellen in einem Cmdlet auf (insbesondere dann, wenn ein Parameter eine Zeichenfolge annimmt, um ein Objekt aus einer Gruppe von Objekten zu identifizieren). Beispielsweise definiert das Beispiel **Stop-proc-** Cmdlet aus dem [stopproc-Tutorial](./stopproc-tutorial.md) einen `Name` Parameter, um Zeichen folgen zu behandeln, die Prozessnamen darstellen. Dieser Parameter unterstützt Platzhalter Zeichen, sodass der Benutzer die zu stoppenden Prozesse problemlos angeben kann.

Wenn die Unterstützung für Platzhalter Zeichen verfügbar ist, erzeugt ein Cmdlet-Vorgang in der Regel ein Array. Gelegentlich ist es nicht sinnvoll, ein Array zu unterstützen, da der Benutzer möglicherweise nur ein einzelnes Element gleichzeitig verwendet. Beispielsweise muss das Cmdlet " [Set-Location](/powershell/module/Microsoft.PowerShell.Management/Set-Location) " kein Array unterstützen, da der Benutzer nur einen einzigen Speicherort festlegt. In diesem Fall unterstützt das Cmdlet weiterhin Platzhalter Zeichen, aber es erzwingt die Auflösung an einem einzelnen Speicherort.

Weitere Informationen zu Platzhalter Zeichen Mustern finden Sie [unter unterstützen von Platzhalter Zeichen in Cmdlet-Parametern](./supporting-wildcard-characters-in-cmdlet-parameters.md).

#### <a name="defining-objects"></a>Definieren von Objekten

Dieser Abschnitt enthält Richtlinien zum Definieren von Objekten für Cmdlets und zum Erweitern vorhandener Objekte.

##### <a name="define-standard-members"></a>Standardmember definieren

Definieren Sie Standardmember, um einen Objekttyp in einer benutzerdefinierten Types. ps1xml-Datei zu erweitern (verwenden Sie die Datei Windows PowerShell Types. ps1xml als Vorlage). Standardmember werden von einem Knoten mit dem Namen psstandardmembers definiert. Mit diesen Definitionen können andere Cmdlets und die Windows PowerShell-Laufzeit auf konsistente Weise mit Ihrem Objekt arbeiten.

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>Definieren von objectmembers, die als Parameter verwendet werden sollen

Wenn Sie ein Objekt für ein Cmdlet entwerfen, stellen Sie sicher, dass seine Member direkt den Parametern der Cmdlets zugeordnet sind, von denen es verwendet wird. Diese Zuordnung ermöglicht, dass das-Objekt problemlos an die Pipeline gesendet und von einem Cmdlet an ein anderes übergeben werden kann.

Bereits vorhandene .NET Framework Objekte, die von Cmdlets zurückgegeben werden, fehlen häufig einige wichtige oder bequeme Member, die vom Skriptentwickler oder-Benutzer benötigt werden. Diese fehlenden Member können besonders wichtig für die Anzeige und das Erstellen der richtigen Elementnamen sein, damit das Objekt ordnungsgemäß an die Pipeline übermittelt werden kann. Erstellen Sie eine benutzerdefinierte Types. ps1xml-Datei, um diese erforderlichen Member zu dokumentieren. Wenn Sie diese Datei erstellen, wird die folgende Benennungs Konvention empfohlen: *< Your_Product_Name >* . Types. ps1xml.

Beispielsweise können Sie dem [System. IO. FileInfo](/dotnet/api/System.IO.FileInfo) -Typ eine `Mode` Script-Eigenschaft hinzufügen, um die Attribute einer Datei deutlicher anzuzeigen. Außerdem können Sie dem [System. Array](/dotnet/api/System.Array) -Typ eine `Count` Alias Eigenschaft hinzufügen, um die konsistente Verwendung dieses Eigenschafts namens (anstelle `Length`) zuzulassen.

##### <a name="implement-the-icomparable-interface"></a>Implementieren der ivergleichbare-Schnittstelle

Implementieren Sie eine [System. ivergleichbare](/dotnet/api/System.IComparable) -Schnittstelle für alle Ausgabe Objekte. Dadurch können die Ausgabe Objekte problemlos an verschiedene Sortierungs-und Analyse-Cmdlets weitergeleitet werden.

##### <a name="update-display-information"></a>Anzeigeinformationen aktualisieren

Wenn die Anzeige für ein Objekt nicht die erwarteten Ergebnisse liefert, erstellen Sie eine benutzerdefinierte *\<yourproductname->* . Format. ps1xml-Datei für dieses Objekt.

### <a name="support-well-defined-pipeline-input-sc02"></a>Unterstützen wohl definierter Pipeline Eingaben (SC02)

#### <a name="implement-for-the-middle-of-a-pipeline"></a>Implementieren für die Mitte einer Pipeline

Implementieren Sie ein Cmdlet, wenn Sie davon ausgehen, dass es von der Mitte einer Pipeline aus aufgerufen wird (d. h., dass andere Cmdlets Ihre Eingabe erzeugen oder Ihre Ausgabe verbrauchen). Beispielsweise können Sie davon ausgehen, dass das Cmdlet "`Get-Process`", weil es Daten generiert, nur als erstes Cmdlet in einer Pipeline verwendet wird. Da dieses Cmdlet jedoch für die Mitte einer Pipeline konzipiert ist, ermöglicht dieses Cmdlet, dass vorherige Cmdlets oder Daten in der Pipeline die abzurufenden Prozesse angeben.

#### <a name="support-input-from-the-pipeline"></a>Unterstützung von Eingaben aus der Pipeline

Fügen Sie in jedem Parametersatz für ein Cmdlet mindestens einen Parameter ein, der Eingaben aus der Pipeline unterstützt. Die Unterstützung von Pipeline Eingaben ermöglicht dem Benutzer das Abrufen von Daten oder Objekten, das Senden an den richtigen Parametersatz und das direkte übergeben der Ergebnisse an ein Cmdlet.

Ein Parameter akzeptiert Eingaben aus der Pipeline, wenn das **Parameter** Attribut das `ValueFromPipeline`-Schlüsselwort, das `ValueFromPipelineByPropertyName`-Schlüsselwort Attribut oder beide Schlüsselwörter in der Deklaration enthält. Wenn keiner der Parameter in einem Parametersatz das `ValueFromPipeline`-oder `ValueFromPipelineByPropertyName`-Schlüsselwort unterstützt, kann das Cmdlet nicht sinnvoll nach einem anderen Cmdlet platziert werden, da dadurch alle Pipeline Eingaben ignoriert werden.

#### <a name="support-the-processrecord-method"></a>Unterstützung der ProcessRecord-Methode

Um alle Datensätze aus dem vorherigen Cmdlet in der Pipeline zu akzeptieren, muss das Cmdlet die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode implementieren. Diese Methode wird von Windows PowerShell mehrmals aufgerufen, einmal für jeden Datensatz, der an Ihr Cmdlet gesendet wird.

### <a name="write-single-records-to-the-pipeline-sc03"></a>Schreiben einzelner Datensätze in die Pipeline (Sc03)

Wenn ein Cmdlet Objekte zurückgibt, sollte das Cmdlet die Objekte sofort beim Generieren schreiben. Das Cmdlet sollte Sie nicht enthalten, um Sie in einem kombinierten Array zu puffern. Die Cmdlets, die die Objekte als Eingabe empfangen, können dann die Ausgabe Objekte ohne Verzögerung verarbeiten, anzeigen oder verarbeiten und anzeigen. Ein Cmdlet, das Ausgabe Objekte nacheinander generiert, muss die [System. Management. Automation. Cmdlet. Write Object](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) -Methode aufzurufen. Ein Cmdlet, das Ausgabe Objekte in Batches generiert (z. b. weil eine zugrunde liegende API ein Array von Ausgabe Objekten zurückgibt), sollte die [System. Management. Automation. Cmdlet. Write-Object](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) -Methode aufrufen, wobei der zweite Parameter auf `true`festgelegt ist.

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>Cmdlets ohne Berücksichtigung der Groß-/Kleinschreibung und Groß-/Kleinschreibung (Sc04)

Standardmäßig wird von Windows PowerShell selbst keine Groß-/Kleinschreibung beachtet. Da es jedoch viele bereits vorhandene Systeme behandelt, behält Windows PowerShell die Groß-/Kleinschreibung bei, um den Betrieb und die Kompatibilität zu vereinfachen. Anders ausgedrückt: Wenn ein Zeichen in Großbuchstaben angegeben wird, speichert Windows PowerShell es in Großbuchstaben. Damit Systeme gut funktionieren, muss ein Cmdlet dieser Konvention folgen. Wenn möglich, sollte die Groß-/Kleinschreibung nicht beachtet werden. Der ursprüngliche Fall für Cmdlets, die später in einem Befehl oder in der Pipeline auftreten, sollte jedoch beibehalten werden.

## <a name="see-also"></a>Weitere Informationen

[Erforderliche Entwicklungs Richtlinien](./required-development-guidelines.md)

[Leitlinien für die Beratung](./advisory-development-guidelines.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
