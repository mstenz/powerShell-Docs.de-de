---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Bekannte Probleme in WMF 5.1
ms.openlocfilehash: e59ea1b9a5282eb5727a37ce605c71724a219827
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225844"
---
# <a name="known-issues-in-wmf-51"></a>Bekannte Probleme in WMF 5.1

> [!Note]
> Diese Informationen können geändert werden.

## <a name="starting-powershell-shortcut-as-administrator"></a>Starten der PowerShell-Verknüpfung als Administrator

Nach der Installation von WMF erhalten Sie möglicherweise eine Fehlermeldung „Undefinierter Fehler“, wenn Sie versuchen, PowerShell als Administrator über die Verknüpfung zu starten.
Öffnen Sie die Verknüpfung erneut als Nicht-Administrator. Anschließend funktioniert die Verknüpfung auch, wenn Sie sie als Administrator verwenden.

## <a name="pester"></a>Pester

In diesem Release treten zwei Probleme auf, derer Sie sich bewusst sein sollten, wenn Sie Pester auf Nano Server verwenden:

- Wenn Pester selbst getestet wird, treten einige Fehler aufgrund von Unterschieden zwischen FullCLR und CoreCLR auf. Vor allem ist die Validate-Methode für den Typ „XmlDocument“ nicht verfügbar. Sechs Tests, die versuchen, das Schema der NUnit-Ausgabeprotokolle zu überprüfen, sind dafür bekannt, dass sie Fehler ausgeben.
- Bei einem Code Coverage-Test tritt aktuell ein Fehler auf, da die DSC-Ressource *WindowsFeature* in Nano Server nicht vorhanden ist. Diese Fehler haben in der Regel jedoch keine Auswirkungen und können ohne Weiteres ignoriert werden.

## <a name="operation-validation"></a>Überprüfung des Vorgangs

- Bei `Update-Help` tritt aufgrund eines nicht funktionierenden Hilfe-URI ein Fehler beim Modul „Microsoft.PowerShell.Operation.Validation“ auf.

## <a name="dsc-after-uninstall-wmf"></a>DSC nach Deinstallieren von WMF

- Nach Deinstallieren von WMF werden DSC MOF-Dokumente nicht aus dem Ordner „Configuration“ gelöscht. DSC funktioniert nicht ordnungsgemäß, wenn die MOF-Dokumente neuere Eigenschaften enthalten, die auf den älteren Systemen nicht verfügbar sind. In diesem Fall führen Sie in einer PowerShell-Konsole mit erhöhten Rechten das folgende Skript aus, um die DSC-Status zu bereinigen.

  ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )
    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a>Virtuelle JEA-Konten

Zur Verwendung virtueller Konten in WMF 5.0 konfigurierte JEA-Endpunkte und -Sitzungskonfigurationen werden nach dem Upgrade auf WMF 5.1 nicht für die Verwendung eines virtuellen Kontos konfiguriert.
Dies bedeutet, dass in JEA-Sitzungen ausgeführte Befehle unter der Identität des verbindenden Benutzers und nicht unter einem temporären Administratorkonto ausgeführt werden, was möglicherweise dazu führt, dass der Benutzer keine Befehle ausführen kann, für die erhöhte Rechte erforderlich sind.
Um die virtuellen Konten wiederherzustellen, müssen Sie die Registrierung für alle Sitzungskonfigurationen, die virtuelle Konten verwenden, aufheben und diese anschließend wieder registrieren.

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```