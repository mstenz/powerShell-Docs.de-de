---
ms.date: 09/10/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Verwalten von API-Schlüsseln
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328291"
---
# <a name="managing-api-keys"></a><span data-ttu-id="48397-103">Verwalten von API-Schlüsseln</span><span class="sxs-lookup"><span data-stu-id="48397-103">Managing API keys</span></span>

<span data-ttu-id="48397-104">Der PowerShell-Katalog unterstützt das Erstellen mehrerer API-Schlüssel für eine Reihe von Anforderungen bei der Veröffentlichung.</span><span class="sxs-lookup"><span data-stu-id="48397-104">The PowerShell Gallery supports creating multiple API keys to support a range of publishing requirements.</span></span> <span data-ttu-id="48397-105">Ein API-Schlüssel kann sich auf ein oder mehrere Pakete beziehen, gewährt bestimmte Berechtigungen und verfügt über ein Ablaufdatum.</span><span class="sxs-lookup"><span data-stu-id="48397-105">An API key can apply to one or more packages, grants specific privileges, and has an expiration date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="48397-106">Benutzer, die vor der Einführung bereichsbezogener API-Schlüssel im PowerShell-Katalog veröffentlicht haben, werden über einen API-Schlüssel mit Vollzugriff verfügen.</span><span class="sxs-lookup"><span data-stu-id="48397-106">Users who published to the PowerShell Gallery prior to the introduction of scoped API keys will have a "Full access API key".</span></span> <span data-ttu-id="48397-107">Die Schlüssel mit Vollzugriff verfügen nicht über die Sicherheitsverbesserungen, die in bereichsbezogene API-Schlüssel eingebaut sind.</span><span class="sxs-lookup"><span data-stu-id="48397-107">The full access keys do not have the security improvements built into scoped API keys.</span></span> <span data-ttu-id="48397-108">Die Schlüssel mit Vollzugriff laufen nie ab und gelten für alles, was dem Benutzer gehört.</span><span class="sxs-lookup"><span data-stu-id="48397-108">The full access keys never expires and apply to everything owned by the user.</span></span> <span data-ttu-id="48397-109">Wenn Sie diesen Schlüssel löschen, kann er nicht neu erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="48397-109">If you delete this key, it cannot be recreated.</span></span>

<span data-ttu-id="48397-110">Die folgende Abbildung zeigt die beim Erstellen eines bereichsbezogenen API-Schlüssels verfügbaren Optionen.</span><span class="sxs-lookup"><span data-stu-id="48397-110">The following image shows the options available when creating a scoped API key.</span></span>

![Erstellen von API-Schlüsseln](../../Images/PSGallery_KeyScoped.png)

<span data-ttu-id="48397-112">In diesem Beispiel haben wir einen API-Schlüssel mit dem Namen **AzureRMDataFactory** erstellt.</span><span class="sxs-lookup"><span data-stu-id="48397-112">In this example, we created an API key named **AzureRMDataFactory**.</span></span> <span data-ttu-id="48397-113">Dieser Schlüsselwert kann zur Übertragung von Paketen mithilfe von Push genutzt werden, deren Namen mit „AzureRM.DataFactory“ beginnen, und ist 365 Tage lang gültig.</span><span class="sxs-lookup"><span data-stu-id="48397-113">This key value can be used to push packages with names that begin with 'AzureRM.DataFactory' and is valid for 365 days.</span></span> <span data-ttu-id="48397-114">Dies ist ein typisches Szenario, wenn verschiedene Teams innerhalb einer Organisation an verschiedenen Paketen arbeiten.</span><span class="sxs-lookup"><span data-stu-id="48397-114">This is a typical scenario when different teams within the same organization work on different packages.</span></span> <span data-ttu-id="48397-115">Die Mitglieder des Teams haben einen Schlüssel, der ihnen Berechtigungen für das jeweilige Paket gewährt, an dem sie arbeiten.</span><span class="sxs-lookup"><span data-stu-id="48397-115">The members of the team have a key that grants them privileges for the specific package they work on.</span></span>
<span data-ttu-id="48397-116">Der Ablaufwert verhindert, dass veraltete oder vergessene Schlüssel verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="48397-116">The expiration value prevents the use of stale or forgotten keys.</span></span>

## <a name="using-glob-patterns"></a><span data-ttu-id="48397-117">Verwenden von Globmustern</span><span class="sxs-lookup"><span data-stu-id="48397-117">Using glob patterns</span></span>

<span data-ttu-id="48397-118">Wenn Sie an mehreren Paketen arbeiten, können Sie mit Globmustern mehrere Pakete als Gruppe zusammenfügen.</span><span class="sxs-lookup"><span data-stu-id="48397-118">If you work on multiple packages, you can use globbing patterns to match multiple packages as a group.</span></span> <span data-ttu-id="48397-119">API-Schlüsselberechtigungen gelten für alle neuen Pakete, die mit dem Globmuster übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="48397-119">API key permissions apply to all new packages matching the glob pattern.</span></span> <span data-ttu-id="48397-120">Im vorherigen Beispiel wurde etwa als **Globmuster**-Wert „AzureRM.DataFactory\*“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="48397-120">For example, the previous example uses a **Glob Pattern** value of 'AzureRM.DataFactory\*'.</span></span> <span data-ttu-id="48397-121">Sie können ein Paket mit dem Namen „AzureRm.DataFactoryV2.Netcore“ mit diesem Schlüssel mithilfe von Push übertragen, da das Paket mit dem Globmuster übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="48397-121">You can push a package named 'AzureRm.DataFactoryV2.Netcore' using this key since the package matches the glob pattern.</span></span>

## <a name="create-api-keys-securely"></a><span data-ttu-id="48397-122">Sicheres Erstellen von API-Schlüsseln</span><span class="sxs-lookup"><span data-stu-id="48397-122">Create API keys securely</span></span>

<span data-ttu-id="48397-123">Aus Sicherheitsgründen wird ein neu erstellter Schlüsselwert nie auf dem Bildschirm angezeigt und ist wie unten dargestellt nur über die Schaltfläche „Kopieren“ verfügbar.</span><span class="sxs-lookup"><span data-stu-id="48397-123">For security, a newly created key value is never shown on the screen and is only available with the Copy button, as shown below.</span></span>

![Abrufen eines neuen API-Schlüsselwerts](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> <span data-ttu-id="48397-125">Sie können den API-Schlüsselwert nur direkt nach dem Erstellen oder Aktualisieren kopieren.</span><span class="sxs-lookup"><span data-stu-id="48397-125">You can only copy the API key value immediately after creating or refreshing it.</span></span> <span data-ttu-id="48397-126">Er wird nicht angezeigt und ist nach dem Aktualisieren der Seite nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="48397-126">It will not be displayed, and will not be accessible again after the page is refreshed.</span></span> <span data-ttu-id="48397-127">Wenn Sie den Schlüsselwert verlieren, müssen Sie „Erneut generieren“ anklicken und den Schlüssel danach kopieren.</span><span class="sxs-lookup"><span data-stu-id="48397-127">If you lose the key value, you must use Regenerate, and copy the key after it is regenerated.</span></span>

## <a name="key-permissions-and-expiration"></a><span data-ttu-id="48397-128">Schlüsselberechtigungen und Ablaufdatum</span><span class="sxs-lookup"><span data-stu-id="48397-128">Key permissions and expiration</span></span>

<span data-ttu-id="48397-129">Bereichsbezogene API-Schlüssel können folgende Berechtigungen zuweisen:</span><span class="sxs-lookup"><span data-stu-id="48397-129">Scoped API keys can assign any of the following permissions:</span></span>

- <span data-ttu-id="48397-130">Neue Pakete mithilfe von Push übertragen</span><span class="sxs-lookup"><span data-stu-id="48397-130">Push new packages</span></span>
- <span data-ttu-id="48397-131">Neue Pakete mithilfe von Push übertragen oder Pakete aktualisieren</span><span class="sxs-lookup"><span data-stu-id="48397-131">Push new or update packages</span></span>
- <span data-ttu-id="48397-132">Auflistung von Paketen aufheben</span><span class="sxs-lookup"><span data-stu-id="48397-132">Unlist packages</span></span>

<span data-ttu-id="48397-133">Jeder neue Schlüssel verfügt über ein Ablaufdatum.</span><span class="sxs-lookup"><span data-stu-id="48397-133">Every new key has an expiration.</span></span> <span data-ttu-id="48397-134">Der Ablaufwert wird in Tagen gemessen.</span><span class="sxs-lookup"><span data-stu-id="48397-134">The expiration value is measured in days.</span></span> <span data-ttu-id="48397-135">Die möglichen Werte für den Ablauf sind:</span><span class="sxs-lookup"><span data-stu-id="48397-135">The possible values for expiration are:</span></span>

- <span data-ttu-id="48397-136">1 Tag</span><span class="sxs-lookup"><span data-stu-id="48397-136">1 day</span></span>
- <span data-ttu-id="48397-137">90 Tage</span><span class="sxs-lookup"><span data-stu-id="48397-137">90 days</span></span>
- <span data-ttu-id="48397-138">180 Tage</span><span class="sxs-lookup"><span data-stu-id="48397-138">180 days</span></span>
- <span data-ttu-id="48397-139">270 Tage</span><span class="sxs-lookup"><span data-stu-id="48397-139">270 days</span></span>
- <span data-ttu-id="48397-140">365 Tage (Standard)</span><span class="sxs-lookup"><span data-stu-id="48397-140">365 days (default)</span></span>

<span data-ttu-id="48397-141">Diese Einstellungen können nicht geändert werden, nachdem der Schlüssel erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="48397-141">These settings cannot be changed once the key is created.</span></span> <span data-ttu-id="48397-142">Sie können keinen neuen Schlüssel erstellen, der nie abläuft.</span><span class="sxs-lookup"><span data-stu-id="48397-142">You cannot create a new key that never expires.</span></span>

## <a name="editing-and-deleting-existing-api-keys"></a><span data-ttu-id="48397-143">Bearbeiten und Löschen vorhandener API-Schlüssel</span><span class="sxs-lookup"><span data-stu-id="48397-143">Editing and deleting existing API keys</span></span>

<span data-ttu-id="48397-144">Sie können einige Einstellungen eines vorhandenen Schlüssels ändern.</span><span class="sxs-lookup"><span data-stu-id="48397-144">You can change some settings of an existing key.</span></span> <span data-ttu-id="48397-145">Wie bereits erwähnt, können Sie den Sicherheitsbereich und das Ablaufdatum eines vorhandenen API-Schlüssels nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="48397-145">As previously noted, you cannot modify the security scope for an existing API key or change the expiration.</span></span> <span data-ttu-id="48397-146">Die Optionen, die geändert werden können, sehen Sie in folgendem Screenshot:</span><span class="sxs-lookup"><span data-stu-id="48397-146">The changeable options are shown in the following screenshot:</span></span>

![Abrufen eines neuen API-Schlüsselwerts](../../Images/PSGallery_EditAPIKey.png)

<span data-ttu-id="48397-148">Zum Ändern der Pakete, die durch einen Schlüssel kontrolliert werden, können Sie einzelne Pakete aus der Liste auswählen oder das Globmuster ändern.</span><span class="sxs-lookup"><span data-stu-id="48397-148">To change the packages controlled by a key, you can choose individual packages from the list or change the glob pattern.</span></span>

<span data-ttu-id="48397-149">Durch Klicken auf **Erneut generieren** wird ein neuer Schlüsselwert erstellt.</span><span class="sxs-lookup"><span data-stu-id="48397-149">Clicking **Regenerate** creates a new key value.</span></span> <span data-ttu-id="48397-150">Wie beim ursprünglichen Erstellen des Schlüssels müssen Sie den Schlüsselwert direkt nach dem Aktualisieren **Kopieren**.</span><span class="sxs-lookup"><span data-stu-id="48397-150">Just like when you initially created the key, you must **Copy** the key value immediately after updating it.</span></span> <span data-ttu-id="48397-151">Die Option **Kopieren** ist nicht mehr verfügbar, wenn Sie diese Seite verlassen.</span><span class="sxs-lookup"><span data-stu-id="48397-151">The **Copy** option is not available once you leave this page.</span></span>

<span data-ttu-id="48397-152">Nach dem Klicken auf **Löschen** wird eine Bestätigungsmeldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="48397-152">Clicking **Delete** displays a confirmation message.</span></span> <span data-ttu-id="48397-153">Wenn ein Schlüssel gelöscht wurde, kann er nicht mehr verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="48397-153">Once a key is deleted, it will be unusable.</span></span>

## <a name="key-expiration"></a><span data-ttu-id="48397-154">Ablauf des Schlüssels</span><span class="sxs-lookup"><span data-stu-id="48397-154">Key expiration</span></span>

<span data-ttu-id="48397-155">Zehn Tage vor Ablauf sendet der PowerShell-Katalog eine E-Mail zur Warnung an den Kontoinhaber des API-Schlüssels.</span><span class="sxs-lookup"><span data-stu-id="48397-155">Ten days before the expiration, the PowerShell Gallery sends a warning email the account holder of the API key.</span></span> <span data-ttu-id="48397-156">Nach Ablauf kann der Schlüssel nicht mehr verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="48397-156">After expiration, the key is unusable.</span></span> <span data-ttu-id="48397-157">Eine Warnmeldung erscheint oben auf der Verwaltungsseite des API-Schlüssels und gibt an, welche Schlüssel nicht mehr gültig sind.</span><span class="sxs-lookup"><span data-stu-id="48397-157">A warning message is displayed at the top of the API key management page showing which keys are no longer valid.</span></span> <span data-ttu-id="48397-158">Sie können einen neuen Schlüsselwert erstellen.</span><span class="sxs-lookup"><span data-stu-id="48397-158">You can generate a new key value.</span></span>
