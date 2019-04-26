---
title: Richtlinien für die Advise-Entwicklung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 871a74a084da3c7ec36767b7195461e0e7290cb9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068792"
---
# <a name="advisory-development-guidelines"></a>Empfohlene Entwicklungsrichtlinien

Dieser Abschnitt beschreibt die Richtlinien, die Sie berücksichtigen sollten, um sicherzustellen, dass gute Erfahrungen für Entwicklung und Benutzer. Manchmal kann gelten, und sie möglicherweise manchmal nicht.

## <a name="design-guidelines"></a>Richtlinien für den Entwurf

- [Unterstützt eine InputObject-Parameter (AD01)](./advisory-development-guidelines.md#AD01)

- [Unterstützung der Force-Parameter (AD02)](./advisory-development-guidelines.md#AD02)

- [Verarbeiten von Anmeldeinformationen mithilfe von Windows PowerShell (AD03)](./advisory-development-guidelines.md#AD03)

- [Encoding-Parameter (AD04) unterstützt](./advisory-development-guidelines.md#AD04)

- [Test-Cmdlets muss einen boolescher Wert (AD05) zurückgeben.](./advisory-development-guidelines.md#AD05)

## <a name="code-guidelines"></a>Coderichtlinien

- [Führen Sie die Cmdlet-Klasse-Benennungskonventionen (AC01)](./advisory-development-guidelines.md#AC01)

- [Wenn keine Pipelineeingabe der BeginProcessing-Methode (AC02) überschreiben](./advisory-development-guidelines.md#AC02)

- [Stop-Anforderungen außer Kraft setzen die StopProcessing-Methode (AC03) behandelt.](./advisory-development-guidelines.md#AC03)

- [Implementieren der IDisposable-Schnittstelle (AC04)](./advisory-development-guidelines.md#AC04)

- [Verwenden Sie die Serialisierung geeignet Parametertypen (AC05)](./advisory-development-guidelines.md#AC05)

- [Verwenden von SecureString für vertrauliche Daten (AC06)](./advisory-development-guidelines.md#AC06)

## <a name="design-guidelines"></a>Richtlinien für den Entwurf

Die folgenden Richtlinien berücksichtigen Sie beim Entwerfen von Cmdlets. Wenn Sie eine designrichtlinie, die auf Ihren Fall zutrifft finden, achten Sie darauf, dass Sie betrachten, die Code-Richtlinien für ähnliche Richtlinien.

### <a name="support-an-inputobject-parameter-ad01"></a>Unterstützt eine InputObject-Parameter (AD01)

Da Windows PowerShell direkt mit Microsoft .NET Framework-Objekten verwendet werden kann, ist ein .NET Framework-Objekt häufig verfügbar, die genau übereinstimmt, die der Typ der Benutzer muss über einen bestimmten Vorgang ausführen. `InputObject` ist der standard-Name für einen Parameter, der solche ein Objekt als Eingabe akzeptiert. Zum Beispiel **Stop-Proc** -Cmdlet in der [StopProc Tutorial](./stopproc-tutorial.md) definiert eine `InputObject` Parameter vom Typ Prozess, der die Eingabe aus der Pipeline unterstützt. Der Benutzer erhalten einen Satz von Prozessobjekten, bearbeiten sie zum Beenden der exakt die Objekte auswählen und dann übergeben sie können die **Stop-Proc** Cmdlet direkt.

### <a name="support-the-force-parameter-ad02"></a>Unterstützung der Force-Parameter (AD02)

In einigen Fällen muss ein Cmdlets verhindern, dass den Benutzer eine angeforderte Operation. Solche ein Cmdlet sollte unterstützen eine `Force` Parameter ermöglicht dem Benutzer, die diesen Schutz zu überschreiben, wenn der Benutzer über Berechtigungen zum Ausführen des Vorgangs verfügt.

Z. B. die [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) Cmdlet werden keine normalerweise eine schreibgeschützte Datei entfernt. Dieses Cmdlet unterstützt jedoch eine `Force` an, damit ein Benutzer zum Entfernen einer schreibgeschützten Datei erzwingen kann. Wenn der Benutzer hat bereits die Berechtigung zum Ändern des Attributs schreibgeschützt, und der Benutzer wird die Datei entfernt, verwenden Sie die `Force` Parameter vereinfacht den Vorgang. Jedoch, wenn der Benutzer keine Berechtigung zum Entfernen der Datei, die `Force` Parameter hat keine Auswirkungen.

### <a name="handle-credentials-through-windows-powershell-ad03"></a>Verarbeiten von Anmeldeinformationen mithilfe von Windows PowerShell (AD03)

Es sollte ein Cmdlet definieren eine `Credential` Parameter, um die Anmeldeinformationen dar. Dieser Parameter muss vom Typ [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) und muss mit einer Attributdeklaration Anmeldeinformationen definiert werden. Diese Unterstützung fordert den Benutzer für den Benutzernamen, Kennwort oder für beides automatisch, wenn vollständige Anmeldeinformationen nicht direkt angegeben ist. Weitere Informationen über die Anmeldeinformationen-Attribut finden Sie unter [Anmeldeinformationen Attributdeklaration](./credential-attribute-declaration.md).

### <a name="support-encoding-parameters-ad04"></a>Encoding-Parameter (AD04) unterstützt

Wenn Ihr Cmdlet liest oder schreibt Text ein, oder von einem binären Format, z. B. zu schreiben oder Lesen einer Datei in ein Dateisystem, muss Ihr Cmdlet Encoding-Parameter verfügen, der angibt, wie der Text in das Binärformat codiert ist.

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>Test-Cmdlets muss einen boolescher Wert (AD05) zurückgeben.

Cmdlets, die Tests für ihre Ressourcen ausführen sollte Zurückgeben einer [System.Boolean](/dotnet/api/System.Boolean) Geben Sie an die Pipeline, damit sie in bedingten Ausdrücken verwendet werden können.

## <a name="code-guidelines"></a>Coderichtlinien

Die folgenden Richtlinien berücksichtigen Sie beim Schreiben von Cmdlet-Code. Wenn Sie eine Richtlinie, die auf Ihren Fall zutrifft finden, achten Sie darauf, dass Sie die Entwurfsrichtlinien für ähnliche Richtlinien ansehen.

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>Führen Sie die Cmdlet-Klasse-Benennungskonventionen (AC01)

Durch folgenden Standardbenennungskonventionen Sie Ihre Cmdlets leichter auffindbar machen und Ihnen helfen, dass der Benutzers vertraut, genau die-Cmdlets. Diese Vorgehensweise ist besonders wichtig für andere Entwickler, die mithilfe von Windows PowerShell, da Cmdlets öffentlichen Typen sind.

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>Definieren Sie ein Cmdlet in den richtigen Namespace

Normalerweise definieren Sie die Klasse für ein Cmdlet in einen .NET Framework-Namespace, der angefügt ". Befehle"auf den Namespace, der das Produkt darstellt, in dem das Cmdlet ausgeführt wird. Z. B. Cmdlets, die mit Windows PowerShell enthalten sind definiert sind, der `Microsoft.PowerShell.Commands` Namespace.

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>Nennen Sie die Cmdlet-Klasse mit dem Cmdlet-Namen übereinstimmen

Beim Benennen von .NET Framework-Klasse, die ein Cmdlet implementiert, nennen Sie die Klasse "*\<Verb >**\<Nomen >**\<Befehl >*", in dem Sie die Ersetzen *\<Verb >* und  *\<Nomen >* Platzhalter mit dem Verb und Substantiv für den cmdletnamen verwendet. Z. B. die [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet wird implementiert, indem eine Klasse namens `GetProcessCommand`.

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>Wenn keine Pipelineeingabe der BeginProcessing-Methode (AC02) überschreiben

Wenn Ihr Cmdlet keine Eingaben aus der Pipeline annimmt, sollte Verarbeitung implementiert werden, der [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) Methode. Mit dieser Methode können Windows PowerShell zum Verwalten der Reihenfolge für die Cmdlets. Das erste Cmdlet in der Pipeline gibt immer die Objekte zurück, bevor die verbleibenden-Cmdlets in der Pipeline ihrer Verarbeitung gestartet werden.

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>Stop-Anforderungen außer Kraft setzen die StopProcessing-Methode (AC03) behandelt.

Überschreiben der [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) Methode, damit Ihr Cmdlet stoppsignal behandeln kann. Einige Cmdlets lange dauern, den Vorgang abzuschließen, und sie viel Zeit zwischen den Aufrufen der Windows PowerShell-Laufzeit, wie z. B. wenn das-Cmdlet den Thread im RPC-Aufrufe für lang andauernde blockiert übergeben können. Dazu gehören Cmdlets, die Aufrufe an die [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) Methode in der [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode und anderes Feedback die Mechanismen, die eine lange Zeit in Anspruch nehmen können. In diesen Fällen kann der Benutzer muss ein stoppsignal für diese Cmdlets zu senden.

### <a name="implement-the-idisposable-interface-ac04"></a>Implementieren der IDisposable-Schnittstelle (AC04)

Wenn Ihr Cmdlet Objekte, die nicht entfernt werden (in der Pipeline geschrieben) hat, indem die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode, Ihr Cmdlet unter Umständen zusätzliche Objekt Freigabe. Wenn Ihr Cmdlet ein Dateihandle im öffnet z. B. die [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -Methode und behält den Bügel zu öffnen, für die Verwendung durch die [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode, muss dieses Handle an das Ende der Verarbeitung abgeschlossen werden.

Die Windows PowerShell-Laufzeit ruft nicht immer die [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Methode. Z. B. die [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Methode kann nicht aufgerufen werden, wenn das Cmdlet Zielpfads durch den Vorgang abgebrochen wird oder wenn ein Abbruch tritt Fehler in einem beliebigen Teil des Cmdlets auf. Aus diesem Grund sollten die .NET Framework-Klasse für ein Cmdlet aus, die Bereinigung Objekte erfordert die vollständige implementieren [System.IDisposable](/dotnet/api/System.IDisposable) Muster "Dienstschnittstelle", einschließlich des Finalizers, der, damit die Windows PowerShell-Laufzeit sowohl aufrufen kann die [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) und [System.IDisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) Methoden am Ende der Verarbeitung.

### <a name="use-serialization-friendly-parameter-types-ac05"></a>Verwenden Sie die Serialisierung geeignet Parametertypen (AC05)

Verwenden Sie zum Ausführen Ihres Cmdlets auf Remotecomputern, Typen, die leicht auf dem Clientcomputer serialisiert, und klicken Sie dann auf dem Servercomputer aktiviert werden können. Die folgenden Typen sind Serialisierung geeignet.

Primitive Typen:

- Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32, und UInt64.

- Boolean, Guid, Byte [], TimeSpan, DateTime, Uri und Version.

- Char-Zeichen, Zeichenfolge XmlDocument.

Integrierte rehydratable Typen:

- PSPrimitiveDictionary

- SwitchParameter

- PSListModifier

- PSCredential

- IPAddress, MailAddress

- CultureInfo

- X509Certificate2, X500DistinguishedName

- DirectorySecurity, FileSecurity, RegistrySecurity

Andere Typen:

- SecureString

- Containern (Listen und Wörterbücher von den oben genannten Typ)

### <a name="use-securestring-for-sensitive-data-ac06"></a>Verwenden von SecureString für vertrauliche Daten (AC06)

Verwenden Sie beim Behandeln von sensibler Daten immer die [System.Security.Securestring](/dotnet/api/System.Security.SecureString) -Datentyp. Dazu gehören die Pipelineeingabe Parameter sowie die sensible Daten an die Pipeline zurückgeben.

## <a name="see-also"></a>Weitere Informationen

[Richtlinien für die Entwicklung von erforderlich](./required-development-guidelines.md)

[Richtlinien für die Entwicklung von dringend empfohlen](./strongly-encouraged-development-guidelines.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
