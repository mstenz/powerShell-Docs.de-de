---
ms.date: 10/13/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: 'Desired State Configuration (DSC): Übersicht für Ingenieure'
ms.openlocfilehash: 0e599c2218cd2df29dbd0529006be5e1ef17ce5f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953797"
---
# <a name="desired-state-configuration-overview-for-engineers"></a><span data-ttu-id="341b8-103">Desired State Configuration (DSC): Übersicht für Ingenieure</span><span class="sxs-lookup"><span data-stu-id="341b8-103">Desired State Configuration Overview for Engineers</span></span>

<span data-ttu-id="341b8-104">Dieses Dokumente richtet sich an Ingenieure und Betriebsteams, um die Vorteile der Desired State Configuration (DSC) von PowerShell kennenzulernen.</span><span class="sxs-lookup"><span data-stu-id="341b8-104">This document is intended for developer and operations teams to understand the benefits of PowerShell Desired State Configuration (DSC).</span></span>
<span data-ttu-id="341b8-105">Eine Ansicht des Werts auf höherer Ebene, den DSC bereitstellt, finden Sie unter [Desired State Configuration (DSC): Übersicht für Entscheidungsträger](decisionMaker.md)</span><span class="sxs-lookup"><span data-stu-id="341b8-105">For a higher level view of the value DSC provides, please see [Desired State Configuration Overview for Decision Makers](decisionMaker.md)</span></span>

## <a name="benefits-of-desired-state-configuration"></a><span data-ttu-id="341b8-106">Vorteile von DSC</span><span class="sxs-lookup"><span data-stu-id="341b8-106">Benefits of Desired State Configuration</span></span>

<span data-ttu-id="341b8-107">Mit DSC können Sie Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="341b8-107">DSC exists to:</span></span>

- <span data-ttu-id="341b8-108">Die Komplexität der Skripterstellung in Windows verringern</span><span class="sxs-lookup"><span data-stu-id="341b8-108">Decrease the complexity of scripting in Windows</span></span>
- <span data-ttu-id="341b8-109">Die Geschwindigkeit der Iteration erhöhen</span><span class="sxs-lookup"><span data-stu-id="341b8-109">Increase the speed of iteration</span></span>

<span data-ttu-id="341b8-110">Das Konzept der „kontinuierlichen Bereitstellung“ gewinnt immer mehr an Wichtigkeit.</span><span class="sxs-lookup"><span data-stu-id="341b8-110">The concept of "continuous deployment" is becoming more important.</span></span>
<span data-ttu-id="341b8-111">Die kontinuierliche Bereitstellung ermöglicht häufige Bereitstellungen, womöglich mehrmals pro Tag.</span><span class="sxs-lookup"><span data-stu-id="341b8-111">Continuous deployment means the ability to deploy frequently, potentially many times per day.</span></span>
<span data-ttu-id="341b8-112">Der Zweck dieser Bereitstellungen ist nicht, etwas zu reparieren, sondern etwas schnell veröffentlichen zu können.</span><span class="sxs-lookup"><span data-stu-id="341b8-112">The purpose of these deployments are not to fix something but to get something published quickly.</span></span>
<span data-ttu-id="341b8-113">Dadurch, dass neue Features durch die Entwicklung so reibungslos und verlässlich wie möglich in Betrieb genommen werden können, kann die Amortisierungszeit der neuen Businesslogik verringert werden.</span><span class="sxs-lookup"><span data-stu-id="341b8-113">By getting new features through development into operation as smoothly and reliably as possible, you reduce time-to-value of new business logic.</span></span>

<span data-ttu-id="341b8-114">Der Wechsel zum Cloudcomputing beinhaltet eine Bereitstellungslösung, bei der ein „deklaratives“ Vorlagenmodell verwendet wird. Hierbei wird eine Umgebung im Endzustand als Text deklariert und in einer Bereitstellungs-Engine veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="341b8-114">The move towards cloud computing implies a deployment solution that utilizes a "declarative" template model, where an end state environment is declared as text and published to a deployment engine.</span></span>
<span data-ttu-id="341b8-115">Diese Bereitstellungstechnik ermöglicht schnelle Änderungen im erforderlichen Umfang, mit robustem Schutz vor Ausfallrisiken, da die Bereitstellung jederzeit konsistent wiederholt werden kann, um einen Endzustand zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="341b8-115">This deployment technique allows for rapid change, at scale, with resilience against threat of failure because at any time the deployment can be consistently repeated to guarantee an end state.</span></span>
<span data-ttu-id="341b8-116">Die Erstellung von Tools und Diensten, die diese Art der Vorgänge durch Automatisierung unterstützen, ist eine Reaktion auf diese Änderungen.</span><span class="sxs-lookup"><span data-stu-id="341b8-116">The creation of tools and services that support this style of operations through automation is a response to these changes.</span></span>

<span data-ttu-id="341b8-117">DSC ist eine Plattform, die deklarative und idempotente (wiederholbare) Bereitstellung, Konfiguration und Konformität bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="341b8-117">DSC is a platform that provides declarative and idempotent (repeatable) deployment, configuration and conformance.</span></span>
<span data-ttu-id="341b8-118">Mit der DSC-Plattform stellen Sie sicher, dass die Komponenten Ihrer Datencenter über die ordnungsgemäße Konfiguration verfügen, wodurch Fehler sowie teure Probleme bei der Bereitstellung vermieden werden können.</span><span class="sxs-lookup"><span data-stu-id="341b8-118">The DSC platform enables you to ensure that the components of your data center have the correct configuration, which avoids errors and prevents costly deployment failures.</span></span>
<span data-ttu-id="341b8-119">Dadurch dass die DSC-Konfiguration als Teil eines Anwendungscodes angesehen wird, ermöglicht DSC die kontinuierliche Bereitstellung.</span><span class="sxs-lookup"><span data-stu-id="341b8-119">By treating DSC configurations as part of application code, DSC enables continuous deployment.</span></span>
<span data-ttu-id="341b8-120">Die DSC-Konfiguration sollte als Teil der Anwendung aktualisiert werden, wodurch sichergestellt werden kann, dass das erforderliche Wissen für die Bereitstellung der Anwendung immer auf dem neuesten Stand und zum Gebrauch bereit ist.</span><span class="sxs-lookup"><span data-stu-id="341b8-120">The DSC configuration should be updated as a part of the application, ensuring that the knowledge needed to deploy the application is always up-to-date and ready to be used.</span></span>

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a><span data-ttu-id="341b8-121">„Ich besitze PowerShell, warum brauche ich Desired State Configuration?“</span><span class="sxs-lookup"><span data-stu-id="341b8-121">"I have PowerShell, why do I need Desired State Configuration?"</span></span>

<span data-ttu-id="341b8-122">Die DSC-Konfigurationen trennen die Absicht – oder „was ich machen will“ – von der Ausführung – oder „wie ich es machen will.“</span><span class="sxs-lookup"><span data-stu-id="341b8-122">DSC configurations separate intent, or "what I want to do", from execution, or "how I want to do it."</span></span>
<span data-ttu-id="341b8-123">Dies bedeutet, dass die Logik der Ausführung in den Ressourcen enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="341b8-123">This means the logic of execution is contained within the resources.</span></span>
<span data-ttu-id="341b8-124">Benutzer müssen nicht wissen, wie Sie eine Funktion implementieren oder bereitstellen, wenn eine DSC-Ressource für diese Funktion verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="341b8-124">Users do not have to know how to implement or deploy a feature when a DSC resource for that feature is available.</span></span>
<span data-ttu-id="341b8-125">Dies ermöglicht es dem Benutzer, sich auf die Struktur der Bereitstellung zu konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="341b8-125">This allows the user to focus on the structure of their deployment.</span></span>

<span data-ttu-id="341b8-126">PowerShell-Skripts sollten beispielsweise so aussehen:</span><span class="sxs-lookup"><span data-stu-id="341b8-126">As an example, PowerShell scripts should look like this:</span></span>
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
<span data-ttu-id="341b8-127">Dieses Skript ist einfach, verständlich und unkompliziert.</span><span class="sxs-lookup"><span data-stu-id="341b8-127">This script is simple, comprehensible, and straightforward.</span></span>
<span data-ttu-id="341b8-128">Wenn Sie jedoch versuchen, dieses Skript in die Produktionsumgebung einzufügen, werden Sie auf verschiedene Probleme stoßen.</span><span class="sxs-lookup"><span data-stu-id="341b8-128">However, if you try putting that script into production, you will run into several issues.</span></span>
<span data-ttu-id="341b8-129">Was geschieht, wenn, das Skript zweimal hintereinander ausgeführt wird?</span><span class="sxs-lookup"><span data-stu-id="341b8-129">What happens if that script is run twice in a row?</span></span>
<span data-ttu-id="341b8-130">Was geschieht, wenn Bob bisher Vollzugriff auf die Freigabe hatte?</span><span class="sxs-lookup"><span data-stu-id="341b8-130">What happens if Bob previously had Full Access to the share?</span></span>

<span data-ttu-id="341b8-131">Um diese Probleme zu berücksichtigen, wird eine „echte“ Version des Skripts genauer auf Beispiele wie das folgende eingehen:</span><span class="sxs-lookup"><span data-stu-id="341b8-131">To compensate for these issues, a "real" version of the script will look closer to something like:</span></span>
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

<span data-ttu-id="341b8-132">Dieses Skript ist komplexer, mit sehr viel Logik und Fehlerbehandlung.</span><span class="sxs-lookup"><span data-stu-id="341b8-132">This script is more complex, with plenty of logic and error handling.</span></span>
<span data-ttu-id="341b8-133">Das Skript ist komplexer, da Ihnen nicht mehr angezeigt wird, was geschehen soll, jedoch *wie es funktioniert*.</span><span class="sxs-lookup"><span data-stu-id="341b8-133">The script is more complex because you are no longer stating what you want done, but *how to do it*.</span></span>

<span data-ttu-id="341b8-134">Mit DSC können Sie angeben, was Sie tun möchten, und die zugrunde liegende Logik wird entfernt.</span><span class="sxs-lookup"><span data-stu-id="341b8-134">DSC allows you to say what you want done, and the underlying logic is abstracted away.</span></span>

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Bob"
          FullAccess  = "Alice"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

<span data-ttu-id="341b8-135">Dieses Skript ist ordnungsgemäß formatiert und einfach zu lesen.</span><span class="sxs-lookup"><span data-stu-id="341b8-135">This script is cleanly formatted and straightforward to read.</span></span>
<span data-ttu-id="341b8-136">Die Logikpfade und Fehlerbehandlungen sind weiterhin, in der Implementierung der [Ressource](../resources/resources.md) vorhanden, sind jedoch für den Autor des Skripts nicht sichtbar.</span><span class="sxs-lookup"><span data-stu-id="341b8-136">The logic paths and error handling are still present in the [resource](../resources/resources.md) implementation, but invisible to the script author.</span></span>

## <a name="separating-environment-from-structure"></a><span data-ttu-id="341b8-137">Trennen der Umgebung von der Struktur</span><span class="sxs-lookup"><span data-stu-id="341b8-137">Separating Environment from Structure</span></span>

<span data-ttu-id="341b8-138">In DevOps kommt es häufig vor, dass es mehrere Umgebungen für die Bereitstellung gibt.</span><span class="sxs-lookup"><span data-stu-id="341b8-138">A common pattern in DevOps is to have multiple environments for deployment.</span></span>
<span data-ttu-id="341b8-139">Es kann z.B. eine „dev“-Umgebung vorhanden sein, die zum schnellen Erstellen von Prototypen für neuen Code verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="341b8-139">For example, there might be a "dev" environment used to quickly prototype new code.</span></span>
<span data-ttu-id="341b8-140">Der Code aus der „dev“-Umgebung (Entwicklungsumgebung) wird dann in eine „test“-Umgebung (Testumgebung) verschoben, wo andere Personen die neue Funktion überprüfen.</span><span class="sxs-lookup"><span data-stu-id="341b8-140">The code from the "dev" environment goes into a "test" environment, where other people verify the new functionality.</span></span>
<span data-ttu-id="341b8-141">Schließlich gelangt der Code in „prod“ (Produktionsumgebung) oder in die Livesite-Produktionsumgebung.</span><span class="sxs-lookup"><span data-stu-id="341b8-141">Finally, the code goes into "prod", or the live site production environment.</span></span>

<span data-ttu-id="341b8-142">DSC-Konfigurationen berücksichtigen diese dev-test-prod-Pipeline durch Verwendung von [Konfigurationsdaten](../configurations/configData.md).</span><span class="sxs-lookup"><span data-stu-id="341b8-142">DSC configurations accommodate this dev-test-prod pipeline through the use of [configuration data](../configurations/configData.md).</span></span>
<span data-ttu-id="341b8-143">Dadurch wird der Unterschied zwischen der Struktur der Konfiguration noch weiter von den verwalteten Knoten abstrahiert.</span><span class="sxs-lookup"><span data-stu-id="341b8-143">This further abstracts the difference between the structure of the configuration from the nodes that are managed.</span></span>
<span data-ttu-id="341b8-144">Sie können beispielsweise eine Konfiguration definieren, die einen SQL-Server, einen IIS-Server und einen Server auf mittlerer Ebene erfordert.</span><span class="sxs-lookup"><span data-stu-id="341b8-144">For example, you can define a configuration that requires a SQL server, an IIS server, and a middle-tier server.</span></span>
<span data-ttu-id="341b8-145">Unabhängig davon, welche Knoten die verschiedenen Teile dieser Konfiguration erhalten, werden diese drei Elemente immer vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="341b8-145">Regardless of what nodes receive the different pieces of this configuration, those three elements will always be present.</span></span>
<span data-ttu-id="341b8-146">Sie können Konfigurationsdaten verwenden, um alle drei Elemente auf den gleichen Computer für eine dev-Umgebung zu verweisen, die drei Elemente auf drei verschiedene Computer für eine Testumgebung zu verteilen und schließlich auf all Ihre Produktionsserver für die Produktionsumgebung.</span><span class="sxs-lookup"><span data-stu-id="341b8-146">You can use configuration data to point all three elements towards the same machine for a dev environment, separate out the three elements to three different machines for a test environment, and finally towards all your production servers for the prod environment.</span></span>
<span data-ttu-id="341b8-147">Damit Sie eine Bereitstellung in unterschiedlichen Umgebungen durchführen können, können Sie **Start-DscConfiguration** mit den richtigen Konfigurationsdaten für die Zielumgebung aufrufen.</span><span class="sxs-lookup"><span data-stu-id="341b8-147">To deploy to the different environments, you can invoke **Start-DscConfiguration** with the correct configuration data for the environment you want to target.</span></span>

## <a name="see-also"></a><span data-ttu-id="341b8-148">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="341b8-148">See Also</span></span>

[<span data-ttu-id="341b8-149">Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="341b8-149">Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="341b8-150">Konfigurationsdaten</span><span class="sxs-lookup"><span data-stu-id="341b8-150">Configuration Data</span></span>](../configurations/configData.md)

[<span data-ttu-id="341b8-151">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="341b8-151">Resources</span></span>](../resources/resources.md)
