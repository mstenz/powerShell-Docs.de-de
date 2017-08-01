---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: Blacklists
ms.technology: powershell
ms.openlocfilehash: e823cc0b130500fb7ea60e65acf27f90ad3f3802
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: de-DE
---
### <a name="on-blacklisting"></a><span data-ttu-id="10b1b-103">Blacklists</span><span class="sxs-lookup"><span data-stu-id="10b1b-103">On Blacklisting</span></span>
<span data-ttu-id="10b1b-104">Nachdem Sie erste Erfahrungen mit JEA gesammelt haben, fragen Sie sich vielleicht, ob es möglich ist, Befehle auf eine „Blacklist“ zu setzen.</span><span class="sxs-lookup"><span data-stu-id="10b1b-104">After playing around with JEA, you may be wondering if it is possible to blacklist commands.</span></span>
<span data-ttu-id="10b1b-105">Das ist eine verständliche Anforderung, derzeit jedoch aus folgenden Gründen für JEA nicht geplant:</span><span class="sxs-lookup"><span data-stu-id="10b1b-105">This is an understandable request, but it is not currently planned for JEA for the following reasons:</span></span>

1.  <span data-ttu-id="10b1b-106">Wir haben JEA dafür konzipiert, Operatoren nur die Aktionen zu erlauben, die sie ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="10b1b-106">We designed JEA to limit operators to only the actions they need to do.</span></span>
<span data-ttu-id="10b1b-107">Eine Blacklist ist das Gegenteil dieses Konzepts.</span><span class="sxs-lookup"><span data-stu-id="10b1b-107">A blacklist is the opposite.</span></span>

2.  <span data-ttu-id="10b1b-108">Die Autoren der PowerShell-Befehle haben diese Befehle nicht mit Blick auf JEA geschrieben.</span><span class="sxs-lookup"><span data-stu-id="10b1b-108">PowerShell command authors did not design PowerShell commands with the JEA in mind.</span></span>
<span data-ttu-id="10b1b-109">Bei einer Neuinstallation von Windows Server 2016 sind etwa 1520 Befehle sofort verfügbar.</span><span class="sxs-lookup"><span data-stu-id="10b1b-109">On a fresh install of Windows Server 2016, there are about 1520 commands immediately available.</span></span>
<span data-ttu-id="10b1b-110">Bei den Gefahrenmodellen für diese Befehle ist die Möglichkeit, dass ein Benutzer Befehle mit einem Konto mit höheren Berechtigungen ausführt, nicht berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="10b1b-110">The threat models for these commands did not include the possibility that a user would be running commands as a more privileged account.</span></span>
<span data-ttu-id="10b1b-111">Einige Befehle lassen per Design Codeeinfügungen zu (z. B. Add-Type und Invoke-Command im PowerShell-Kernmodul).</span><span class="sxs-lookup"><span data-stu-id="10b1b-111">For example, certain commands allow for code injection by design (e.g. Add-Type and Invoke-Command in the core PowerShell module).</span></span>
<span data-ttu-id="10b1b-112">JEA kann Sie warnen, wenn Sie bestimmte, uns bekannte Befehle verfügbar machen, wir haben jedoch nicht jeden einzelnen Befehl in Windows basierend auf dem neuen Gefahrenmodell neu bewertet.</span><span class="sxs-lookup"><span data-stu-id="10b1b-112">JEA can warn you when you expose the specific commands we know about, but we have not re-assessed every other command in Windows based on the new threat model.</span></span>
<span data-ttu-id="10b1b-113">Sie müssen die Funktionen der Befehle verstehen, die Sie über JEA verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="10b1b-113">You must understand the capabilities of the commands you exposing through JEA.</span></span>  

3.  <span data-ttu-id="10b1b-114">Darüber hinaus: Selbst wenn JEA alle Befehle mit möglichen Schwachstellen durch Codeeinfügung blockieren würde, gäbe es keine Garantie, dass ein böswilliger Benutzer nicht in der Lage wäre, eine auf der Blacklist stehende Aktion über einen anderen Befehl auszuführen.</span><span class="sxs-lookup"><span data-stu-id="10b1b-114">Furthermore, even if JEA blocked all commands with code-injection vulnerabilities, there is no guarantee that a malicious user would not be able to carry out a blacklisted action with another related command.</span></span>
<span data-ttu-id="10b1b-115">Wenn Sie die Befehle, die Sie verfügbar machen, nicht genau kennen, können Sie nicht garantieren, dass eine bestimmte Aktion nicht möglich ist.</span><span class="sxs-lookup"><span data-stu-id="10b1b-115">Unless you understand all of the commands that you are exposing, it is impossible for you to guarantee that a certain action is not possible.</span></span>
<span data-ttu-id="10b1b-116">Die Verantwortung dafür, die Befehle zu verstehen, die Sie verfügbar machen, liegt vollständig bei Ihnen – unabhängig davon, ob eine Whitelist oder eine Blacklist verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="10b1b-116">The burden is on you to understand what commands you are exposing, whether they are using a whitelist or a blacklist.</span></span>
<span data-ttu-id="10b1b-117">Die Anzahl von Befehlen, die auf einer Blacklist aufgeführt werden müssten, wäre unüberschaubar. Daher wird JEA stattdessen mit Whitelists implementiert.</span><span class="sxs-lookup"><span data-stu-id="10b1b-117">The number of commands a blacklist would expose is unmanageable, so JEA is implemented using whitelists instead.</span></span>

