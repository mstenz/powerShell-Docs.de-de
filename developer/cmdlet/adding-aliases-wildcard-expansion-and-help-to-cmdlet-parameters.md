---
title: Hinzufügen von Platzhaltererweiterung, Aliase und Cmdlet-Parameter sollte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: 946b71e4480a47ac6ccd6930be445d7efb4fb62d
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854892"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>Hinzufügen von Aliasen, Platzhaltererweiterung und Hilfe zu Cmdlet-Parametern

In diesem Abschnitt wird beschrieben, wie Aliase, platzhaltererweiterung, hinzufügen und Hilfe von Nachrichten an die Parameter des Cmdlets Stop-Prozessor (beschrieben [ein Cmdlets zu erstellen, ändert das System](./creating-a-cmdlet-that-modifies-the-system.md)).

Dieses Cmdlet Stop-Prozessor versucht, Sie Prozesse beenden, die mit dem Get-Proc-Cmdlet abgerufen werden (beschrieben [Erstellen Ihrer ersten Cmdlet](./creating-a-cmdlet-without-parameters.md)).

## <a name="defining-the-cmdlet"></a>Definieren das Cmdlet

Der erste Schritt bei der Cmdlet-Erstellung ist immer benennen das Cmdlet und .NET implementiert die Klasse, mit dem-Cmdlet deklarieren. Da Sie ein Cmdlet aus, um das System ändern, schreiben, sollten sie entsprechend benannt werden. Da dieses Cmdlet Systemprozesse beendet wird, verwendet es das Verb "Stop", definiert durch die [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) Klasse, mit dem Namen "Proc" an Prozess. Weitere Informationen zu zulässigen Cmdlet-Verben, finden Sie unter [Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md).

Der folgende Code ist die Definition der Klasse für dieses Cmdlet Stop-Prozessor.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definieren von Parametern für die System-Änderung

Ihr Cmdlet muss Parameter, die Unterstützung von Änderungen und Feedback von Benutzern zu definieren. Sollte das Cmdlet definieren eine `Name` Parameter oder einer entsprechenden Gruppe, damit das Cmdlet das System von einer bestimmten Art des Bezeichners ändern kann. Darüber hinaus sollte das Cmdlet definieren die `Force` und `PassThru` Parameter. Weitere Informationen zu diesen Parametern finden Sie unter [ein Cmdlets zu erstellen, ändert das System](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="defining-a-parameter-alias"></a>Definieren einen Parameteralias

Ein parameteralias kann es sich um einen alternativen Namen oder einen klar definierten Buchstaben 1 oder 2 Buchstaben Kurznamen für ein Cmdlet-Parameter sein. Das Ziel der using-Aliase werden in beiden Fällen Eintrag des Benutzers über die Befehlszeile zu vereinfachen. Windows PowerShell unterstützt parameteraliase über die [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) -Attribut, das die Syntax zum Deklarieren [Alias()] verwendet.

Der folgende Code zeigt, wie ein Alias hinzugefügt wird die `Name` Parameter.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

Zusätzlich zur Verwendung der [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) -Attribut, die Windows PowerShell-Laufzeit führt teilweise namensübereinstimmung, auch wenn keine Aliase angegeben werden. Wenn Ihr Cmdlet hat beispielsweise eine `FileName` Parameter und d. h. der einzige Parameter, die mit beginnt `F`, der Benutzer eingeben kann `Filename`, `Filenam`, `File`, `Fi`, oder `F` und erkennen Sie immer noch die Je nach den `FileName` Parameter.

## <a name="creating-help-for-parameters"></a>Hilfe für Parameter erstellen

Windows PowerShell können Sie Hilfe für Cmdlet-Parameter zu erstellen. Hierzu für jeden Parameter, die für die Änderung und der Benutzer Feedback zum plattformbenachrichtigungssystem verwendet. Für jeden Parameter, um Hilfe zu unterstützen, können Sie festlegen der `HelpMessage` Attribut-Schlüsselwort in der [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attributdeklaration. Dieses Schlüsselwort definiert, den Text, der den Benutzer zur Unterstützung bei der mit dem Parameter angezeigt wird. Sie können auch Festlegen der `HelpMessageBaseName` Schlüsselwort zum Identifizieren der Basisname der Ressource, für die Nachricht verwendet. Wenn Sie dieses Schlüsselwort festlegen, müssen Sie auch Festlegen der `HelpMessageResourceId` Schlüsselwort, um die Ressourcen-ID angeben.

Der folgende Code aus diesem Stop-Proc-Cmdlet definiert die `HelpMessage` Attribut-Schlüsselwort für die `Name` Parameter.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a>Überschreiben einer Eingabeverarbeitungsmethode

Ihr Cmdlet ein eingabeverarbeitungsmethode muss überschrieben werden, am häufigsten [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Wenn Sie das System ändern zu können, sollte das-Cmdlet Aufrufen der [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) und [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methoden, um dem Benutzer erlauben Um Feedback bereitzustellen, bevor eine Änderung vorgenommen wird. Weitere Informationen zu diesen Methoden finden Sie unter [ein Cmdlets zu erstellen, ändert das System](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="supporting-wildcard-expansion"></a>Unterstützung von Platzhaltererweiterung

Um die Auswahl mehrerer Objekte zu ermöglichen, Ihr Cmdlet verwenden, kann die [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) und [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) Klassen das Bereitstellen Unterstützung von Platzhalterzeichen-Erweiterung für den Parameter eingeben. Beispiele für Platzhaltermuster sind Lsa * \*txt- und [a-c]\*. Verwenden Sie das invertierte Hochkomma (') als Escapezeichen verwendet werden, wenn das Muster, ein Zeichen enthält, die buchstäblich verwendet werden soll.

Platzhalter-Erweiterungen von Datei-und Pfadnamen sind Beispiele für häufige Szenarien, in dem das Cmdlet sollten, um Unterstützung für Pfad Eingaben zu ermöglichen, wenn die Auswahl mehrerer Objekte erforderlich ist. Ein häufiges Szenario ist im Dateisystem, in denen ein Benutzer möchte auf alle Dateien im aktuellen Ordner finden Sie unter.

Sie sollten eine übereinstimmende benutzerdefinierte Platzhalter-Muster-Implementierung nur selten benötigen. In diesem Fall sollte Ihr Cmdlet entweder das vollständige POSIX 1003.2 wie 3,13 Spezifikation für die platzhaltererweiterung oder die folgende vereinfachte Teilmenge unterstützen:

- **Fragezeichen (?).** Entspricht jedem Zeichen an der angegebenen Position.

- **Sternchen (\*).** Entspricht null oder mehr Zeichen beginnend am angegebenen Speicherort.

- **Öffnende Klammer ([]).** Führt einen Klammerausdruck Muster, der Zeichen oder einen Bereich von Zeichen enthalten kann. Wenn ein Bereich erforderlich ist, wird ein Bindestrich (-) an, dass der Bereich verwendet.

- **Geschweiften Klammer (]).** Einen Klammerausdruck Muster wird beendet.

- **Back-Quote Escape-Zeichen (').** Gibt an, dass das nächste Zeichen Literal verwendet werden soll. Denken Sie beim Angeben der invertierte Hochkomma über die Befehlszeile (im Gegensatz zu programmgesteuert angeben) das Back-Quote Escapezeichen zweimal muss angegeben werden.

> [!NOTE]
> Weitere Informationen zu Platzhaltermustern finden Sie unter [unterstützen Platzhalter in der Cmdlet-Parameter](./supporting-wildcard-characters-in-cmdlet-parameters.md).

Der folgende Code zeigt, wie Platzhalteroptionen festlegen, und definieren das Platzhaltermuster verwendet für die Auflösung der `Name` -Parameter für dieses Cmdlet aus.

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

Der folgende Code zeigt die Vorgehensweise: testen, ob der Name des Prozesses der definierten Platzhaltermuster übereinstimmt. Beachten Sie, dass in diesem Fall, wenn der Name des Prozesses nicht mit das Muster übereinstimmt, das Cmdlet auf weiterhin den nächsten Prozessnamen abzurufen.

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>Codebeispiel

Für die vollständige C# Beispielcode, finden Sie unter [StopProcessSample03 Beispiel](./stopprocesssample03-sample.md).

## <a name="define-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

Windows PowerShell übergibt Informationen zwischen Cmdlets, die mithilfe von .NET-Objekten. Daher müssen möglicherweise ein Cmdlet seinen eigenen Typ definieren, oder das-Cmdlet zum Erweitern eines vorhandenen Typs, der durch ein anderes Cmdlet angegeben müssen. Weitere Informationen zum Definieren neuer Typen, oder erweitern vorhandene Typen finden Sie unter [Objekttypen erweitern und Formatierung](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Erstellen das Cmdlet

Nach der Implementierung eines Cmdlets, müssen sie über ein Windows PowerShell-Snap-in mit Windows PowerShell registriert werden. Weitere Informationen zum Registrieren von Cmdlets finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testen das Cmdlet

Wenn Ihr Cmdlet in Windows PowerShell registriert wurde, können Sie es testen, indem Sie sie in der Befehlszeile ausführen. Testen Sie nun das Beispiel beenden-Proc-Cmdlet. Weitere Informationen zur Verwendung von Cmdlets, über die Befehlszeile finden Sie unter den [erste Schritte mit Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Starten Sie Windows PowerShell, und verwenden Sie Stop-Proc beim Beenden eines Prozesses mit der ProcessName-Alias für die `Name` Parameter.

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

Die folgende Ausgabe wird angezeigt.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Nehmen Sie den folgenden Eintrag in der Befehlszeile ein. Da es sich bei der Name-Parameter obligatorisch ist, werden Sie dazu aufgefordert. Eingeben von "!" der Hilfetext, der dem Parameter zugeordnet wird.

    ```powershell
    PS> stop-proc
    ```

Die folgende Ausgabe wird angezeigt.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- Stellen Sie jetzt den folgenden Eintrag zum Beenden aller Prozesse, die das Platzhaltermuster entsprechen "* Hinweis\*". Sie werden aufgefordert, vor dem Beenden der einzelnen Prozesse mit dem Muster übereinstimmt.

    ```powershell
    PS> stop-proc -Name *note*
    ```

Die folgende Ausgabe wird angezeigt.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

Die folgende Ausgabe wird angezeigt.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

Die folgende Ausgabe wird angezeigt.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Weitere Informationen

[Erstellen Sie ein Cmdlet, das das System geändert wird](./creating-a-cmdlet-that-modifies-the-system.md)

[Vorgehensweise: Erstellen eines Windows PowerShell-Cmdlets](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Erweitern die Objekttypen und Formatierung](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Unterstützung von Platzhaltern in der Cmdlet-Parameter](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
