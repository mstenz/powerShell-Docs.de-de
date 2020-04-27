---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC-Ressource „File“
ms.openlocfilehash: 4c6945d4cdcbc64ac6d52db563823efe8fd0247e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954677"
---
# <a name="dsc-file-resource"></a>DSC-Ressource „File“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.x

Die Ressource **File** in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten von Dateien und Verzeichnissen auf einem Zielknoten. Der Zielknoten muss auf **DestinationPath** und **SourcePath** zugreifen können.

## <a name="syntax"></a>Syntax

```Syntax
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschaften

|Eigenschaft |BESCHREIBUNG |
|---|---|
|DestinationPath |Der Speicherort auf dem Zielknoten, den Sie sicherstellen möchten, ist **Present** oder **Absent** mit **Ensure**. |
|Attributes |Der gewünschte Status der Attribute der Zieldatei oder des Zielverzeichnisses. Gültige Werte sind _Archive_, _Hidden_, _ReadOnly_ und _System_. |
|Checksum |Der zu verwendende Prüfsummentyp, wenn bestimmt wird, ob zwei Dateien identisch sind. Gültige Werte: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**. |
|Contents |Nur bei Verwendung mit **Type** **File** gültig. Gibt den Inhalt an, von dem sichergestellt werden soll (**Ensure**), ob er in der Zieldatei vorhanden (**Present**) oder nicht vorhanden (**Absent**) ist. |
|Anmeldeinformationen |Die Anmeldeinformationen, die für den Zugriff auf Ressourcen wie z.B. Quelldateien erforderlich sind. |
|Force |Setzt bestimmte Zugriffsoperationen außer Kraft, die zu einem Fehler führen würden (z.B. das Überschreiben einer Datei oder Löschen eines Verzeichnisses, das nicht leer ist). Der Standardwert ist `$false`. |
|Recurse |Nur bei Verwendung mit **Type** **Directory** gültig. Führt den Statusvorgang rekursiv für alle Unterverzeichnisse aus. Der Standardwert ist `$false`. |
|SourcePath |Der Pfad, aus dem die Datei- oder Ordnerressource kopiert werden soll. |
|type |Der Typ der zu konfigurierenden Ressource. Gültige Werte sind **Directory** und **File**. Der Standardwert ist **File**. |
|MatchSource |Bestimmt, ob die Ressource überwachen sollte, ob dem Quellverzeichnis nach der ersten Kopie neue Dateien hinzugefügt werden. Der Wert `$true` gibt an, dass nach Erstellen der ersten Kopie alle neuen Quelldateien in das Ziel kopiert werden sollten. Bei Festlegung auf `$false` speichert die Ressource den Inhalt des Quellverzeichnisses zwischen und ignoriert alle Dateien, die nach der ersten Kopie hinzugefügt werden. Der Standardwert ist `$false`. |

> [!WARNING]
> Wenn Sie keinen Wert für **Credential** oder **PSRunAsCredential** angeben, greift die Ressource mithilfe des Computerkontos des Zielknotens auf den **SourcePath** zu. Wenn der **SourcePath** eine UNC-Freigabe ist, könnte dies zu einem „Zugriff verweigert“-Fehler führen. Vergewissern Sie sich, dass Ihre Berechtigungen entsprechend festgelegt sind, oder verwenden Sie die **Credential** bzw. **PSRunAsCredential**, um das Konto anzugeben, das verwendet werden sollte.

## <a name="common-properties"></a>Allgemeine Eigenschaften

|Eigenschaft |BESCHREIBUNG |
|---|---|
|DependsOn |Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Legt fest, ob die Datei und Inhalte (**Contents**) am Ziel (**Destination**) vorhanden sein sollen oder nicht. Legen Sie diese Eigenschaft auf **Present** fest, um sicherzustellen, dass die Datei vorhanden ist. Legen Sie sie auf **Absent** fest, um sicherzustellen, dass der Inhalt nicht vorhanden ist. Der Standardwert ist **Present**. |
|PsDscRunAsCredential |Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest. |

> [!NOTE]
> Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen. Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).

### <a name="additional-information"></a>Zusätzliche Informationen

- Wenn Sie nur einen Zielpfad (**DestinationPath**) angeben, stellt die Ressource sicher, ob der Pfad vorhanden (**Present**) oder nicht vorhanden ist (**Absent**).
- Wenn Sie einen Quellpfad **SourcePath** und einen Zielpfad (**DestinationPath**) mit dem **Type**-Wert **Directory** angeben, kopiert die Ressource das Quellverzeichnis in den Zielpfad. Die Eigenschaften **Recurse**, **Force** und **MatchSource** ändern den Typ des ausgeführten Kopiervorgangs, während **Credential** bestimmt, welches Konto für den Zugriff auf das Quellverzeichnis verwendet wird.
- Wenn Sie den Wert von **ReadOnly** für die Eigenschaft **Attributes** gemeinsam mit einem Zielpfad (**DestinationPath**) angegeben haben, wird mit der Einstellung **Ensure** **Present** der angegebene Pfad erstellt, während mit **Contents** die Inhalte der Datei festgelegt werden. Bei der Einstellung **Ensure** **Absent** würde die **Attributes**-Eigenschaft vollständig ignoriert und jede Datei im angegebenen Pfad entfernt.

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden ein Verzeichnis und seine Unterverzeichnisse unter Verwendung der Ressource „File“ von einem Pullserver auf einen Zielknoten kopiert. Wenn der Vorgang erfolgreich ist, schreibt die Ressource „Log“ eine Bestätigungsmeldung in das Ereignisprotokoll.

Das Quellverzeichnis ist ein auf dem Pullserver freigegebener UNC-Pfad (`\\PullServer\DemoSource`). Die **Recurse**-Eigenschaft gewährleistet, dass auch alle Unterverzeichnisse kopiert werden.

> [!IMPORTANT]
> Der LCM auf dem Zielknoten wird standardmäßig im Kontext des lokalen Systemkontos ausgeführt. Um Zugriff auf den **SourcePath** zu gewähren, erteilen Sie dem Computerkonto des Zielknotens entsprechende Berechtigungen. **Credential** und **PSDSCRunAsCredential** ändern beide den Kontext, den der LCM für den Zugriff auf den **SourcePath** verwendet. Sie müssen weiterhin Zugriff auf das Konto gewähren, das für den Zugriff auf den **SourcePath** verwendet wird.

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