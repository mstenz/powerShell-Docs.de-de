---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Ressourcenabhängigkeiten mithilfe von DependsOn
ms.openlocfilehash: 5ea08c76c203188f41513ad0cc1f4571579b4172
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954477"
---
# <a name="resource-dependencies-using-dependson"></a><span data-ttu-id="a91e6-103">Ressourcenabhängigkeiten mithilfe von DependsOn</span><span class="sxs-lookup"><span data-stu-id="a91e6-103">Resource dependencies using DependsOn</span></span>

<span data-ttu-id="a91e6-104">Wenn Sie [Konfigurationen](configurations.md) schreiben, fügen Sie [Ressourcenblöcke](../resources/resources.md) hinzu, um Aspekte eines Zielknotens zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="a91e6-104">When you write [Configurations](configurations.md), you add [Resource blocks](../resources/resources.md) to configure aspects of a target Node.</span></span> <span data-ttu-id="a91e6-105">Wenn immer mehr Ressourcenblöcke hinzugefügt werden, können Konfigurationen recht groß und ihre Verwaltung aufwändig werden.</span><span class="sxs-lookup"><span data-stu-id="a91e6-105">As you continue to add Resource blocks, your Configurations can grow quite large and cumbersome to manage.</span></span> <span data-ttu-id="a91e6-106">Eine Herausforderung besteht hierbei in der Reihenfolge der Anwendung Ihrer Ressourcenblöcke.</span><span class="sxs-lookup"><span data-stu-id="a91e6-106">One such challenge is the applied order of your resource blocks.</span></span> <span data-ttu-id="a91e6-107">Normalerweise werden Ressourcen in der Reihenfolge angewendet, in der sie in der Konfiguration angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="a91e6-107">Typically resources are applied in the order they are defined within the Configuration.</span></span> <span data-ttu-id="a91e6-108">Wenn Ihre Konfiguration größer und komplexer wird, können Sie den `DependsOn`-Schlüssel verwenden, um die Reihenfolge der Anwendung Ihrer Ressourcen zu ändern, indem Sie angeben, dass eine Ressource von einer anderen abhängt.</span><span class="sxs-lookup"><span data-stu-id="a91e6-108">As your Configuration grows larger and more complex, you can use the `DependsOn` key to change the applied order of your resources by specifying that a resource depends on another resource.</span></span>

<span data-ttu-id="a91e6-109">Der `DependsOn`-Schlüssel kann in jedem Ressourcenblock verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a91e6-109">The `DependsOn` key can be used in any Resource block.</span></span> <span data-ttu-id="a91e6-110">Er wird mit denselben Schlüssel/Wert-Mechanismen angegeben wie andere Ressourcenschlüssel.</span><span class="sxs-lookup"><span data-stu-id="a91e6-110">It is defined with the same key/value mechanism as other Resource keys.</span></span> <span data-ttu-id="a91e6-111">Der `DependsOn`-Schlüssel erwartet ein Zeichenfolgenarray mit folgender Syntax.</span><span class="sxs-lookup"><span data-stu-id="a91e6-111">The `DependsOn` key expects an array of strings with the following syntax.</span></span>

```
DependsOn = '[<Resource Type>]<Resource Name>', '[<Resource Type>]<Resource Name'
```

<span data-ttu-id="a91e6-112">Im folgenden Beispiel wird eine Firewallregel konfiguriert, nachdem das öffentliche Profil aktiviert und konfiguriert wurde.</span><span class="sxs-lookup"><span data-stu-id="a91e6-112">The following example configures a firewall rule after enabling and configuring the public profile.</span></span>

```powershell
# Install the NetworkingDSC module to configure firewall rules and profiles.
Install-Module -Name NetworkingDSC

Configuration ConfigureFirewall
{
    Import-DSCResource -Name Firewall, FirewallProfile
    Node localhost
    {
        Firewall Firewall
        {
            Name                  = 'IIS-WebServerRole-HTTP-In-TCP'
            Ensure                = 'Present'
            Enabled               = 'True'
            DependsOn             = '[FirewallProfile]FirewallProfilePublic'
        }

        FirewallProfile FirewallProfilePublic
        {
            Name = 'Public'
            Enabled = 'True'
            DefaultInboundAction = 'Block'
            DefaultOutboundAction = 'Allow'
            AllowInboundRules = 'True'
            AllowLocalFirewallRules = 'False'
            AllowLocalIPsecRules = 'False'
            NotifyOnListen = 'True'
            LogFileName = '%systemroot%\system32\LogFiles\Firewall\pfirewall.log'
            LogMaxSizeKilobytes = 16384
            LogAllowed = 'False'
            LogBlocked = 'True'
            LogIgnored = 'NotConfigured'
        }
    }
}

ConfigureFirewall -OutputPath C:\Temp\
```

<span data-ttu-id="a91e6-113">Wenn Sie die Konfiguration anwenden, wird das Firewallprofil immer zuerst konfiguriert, unabhängig davon, in welcher Reihenfolge die Ressourcenblöcke angegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="a91e6-113">When you apply the Configuration, the firewall profile will always be configured first regardless of which order the Resource blocks are defined.</span></span> <span data-ttu-id="a91e6-114">Wenn Sie die Konfiguration anwenden sollten Sie sich die Konfiguration Ihres vorhandenen Zielknotens notieren, um sie ggf. wiederherzustellen.</span><span class="sxs-lookup"><span data-stu-id="a91e6-114">If you apply the Configuration, be sure to note your target Nodes existing Configuration so you can revert if desired.</span></span>

```
PS> Start-DSCConfiguration -Verbose -Wait -Path C:\Temp\ -ComputerName localhost

VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-181338-0189125723-1543119021-1282804.
VERBOSE: [SERVER01]: LCM:  [ Start  Set      ]
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module C:\Program Files\WindowsPowerShell\Modules\NetworkingDsc\6.1.0.0\DscResources\MSFT_Firewall\MSFT_Firewall.psm1 in force mode.
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module C:\Program Files\WindowsPowerShell\Modules\NetworkingDsc\6.1.0.0\DscResources\MSFT_FirewallProfile\MSFT_FirewallProfile.psm1 in force mode.
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[FirewallProfile]FirewallProfilePublic]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[FirewallProfile]FirewallProfilePublic]
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Importing the module MSFT_FirewallProfile in force mode.
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Test-TargetResource: Testing Firewall Public Profile.
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Test-TargetResource: Firewall Public Profile "AllowInboundRules" is "NotConfigured" but should be "True". Change required.
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Test-TargetResource: Firewall Public Profile "AllowLocalFirewallRules" is "NotConfigured" but should be "False". Change required.
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Test-TargetResource: Firewall Public Profile "AllowLocalIPsecRules" is "NotConfigured" but should be "False". Change required.
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Test-TargetResource: Firewall Public Profile "DefaultOutboundAction" is "NotConfigured" but should be "Allow". Change required.
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Test-TargetResource: Firewall Public Profile "LogBlocked" is "False" but should be "True". Change required.
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Test-TargetResource: Firewall Public Profile "LogMaxSizeKilobytes" is "4096" but should be "16384". Change required.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[FirewallProfile]FirewallProfilePublic]  in 1.6890 seconds.
VERBOSE: [SERVER01]: LCM:  [ Start  Set      ]  [[FirewallProfile]FirewallProfilePublic]
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Importing the module MSFT_FirewallProfile in force mode.
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Set-TargetResource: Setting Firewall Public Profile.
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Set-TargetResource: Setting Firewall Public Profile parameter AllowInboundRules to "AllowInboundRules".
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Set-TargetResource: Setting Firewall Public Profile parameter AllowLocalFirewallRules to "AllowLocalFirewallRules".
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Set-TargetResource: Setting Firewall Public Profile parameter AllowLocalIPsecRules to "AllowLocalIPsecRules".
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Set-TargetResource: Setting Firewall Public Profile parameter DefaultOutboundAction to "DefaultOutboundAction".
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Set-TargetResource: Setting Firewall Public Profile parameter LogBlocked to "LogBlocked".
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Set-TargetResource: Setting Firewall Public Profile parameter LogMaxSizeKilobytes to "LogMaxSizeKilobytes".
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Set-TargetResource: Setting Firewall Public Profile updated.
VERBOSE: [SERVER01]: LCM:  [ End    Set      ]  [[FirewallProfile]FirewallProfilePublic]  in 10.0360 seconds.
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[FirewallProfile]FirewallProfilePublic]
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[Firewall]Firewall]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[Firewall]Firewall]
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Importing the module MSFT_Firewall in force mode.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Test-TargetResource: Checking settings for firewall rule with Name 'IIS-WebServerRole-HTTP-In-TCP'.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Test-TargetResource: Find firewall rule with Name 'IIS-WebServerRole-HTTP-In-TCP'.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Get-FirewallRule: No Firewall Rule found with Name 'IIS-WebServerRole-HTTP-In-TCP'.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Test-TargetResource: Firewall rule with Name 'IIS-WebServerRole-HTTP-In-TCP' does not exist.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Test-TargetResource: Check Firewall rule with Name 'IIS-WebServerRole-HTTP-In-TCP' returning False.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[Firewall]Firewall]  in 1.1780 seconds.
VERBOSE: [SERVER01]: LCM:  [ Start  Set      ]  [[Firewall]Firewall]
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Importing the module MSFT_Firewall in force mode.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Set-TargetResource: Applying settings for firewall rule with Name 'IIS-WebServerRole-HTTP-In-TCP'.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Set-TargetResource: Find firewall rule with Name 'IIS-WebServerRole-HTTP-In-TCP'.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Get-FirewallRule: No Firewall Rule found with Name 'IIS-WebServerRole-HTTP-In-TCP'.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Set-TargetResource: We want the firewall rule with Name 'IIS-WebServerRole-HTTP-In-TCP' to exist since Ensure is set to Present.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Set-TargetResource: We want the firewall rule with Name 'IIS-WebServerRole-HTTP-In-TCP' to exist, but it does not.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] New-NetFirewallRule DisplayName: IIS-WebServerRole-HTTP-In-TCP
VERBOSE: [SERVER01]: LCM:  [ End    Set      ]  [[Firewall]Firewall]  in 1.0850 seconds.
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[Firewall]Firewall]
VERBOSE: [SERVER01]: LCM:  [ End    Set      ]
VERBOSE: [SERVER01]: LCM:  [ End    Set      ]    in  15.2880 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Time taken for configuration job to complete is 15.385 seconds
```

<span data-ttu-id="a91e6-115">Dadurch wird auch sichergestellt, dass der **Firewall**-Block nicht ausgeführt wird, wenn es aus irgendeinem Grund zu einem Fehler mit der **FirewallProfile**-Ressource kommt, obwohl dieser Block zuerst angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="a91e6-115">This also ensures that if the **FirewallProfile** resource fails for any reason, the **Firewall** block will not execute even though it was defined first.</span></span> <span data-ttu-id="a91e6-116">Der `DependsOn`-Schlüssel bietet mehr Flexibilität dabei, Ressourcenblöcke zu gruppieren und dafür zu sorgen, dass Abhängigkeiten aufgelöst werden, bevor eine Ressource ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="a91e6-116">The `DependsOn` key allows more flexibility in grouping resource blocks and ensuring that dependencies are resolved before a Resource executes.</span></span>

<span data-ttu-id="a91e6-117">In komplexeren Konfigurationen können Sie auch [knotenübergreifende Abhängigkeiten](crossNodeDependencies.md) verwenden, um eine noch feiner abgestimmte Kontrolle zu ermöglichen, z. B., um sicherzustellen, dass ein Domänencontroller konfiguriert wird, bevor der Domäne ein Client hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="a91e6-117">In more advanced Configurations, you can also use [Cross Node Dependency](crossNodeDependencies.md) to allow even more granular control (For example, ensuring a domain controller is configured before joining a client to the domain).</span></span>

## <a name="cleaning-up"></a><span data-ttu-id="a91e6-118">Bereinigung</span><span class="sxs-lookup"><span data-stu-id="a91e6-118">Cleaning Up</span></span>

<span data-ttu-id="a91e6-119">Wenn Sie die obige Konfiguration angewendet haben, können Sie Schlüssel umkehren, um Änderungen rückgängig zu machen.</span><span class="sxs-lookup"><span data-stu-id="a91e6-119">If you applied the Configuration above, you can reverse keys to undo any changes.</span></span> <span data-ttu-id="a91e6-120">Im obigen Beispiel wird die Firewallregel und das Firewallprofil deaktiviert, wenn der **Enabled**-Schlüssel (Aktiviert) auf „False“ festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="a91e6-120">In the above example, setting the **Enabled** key to false will disable the firewall rule and profile.</span></span> <span data-ttu-id="a91e6-121">Sie sollten das Beispiel Ihren Bedürfnissen anpassen, damit es mit dem zuvor konfigurierten Zustand Ihres Zielknotens übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="a91e6-121">You should modify the example as needed to match your target Node's previous configured state.</span></span>

```powershell
        Firewall Firewall
        {
            Name                  = 'IIS-WebServerRole-HTTP-In-TCP'
            Enabled               = 'False'
            DependsOn             = '[FirewallProfile]FirewallProfilePublic'
        }

        FirewallProfile FirewallProfilePublic
        {
            Name = 'Public'
            Enabled = 'False'
        }
```

## <a name="see-also"></a><span data-ttu-id="a91e6-122">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a91e6-122">See also</span></span>

- [<span data-ttu-id="a91e6-123">Use Cross Node Dependencies (Verwenden knotenübergreifender Abhängigkeiten)</span><span class="sxs-lookup"><span data-stu-id="a91e6-123">Use Cross Node Dependencies</span></span>](./crossNodeDependencies.md)
