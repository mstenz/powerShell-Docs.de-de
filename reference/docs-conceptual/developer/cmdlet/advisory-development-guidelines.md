---
title: Leitfaden für die Empfehlung zur Entwicklung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 980b488800587e31286e2ca2ece924e07f8af3f3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370039"
---
# <a name="advisory-development-guidelines"></a>Empfohlene Entwicklungsrichtlinien

In diesem Abschnitt werden Richtlinien beschrieben, die Sie berücksichtigen sollten, um eine gute Entwicklung und Benutzerfreundlichkeit sicherzustellen. Manchmal können Sie angewendet werden, und manchmal nicht.

## <a name="design-guidelines"></a>Entwurfs Richtlinien

Beim Entwerfen von Cmdlets sollten die folgenden Richtlinien berücksichtigt werden. Wenn Sie eine Entwurfsrichtlinie finden, die für Ihre Situation gilt, sollten Sie sich die Code Richtlinien für ähnliche Richtlinien ansehen.

### <a name="support-an-inputobject-parameter-ad01"></a>Unterstützung eines Inputobject-Parameters (ad01)

Da Windows PowerShell direkt mit Microsoft .NET Framework-Objekten arbeitet, ist häufig ein .NET Framework Objekt verfügbar, das genau mit dem Typ übereinstimmt, den der Benutzer zum Ausführen eines bestimmten Vorgangs benötigt. `InputObject` ist der Standardname für einen Parameter, der ein solches Objekt als Eingabe annimmt. Beispielsweise definiert das Beispiel **Stop-proc-** Cmdlet im [stopproc-Tutorial](./stopproc-tutorial.md) einen `InputObject`-Parameter des Typs Process, der die Eingabe aus der Pipeline unterstützt. Der Benutzer kann einen Satz von Prozess Objekten erhalten, ihn bearbeiten, um die genauen Objekte auszuwählen, die beendet werden sollen, und Sie dann direkt an das Cmdlet "Set **-proc** " übergeben.

### <a name="support-the-force-parameter-ad02"></a>Unterstützen des Force-Parameters (ad02)

Gelegentlich muss ein Cmdlet den Benutzer vor der Ausführung eines angeforderten Vorgangs schützen. Ein derartiges Cmdlet sollte einen `Force`-Parameter unterstützen, um dem Benutzer zu ermöglichen, diesen Schutz zu überschreiben, wenn der Benutzer über Berechtigungen zum Ausführen des Vorgangs verfügt.

Beispielsweise entfernt das [Remove-Item-](/powershell/module/microsoft.powershell.management/remove-item) Cmdlet normalerweise keine schreibgeschützte Datei. Dieses Cmdlet unterstützt jedoch einen `Force`-Parameter, damit ein Benutzer das Entfernen einer schreibgeschützten Datei erzwingen kann. Wenn der Benutzer bereits über die Berechtigung zum Ändern des schreibgeschützten Attributs verfügt und der Benutzer die Datei entfernt, vereinfacht die Verwendung des Parameters "`Force`" den Vorgang. Wenn der Benutzer jedoch nicht über die Berechtigung zum Entfernen der Datei verfügt, hat der Parameter "`Force`" keine Auswirkung.

### <a name="handle-credentials-through-windows-powershell-ad03"></a>Behandeln von Anmelde Informationen über Windows PowerShell (AD03)

Ein Cmdlet muss einen `Credential`-Parameter definieren, um die Anmelde Informationen darzustellen. Dieser Parameter muss vom Typ " [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) " sein und muss mithilfe der Deklaration eines Credential-Attributs definiert werden. Durch diese Unterstützung wird der Benutzer automatisch zur Eingabe des Benutzernamens, des Kennworts oder für beides aufgefordert, wenn keine vollständigen Anmelde Informationen direkt bereitgestellt werden. Weitere Informationen zum Credential-Attribut finden Sie unter [Credential Attribute Declaration](./credential-attribute-declaration.md).

### <a name="support-encoding-parameters-ad04"></a>Unterstützen von Codierungs Parametern (AD04)

Wenn das Cmdlet Text in oder aus einer Binärdatei liest oder in ein Binärformat schreibt (z. b. Schreiben in eine Datei in einem Dateisystem), muss das Cmdlet über einen Codierungs Parameter verfügen, der angibt, wie der Text im Binärformat codiert wird.

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>Test-Cmdlets sollten einen booleschen Wert zurückgeben (AD05).

Cmdlets, die Tests für Ihre Ressourcen durchführen, sollten einen [System. Boolean](/dotnet/api/System.Boolean) -Typ an die Pipeline zurückgeben, damit Sie in bedingten Ausdrücken verwendet werden können.

## <a name="code-guidelines"></a>Code Richtlinien

Beim Schreiben von Cmdlet-Code sollten die folgenden Richtlinien berücksichtigt werden. Wenn Sie eine Richtlinie finden, die für Ihre Situation gilt, sollten Sie sich die Entwurfs Richtlinien für ähnliche Richtlinien ansehen.

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>Befolgen Sie die Cmdlet-Benennungs Konventionen (AC01).

Durch die folgenden Standard Benennungs Konventionen machen Sie Ihre Cmdlets leichter auffindbar, und Sie unterstützen den Benutzer dabei, genau zu verstehen, was die Cmdlets tun. Diese Vorgehensweise ist besonders wichtig für andere Entwickler, die Windows PowerShell verwenden, da es sich bei Cmdlets um öffentliche Typen handelt.

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>Definieren eines Cmdlets im richtigen Namespace

Normalerweise definieren Sie die-Klasse für ein Cmdlet in einem .NET Framework Namespace, der "" anfügt. Befehle "für den Namespace, der das Produkt darstellt, in dem das Cmdlet ausgeführt wird. Beispielsweise werden Cmdlets, die in Windows PowerShell enthalten sind, im `Microsoft.PowerShell.Commands`-Namespace definiert.

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>Benennen Sie die Cmdlet-Klasse mit dem Namen des Cmdlets.

Wenn Sie die .NET Framework Klasse benennen, die ein Cmdlet implementiert, benennen Sie die Klasse " *\<verb > **\<noun >** \<command >* ", wobei Sie das *\<verb >* und *\<noun >* Platzhalter durch ersetzen. das Verb und das Substantiv, die für den Cmdlet-Namen verwendet werden. Das [Get-Process-](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet wird z. b. von einer Klasse mit dem Namen `GetProcessCommand` implementiert.

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>Wenn keine Pipeline Eingabe die BeginProcessing-Methode außer Kraft setzt (AC02)

Wenn das Cmdlet keine Eingaben aus der Pipeline annimmt, sollte die Verarbeitung in der [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -Methode implementiert werden. Die Verwendung dieser Methode ermöglicht Windows PowerShell, die Reihenfolge zwischen Cmdlets beizubehalten. Das erste Cmdlet in der Pipeline gibt immer seine Objekte zurück, bevor die restlichen Cmdlets in der Pipeline die Möglichkeit haben, ihre Verarbeitung zu starten.

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>Überschreiben Sie die StopProcessing-Methode (AC03), um Stopp Anforderungen zu verarbeiten.

Überschreiben Sie die [System. Management. Automation. Cmdlet. StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) -Methode, damit das Cmdlet das Stoppsignal verarbeiten kann. Einige Cmdlets nehmen lange Zeit in Anspruch, und Sie ermöglichen eine lange Zeit zwischen Aufrufen der Windows PowerShell-Laufzeit, z. b. wenn das Cmdlet den Thread in lang andauernden RPC-Aufrufen blockiert. Dies schließt Cmdlets ein, die Aufrufe an die [System. Management. Automation. Cmdlet. Write Object](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) -Methode, an die [System. Management. Automation. Cmdlet. Write-error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode und an andere Feedback Mechanismen machen, die möglicherweise viel Zeit in Anspruch nehmen. . In diesen Fällen muss der Benutzer möglicherweise ein Stoppsignal an diese Cmdlets senden.

### <a name="implement-the-idisposable-interface-ac04"></a>Implementieren der iverwerfbaren Schnittstelle (AC04)

Wenn das Cmdlet Objekte enthält, die nicht von der [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode verworfen (in die Pipeline geschrieben) werden, benötigt das Cmdlet möglicherweise eine zusätzliche Objekt Beseitigung. Wenn das Cmdlet z. b. ein Datei Handle in der [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -Methode öffnet und das Handle für die Verwendung durch die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode offen hält, muss dieses handle geschlossen am Ende der Verarbeitung.

Von der Windows PowerShell-Laufzeit wird nicht immer die [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode aufgerufen. Beispielsweise kann die [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode nicht aufgerufen werden, wenn das Cmdlet in der Mitte durch den Vorgang abgebrochen wird oder wenn in einem beliebigen Teil des Cmdlets ein Abbruch Fehler auftritt. Daher sollte die .NET Framework-Klasse für ein Cmdlet, das die Objekt Bereinigung erfordert, das gesamte [System. iverwerfbare](/dotnet/api/System.IDisposable) Schnittstellen Muster implementieren, einschließlich des Finalizers, damit die Windows PowerShell-Laufzeit beide [ System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -und [System. iverwerf. verwerfen *](/dotnet/api/System.IDisposable.Dispose) -Methoden am Ende der Verarbeitung.

### <a name="use-serialization-friendly-parameter-types-ac05"></a>Verwenden von serialisierungsfreundlichen Parameter Typen (AC05)

Um das Ausführen des Cmdlets auf Remote Computern zu unterstützen, verwenden Sie Typen, die auf dem Client Computer leicht serialisiert und dann auf dem Server Computer aktiviert werden können. Die folgenden Typen sind serialisierungsfreundlich.

Primitive Typen:

- Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, UInt16, UInt32 und UInt64.

- Boolean, Guid, Byte [], TimeSpan, DateTime, URI und Version.

- Char, String, XmlDocument.

Integrierte, verteilbare Typen:

- Psprientschärvedictionary

- Switch

- Pslistmodifier

- PSCredential

- IPAddress, Mail Address

- CultureInfo

- X509Certificate2, X500DistinguishedName

- Directoriysecurity, File Security, RegistrySecurity

Andere Typen:

- SecureString

- Container (Listen und Wörterbücher des obigen Typs)

### <a name="use-securestring-for-sensitive-data-ac06"></a>Verwenden von SecureString für sensible Daten (AC06)

Verwenden Sie bei der Behandlung sensibler Daten stets den Datentyp [System. Security. SecureString](/dotnet/api/System.Security.SecureString) . Dies kann die Pipeline Eingabe für Parameter und die Rückgabe von sensiblen Daten an die Pipeline einschließen.

## <a name="see-also"></a>Weitere Informationen

[Erforderliche Entwicklungs Richtlinien](./required-development-guidelines.md)

[Stark unterstützt Entwicklungs Richtlinien](./strongly-encouraged-development-guidelines.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
