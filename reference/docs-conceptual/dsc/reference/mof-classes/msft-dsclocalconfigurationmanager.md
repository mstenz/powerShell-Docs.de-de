---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 09b30edd48384c0e8412e0e6ee926a719249c5b8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953267"
---
# <a name="msft_dsclocalconfigurationmanager-class"></a><span data-ttu-id="f94fb-103">MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="f94fb-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f94fb-104">Der lokale Konfigurations-Manager, der die Zustände von Konfigurationsdateien steuert und den Konfigurations-Agent verwendet, um die Konfigurationen anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="f94fb-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="f94fb-105">Die folgende Syntax wurde aus MOF-Code (Managed Object Format, verwaltetes Objektformat) vereinfacht und enthält alle geerbten Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="f94fb-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="f94fb-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f94fb-106">Syntax</span></span>

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="f94fb-107">Members</span><span class="sxs-lookup"><span data-stu-id="f94fb-107">Members</span></span>

<span data-ttu-id="f94fb-108">Die **MSFT_DSCLocalConfigurationManager**-Klasse hat folgende Member:</span><span class="sxs-lookup"><span data-stu-id="f94fb-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

- <span data-ttu-id="f94fb-109">[Methoden][]</span><span class="sxs-lookup"><span data-stu-id="f94fb-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="f94fb-110">Methoden</span><span class="sxs-lookup"><span data-stu-id="f94fb-110">Methods</span></span>

<span data-ttu-id="f94fb-111">Die **MSFT_DSCLocalConfigurationManager**-Klasse enthält diese Methoden.</span><span class="sxs-lookup"><span data-stu-id="f94fb-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="f94fb-112">Methode</span><span class="sxs-lookup"><span data-stu-id="f94fb-112">Method</span></span> |<span data-ttu-id="f94fb-113">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="f94fb-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="f94fb-114">ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="f94fb-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="f94fb-115">Verwendet den Konfigurations-Agent, um die ausstehende Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="f94fb-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>|
| [<span data-ttu-id="f94fb-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="f94fb-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="f94fb-117">Deaktiviert das Debuggen von DSC-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="f94fb-117">Disables DSC resource debugging.</span></span>|
| [<span data-ttu-id="f94fb-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="f94fb-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="f94fb-119">Aktiviert das Debuggen von DSC-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="f94fb-119">Enables DSC resource debugging.</span></span>|
| [<span data-ttu-id="f94fb-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="f94fb-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="f94fb-121">Sendet das Konfigurationsdokument an den verwalteten Knoten und verwendet die **Get**-Methode des Konfigurations-Agents, um die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="f94fb-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="f94fb-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="f94fb-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="f94fb-123">Ruft die Konfigurations-Agent-Ausgabe im Zusammenhang mit einem bestimmten Auftrag ab.</span><span class="sxs-lookup"><span data-stu-id="f94fb-123">Gets the Configuration Agent output relating to a specific job.</span></span>|
| [<span data-ttu-id="f94fb-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="f94fb-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="f94fb-125">Abrufen des Konfigurationsstatusverlaufs.</span><span class="sxs-lookup"><span data-stu-id="f94fb-125">Get the configuration status history.</span></span>|
| [<span data-ttu-id="f94fb-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="f94fb-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="f94fb-127">Ruft die Einstellungen des lokalen Konfigurations-Managers ab, die zur Steuerung des Konfigurations-Agents verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f94fb-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>|
| [<span data-ttu-id="f94fb-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="f94fb-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="f94fb-129">Startet die Konsistenzprüfung.</span><span class="sxs-lookup"><span data-stu-id="f94fb-129">Starts the consistency check.</span></span>|
| [<span data-ttu-id="f94fb-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="f94fb-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="f94fb-131">Entfernt die Konfigurationsdateien.</span><span class="sxs-lookup"><span data-stu-id="f94fb-131">Removes the configuration files.</span></span>|
| [<span data-ttu-id="f94fb-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="f94fb-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="f94fb-133">Ruft direkt die **Get**-Methode einer DSC-Ressource auf.</span><span class="sxs-lookup"><span data-stu-id="f94fb-133">Directly calls the **Get** method of a DSC resource.</span></span>|
| [<span data-ttu-id="f94fb-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="f94fb-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="f94fb-135">Ruft direkt die **Set**-Methode einer DSC-Ressource auf.</span><span class="sxs-lookup"><span data-stu-id="f94fb-135">Directly calls the **Set** method of a DSC resource.</span></span>|
| [<span data-ttu-id="f94fb-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="f94fb-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="f94fb-137">Ruft direkt die **Test**-Methode einer DSC-Ressource auf.</span><span class="sxs-lookup"><span data-stu-id="f94fb-137">Directly calls the **Test** method of a DSC resource.</span></span>|
| [<span data-ttu-id="f94fb-138">RollBack</span><span class="sxs-lookup"><span data-stu-id="f94fb-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="f94fb-139">Führt einen Rollback zu einer vorherigen Konfiguration aus.</span><span class="sxs-lookup"><span data-stu-id="f94fb-139">Rolls back to a previous configuration.</span></span>|
| [<span data-ttu-id="f94fb-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="f94fb-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="f94fb-141">Sendet das Konfigurationsdokument an den verwalteten Knoten und speichert es als ausstehende Änderung.</span><span class="sxs-lookup"><span data-stu-id="f94fb-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>|
| [<span data-ttu-id="f94fb-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="f94fb-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="f94fb-143">Sendet das Konfigurationsdokument an den verwalteten Knoten und verwendet den Konfigurations-Agent zum Anwenden der Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="f94fb-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="f94fb-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="f94fb-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="f94fb-145">Senden des Konfigurationsdokuments an den verwalteten Knoten und Beginnen mit der Verwendung des Konfigurations-Agents zum Anwenden der Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="f94fb-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="f94fb-146">Verwenden Sie „GetConfigurationResultOutput“, um Ergebnisausgaben abzurufen.</span><span class="sxs-lookup"><span data-stu-id="f94fb-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>|
| [<span data-ttu-id="f94fb-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="f94fb-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="f94fb-148">Legt die Einstellungen des lokalen Konfigurations-Managers fest, die zur Steuerung des Konfigurations-Agents verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f94fb-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>|
| [<span data-ttu-id="f94fb-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="f94fb-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="f94fb-150">Beende die Konfiguration, die gerade ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f94fb-150">Stops the configuration that is in progress.</span></span>|
| [<span data-ttu-id="f94fb-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="f94fb-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="f94fb-152">Sendet das Konfigurationsdokument an den verwalteten Knoten und überprüft die aktuelle Konfiguration anhand dieses Dokuments.</span><span class="sxs-lookup"><span data-stu-id="f94fb-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>|

## <a name="requirements"></a><span data-ttu-id="f94fb-153">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="f94fb-153">Requirements</span></span>

<span data-ttu-id="f94fb-154">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f94fb-154">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f94fb-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f94fb-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>
