---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „File“
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679297"
---
# <a name="dsc-file-resource"></a>DSC-Ressource „File“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource „File“ in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten von Dateien und Verzeichnissen auf einem Zielknoten. Die **DestinationPath** und **SourcePath** müssen vom Ziel Knoten zugegriffen werden kann.

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
|DestinationPath|Der Speicherort, auf dem Zielknoten Sie sicherstellen möchten, ist `Present` oder `Absent`.|Ja|Nein|
|Attributes     |Der gewünschte Zustand der Attribute für die Zieldatei oder das Verzeichnis. Gültige Werte sind **Archiv**, **Hidden**, **ReadOnly**, und **System**.|Nein|Keine|
|Checksum      |Der Checksum-Typ, mit denen Sie bestimmen, ob zwei Dateien identisch sind. Gültige Werte sind: SHA-1, SHA-256, SHA-512, CreatedDate, ModifiedDate.|Nein|Nur die Datei oder Verzeichnis Namen verglichen wird.|
|Contents       |Nur gültig, bei der Verwendung mit `File` Typ. Gibt an, den Inhalt, stellen Sie sicher sind `Present` oder `Absent` aus der entsprechenden Datei. |Nein|Keine|
|Credential     |Die Anmeldeinformationen, die erforderlich, um den Zugriff auf Ressourcen, wie z.B. Quelldateien sind.|Nein|Computerkonto für des Zielknotens. (*Siehe Hinweis*)|
|Ensure         |Der gewünschte Zustand der Zieldatei oder des Verzeichnisses. |Nein|**Vorhanden**|
|Force          |Überschreibt die Access-Vorgänge, die zu einem Fehler (z. B. das Überschreiben einer Datei oder das Löschen eines Verzeichnisses, das nicht leer ist) führen würde.|Nein|`$false`|
|Recurse        |Nur gültig, bei der Verwendung mit `Directory` Typ. Führt die Status-Vorgang rekursiv für alle Unterverzeichnisse.|Nein|`$false`|
|DependsOn      |Legt eine Abhängigkeit auf der angegebenen Ressourcen fest. Diese Ressource wird nur nach erfolgreicher Ausführung aller abhängigen Ressourcen ausgeführt. Sie können angeben, dass abhängige Ressourcen, die mit der Syntax `"[ResourceType]ResourceName"`. Finden Sie unter [About_DependsOn](../../../configurations/resource-depends-on.md)|Nein|Keine|
|SourcePath     |Der Pfad, von dem die Datei oder Ordner kopiert werden soll.|Nein|Keine|
|Type           |Der Typ der zu konfigurierende Ressource. Gültige Werte sind `Directory` und `File`.|Nein|`File`|
|MatchSource    |Bestimmt, ob die Ressource für neue Dateien, die zum Quellverzeichnis hinzugefügt werden, nachdem die erste Kopie überwachen soll. Der Wert `$true` gibt an, dass nach Erstellen der ersten Kopie aller neuen Quelldateien in das Ziel kopiert werden sollen. Wenn auf festgelegt `$False`, die Ressource speichert den Inhalt des Quellverzeichnisses und ignoriert alle Dateien hinzugefügt, nachdem die erste Kopie.|Nein|`$false`|

> [!WARNING]
> Wenn Sie einen Wert für nicht angeben `Credential` oder `PSRunAsCredential` (PS V.5), die Ressource wird mithilfe des Computerkontos des Zielknotens auf die `SourcePath`.  Wenn die `SourcePath` ist eine UNC-Freigabe, könnte dies zu einem Fehler "Zugriff verweigert". Vergewissern Sie sich Ihre Berechtigungen werden entsprechend festgelegt wird, oder verwenden Sie die `Credential` oder `PSRunAsCredential` Eigenschaften für das Konto angeben, die verwendet werden soll.

## <a name="present-vs-absent"></a>Stellen Sie die Visual Studio. Nicht vorhanden

Jede DSC-Ressource führt verschiedene Vorgänge, die auf Grundlage des Werts, die Sie, für angeben die `Ensure` Eigenschaft. Die Werte, die Sie angeben, für die oben aufgeführten Eigenschaften bestimmt den Status-Vorgang ausgeführt.

### <a name="existence"></a>Vorhandensein

Wenn Sie nur angeben, ein `DestinationPath`, die Ressource wird sichergestellt, dass der Pfad vorhanden ist (`Present`) oder ist nicht vorhanden (`Absent`).

### <a name="copy-operations"></a>Kopiervorgänge

Beim Angeben von eine `SourcePath` und ein `DestinationPath` mit einer `Type` Wert **Directory**, das Ressourcenverzeichnis für die Quelle von Kopien in den Zielpfad. Die Eigenschaften `Recurse`, `Force`, und `MatchSource` ändern Sie den Typ des Kopiervorgangs ausgeführt, während er sich `Credential` bestimmt, welches Konto Sie verwenden, um das Quellverzeichnis zuzugreifen.

### <a name="limitations"></a>Einschränkungen

Wenn Sie den Wert angegeben `ReadOnly` für die `Attributes` Eigenschaft zusammen mit einer `DestinationPath`, `Ensure = "Present"` würde den angegebene Pfad erstellen während `Contents` würde Legen Sie den Inhalt der Datei.  Ein `Absent` Zustands ignorieren würde die `Attributes` Eigenschaft vollständig, und entfernen Sie alle Dateien im angegebenen Pfad.

## <a name="example"></a>Beispiel

Das folgende Beispiel kopiert ein Verzeichnis und seinen Unterverzeichnissen von einem pullserver auf einen Zielknoten, die mit der Ressource "File". Wenn der Vorgang erfolgreich ist, schreibt die Ressource "Log" eine bestätigungsmeldung angezeigt, in das Ereignisprotokoll geschrieben.

Das Quellverzeichnis ist ein UNC-Pfad (`\\PullServer\DemoSource`) aus dem Pull-Server freigegeben. Die `Recurse` Eigenschaft wird sichergestellt, dass auch alle Unterverzeichnisse kopiert werden.

> [!IMPORTANT]
> Der LCM auf dem Ziel Knoten führt standardmäßig im Kontext des lokalen Systemkontos aus. Gewähren von Zugriff auf die **SourcePath**, legen Sie Berechtigungen für das Computerkonto des Zielknotens. Die **Anmeldeinformationen** und **"psdscrunascredential"** (v5) Ändern der Kontext der LCM verwendet den Zugriff auf die **SourcePath**. Müssen Sie weiterhin Zugriff auf das Konto zu gewähren, die verwendet werden, für den Zugriff auf die **SourcePath**.

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

Für die weitere Verwendung von auf **Anmeldeinformationen** in DSC finden Sie unter [als Benutzer ausführen](../../../configurations/runAsUser.md) oder [Config Anmeldeinformationen](../../../configurations/configDataCredentials.md).
