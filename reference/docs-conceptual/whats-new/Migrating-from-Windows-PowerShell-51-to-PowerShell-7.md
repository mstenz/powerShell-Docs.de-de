---
title: Migrieren von Windows PowerShell 5.1 zu PowerShell 7
description: Informationen zum Update von PowerShell 5.1 auf PowerShell 7 für Ihre Windows-Plattformen.
ms.date: 03/25/2020
ms.openlocfilehash: 8f19297bdb4825f3bbd50544dc5737997e3c83e3
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81440491"
---
# <a name="migrating-from-windows-powershell-51-to-powershell-7"></a>Migrieren von Windows PowerShell 5.1 zu PowerShell 7

PowerShell 7 wurde für Cloud-, lokale und Hybridumgebungen entwickelt und bietet Verbesserungen sowie [neue Features](What-s-New-in-PowerShell-70.md).

- Parallele Installation und Ausführung mit Windows PowerShell
- Verbesserte Kompatibilität mit vorhandenen Windows PowerShell-Modulen
- Neue Sprachfeatures wie ternäre Operatoren und `ForEach-Object -Parallel`
- Verbesserte Leistung
- SSH-basiertes Remoting
- Plattformübergreifende Interoperabilität
- Unterstützung für Docker-Container

PowerShell 7 funktioniert parallel mit Windows PowerShell, sodass Sie Editionen vor der Bereitstellung problemlos testen und vergleichen können. Die Migration erfolgt einfach, schnell und betriebssicher .

Die folgenden Windows-Betriebssysteme unterstützen PowerShell 7:

- Windows 8.1 und 10
- Windows Server 2012, 2012 R2, 2016, und 2019

PowerShell 7 lässt sich auch unter macOS und mehreren Linux-Distributionen ausführen. Eine Liste der unterstützten Betriebssysteme und Informationen zum Supportlebenszyklus finden Sie unter [PowerShell-Supportlebenszyklus](/powershell/scripting/powershell-support-lifecycle).

## <a name="installing-powershell-7"></a>Installieren von PowerShell 7

Aus Gründen der Flexibilität und zur Unterstützung der Anforderungen von IT- und DevOps-Mitarbeitern sowie Entwicklern stehen mehrere Optionen zur Installation von PowerShell 7 zur Verfügung. In den meisten Fällen können die Installationsoptionen auf die folgenden reduziert werden:

- Bereitstellen von PowerShell mit dem [MSI-Paket](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)
- Bereitstellen von PowerShell mit dem [ZIP-Paket](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)

> [!NOTE]
> Das MSI-Paket kann mit Verwaltungsprodukten wie [System Center Configuration Manager (SCCM)](/configmgr/apps/) bereitgestellt und aktualisiert werden. Laden Sie die Pakete von der [GitHub-Seite „Releases“](https://github.com/PowerShell/PowerShell/releases) herunter.

Zum Bereitstellen des MSI-Pakets sind Administratorberechtigungen erforderlich. Das ZIP-Paket kann von beliebigen Benutzern bereitgestellt werden. Das ZIP-Paket ist die einfachste Möglichkeit, PowerShell 7 zum Testen zu installieren, bevor eine vollständige Installation erfolgt.

## <a name="using-powershell-7-side-by-side-with-windows-powershell-51"></a>Parallele Nutzung von PowerShell 7 mit Windows PowerShell 5.1

PowerShell 7 ist für die parallele Nutzung mit Windows PowerShell 5.1 konzipiert. Die folgenden Features stellen sicher, dass Ihre Investition in PowerShell geschützt und die Migration zu PowerShell 7 einfach ist.

- Trennung von Installationspfad und Namen der ausführbaren Datei
- Trennung von PSModulePath
- Getrennte Profile für jede Version
- Verbesserte Modulkompatibilität
- Neue Remoting-Endpunkte
- Unterstützung von Gruppenrichtlinien
- Getrennte Ereignisprotokolle

### <a name="separate-installation-path-and-executable-name"></a>Trennung von Installationspfad und Namen der ausführbaren Datei

PowerShell 7 wird in ein neues Verzeichnis installiert und ermöglicht die parallele Ausführung mit Windows PowerShell 5.1.

Installationsspeicherorte nach Version:

- Windows PowerShell 5.1: `$env:WINDIR\System32\WindowsPowerShell\v1.0`
- PowerShell Core 6.x: `$env:ProgramFiles\PowerShell\6`
- PowerShell 7: `$env:ProgramFiles\PowerShell\7`

Der neue Speicherort wird Ihrer Umgebungsvariablen PATH hinzugefügt, sodass Sie sowohl Windows PowerShell 5.1 als auch PowerShell 7 ausführen können. Wenn Sie von PowerShell Core 6.x zu PowerShell 7 migrieren, wird PowerShell 6 entfernt und PATH ersetzt.

In Windows PowerShell heißt die ausführbare Datei `powershell.exe`. Ab Version 6 heißt die ausführbare Datei `pwsh.exe`. Der neue Name vereinfacht die parallele Ausführung beider Versionen.

### <a name="separate-psmodulepath"></a>Trennung von PSModulePath

Standardmäßig werden Module in Windows PowerShell und PowerShell 7 an verschiedenen Speicherorten gespeichert. PowerShell 7 kombiniert diese Speicherorte in der Umgebungsvariablen `$Env:PSModulePath`. Wenn Sie ein Modul nach Name importieren, prüft PowerShell den von `$Env:PSModulePath` angegebenen Speicherort. Dies ermöglicht PowerShell 7 das Laden von Core- und Desktop-Modulen.

|            Installationsumfang            |                Windows PowerShell 5.1                 |             PowerShell 7.0             |
| ----------------------------------- | ----------------------------------------------------- | -------------------------------------- |
| PowerShell-Module                  | `$env:WINDIR\system32\WindowsPowerShell\v1.0\Modules` | `$PSHOME\Modules`                      |
| Vom Benutzer installierter<br>Geltungsbereich AllUsers    | `$env:ProgramFiles\WindowsPowerShell\Modules`         | `$env:ProgramFiles\PowerShell\Modules` |
| Vom Benutzer installierter<br>Geltungsbereich CurrentUser | `$HOME\Documents\WindowsPowerShell\Modules`           | `$HOME\Documents\PowerShell\Modules`   |

In den folgenden Beispielen sind die Standardwerte von `$Env:PSModulePath` für jede Version angegeben.

- Windows PowerShell 5.1:

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\WindowsPowerShell\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

- PowerShell 7:

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\PowerShell\Modules
  C:\Program Files\PowerShell\Modules
  C:\Program Files\PowerShell\7\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

Beachten Sie, dass PowerShell 7 die Windows PowerShell-Pfade und die PowerShell 7-Pfade enthält, um das automatische Laden von Modulen zu ermöglichen.

> [!NOTE]
> Zusätzliche Pfade sind möglicherweise vorhanden, wenn Sie die Umgebungsvariable PSModulePath geändert oder benutzerdefinierte Module oder Anwendungen installiert haben.

Weitere Informationen finden Sie unter [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences) in `PSModulePath`.

Weitere Informationen zu Modulen finden Sie unter [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules).

### <a name="separate-profiles"></a>Getrennte Profile

Ein PowerShell-Profil ist ein Skript, das beim Start von PowerShell ausgeführt wird. Dieses Skript passt Ihre Umgebung durch Hinzufügen von Befehlen, Aliasen, Funktionen, Variablen, Modulen und PowerShell-Laufwerken an. Das Profilskript stellt diese Anpassungen in jeder Sitzung zur Verfügung, ohne dass sie manuell neu erstellt werden müssen.

Der Pfad zum Speicherort des Profils hat sich in PowerShell 7 geändert.

- In Windows PowerShell 5.1 lautet der Speicherort des Profils `$HOME\Documents\WindowsPowerShell`.
- In PowerShell 7 lautet der Speicherort des Profils `$HOME\Documents\PowerShell`.

Die Profildateinamen wurden ebenfalls geändert:

   ```powershell
   PS> $PROFILE | Select-Object *Host* | Format-List

   AllUsersAllHosts       : C:\Program Files\PowerShell\7\profile.ps1
   AllUsersCurrentHost    : C:\Program Files\PowerShell\7\Microsoft.PowerShell_profile.ps1
   CurrentUserAllHosts    : C:\Users\<user>\Documents\PowerShell\profile.ps1
   CurrentUserCurrentHost : C:\Users\<user>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
   ```

Weitere Informationen finden Sie unter [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).

### <a name="powershell-7-compatibility-with-windows-powershell-51-modules"></a>Kompatibilität von PowerShell 7 mit Windows PowerShell 5.1-Modulen

Die meisten Module, die Sie in Windows PowerShell 5.1 verwenden, funktionieren bereits mit PowerShell 7, einschließlich Azure PowerShell und Active Directory. Wir arbeiten weiterhin mit anderen Teams zusammen, um native PowerShell 7-Unterstützung für weitere Module wie Microsoft Graph, Office 365 und andere hinzuzufügen. Die aktuelle Liste der unterstützten Module finden Sie unter [Kompatibilität von PowerShell 7-Modulen](/powershell/scripting/whats-new/module-compatibility).

> [!NOTE]
> Unter Windows haben wir außerdem den Schalter **UseWindowsPowerShell** zu `Import-Module` hinzugefügt, um Benutzern mit inkompatiblen Modulen den Umstieg auf PowerShell 7 zu erleichtern. Weitere Informationen zu dieser Funktionalität finden Sie unter [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility).

### <a name="powershell-remoting"></a>PowerShell-Remoting

PowerShell-Remoting ermöglicht Ihnen, jeden Windows PowerShell-Befehl auf einem oder mehreren Remotecomputern ausführen. Sie können dauerhafte Verbindungen herstellen, interaktive Sitzungen starten und Skripts auf Remotecomputern ausführen.

#### <a name="ws-management-remoting"></a>WS-Management-Remoting

Bis Windows PowerShell 5.1 wird für die Verbindungsaushandlung und den Datentransport das WSMAN-Protokoll (WS-Management) verwendet. WinRM (Windows Remote Management) verwendet das WSMAN-Protokoll. Wenn WinRM aktiviert wurde, verwendet PowerShell 7 für Remoteverbindungen den vorhandenen Windows PowerShell 5.1-Endpunkt namens `Microsoft.PowerShell`. Um PowerShell 7 so zu aktualisieren, dass es seinen eigenen Endpunkt einbezieht, führen Sie das Cmdlet `Enable-PSRemoting` aus. Informationen zum Herstellen einer Verbindung mit bestimmten Endpunkten finden Sie unter [WS-Management-Remoting in PowerShell Core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core).

Um Windows PowerShell-Remoting zu verwenden, muss der Remotecomputer für die Remoteverwaltung konfiguriert sein.
Weitere Informationen und Anweisungen hierzu finden Sie unter [Informationen zu Remoteanforderungen](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).

Weitere Informationen zum Arbeiten mit Remoteverbindungen finden Sie unter [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote) (Informationen zu Remotebefehlen).

#### <a name="ssh-based-remoting"></a>SSH-basiertes Remoting

SSH-basiertes Remoting wurde in PowerShell 6.x hinzugefügt, um andere Betriebssysteme zu unterstützen, die keine nativen Windows-Komponenten wie **WinRM** verwenden können. SSH-Remoting erstellt einen PowerShell-Hostprozess als SSH-Subsystem auf dem Zielcomputer. Einzelheiten und Beispiele zum Einrichten von SSH-basiertem Remoting unter Windows und Linux finden Sie unter: [PowerShell-Remoting über SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

> [!NOTE]
> Der PowerShell-Katalog (PSGallery) enthält ein Modul und ein Cmdlet, mit dem SSH-basiertes Remoting automatisch konfiguriert kann. Laden Sie das Modul `Microsoft.PowerShell.RemotingTools` aus [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) herunter, installieren Sie es, und führen Sie das Cmdlet `Enable-SSH` aus.

Die Cmdlets `New-PSSession`, `Enter-PSSession` und `Invoke-Command` weisen neue Parametersätze zur Unterstützung von SSH-Verbindungen auf.

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Um eine Remotesitzung zu erstellen, geben Sie den Zielcomputer mit dem Parameter **HostName**an, und fügen Sie mit **UserName** den Benutzernamen hinzu. Wenn Sie die Cmdlets interaktiv ausführen, werden Sie zur Kennworteingabe aufgefordert.

```powershell
Enter-PSSession -HostName <Computer> -UserName <Username>
```

Wenn Sie den Parameter **HostName** verwenden, geben Sie alternativ die Informationen zum Benutzernamen gefolgt vom At-Zeichen (`@`) und Computernamen an.

```powershell
Enter-PSSession -HostName <Username>@<Computer>
```

Sie können die SSH-Schlüsselauthentifizierung auch mithilfe einer privaten Schlüsseldatei und des Parameters **KeyFilePath** einrichten.
Weitere Informationen finden Sie unter [OpenSSH-Schlüsselverwaltung](/windows-server/administration/openssh/openssh_keymanagement).

### <a name="group-policy-supported"></a>Unterstützung von Gruppenrichtlinien

PowerShell enthält Gruppenrichtlinieneinstellungen, die Ihnen helfen, einheitliche Optionswerte für Server in einer Unternehmensumgebung festzulegen. Dies umfasst Folgendes:

- Konfiguration der Konsolensitzung: Legt einen Konfigurationsendpunkt fest, an dem PowerShell ausgeführt wird.
- Modulprotokollierung aktivieren: Legt die Eigenschaft LogPipelineExecutionDetails von Modulen fest.
- Protokollierung von PowerShell-Skriptblöcken: Aktiviert die ausführliche Protokollierung aller PowerShell-Skripts.
- Skriptausführung aktivieren: Legt die PowerShell-Ausführungsrichtlinie fest.
- PowerShell-Aufzeichnung aktivieren: ermöglicht die Erfassung der Ein- und Ausgabe von PowerShell-Befehlen in textbasierten Transkripten.
- Standardquellpfad für "Update-Help" festlegen: Legt die Quelle für die aktualisierbare Hilfe auf ein Verzeichnis und nicht auf das Internet fest.

Weitere Informationen finden Sie unter [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings).

PowerShell 7 bietet Gruppenrichtlinienvorlagen und in `$PSHOME` ein Installationsskript.

Gruppenrichtlinientools verwenden administrative Vorlagendateien (`.admx`, `.adml`), um Richtlinieneinstellungen auf der Benutzeroberfläche aufzufüllen. Dies ermöglicht Administratoren die Verwaltung registrierungsbasierter Richtlinieneinstellungen. Das Skript `InstallPSCorePolicyDefinitions.ps1` installiert administrative PowerShell Core-Vorlagen auf dem lokalen Computer.

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/27/2020 12:38 AM          15861 InstallPSCorePolicyDefinitions.ps1
-a---           2/27/2020 12:28 AM           9675 PowerShellCoreExecutionPolicy.adml
-a---           2/27/2020 12:28 AM           6201 PowerShellCoreExecutionPolicy.admx
```

### <a name="separate-event-logs"></a>Getrennte Ereignisprotokolle

Windows PowerShell und PowerShell 7 protokollieren Ereignisse in getrennten Ereignisprotokollen. Verwenden Sie den folgenden Befehl, um eine Liste der PowerShell-Protokolle abzurufen.

```powershell
Get-WinEvent -ListLog *PowerShell*
```

Weitere Informationen finden Sie unter [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows).

## <a name="improved-editing-experience-with-visual-studio-code"></a>Verbesserte Bearbeitungsumgebung in Visual Studio Code

[Visual Studio Code (VS Code)](https://code.visualstudio.com/) mit der [PowerShell-Erweiterung](https://code.visualstudio.com/docs/languages/powershell) ist die unterstützte Skriptumgebung für PowerShell 7. Die Windows PowerShell Integrated Scripting Environment (ISE) unterstützt nur Windows PowerShell.

Die aktualisierte PowerShell-Erweiterung umfasst Folgendes:

- Neuen ISE-Kompatibilitätsmodus
- PSReadLine in der integrierten Konsole, einschließlich Syntaxhervorhebung, mehrzeilige Bearbeitung und Rückwärtssuche
- Stabilitäts- und Leistungsverbesserungen
- Neue CodeLens-Integration
- Verbesserte automatische Pfadvervollständigung

Um den Umstieg auf Visual Studio Code zu erleichtern, verwenden Sie in der **Befehlspalette** die Funktion  **ISE-Modus aktivieren**. Über diese Option wird auf ein Layout im ISE-Stil umgestellt. Das Layout im ISE-Stil bietet Ihnen alle neuen Features und Funktionen von PowerShell in einer vertrauten Benutzerumgebung.

Um auf das neue ISE-Layout umzustellen, drücken Sie <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd>, um die **Befehlspalette** zu öffnen. Geben Sie `PowerShell` ein, und wählen Sie folgende Option aus: **PowerShell: ISE-Modus aktivieren**.

Um das Layout auf das Originallayout festzulegen, öffnen Sie die **Befehlspalette**, und wählen Sie folgende Option aus: **PowerShell: ISE-Modus deaktivieren (Standard wiederherstellen)** .

Ausführliche Informationen zum Anpassen des Layouts von Visual Studio Code an ISE finden Sie unter [Replizieren der ISE-Benutzeroberfläche in Visual Studio Code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode).

> [!NOTE]
> Es ist nicht geplant, die ISE mit neuen Features zu aktualisieren. Die ISE ist jetzt in den neuesten Versionen von Windows 10 und Windows Server ein vom Benutzer deinstallierbares Feature. Es ist nicht geplant, die ISE dauerhaft zu entfernen. Das PowerShell-Team und seine Partner konzentrieren sich auf die Verbesserung der Skripterstellung in der PowerShell-Erweiterung für Visual Studio Code.

## <a name="next-steps"></a>Nächste Schritte

Mit dem Wissen zur effektiven Migration jetzt [PowerShell 7 installieren](/powershell/scripting/install/installing-powershell-core-on-windows)!
