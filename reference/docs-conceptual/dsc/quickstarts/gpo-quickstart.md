---
ms.date: 07/09/2019
keywords: DSC, GPO, PowerShell, Konfiguration, Setup
title: Schnellstart – Konvertieren von Gruppenrichtlinien in DSC
ms.openlocfilehash: 8c89dbbce5b2b146194b799d7e36ecce3105bfeb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953467"
---
> <span data-ttu-id="98b3a-103">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="98b3a-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart-convert-group-policy-into-dsc"></a><span data-ttu-id="98b3a-104">Schnellstart: Konvertieren von Gruppenrichtlinien in DSC</span><span class="sxs-lookup"><span data-stu-id="98b3a-104">Quickstart: Convert Group Policy into DSC</span></span>

<span data-ttu-id="98b3a-105">Sie können eine DSC-Konfiguration aus einer Gruppenrichtlinie oder Azure Security Center-Baseline generieren.</span><span class="sxs-lookup"><span data-stu-id="98b3a-105">You can generate a DSC configuration from a Group Policy or Azure Security Center baseline.</span></span> <span data-ttu-id="98b3a-106">Das Modul [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) umfasst die folgenden Befehle für diese Aufgabe.</span><span class="sxs-lookup"><span data-stu-id="98b3a-106">The [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) module includes the following commands for accomplishing this task.</span></span>

- <span data-ttu-id="98b3a-107">`ConvertFrom-GPO`: Konvertiert Gruppenrichtlinien, als Dateien gespeichert.</span><span class="sxs-lookup"><span data-stu-id="98b3a-107">`ConvertFrom-GPO` - Converts Group Policies, stored as files.</span></span> <span data-ttu-id="98b3a-108">Sie können auch ein Verzeichnis mit mehreren Richtlinien angeben, die in einer Konfiguration zusammengefasst werden.</span><span class="sxs-lookup"><span data-stu-id="98b3a-108">You can also specify a directory containing multiple policies that will be combined into one Configuration.</span></span>
  - <span data-ttu-id="98b3a-109">Verwenden Sie zum Exportieren von Gruppenrichtlinien in Ihrer Umgebung das Cmdlet [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps), oder folgen Sie den Anweisungen unter [Export a GPO to a File (Exportieren von Gruppenrichtlinienobjekten in eine Datei)](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span><span class="sxs-lookup"><span data-stu-id="98b3a-109">To export Group Policies in your environment, use the [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet, or follow the instructions in [Export a GPO to a File](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span></span>
- <span data-ttu-id="98b3a-110">`ConvertFrom-SCM`: Konvertiert Security Compliance Manager-Baselines, als `.xml`-Dateien gespeichert.</span><span class="sxs-lookup"><span data-stu-id="98b3a-110">`ConvertFrom-SCM` - Converts Security Compliance Manager baselines, stored as `.xml` files.</span></span>
- <span data-ttu-id="98b3a-111">`ConvertFrom-ASC`: Konvertiert Azure Security Center-Baselines, als `.json`-Dateien gespeichert.</span><span class="sxs-lookup"><span data-stu-id="98b3a-111">`ConvertFrom-ASC` - Converts Azure Security Center baselines, stored as `.json` files.</span></span>
- <span data-ttu-id="98b3a-112">`Merge-GPOs`: Konvertiert auf einen Zielcomputer angewendete Gruppenrichtlinien.</span><span class="sxs-lookup"><span data-stu-id="98b3a-112">`Merge-GPOs` - Converts Group Policies applied to a target computer.</span></span>

<span data-ttu-id="98b3a-113">Mit den oben aufgeführten Cmdlets wird eine Baseline in eine DSC-`.mof`-Datei konvertiert.</span><span class="sxs-lookup"><span data-stu-id="98b3a-113">The cmdlets listed above convert a baseline into a DSC `.mof` file.</span></span> <span data-ttu-id="98b3a-114">Sie können auch ein Konfigurationsskript ausgeben (`.ps1`), das bearbeitet und neu kompiliert werden kann.</span><span class="sxs-lookup"><span data-stu-id="98b3a-114">You can also choose to output a Configuration script (`.ps1`), that you can edit and recompile.</span></span> <span data-ttu-id="98b3a-115">Die Cmdlets erkennen Kompilierungsfehler für fehlende Ressourcen oder doppelte Ressourcenblöcke.</span><span class="sxs-lookup"><span data-stu-id="98b3a-115">The cmdlets detect compilation errors for missing resources, or duplicate resource blocks.</span></span> <span data-ttu-id="98b3a-116">Ressourcenblöcke, die Kompilierungsfehler verursachen, werden auskommentiert.</span><span class="sxs-lookup"><span data-stu-id="98b3a-116">Resource blocks that would cause compilation errors are commented out.</span></span>

<span data-ttu-id="98b3a-117">Im folgenden Beispiel wird eine [Microsoft Security-Baseline](https://www.microsoft.com/en-us/download/details.aspx?id=55319) in ein DSC-Konfigurationsskript (`.ps1`) und eine `.mof`-Datei konvertiert.</span><span class="sxs-lookup"><span data-stu-id="98b3a-117">The following example converts a [Microsoft Security Baseline](https://www.microsoft.com/en-us/download/details.aspx?id=55319) into a DSC configuration script (`.ps1`) and `.mof` file.</span></span>

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

<span data-ttu-id="98b3a-118">Nach dem Ausführen der Befehle sehen Sie zwei Dateien im Standardausgabeverzeichnis, das unter dem aktuellen Pfad erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="98b3a-118">After running the commands, you see two files in the default "Output" directory created under your current path.</span></span>

```powershell
Get-ChildItem -Path .\Output
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----         7/9/2019   9:35 AM   227.37KB DSCFromGPO.ps1
-a----         7/9/2019   9:35 AM   410.03KB localhost.mof
```

<span data-ttu-id="98b3a-119">Für jeden verwalteten Knoten sind außerdem die folgenden zwei Module erforderlich:</span><span class="sxs-lookup"><span data-stu-id="98b3a-119">Each managed node will also need the following two modules:</span></span>

- [<span data-ttu-id="98b3a-120">SecurityPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="98b3a-120">SecurityPolicyDSC</span></span>](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [<span data-ttu-id="98b3a-121">AuditPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="98b3a-121">AuditPolicyDSC</span></span>](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> <span data-ttu-id="98b3a-122">**BaselineManagement** ist eine von der Community entwickelte Lösung, durch die DSC für den Support leichter analysierbar ist, da Communitylösungen von den Projektverantwortlichen und nicht von Microsoft stammen.</span><span class="sxs-lookup"><span data-stu-id="98b3a-122">**BaselineManagement** is a solution developed by the community to make DSC more discoverable for Support for community solutions come from the project maintainers and not from Microsoft.</span></span> <span data-ttu-id="98b3a-123">Sie können ein neues Problem für **BaselineManagement** auf [GitHub](https://github.com/microsoft/BaselineManagement) öffnen.</span><span class="sxs-lookup"><span data-stu-id="98b3a-123">You can open a new issue for **BaselineManagement** on [GitHub](https://github.com/microsoft/BaselineManagement).</span></span>

## <a name="next-steps"></a><span data-ttu-id="98b3a-124">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="98b3a-124">Next steps</span></span>

- <span data-ttu-id="98b3a-125">Informationen zum Hochladen Ihres Konfigurationsskripts in Azure Automation State Configuration finden Sie unter [Erste Schritte](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span><span class="sxs-lookup"><span data-stu-id="98b3a-125">To upload your configuration script into Azure Automation State Configuration, see [Getting Started](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span></span>
- <span data-ttu-id="98b3a-126">Fügen Sie Ihrem [Automation-Konto](/azure/automation/shared-resources/modules) das **SecurityPolicyDSC**-Modul und das **AuditPolicyDSC**-Modul hinzu.</span><span class="sxs-lookup"><span data-stu-id="98b3a-126">Add the **SecurityPolicyDSC** and **AuditPolicyDSC** modules to your [Automation Account](/azure/automation/shared-resources/modules).</span></span>
- <span data-ttu-id="98b3a-127">DSC-Konfigurationen und -Ressourcen finden Sie unter [PowerShell-Katalog](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="98b3a-127">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
