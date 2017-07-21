---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Bekannte Probleme in WMF 5.1
ms.openlocfilehash: 93113962781f1cc84a80f8f97f56ffd7622fec6b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="944e6-103">Bekannte Probleme in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="944e6-103">Known Issues in WMF 5.1</span></span> #

> <span data-ttu-id="944e6-104">Hinweis: Diese Dokumentation kann geändert werden.</span><span class="sxs-lookup"><span data-stu-id="944e6-104">Note: This information is subject to change.</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="944e6-105">Starten der PowerShell-Verknüpfung als Administrator</span><span class="sxs-lookup"><span data-stu-id="944e6-105">Starting PowerShell shortcut as Administrator</span></span>
<span data-ttu-id="944e6-106">Nach der Installation von WMF erhalten Sie möglicherweise eine Fehlermeldung „Undefinierter Fehler“, wenn Sie versuchen, PowerShell als Administrator über die Verknüpfung zu starten.</span><span class="sxs-lookup"><span data-stu-id="944e6-106">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span>
<span data-ttu-id="944e6-107">Öffnen Sie die Verknüpfung erneut als Nicht-Administrator. Anschließend funktioniert die Verknüpfung auch, wenn Sie sie als Administrator verwenden.</span><span class="sxs-lookup"><span data-stu-id="944e6-107">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="944e6-108">Pester</span><span class="sxs-lookup"><span data-stu-id="944e6-108">Pester</span></span>
<span data-ttu-id="944e6-109">In diesem Release treten zwei Probleme auf, derer Sie sich bewusst sein sollten, wenn Sie Pester auf Nano Server verwenden:</span><span class="sxs-lookup"><span data-stu-id="944e6-109">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

* <span data-ttu-id="944e6-110">Wenn Pester selbst getestet wird, treten einige Fehler aufgrund von Unterschieden zwischen FullCLR und CoreCLR auf.</span><span class="sxs-lookup"><span data-stu-id="944e6-110">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="944e6-111">Vor allem ist die Validate-Methode für den Typ „XmlDocument“ nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="944e6-111">In particular, the Validate method is not available on the XmlDocument type.</span></span> <span data-ttu-id="944e6-112">Sechs Tests, die versuchen, das Schema der NUnit-Ausgabeprotokolle zu überprüfen, sind dafür bekannt, dass sie Fehler ausgeben.</span><span class="sxs-lookup"><span data-stu-id="944e6-112">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span> 
* <span data-ttu-id="944e6-113">Bei einem Code Coverage-Test tritt aktuell ein Fehler auf, da die DSC-Ressource *WindowsFeature* in Nano Server nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="944e6-113">One Code Coverage test fails currently because the *WindowsFeature* DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="944e6-114">Diese Fehler haben in der Regel jedoch keine Auswirkungen und können ohne Weiteres ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="944e6-114">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="944e6-115">Überprüfung des Vorgangs</span><span class="sxs-lookup"><span data-stu-id="944e6-115">Operation Validation</span></span> 

* <span data-ttu-id="944e6-116">Bei „Update-Help“ tritt aufgrund eines nicht funktionierenden Hilfe-URIs ein Fehler für das Modul „Microsoft.PowerShell.Operation.Validation“ auf.</span><span class="sxs-lookup"><span data-stu-id="944e6-116">Update-Help fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="944e6-117">DSC nach Deinstallieren von WMF</span><span class="sxs-lookup"><span data-stu-id="944e6-117">DSC after uninstall WMF</span></span> 
* <span data-ttu-id="944e6-118">Nach Deinstallieren von WMF werden DSC MOF-Dokumente nicht aus dem Ordner „Configuration“ gelöscht.</span><span class="sxs-lookup"><span data-stu-id="944e6-118">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="944e6-119">DSC funktioniert nicht ordnungsgemäß, wenn die MOF-Dokumente neuere Eigenschaften enthalten, die auf den älteren Systemen nicht verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="944e6-119">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="944e6-120">In diesem Fall führen Sie in einer PowerShell-Konsole mit erhöhten Rechten das folgende Skript aus, um die DSC-Status zu bereinigen.</span><span class="sxs-lookup"><span data-stu-id="944e6-120">In this case, run the following script from elevated PowerShell console to to clean up the DSC states.</span></span>
 ```PowerShell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```  

## <a name="jea-virtual-accounts"></a><span data-ttu-id="944e6-121">Virtuelle JEA-Konten</span><span class="sxs-lookup"><span data-stu-id="944e6-121">JEA Virtual Accounts</span></span>
<span data-ttu-id="944e6-122">Zur Verwendung virtueller Konten in WMF 5.0 konfigurierte JEA-Endpunkte und -Sitzungskonfigurationen werden nach dem Upgrade auf WMF 5.1 nicht für die Verwendung eines virtuellen Kontos konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="944e6-122">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span>
<span data-ttu-id="944e6-123">Dies bedeutet, dass in JEA-Sitzungen ausgeführte Befehle unter der Identität des verbindenden Benutzers und nicht unter einem temporären Administratorkonto ausgeführt werden, was möglicherweise dazu führt, dass der Benutzer keine Befehle ausführen kann, für die erhöhte Rechte erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="944e6-123">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span>
<span data-ttu-id="944e6-124">Um die virtuellen Konten wiederherzustellen, müssen Sie die Registrierung für alle Sitzungskonfigurationen, die virtuelle Konten verwenden, aufheben und diese anschließend wieder registrieren.</span><span class="sxs-lookup"><span data-stu-id="944e6-124">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```

