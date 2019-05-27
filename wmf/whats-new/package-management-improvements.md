---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Verbesserungen bei der Paketverwaltung in WMF 5.1
ms.openlocfilehash: 24ff05d6bf5993826106f1a1d2cee6dad363d1e2
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855425"
---
# <a name="improvements-to-package-management-in-wmf-51"></a>Verbesserungen bei der Paketverwaltung in WMF 5.1

In WMF 5.1 wurden folgende Probleme behoben:

## <a name="version-alias"></a>Versionsalias

**Szenario:** Sie haben Version 1.0 und 2.0 des Pakets P1 auf Ihrem System installiert und möchten nun die Version 1.0 deinstallieren. Deshalb führen Sie `Uninstall-Package -Name P1 -Version 1.0` aus. Sie erwarten, dass Version 1.0 nach dem Ausführen des Cmdlets deinstalliert wurde. Das Ergebnis ist jedoch, dass Version 2.0 deinstalliert wird.

Dies passiert, weil der `-Version`-Parameter ein Alias für den `-MinimumVersion`-Parameter ist. Wenn PackageManagement ein qualifiziertes Paket mit der Mindestversion 1.0 sucht, wird die neueste Version zurückgegeben. Dieses Verhalten wird normalerweise erwartet, da meistens die neueste Version gefunden werden soll. Für `Uninstall-Package` sollte dies aber nicht gelten.

**Lösung**: Der Alias `-Version` wurde in PackageManagement (auch bekannt als OneGet) und PowerShellGet vollständig entfernt.

## <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a>Mehrere Aufforderungen zum Bootstrapping des NuGet-Anbieters

**Szenario:** Wenn Sie `Find-Module` oder `Install-Module` oder andere PackageManagement-Cmdlets erstmals auf Ihrem Computer ausführen, versucht PackageManagement das Bootstrapping des NuGet-Anbieters. Das liegt daran, dass der PowerShellGet-Anbieter auch den NuGet-Anbieter verwendet, um PowerShell-Module herunterzuladen.
PackageManagement fordert dann vom Benutzer die Berechtigung zum Installieren des NuGet-Anbieters an. Nachdem der Benutzer für das Bootstrapping „yes“ ausgewählt hat, wird die neueste Version des NuGet-Anbieters installiert.

Wenn jedoch eine ältere Version des NuGet-Anbieters auf Ihrem Computer installiert ist, wird mitunter die ältere NuGet-Version zuerst in die PowerShell-Sitzung geladen (was die Racebedingung in PackageManagement ist). Damit PowerShellGet funktioniert, ist jedoch die neuere Version des NuGet-Anbieters erforderlich. Deshalb wird PackageManagement von PowerShellGet aufgefordert, für den NuGet-Anbieter erneut das Bootstrapping auszuführen.
Dies führt zu mehreren Aufforderungen zum Bootstrapping des NuGet-Anbieters.

**Lösung**: In WMF 5.1 lädt PackageManagement die neueste Version des NuGet-Anbieters, um mehrere Aufforderungen zum Bootstrapping des NuGet-Anbieters zu vermeiden.

Es gibt auch eine Umgehung dieses Problems. Löschen Sie dazu manuell die alte Version des NuGet-Anbieters (NuGet-Anycpu.exe), sofern vorhanden, aus „$env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies“.

## <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a>Unterstützung für PackageManagement auf Computern mit ausschließlichem Intranetzugriff

**Szenario:** Benutzer im Unternehmen haben keinen Zugriff auf das Internet, sondern nur auf das Intranet. Dies wurde von PackageManagement in WMF 5.0 nicht unterstützt.

**Szenario:** In WMF 5.0 hat PackageManagement keine Computer unterstützt, die nur auf das Intranet (aber nicht auf das Internet) zugreifen dürfen.

**Lösung**: In WMF 5.1 können Sie diese Schritte ausführen, um Intranetcomputern das Verwenden von PackageManagement zu erlauben:

1. Laden Sie den NuGet-Anbieter auf einem anderen Computer mit Internetverbindung mit dem Befehl `Install-PackageProvider -Name NuGet` herunter.

2. Suchen Sie den NuGet-Anbieter entweder unter `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` oder `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.

3. Kopieren Sie die Binärdateien in einen Ordner oder eine Netzwerkfreigabe, auf die der Intranetcomputer zugreifen kann, und installieren Sie den NuGet-Anbieter mit `Install-PackageProvider -Name NuGet -Source <Path to folder>`.


## <a name="event-logging-improvements"></a>Verbesserungen bei der Ereignisprotokollierung

Wenn Sie Pakete installieren, ändern Sie den Status des Computers. In WMF 5.1 protokolliert PackageManagement jetzt Ereignisse im Windows-Ereignisprotokoll für die Aktivitäten `Install-Package`, `Uninstall-Package` und `Save-Package`. Das Ereignisprotokoll ist dasselbe wie für PowerShell, d. h. `Microsoft-Windows-PowerShell, Operational`.

## <a name="support-for-basic-authentication"></a>Unterstützung für Standardauthentifizierung

In WMF 5.1 unterstützt PackageManagement das Suchen und Installieren von Paketen aus einem Repository, das Standardauthentifizierung erfordert. Sie können Ihre Anmeldeinformationen für die Cmdlets `Find-Package` und `Install-Package` angeben. Beispiel:

```powershell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```

## <a name="support-for-using-packagemanagement-behind-a-proxy"></a>Unterstützung für die Verwendung von PackageManagement hinter einem Proxy

In WMF 5.1 verwendet PackageManagement jetzt die neuen Proxyparameter `-ProxyCredential` und `-Proxy`. Mithilfe dieser Parameter können Sie den Proxy-URL und die Anmeldeinformationen für PackageManagement-Cmdlets angeben. Standardmäßig werden die Proxyeinstellungen des Systems verwendet. Beispiel:

```powershell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
