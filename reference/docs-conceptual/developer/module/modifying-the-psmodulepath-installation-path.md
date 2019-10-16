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
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360669"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Ändern des Installationspfads PSModulePath

Die Umgebungsvariable `PSModulePath` speichert die Pfade zu den Speicherorten der Module, die auf dem Datenträger installiert sind. Windows PowerShell verwendet diese Variable, um Module zu suchen, wenn der Benutzer nicht den vollständigen Pfad zu einem Modul angibt. Die Pfade in dieser Variablen werden in der Reihenfolge durchsucht, in der Sie angezeigt werden.

Beim Starten von Windows PowerShell wird `PSModulePath` als System Umgebungsvariable mit dem folgenden Standardwert erstellt: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.

## <a name="to-view-the-psmodulepath-variable"></a>So zeigen Sie die psmodulepath-Variable an

Geben Sie den folgenden Befehl ein, um die in der `PSModulePath`-Variablen angegebenen Pfade anzuzeigen:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>So fügen Sie der psmodulepath-Variablen Speicherorte hinzu

Um dieser Variablen Pfade hinzuzufügen, verwenden Sie eine der folgenden Methoden:

- Wenn Sie einen temporären Wert hinzufügen möchten, der nur für die aktuelle Sitzung verfügbar ist, führen Sie den folgenden Befehl in der Befehlszeile aus:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- Fügen Sie den folgenden Befehl in ein Windows PowerShell-Profil ein, um einen persistenten Wert hinzuzufügen, der immer verfügbar ist, wenn eine Sitzung geöffnet wird:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  Weitere Informationen zu Profilen finden Sie unter [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in der Microsoft TechNet-Bibliothek.

- Um der Registrierung eine permanente Variable hinzuzufügen, erstellen Sie eine neue Benutzer Umgebungsvariable mit dem Namen "`PSModulePath`", indem Sie im Dialogfeld " **System Eigenschaften** " den Umgebungsvariablen-Editor verwenden.

- Um eine persistente Variable mithilfe eines Skripts hinzuzufügen, verwenden Sie die Methode "*" **in der Umgebungs** Klasse. Mit dem folgenden Skript wird z. b. der Pfad "c:\programme\fabrikam\module" dem Wert der Umgebungsvariablen "psmodulepath" für den Computer hinzugefügt. Zum Hinzufügen des Pfads zur Benutzer-psmodulepath-Umgebungsvariablen legen Sie für das Ziel den Wert "User" fest.

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>So entfernen Sie Speicherorte aus dem psmodulepath

Sie können Pfade aus der Variablen entfernen, indem Sie ähnliche Methoden verwenden: beispielsweise entfernt `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` den Pfad " **c:\modulepath** " aus der aktuellen Sitzung.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Moduls](./writing-a-windows-powershell-module.md)
