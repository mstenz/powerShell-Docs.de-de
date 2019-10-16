---
title: Hinzufügen von Aliasen, Platzhalter Erweiterungen und Hilfe zu Cmdlet-Parametern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: bc921537062e35aa203fa3ee95d3b7211c89cb28
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370089"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>Hinzufügen von Aliasen, Platzhaltererweiterung und Hilfe zu Cmdlet-Parametern

In diesem Abschnitt wird beschrieben, wie Aliase, Platzhalter Erweiterung und Hilfe Meldungen den Parametern des Cmdlets "-Beendigung-proc" hinzugefügt werden (siehe [Erstellen eines Cmdlets, das das System ändert](./creating-a-cmdlet-that-modifies-the-system.md)).

Dieses Cmdlet "Pause-proc" versucht, Prozesse zu unterbinden, die mithilfe des Cmdlets "Get-proc" abgerufen werden (siehe [Erstellen des ersten Cmdlets](./creating-a-cmdlet-without-parameters.md)).

## <a name="defining-the-cmdlet"></a>Definieren des Cmdlets

Der erste Schritt bei der Cmdlet-Erstellung ist die Benennung des Cmdlets und das Deklarieren der .NET-Klasse, die das Cmdlet implementiert. Da Sie ein Cmdlet schreiben, um das System zu ändern, sollte es entsprechend benannt werden. Da dieses Cmdlet System Prozesse stoppt, wird das Verb "Stopp", das von der [System. Management. Automation. verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) -Klasse definiert wird, mit dem Substantiv "proc" verwendet, um den Prozess anzugeben. Weitere Informationen zu genehmigten Cmdlet-Verben finden Sie unter [Cmdlet-Verb Namen](./approved-verbs-for-windows-powershell-commands.md).

Der folgende Code stellt die Klassendefinition für dieses Cmdlet "Pause-proc" dar.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definieren von Parametern für die System Änderung

Ihr Cmdlet muss Parameter definieren, die Systemänderungen und Benutzer Feedback unterstützen. Mit dem-Cmdlet sollte ein `Name`-Parameter oder eine-Entsprechung definiert werden, damit das Cmdlet das System mit einer Art von Bezeichner ändern kann. Außerdem sollte das Cmdlet die Parameter "`Force`" und "`PassThru`" definieren. Weitere Informationen zu diesen Parametern finden Sie unter [Erstellen eines Cmdlets, das das System ändert](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="defining-a-parameter-alias"></a>Definieren eines parameteralias

Ein parameteralias kann ein alternativer Name oder ein gut definierter Kurzname mit einem oder zwei Buchstaben für einen Cmdlet-Parameter sein. In beiden Fällen besteht das Ziel der Verwendung von Aliasen darin, den Benutzereintrag von der Befehlszeile aus zu vereinfachen. Windows PowerShell unterstützt Parameter Aliase über das [System. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) -Attribut, das die Deklarations Syntax [Alias ()] verwendet.

Der folgende Code zeigt, wie dem `Name`-Parameter ein Alias hinzugefügt wird.

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

Zusätzlich zur Verwendung des [System. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) -Attributs führt die Windows PowerShell-Laufzeit eine partielle namens Übereinstimmung aus, auch wenn keine Aliase angegeben werden. Wenn das Cmdlet z. b. über einen `FileName`-Parameter verfügt und der einzige Parameter ist, der mit `F` beginnt, kann der Benutzer `Filename`, `Filenam`, `File`, `Fi` oder `F` eingeben und den Eintrag weiterhin als `FileName`-Parameter erkennen.

## <a name="creating-help-for-parameters"></a>Erstellen von Hilfe für Parameter

Mit Windows PowerShell können Sie Hilfe für Cmdlet-Parameter erstellen. Verwenden Sie dies für alle Parameter, die für die Systemänderung und das Benutzer Feedback verwendet werden. Für jeden Parameter, der die Hilfe unterstützt, können Sie das Attribut "`HelpMessage`" in der Attribut Deklaration " [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) " festlegen. Dieses Schlüsselwort definiert den Text, der dem Benutzer zur Unterstützung bei der Verwendung des-Parameters angezeigt werden soll. Sie können auch das `HelpMessageBaseName`-Schlüsselwort festlegen, um den Basis Namen einer Ressource zu identifizieren, die für die Nachricht verwendet werden soll. Wenn Sie dieses Schlüsselwort festlegen, müssen Sie auch das `HelpMessageResourceId`-Schlüsselwort festlegen, um den Ressourcen Bezeichner anzugeben.

Der folgende Code aus diesem Cmdlet "halte-proc" definiert das Attribut Schlüsselwort "`HelpMessage`" für den Parameter "`Name`".

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

## <a name="overriding-an-input-processing-method"></a>Überschreiben einer Eingabe Verarbeitungsmethode

Ihr Cmdlet muss eine Eingabe Verarbeitungsmethode überschreiben, meistens handelt es sich hierbei um [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Wenn Sie das System ändern, sollte das Cmdlet die Methoden " [System. Management. Automation. Cmdlet. schuldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) " und " [System. Management. Automation. Cmdlet.-dcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) " anrufen, damit der Benutzer Feedback bereitstellen kann, bevor eine Änderung vorgenommen wird. Weitere Informationen zu diesen Methoden finden Sie unter [Erstellen eines Cmdlets, das das System ändert](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="supporting-wildcard-expansion"></a>Unterstützung für Platzhalter

Um die Auswahl mehrerer Objekte zu ermöglichen, kann das Cmdlet die Klassen " [System. Management. Automation. wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) " und " [System. Management. Automation. wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) " verwenden, um die Unterstützung für Platzhalter Erweiterungen für Parameter Eingaben bereitzustellen. Beispiele für Platzhalter Muster sind LSA *, @no__t -0. txt und [a-c] \*. Verwenden Sie das backanführungs Zeichen (') als Escapezeichen, wenn das Muster ein Zeichen enthält, das buchstäblich verwendet werden soll.

Platzhalter Erweiterungen von Datei-und Pfadnamen sind Beispiele für gängige Szenarien, in denen das Cmdlet möglicherweise die Unterstützung von Pfad Eingaben zulässt, wenn die Auswahl mehrerer Objekte erforderlich ist. Häufig wird das Dateisystem angezeigt, in dem ein Benutzer alle Dateien im aktuellen Ordner anzeigen möchte.

Sie sollten eine angepasste Platzhalter Muster Vergleichs Implementierung nur selten benötigen. In diesem Fall sollte Ihr Cmdlet entweder die vollständige POSIX 1003,2-und 3,13-Spezifikation für die Platzhalter Erweiterung oder die folgende vereinfachte Teilmenge unterstützen:

- **Fragezeichen (?).** Entspricht einem beliebigen Zeichen an der angegebenen Position.

- **Sternchen (\*).** Entspricht 0 (null) oder mehr Zeichen, beginnend an der angegebenen Position.

- **Öffnende eckige Klammer ([).** Führt einen Muster Klammer Ausdruck ein, der Zeichen oder einen Zeichenbereich enthalten kann. Wenn ein Bereich erforderlich ist, wird ein Bindestrich (-) verwendet, um den Bereich anzugeben.

- **Schließende Klammer (]).** Beendet einen Muster Klammer Ausdruck.

- **Escape-Escapezeichen (').** Gibt an, dass das nächste Zeichen wörtlich genommen werden soll. Beachten Sie, dass bei der Angabe des backanführungs Zeichens von der Befehlszeile aus (im Gegensatz zur programmgesteuerten Angabe) das Escapezeichen für das Back-End zweimal angegeben werden muss.

> [!NOTE]
> Weitere Informationen zu Platzhalter Mustern finden Sie [unter unterstützen von Platzhaltern in Cmdlet-Parametern](./supporting-wildcard-characters-in-cmdlet-parameters.md).

Der folgende Code zeigt, wie Sie Platzhalter Optionen festlegen und das Platzhalter Muster definieren, das zum Auflösen des Parameters "`Name`" für dieses Cmdlet verwendet wird.

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

Der folgende Code zeigt, wie Sie überprüfen, ob der Prozess Name mit dem definierten Platzhalter Muster übereinstimmt. Beachten Sie, dass in diesem Fall, wenn der Prozess Name nicht mit dem Muster identisch ist, das Cmdlet fortgesetzt wird, um den nächsten Prozessnamen zu erhalten.

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>Code Beispiel

Den gesamten C# Beispielcode finden Sie unter [StopProcessSample03 Sample](./stopprocesssample03-sample.md).

## <a name="define-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

Windows PowerShell übergibt Informationen zwischen Cmdlets mithilfe von .NET-Objekten. Folglich muss ein Cmdlet möglicherweise seinen eigenen Typ definieren, oder das Cmdlet muss möglicherweise einen vorhandenen Typ erweitern, der von einem anderen Cmdlet bereitgestellt wird. Weitere Informationen zum Definieren neuer Typen oder zum Erweitern vorhandener Typen finden Sie unter [Erweitern von Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Cmdlet wird aufgebaut

Nachdem ein Cmdlet implementiert wurde, muss es über ein Windows PowerShell-Snap-in in Windows PowerShell registriert werden. Weitere Informationen zum Registrieren von Cmdlets finden [Sie unter Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Testen des Cmdlets

Wenn das Cmdlet bei Windows PowerShell registriert wurde, können Sie es in der Befehlszeile testen. Testen Sie das Beispiel-Cmdlet "Stopp-proc". Weitere Informationen zur Verwendung von Cmdlets über die Befehlszeile finden Sie unter [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Starten Sie Windows PowerShell, und verwenden Sie "Ende-proc", um einen Prozess mit dem "ProcessName"-Alias für den Parameter "`Name`"

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

- Legen Sie den folgenden Eintrag in der Befehlszeile ab. Da der Name-Parameter obligatorisch ist, werden Sie dazu aufgefordert. Eingabe von "!?" Ruft den Hilfetext auf, der dem-Parameter zugeordnet ist.

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

- Führen Sie nun den folgenden Eintrag aus, um alle Prozesse anzuhalten, die dem Platzhalter Muster "* Note @ no__t-0" entsprechen. Sie werden dazu aufgefordert, jeden Prozess anzuhalten, der mit dem Muster übereinstimmt.

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

[Erstellen Sie ein Cmdlet, das das System ändert.](./creating-a-cmdlet-that-modifies-the-system.md)

[Erstellen eines Windows PowerShell-Cmdlets](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Erweitern von Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85))

[Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions//ms714644(v=vs.85))

[Unterstützen von Platzhaltern in Cmdlet-Parametern](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
