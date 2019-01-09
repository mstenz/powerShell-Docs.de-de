---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Aktualisieren von Knoten von einem Pullserver
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401127"
---
# <a name="update-nodes-from-a-pull-server"></a>Aktualisieren von Knoten von einem Pullserver

In den folgenden Abschnitten wird davon ausgegangen, dass Sie bereits einen Pull-Server eingerichtet haben. Wenn Sie Ihre Pull-Server nicht eingerichtet haben, können Sie die folgenden Handbüchern:

- [Einrichten eines DSC-SMB-Pullservers](pullServerSmb.md)
- [Einrichten eines DSC-HTTP-Pullservers](pullServer.md)

Jeder Zielknoten kann für das Herunterladen von Konfigurationen, Ressourcen und sogar meldet seinen Status konfiguriert werden. In diesem Artikel wird zeigen, wie Ressourcen hochladen, damit sie die heruntergeladen werden, und Konfigurieren von Clients zum automatischen Herunterladen von Ressourcen verfügbar sind. Zeitpunkt des Knotens eine zugewiesenen Konfiguration und empfängt, über **Pull** oder **Push** (v5), automatisch heruntergeladen von der Konfiguration aus dem Speicherort, die im LCM angegebene erforderlichen Ressourcen.

## <a name="using-the-update-dscconfiguration-cmdlet"></a>Verwenden das Cmdlet "Update-DSCConfiguration"

In PowerShell 5.0 ab der [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) Cmdlet erzwingt einen Knoten, dessen Konfiguration vom Pullserver in der LCM konfiguriert.

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>Mithilfe von Invoke-CIMMethod

In PowerShell 4.0 können Sie immer noch manuell erzwingen ein Pull-Client zum Aktualisieren der Konfiguration mit [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod). Das folgende Beispiel erstellt eine CIM-Sitzung mit den angegebenen Anmeldeinformationen, ruft die entsprechende CIM-Methode und die Sitzung entfernt.

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>Weitere Informationen

[PerformRequiredConfigurationChecks](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
