---
title: Ändern den Installationspfad PSModulePath | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082208"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Ändern des Installationspfads PSModulePath

Die `PSModulePath` Umgebungsvariable speichert die Pfade zu den Speicherorten der Module, die auf dem Datenträger installiert sind. Windows PowerShell verwendet diese Variable, um Module zu suchen, wenn der Benutzer nicht den vollständigen Pfad zu einem Modul angibt. Die Pfade in dieser Variablen werden in der Reihenfolge durchsucht, in denen sie angezeigt werden.

Wenn Windows PowerShell gestartet wird, `PSModulePath` wird als eine Systemumgebungsvariable mit dem folgenden Standardwert erstellt: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.

## <a name="to-view-the-psmodulepath-variable"></a>Anzeigen der PSModulePath-variable

Die Pfade anzeigen, die im angegebenen die `PSModulePath` Variable Geben Sie den folgenden Befehl aus:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Speicherorte der PSModulePath-Variable hinzufügen

Um diese Variable Pfade hinzuzufügen, verwenden Sie eine der folgenden Methoden:

- Um einen temporären Wert hinzufügen, der nur für die aktuelle Sitzung verfügbar ist, führen Sie den folgenden Befehl an der Befehlszeile aus:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- Um einen persistenten Wert hinzuzufügen, der verfügbar ist, wenn eine Sitzung geöffnet ist, fügen Sie den folgenden Befehl, um ein Windows PowerShell-Profil:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  Weitere Informationen zu Profilen finden Sie unter ["about_profiles"](/powershell/module/microsoft.powershell.core/about/about_profiles) in der Microsoft TechNet-Bibliothek.

- Um die Registrierung eine permanente Variablen hinzugefügt haben, erstellen Sie eine neue Benutzerumgebungsvariable aufgerufen `PSModulePath` mit dem Umgebung Variablen-Editor in die **Systemeigenschaften** Dialogfeld.

- Verwenden Sie zum Hinzufügen einer permanenten Variablen mithilfe eines Skripts die **SetEnvironmentVariable** Methode für die Umgebung-Klasse. Das folgende Skript fügt beispielsweise den "c:\Programme\Microsoft Files\Fabrikam\Module Pfad auf den Wert der PSModulePath-Umgebungsvariablen für den Computer. Um den Pfad die Umgebungsvariable PSModulePath hinzuzufügen, legen Sie das Ziel auf "Benutzer" ein.

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>So entfernen Sie die Standorte aus der PSModulePath

Sie können Pfade aus der Variablen mit ähnlichen Methoden entfernen: z. B. `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` entfernt die **c:\ModulePath** Pfad aus der aktuellen Sitzung.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Moduls](./writing-a-windows-powershell-module.md)
