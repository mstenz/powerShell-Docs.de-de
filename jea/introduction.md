---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "Einführung"
ms.technology: powershell
ms.openlocfilehash: 71264d1001228249d9f2bb0f72473e9761170bf0
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="introduction"></a><span data-ttu-id="68f2d-103">Einführung</span><span class="sxs-lookup"><span data-stu-id="68f2d-103">Introduction</span></span>

##  <a name="motivation"></a><span data-ttu-id="68f2d-104">**Beweggründe**</span><span class="sxs-lookup"><span data-stu-id="68f2d-104">**Motivation**</span></span>  
<span data-ttu-id="68f2d-105">Wenn Sie einer Person privilegierten Zugriff auf Ihre Systeme gewähren, erweitern Sie Ihre Vertrauensstellungsgrenze auf diese Person.</span><span class="sxs-lookup"><span data-stu-id="68f2d-105">When you grant someone privileged access to your systems, you extend your trust boundary to that person.</span></span>
<span data-ttu-id="68f2d-106">Dies birgt Risiken – Administratoren sind eine Angriffsfläche.</span><span class="sxs-lookup"><span data-stu-id="68f2d-106">This is a risk -- administrators are an attack surface.</span></span>
<span data-ttu-id="68f2d-107">Sowohl Angriffe als auch gestohlene Anmeldeinformationen sind reale und nicht seltene Gefahren.</span><span class="sxs-lookup"><span data-stu-id="68f2d-107">Insider attacks and stolen credentials are both real and common.</span></span>

##  <a name="not-a-new-problem"></a><span data-ttu-id="68f2d-108">**Das ist kein neues Problem.**</span><span class="sxs-lookup"><span data-stu-id="68f2d-108">**Not a new problem**</span></span>  
<span data-ttu-id="68f2d-109">Sie sind sicher mit der Regel der geringsten Rechte vertraut, und Sie verwenden bestimmt eine Form der rollenbasierten Zugriffssteuerung (Role-Based Access Control, RBAC) bei Anwendungen, die diese bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="68f2d-109">You are probably very familiar with the principle of least privilege, and you might use some form of role-based access control (RBAC) with applications that provide it.</span></span>
<span data-ttu-id="68f2d-110">Effektivität und Verwaltungsfreundlichkeit solcher Lösungen sind jedoch häufig durch ihren Funktionsumfang und ihre Ungenauigkeit begrenzt.</span><span class="sxs-lookup"><span data-stu-id="68f2d-110">However, the effectiveness and manageability of these solutions are often limited by their broad scope and imprecision.</span></span>
<span data-ttu-id="68f2d-111">Darüber hinaus weist die rollenbasierte Zugriffssteuerung Lücken auf.</span><span class="sxs-lookup"><span data-stu-id="68f2d-111">Furthermore, there are gaps in RBAC coverage.</span></span>
<span data-ttu-id="68f2d-112">In Windows beispielsweise ist der privilegierte Zugriff im Großen und Ganzen ein binärer Schalter, sodass Sie unnötige Berechtigungen erteilen müssen, wenn Sie Benutzer zur Administratorengruppe hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="68f2d-112">For example, in Windows, privileged access is largely a binary switch, forcing you to give unnecessary permissions when adding users to the Administrators group.</span></span>

##  <a name="just-enough-administration-jea"></a><span data-ttu-id="68f2d-113">**Just Enough Administration (JEA)**</span><span class="sxs-lookup"><span data-stu-id="68f2d-113">**Just Enough Administration (JEA)**</span></span> 
<span data-ttu-id="68f2d-114">Bietet eine Plattform für rollenbasierte Zugriffssteuerung (Role-based Access Control, RBAC) durch PowerShell-Remoting.</span><span class="sxs-lookup"><span data-stu-id="68f2d-114">Provides a role-based access control (RBAC) platform through PowerShell Remoting.</span></span>
<span data-ttu-id="68f2d-115">*Damit können bestimmte Benutzer bestimmte administrative Aufgaben auf Servern ausführen, ohne dass ihnen Administratorrechte gewährt werden müssen.*</span><span class="sxs-lookup"><span data-stu-id="68f2d-115">*It allows specific users to perform specific administrative tasks on servers without giving them administrator rights.*</span></span>
<span data-ttu-id="68f2d-116">So können Sie die Lücken zwischen Ihren vorhandenen RBAC-Lösungen schließen, und die Verwaltung dieser Einstellungen wird vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="68f2d-116">This allows you to fill in the gaps between your existing RBAC solutions, and simplifies management of those settings.</span></span>

