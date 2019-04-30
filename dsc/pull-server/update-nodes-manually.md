---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Aktualisieren von Knoten von einem Pullserver
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079097"
---
# <a name="update-nodes-from-a-pull-server"></a>Aktualisieren von Knoten von einem Pullserver

Die folgenden Abschnitte gehen davon aus, dass Sie bereits einen Pullserver eingerichtet haben. Wenn Sie noch keinen Pullserver eingerichtet haben, können Sie die folgenden Anleitungen verwenden:

- [Einrichten eines DSC-SMB-Pullservers](pullServerSmb.md)
- [Einrichten eines DSC-HTTP-Pullservers](pullServer.md)

Jeder Zielknoten kann zum Herunterladen von Konfigurationen, Ressourcen und sogar zum Berichten seines Status konfiguriert werden. Dieser Artikel zeigt Ihnen, wie Sie Ressourcen hochladen können, damit sie zum Download zur Verfügung stehen, und wie Sie Clients so konfigurieren, dass sie Ressourcen automatisch herunterladen. Wenn der Knoten eine zugewiesene Konfiguration empfängt (durch **Pull** oder **Push** (v5)), lädt er automatisch alle für die Konfiguration erforderlichen Ressourcen vom in LCM angegebenen Speicherort herunter.

## <a name="using-the-update-dscconfiguration-cmdlet"></a>Verwenden des Cmdlets „Update-DSCConfiguration“

Ab PowerShell 5.0 erzwingt das Cmdlet [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration), dass ein Knoten seine Konfiguration aus dem in LCM konfigurierten Pullserver aktualisiert.

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>Verwenden von „Invoke-CimMethod“

In PowerShell 4.0 können Sie einen Pullclient weiterhin manuell zwingen, seine Konfiguration mithilfe von [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod) zu aktualisieren. Das folgende Beispiel erstellt eine CIM-Sitzung mit angegebenen Anmeldeinformationen, ruft die entsprechende CIM-Methode auf und entfernt die Sitzung.

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>Weitere Informationen

[PerformRequiredConfigurationChecks](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
