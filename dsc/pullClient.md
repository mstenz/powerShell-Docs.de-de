---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Einrichten eines DSC-Pullclients
ms.openlocfilehash: e6d73187566db2756ae24dabe0a825fffb5ecce0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="7d875-103">Einrichten eines DSC-Pullclients</span><span class="sxs-lookup"><span data-stu-id="7d875-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="7d875-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7d875-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="7d875-105">Jeder Zielknoten muss angewiesen werden, den Pullmodus zu verwenden. Außerdem muss die URL oder der Dateispeicherort angegeben werden, unter der bzw. dem der Pullserver Konfigurationen und Ressourcen abrufen kann und an die bzw. den Berichtsdaten gesendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="7d875-105">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>


<span data-ttu-id="7d875-106">In den folgenden Themen wird erläutert, wie Pullclients eingerichtet werden:</span><span class="sxs-lookup"><span data-stu-id="7d875-106">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="7d875-107">Einrichten eines Pullclients mithilfe von Konfigurationsnamen</span><span class="sxs-lookup"><span data-stu-id="7d875-107">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="7d875-108">Einrichten eines Pullclients mithilfe einer Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="7d875-108">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="7d875-109">**Hinweis**: Diese Themen beziehen sich auf PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="7d875-109">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="7d875-110">Informationen zum Einrichten eines Pullclients in PowerShell 4.0 finden Sie unter [Einrichten eines Pullclients mithilfe der Konfigurations-ID in PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="7d875-110">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>