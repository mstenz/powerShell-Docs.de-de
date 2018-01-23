---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Desired State Configuration Schnellstart
ms.openlocfilehash: e21017f24db8c90229063895c1a7e4c6f0546d0c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="desired-state-configuration-quick-start"></a>Desired State Configuration Schnellstart

Diese Übung führt Sie von Anfang bis Ende durch das Erstellen und Anwenden einer Desired State Configuration (DSC)-Konfiguration.
Das Beispiel, das wir verwenden, stellt sicher, dass ein Server die `Web-Server` (IIS)-Funktion aktiviert hat und der Inhalt für eine einfache „Hello World“-Website ist im Verzeichnis `intepub\wwwroot` des Servers vorhanden ist.

Eine Übersicht über DSC und die Funktionsweise finden Sie unter [Desired State Configuration (DSC): Übersicht für Entscheidungsträger](decisionMaker.md).

## <a name="requirements"></a>Anforderungen

Sie benötigen einen Computer mit Windows Server 2012 oder höher und mit PowerShell 4.0 oder höher, um dieses Beispiel auszuführen.

## <a name="write-and-place-the-indexhtm-file"></a>Schreiben und Platzieren der Datei „Index.htm“

Zunächst erstellen wir die HTML-Datei, die wir als Website-Inhalt verwenden werden.

Erstellen Sie in Ihrem Stammordner einen Ordner namens `test`.

Geben Sie in einem Text-Editor den folgenden Text ein:

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

Speichern Sie dies als `index.htm` in den Ordner `test`, den Sie zuvor erstellt haben. 

## <a name="write-the-configuration"></a>Schreiben der Konfiguration

Eine [DSC-Konfiguration](configurations.md) ist eine spezielle PowerShell-Funktion, die definiert, wie Sie einen oder mehrere Zielcomputer (Knoten) konfigurieren möchten.

Geben Sie in der PowerShell ISE Folgendes ein:

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

Speichern Sie die Datei unter dem Namen `WebsiteTest.ps1`.

Sie sehen, dass sie wie eine PowerShell-Funktion aussieht und zusätzlich das Schlüsselworts **Configuration** enthält, welches vor dem Namen der Funktion verwendet wurde.

Der **Node**-Block gibt den zu konfigurierenden Zielknoten an, in diesem Fall `localhost`.

Die Konfiguration ruft zwei [Ressourcen](resources.md) auf, [WindowsFeature](windowsFeatureResource.md) und [File](fileResource.md).
Ressourcen stellen sicher, dass sich der Zielknoten im durch die Konfiguration definierten Zustand befindet.

## <a name="compile-the-configuration"></a>Kompilieren der Konfiguration

Damit eine DSC-Konfiguration auf einem Knoten angewendet werden kann, muss sie zunächst in eine MOF-Datei kompiliert werden.
Hierzu führen Sie die Konfiguration wie eine Funktion aus.
Wechseln Sie in einer PowerShell-Konsole in den gleichen Ordner, in dem Sie die Konfiguration gespeichert haben, und führen Sie die folgenden Befehle aus, um die Konfiguration in eine MOF-Datei zu kompilieren:

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

Die folgende Ausgabe wird generiert:

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

Die erste Zeile macht die Konfigurationsfunktion in der Konsole verfügbar.
In der zweiten Zeile wird die Konfiguration ausgeführt.
Dies bedeutet, dass ein neuer Ordner mit dem Namen `WebsiteTest` als Unterordner des aktuellen Ordners erstellt wird.
Der Ordner `WebsiteTest` enthält eine Datei mit dem Namen `localhost.mof`.
Diese Datei, kann dann auf den Zielknoten angewendet werden.

## <a name="apply-the-configuration"></a>Anwenden der Konfiguration

Nun, da Sie die kompilierte MOF-Dateien haben, können Sie die Konfiguration auf den Zielknoten (in diesem Fall der lokale Computer) anwenden, indem Sie das Cmdlet [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration) aufrufen.

Das `Start-DscConfiguration` fordert den [lokalen Konfigurations-Manager (Local Configuration Manager – LCM)](metaConfig.md), das DSC-Modul, auf, die Konfiguration anzuwenden.
Der LCM übernimmt das Aufrufen der DSC-Ressourcen, um die Konfiguration anzuwenden.

Wechseln Sie in einer PowerShell-Konsole in den gleichen Ordner, in dem Sie die Konfiguration gespeichert haben, und führen Sie den folgenden Befehl aus:

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>Testen der Konfiguration

Sie können das Cmdlet [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus), aufrufen, um zu überprüfen, ob die Konfiguration erfolgreich war. 

Sie können die Ergebnisse auch direkt testen, in diesem Fall durch Aufrufen von `http://localhost/` in einem Webbrowser.
Es sollte die „Hello World“-HTML-Seite angezeigt werden, die Sie im ersten Schritt dieses Beispiels erstellt haben.

## <a name="next-steps"></a>Nächste Schritte

- Weiteren Informationen zu DSC-Konfigurationen erhalten Sie unter [DSC-Konfigurationen](configurations.md).
- Welche DSC-Ressourcen verfügbar sind und wie Sie benutzerdefinierte DSC-Ressourcen erstellen erfahren Sie unter [DSC-Ressourcen](resources.md).
- DSC-Konfigurationen und -Ressourcen finden Sie unter [PowerShell-Katalog](https://www.powershellgallery.com/).



