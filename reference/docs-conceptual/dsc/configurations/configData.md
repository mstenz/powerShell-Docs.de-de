---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Verwenden von Konfigurationsdaten
ms.openlocfilehash: 7d13b19ba932d1a818194a221f145fd1a3832547
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954187"
---
# <a name="using-configuration-data-in-dsc"></a>Verwenden von Konfigurationsdaten in DSC

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Mithilfe des integrierten DSC-Parameters **ConfigurationData** können Sie Daten definieren, die innerhalb einer Konfiguration verwendet werden können.
Dadurch können Sie eine einzige Konfiguration erstellen, die für mehrere Knoten oder für unterschiedliche Umgebungen verwendet werden kann.
Wenn Sie z.B. eine Anwendung entwickeln, können Sie eine Konfiguration für die Entwicklungs-und die Produktionsumgebung verwenden und mithilfe von Konfigurationsdaten Daten für jede Umgebung angeben.

In diesem Thema wird die Struktur der Hashtabelle **ConfigurationData** beschrieben.
Beispiele zur Verwendung von Konfigurationsdaten finden Sie unter [Trennen von Konfigurations- und Umgebungsdaten](separatingEnvData.md).

## <a name="the-configurationdata-common-parameter"></a>Der allgemeine Parameter „ConfigurationData“

Eine DSC-Konfiguration umfasst einen allgemeinen Parameter namens **ConfigurationData**, den Sie beim Kompilieren der Konfiguration angeben.
Informationen zum Kompilieren von Konfigurationen finden Sie unter [DSC-Konfigurationen](configurations.md).

Der Parameter **ConfigurationData** ist eine Hashtabelle, die mindestens einen Schlüssel namens **AllNodes** benötigt.
Die Hashtabelle kann außerdem noch weitere Schlüssel umfassen.

> [!NOTE]
> In den Beispielen in diesem Artikel wird (neben dem Schlüssel **AllNodes**) nur ein einziger zusätzlicher Schlüssel verwendet. Dieser trägt den Namen `NonNodeData`. Sie können jedoch eine beliebige Anzahl zusätzlicher Schlüssel verwenden und diese nach Wunsch benennen.

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

Der Wert des **AllNodes**-Schlüssels ist ein Array. Jedes Element dieses Arrays ist ebenfalls eine Hashtabelle, die mindestens einen Schlüssel namens **NodeName** benötigt:

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

Sie können jeder Hashtabelle auch andere Schlüssel hinzufügen:

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

Um allen Knoten eine Eigenschaft zuzuweisen, können Sie ein Member des **AllNodes**-Arrays erstellen, dessen **NodeName** gleich `*` ist.
Verwenden Sie z.B. folgenden Code, um allen Knoten die Eigenschaft `LogPath` zuzuweisen:

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

Dies entspricht dem Hinzufügen einer Eigenschaft namens `LogPath` mit einem Wert `"C:\Logs"` zu jedem der anderen Blöcke (`VM-1`, `VM-2` und `VM-3`).

## <a name="defining-the-configurationdata-hashtable"></a>Definieren der ConfigurationData-Hashtabelle

Sie können **ConfigurationData** entweder als eine Variable innerhalb derselben Skriptdatei als Konfiguration (wie in unseren bisherigen Beispielen) oder in einer separaten `.psd1`-Datei definieren.
Erstellen Sie zum Definieren von **ConfigurationData** in einer `.psd1`-Datei eine Datei, die nur die Hashtabelle enthält, die die Konfigurationsdaten darstellt.

Sie könnten z.B. eine Datei namens `MyData.psd1` mit folgendem Inhalt erstellen:

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a>Kompilieren einer Konfiguration mit Konfigurationsdaten

Um eine Konfiguration zu kompilieren, für die Sie Konfigurationsdaten definiert haben, übergeben Sie die Konfigurationsdaten als Wert des Parameters **ConfigurationData**.

Auf diese Weise wird für jeden Eintrag im **AllNodes**-Array eine MOF-Datei erstellt.
Jede MOF-Datei wird nach der `NodeName`-Eigenschaft des zugehörigen Arrayeintrags benannt.

Wenn Sie beispielsweise Konfigurationsdaten wie in der vorstehenden `MyData.psd1`-Datei definieren, werden beim Kompilieren einer Konfiguration sowohl `VM-1.mof`- als auch `VM-2.mof`-Dateien erstellt.

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>Kompilieren einer Konfiguration mit Konfigurationsdaten unter Verwendung einer Variablen

Um Konfigurationsdaten zu verwenden, die in derselben `.ps1`-Datei wie die Konfiguration als Variable definiert sind, übergeben Sie den Variablennamen beim Kompilieren der Konfiguration als Wert des Parameters **ConfigurationData**:

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>Kompilieren einer Konfiguration mit Konfigurationsdaten unter Verwendung einer Datendatei

Um Konfigurationsdaten zu verwenden, die in einer PSD1-Datei definiert sind, übergeben Sie Pfad und Namen der Datei bei der Kompilierung der Konfiguration als Wert des Parameters **ConfigurationData**:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>Verwenden von ConfigurationData-Variablen in einer Konfiguration

DSC stellt die folgenden speziellen Variablen bereit, die in einem Skript verwendet werden können:

- **$AllNodes** bezieht sich auf die gesamte, in **ConfigurationData** definierte Knotensammlung. Sie können die **AllNodes**-Sammlung mit **.Where()** und **.ForEach()** filtern.
- **ConfigurationData** bezieht sich auf die gesamte Hashtabelle, die beim Kompilieren einer Konfiguration als Parameter übergeben wird.
- **MyTypeName** enthält den [Namen der Konfiguration](configurations.md), in der die Variable verwendet wird. In der Konfiguration `MyDscConfiguration` weist `$MyTypeName` beispielsweise den Wert `MyDscConfiguration` auf.
- **Nodes** bezieht sich auf einen bestimmten Eintrag in der **AllNodes**-Sammlung, nachdem sie mithilfe von **.Where()** oder **.ForEach()** gefiltert wurde.
  - Weitere Informationen zu diesen Methoden finden Sie unter [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays).

## <a name="using-non-node-data"></a>Verwenden von Daten ohne Knoten

Wie wir in den vorherigen Beispielen gesehen haben, kann die Hashtabelle **ConfigurationData** neben dem erforderlichen Schlüssel **AllNodes** weitere Schlüssel aufweisen.
In den Beispielen in diesem Thema wurde nur ein einziger zusätzlicher Knoten namens `NonNodeData` verwendet.
Sie können jedoch eine beliebige Anzahl von zusätzlichen Schlüsseln definieren und diese nach Wunsch benennen.

Ein Beispiel für die Verwendung von Nicht-Knotendaten finden Sie unter [Trennen von Konfigurations- und Umgebungsdaten](separatingEnvData.md).

## <a name="see-also"></a>Weitere Informationen

- [Optionen für Anmeldeinformationen in den Konfigurationsdaten](configDataCredentials.md)
- [DSC-Konfigurationen](configurations.md)