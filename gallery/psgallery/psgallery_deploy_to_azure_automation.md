---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, Cmdlet, Katalog
ms.date: 2016-10-14
contributor: manikb
title: Bereitstellen in Azure Automation | MSDN
ms.technology: powershell
ms.openlocfilehash: 20b0dd53b5d10f36089a884a99209a575332a91a
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
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

Weitere Informationen zu Azure Automation finden Sie auf der [Azure Automation-Website](http://azure.microsoft.com/en-us/services/automation/).

