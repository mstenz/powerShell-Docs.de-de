---
ms.date: 03/27/2018
contributor: JKeithB
keywords: katalog,powershell,psgallery,GDPR
title: DSGVO-Kompatibilität für den PowerShell-Katalog
ms.openlocfilehash: fb1191d8a1cd12d5994e41238c384eb504d0c261
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328321"
---
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="b0f5d-103">DSGVO-Kompatibilität für den PowerShell-Katalog</span><span class="sxs-lookup"><span data-stu-id="b0f5d-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="b0f5d-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="b0f5d-104">Overview</span></span>

<span data-ttu-id="b0f5d-105">Im Mai 2018 trat die Datenschutz-Grundverordnung (DSGVO) der Europäischen Union in Kraft.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), took effect.</span></span>
<span data-ttu-id="b0f5d-106">Im Rahmen der DSGVO treten neue Regeln für Unternehmen, Behörden und gemeinnützige sowie andere Organisationen in Kraft, die den Verbrauchern in der Europäischen Union Güter und Dienstleitungen anbieten bzw. personenbezogene Daten der EU-Bürger sammeln und analysieren.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span>
<span data-ttu-id="b0f5d-107">Diese Grundverordnung gilt unabhängig von Ihrem Unternehmenssitz.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="b0f5d-108">In diesem Artikel wird erläutert, wie Sie personenbezogene Daten aus dem PowerShell-Katalog löschen und Ihre Verpflichtungen gemäß der DSGVO erfüllen.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="b0f5d-109">Allgemeine Informationen zur DSGVO finden Sie unter [GDPR section of the Service Trust portal (DSGVO-Bereich des Service Trust Portals)](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span><span class="sxs-lookup"><span data-stu-id="b0f5d-109">If you’re looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="b0f5d-110">Personenbezogene Daten</span><span class="sxs-lookup"><span data-stu-id="b0f5d-110">Personally identifiable data</span></span>

<span data-ttu-id="b0f5d-111">Im PowerShell-Katalog werden die folgenden Informationen gespeichert, die möglicherweise von Benutzern bereitgestellt werden und personenbezogene Daten enthalten:</span><span class="sxs-lookup"><span data-stu-id="b0f5d-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

- <span data-ttu-id="b0f5d-112">PowerShell-Katalog-Konto</span><span class="sxs-lookup"><span data-stu-id="b0f5d-112">PowerShell Gallery account</span></span>
- <span data-ttu-id="b0f5d-113">Im PowerShell-Katalog veröffentlichte Pakete</span><span class="sxs-lookup"><span data-stu-id="b0f5d-113">Packages published to the PowerShell Gallery</span></span>
- <span data-ttu-id="b0f5d-114">E-Mail-Korrespondenz mit dem PowerShell-Katalog-Team</span><span class="sxs-lookup"><span data-stu-id="b0f5d-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="b0f5d-115">Die meisten Benutzer erstellen kein Konto für den PowerShell-Katalog.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-115">Most users do not create a PowerShell Gallery account.</span></span>
<span data-ttu-id="b0f5d-116">Ein Konto ist nur erforderlich, wenn Sie ein Paket veröffentlichen oder das Feature „Besitzer kontaktieren“ im PowerShell-Katalog verwenden wollen.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-116">An account is not required unless you are going to publish a package or use the "Contact Owner" feature in the PowerShell Gallery.</span></span>
<span data-ttu-id="b0f5d-117">Neben der vom Benutzer ausgehenden E-Mail-Korrespondenz speichert der PowerShell-Katalog keine personenbezogenen Daten von Benutzern, die kein Konto erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="b0f5d-118">Benutzer, die ein Konto im PowerShell-Katalog erstellen, können dort Pakete veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-118">Users who create a PowerShell Gallery account can publish packages to the PowerShell Gallery.</span></span>
<span data-ttu-id="b0f5d-119">Es wird zwar erwartet, dass es sich bei diesen Paketen um PowerShell-Code handelt, sie können jedoch auch andere Informationen enthalten, z.B. personenbezogene Daten.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-119">Those packages are expected to be PowerShell code, but may contain other information including personal information.</span></span>
<span data-ttu-id="b0f5d-120">Im Folgenden erhalten Sie Informationen dazu, wie Sie sämtliche Pakete abrufen, die Sie im PowerShell-Katalog veröffentlicht haben.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-120">The information below will show how you can get all the packages you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="b0f5d-121">DSR-Export von Daten aus dem PowerShell-Katalog</span><span class="sxs-lookup"><span data-stu-id="b0f5d-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="b0f5d-122">In den folgenden Abschnitten wird erläutert, wie der PowerShell-Katalog sämtliche DSR-Anforderungen (Data Subject Rights) unterstützt. Sie erhalten Informationen dazu, wie Sie im PowerShell-Katalog gespeicherte Informationen exportieren und wie Sie das Löschen dieser Informationen anfordern.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="b0f5d-123">E-Mail</span><span class="sxs-lookup"><span data-stu-id="b0f5d-123">Email</span></span>

<span data-ttu-id="b0f5d-124">Die E-Mail-Korrespondenz kann Folgendes umfassen:</span><span class="sxs-lookup"><span data-stu-id="b0f5d-124">Email correspondence may include any of the following:</span></span>

- <span data-ttu-id="b0f5d-125">E-Mails an Besitzer von Paketen im PowerShell-Katalog, wenn die Codeanalyse ein Problem mit einem Paket erkennt, das diese im PowerShell-Katalog veröffentlicht haben</span><span class="sxs-lookup"><span data-stu-id="b0f5d-125">Email sent to the owners of PowerShell Gallery packages if the code analysis scans detected an issue with any package they have published to the PowerShell Gallery</span></span>
- <span data-ttu-id="b0f5d-126">E-Mail von einer beliebigen Person an das PowerShell-Katalogteam, die an die auf der Seite „Kontakt“ ([cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)) genannte E-Mail-Adresse gesendet wurde</span><span class="sxs-lookup"><span data-stu-id="b0f5d-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)</span></span>
- <span data-ttu-id="b0f5d-127">E-Mails registrierter Benutzer, die im PowerShell-Katalog das Feature „Besitzer kontaktieren“ verwenden, um eine E-Mail an den Besitzer eines Pakets zu senden, das sich im PowerShell-Katalog befindet</span><span class="sxs-lookup"><span data-stu-id="b0f5d-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of a package in the PowerShell Gallery</span></span>

<span data-ttu-id="b0f5d-128">Für E-Mails, die vom PowerShell-Katalog oder an diesen gesendet werden, gilt eine Aufbewahrungsrichtlinie, gemäß derer die E-Mails 90 Tage lang für mögliche Sicherheitsuntersuchungen gespeichert werden müssen, die durchgeführt werden, wenn schädlicher Code im PowerShell-Katalog entdeckt werden sollte.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span>
<span data-ttu-id="b0f5d-129">Gemäß der Richtlinie werden diese E-Mails nach 90 Tagen gelöscht.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="b0f5d-130">Sie können innerhalb von 90 Tagen Kopien aller E-Mails anfordern, die Sie mit Ihrer E-Mail-Adresse oder dem PowerShell-Katalog gesendet haben oder die an Sie gesendet wurden.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span>
<span data-ttu-id="b0f5d-131">Um diese Zuordnung anzufordern, senden Sie eine E-Mail mit dem folgenden Titel an [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com): DSR-Anforderung für E-Mails im Zusammenhang mit diesem Konto.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-131">To request this correspondence, send an email to [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com), with the title: "DSR Request for emails relating to this account".</span></span>
<span data-ttu-id="b0f5d-132">Geben Sie in dieser E-Mail an, welche Informationen Sie anfordern (Beispiel: Bitte übermitteln Sie alle E-Mail-Nachrichten, die an diese E-Mail-Adresse gesendet oder von ihr empfangen wurden). Alle E-Mails der letzten 90 Tage, die Ihre E-Mail-Adresse betreffen, werden innerhalb von sieben Werktagen an Sie gesendet.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="b0f5d-133">Informationen zum PowerShell-Katalog-Konto</span><span class="sxs-lookup"><span data-stu-id="b0f5d-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="b0f5d-134">Wenn Sie ein PowerShell-Katalog-Konto erstellt haben, finden Sie sämtliche personenbezogenen Daten, die im PowerShell-Katalog gespeichert wurden, indem Sie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="b0f5d-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="b0f5d-135">Melden Sie sich im PowerShell-Katalog an, und klicken Sie auf Ihren Benutzernamen</span><span class="sxs-lookup"><span data-stu-id="b0f5d-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="b0f5d-136">Dann wird als nächstes die Seite „Konto“ angezeigt, auf der Sie die E-Mail-Adresse sehen, die für das PowerShell-Katalog-Konto verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="b0f5d-137">Wenn Sie mehr als ein Konto im PowerShell-Katalog erstellt haben, müssen Sie diese Schritte für jedes einzelne Konto ausführen.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="packages-in-the-powershell-gallery"></a><span data-ttu-id="b0f5d-138">Pakete im PowerShell-Katalog</span><span class="sxs-lookup"><span data-stu-id="b0f5d-138">Packages in the PowerShell Gallery</span></span>

<span data-ttu-id="b0f5d-139">Um das Exportieren von im PowerShell-Katalog veröffentlichten Pakete zu vereinfachen, wurde das Skript „GetPSGalleryItemsForAuthor“ im PowerShell-Katalog veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-139">To facilitate exporting packages published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span>
<span data-ttu-id="b0f5d-140">Dieses Skript exportiert auf Grundlage der im Paket gespeicherten Autorinformationen eine Kopie jeder Version von jedem Paket, das im PowerShell-Katalog gespeichert wurde.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-140">This script exports a copy of every version of every package put into the PowerShell Gallery based on the author information stored in the package.</span></span>

> [!NOTE]
> <span data-ttu-id="b0f5d-141">Der Autor wird im Paketmanifest gespeichert, wenn Sie Ihr Paket veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-141">The Author is stored in the package manifest when you publish your package.</span></span>
> <span data-ttu-id="b0f5d-142">Es gibt keine Garantie dafür, dass der Autor dieselbe Identität aufweist wie das von Ihnen im PowerShell-Katalog verwendete Konto.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span>
> <span data-ttu-id="b0f5d-143">Wenn Sie im Feld „Autor“ einen anderen Wert verwenden, müssen Sie den Wert angeben, wenn Sie dieses Skript verwenden.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="b0f5d-144">Sie können das Skript über den folgenden PowerShell-Befehl downloaden:</span><span class="sxs-lookup"><span data-stu-id="b0f5d-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script Get-repository psgallery
```

<span data-ttu-id="b0f5d-145">Sie können das Skript direkt ausführen, indem Sie den folgenden PowerShell-Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="b0f5d-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="b0f5d-146">Sie werden aufgefordert, den Autor und einen Ordner in Ihrem System anzugeben, in dem die Pakete gespeichert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-146">You will be prompted to supply the Author and a folder on your system where you want the packages to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="b0f5d-147">Löschen von personenbezogenen Daten aus dem PowerShell-Katalog</span><span class="sxs-lookup"><span data-stu-id="b0f5d-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="b0f5d-148">Um Ihr PowerShell-Katalogkonto oder ein beliebiges Paket zu löschen, das Sie im PowerShell-Katalog besitzen, senden Sie eine E-Mail an cgadmin@microsoft.com mit dem Betreff: „DSGVO-Anfrage für Elemente in Zusammenhang mit diesem Konto“.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-148">To delete your PowerShell Gallery account or any package you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span>
<span data-ttu-id="b0f5d-149">Geben Sie in dieser E-Mail an, welche Informationen gelöscht werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="b0f5d-150">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b0f5d-150">For example:</span></span>

- <span data-ttu-id="b0f5d-151">Bitte löschen Sie Version x.y.z des Pakets „Paketname“.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-151">Please delete version x.y.z of my package "package name"</span></span>
- <span data-ttu-id="b0f5d-152">Bitte löschen Sie alle Versionen des Pakets „Paketname“.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-152">Please delete all versions of my package "package name"</span></span>
- <span data-ttu-id="b0f5d-153">Bitte löschen Sie mein PowerShell-Katalog-Konto</span><span class="sxs-lookup"><span data-stu-id="b0f5d-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="b0f5d-154">Die Administratoren von PowerShell-Katalog werden Ihnen innerhalb von sieben Werktagen eine Antwort zukommen lassen.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="b0f5d-155">Die angegebenen Pakete werden innerhalb von 30 Tagen nach Senden der Anfrage gelöscht.</span><span class="sxs-lookup"><span data-stu-id="b0f5d-155">The packages specified will be deleted within 30 days after the request is sent.</span></span>
