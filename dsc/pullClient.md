---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Einrichten eines DSC-Pullclients
ms.openlocfilehash: 98a67b8d27eeb445bb70f75253ca31e12207d5bd
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="3286d-103">Einrichten eines DSC-Pullclients</span><span class="sxs-lookup"><span data-stu-id="3286d-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="3286d-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3286d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="3286d-105">Jeder Zielknoten muss angewiesen werden, den Pullmodus zu verwenden. Außerdem muss die URL oder der Dateispeicherort angegeben werden, unter der bzw. dem der Pullserver Konfigurationen und Ressourcen abrufen kann und an die bzw. den Berichtsdaten gesendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="3286d-105">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>


<span data-ttu-id="3286d-106">In den folgenden Themen wird erläutert, wie Pullclients eingerichtet werden:</span><span class="sxs-lookup"><span data-stu-id="3286d-106">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="3286d-107">Einrichten eines Pullclients mithilfe von Konfigurationsnamen</span><span class="sxs-lookup"><span data-stu-id="3286d-107">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="3286d-108">Einrichten eines Pullclients mithilfe einer Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="3286d-108">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="3286d-109">**Hinweis**: Diese Themen beziehen sich auf PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="3286d-109">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="3286d-110">Informationen zum Einrichten eines Pullclients in PowerShell 4.0 finden Sie unter [Einrichten eines Pullclients mithilfe der Konfigurations-ID in PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="3286d-110">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>

