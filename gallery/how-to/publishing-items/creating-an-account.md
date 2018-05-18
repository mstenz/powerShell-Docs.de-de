---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: Erstellen eines PowerShell-Katalogkontos
ms.openlocfilehash: 3ec9ad8f979fc0b88fbee72fc28ad1e3394eb01d
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
## <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="7dac8-103">Erstellen eines PowerShell-Katalogkontos</span><span class="sxs-lookup"><span data-stu-id="7dac8-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="7dac8-104">Bevor Elemente im PowerShell-Katalog veröffentlicht werden können, muss ein PowerShell-Katalogkonto eingerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="7dac8-104">A PowerShell Gallery account must be established before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="7dac8-105">Das PowerShell-Katalogkonto muss mit einem E-Mail-aktivierten Azure Active Directory-Konto oder mit einem Microsoft-E-Mail-Konto (mit der Domäne outlook.com, hotmail.com usw.) verknüpft werden.</span><span class="sxs-lookup"><span data-stu-id="7dac8-105">The PowerShell Gallery accounts must be linked to an Azure Active Directory email-enabled account, or a Microsoft email account (with a domain of outlook.com, hotmail.com, etc.)</span></span>

<span data-ttu-id="7dac8-106">Besuchen Sie https://PowerShellGallery.com, und klicken Sie auf „Register“ (Registrieren), um ein PowerShell-Katalogkonto zu erstellen (siehe Abbildung unten).</span><span class="sxs-lookup"><span data-stu-id="7dac8-106">To create a PowerShell Gallery account, go to https://PowerShellGallery.com and click on "Register" (see the image below).</span></span>

![Registrieren eines neuen Kontos](../../Images/CreatingAccount-Register.png)

<span data-ttu-id="7dac8-108">Verwenden Sie auf der nächsten Seite ein Azure Active Directory-Konto, wählen Sie „Work or School Account“ (Geschäfts-, Schul- oder Unikonto) aus, und melden Sie sich mit Ihrem Konto an.</span><span class="sxs-lookup"><span data-stu-id="7dac8-108">In the next page, to use an Azure Active Directory account, select "Work or School Account", and log in with your account.</span></span>
<span data-ttu-id="7dac8-109">Um ein Microsoft-Konto zu verwenden – beispielsweise in der Domäne Hotmail.com oder Outlook.com –, wählen Sie „Personal Account“ (Privates Konto) aus, und melden Sie sich an. </span><span class="sxs-lookup"><span data-stu-id="7dac8-109">To use a Microsoft account - such as one in a Hotmail.com or Outlook.com domain - choose "Personal Account", and log in.</span></span>

<span data-ttu-id="7dac8-110">Nach der Anmeldung werden Sie aufgefordert, einen Benutzernamen für den PowerShell-Katalog zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7dac8-110">Once you have logged in, you will be prompted to create a username for the PowerShell Gallery.</span></span>
<span data-ttu-id="7dac8-111">Lesen Sie die verlinkten Nutzungsbestimmungen und die Datenschutzrichtlinie, geben Sie einen Benutzernamen ein, und klicken Sie dann auf „Register“ (Registrieren).</span><span class="sxs-lookup"><span data-stu-id="7dac8-111">Review the Terms of Use and Privacy Policy that are linked in, enter a username, and then click Register.</span></span>

<span data-ttu-id="7dac8-112">Hinweis: Dieser Kontoname kann nach der Erstellung nicht mehr geändert werden.</span><span class="sxs-lookup"><span data-stu-id="7dac8-112">Note: This account name cannot be changed once it is created.</span></span>
<span data-ttu-id="7dac8-113">Weitere Informationen hierzu finden Sie unter [Verwalten von Elementbesitzern](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners).</span><span class="sxs-lookup"><span data-stu-id="7dac8-113">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details related to this.</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="7dac8-114">Empfohlene Vorgehensweisen für PowerShell-Katalogkonten</span><span class="sxs-lookup"><span data-stu-id="7dac8-114">Recommended Practices for PowerShell Gallery Accounts</span></span>

<span data-ttu-id="7dac8-115">Es ist wichtig, dass mit Ihrem PowerShell-Katalogkonto verwendete E-Mail-Konto aktiv zu überwachen.</span><span class="sxs-lookup"><span data-stu-id="7dac8-115">It is important that the email account used with your PowerShell Gallery account be actively monitored.</span></span>
<span data-ttu-id="7dac8-116">Die gesamte Kommunikation mit Besitzern von PowerShell-Katalogelementen erfolgt über die E-Mail-Adresse, die Ihrem PowerShell-Katalogkonto zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="7dac8-116">All communiction with owners of PowerShell Gallery items is through the email using the address associated with your PowerShell Gallery account.</span></span>
<span data-ttu-id="7dac8-117">Wenn Sie einen Elementbesitzer nicht erreichen können, kann es unter bestimmten Umständen erforderlich sein, ein Element durch das Team für den Katalogbetrieb löschen zu lassen.</span><span class="sxs-lookup"><span data-stu-id="7dac8-117">If we are unable to contact an item owner, the Operations team may be required to delete an item under some circumstances.</span></span>

<span data-ttu-id="7dac8-118">Organisationen, die Elemente im PowerShell-Katalog veröffentlichen, erstellen zu diesem Zweck häufig ein eindeutiges Konto in Outlook.com oder einer anderen Microsoft-Kontodomäne.</span><span class="sxs-lookup"><span data-stu-id="7dac8-118">Organizations that publish to the PowerShell Gallery often create a unique account for that purpose in Outlook.com, or another Microsoft account domain.</span></span>
<span data-ttu-id="7dac8-119">Oft wird dieses Konto nicht regelmäßig überwacht.</span><span class="sxs-lookup"><span data-stu-id="7dac8-119">In many cases that account is not regularly monitored.</span></span>
<span data-ttu-id="7dac8-120">Eine bewährte Methode ist in diesem Fall die Outlook-Weiterleitung von E-Mails an ein anderes Konto – typischerweise innerhalb der Organisation –, das vom Elementbesitzer überwacht wird.</span><span class="sxs-lookup"><span data-stu-id="7dac8-120">A best practice in that case is to use Outlook Forwarding to send email to another account, typically one within the organization, that will be monitored by the item owner(s).</span></span>

<span data-ttu-id="7dac8-121">Wenn einem Element mehrere Besitzer zugeordnet sind, wird die gesamte vom PowerShell-Katalog ausgehende Kommunikation an alle Benutzer gesendet.</span><span class="sxs-lookup"><span data-stu-id="7dac8-121">If there are multiple owners associated with an item, all communications that come from the PowerShell Gallery will go to all owners.</span></span>
<span data-ttu-id="7dac8-122">Ausführliche Informationen zum Hinzufügen von Besitzern zu einem Element finden Sie unter [Verwalten von Elementbesitzern](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners).</span><span class="sxs-lookup"><span data-stu-id="7dac8-122">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details on adding owners to an item.</span></span>