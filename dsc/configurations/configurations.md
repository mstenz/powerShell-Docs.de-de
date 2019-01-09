---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: DSC-Konfigurationen
ms.openlocfilehash: 6af27f442de3080facd65892c713c989d0e388c5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401448"
---
# <a name="dsc-configurations"></a>DSC-Konfigurationen

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC-Konfigurationen sind PowerShell-Skripts, die eine besondere Art von Funktion definieren.
Zum Definieren einer Konfiguration verwenden Sie das PowerShell-Schlüsselwort **Configuration**.

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

Speichern Sie das Skript eine `.ps1` Datei.

## <a name="configuration-syntax"></a>Konfigurationssyntax

Ein Konfigurationsskript besteht aus den folgenden Teilen:

- Dem **Configuration**-Block. Dies ist die äußerste Skriptblock. Sie definieren ihn mithilfe des Schlüsselworts **Configuration** und der Angabe eines Namens. In diesem Fall lautet der Name der Konfiguration „MyDscConfiguration“.
- Mindestens einem **Node**-Block. Diese Blöcke definieren die Knoten (Computer oder VMs), die Sie konfigurieren. Bei der obigen Konfiguration gibt es einen **Node**-Block für den Computer „TEST-PC1“. Der "Node"-Block kann mehrere Computernamen akzeptieren.
- Mindestens einen Ressourcenblock. In diesen Blöcken werden die Eigenschaften der Ressourcen festlegt, die konfiguriert werden. In diesem Fall gibt es zwei Ressourcenblöcke, die beide die Ressource „WindowsFeature“ aufrufen.

Innerhalb eines **Configuration**-Blocks sind alle Aktionen möglich, die Sie normalerweise mit einer PowerShell-Funktion ausführen. Wenn Sie beispielsweise im vorherigen Beispiel den Namen des Zielcomputers nicht in der Konfiguration hart codieren möchten, können Sie einen Parameter für den Knotennamen hinzufügen:

In diesem Beispiel geben Sie den Namen des Knotens an, indem Sie ihn als **ComputerName**-Parameter übergeben, wenn Sie die Konfiguration kompilieren. Der Standardname ist „localhost“.

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

Die **Knoten** Block kann auch mehrere Computernamen akzeptieren. Im obigen Beispiel können Sie entweder die `-ComputerName` Parameter oder übergeben Sie eine durch Trennzeichen getrennte Liste der Computer direkt die **Knoten** Block.

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

Wenn Sie eine Liste von Computern zum Angeben der **Knoten** Block von innerhalb einer Konfiguration müssen Sie mithilfe der Arraynotation.

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a>Kompilieren der Konfiguration

Bevor Sie eine Konfiguration anwenden können, müssen Sie sie in einem MOF-Dokument kompilieren.
Dazu rufen Sie die Konfiguration wie eine PowerShell-Funktion auf.
Die letzte Zeile des Beispiels, die nur den Namen der Konfiguration enthält, ruft die Konfiguration auf.

> [!NOTE]
> Damit eine Konfiguration aufgerufen werden kann, muss sie sich (wie jede andere PowerShell-Funktion) im globalen Bereich befinden.
> Dies erfolgt, indem Sie das Skript mit „Dot-Sourcing“ ausführen oder das Konfigurationsskript durch Drücken von F5 oder Klicken auf die Schaltfläche **Skript ausführen** in der integrierte Skriptumgebung starten.
> Um das Skript mit „Dot-Sourcing“ ausführen, rufen Sie den Befehl `. .\myConfig.ps1` auf, wobei `myConfig.ps1` der Name der Skriptdatei mit Ihrer Konfiguration ist.

Beim Aufruf der Konfiguration erfolgt Folgendes:

- Alle Variablen werden aufgelöst.
- Im aktuellen Verzeichnis wird ein Ordner mit dem Namen der Konfiguration erstellt.
- Eine Datei namens _NodeName.mof_ wird im neuen Verzeichnis erstellt, wobei _NodeName_ der Name des Zielknotens der Konfiguration ist.
  Wenn mehrere Knoten vorhanden ist, wird eine MOF-Datei für jeden Knoten erstellt werden.

> [!NOTE]
> Die MOF-Datei enthält alle Konfigurationsinformationen für den Zielknoten. Aus diesem Grund ist es wichtig, sie geschützt zu halten.
> Weitere Informationen finden Sie unter [Schützen der MOF-Datei](../pull-server/secureMOF.md).

Das Kompilieren der ersten oben gezeigten Konfiguration führt zur folgenden Ordnerstruktur:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

Wenn die Konfiguration wie im zweiten Beispiel einen Parameter verwendet, muss dieser zur Kompilierungszeit angegeben werden. Das sieht dann so aus:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a>Verwenden neuer Ressourcen in Ihrer Konfiguration

Wenn Sie die vorherigen Beispielen ausgeführt haben, werden Sie vielleicht die Warnung bemerkt haben, dass Sie eine Ressource verwendet haben, ohne sie explizit zu importieren.
Derzeit gehören 12 Ressourcen zum Funktionsumfang von DSC im „PSDesiredStateConfiguration“-Modul.

Das Cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) kann verwendet werden, um zu bestimmen, welche Ressourcen im System installiert sind und dem LCM zur Verfügung stehen.
Nachdem diese Module in `$env:PSModulePath` abgelegt und von [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) ordnungsgemäß erkannt wurden, müssen sie dennoch in Ihre Konfiguration geladen werden.

**Import-DscResource** ist ein dynamisches Schlüsselwort, das nur in erkannt wird eine **Konfiguration** blockieren, es kein Cmdlet ist.
**Import-DscResource** unterstützt zwei Parameter:

- **ModuleName** ist die empfohlene Methode der Verwendung von **Import DscResource**. Dieser Parameter akzeptiert den Namen des Moduls mit den Ressourcen, die importiert werden sollen, (sowie einem Zeichenfolgenarray mit Modulnamen).
- **Name** ist der Name der zu importierenden Ressource. Dies ist nicht der Anzeigename, der als „Name“ von [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) zurückgegeben wird, sondern der Klassennamen, der verwendet wird, wenn Sie das Ressourcenschema definieren (wird als **ResourceType** von [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) zurückgegeben).

Weitere Informationen zur Verwendung von `Import-DSCResource`, finden Sie unter [mithilfe von Import-DSCResource](import-dscresource.md)

## <a name="powershell-v4-and-v5-differences"></a>PowerShell-v4- und v5-Unterschiede

Es gibt Unterschiede in der, in denen DSC-Ressourcen müssen in PowerShell 4.0 gespeichert werden. Weitere Informationen finden Sie unter [Ressourcenspeicherort](import-dscresource.md#resource-location).

## <a name="see-also"></a>Weitere Informationen

- [Windows PowerShell DSC – Übersicht](../overview/overview.md)
- [DSC-Ressourcen](../resources/resources.md)
- [Konfigurieren des lokalen Konfigurations-Managers](../managing-nodes/metaConfig.md)
