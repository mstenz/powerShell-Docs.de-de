---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: PowerShell-Katalogstatus | MSDN
ms.openlocfilehash: 0b2f1ebcb365fcd24438a028a9c8181449266a8b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a name="powershell-gallery-status"></a><span data-ttu-id="13164-103">PowerShell-Katalogstatus</span><span class="sxs-lookup"><span data-stu-id="13164-103">PowerShell Gallery Status</span></span>
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="13164-104">27.03.2017 – GELÖST: Einzelne Modul- und Skriptseiten können nicht angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="13164-104">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="13164-105">__Zusammenfassung der Auswirkungen__: Die direkten Links zu einzelnen Modul- und Skriptseiten auf https://www.powershellgallery.com haben nicht funktioniert.</span><span class="sxs-lookup"><span data-stu-id="13164-105">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="13164-106">Dies wurde aus allen Regionen gemeldet.</span><span class="sxs-lookup"><span data-stu-id="13164-106">This was being reported across all the regions.</span></span> <span data-ttu-id="13164-107">Dies hat sich nicht auf alle PowerShellGet-Cmdlets ausgewirkt, d.h. Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script haben weiterhin funktioniert.</span><span class="sxs-lookup"><span data-stu-id="13164-107">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continued to work.</span></span>

<span data-ttu-id="13164-108">__Grundursache__: Laut unseren Technikern ist die Ursache ein Problem bei der Einbindung von Schaltflächen für soziale Netzwerke, z.B. Facebook, auf der Seite.</span><span class="sxs-lookup"><span data-stu-id="13164-108">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>  

<span data-ttu-id="13164-109">__Lösung__: Die Techniker haben das Problem gelöst, indem sie die Facebook-Kontoinformationen deaktiviert haben.</span><span class="sxs-lookup"><span data-stu-id="13164-109">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="13164-110">__Nächste Schritte__: Wir haben ein internes Nachverfolgungsproblem geöffnet, um unseren Gebrauch der Facebook-API zu reparieren.</span><span class="sxs-lookup"><span data-stu-id="13164-110">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="13164-111">15.12.2016 – Es konnten keine E-Mails über die PowerShell-Katalogwebsite gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="13164-111">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="13164-112">__Zusammenfassung der Auswirkungen__: Zwischen dem 13. und 15. Dezember 2016 über „Contact owners“ (Besitzer kontaktieren), „Manage Owners“ (Besitzer verwalten), „Support kontaktieren“ oder „Missbrauch melden“ gesendete E-Mails wurden von den Administratoren des PowerShell-Katalogs nicht empfangen.</span><span class="sxs-lookup"><span data-stu-id="13164-112">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>  
<span data-ttu-id="13164-113">__Grundursache__: Das Problem wurde von Technikern auf einen Authentifizierungsfehler beim SMTP-Server zurückgeführt.</span><span class="sxs-lookup"><span data-stu-id="13164-113">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>  
<span data-ttu-id="13164-114">__Lösung__: Techniker konnten das Authentifizierungsproblem lösen und die Verbindung mit dem SMTP-Server wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="13164-114">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>  
<span data-ttu-id="13164-115">__Nächste Schritte__: Wenn Sie die Links „Contact owners“ (Besitzer kontaktieren), „Manage Owners“ (Besitzer verwalten), „Support kontaktieren“ oder „Missbrauch melden“ während dieses Zeitraums an cgadmin@microsoft.com gesendet und keine Antwort erhalten haben, versuchen Sie es erneut.</span><span class="sxs-lookup"><span data-stu-id="13164-115">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="13164-116">Wir entschuldigen uns für eventuelle Unannehmlichkeiten.</span><span class="sxs-lookup"><span data-stu-id="13164-116">We apologize for the inconvenience.</span></span>   


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="13164-117">10.08.2016 – Gelöst: Senden von E-Mails an cgadmin@microsoft.com nicht möglich</span><span class="sxs-lookup"><span data-stu-id="13164-117">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>
<span data-ttu-id="13164-118">__Zusammenfassung der Auswirkungen__: Vom 05.08.2016 bis zum 10.08.2016 konnten Kunden keine E-Mails an cgadmin@microsoft.com senden bzw. die Funktion zur Kontaktaufnahme nicht nutzen.</span><span class="sxs-lookup"><span data-stu-id="13164-118">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>  
<span data-ttu-id="13164-119">__Grundursache__: Als Ursache haben Techniker eine Konfigurationsänderung des E-Mail-Kontos ausgemacht.</span><span class="sxs-lookup"><span data-stu-id="13164-119">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>  
<span data-ttu-id="13164-120">__Lösung__: Techniker haben das Konfigurationsproblem behoben.</span><span class="sxs-lookup"><span data-stu-id="13164-120">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>  
<span data-ttu-id="13164-121">__Nächste Schritte__: Wenn Sie in diesem Zeitraum den Link zur Kontaktaufnahme genutzt oder eine E-Mail an cgadmin@microsoft.com gesendet und wir nicht geantwortet haben, versuchen Sie es erneut.</span><span class="sxs-lookup"><span data-stu-id="13164-121">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="13164-122">Vielen Dank für Ihre Geduld.</span><span class="sxs-lookup"><span data-stu-id="13164-122">Thank you for your patience.</span></span>


