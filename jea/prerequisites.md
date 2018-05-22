---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: JEA-Voraussetzungen
ms.openlocfilehash: a5cf5519b30b24d44c12bdeedcf4cd763e2edbde
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
# <a name="prerequisites"></a><span data-ttu-id="28f17-103">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="28f17-103">Prerequisites</span></span>

> <span data-ttu-id="28f17-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="28f17-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="28f17-105">„Just Enough Administration“ ist ein in Windows PowerShell 5.0 und höher enthaltenes Feature.</span><span class="sxs-lookup"><span data-stu-id="28f17-105">Just Enough Administration is a feature included with Windows PowerShell 5.0 and higher.</span></span>
<span data-ttu-id="28f17-106">Dieses Thema beschreibt die Voraussetzungen, die erfüllt sein müssen, um JEA verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="28f17-106">This topic describes the prerequisites that must be satisfied in order to start using JEA.</span></span>

## <a name="install-jea"></a><span data-ttu-id="28f17-107">Installieren von JEA</span><span class="sxs-lookup"><span data-stu-id="28f17-107">Install JEA</span></span>

<span data-ttu-id="28f17-108">JEA ist in Windows PowerShell 5.0 und höher verfügbar. Wenn Sie jedoch die vollständige Funktionalität nutzen möchten, empfehlen wir Ihnen die Installation der neuesten Version von PowerShell für Ihr Betriebssystem.</span><span class="sxs-lookup"><span data-stu-id="28f17-108">JEA is available with Windows PowerShell 5.0 and higher, but for full functionality it is recommended that you install the latest version of PowerShell available for your system.</span></span>
<span data-ttu-id="28f17-109">Die folgende Tabelle beschreibt die Verfügbarkeit von JEA unter Windows Server:</span><span class="sxs-lookup"><span data-stu-id="28f17-109">The following table describes JEA's availability on Windows Server:</span></span>

<span data-ttu-id="28f17-110">Serverbetriebssystem</span><span class="sxs-lookup"><span data-stu-id="28f17-110">Server Operating System</span></span>   | <span data-ttu-id="28f17-111">JEA-Verfügbarkeit</span><span class="sxs-lookup"><span data-stu-id="28f17-111">JEA Availability</span></span>
--------------------------|--------------------------------
<span data-ttu-id="28f17-112">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="28f17-112">Windows Server 2016</span></span>       | <span data-ttu-id="28f17-113">Vorinstalliert</span><span class="sxs-lookup"><span data-stu-id="28f17-113">Preinstalled</span></span>
<span data-ttu-id="28f17-114">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="28f17-114">Windows Server 2012 R2</span></span>    | <span data-ttu-id="28f17-115">Vollständige Funktionalität mit WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="28f17-115">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="28f17-116">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="28f17-116">Windows Server 2012</span></span>       | <span data-ttu-id="28f17-117">Vollständige Funktionalität mit WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="28f17-117">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="28f17-118">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="28f17-118">Windows Server 2008 R2</span></span>    | <span data-ttu-id="28f17-119">Reduzierte Funktionalität<sup>1</sup> mit WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="28f17-119">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="28f17-120">Sie können JEA auch auf Ihrem Heim- oder Firmencomputer verwenden:</span><span class="sxs-lookup"><span data-stu-id="28f17-120">You can also use JEA on your home or work computer:</span></span>

<span data-ttu-id="28f17-121">Clientbetriebssystem</span><span class="sxs-lookup"><span data-stu-id="28f17-121">Client Operating System</span></span>   | <span data-ttu-id="28f17-122">JEA-Verfügbarkeit</span><span class="sxs-lookup"><span data-stu-id="28f17-122">JEA Availability</span></span>
--------------------------|-----------------------------------------------------
<span data-ttu-id="28f17-123">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="28f17-123">Windows 10 1607+</span></span>          | <span data-ttu-id="28f17-124">Vorinstalliert</span><span class="sxs-lookup"><span data-stu-id="28f17-124">Preinstalled</span></span>
<span data-ttu-id="28f17-125">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="28f17-125">Windows 10 1603, 1511</span></span>     | <span data-ttu-id="28f17-126">Vorinstalliert, mit eingeschränkter Funktionalität<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="28f17-126">Preinstalled, with reduced functionality<sup>2</sup></span></span>
<span data-ttu-id="28f17-127">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="28f17-127">Windows 10 1507</span></span>           | <span data-ttu-id="28f17-128">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="28f17-128">Not available</span></span>
<span data-ttu-id="28f17-129">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="28f17-129">Windows 8, 8.1</span></span>            | <span data-ttu-id="28f17-130">Vollständige Funktionalität mit WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="28f17-130">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="28f17-131">Windows 7</span><span class="sxs-lookup"><span data-stu-id="28f17-131">Windows 7</span></span>                 | <span data-ttu-id="28f17-132">Reduzierte Funktionalität<sup>1</sup> mit WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="28f17-132">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="28f17-133"><sup>1</sup> JEA kann nicht konfiguriert werden, um gruppenverwaltete Dienstkonten unter Windows Server 2008 R2 oder Windows 7 zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="28f17-133"><sup>1</sup> JEA cannot be configured to use group managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span>
<span data-ttu-id="28f17-134">Virtuelle Konten und andere JEA-Features *werden* unterstützt.</span><span class="sxs-lookup"><span data-stu-id="28f17-134">Virtual accounts and other JEA features *are* supported.</span></span>

<span data-ttu-id="28f17-135"><sup>2</sup> Die folgenden JEA-Features werden von den Windows 10-Versionen 1511 und 1603 nicht unterstützt: Ausführen als gruppenverwaltetes Dienstkonto, bedingte Zugriffsregeln in Sitzungskonfigurationen, Benutzerlaufwerk und Gewähren von Zugriff auf lokale Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="28f17-135"><sup>2</sup> Windows 10 versions 1511 and 1603 do not support the following JEA features: running as a group managed service account, conditional access rules in session configurations, the user drive, and granting access to local user accounts.</span></span>
<span data-ttu-id="28f17-136">Aktualisieren Sie Windows auf Version 1607 (Anniversary Update) oder höher, um Unterstützung für diese Features zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="28f17-136">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="28f17-137">Überprüfen der installierten Version von PowerShell</span><span class="sxs-lookup"><span data-stu-id="28f17-137">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="28f17-138">Überprüfen Sie die `$PSVersionTable`-Variable in einer Windows PowerShell-Aufforderung, um festzustellen, welche PowerShell-Version auf Ihrem System installiert ist.</span><span class="sxs-lookup"><span data-stu-id="28f17-138">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
PS C:\> $PSVersionTable.PSVersion

Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="28f17-139">Sie können JEA verwenden, wenn die *Hauptversion* mindestens **5** ist.</span><span class="sxs-lookup"><span data-stu-id="28f17-139">You are ready to use JEA if the *Major* version is equal to or greater than **5**.</span></span>
<span data-ttu-id="28f17-140">Wir empfehlen Ihnen, soweit möglich, ein Upgrade auf die PowerShell-Version **5.1** durchzuführen, um sich optimale Ergebnisse und Zugriff auf die neuesten Features zu sichern.</span><span class="sxs-lookup"><span data-stu-id="28f17-140">For the best experience, and to have access to all the latest features, it is recommended that you upgrade to PowerShell version **5.1** when possible.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="28f17-141">Installieren von Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="28f17-141">Install Windows Management Framework</span></span>

<span data-ttu-id="28f17-142">Wenn Sie eine ältere Version von PowerShell ausführen, müssen Sie Ihr System mit dem aktuellen Update von Windows Management Framework (WMF) aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="28f17-142">If you are running an older version of PowerShell, you will need to update your system with the latest Windows Management Framework (WMF) update.</span></span>
<span data-ttu-id="28f17-143">Updatepakete und einen Link zu den neuesten Anmerkungen zur WMF-Version finden Sie im [Download Center](https://aka.ms/WMF5).</span><span class="sxs-lookup"><span data-stu-id="28f17-143">Update packages and a link to the latest WMF release notes are available in the [Download Center](https://aka.ms/WMF5).</span></span>

<span data-ttu-id="28f17-144">Es wird dringend empfohlen, vor dem Upgrade aller Server die Kompatibilität Ihrer Workload mit WMF zu testen.</span><span class="sxs-lookup"><span data-stu-id="28f17-144">It is strongly recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="28f17-145">Windows 10-Benutzer sollten die neuesten Funktionsupdates zum Abrufen der aktuellen Version von Windows PowerShell installieren.</span><span class="sxs-lookup"><span data-stu-id="28f17-145">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="28f17-146">Aktivieren von PowerShell-Remoting</span><span class="sxs-lookup"><span data-stu-id="28f17-146">Enable PowerShell Remoting</span></span>

<span data-ttu-id="28f17-147">PowerShell-Remoting stellt die Grundlage für JEA dar.</span><span class="sxs-lookup"><span data-stu-id="28f17-147">PowerShell Remoting provides the foundation on which JEA is built.</span></span>
<span data-ttu-id="28f17-148">Daher sollten Sie sicherstellen, dass PowerShell-Remoting aktiviert ist und auf Ihrem System [ordnungsgemäß abgesichert](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) ist, bevor Sie JEA verwenden können.</span><span class="sxs-lookup"><span data-stu-id="28f17-148">It is therefore necessary to ensure PowerShell Remoting is enabled and [properly secured](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) on your system before you can use JEA.</span></span>

<span data-ttu-id="28f17-149">PowerShell-Remoting ist unter Windows Server 2012, 2012 R2 und 2016 standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="28f17-149">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span>
<span data-ttu-id="28f17-150">Sie können PowerShell-Remoting aktivieren, indem Sie den folgenden Befehl in einem PowerShell-Fenster mit erhöhten Rechten ausführen.</span><span class="sxs-lookup"><span data-stu-id="28f17-150">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="28f17-151">Aktivieren der PowerShell-Modul- und Skriptblockprotokollierung (optional)</span><span class="sxs-lookup"><span data-stu-id="28f17-151">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="28f17-152">Die folgenden Schritte aktivieren die Protokollierung für alle PowerShell-Aktionen in Ihrem System.</span><span class="sxs-lookup"><span data-stu-id="28f17-152">The following steps enable logging for all PowerShell actions on your system.</span></span>
<span data-ttu-id="28f17-153">Für JEA ist die PowerShell-Modulprotokollierung nicht erforderlich. Es wird jedoch dringend empfohlen, dass Sie dieses Feature aktivieren, um sicherzustellen, dass von Benutzern ausgeführte Befehle an einem zentralen Ort protokolliert werden.</span><span class="sxs-lookup"><span data-stu-id="28f17-153">PowerShell Module Logging is not required for JEA, however it is strongly recommended that you turn it on to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="28f17-154">Sie können die Richtlinien für die PowerShell-Modulprotokollierung mithilfe von Gruppenrichtlinien konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="28f17-154">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="28f17-155">Öffnen Sie den Editor für lokale Gruppenrichtlinien auf einer Arbeitsstation oder ein Gruppenrichtlinienobjekt in der Gruppenrichtlinien-Verwaltungskonsole auf einem Active Directory-Domänencontroller.</span><span class="sxs-lookup"><span data-stu-id="28f17-155">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="28f17-156">Navigieren Sie zu **Computerkonfiguration\\Administrative Vorlagen\\Windows-Komponenten\\Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="28f17-156">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="28f17-157">Doppelklicken Sie auf **Modulprotokollierung aktivieren**.</span><span class="sxs-lookup"><span data-stu-id="28f17-157">Double click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="28f17-158">Klicken Sie auf **Aktiviert**.</span><span class="sxs-lookup"><span data-stu-id="28f17-158">Click **Enabled**</span></span>
5. <span data-ttu-id="28f17-159">Klicken Sie im Abschnitt „Optionen“ neben den Modulnamen auf **Anzeigen** </span><span class="sxs-lookup"><span data-stu-id="28f17-159">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="28f17-160">Geben Sie „**\***“ in das Popupfenster ein.</span><span class="sxs-lookup"><span data-stu-id="28f17-160">Type "**\***" in the pop up window.</span></span> <span data-ttu-id="28f17-161">So wird PowerShell angewiesen, Befehle aus allen Modulen zu protokollieren.</span><span class="sxs-lookup"><span data-stu-id="28f17-161">This instructs PowerShell to log commands from all modules.</span></span>
7. <span data-ttu-id="28f17-162">Klicken Sie auf **OK**, um die Richtlinie festzulegen.</span><span class="sxs-lookup"><span data-stu-id="28f17-162">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="28f17-163">Doppelklicken Sie anschließend auf **Protokollierung von PowerShell-Skriptblöcken aktivieren**.</span><span class="sxs-lookup"><span data-stu-id="28f17-163">Double click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="28f17-164">Klicken Sie auf **Aktiviert**.</span><span class="sxs-lookup"><span data-stu-id="28f17-164">Click **Enabled**</span></span>
10. <span data-ttu-id="28f17-165">Klicken Sie auf **OK**, um die Richtlinie festzulegen.</span><span class="sxs-lookup"><span data-stu-id="28f17-165">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="28f17-166">(Nur auf der Domäne zugehörige Computer:) Führen Sie **gpupdate** aus, oder warten Sie, bis die Gruppenrichtlinie die aktualisierte Richtlinie verarbeitet hat und diese Einstellungen anwendet.</span><span class="sxs-lookup"><span data-stu-id="28f17-166">(On domain-joined machines only) Run **gpupdate** or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="28f17-167">Sie können über eine Gruppenrichtlinie auch die systemweite PowerShell-Aufzeichnung aktivieren.</span><span class="sxs-lookup"><span data-stu-id="28f17-167">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="28f17-168">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="28f17-168">Next steps</span></span>

- [<span data-ttu-id="28f17-169">Create a role capability file (Erstellen einer Rollenfunktionsdatei)</span><span class="sxs-lookup"><span data-stu-id="28f17-169">Create a role capability file</span></span>](role-capabilities.md)
- [<span data-ttu-id="28f17-170">Create a session configuration file (Erstellen einer Sitzungskonfigurationsdatei)</span><span class="sxs-lookup"><span data-stu-id="28f17-170">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="28f17-171">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="28f17-171">See also</span></span>

- [<span data-ttu-id="28f17-172">Sicherheitsaspekte von PowerShell-Remoting</span><span class="sxs-lookup"><span data-stu-id="28f17-172">Additional information about PowerShell Remoting and WinRM security</span></span>](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity)
- [<span data-ttu-id="28f17-173">*PowerShell ♥ the Blue Team (PowerShell ♥ das Blue Team)* – Blogbeitrag zum Thema Sicherheit</span><span class="sxs-lookup"><span data-stu-id="28f17-173">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)