---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: Neuerstellen des Demoendpunkts
ms.technology: powershell
ms.openlocfilehash: 4a56272b6f995500d443d441f5e03db85dac6f96
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="remake-the-demo-endpoint"></a><span data-ttu-id="70ed7-103">Neuerstellen des Demoendpunkts</span><span class="sxs-lookup"><span data-stu-id="70ed7-103">Remake the Demo Endpoint</span></span>
<span data-ttu-id="70ed7-104">In diesem Abschnitt erfahren Sie, wie Sie ein exaktes Replikat des Demoendpunkts erstellen, das Sie im vorherigen Abschnitt verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="70ed7-104">In this section, you will learn how to generate an exact replica of the demo endpoint you used in the above section.</span></span>
<span data-ttu-id="70ed7-105">Hierbei werden wichtige Konzepte vorgestellt, die für ein genaues Verständnis von JEA notwendig sind, einschließlich der PowerShell-Sitzungskonfigurationen und -Rollenfunktionen.</span><span class="sxs-lookup"><span data-stu-id="70ed7-105">This will introduce core concepts that are necessary to understand JEA, including PowerShell Session Configurations and Role Capabilities.</span></span>

## <a name="powershell-session-configurations"></a><span data-ttu-id="70ed7-106">PowerShell-Sitzungskonfigurationen</span><span class="sxs-lookup"><span data-stu-id="70ed7-106">PowerShell Session Configurations</span></span>
<span data-ttu-id="70ed7-107">Bei der Verwendung von JEA im vorherigen Abschnitt bestand der erste Schritt darin, den folgenden Befehl auszuführen:</span><span class="sxs-lookup"><span data-stu-id="70ed7-107">When you used JEA in the above section, you started by running the following command:</span></span>

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

<span data-ttu-id="70ed7-108">Die meisten Parameter sind selbsterklärend, der Parameter *ConfigurationName* kann jedoch auf den ersten Blick verwirrend sein.</span><span class="sxs-lookup"><span data-stu-id="70ed7-108">While most of the parameters are self-explanatory, the *ConfigurationName* parameter may seem confusing at first.</span></span>
<span data-ttu-id="70ed7-109">Dieser Parameter gab die PowerShell-Sitzungskonfiguration an, mit der Sie eine Verbindung hergestellt haben.</span><span class="sxs-lookup"><span data-stu-id="70ed7-109">That parameter specified the PowerShell Session Configuration to which you were connecting.</span></span>

<span data-ttu-id="70ed7-110">*PowerShell-Sitzungskonfiguration* ist im Grunde nur eine andere, schickere Bezeichnung für einen PowerShell-Endpunkt.</span><span class="sxs-lookup"><span data-stu-id="70ed7-110">*PowerShell Session Configuration* is a fancy term for a PowerShell endpoint.</span></span>
<span data-ttu-id="70ed7-111">Es ist im übertragenen Sinn der „Ort“, an dem Benutzer eine Verbindung herstellen und Zugriff auf PowerShell-Funktionen erhalten.</span><span class="sxs-lookup"><span data-stu-id="70ed7-111">It is the figurative "place" where users connect and get access to PowerShell functionality.</span></span>
<span data-ttu-id="70ed7-112">Je nachdem, wie Sie eine Sitzungskonfiguration einrichten, können Sie unterschiedliche Funktionen für die Benutzer bereitstellen, die eine Verbindung herstellen.</span><span class="sxs-lookup"><span data-stu-id="70ed7-112">Based on how you set up a Session Configuration, it can provide different functionality to connecting users.</span></span>
<span data-ttu-id="70ed7-113">Bei JEA werden Sitzungskonfigurationen verwendet, um die in PowerShell verfügbaren Funktionen einzuschränken und eine Ausführung als privilegiertes virtuelles Konto zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="70ed7-113">For JEA, we use Session Configurations to restrict PowerShell to a limited set of functionality and to run as a privileged virtual account.</span></span>

<span data-ttu-id="70ed7-114">Sie verfügen bereits über einige registrierte PowerShell-Sitzungskonfigurationen auf Ihrem Computer, die jeweils leicht unterschiedlich eingerichtet sind.</span><span class="sxs-lookup"><span data-stu-id="70ed7-114">You already have several registered PowerShell Session Configurations on your machine, each set up slightly differently.</span></span>
<span data-ttu-id="70ed7-115">Die meisten Konfigurationen sind im Lieferumfang von Windows enthalten, die Sitzungskonfiguration „JEA_Demo“ wurde jedoch im Abschnitt [Voraussetzungen](prerequisites.md) eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="70ed7-115">Most of them come with Windows, but the "JEA_Demo" Session Configuration was set up in the [prerequisites](prerequisites.md) section.</span></span>
<span data-ttu-id="70ed7-116">Sie können alle registrierten Sitzungskonfigurationen anzeigen, indem Sie folgenden Befehl an einer PowerShell-Administratoreingabeaufforderung ausführen:</span><span class="sxs-lookup"><span data-stu-id="70ed7-116">You can see all registered Session Configurations by running the following command in an Administrator PowerShell prompt:</span></span>

```PowerShell
Get-PSSessionConfiguration
```

## <a name="powershell-session-configuration-files"></a><span data-ttu-id="70ed7-117">PowerShell-Sitzungskonfigurationsdateien</span><span class="sxs-lookup"><span data-stu-id="70ed7-117">PowerShell Session Configuration Files</span></span>
<span data-ttu-id="70ed7-118">Sie können neuen Sitzungskonfigurationen erstellen, indem Sie neue *PowerShell-Sitzungskonfigurationsdateien* registrieren.</span><span class="sxs-lookup"><span data-stu-id="70ed7-118">You can make new Session Configurations by registering new *PowerShell Session Configuration Files*.</span></span>
<span data-ttu-id="70ed7-119">Sitzungskonfigurationsdateien weisen die Dateierweiterung PSSC auf.</span><span class="sxs-lookup"><span data-stu-id="70ed7-119">Session Configuration Files have ".pssc" file extensions.</span></span>
<span data-ttu-id="70ed7-120">Sie können Sitzungskonfigurationsdateien mit dem Cmdlet New-PSSessionConfigurationFile generieren.</span><span class="sxs-lookup"><span data-stu-id="70ed7-120">You can generate Session Configuration Files with the New-PSSessionConfigurationFile cmdlet.</span></span>

<span data-ttu-id="70ed7-121">Als Nächstes werden Sie eine neue Sitzungskonfiguration für JEA erstellen und registrieren.</span><span class="sxs-lookup"><span data-stu-id="70ed7-121">Next, you are going to create and register a new Session Configuration for JEA.</span></span>

## <a name="generate-and-modify-your-powershell-session-configuration"></a><span data-ttu-id="70ed7-122">Generieren und Ändern der PowerShell-Sitzungskonfiguration</span><span class="sxs-lookup"><span data-stu-id="70ed7-122">Generate and Modify your PowerShell Session Configuration</span></span>
<span data-ttu-id="70ed7-123">Führen Sie folgenden Befehl aus, um eine Gerüstdatei („Skeleton“) für eine PowerShell-Sitzungskonfiguration zu generieren.</span><span class="sxs-lookup"><span data-stu-id="70ed7-123">Run the following command to generate a PowerShell Session Configuration "skeleton" file.</span></span>

```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

> <span data-ttu-id="70ed7-124">**TIPP**: Standardmäßig sind nur die häufigsten Konfigurationseinstellungen in der Gerüstdatei vorhanden.</span><span class="sxs-lookup"><span data-stu-id="70ed7-124">**TIP:** Only the most common configuration settings are included in the skeleton file by default.</span></span>
> <span data-ttu-id="70ed7-125">Verwenden Sie den `-Full`-Parameter, um alle anwendbaren Einstellungen in die generierte PSSC-Datei einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="70ed7-125">Use the `-Full` parameter to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="70ed7-126">Öffnen Sie die Datei in der PowerShell ISE oder einem Text-Editor Ihrer Wahl.</span><span class="sxs-lookup"><span data-stu-id="70ed7-126">Open the file in PowerShell ISE, or your favorite text editor.</span></span>

```PowerShell
ise "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

<span data-ttu-id="70ed7-127">Aktualisieren Sie die folgenden Felder mit den nachstehenden Werten (denken Sie daran, Ihre eigene Sicherheitsgruppe ohne Administratorrechte einzusetzen):</span><span class="sxs-lookup"><span data-stu-id="70ed7-127">Update the following fields in the file with the values below (remember to substitute in your own non-administrator security group):</span></span>

```PowerShell
# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: # RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{'CONTOSO\JEA_NonAdmin_Operator' = @{ RoleCapabilities =  'Maintenance' }}
```

<span data-ttu-id="70ed7-128">Die Einträge haben folgende Bedeutung:</span><span class="sxs-lookup"><span data-stu-id="70ed7-128">Here is what each of those entries mean:</span></span>

1.  <span data-ttu-id="70ed7-129">Das Feld *SessionType* definiert vorab eingerichtete Standardeinstellungen, die für diesen Endpunkt verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="70ed7-129">The *SessionType* field defines preset default settings to use with this endpoint.</span></span>
<span data-ttu-id="70ed7-130">*RestrictedRemoteServer* definiert die Mindesteinstellungen, die für die Remoteverwaltung erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="70ed7-130">*RestrictedRemoteServer* defines the minimal settings necessary for remote management.</span></span>
<span data-ttu-id="70ed7-131">Standardmäßig macht ein *RestrictedRemoteServer*-Endpunkt die Befehle Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clea-Host, und Out-Default verfügbar.</span><span class="sxs-lookup"><span data-stu-id="70ed7-131">By default, a *RestrictedRemoteServer* endpoint will expose Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host, and Out-Default.</span></span>
<span data-ttu-id="70ed7-132">Die Einstellung *ExecutionPolicy* wird auf *RemoteSigned* und die Einstellung *LanguageMode* auf *NoLanguage* festgelegt.</span><span class="sxs-lookup"><span data-stu-id="70ed7-132">It will set the *ExecutionPolicy* to *RemoteSigned*, and the *LanguageMode* to *NoLanguage*.</span></span>
<span data-ttu-id="70ed7-133">Das Ergebnis dieser Einstellungen ist ein sicherer und einfacher Startpunkt zum Konfigurieren des Endpunkts.</span><span class="sxs-lookup"><span data-stu-id="70ed7-133">The net effect of these settings is a secure and minimal starting point for configuring your endpoint.</span></span>

2.  <span data-ttu-id="70ed7-134">Das Feld *RoleDefinitions* weist bestimmten Gruppen Rollenfunktionen zu.</span><span class="sxs-lookup"><span data-stu-id="70ed7-134">The *RoleDefinitions* field assigns Role Capabilities to specific groups.</span></span>
<span data-ttu-id="70ed7-135">Es definiert, welcher Benutzer mit einem privilegierten Konto welche Aufgaben ausführen darf.</span><span class="sxs-lookup"><span data-stu-id="70ed7-135">It defines who can do what as a privileged account.</span></span>
<span data-ttu-id="70ed7-136">Mit diesem Feld können Sie basierend auf der Gruppenmitgliedschaft die Funktionen angeben, die für einen verbundenen Benutzer zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="70ed7-136">With this field, you can specify the functionality available to any connecting user based on group membership.</span></span>
<span data-ttu-id="70ed7-137">Dies ist das Kernstück der RBAC-Funktionalität von JEA.</span><span class="sxs-lookup"><span data-stu-id="70ed7-137">This is the core of JEA's RBAC functionality.</span></span>
<span data-ttu-id="70ed7-138">In diesem Beispiel machen Sie die vorab erstellte Rollenfunktion „Maintenance“ für Mitglieder der Gruppe „Contoso\JEA_NonAdmin_Operator“ verfügbar.</span><span class="sxs-lookup"><span data-stu-id="70ed7-138">In this example, you are exposing the pre-made "Maintenance" RoleCapability to members of the "Contoso\JEA_NonAdmin_Operator" group.</span></span>

3.  <span data-ttu-id="70ed7-139">Das Feld *RunAsVirtualAccount* gibt an, dass PowerShell auf diesem Endpunkt mit einem ausführenden virtuellen Konto ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="70ed7-139">The *RunAsVirtualAccount* field indicates that PowerShell should "run as" a Virtual Account at this endpoint.</span></span>
<span data-ttu-id="70ed7-140">Standardmäßig ist das virtuelle Konto Mitglied der integrierten Administratorengruppe.</span><span class="sxs-lookup"><span data-stu-id="70ed7-140">By default, the Virtual Account is a member of the built in Administrators group.</span></span>
<span data-ttu-id="70ed7-141">Auf einem Domänencontroller ist es standardmäßig auch Mitglied der Domänenadministratorengruppe.</span><span class="sxs-lookup"><span data-stu-id="70ed7-141">On a domain controller, it is also a member of the Domain Administrators group by default.</span></span>
<span data-ttu-id="70ed7-142">Im weiteren Verlauf dieses Leitfadens erfahren Sie, wie Sie die Berechtigungen des virtuellen Kontos anpassen.</span><span class="sxs-lookup"><span data-stu-id="70ed7-142">Later in this guide, you will learn how to customize the privileges of the Virtual Account.</span></span>

4.  <span data-ttu-id="70ed7-143">Das Feld *TranscriptDirectory* definiert, wo mitgeschnittene PowerShell-Aufzeichnungen nach jeder Remotesitzung gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="70ed7-143">The *TranscriptDirectory* field defines where "over-the-shoulder" PowerShell transcripts are saved after each remote session.</span></span>
<span data-ttu-id="70ed7-144">Diese Aufzeichnungen bieten eine gut lesbare Möglichkeit, die Aktionen zu überprüfen, die in jeder Sitzung ausgeführt wurden.</span><span class="sxs-lookup"><span data-stu-id="70ed7-144">These transcripts allow you to inspect the actions taken in each session in a readable way.</span></span>
<span data-ttu-id="70ed7-145">Weitere Informationen über PowerShell-Aufzeichnungen finden Sie in diesem [Blogbeitrag](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span><span class="sxs-lookup"><span data-stu-id="70ed7-145">For more information about PowerShell transcripts, check out this [blog post](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span></span>
<span data-ttu-id="70ed7-146">Hinweis: Die reguläre Windows-Ereignisverwaltung erfasst ebenfalls Informationen darüber, welche Befehle von den einzelnen Benutzern mit PowerShell ausgeführt wurden.</span><span class="sxs-lookup"><span data-stu-id="70ed7-146">Note: regular Windows Eventing also captures information about what each user ran with PowerShell.</span></span>
<span data-ttu-id="70ed7-147">PowerShell-Aufzeichnungen sind allerdings besser lesbar.</span><span class="sxs-lookup"><span data-stu-id="70ed7-147">Transcripts are just a bit more readable.</span></span>

<span data-ttu-id="70ed7-148">Speichern Sie Ihre Änderungen abschließend in *JEADemo2.pssc*.</span><span class="sxs-lookup"><span data-stu-id="70ed7-148">Finally, save your changes to *JEADemo2.pssc*.</span></span>

## <a name="apply-the-powershell-session-configuration"></a><span data-ttu-id="70ed7-149">Anwenden der PowerShell-Sitzungskonfiguration</span><span class="sxs-lookup"><span data-stu-id="70ed7-149">Apply the PowerShell Session Configuration</span></span>

<span data-ttu-id="70ed7-150">Um aus einer Sitzungskonfigurationsdatei einen Endpunkt zu erstellen, müssen Sie die Datei registrieren.</span><span class="sxs-lookup"><span data-stu-id="70ed7-150">To create an endpoint from a Session Configuration file, you need to register the file.</span></span>
<span data-ttu-id="70ed7-151">Dafür sind einige Informationen erforderlich:</span><span class="sxs-lookup"><span data-stu-id="70ed7-151">This requires a few pieces of information:</span></span>

1. <span data-ttu-id="70ed7-152">Der Pfad zur Sitzungskonfigurationsdatei.</span><span class="sxs-lookup"><span data-stu-id="70ed7-152">The path to the Session Configuration file.</span></span>
2. <span data-ttu-id="70ed7-153">Der Name Ihrer registrierten Sitzungskonfiguration.</span><span class="sxs-lookup"><span data-stu-id="70ed7-153">The name of your registered Session Configuration.</span></span> <span data-ttu-id="70ed7-154">Dies ist der gleiche Name, den Benutzer im ConfigurationName-Parameter angeben, wenn sie mithilfe von `Enter-PSSession` oder `New-PSSession` eine Verbindung mit Ihrem Endpunkt herstellen.</span><span class="sxs-lookup"><span data-stu-id="70ed7-154">This is the same name users provide to the "ConfigurationName" parameter when they connect to your endpoint with `Enter-PSSession` or `New-PSSession`.</span></span>

<span data-ttu-id="70ed7-155">Um die Sitzungskonfiguration auf Ihrem lokalen Computer zu registrieren, führen Sie folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="70ed7-155">To register the Session Configuration on your local machine, run the following command:</span></span>

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

<span data-ttu-id="70ed7-156">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="70ed7-156">Congratulations!</span></span> <span data-ttu-id="70ed7-157">Sie haben Ihren JEA-Endpunkt eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="70ed7-157">You have set up your JEA endpoint.</span></span>

## <a name="test-out-your-endpoint"></a><span data-ttu-id="70ed7-158">Testen Ihres Endpunkts</span><span class="sxs-lookup"><span data-stu-id="70ed7-158">Test Out Your Endpoint</span></span>
<span data-ttu-id="70ed7-159">Führen Sie die Schritte im Abschnitt [Verwenden von JEA](using-jea.md) erneut für Ihren neuen Endpunkt aus, um zu überprüfen, ob er erwartungsgemäß ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="70ed7-159">Re-run the steps listed in the [Using JEA](using-jea.md) section against your new endpoint to confirm it is operating as intended.</span></span>
<span data-ttu-id="70ed7-160">Stellen Sie sicher, dass Sie einen neuen Endpunktnamen verwenden (JEADemo2), wenn Sie den Konfigurationsnamen in `Enter-PSSession` bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="70ed7-160">Be sure to use the new endpoint name (JEADemo2) when providing the configuration name to `Enter-PSSession`.</span></span>

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

## <a name="key-concepts"></a><span data-ttu-id="70ed7-161">Wichtige Konzepte</span><span class="sxs-lookup"><span data-stu-id="70ed7-161">Key Concepts</span></span>
<span data-ttu-id="70ed7-162">**PowerShell Session-Sitzungskonfiguration**: Wird auch als *PowerShell-Endpunkt* bezeichnet und ist im übertragenen Sinn der „Ort“, an dem Benutzer eine Verbindung herstellen und Zugriff auf PowerShell-Funktionen erhalten.</span><span class="sxs-lookup"><span data-stu-id="70ed7-162">**PowerShell Session Configuration**: Sometimes referred to as *PowerShell Endpoint*, this is the figurative "place" where users connect and get access to PowerShell functionality.</span></span>
<span data-ttu-id="70ed7-163">Sie können die in Ihrem System registrierten Sitzungskonfigurationen durch Ausführen von `Get-PSSessionConfiguration` auflisten.</span><span class="sxs-lookup"><span data-stu-id="70ed7-163">You can list the registered Session Configurations on your system by running `Get-PSSessionConfiguration`.</span></span>
<span data-ttu-id="70ed7-164">Wenn eine PowerShell-Sitzungskonfiguration auf bestimmte Weise konfiguriert ist, kann sie auch als *JEA-Endpunkt* bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="70ed7-164">When configured in a specific way, a PowerShell Session Configuration can be called a *JEA Endpoint*.</span></span>

<span data-ttu-id="70ed7-165">**PowerShell-Sitzungskonfigurationsdatei (PSSC)**: Eine Datei, die nach der Registrierung Einstellungen für eine PowerShell-Sitzungskonfiguration definiert.</span><span class="sxs-lookup"><span data-stu-id="70ed7-165">**PowerShell Session Configuration File (.pssc)**: A file that, when registered, defines settings for a PowerShell Session Configuration.</span></span>
<span data-ttu-id="70ed7-166">Sie enthält Spezifikationen für Benutzerrollen, die eine Verbindung mit dem Endpunkt herstellen können, das ausführende virtuelle Konto sowie weitere Details.</span><span class="sxs-lookup"><span data-stu-id="70ed7-166">It contains specifications for user roles that can connect to the endpoint, the "run as" Virtual Account, and more.</span></span>     

<span data-ttu-id="70ed7-167">**RoleDefinitions**: Das Feld in einer Sitzungskonfigurationsdatei, das die Rollenfunktionen definiert, die verbundene Benutzer ausführen können.</span><span class="sxs-lookup"><span data-stu-id="70ed7-167">**Role Definitions**: The field in a Session Configuration File that defines the Role Capabilities granted to connecting users.</span></span>
<span data-ttu-id="70ed7-168">Es definiert, *welcher Benutzer* mit einem privilegierten Konto *welche Aufgaben* ausführen darf.</span><span class="sxs-lookup"><span data-stu-id="70ed7-168">It defines *who* can do *what* as a privileged account.</span></span>
<span data-ttu-id="70ed7-169">Dies ist das Kernstück der RBAC-Funktionalität von JEA.</span><span class="sxs-lookup"><span data-stu-id="70ed7-169">This is the core of JEA's RBAC capabilities.</span></span>

<span data-ttu-id="70ed7-170">**SessionType**: Ein Feld in einer Sitzungskonfigurationsdatei, das Standardeinstellungen für eine Sitzungskonfiguration darstellt.</span><span class="sxs-lookup"><span data-stu-id="70ed7-170">**SessionType**: A field in a Session Configuration File that represents default settings for a Session Configuration.</span></span>
<span data-ttu-id="70ed7-171">Bei JEA-Endpunkten muss dieses Feld auf RestrictedRemoteServer festgelegt sein.</span><span class="sxs-lookup"><span data-stu-id="70ed7-171">For JEA endpoints, this must be set to RestrictedRemoteServer.</span></span>

<span data-ttu-id="70ed7-172">**PowerShell-Aufzeichnung**: Eine Datei mit einem Mitschnitt einer PowerShell-Sitzung.</span><span class="sxs-lookup"><span data-stu-id="70ed7-172">**PowerShell Transcript**: A file containing an "over-the-shoulder" view of a PowerShell session.</span></span>
<span data-ttu-id="70ed7-173">Sie können PowerShell mithilfe des Felds TranscriptDirectory so einrichten, dass Aufzeichnungen von JEA-Sitzungen generiert werden.</span><span class="sxs-lookup"><span data-stu-id="70ed7-173">You can set PowerShell to generate transcripts for JEA sessions using the TranscriptDirectory field.</span></span>
<span data-ttu-id="70ed7-174">Weitere Informationen über Aufzeichnungen finden Sie in diesem [Blogbeitrag](https://technet.microsoft.com/en-us/magazine/ff687007.aspx).</span><span class="sxs-lookup"><span data-stu-id="70ed7-174">For more information on transcripts, check out this [blog post](https://technet.microsoft.com/en-us/magazine/ff687007.aspx).</span></span>

