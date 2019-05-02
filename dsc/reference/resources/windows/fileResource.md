---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „File“
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077329"
---
# <a name="dsc-file-resource"></a>DSC-Ressource „File“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource „File“ in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten von Dateien und Verzeichnissen auf einem Zielknoten. Der Zielknoten muss auf **DestinationPath** und **SourcePath** zugreifen können.

## <a name="syntax"></a>Syntax

```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a>Eigenschaften

|Eigenschaft       |Beschreibung                                                                   |Erforderlich|Standardwert|
|---------------|------------------------------------------------------------------------------|--------|-------|
|DestinationPath|Der Speicherort auf dem Zielknoten, den Sie sicherstellen möchten, ist `Present` oder `Absent`.|Ja|Nein|
|Attributes     |Der gewünschte Status der Attribute der Zieldatei oder des Zielverzeichnisses. Gültige Werte sind **Archive**, **Hidden**, **ReadOnly** und **System**.|Nein|Keine|
|Checksum      |Der zu verwendende Prüfsummentyp, wenn bestimmt wird, ob zwei Dateien identisch sind. Gültige Werte: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.|Nein|Nur der Datei- oder Verzeichnisname wird verglichen.|
|Contents       |Nur bei der Verwendung mit `File`-Typ gültig. Gibt den Inhalt an, von dem sichergestellt werden soll (Ensure), ob er in der Zieldatei vorhanden (`Present`) oder nicht vorhanden (`Absent`) ist. |Nein|Keine|
|Credential     |Die Anmeldeinformationen, die für den Zugriff auf Ressourcen wie z.B. Quelldateien erforderlich sind.|Nein|Das Computerkonto des Zielknotens. (*Siehe Hinweis*)|
|Ensure         |Der gewünschte Zustand von Zieldatei oder -verzeichnis. |Nein|**Vorhanden**|
|Force          |Setzt bestimmte Zugriffsoperationen außer Kraft, die zu einem Fehler führen würden (z.B. das Überschreiben einer Datei oder Löschen eines Verzeichnisses, das nicht leer ist).|Nein|`$false`|
|Recurse        |Nur bei der Verwendung mit `Directory`-Typ gültig. Führt den Statusvorgang rekursiv für alle Unterverzeichnisse aus.|Nein|`$false`|
|DependsOn      |Legt auf angegebenen Ressourcen eine Abhängigkeit fest. Diese Ressource wird nur nach erfolgreicher Ausführung aller abhängigen Ressourcen ausgeführt. Sie können abhängige Ressourcen mit der Syntax `"[ResourceType]ResourceName"` angeben. Weitere Informationen finden Sie unter [about_DependsOn](../../../configurations/resource-depends-on.md).|Nein|Keine|
|SourcePath     |Der Pfad, aus dem die Datei- oder Ordnerressource kopiert werden soll.|Nein|Keine|
|Type           |Der Typ der zu konfigurierenden Ressource. Gültige Werte sind `Directory` und `File`.|Nein|`File`|
|MatchSource    |Bestimmt, ob die Ressource überwachen sollte, ob dem Quellverzeichnis nach der ersten Kopie neue Dateien hinzugefügt werden. Der Wert `$true` gibt an, dass nach Erstellen der ersten Kopie alle neuen Quelldateien in das Ziel kopiert werden sollten. Bei Festlegung auf `$False` speichert die Ressource den Inhalt des Quellverzeichnisses zwischen und ignoriert alle Dateien, die nach der ersten Kopie hinzugefügt werden.|Nein|`$false`|

> [!WARNING]
> Wenn Sie keinen Wert für `Credential` oder `PSRunAsCredential` (PS V.5) angeben, greift die Ressource mithilfe des Computerkontos des Zielknotens auf den `SourcePath` zu.  Wenn der `SourcePath` eine UNC-Freigabe ist, könnte dies zu einem „Zugriff verweigert“-Fehler führen. Vergewissern Sie sich, dass Ihre Berechtigungen entsprechend festgelegt sind, oder verwenden Sie die Eigenschaften `Credential` oder `PSRunAsCredential`, um das Konto anzugeben, das verwendet werden sollte.

## <a name="present-vs-absent"></a>„Present“ im Vergleich zu „Absent“

Jede DSC-Ressource führt auf Grundlage des Werts, den Sie für die `Ensure`-Eigenschaft angeben, verschiedene Vorgänge aus. Die Werte, die Sie für die oben aufgeführten Eigenschaften angeben, bestimmen den ausgeführten Statusvorgang.

### <a name="existence"></a>Vorhandensein

Wenn Sie nur einen `DestinationPath` angeben, stellt die Ressource sicher, ob der Pfad vorhanden (`Present`) oder nicht vorhanden ist (`Absent`).

### <a name="copy-operations"></a>Kopiervorgänge

Wenn Sie einen `SourcePath` und einen `DestinationPath` mit dem `Type`-Wert **Directory** angeben, kopiert die Ressource das Quellverzeichnis in den Zielpfad. Die Eigenschaften `Recurse`, `Force` und `MatchSource` ändern den Typ des ausgeführten Kopiervorgangs, während `Credential` bestimmt, welches Konto zum Zugriff auf das Quellverzeichnis verwendet wird.

### <a name="limitations"></a>Einschränkungen

Wenn Sie den Wert `ReadOnly` für die `Attributes`-Eigenschaft zusammen mit einem `DestinationPath` angeben würden, würde `Ensure = "Present"` den angegebene Pfad erstellen, während `Contents` den Inhalt der Datei festlegen würde.  Ein `Absent`-Statusvorgang würde die `Attributes`-Eigenschaft vollständig ignorieren und jede Datei im angegebenen Pfad entfernen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden ein Verzeichnis und seine Unterverzeichnisse unter Verwendung der Ressource „File“ von einem Pullserver auf einen Zielknoten kopiert. Wenn der Vorgang erfolgreich ist, schreibt die Ressource „Log“ eine Bestätigungsmeldung in das Ereignisprotokoll.

Das Quellverzeichnis ist ein auf dem Pullserver freigegebener UNC-Pfad (`\\PullServer\DemoSource`). Die `Recurse`-Eigenschaft gewährleistet, dass auch alle Unterverzeichnisse kopiert werden.

> [!IMPORTANT]
> Der LCM auf dem Zielknoten wird standardmäßig im Kontext des lokalen Systemkontos ausgeführt. Um Zugriff auf den **SourcePath** zu gewähren, erteilen Sie dem Computerkonto des Zielknotens entsprechende Berechtigungen. **Credential** und **PSDSCRunAsCredential** (v5) ändern beide den Kontext, den der LCM für den Zugriff auf den **SourcePath** verwendet. Sie müssen weiterhin Zugriff auf das Konto gewähren, das für den Zugriff auf den **SourcePath** verwendet wird.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

Weitere Informationen zur Verwendung von **Credentials** in DSC finden Sie unter [Verwenden von Anmeldeinformationen mit DSC-Ressourcen](../../../configurations/runAsUser.md) oder [Optionen für Anmeldeinformationen in den Konfigurationsdaten](../../../configurations/configDataCredentials.md).
