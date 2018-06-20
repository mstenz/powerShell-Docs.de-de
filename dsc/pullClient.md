---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Einrichten eines DSC-Pullclients
ms.openlocfilehash: 7f8758bd7145518e30e9c28b74d0db5d74dfaab3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186659"
---
# <a name="setting-up-a-dsc-pull-client"></a>Einrichten eines DSC-Pullclients

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Der Pull-Server (Windows-Feature *DSC-Dienst*) ist eine von Windows Server unterstützte Komponente, jedoch sollen keine neuen Features oder Funktionen angeboten werden. Es wird empfohlen, verwaltete Clients auf [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) umzustellen (enthält Features zusätzlich zum Pull-Server unter Windows Server) oder auf eine der [hier](pullserver.md#community-solutions-for-pull-service) aufgeführten Communitylösungen.

Jeder Zielknoten muss angewiesen werden, den Pullmodus zu verwenden. Außerdem muss die URL oder der Dateispeicherort angegeben werden, unter der bzw. dem der Pullserver Konfigurationen und Ressourcen abrufen kann und an die bzw. den Berichtsdaten gesendet werden sollen.

In den folgenden Themen wird erläutert, wie Pullclients eingerichtet werden:

* [Einrichten eines Pullclients mithilfe von Konfigurationsnamen](pullClientConfigNames.md)
* [Einrichten eines Pullclients mithilfe einer Konfigurations-ID](pullClientConfigID.md)

> **Hinweis**: Diese Themen beziehen sich auf PowerShell 5.0. Informationen zum Einrichten eines Pullclients in PowerShell 4.0 finden Sie unter [Einrichten eines Pullclients mithilfe der Konfigurations-ID in PowerShell 4.0](pullClientConfigID4.md).