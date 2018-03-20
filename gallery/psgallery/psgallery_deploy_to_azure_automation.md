---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: Bereitstellen in Azure Automation | MSDN
ms.openlocfilehash: 223acbcc2f6cd4f15e1ee55d3f2f68df851cd902
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
<a name="deploy-to-azure-automation"></a>Bereitstellen in Azure Automation
===========================

Mit der Schaltfläche „Deploy to Azure Automation“ (Bereitstellen in Azure Automation) auf der Seite mit den Elementdetails können Sie ein Element aus dem PowerShell-Katalog auf Azure Automation bereitstellen.

![Schaltfläche zum Bereitstellen in Azure Automation](Images/DeployToAzureAutomationButton.png)

Wenn Sie auf diese Schaltfläche klicken, werden Sie zum Azure-Verwaltungsportal umgeleitet, wo Sie sich mit den Anmeldeinformationen Ihres Azure-Kontos anmelden.
Wenn das Element Abhängigkeiten enthält, werden diese ebenfalls auf Azure Automation bereitgestellt.

WARNUNG: Wenn Element und Version bereits identisch in Ihrem Automation-Konto vorhanden sind, wird eine erneute Bereitstellung aus dem PowerShell-Katalog das Element in Ihrem Automation-Konto überschreiben.

Wenn Sie ein Modul bereitstellen, wird es im Abschnitt „Module“ von Azure Automation angezeigt.  Wenn Sie ein Skript bereitstellen, wird es im Abschnitt „Runbooks“ von Azure Automation angezeigt.

Sie können die Schaltfläche „Deploy to Azure Automation“ (Bereitstellen in Azure Automation) deaktivieren, indem Sie den Elementmetadaten das Tag „AzureAutomationNotSupported“ hinzufügen.

Weitere Informationen zu Azure Automation finden Sie auf der [Azure Automation-Website](http://azure.microsoft.com/services/automation/).

