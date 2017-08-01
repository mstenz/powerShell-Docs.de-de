---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "Häufige Fehler bei Rollenfunktionen"
ms.technology: powershell
ms.openlocfilehash: 8e928ec07ef98b2ec8186a27d3aefa1450a3a424
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: de-DE
---
### <a name="common-role-capability-pitfalls"></a><span data-ttu-id="4b0ea-103">Häufige Fehler bei Rollenfunktionen</span><span class="sxs-lookup"><span data-stu-id="4b0ea-103">Common Role Capability Pitfalls</span></span>
<span data-ttu-id="4b0ea-104">Wenn Sie diesen Prozess alleine absolvieren, könnten Ihnen einige häufig auftretende Fehler unterlaufen.</span><span class="sxs-lookup"><span data-stu-id="4b0ea-104">You may run into a few common pitfalls if you go through this process yourself.</span></span>
<span data-ttu-id="4b0ea-105">Hier finden Sie einige wichtige Informationen dazu, wie Sie solche Fehler identifizieren und beheben, wenn Sie einen neuen Endpunkt erstellen oder ändern:</span><span class="sxs-lookup"><span data-stu-id="4b0ea-105">Here is a quick guide explaining how to identify and remediate these issues when modifying or creating a new endpoint:</span></span>

#### <a name="functions-vs-cmdlets"></a><span data-ttu-id="4b0ea-106">Funktionen im Vergleich zu Cmdlets</span><span class="sxs-lookup"><span data-stu-id="4b0ea-106">Functions vs. Cmdlets</span></span>
<span data-ttu-id="4b0ea-107">In PowerShell geschriebene PowerShell-Befehle sind PowerShell-Funktionen.</span><span class="sxs-lookup"><span data-stu-id="4b0ea-107">PowerShell commands written in PowerShell are PowerShell functions.</span></span>
<span data-ttu-id="4b0ea-108">Als spezielle .NET-Klassen geschriebene PowerShell-Befehle sind PowerShell-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="4b0ea-108">PowerShell commands written as specialized .NET classes are PowerShell cmdlets.</span></span>
<span data-ttu-id="4b0ea-109">Sie können den Befehlstyp prüfen, indem Sie `Get-Command` ausführen.</span><span class="sxs-lookup"><span data-stu-id="4b0ea-109">You can check the command type by running `Get-Command`.</span></span>

#### <a name="visibleproviders"></a><span data-ttu-id="4b0ea-110">VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="4b0ea-110">VisibleProviders</span></span>
<span data-ttu-id="4b0ea-111">Sie müssen alle Anbieter verfügbar machen, die von Ihren Befehlen benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="4b0ea-111">You will need to expose any providers your commands need.</span></span>
<span data-ttu-id="4b0ea-112">Am häufigsten wird der Dateisystemanbieter verwendet, Sie werden jedoch möglicherweise auch weitere Anbieter verfügbar machen müssen, beispielsweise den Registrierungsanbieter.</span><span class="sxs-lookup"><span data-stu-id="4b0ea-112">The most common is the FileSystem provider, but you may also need to expose others, like the Registry provider.</span></span>
<span data-ttu-id="4b0ea-113">Eine Einführung in das Thema Anbieter finden Sie in diesem Blogbeitrag von [Hey, Scripting Guy!](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).</span><span class="sxs-lookup"><span data-stu-id="4b0ea-113">For an introduction to providers, check out this [Hey, Scripting Guy blog post](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).</span></span>
<span data-ttu-id="4b0ea-114">Gehen Sie vorsichtig vor, wenn Sie Anbieter verfügbar machen – häufig ist es besser, selbst eine Funktion zu definieren, die mit den zugrunde liegenden Anbietern arbeitet, als den Anbieter in einer JEA-Sitzung direkt verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="4b0ea-114">Be careful when exposing providers -- often, it is better to define your own function that works with the underlying providers than to directly expose the provider in a JEA session.</span></span>
<span data-ttu-id="4b0ea-115">Auf diese Weise können Sie Benutzern weiterhin ermöglichen, mit Dateien, Registrierungsschlüsseln usw. zu arbeiten, behalten aber dank einer benutzerdefinierten Validierungslogik die Kontrolle darüber, mit **welchen** Dateien und Registrierungsschlüsseln die Benutzer arbeiten.</span><span class="sxs-lookup"><span data-stu-id="4b0ea-115">This way, you can still allow users to work with files, registry keys, etc. but retain control over **which** files and registry keys they can work with using custom validation logic.</span></span>

