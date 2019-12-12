---
title: Ändern des psmodulepath-Installations Pfads | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 5957ea4c15cd3778bd09b67c4b97de0ef0cfdd2a
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953839"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Ändern des Installationspfads PSModulePath

Die `PSModulePath`-Umgebungsvariable speichert die Pfade zu den Speicherorten der Module, die auf dem Datenträger installiert sind. PowerShell verwendet diese Variable, um Module zu suchen, wenn der Benutzer nicht den vollständigen Pfad zu einem Modul angibt. Die Pfade in dieser Variablen werden in der Reihenfolge durchsucht, in der Sie angezeigt werden.

Wenn PowerShell gestartet wird, wird `PSModulePath` als System Umgebungsvariable mit dem folgenden Standardwert erstellt: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` oder `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` für Windows PowerShell.

## <a name="to-view-the-psmodulepath-variable"></a>So zeigen Sie die psmodulepath-Variable an

Geben Sie den folgenden Befehl ein, um die in der `PSModulePath` Variablen angegebenen Pfade anzuzeigen:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>So fügen Sie der psmodulepath-Variablen Speicherorte hinzu

Um dieser Variablen Pfade hinzuzufügen, verwenden Sie eine der folgenden Methoden:

- Wenn Sie einen temporären Wert hinzufügen möchten, der nur für die aktuelle Sitzung verfügbar ist, führen Sie den folgenden Befehl in der Befehlszeile aus:

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- Wenn Sie einen persistenten Wert hinzufügen möchten, der immer verfügbar ist, wenn eine Sitzung geöffnet wird, fügen Sie den obigen Befehl einer PowerShell-Profil Datei (`$PROFILE`) hinzu >

  Weitere Informationen zu Profilen finden Sie unter [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).

- Um der Registrierung eine permanente Variable hinzuzufügen, erstellen Sie eine neue Benutzer Umgebungsvariable mit dem Namen `PSModulePath`, indem Sie im Dialogfeld **System Eigenschaften** den Umgebungsvariablen-Editor verwenden.

- Verwenden Sie die .NET-Methode " [stenvironmentvariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) " in der [System. Environment](https://docs.microsoft.com/dotnet/api/system.environment) -Klasse, um eine persistente Variable mithilfe eines Skripts hinzuzufügen. Das folgende Skript fügt z. b. den `C:\Program Files\Fabrikam\Module` Pfad zum Wert der Umgebungsvariablen `PSModulePath` des Computers hinzu. Um den Pfad der Umgebungsvariablen User `PSModulePath` hinzuzufügen, legen Sie für das Ziel den Wert "User" fest.

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>So entfernen Sie Speicherorte aus dem psmodulepath

Sie können Pfade aus der Variablen entfernen, indem Sie ähnliche Methoden verwenden, z. b. `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` den Pfad " **c:\modulepath** " aus der aktuellen Sitzung entfernt.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Moduls](./writing-a-windows-powershell-module.md)
