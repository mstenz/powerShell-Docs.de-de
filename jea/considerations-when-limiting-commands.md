---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "Überlegungen zum Einschränken von Befehlen"
ms.technology: powershell
ms.openlocfilehash: 0b4396ee130d99c42f613c1b79193c236ad472e7
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: de-DE
---
### <a name="considerations-when-limiting-commands"></a><span data-ttu-id="f5b09-103">Überlegungen zum Einschränken von Befehlen</span><span class="sxs-lookup"><span data-stu-id="f5b09-103">Considerations When Limiting Commands</span></span>
<span data-ttu-id="f5b09-104">Ein wichtiger Hinweis zu diesem Schritt:</span><span class="sxs-lookup"><span data-stu-id="f5b09-104">There is one important point to make about this step.</span></span>
<span data-ttu-id="f5b09-105">Es ist von entscheidender Bedeutung, dass alle über JEA verfügbar gemachten Funktionen sich in Bereichen befinden, auf die nur Administratoren zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="f5b09-105">It is critical that all capabilities exposed through JEA are located in administrator-restricted areas.</span></span>
<span data-ttu-id="f5b09-106">Benutzer ohne Administratorrechte dürfen nicht die Möglichkeit haben, die verwendeten Skripts über JEA-Endpunkte zu ändern.</span><span class="sxs-lookup"><span data-stu-id="f5b09-106">Non-administrator users should not have the capability to modify the scripts used through JEA endpoints.</span></span>

<span data-ttu-id="f5b09-107">In diesem Zusammenhang ist es ebenso wichtig, dass Sie JEA-Benutzern nicht die Möglichkeit bieten, JEA-Konfigurationen und Skripts auf der Whitelist in ihren JEA-Sitzungen zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="f5b09-107">On a related note, it is critical that you do not give JEA users the ability to overwrite JEA configurations and whitelisted scripts within their JEA sessions.</span></span>
<span data-ttu-id="f5b09-108">Gehen Sie mit größter Umsicht vor, wenn Sie Befehle wie `Copy-Item` verfügbar machen!</span><span class="sxs-lookup"><span data-stu-id="f5b09-108">Be extremely careful when exposing commands like `Copy-Item`!</span></span>

