---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: PowerShell-Katalogstatus | MSDN
ms.openlocfilehash: 08d09ce83b5133598152186e12fc8ced90c36a88
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
<a name="powershell-gallery-status"></a><span data-ttu-id="64e64-103">PowerShell-Katalogstatus</span><span class="sxs-lookup"><span data-stu-id="64e64-103">PowerShell Gallery Status</span></span>
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a><span data-ttu-id="64e64-104">10.10.2017 – Der PowerShell-Katalog war am 10.10.17 für 2 Stunden nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="64e64-104">10/10/2017 - PowerShell Gallery unavailable for 2 hours 10/10/17</span></span>

<span data-ttu-id="64e64-105">__Zusammenfassung der Auswirkungen__: Beim PowerShell-Katalog kam es während eines Zeitraums zu sehr hohen Wartezeiten, wodurch am 10.10.17 ab ca. 17:00 Uhr (PDT) zeitweilige Verbindungsprobleme verursacht wurden.</span><span class="sxs-lookup"><span data-stu-id="64e64-105">__Summary of Impact__: The PowerShell Gallery experienced a period of very high latency, resulting in intermittent connection issues, beginning approximately 5pm (PDT) 10/10/17.</span></span> <span data-ttu-id="64e64-106">Zur Behebung des Problems wurde der Standort ab ca. 22 Uhr (PDT) für 2 Stunden offline geschaltet.</span><span class="sxs-lookup"><span data-stu-id="64e64-106">While resolving the issue, the site was taken offline for 2 hours starting approximately 10pm (PDT).</span></span> <span data-ttu-id="64e64-107">Der Standort wurde am 10.10.2017 kurz vor Mitternacht wiederhergestellt.</span><span class="sxs-lookup"><span data-stu-id="64e64-107">The site was restored shortly before midnight 10/10/2017.</span></span>

<span data-ttu-id="64e64-108">__Grundursache__: Die Grundursache für die hohe Wartezeit wird zurzeit noch untersucht.</span><span class="sxs-lookup"><span data-stu-id="64e64-108">__Root Cause__: The root cause of the high latency is still being investigated.</span></span>

<span data-ttu-id="64e64-109">__Lösung__: Die Webdienste mussten offline geschaltet und wiederhergestellt werden, um das primäre Problem zu beheben.</span><span class="sxs-lookup"><span data-stu-id="64e64-109">__Resolution__: The web services had to be taken offline and restored in order to address the primary issue.</span></span>

<span data-ttu-id="64e64-110">__Nächste Schritte__: Die Grundursache für das ursprüngliche Problem wird zurzeit untersucht.</span><span class="sxs-lookup"><span data-stu-id="64e64-110">__Next Steps__: The root cause for the original issue is being investigated.</span></span>

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a><span data-ttu-id="64e64-111">01.06.2017: Bereitstellung in Azure Automation aktuell nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="64e64-111">06/01/2017 - Deploy to Azure Automation Currently Unavailable</span></span>

<span data-ttu-id="64e64-112">__Zusammenfassung der Auswirkungen__: Aktuell können vom PowerShell-Katalog aus keine Elemente mit Abhängigkeiten in Azure Automation bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="64e64-112">__Summary of Impact__: Deploying items with dependencies to Azure Automation from the PowerShell Gallery is currently unavailable.</span></span>  <span data-ttu-id="64e64-113">Von Azure Automation aus ist es weiterhin möglich, Elemente aus dem PowerShell-Katalog zu importieren.</span><span class="sxs-lookup"><span data-stu-id="64e64-113">Importing items from the PowerShell Gallery from inside Azure Automation is still available.</span></span>

<span data-ttu-id="64e64-114">__Grundursache__: Elemente, die von anderen Elementen abhängen und zuvor in Azure Automation bereitgestellt wurden, können nicht in Azure Automation bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="64e64-114">__Root Cause__: Items that have dependencies on others, and have been previously deployed to Azure Automation, will not be deployed to Azure Automation.</span></span> <span data-ttu-id="64e64-115">Techniker haben ein Problem damit festgestellt, wie ARM-Vorlagen für Elemente mit Abhängigkeiten zur Bereitstellung in Azure Automation generiert werden.</span><span class="sxs-lookup"><span data-stu-id="64e64-115">Engineers have identified an issue with how ARM templates are generated for items with dependencies for the Deploy to Azure Automation functionality.</span></span>

<span data-ttu-id="64e64-116">__Lösung__: Unsere Techniker arbeiten an einer Lösung für dieses Problem.</span><span class="sxs-lookup"><span data-stu-id="64e64-116">__Resolution__: Engineers are working to resolve issue.</span></span>  <span data-ttu-id="64e64-117">Die aktuelle Problemumgehung für Benutzer besteht darin, das Element mithilfe von Azure Automation aus dem PowerShell-Katalog zu importieren.</span><span class="sxs-lookup"><span data-stu-id="64e64-117">The current workaround for users is to import the item from the PowerShell Gallery from inside Azure Automation.</span></span>

<span data-ttu-id="64e64-118">__Nächste Schritte__: Unsere Techniker stellen in Kürze einen Fix bereit.</span><span class="sxs-lookup"><span data-stu-id="64e64-118">__Next Steps__: Engineers will release the fix shortly.</span></span>  <span data-ttu-id="64e64-119">Verwenden Sie in der Zwischenzeit die empfohlene Problemumgehung.</span><span class="sxs-lookup"><span data-stu-id="64e64-119">In the meantime, please use the recommended workaround.</span></span>


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a><span data-ttu-id="64e64-120">11.04.2017: Benutzer können sich nicht mit Azure Active Directory-Konten (AAD) anmelden</span><span class="sxs-lookup"><span data-stu-id="64e64-120">04/11/2017 - Users unable to log in with Azure Active Directory (AAD) accounts</span></span>

<span data-ttu-id="64e64-121">__Zusammenfassung der Auswirkungen__: Einige Benutzer konnten sich mit ihren Azure AD-Konten nicht beim PowerShell-Katalog anmelden.</span><span class="sxs-lookup"><span data-stu-id="64e64-121">__Summary of Impact__: Some users were unable to log in to the PowerShell Gallery using Azure AD Accounts.</span></span>

<span data-ttu-id="64e64-122">__Grundursache__: Bei einem Update für eine sicherere Interaktion mit AAD wurde eine Einstellung nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="64e64-122">__Root Cause__: During an update to interact more securely with AAD, a setting change was missed.</span></span>
<span data-ttu-id="64e64-123">Die Tests zur Überprüfung der Änderung umfassten bestimmte Arten von AAD-Konten nicht, daher wurde die Bereitstellung fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="64e64-123">The testing done to validate the change did not include certain types of AAD accounts, so the deployment proceeded.</span></span>

<span data-ttu-id="64e64-124">__Lösung__: Techniker haben die fehlende Einstellung ermittelt und das Problem behoben.</span><span class="sxs-lookup"><span data-stu-id="64e64-124">__Resolution__: Engineers identified the missing setting and corrected the problem.</span></span>

<span data-ttu-id="64e64-125">__Nächste Schritte__: Wir ändern unsere Tests, sodass eine größere Gruppe von AAD-Kontotypen einbezogen wird.</span><span class="sxs-lookup"><span data-stu-id="64e64-125">__Next Steps__: We will be modifying our testing to include a broader set of AAD account types.</span></span>

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="64e64-126">27.03.2017 – GELÖST: Einzelne Modul- und Skriptseiten können nicht angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="64e64-126">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="64e64-127">__Zusammenfassung der Auswirkungen__: Die direkten Links zu einzelnen Modul- und Skriptseiten auf https://www.powershellgallery.com haben nicht funktioniert.</span><span class="sxs-lookup"><span data-stu-id="64e64-127">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="64e64-128">Dies wurde aus allen Regionen gemeldet.</span><span class="sxs-lookup"><span data-stu-id="64e64-128">This was being reported across all the regions.</span></span> <span data-ttu-id="64e64-129">Dies hat sich nicht auf alle PowerShellGet-Cmdlets ausgewirkt, d.h. Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script haben weiterhin funktioniert.</span><span class="sxs-lookup"><span data-stu-id="64e64-129">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt continued to work.</span></span>

<span data-ttu-id="64e64-130">__Grundursache__: Laut unseren Technikern ist die Ursache ein Problem bei der Einbindung von Schaltflächen für soziale Netzwerke, z.B. Facebook, auf der Seite.</span><span class="sxs-lookup"><span data-stu-id="64e64-130">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>

<span data-ttu-id="64e64-131">__Lösung__: Die Techniker haben das Problem gelöst, indem sie die Facebook-Kontoinformationen deaktiviert haben.</span><span class="sxs-lookup"><span data-stu-id="64e64-131">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="64e64-132">__Nächste Schritte__: Wir haben ein internes Nachverfolgungsproblem geöffnet, um unseren Gebrauch der Facebook-API zu reparieren.</span><span class="sxs-lookup"><span data-stu-id="64e64-132">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="64e64-133">15.12.2016 – Es konnten keine E-Mails über die PowerShell-Katalogwebsite gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="64e64-133">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="64e64-134">__Zusammenfassung der Auswirkungen__: Zwischen dem 13. und 15. Dezember 2016 über „Contact owners“ (Besitzer kontaktieren), „Manage Owners“ (Besitzer verwalten), „Support kontaktieren“ oder „Missbrauch melden“ gesendete E-Mails wurden von den Administratoren des PowerShell-Katalogs nicht empfangen.</span><span class="sxs-lookup"><span data-stu-id="64e64-134">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="64e64-135">__Grundursache__: Das Problem wurde von Technikern auf einen Authentifizierungsfehler beim SMTP-Server zurückgeführt.</span><span class="sxs-lookup"><span data-stu-id="64e64-135">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>
<span data-ttu-id="64e64-136">__Lösung__: Techniker konnten das Authentifizierungsproblem lösen und die Verbindung mit dem SMTP-Server wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="64e64-136">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>
<span data-ttu-id="64e64-137">__Nächste Schritte__: Wenn Sie die Links „Contact owners“ (Besitzer kontaktieren), „Manage Owners“ (Besitzer verwalten), „Support kontaktieren“ oder „Missbrauch melden“ während dieses Zeitraums an cgadmin@microsoft.com gesendet und keine Antwort erhalten haben, versuchen Sie es erneut.</span><span class="sxs-lookup"><span data-stu-id="64e64-137">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="64e64-138">Wir entschuldigen uns für eventuelle Unannehmlichkeiten.</span><span class="sxs-lookup"><span data-stu-id="64e64-138">We apologize for the inconvenience.</span></span>



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="64e64-139">10.08.2016 – Gelöst: Senden von E-Mails an cgadmin@microsoft.com nicht möglich</span><span class="sxs-lookup"><span data-stu-id="64e64-139">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>

<span data-ttu-id="64e64-140">__Zusammenfassung der Auswirkungen__: Vom 05.08.2016 bis zum 10.08.2016 konnten Kunden keine E-Mails an cgadmin@microsoft.com senden bzw. die Funktion zur Kontaktaufnahme nicht nutzen.</span><span class="sxs-lookup"><span data-stu-id="64e64-140">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>
<span data-ttu-id="64e64-141">__Grundursache__: Als Ursache haben Techniker eine Konfigurationsänderung des E-Mail-Kontos ausgemacht.</span><span class="sxs-lookup"><span data-stu-id="64e64-141">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>
<span data-ttu-id="64e64-142">__Lösung__: Techniker haben das Konfigurationsproblem behoben.</span><span class="sxs-lookup"><span data-stu-id="64e64-142">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>
<span data-ttu-id="64e64-143">__Nächste Schritte__: Wenn Sie in diesem Zeitraum den Link zur Kontaktaufnahme genutzt oder eine E-Mail an cgadmin@microsoft.com gesendet und wir nicht geantwortet haben, versuchen Sie es erneut.</span><span class="sxs-lookup"><span data-stu-id="64e64-143">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="64e64-144">Vielen Dank für Ihre Geduld.</span><span class="sxs-lookup"><span data-stu-id="64e64-144">Thank you for your patience.</span></span>



## <a name="7132016---download-items-failed"></a><span data-ttu-id="64e64-145">13.07.2016 – Herunterladen von Elementen nicht möglich</span><span class="sxs-lookup"><span data-stu-id="64e64-145">7/13/2016 - Download Items Failed</span></span>

<span data-ttu-id="64e64-146">__Zusammenfassung der Auswirkungen__: Vom 11.7.2016 bis 13.7.2016 hatten Kunden teilweise Probleme beim Herunterladen von Elementen aus dem PowerShell-Katalog.</span><span class="sxs-lookup"><span data-stu-id="64e64-146">__Summary of Impact__: Between 7/11/2016 and 7/13/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="64e64-147">Das Problem manifestierte sich in der folgenden Fehlermeldung, die von „Install-Module/Install-Script“ und „Save-Module/Save-Script“ zurückgegeben wurde:</span><span class="sxs-lookup"><span data-stu-id="64e64-147">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
PS C:\> Install-Module xStorage
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because:
End of Central Directory record could not be found. At C:\Program
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ...
$null = PackageManagement\Install-Package @PSBoundParameters +
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult:
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}'
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage
```

<span data-ttu-id="64e64-148">__Vorläufige Grundursache__: Techniker haben ein Problem mit dem Azure Content Delivery Network (CDN) ausgemacht, das am 11.7.2016 im PowerShell-Katalog bereitgestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="64e64-148">__Preliminary root cause__: Engineers identified an issue with Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 7/11/2016.</span></span>
<span data-ttu-id="64e64-149">__Lösung__: Techniker haben Azure CDN im PowerShell-Katalog deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="64e64-149">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>
<span data-ttu-id="64e64-150">__Nächste Schritte__: Untersuchen der Grundursache und Entwickeln einer Lösung, um zu verhindern, dass dies künftig erneut vorkommt.</span><span class="sxs-lookup"><span data-stu-id="64e64-150">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>


## <a name="5192016---download-items-failed"></a><span data-ttu-id="64e64-151">19.05.2016 – Herunterladen von Elementen nicht möglich</span><span class="sxs-lookup"><span data-stu-id="64e64-151">5/19/2016 - Download Items Failed</span></span>
<span data-ttu-id="64e64-152">__Zusammenfassung der Auswirkungen__: Vom 17.5.2016 bis 19.5.2016 hatten Kunden teilweise Probleme beim Herunterladen von Elementen aus dem PowerShell-Katalog.</span><span class="sxs-lookup"><span data-stu-id="64e64-152">__Summary of Impact__: Between 5/17/2016 and 5/19/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="64e64-153">Das Problem manifestierte sich in der folgenden Fehlermeldung, die von „Install-Module/Install-Script“ und „Save-Module/Save-Script“ zurückgegeben wurde:</span><span class="sxs-lookup"><span data-stu-id="64e64-153">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because:
End of Central Directory record could not be found.
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install.
WARNING: Package 'AzureRM' failed to install.
VERBOSE: Module 'AzureRM.Network' was saved successfully.
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the
module 'AzureRM'.
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully.
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 +
$null = PackageManagement\Save-Package @PSBoundParameters +
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ +
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage)
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage
```

<span data-ttu-id="64e64-154">__Vorläufige Grundursache__: Techniker haben ein Problem mit dem Azure Content Delivery Network (CDN) ausgemacht, das am 17.5.2016 im PowerShell-Katalog bereitgestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="64e64-154">__Preliminary root cause__: Engineers identified an outage in the underlying provider of Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 5/17/2016.</span></span>
<span data-ttu-id="64e64-155">__Lösung__: Techniker haben Azure CDN im PowerShell-Katalog deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="64e64-155">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>
<span data-ttu-id="64e64-156">__Nächste Schritte__: Untersuchen der Grundursache und Entwickeln einer Lösung, um zu verhindern, dass dies künftig erneut vorkommt.</span><span class="sxs-lookup"><span data-stu-id="64e64-156">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>