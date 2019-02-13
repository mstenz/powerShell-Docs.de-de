---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,service,setup
title: Schreiben, Kompilieren und Anwenden einer Konfiguration
ms.openlocfilehash: fa4d98fd12202439ba7025fd8af3fa398653ca05
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677840"
---
> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="write-compile-and-apply-a-configuration"></a>Schreiben, Kompilieren und Anwenden einer Konfiguration

Diese Übung führt Sie von Anfang bis Ende durch das Erstellen und Anwenden einer Desired State Configuration (DSC)-Konfiguration.
Im folgenden Beispiel erfahren Sie, wie zum Schreiben und eine sehr einfache Konfiguration anwenden. Die Konfiguration wird Stellen Sie sicher, dass eine Datei "HelloWorld.txt" auf dem lokalen Computer vorhanden ist. Wenn Sie die Datei löschen, werden DSC es das nächste Mal neu erstellt, die, das Sie aktualisiert.

Eine Übersicht über DSC und wie es funktioniert, finden Sie unter [Desired State Configuration-Übersicht für Entwickler](../overview/overview.md).

## <a name="requirements"></a>Anforderungen

Um dieses Beispiel auszuführen, benötigen Sie einen Computer mit PowerShell 4.0 oder höher.

## <a name="write-the-configuration"></a>Schreiben der Konfiguration

Eine DSC-[Konfiguration](configurations.md) ist eine spezielle PowerShell-Funktion, die definiert, wie Sie einen oder mehrere Zielcomputer (Knoten) konfigurieren möchten.

Geben Sie in der PowerShell ISE oder andere PowerShell-Editor Folgendes ein:

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

Speichern Sie die Datei als "HelloWorld.ps1".

Definieren eine Konfiguration ist wie eine Funktion definieren. Der **Node**-Block gibt den zu konfigurierenden Zielknoten an, in diesem Fall `localhost`.

Ruft die Konfiguration einer [Ressourcen](../resources/resources.md), `File` Ressource. Ressourcen stellen sicher, dass sich der Zielknoten im durch die Konfiguration definierten Zustand befindet.

## <a name="compile-the-configuration"></a>Kompilieren der Konfiguration

Damit eine DSC-Konfiguration auf einem Knoten angewendet werden kann, muss sie zunächst in eine MOF-Datei kompiliert werden.
Ausführen der Konfiguration, wie eine Funktion kann für jeden Knoten, die definiert, die von einem "MOF"-Datei kompiliert die `Node` Block.
Um die Konfiguration ausgeführt werden, müssen Sie *Punkt als Stammelement* Ihr Skript "HelloWorld.ps1" in den aktuellen Bereich.
Weitere Informationen finden Sie unter [About_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).

*Punkt als Stammelement* Ihr Skript "HelloWorld.ps1" Geben Sie in den Pfad, in dem Sie, nachdem gespeichert, die `. ` (Punkt, Speicherplatz). Anschließend können Sie Ihre Konfiguration ausführen, indem Sie es wie eine Funktion aufrufen.

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

Die folgende Ausgabe wird generiert:

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>Anwenden der Konfiguration

Nun, da Sie die kompilierte MOF-Dateien haben, können Sie die Konfiguration auf den Zielknoten (in diesem Fall der lokale Computer) anwenden, indem Sie das Cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aufrufen.

Die `Start-DscConfiguration` Cmdlet fordert den [lokalen Konfigurations-Manager (LCM)](../managing-nodes/metaConfig.md), der Engine für DSC, um die Konfiguration anzuwenden.
Der LCM übernimmt das Aufrufen der DSC-Ressourcen, um die Konfiguration anzuwenden.

Verwenden Sie den folgenden Code zum Ausführen der `Start-DSCConfiguration` Cmdlet. Geben Sie den Directory-Pfad, in Ihrer "localhost.mof", um gespeichert ist, die `-Path` Parameter. Die `Start-DSCConfiguration` Cmdlet durchsucht den für eine angegebene Verzeichnis "\<Computername\>.mof" Dateien. Die `Start-DSCConfiguration` Cmdlet versucht, jede "MOF"-Datei gefundenen auf den Computernamen, angegeben durch den Dateinamen ("Localhost", "server01", "dc-02" usw.) anwenden.

> [!NOTE]
> Wenn die `-Wait` Parameter nicht angegeben ist, `Start-DSCConfiguration` erstellt einen Hintergrundauftrag, um den Vorgang auszuführen. Angeben der `-Verbose` Parameter können Sie sehen Sie sich die **ausführlich** Ausgabe des Vorgangs. `-Wait`, und `-Verbose` sind beide optionale Parameter.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>Testen der Konfiguration

Sobald die `Start-DSCConfiguration` Cmdlet abgeschlossen ist, sollte eine "HelloWorld.txt"-Datei im angegebenen Speicherort. Sie können überprüfen, ob die Inhalte mit der [Get-Content](/powershell/module/microsoft.powershell.management/get-content) Cmdlet.

Sie können auch *testen* den aktuellen Status mit [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

Die Ausgabe sollte "True" sein, wenn der Knoten derzeit mit den angewendeten Konfiguration kompatibel ist.

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a>Erneutes Anwenden der Konfigurations

Zum Anzeigen Ihrer Konfiguration erneut angewendet werden, können Sie die Textdatei wird von Ihrer Konfiguration entfernen. Die Verwendung der `Start-DSCConfiguration` Cmdlet mit dem `-UseExisting` Parameter. Die `-UseExisting` -Parameter weist `Start-DSCConfiguration` um die Datei "current.mof" erneut anzuwenden, die zuletzt erfolgreich steht Konfiguration angewendet.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Nächste Schritte

- Weiteren Informationen zu DSC-Konfigurationen erhalten Sie unter [DSC-Konfigurationen](configurations.md).
- Welche DSC-Ressourcen verfügbar sind und wie Sie benutzerdefinierte DSC-Ressourcen erstellen erfahren Sie unter [DSC-Ressourcen](../resources/resources.md).
- DSC-Konfigurationen und -Ressourcen finden Sie unter [PowerShell-Katalog](https://www.powershellgallery.com/).
