---
title: Richtlinien für die Entwicklung dringend empfohlen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: c11e50913d2654b786e0e8cfeaf41454999bf75e
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794968"
---
# <a name="strongly-encouraged-development-guidelines"></a>Ausdrücklich empfohlene Entwicklungsrichtlinien

Dieser Abschnitt beschreibt die Richtlinien, die Sie befolgen sollten, wenn Sie Ihre Cmdlets schreiben. Sie werden in den Richtlinien zum Entwerfen von Cmdlets und Richtlinien zum Schreiben von Cmdlet-Code getrennt. Sie können feststellen, dass es sich bei diesen Richtlinien nicht für jedes Szenario gelten. Jedoch wenn sie gelten, und Sie diese Richtlinien nicht führen, Ihre Benutzer eine schlechte benutzererfahrung möglicherweise, wenn sie Ihre Cmdlets verwenden.

## <a name="design-guidelines"></a>Richtlinien für den Entwurf

- [Verwenden Sie für einen Cmdlet-Namen (SD01) einem bestimmten Nomen verbunden](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [Verwenden Sie die Pascal-Schreibweise für Cmdlet-Namen (SD02)](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [Parameter-Entwurfsrichtlinien (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [Bereitstellen von Feedback an den Benutzer (SD04)](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [Erstellen Sie eine Cmdlet-Hilfe-Datei (SD05)](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>Coderichtlinien

- [Parameter (SC01) codieren](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [Unterstützt wohldefinierte Pipelineeingabe (SC02)](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [Schreiben Sie die einzelnen Datensätze an die Pipeline (SC03)](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [Stellen Sie Cmdlets Groß-/Kleinschreibung und Groß-/Kleinschreibung beibehalten werden soll (SC04)](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>Richtlinien für den Entwurf

Die folgenden Richtlinien sollten beim Entwerfen von Cmdlets, um sicherzustellen, dass eine konsistente benutzererfahrung zwischen der Verwendung, Ihre Cmdlets und andere Cmdlets folgen. Wenn Sie eine designrichtlinie, die auf Ihren Fall zutrifft finden, achten Sie darauf, dass Sie betrachten, die Code-Richtlinien für ähnliche Richtlinien.

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>Verwenden Sie für einen Cmdlet-Namen (SD01) einem bestimmten Nomen verbunden

Nomen im Cmdlet-Namen verwendet, müssen sehr spezifisch sein, damit der Benutzer Ihre Cmdlets ermitteln kann. Generische Nomen, z. B. "Server" mit der eine gekürzte Version des Produktnamens als Präfix voranstellen. Wenn ein Substantiv auf einen Server, die eine Instanz von Microsoft SQL Server ausgeführt wird verweist, verwenden Sie z. B. ein Substantiv, z. B. "SQLServer". Die Kombination aus bestimmten Nomen und die kurze Liste der zulässigen Verben ermöglichen es dem Benutzer schnell ermitteln und ihre Funktionalität schließen, während die Vermeidung der mehrfachen Ausführung von Cmdlet-Namen.

Um die benutzerfreundlichkeit zu verbessern, sollte das Nomen, das Sie, für einen Cmdlet-Namen auswählen im singular. Verwenden Sie z. B. den Namen `Get-Process` anstelle von **Get-Prozesse**. Es wird empfohlen, befolgen Sie diese Regel für alle cmdletnamen, sogar, wenn ein Cmdlet wahrscheinlich zu mehr als ein Element reagieren.

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>Verwenden Sie die Pascal-Schreibweise für Cmdlet-Namen (SD02)

Verwenden Sie Pascal-Schreibweise für Parameternamen. Das heißt, profitieren Sie den ersten Buchstaben des Verbs und alle Ausdrücke, die in die das Nomen verwendet. Z. B. "`Clear-ItemProperty`".

### <a name="parameter-design-guidelines-sd03"></a>Parameter-Entwurfsrichtlinien (SD03)

Ein Cmdlet benötigt, Parameter, die die Daten zu empfangen, auf denen sie betrieben werden muss, und Parameter, die Informationen, die verwendet wird, um zu bestimmen, die Merkmale des Vorgangs auf. Angenommen, ein Cmdlet haben eine `Name` Parameter, der Daten aus der Pipeline, und das Cmdlet empfängt möglicherweise eine `Force` Parameter, um anzugeben, dass das Cmdlet erzwungen werden kann, um diesen Vorgang auszuführen. Es gibt keine Beschränkung der Anzahl von Parametern, die ein Cmdlet definieren können.

#### <a name="use-standard-parameter-names"></a>Standard-Parameternamen verwenden

Ihr Cmdlet sollten Standardparameternamen verwenden, sodass der Benutzer schnell bestimmen kann, was bedeutet, dass ein bestimmter Parameter. Wenn Sie ein genaueren Namen erforderlich ist, verwenden Sie einen Namen für die Standardparameter, und geben Sie einen spezifischeren Namen als Alias. Z. B. die `Get-Service` Cmdlet verfügt über einen Parameter, der einen generischen Namen aufweist (`Name`) und eine spezifischere Alias (`ServiceName`). Beide Begriffe können zum Angeben des Parameters verwendet werden.

Weitere Informationen zu Parameternamen und Datentypen finden Sie unter [Cmdlet-Parameternamen und Funktionalität Richtlinien](./standard-cmdlet-parameter-names-and-types.md).

#### <a name="use-singular-parameter-names"></a>Verwenden von Singular-Parameternamen

Verwenden Sie Pluralnamen für Parameter, dessen Wert ein einzelnes Element ist. Dies enthält Parameter, die Arrays werden oder listet daran, dass der Benutzer auf ein Array oder eine Liste mit nur einem Element bereitstellen kann.

Im Plural Parameternamen sollten nur in diesen Fällen verwendet werden, der Wert des Parameters immer einen Wert von mehreren Elementen lautet. In diesen Fällen sollte das-Cmdlet überprüfen, ob mehrere Elemente bereitgestellt werden, und das-Cmdlet sollte eine Warnung für den Benutzer angezeigt, wenn mehrere Elemente nicht bereitgestellt werden.

#### <a name="use-pascal-case-for-parameter-names"></a>Verwenden der Pascal-Schreibweise für Parameternamen

Verwenden Sie Pascal-Schreibweise für Parameternamen. Profitieren Sie in anderen Worten: der erste Buchstabe jedes Worts in den Parameternamen, einschließlich den ersten Buchstaben des Namens. Z. B. der Parametername `ErrorAction` die richtige Groß-/Kleinschreibung verwendet. Verwenden Sie die folgenden Parameternamen falsche Groß-/Kleinschreibung:

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>Parameter, die eine Liste mit Optionen ausführen

Es gibt zwei Möglichkeiten, einen Parameter zu erstellen, dessen Wert in einen Satz von Optionen ausgewählt werden kann.

- Definieren Sie einen Enumerationstyp (oder einen vorhandenen Enumerationstyp verwenden), die die gültigen Werte angibt. Klicken Sie dann verwenden Sie den Enumerationstyp, um einen Parameter dieses Typs zu erstellen.

- Hinzufügen der **ValidateSet** -Attribut auf die Parameterdeklaration. Weitere Informationen zu diesem Attribut finden Sie unter [ValidateSet Attributdeklaration](./validateset-attribute-declaration.md).

#### <a name="use-standard-types-for-parameters"></a>Verwenden Sie die Standardtypen für Parameter

Verwenden Sie zur Gewährleistung der Konsistenz mit anderen Cmdlets Standardtypen für Parameter, egal wo möglich. Weitere Informationen zu den Typen, die für verschiedene Parameter verwendet werden soll, finden Sie unter [Standard-Cmdlet-Parameternamen und-Typen](./standard-cmdlet-parameter-names-and-types.md). Dieses Thema enthält Links zu verschiedenen Themen, in denen die Namen und die .NET Framework-Typen für Gruppen von Standardparameter, z. B. "Aktivitätsparameter" beschrieben.

#### <a name="use-strongly-typed-net-framework-types"></a>Verwenden von stark typisierten .NET Framework-Typen

Parameter müssen als .NET Framework-Typen zu besseren parametervalidierung definiert sein. Beispielsweise sollten Parameter, die auf einen Wert aus einem Satz von Werten beschränkt sind, als ein Enumerationstyp definiert werden. Um einen Uniform Resource Identifier (URI)-Wert zu unterstützen, definieren Sie den Parameter als ein [System.Uri](/dotnet/api/System.Uri) Typ. Vermeiden Sie die allgemeine Zeichenfolgen-Parameter für alle außer Freitext-Eigenschaften.

#### <a name="use-consistent-parameter-types"></a>Konsistente Parametertypen verwenden

Wenn von mehreren Cmdlets derselbe Parameter verwendet wird, verwenden Sie immer den gleichen Parametertyp aus.  Z. B. wenn die `Process` -Parameter ist ein [System. Int16](/dotnet/api/System.Int16) für ein Cmdlet geben, nehmen Sie keine der `Process` -Parameter für ein anderes Cmdlet eine [System. UInt16](/dotnet/api/System.UInt16) Typ.

#### <a name="parameters-that-take-true-and-false"></a>Parameter, die "true" verwenden und "false"

Wenn der Parameter nur dauert `true` und `false`, definieren Sie den Parameter als Typ [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter). Ein Switch-Parameter wird als behandelt `true` wenn er in einem Befehl angegeben wird. Wenn der Parameter nicht in einem Befehl enthalten ist, hält Windows PowerShell den Wert des Parameters, der sein `false`. Boolesche Parameter ist nicht definiert werden.

Wenn der Parameter zwischen 3 Werte unterscheiden muss: $true, $false und "nicht angegeben", definieren Sie dann auf einen Parameter vom Typ Nullable\<Bool >.  Die Notwendigkeit einer 3., tritt "nicht angegebenen" Wert in der Regel ein, wenn das Cmdlet eine boolesche Eigenschaft eines Objekts ändern kann. In diesem Fall bedeutet, dass "nicht angegeben" den aktuellen Wert der Eigenschaft nicht ändern.

#### <a name="support-arrays-for-parameters"></a>Unterstützung für Arrays für Parameter

In vielen Fällen müssen Benutzer den gleichen Vorgang für mehrere Argumente ausführen. Diese Benutzer sollten ein Cmdlet ein Array akzeptieren, als Parameter eingeben, damit ein Benutzer die Argumente an den Parameter als eine Windows PowerShell-Variable übergeben werden kann. Z. B. die [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet verwendet ein Array für die Zeichenfolgen, die die Namen der abzurufenden Prozesse zu identifizieren.

#### <a name="support-the-passthru-parameter"></a>Unterstützen Sie den PassThru-Parameter

Standardmäßig viele Cmdlets, das Ändern des Systems wie z. B. die [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) -Cmdlet als "Sinks" für Objekte fungieren, und führen Sie kein Ergebnis zurückgegeben. Diese Cmdlets sollten implementieren die `PassThru` Parameter, um zu erzwingen, dass das Cmdlet ein Objekt zurückgegeben. Wenn die `PassThru` -Parameter angegeben wird, mit dem-Cmdlet gibt ein Objekt zurück, mit einem Aufruf der [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) Methode. Beispielsweise wird der folgende Befehl beendet den Calc-Prozess und übergibt an die Pipeline den resultierenden Prozess.

```powershell
Stop-Process calc -passthru
```

In den meisten Fällen sollte die Add, Set und neuen-Cmdlets unterstützen eine `PassThru` Parameter.

#### <a name="support-parameter-sets"></a>Unterstützung von Parametersätzen

Ein Cmdlet soll einen Zweck zu erreichen. Es ist jedoch häufig mehr als eine Möglichkeit, um den Vorgang oder das Ziel des Vorgangs zu beschreiben. Beispielsweise kann ein Prozess mit dem Namen, durch seinen Bezeichner oder ein Prozessobjekt identifiziert werden. Das Cmdlet sollte die angemessenen Darstellungen der zugehörigen Ziele unterstützen. In der Regel führt das Cmdlet diese Anforderung durch Angabe der Sätze von Parametern (wie Parametersätze bezeichnet), die zusammen verwendet werden. Ein einzelner Parameter kann eine beliebige Anzahl von Parametersätzen angehören. Weitere Informationen zu Parametersätze, finden Sie unter [Cmdlet Parametersätze](./cmdlet-parameter-sets.md).

Wenn Sie die Parametersätze angeben, legen Sie nur einen Parameter in der Gruppe, ValueFromPipeline. Weitere Informationen dazu, wie Sie deklarieren die **Parameter** Attribut, finden Sie unter [ParameterAttribute Deklaration](./parameter-attribute-declaration.md).

Wenn Parametersätze verwendet werden, wird von der Standard-Parametersatz definiert die **Cmdlet** Attribut. Der Standard-Parametersatz aufzunehmen die Parameter, die wahrscheinlich in einer interaktiven Windows PowerShell-Sitzung verwendet werden. Weitere Informationen dazu, wie Sie deklarieren die **Cmdlet** Attribut, finden Sie unter [CmdletAttribute-Deklaration](./cmdlet-attribute-declaration.md).

### <a name="provide-feedback-to-the-user-sd04"></a>Bereitstellen von Feedback an den Benutzer (SD04)

Verwenden Sie die Richtlinien in diesem Abschnitt, um dem Benutzer Feedback bereitzustellen. Dieses Feedback ermöglicht den Benutzer zu beachten, was im System ausgeführt wird und eine bessere Verwaltung Entscheidungen zu treffen.

Die Windows PowerShell-Laufzeit ermöglicht einem Benutzer angeben, wie die Ausgabe aus jedem Aufruf zum Verarbeiten der `Write` Methode durch eine Einstellungsvariable festlegen. Der Benutzer kann mehrere Preference-Variablen, einschließlich einer Variablen, die bestimmt, ob das System angezeigt werden sollen, Informationen und eine Variable, die bestimmt, ob das System des Benutzers abgefragt werden sollen, bevor eine weitere Aktion festlegen.

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>Unterstützen der WriteWarning WriteVerbose und WriteDebug-Methoden

Es sollte ein Cmdlet aufrufen. die [System.Management.Automation.Cmdlet.Writewarning*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) Methode, wenn das Cmdlet einen Vorgang ausführen, die möglicherweise eine unbeabsichtigte Nebeneffekte haben. Beispielsweise sollte ein Cmdlet diese Methode aufrufen, wenn das-Cmdlet wird eine schreibgeschützte Datei zu überschreiben.

Es sollte ein Cmdlet aufrufen. die [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) Methode, wenn der Benutzer einige Details benötigt, das Cmdlet Wozu dient. Beispielsweise sollte ein Cmdlet diese Informationen aufrufen, wenn es sich bei der Cmdlet-Autor Gefühl, dass es Szenarien, die möglicherweise weitere Informationen zu können, das Cmdlet Wozu dient.

Rufen Sie das Cmdlet sollte die [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) Methode, wenn ein Entwickler oder Produkt Supporttechniker verstehen muss, welche Daten die Cmdlet-Vorgangs beschädigt wurde. Es muss nicht für das-Cmdlet aufrufen, die [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) -Methode in der der gleiche Code, der Aufrufe der [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) Methode da die `Debug` Parameter stellt die erforderlichen Informationen.

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>Unterstützung von WriteProgress für Vorgänge, die sehr lange dauern

Cmdlet-Vorgänge für diese akzeptieren, die eine lange Zeit in Anspruch und, können nicht im Hintergrund ausgeführt sollte über periodische Aufrufe von statusberichterstellung unterstützen die [System.Management.Automation.Cmdlet.Writeprogress*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) Methode.

#### <a name="use-the-host-interfaces"></a>Verwenden Sie die Hostschnittstellen

In einigen Fällen ein Cmdlet muss kommunizieren direkt mit dem Benutzer anstelle von mithilfe der verschiedenen schreiben oder von unterstützte Methoden sollten die [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) Klasse. In diesem Fall sollte das Cmdlet leiten Sie von der [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) Klasse, und Verwenden der [System.Management.Automation.Pscmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) Eigenschaft. Diese Eigenschaft unterstützt verschiedene Abonnementebenen Kommunikationsart, einschließlich der Typen PromptForChoice, Eingabe und WriteLine / "ReadLine" an. Auf der höchsten bestimmte Zugriffsebene, bietet aber auch Möglichkeiten zum Lesen und schreiben die einzelnen Schlüssel und zur Behandlung von Puffern.

Wenn ein Cmdlet speziell entwickelt wird, um eine grafische Benutzeroberfläche (GUI) zu generieren, sollte es den Host nicht umgehen, indem Sie mit der [System.Management.Automation.Pscmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) Eigenschaft. Ein Beispiel für ein Cmdlet aus, die entwickelt wurde, um eine grafische Benutzeroberfläche zu generieren ist die [Out-GridView](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) Cmdlet.

> [!NOTE]
> Cmdlets sollten nicht verwenden, die ["System.Console"](/dotnet/api/System.Console) API.

### <a name="create-a-cmdlet-help-file-sd05"></a>Erstellen Sie eine Cmdlet-Hilfe-Datei (SD05)

Erstellen Sie eine Help.xml-Datei, die Informationen zum Cmdlet enthält, für jede Assembly Cmdlet. Diese Informationen umfassen eine Beschreibung der Cmdlets, Beschreibungen der Cmdlet Parameter, Beispiele für die Cmdlet Verwendung und vieles mehr.

## <a name="code-guidelines"></a>Coderichtlinien

Die folgenden Richtlinien sollten beim Schreiben von Cmdlets, um sicherzustellen, dass eine konsistente benutzererfahrung zwischen der Verwendung, Ihre Cmdlets und andere Cmdlets folgen. Wenn Sie eine Richtlinie Code, die auf Ihren Fall zutrifft finden, achten Sie darauf, dass Sie die Entwurfsrichtlinien für ähnliche Richtlinien ansehen.

### <a name="coding-parameters-sc01"></a>Parameter (SC01) codieren

Definieren eines Parameters durch Deklarieren einer öffentlichen Eigenschaft der Cmdlet-Klasse, die mit ergänzt wird die **Parameter** Attribut. Parameter müssen nicht statische Member des abgeleiteten .NET Framework-Klasse für das-Cmdlet werden. Weitere Informationen dazu, wie Sie deklarieren die **Parameter** Attribut, finden Sie unter [Parameter Attributdeklaration](./parameter-attribute-declaration.md).

#### <a name="support-windows-powershell-paths"></a>Unterstützung von Windows PowerShell-Pfaden

Der Windows PowerShell-Pfad ist der Mechanismus für den Zugriff auf Namespaces normalisieren. Wenn Sie einen Windows PowerShell-Pfad auf einen Parameter im Cmdlet zuweisen, kann der Benutzer ein benutzerdefiniertes "Drive", die als Verknüpfung zu einem bestimmten Pfad fungiert definieren. Wenn ein Benutzer diese einem Laufwerk festlegt, können die gespeicherte Daten, z.B. in der Registrierung auf konsistente Weise verwendet werden.

Wenn Ihr Cmdlet den Benutzer eine Datei oder eine Datenquelle angeben kann, sollten sie einen Parameter vom Typ definieren [System.String](/dotnet/api/System.String). Wenn mehr als ein Laufwerk unterstützt wird, sollte der Typ ein Array sein. Der Name des Parameters muss `Path`, mit einem Alias von `PSPath`. Darüber hinaus die `Path` Parameter sollte ein Platzhalterzeichen unterstützen. Wenn die Unterstützung für Platzhalterzeichen ist nicht erforderlich, zum Definieren einer `LiteralPath` Parameter.

Wenn die Daten, die mit dem-Cmdlet liest oder schreibt eine Datei sein müssen, das Cmdlet Windows PowerShell-Pfad-Eingabe akzeptieren sollte und das Cmdlet verwenden, sollten die [System.Management.Automation.Sessionstate.Path](/dotnet/api/System.Management.Automation.SessionState.Path) zu den Windows zu übersetzenden Eigenschaft PowerShell-Pfaden in Pfade, die im Dateisystem erkennt. Die bestimmten Mechanismen umfassen die folgenden Methoden:

- [System.Management.Automation.Pscmdlet.Getresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.Pscmdlet.Getunresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System.Management.Automation.Pathintrinsics.Getresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.Pathintrinsics.Getunresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

Wenn die Daten, die mit dem-Cmdlet liest oder schreibt nur ein Satz von Zeichenfolgen anstelle einer Datei mit dem Cmdlet sollten die Inhaltsinformationen für Anbieter verwenden (`Content` Member) zum Lesen und schreiben. Diese Informationen werden abgerufen, von der [System.Management.Automation.Provider.Cmdletprovider.Invokeprovider*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider) Eigenschaft. Anhand dieser Mechanismen kann es sich um andere Datenspeicher zur Teilnahme an das Lesen und Schreiben von Daten.

#### <a name="support-wildcard-characters"></a>Unterstützung von Platzhalterzeichen

Platzhalterzeichen sollten nach Möglichkeit ein Cmdlet unterstützt werden. Unterstützung für Platzhalterzeichen tritt auf, an vielen Stellen in einem Cmdlet (insbesondere bei Verwendung der Parameter eine Zeichenfolge, die ein Objekt aus einem Satz von Objekten identifizieren dauert). Beispielsweise das Beispiel **Stop-Proc** Cmdlet über die [StopProc Tutorial](./stopproc-tutorial.md) definiert eine `Name` Parameter, um Zeichenfolgen zu behandeln, die Prozessnamen darstellen. Dieser Parameter unterstützt Platzhalterzeichen, damit der Benutzer leicht die Prozesse beenden angeben kann.

Wenn die Unterstützung für Platzhalter Zeichen verfügbar ist, erzeugt ein Cmdlet-Vorgang in der Regel ein Array. In einigen Fällen ist es nicht sinnvoll, ein Array zu unterstützen, da der Benutzer nur ein einziges Element zu einem Zeitpunkt verwenden kann. Z. B. die [Set-Location](/powershell/module/Microsoft.PowerShell.Management/Set-Location) Cmdlet muss sich nicht um ein Array zu unterstützen, da der Benutzer nur eine einzige Position festlegt. In diesem Fall das Cmdlet immer noch unterstützt Platzhalterzeichen an zentraler Stelle Auflösung wird erzwungen.

Weitere Informationen zu Platzhalterzeichen Mustern finden Sie unter [Platzhalterzeichen unterstützt, in der Cmdlet-Parameter](./supporting-wildcard-characters-in-cmdlet-parameters.md).

#### <a name="defining-objects"></a>Definieren von Objekten

Dieser Abschnitt enthält Richtlinien zum Definieren von Objekten für Cmdlets und zum Erweitern der vorhandener Objekts.

##### <a name="define-standard-members"></a>Definieren Sie Standard-Member

Definieren Sie standard Member um einen Objekttyp in einer benutzerdefinierten Types. ps1xml-Datei (verwenden Sie die Windows PowerShell Types. ps1xml-Datei als Vorlage) zu erweitern. Standard-Elemente werden von einem Knoten mit dem Namen PSStandardMembers definiert. Diese Definitionen ermöglicht werden, andere Cmdlets und die Windows PowerShell-Laufzeit mit dem Objekt auf konsistente Weise funktioniert.

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>Definieren von ObjectMembers als Parameter verwendet werden soll

Wenn Sie ein Objekt für ein Cmdlet entwerfen, stellen Sie sicher, dass Member direkt in den Parametern der Cmdlets zugeordnet werden, die sie verwenden. Diese Zuordnung ermöglicht das Objekt einfach an die Pipeline gesendet werden und von einem Cmdlet an eine andere übergeben werden.

Bereits vorhandene .NET Framework-Objekten, die von Cmdlets zurückgegebenen fehlen häufig einige wichtige oder einfache Mitglieder, die vom Skriptentwickler oder Benutzer erforderlich sind. Diese fehlenden Member möglich besonders wichtig, für die Anzeige und das richtige Element Namen erstellen können, damit das Objekt ordnungsgemäß an die Pipeline übergeben werden kann. Erstellen Sie eine benutzerdefinierte Types. ps1xml-Datei, um diese erforderlichen Elemente zu dokumentieren. Wenn Sie diese Datei erstellen, sollten Sie die folgende Benennungskonvention verwendet: *< Your_Product_Name >*. Types. ps1xml.

Sie könnten z. B. Hinzufügen einer `Mode` -skripteigenschaft zu den [System.IO.Fileinfo](/dotnet/api/System.IO.FileInfo) Typs, um die Attribute einer Datei deutlicher anzuzeigen. Außerdem kann hinzugefügt werden, eine `Count` aliaseigenschaft der [System.Array](/dotnet/api/System.Array) die konsistente Verwendung von der Eigenschaftenname zuzulassenden Typs (anstelle von `Length`).

##### <a name="implement-the-icomparable-interface"></a>Implementieren der IComparable-Schnittstelle

Implementieren einer [System.Icomparable](/dotnet/api/System.IComparable) Schnittstelle für alle Ausgabeobjekte. Dadurch wird die Ausgabeobjekte, die problemlos für verschiedene Sortier- und Analyse-Cmdlets übergeben werden.

##### <a name="update-display-information"></a>Aktualisieren Sie die Anzeigeinformationen

Wenn die Anzeige für ein Objekt nicht die erwarteten Ergebnisse bietet, erstellen Sie eine benutzerdefinierte  *\<YourProductName >*. Format. ps1xml-Datei für dieses Objekt.

### <a name="support-well-defined-pipeline-input-sc02"></a>Unterstützt wohldefinierte Pipelineeingabe (SC02)

#### <a name="implement-for-the-middle-of-a-pipeline"></a>Implementieren Sie für die Mitte der Pipeline

Implementieren ein Cmdlets, vorausgesetzt, dass es aus der Mitte der Pipeline aufgerufen wird (d. h. wird andere Cmdlets Eingabe erzeugt oder nutzen Sie die Ausgabe). Sie könnten beispielsweise annehmen, die die `Get-Process` -Cmdlet, da es die Daten generiert wird lediglich als das erste Cmdlet in einer Pipeline verwendet. Da dieses Cmdlet aus, für die Mitte der Pipeline ausgelegt ist, kann jedoch mit diesem Cmdlet vorherigen Cmdlets oder die Daten in der Pipeline an die Prozesse abzurufen.

#### <a name="support-input-from-the-pipeline"></a>Unterstützung von Eingaben aus der Pipeline

Enthalten Sie in jedem Parameter für ein Cmdlet festlegen mindestens einen Parameter, die Eingaben aus der Pipeline unterstützt. Unterstützung für Pipelineeingabe ermöglicht, dem Benutzer zum Abrufen von Daten oder Objekte, die sie an den richtigen Parametersatz zu senden und die Ergebnisse direkt an ein Cmdlet übergeben wird.

Einen Parameter akzeptiert Eingaben aus der Pipeline aus, wenn die **Parameter** Attribut enthält die `ValueFromPipeline` -Schlüsselwort, das `ValueFromPipelineByPropertyName` Keyword-Attribut, oder beide Schlüsselwörter in der Deklaration. Wenn keiner der Parameter in einem Parameter festlegen, dass Unterstützung der `ValueFromPipeline` oder `ValueFromPipelineByPropertyName` Schlüsselwörter, mit dem-Cmdlet können nicht nach einem anderen Cmdlet Klassenmemberfunktionen platziert werden, da Pipelineeingabe ignoriert wird.

#### <a name="support-the-processrecord-method"></a>Unterstützung für die ProcessRecord-Methode

Um alle Datensätze aus dem vorherigen Cmdlet in der Pipeline akzeptieren zu können, muss Ihr Cmdlet implementieren die [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode. Windows PowerShell ruft diese Methode mehrfach, einmal für jeden Datensatz an, die dem Cmdlet gesendet wird.

### <a name="write-single-records-to-the-pipeline-sc03"></a>Schreiben Sie die einzelnen Datensätze an die Pipeline (SC03)

Wenn ein Cmdlet Objekte zurückgibt, schreibt das Cmdlet sollte die Objekte sofort, sobald sie generiert werden. Das Cmdlet sollte nicht sie speichern und diese in ein Array im kombinierten Puffern. Die Cmdlets, die die Objekte als Eingabe empfangen werden können zu verarbeiten, anzuzeigen oder zu verarbeiten und zeigt die Ausgabeobjekte ohne Verzögerung. Ein Cmdlet, das Ausgaben generiert Objekte einzeln aufrufen sollten die [System.Management.Automation.Cmdlet.Writeobject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) Methode. Es sollte ein Cmdlet, das Ausgabeobjekte in Batches generiert (z. B. weil eine zugrunde liegende API ein Array von Ausgabeobjekten zurückgibt) aufrufen. die [System.Managemet.Automation.Cmdlet.Writeobject](/dotnet/api/System.Managemet.Automation.Cmdlet.WriteObject) Methode, für den zweiten Parameter festgelegt um `true`.

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>Stellen Sie Cmdlets Groß-/Kleinschreibung und Groß-/Kleinschreibung beibehalten werden soll (SC04)

Standardmäßig ist Windows PowerShell selbst Groß-/Kleinschreibung. Da es mit vielen vorhandenen Systemen behandelt wird, wird Windows PowerShell jedoch bei einfachen Vorgang und Kompatibilität beibehalten. Das heißt, wenn ein Zeichen in Großbuchstaben angegeben wird, behält Windows PowerShell es in Großbuchstaben. Für Systeme, die gut funktioniert muss ein Cmdlet dieser Konvention folgen. Wenn möglich, sollten sie auf eine Weise Groß-/Kleinschreibung verwendet werden. Die ursprüngliche Groß-/Kleinschreibung für Cmdlets sollte, die später in einem Befehl oder in der Pipeline auftreten jedoch beibehalten.

## <a name="see-also"></a>Weitere Informationen

[Richtlinien für die Entwicklung von erforderlich](./required-development-guidelines.md)

[Richtlinien für die Advise-Entwicklung](./advisory-development-guidelines.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
