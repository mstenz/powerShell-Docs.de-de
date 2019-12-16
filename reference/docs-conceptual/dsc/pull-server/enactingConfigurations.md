---
ms.date: 10/16/2017
keywords: dsc,powershell,configuration,setup
title: Inkraftsetzung von Konfigurationen
ms.openlocfilehash: 2a40f2055dda78cc0cb6cb05a5e14dce48be9d00
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953647"
---
# <a name="enacting-configurations"></a>Inkraftsetzung von Konfigurationen

>Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Es gibt zwei Möglichkeiten, PowerShell DSC-Konfigurationen (Desired State Configuration) anzuwenden: Push- und Pullmodus.

## <a name="push-mode"></a>Pushmodus

![Pushmodus](../images/pushModel.png "Funktionsweise des Pushmodus")

Der Pushmodus bezieht sich auf einen Benutzer, der eine Konfiguration durch Aufrufen des Cmdlets [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aktiv auf einen Zielknoten anwendet.

Nach dem Erstellen und Kompilieren einer Konfiguration können Sie sie im Pushmodus anwenden, indem Sie das Cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aufrufen und den Parameter „-Path“ des Cmdlets auf den Pfad festlegen, in dem sich die MOF-Konfigurationsdatei befindet.
Wenn sich die MOF-Konfigurationsdatei z.B. in `C:\DSC\Configurations\localhost.mof` befindet, wenden Sie sie mit dem folgenden Befehl auf den lokalen Computer an: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`.

> __Hinweis__: DSC führt eine Konfiguration standardmäßig als Hintergrundauftrag aus. Um die Konfiguration interaktiv auszuführen, rufen Sie das Cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) mit dem __-Wait__-Parameter auf.

## <a name="pull-mode"></a>Pullmodus

![Pullmodus](../images/pullModel.png "Funktionsweise des Pullmodus")

Im Pullmodus werden Pullclients so konfiguriert, dass sie ihre Konfigurationen des gewünschten Zustands von einem Remotepulldienst erhalten.
Der Pulldienst muss so eingerichtet werden, dass er den DSC-Dienst hostet und mit den Konfigurationen und Ressourcen versehen wird, die von den Pullclients benötigt werden.
Jeder der Pullclients weist ein geplantes Ereignis auf, das für die Konfiguration auf dem Knoten eine regelmäßige Kompatibilitätsprüfung durchführt.
Wenn das Ereignis erstmals ausgelöst wird, sendet der lokale Konfigurations-Manager (LCM) auf dem Pullclient eine Anforderung an den Pulldienst, um die im LCM angegebene Konfiguration abzurufen.
Wenn diese Konfiguration auf dem Pulldienst vorhanden ist und anfängliche Überprüfungen besteht, wird die Konfiguration auf den Pullclient heruntergeladen, auf dem sie vom LCM ausgeführt wird.

Entsprechend den Einstellungen der Eigenschaft **ConfigurationModeFrequencyMins** des LCMs überprüft dieser in regelmäßigen Abständen, ob der Client mit der Konfiguration übereinstimmt.
Entsprechend den Einstellungen der Eigenschaft **RefreshModeFrequency** des LCMs sucht dieser in regelmäßigen Abständen nach aktualisierten Konfigurationen auf dem Pulldienst.
Informationen zum Konfigurieren des LCMs finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](../managing-nodes/metaConfig.md).

Die empfohlene Lösung für das Hosten eines Pulldiensts ist der DSC-Clouddienst, [Azure Automation](https://azure.microsoft.com/services/automation/).
Diese gehostete Lösung ermöglicht eine grafische Verwaltung, Berichterstellung und zentrale Verwaltung.

Weitere Informationen zum Einrichten eines Pulldiensts unter Windows Server finden Sie unter [Einrichten eines DSC-Webpullservers](pullServer.md).
Beachten Sie jedoch, dass die Funktionen dieser Implementierung eingeschränkt sind und dass einige Integrationsschritte manuell durchgeführt werden müssen.

In den folgenden Themen werden Pulldienst und -clients erläutert:

- [Azure Automation DSC – Übersicht](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Einrichten eines SMB-Pullservers](pullServerSMB.md)
- [Konfigurieren eines Pullclients](pullClientConfigID.md)
