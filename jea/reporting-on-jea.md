---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: Berichterstellung zu JEA
ms.technology: powershell
ms.openlocfilehash: 3e7bd2755281f491bba8a905df018fb2e1cac6ff
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="reporting-on-jea"></a><span data-ttu-id="c1bb8-103">Berichterstellung zu JEA</span><span class="sxs-lookup"><span data-stu-id="c1bb8-103">Reporting on JEA</span></span>
<span data-ttu-id="c1bb8-104">Da JEA es nicht privilegierten Benutzern erlaubt, in einem privilegierten Kontext zu arbeiten, sind Protokollierung und Überprüfung extrem wichtig.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-104">Because JEA allows non-privileged users to run in a privileged context, logging and auditing are extremely important.</span></span>
<span data-ttu-id="c1bb8-105">In diesem Abschnitt geht es um die Tools, die Sie für die Protokollierung und Berichterstellung verwenden können.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-105">In this section, we'll run through the tools you can use to help you with logging and reporting.</span></span>

## <a name="reporting-on-jea-actions"></a><span data-ttu-id="c1bb8-106">Berichterstellung zu JEA-Aktionen</span><span class="sxs-lookup"><span data-stu-id="c1bb8-106">Reporting on JEA Actions</span></span>
### <a name="over-the-shoulder-transcription"></a><span data-ttu-id="c1bb8-107">Mitschnitt einer Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="c1bb8-107">Over-the-Shoulder Transcription</span></span>
<span data-ttu-id="c1bb8-108">Eine der schnellsten Möglichkeiten, sich einen Überblick über die Aktivitäten in einer PowerShell-Sitzung zu verschaffen, ist es, der Person, die Daten eingibt, über die Schulter zu schauen.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-108">One of the quickest ways to get a summary of what's happening in a PowerShell session is to look over the shoulder of the person typing.</span></span>
<span data-ttu-id="c1bb8-109">So sehen Sie die eingegebenen Befehle, die Ausgabe dieser Befehle, und alles ist gut.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-109">You see their commands, the output of those commands, and all is well.</span></span>
<span data-ttu-id="c1bb8-110">Vielleicht ist auch nicht alles gut, aber zumindest wissen Sie dann Bescheid.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-110">Or it's not, but at least you'll know.</span></span>
<span data-ttu-id="c1bb8-111">PowerShell-Aufzeichnungen bieten eine ähnliche Ansicht nach Abschluss der Aktivitäten.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-111">PowerShell transcription is designed to give you a similar view after the fact.</span></span>

<span data-ttu-id="c1bb8-112">Wenn Sie das Feld „TranscriptDirectory“ in Ihrer Sitzungskonfiguration verwenden, zeichnet PowerShell automatisch alle Aktionen in einer bestimmten Sitzung auf.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-112">When using the "TranscriptDirectory" field in your Session Configuration, PowerShell will automatically record a transcript of all actions taken in a given session.</span></span>
<span data-ttu-id="c1bb8-113">Sie finden die Aufzeichnungen Ihrer Sitzungen in diesem Dokument: $env:ProgramData\JEAConfiguration\Transcripts.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-113">You can find transcripts from your sessions in this document here: "$env:ProgramData\JEAConfiguration\Transcripts"</span></span>

<span data-ttu-id="c1bb8-114">Wie Sie sehen, werden Informationen über den verbundenen Benutzer, den ausführenden Benutzer, die in dieser Sitzung ausgeführten Befehle und vieles mehr aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-114">As you can tell, the transcript records information about the "Connected" user, the "Run As" user, the commands run in the session, and more.</span></span>
<span data-ttu-id="c1bb8-115">Weitere Informationen über PowerShell-Aufzeichnungen finden Sie in diesem [Blogbeitrag](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span><span class="sxs-lookup"><span data-stu-id="c1bb8-115">For more information about PowerShell transcription, check out [this blog post](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span></span>

### <a name="powershell-event-logs"></a><span data-ttu-id="c1bb8-116">PowerShell-Ereignisprotokolle</span><span class="sxs-lookup"><span data-stu-id="c1bb8-116">PowerShell Event Logs</span></span>
<span data-ttu-id="c1bb8-117">Wenn die Modulprotokollierung aktiviert ist, werden alle PowerShell-Aktionen auch in regulären Windows-Ereignisprotokollen aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-117">When you have module logging turned on, all PowerShell actions are also recorded in regular Windows Event logs.</span></span>
<span data-ttu-id="c1bb8-118">Diese sind im Vergleich zu Aufzeichnungen etwas schwieriger zu lesen, aber die Detailgenauigkeit kann sehr hilfreich sein.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-118">This is slightly messier to deal with when compared to transcripts, but the level of detail it gives you can be useful.</span></span>

<span data-ttu-id="c1bb8-119">Im Betriebsprotokoll „PowerShell“ wird unter der Ereignis-ID 4104 jeder aufgerufene Befehl aufgezeichnet, wenn die Modulprotokollierung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-119">In the "PowerShell" operational log, Event ID 4104 will record each command invoked if you have enabled module logging.</span></span>

### <a name="other-event-logs"></a><span data-ttu-id="c1bb8-120">Weitere Ereignisprotokolle</span><span class="sxs-lookup"><span data-stu-id="c1bb8-120">Other Event Logs</span></span>
<span data-ttu-id="c1bb8-121">Im Gegensatz zu PowerShell-Protokollen und -Aufzeichnungen erfassen andere Protokollierungsmechanismen nicht den „verbundenen Benutzer“.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-121">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the "Connected User".</span></span>
<span data-ttu-id="c1bb8-122">Sie müssen PowerShell-Protokolle und andere Protokolle korrelieren, um durchgeführte Aktionen zu vergleichen.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-122">You will need to do some correlation between other logs and PowerShell logs to match up actions taken.</span></span>

<span data-ttu-id="c1bb8-123">Im Betriebsprotokoll „Windows Remote Management“ werden unter der Ereignis-ID 193 die SID und der Name des Benutzers aufgezeichnet, der die Verbindung herstellt. Zur Unterstützung der Korrelation wird auch die SID des virtuellen ausführenden Kontos aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-123">In the "Windows Remote Management" operational log, Event ID 193 will record the Connecting User's SID and Name, as well as the RunAs Virtual Account's SID to assist with this correlation.</span></span>
<span data-ttu-id="c1bb8-124">Sie haben sicherlich auch bemerkt, dass der Name des virtuellen ausführenden Kontos am Ende die Domäne und den Benutzernamen des Benutzers enthält, der die Verbindung herstellt.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-124">You may have also noticed that the name of the RunAs Virtual Account includes the connecting user's domain and username at the end.</span></span>

## <a name="reporting-on-jea-configuration"></a><span data-ttu-id="c1bb8-125">Berichterstellung für die JEA-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="c1bb8-125">Reporting on JEA Configuration</span></span>
### <a name="get-pssessionconfiguration"></a><span data-ttu-id="c1bb8-126">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="c1bb8-126">Get-PSSessionConfiguration</span></span>
<span data-ttu-id="c1bb8-127">Um einen exakten Bericht über den Status Ihrer Umgebung zu erhalten, müssen Sie wissen, wie viele JEA-Endpunkte Sie auf Ihrem Computer eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-127">In order to accurately report on the state of your environment, it's important to know how many JEA endpoints you have set up on your machine.</span></span>
<span data-ttu-id="c1bb8-128">`Get-PSSessionConfiguration` ruft diese Informationen ab.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-128">`Get-PSSessionConfiguration` does just that.</span></span>

### <a name="get-pssessioncapability"></a><span data-ttu-id="c1bb8-129">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="c1bb8-129">Get-PSSessionCapability</span></span>
<span data-ttu-id="c1bb8-130">Die manuelle Berichterstellung zu den Funktionen eines bestimmten Benutzers über einen JEA-Endpunkt kann ziemlich komplex sein.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-130">Manually reporting on the capabilities of any given user through a JEA endpoint can be quite complex.</span></span>
<span data-ttu-id="c1bb8-131">Sie müssen wahrscheinlich mehrere verschiedene Rollenfunktionen überprüfen.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-131">You would potentially need to inspect several role capabilities.</span></span>
<span data-ttu-id="c1bb8-132">Glücklicherweise macht das Cmdlet „Get-PSSessionCapability“ genau das.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-132">Fortunately, the "Get-PSSessionCapability" cmdlet does this.</span></span>

<span data-ttu-id="c1bb8-133">Führen Sie zum Testen den folgenden Befehl von einer PowerShell-Administratoreingabeaufforderung aus:</span><span class="sxs-lookup"><span data-stu-id="c1bb8-133">To test this out, run the following command from an administrator PowerShell prompt:</span></span>
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```

