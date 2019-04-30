---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Verwalten von Paketbesitzern
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084146"
---
# <a name="managing-package-owners"></a><span data-ttu-id="cc131-103">Verwalten von Paketbesitzern</span><span class="sxs-lookup"><span data-stu-id="cc131-103">Managing package owners</span></span>

<span data-ttu-id="cc131-104">Der Besitz eines Pakets im PowerShell-Katalog wird durch die Person definiert, die das Paket im Katalog veröffentlicht hat.</span><span class="sxs-lookup"><span data-stu-id="cc131-104">Ownership of a package in the PowerShell Gallery is defined by who published the package to the gallery.</span></span>
<span data-ttu-id="cc131-105">Mitunter müssen diese Metadaten über die erste Veröffentlichung des Pakets hinaus verwaltet werden, was bedeutet, dass die Besitzermetadaten veränderlich sein müssen, das Paket hingegen nicht.</span><span class="sxs-lookup"><span data-stu-id="cc131-105">Sometimes this metadata needs to be managed beyond the initial package publishing, which means the owner metadata needs to be mutable while the package itself is not.</span></span>

<span data-ttu-id="cc131-106">Alle Paketbesitzer sind Peers.</span><span class="sxs-lookup"><span data-stu-id="cc131-106">All package owners are peers.</span></span>
<span data-ttu-id="cc131-107">Das bedeutet, dass alle Paketbesitzer eine neue Version eines Pakets veröffentlichen können.</span><span class="sxs-lookup"><span data-stu-id="cc131-107">This means any package owner can publish a new version of an package.</span></span> <span data-ttu-id="cc131-108">Es bedeutet aber auch, dass jeder Paketbesitzer jeden anderen Paketbesitzer entfernen kann.</span><span class="sxs-lookup"><span data-stu-id="cc131-108">It also means that any package owner can remove any other package owner.</span></span>
<span data-ttu-id="cc131-109">Kein Besitzer verfügt über mehr Berechtigungen als andere Besitzer.</span><span class="sxs-lookup"><span data-stu-id="cc131-109">No owner has more authority than other owners.</span></span>

## <a name="setting-a-packages-initial-owner"></a><span data-ttu-id="cc131-110">Festlegen des anfänglichen Besitzers eines Pakets</span><span class="sxs-lookup"><span data-stu-id="cc131-110">Setting a Package's Initial Owner</span></span>

<span data-ttu-id="cc131-111">Beim Veröffentlichen eines neues Pakets im PowerShell-Katalog wird der anfängliche Besitzer durch den Benutzer definiert, der das Paket veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="cc131-111">When a new package is published to PowerShell Gallery, the initial owner is defined by the user that published the package.</span></span> <span data-ttu-id="cc131-112">Dies richtet sich danach, wessen API-Schlüssel im Cmdlet „Publish-Modul“ verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="cc131-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="cc131-113">Hinzufügen von Besitzern</span><span class="sxs-lookup"><span data-stu-id="cc131-113">Adding Owners</span></span>

<span data-ttu-id="cc131-114">Sobald ein Paket im PowerShell-Katalog veröffentlicht wurde, können ganz einfach zusätzliche Benutzer als Besitzer eines Pakets eingeladen werden.</span><span class="sxs-lookup"><span data-stu-id="cc131-114">Once a package has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of a package.</span></span>

1. <span data-ttu-id="cc131-115">[Melden Sie sich beim PowerShell-Katalog mit dem Konto an](https://powershellgallery.com/users/account/LogOn), das der aktuelle Besitzer eines Pakets ist.</span><span class="sxs-lookup"><span data-stu-id="cc131-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of a package.</span></span>
2. <span data-ttu-id="cc131-116">Navigieren Sie zu einer Paketseite, indem Sie die Registerkarte „Pakete“ verwenden, suchen oder auf Ihren Benutzernamen und dann auf [**Meine Pakete verwalten**](https://www.powershellgallery.com/account/Packages) klicken.</span><span class="sxs-lookup"><span data-stu-id="cc131-116">Navigate to a package page using the 'Items' tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="cc131-117">Wenn Sie als Besitzer eines Pakets angemeldet sind, finden Sie auf der linken Seite einen Link „Besitzer verwalten“, auf den Sie klicken können.</span><span class="sxs-lookup"><span data-stu-id="cc131-117">When logged on as an package's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="cc131-118">Geben Sie den Benutzernamen der Person ein, die Sie als Besitzer hinzufügen möchten, und klicken Sie auf „Hinzufügen“.</span><span class="sxs-lookup"><span data-stu-id="cc131-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="cc131-119">Eine E-Mail wird an den neuen Mitbesitzer gesendet, um ihn als Besitzer eines Pakets einzuladen.</span><span class="sxs-lookup"><span data-stu-id="cc131-119">An email is then sent to the new co-owner, as an invitation to become an owner of a package.</span></span>
6. <span data-ttu-id="cc131-120">Sobald der Benutzer auf den Link klickt, ist er ein vollständiger Mitbesitzer mit Vollzugriff auf ein Paket, einschließlich der Möglichkeit, andere Benutzer als Besitzer zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="cc131-120">Once that user clicks the link, they are a full co-owner with full control over a package, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="cc131-121">**HINWEIS**: Der neue Besitzer wird *erst dann* als Besitzer eines Pakets aufgeführt, wenn er den Besitz bestätigt.</span><span class="sxs-lookup"><span data-stu-id="cc131-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of a package.</span></span>
<span data-ttu-id="cc131-122">Beim Anzeigen der Seite **Besitzer verwalten** sehen Sie bei den aktuellen Besitzern einen Eintrag „Genehmigung steht aus“.</span><span class="sxs-lookup"><span data-stu-id="cc131-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="cc131-123">Diese Einladung kann ebenso entfernt werden wie andere Besitzer entfernt werden können.</span><span class="sxs-lookup"><span data-stu-id="cc131-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="cc131-124">Dieser Einladungsprozess verhindert, dass Benutzer fälschlicherweise andere Benutzer als Besitzer ihrer Pakete hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="cc131-124">This process of invitations prevents users from falsely adding other users as owners of their packages.</span></span>

<span data-ttu-id="cc131-125">Beachten Sie, dass die Metadaten „Autoren“ in reinem Freiformtext vorliegen. Nur „Besitzer“ werden gesteuert.</span><span class="sxs-lookup"><span data-stu-id="cc131-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="cc131-126">Entfernen von Besitzern</span><span class="sxs-lookup"><span data-stu-id="cc131-126">Removing Owners</span></span>

<span data-ttu-id="cc131-127">Wenn ein Paket mehrere Besitzer aufweist und einer entfernt werden muss, ist der Prozess einfach:</span><span class="sxs-lookup"><span data-stu-id="cc131-127">When a package has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="cc131-128">[Melden Sie sich beim PowerShell-Katalog mit dem Konto an](https://powershellgallery.com/users/account/LogOn), das der aktuelle Besitzer eines Paket ist.</span><span class="sxs-lookup"><span data-stu-id="cc131-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of a package;</span></span>
2. <span data-ttu-id="cc131-129">Navigieren Sie zu einer Paketseite, indem Sie die Registerkarte „Pakete“ verwenden, suchen oder auf Ihren Benutzernamen und dann auf [**Meine Pakete verwalten**](https://www.powershellgallery.com/account/Packages) klicken.</span><span class="sxs-lookup"><span data-stu-id="cc131-129">Navigate to a package page using the Packages tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="cc131-130">Wenn Sie als Besitzer eines Pakets angemeldet sind, finden Sie auf der linken Seite einen Link „Besitzer verwalten“, auf den Sie klicken können.</span><span class="sxs-lookup"><span data-stu-id="cc131-130">When logged on as a package's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="cc131-131">Klicken Sie neben dem Besitzer, der entfernt werden soll, auf den Link „Entfernen“.</span><span class="sxs-lookup"><span data-stu-id="cc131-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-package-ownership"></a><span data-ttu-id="cc131-132">Übertragen des Paketbesitzes</span><span class="sxs-lookup"><span data-stu-id="cc131-132">Transferring Package Ownership</span></span>

<span data-ttu-id="cc131-133">Gelegentlich erhalten wir Supportanfragen, um den Besitz eines Pakets von einem Benutzer auf einen anderen zu übertragen. Diesen Vorgang können Sie allerdings fast immer selbst durchführen.</span><span class="sxs-lookup"><span data-stu-id="cc131-133">We sometimes get support requests to transfer package ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="cc131-134">Das Übertragen des Besitzes von einem Benutzer auf einen anderen ist einfach eine Kombination aus den beiden oben genannten Funktionen.</span><span class="sxs-lookup"><span data-stu-id="cc131-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="cc131-135">Der aktuelle Besitzer lädt den neuen Benutzer als Mitbesitzer ein, und der neue Benutzer akzeptiert die Einladung.</span><span class="sxs-lookup"><span data-stu-id="cc131-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="cc131-136">Der neue Benutzer entfernt den alten Benutzer aus der Liste der Besitzer.</span><span class="sxs-lookup"><span data-stu-id="cc131-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="cc131-137">Diese Anfrage ist über mehrere Formulare eingegangen, der Prozess funktioniert aber immer gleich.</span><span class="sxs-lookup"><span data-stu-id="cc131-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="cc131-138">Der Besitz eines Pakets wechselt von einem Entwickler zu einem anderen.</span><span class="sxs-lookup"><span data-stu-id="cc131-138">The package ownership is changing from one developer to another</span></span>
- <span data-ttu-id="cc131-139">Das Paket wurde versehentlich über das falsche Konto veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="cc131-139">The package was accidentally published using the wrong account</span></span>


## <a name="orphaned-packages"></a><span data-ttu-id="cc131-140">Verwaiste Pakete</span><span class="sxs-lookup"><span data-stu-id="cc131-140">Orphaned Packages</span></span>

<span data-ttu-id="cc131-141">Ein letztes Szenario ist aufgetreten, wenn auch nicht häufig.</span><span class="sxs-lookup"><span data-stu-id="cc131-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="cc131-142">Pakete waren verwaist und das einzige Paketbesitzerkonto kann nicht zum Hinzufügen neuer Besitzer verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="cc131-142">Packages have become orphans and the only package owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="cc131-143">Im Folgenden sind einige Beispiele für dieses Szenario aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="cc131-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="cc131-144">Dem Konto des Besitzers ist eine E-Mail-Adresse zugeordnet, die nicht mehr existiert, und der Benutzer hat das Kennwort vergessen.</span><span class="sxs-lookup"><span data-stu-id="cc131-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="cc131-145">Der registrierte Besitzer hat das Unternehmen verlassen, in dem das Paket erzeugt wird, und kann nicht erreicht werden, um den Besitz des Pakets zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="cc131-145">The registered owner has left the company that produces the package and cannot be reached to update the package ownership</span></span>
- <span data-ttu-id="cc131-146">Aufgrund eines Fehlers, der nur wenige Pakete betrifft, befindet sich das Paket ohne Besitzer im Katalog.</span><span class="sxs-lookup"><span data-stu-id="cc131-146">Due to a bug that has only affected a handful of packages, the package is somehow ownerless on the gallery</span></span>

<span data-ttu-id="cc131-147">Die PowerShell-Katalogadministratoren können für jedes Paket auf den Link „Besitzer verwalten“ zugreifen.</span><span class="sxs-lookup"><span data-stu-id="cc131-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any package.</span></span>
<span data-ttu-id="cc131-148">Wenn Sie der rechtmäßige Besitzer eines Pakets sind und den aktuellen Besitzer nicht erreichen können, um Besitzberechtigungen zu erlangen, wenden Sie sich über den Link „Missbrauch melden“ im Katalog an die PowerShell-Katalogadministratoren.</span><span class="sxs-lookup"><span data-stu-id="cc131-148">If you are the rightful owner of a package and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="cc131-149">Wir überprüfen dann Ihren Besitz des Pakets anhand eines festgelegten Prozesses.</span><span class="sxs-lookup"><span data-stu-id="cc131-149">We will then follow a process to verify your ownership of the package.</span></span>
<span data-ttu-id="cc131-150">Wenn wir feststellen, dass Sie der Besitzer des Pakets sein sollten, verwenden wir selbst den Link „Besitzer verwalten“ für das Paket und senden Ihnen die Einladung als Besitzer.</span><span class="sxs-lookup"><span data-stu-id="cc131-150">If we determine you should be an owner of the package, we will use the 'Manage Owners' link for the package ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="cc131-151">Dies erfolgt jedoch erst, nachdem wir Sie als Besitzer bestätigt haben, und der Vorgang variiert je nach den Umständen.</span><span class="sxs-lookup"><span data-stu-id="cc131-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="cc131-152">Oft verwenden wir die Projekt-URL des Pakets, um eine Möglichkeit zum Kontaktieren des Projektbesitzers zu finden. Gelegentlich wenden wir uns jedoch auch über Twitter, E-Mail oder andere Methoden an den Besitzer.</span><span class="sxs-lookup"><span data-stu-id="cc131-152">Often times, we will use the package's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>
