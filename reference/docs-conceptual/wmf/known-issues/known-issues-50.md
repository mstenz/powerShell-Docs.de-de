---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Bekannte Probleme in WMF 5.0
ms.openlocfilehash: 91f556cb43ef971107f05c4041b725b1c7e4f1bd
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71147740"
---
# <a name="known-issues-in-wmf-50"></a>Bekannte Probleme in WMF 5.0

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a>PowerShell-Verknüpfungen sind beim ersten Verwenden unterbrochen

**Lösung:** Führen Sie eine der folgenden Aktionen aus:

1. Klicken Sie mit der rechten Maustaste auf die PowerShell-Verknüpfung. Wählen Sie „Windows PowerShell“ aus, um in einem Modus ohne erhöhte Rechte zu starten.
2. Klicken Sie mit der rechten Maustaste auf die PowerShell-Verknüpfung. Klicken Sie mit der rechten Maustaste auf „Windows PowerShell“, und wählen Sie „Als Administrator ausführen“ aus, um im Modus mit erhöhten Rechten zu starten.

Nachdem Sie eine der oben aufgeführten Aktionen ausgeführt haben, funktionieren die PowerShell-Verknüpfungen. Diese Aktionen müssen nur einmal ausgeführt werden.

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a>PowerShell-Module und DSC-Ressourcen melden Fehler zu „ExecutionPolicy“ unter Windows 7

Unter Windows 7 kann die Verwendung von PowerShell-Modulen und DSC-Ressourcen zu Fehlern führen, die zu „ExecutionPolicy“ gemeldet werden.

**Lösung:** Legen Sie „ExecutionPolicy“ auf **RemoteSigned** fest, indem Sie den folgenden Befehl mit erhöhten Rechten in einer PowerShell-Sitzung ausführen (Als Administrator ausführen):

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a>Herstellen einer Verbindung mit einem alten Exchange- Remoteendpunkt führt zum Absturz

Der alte Exchange-Endpunkt wird zu einem neuen Endpunkt umgeleitet. Die Umleitungslogik weist einen Fehler auf, der zu einem Absturz führt.

**Lösung:** Stellen Sie eine direkte Verbindung mit dem neuen Endpunkt her.

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a>Das Feature „Protokollierung des Softwarebestands“ wird nach der Installation von WMF 5.0 unter Windows Server 2012 R2 fälschlicherweise beendet

Wenn WMF 5.0 auf einem Computer mit Windows Server 2012 R2 installiert wird, auf dem die Protokollierung des Softwarebestands bereits ausgeführt wird, wird dieses Feature nach der Installation fälschlicherweise beendet.

**Lösung:** Führen Sie das Cmdlet „`Start-SilLogging`“ einmal nach der Installation von WMF aus, da der Installationsvorgang fälschlicherweise das Feature „Protokollierung des Softwarebestands“ beendet.

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a>`Get-ChildItem` funktioniert nicht, wenn „-LiteralPath“ und „-Recurse“ zusammen verwendet werden

Wenn ein Verzeichnisname ein ungültiges Platzhalterzeichen enthält, liefert `Get-ChildItem` nicht die erwarteten Ergebnisse, wenn „-LiteralPath“ und „-Recurse“ zusammen verwendet werden.

**Lösung:** Die aktuelle, allerdings nicht ideale Umgehung ist das Implementieren der Rekursion im Skript, anstatt das Cmdlet zu verwenden.

## <a name="sysprep-fails-after-wmf-50-installation"></a>Sysrep schlägt nach der Installation von WMF 5.0 fehl.

Es gibt zwei Problemumgehungen für dieses Problem, abhängig davon, welche Version von Windows Server Sie ausführen.

**Lösung:**

- Für Systeme, die **Windows Server 2008 R2** ausführen
  1. Öffnen Sie PowerShell als Administrator.
  2. Führen Sie den folgenden Befehl aus.

     ```powershell
     Set-SilLogging -TargetUri https://BlankTarget -CertificateThumbprint 0123456789
     ```

  3. Führen Sie den Befehl aus, und ignorieren Sie die Fehler, da diese zu erwarten sind.

     ```powershell
     Publish-SilData
     ```

  4. Löschen Sie die Dateien im Verzeichnis \Windows\System32\Logfiles\SIL\.

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. Installieren Sie alle verfügbaren wichtigen Windows-Updates und beginnen Sie normal mit dem Sysyprep-Vorgang.

- Für Systeme, die **Windows Server 2012** ausführen
  1. Nach der Installation von WMF 5.0 auf dem Server, der mit Sysrep vorbereitet werden soll, melden Sie sich als Administrator an.
  2. Kopieren Sie „Generize.xml“ aus dem Verzeichnis `\Windows\System32\Sysprep\ActionFiles\` an einen Ort außerhalb des Windows-Verzeichnisses, z. B. `C:\`.
  3. Öffnen Sie die „Generalize.xml“-Kopie mit dem Editor.
  4. Suchen und entfernen Sie den folgenden Text. Eine Instanz von jedem Textelement muss gelöscht werden (sie sind fast am Ende des Dokuments zu finden).

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. Speichern Sie die bearbeitete Kopie von „Generalize.xml“, und schließen Sie die Datei.
  6. Öffnen Sie eine Eingabeaufforderung als Administrator.
  7. Führen Sie den folgenden Befehl aus, um die „Generalize.xml“-Datei im Ordner „system32“ in Besitz zu nehmen.

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. Führen Sie den folgenden Befehl aus, um die entsprechende Berechtigung für die Datei festzulegen:

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - Geben Sie bei der Aufforderung zur Bestätigung geben „Ja“ an.
     - Beachten Sie, dass `<AdministratorUserName>` durch den Benutzernamen ersetzt werden sollte, der Administrator auf dem Computer ist. Beispiel: „Administrator“.

  9. Kopieren Sie die von Ihnen bearbeitete und gespeicherte Datei mit dem folgenden Befehl in das Sysprep-Verzeichnis:

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - Geben Sie „Ja“ an, um die Datei zu überschreiben (Überprüfen Sie nochmal den Pfad, den Sie eingegeben haben, falls keine Aufforderung zum Überschreiben erscheint).
     - Es wird davon ausgegangen, dass Ihre bearbeitete Kopie von „Generalize.xml“ nach C:\ kopiert wurde.

  10. „Generalize.XML“ wird jetzt mit der Problemumgehung aktualisiert. Führen Sie Sysprep bitte mit der aktivierten Generalisierungsoption aus.