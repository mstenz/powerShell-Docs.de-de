---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "Erstellen eines Domänencontrollers"
ms.technology: powershell
ms.openlocfilehash: 80b957ed666ca626c6083041cf99c263e2e0dc27
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: de-DE
---
### <a name="creating-a-domain-controller"></a><span data-ttu-id="976d8-103">Erstellen eines Domänencontrollers</span><span class="sxs-lookup"><span data-stu-id="976d8-103">Creating a Domain Controller</span></span>

<span data-ttu-id="976d8-104">Im vorliegenden Dokument wird davon ausgegangen, dass Ihr Computer in eine Domäne eingebunden ist.</span><span class="sxs-lookup"><span data-stu-id="976d8-104">This document assumes that your machine is domain joined.</span></span>
<span data-ttu-id="976d8-105">Wenn Sie derzeit nicht über eine Domäne verfügen, in die der Computer eingebunden werden kann, hilft Ihnen dieser Abschnitt dabei, mithilfe von DSC schnell einen Domänencontroller einzurichten.</span><span class="sxs-lookup"><span data-stu-id="976d8-105">If you currently don't have a domain to join, this section can help you quickly stand up a domain controller using DSC.</span></span>

#### <a name="prerequisites"></a><span data-ttu-id="976d8-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="976d8-106">Prerequisites</span></span>

1.  <span data-ttu-id="976d8-107">Der Computer befindet sich in einem internen Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="976d8-107">The machine is on an internal network</span></span>
2.  <span data-ttu-id="976d8-108">Der Computer ist nicht in eine vorhandene Domäne eingebunden.</span><span class="sxs-lookup"><span data-stu-id="976d8-108">The machine is not joined to an existing domain</span></span>
3.  <span data-ttu-id="976d8-109">Auf dem Computer wird Windows Server 2016 ausgeführt, oder es ist WMF 5.0 installiert.</span><span class="sxs-lookup"><span data-stu-id="976d8-109">The machine is running Windows Server 2016 or has WMF 5.0 installed</span></span>

#### <a name="install-xactivedirectory"></a><span data-ttu-id="976d8-110">Installieren von xActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="976d8-110">Install xActiveDirectory</span></span>
<span data-ttu-id="976d8-111">Wenn Ihr Computer über eine aktive Internetverbindung verfügt, führen Sie folgenden Befehl in einem PowerShell-Fenster mit erhöhten Rechten aus:</span><span class="sxs-lookup"><span data-stu-id="976d8-111">If your machine has an active internet connection, run the following command in an elevated PowerShell window:</span></span>
```PowerShell
Install-Module xActiveDirectory -Force
```
<span data-ttu-id="976d8-112">Wenn Sie nicht über eine Internetverbindung verfügen, installieren Sie xActiveDirectory auf einem anderen Computer, und kopieren Sie den xActiveDirectory-Ordner in das Verzeichnis „C:\Programme\WindowsPowerShell\Modules“ auf Ihrem Computer.</span><span class="sxs-lookup"><span data-stu-id="976d8-112">If you do not have an internet connection, install xActiveDirectory to another machine and then copy the xActiveDirectory folder to the "C:\Program Files\WindowsPowerShell\Modules" folder on your machine.</span></span>

<span data-ttu-id="976d8-113">Um zu überprüfen, ob die Installation erfolgreich war, führen Sie folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="976d8-113">To confirm the installation succeeded, run the following command:</span></span>
```PowerShell
Get-Module xActiveDirectory -ListAvailable
```

#### <a name="set-up-a-domain-with-dsc"></a><span data-ttu-id="976d8-114">Einrichten einer Domäne mit DSC</span><span class="sxs-lookup"><span data-stu-id="976d8-114">Set up a domain with DSC</span></span>
<span data-ttu-id="976d8-115">Kopieren Sie das folgende Skript in PowerShell, um Ihren Computer als Domänencontroller in einer neuen Domäne einzurichten.</span><span class="sxs-lookup"><span data-stu-id="976d8-115">Copy the following script in PowerShell to make your machine a Domain Controller in a new domain.</span></span>
<span data-ttu-id="976d8-116">**HINWEIS DES AUTORS: ES GIBT EIN BEKANNTES PROBLEM, DASS DIE BEREITGESTELLTEN ANMELDEINFORMATIONEN NICHT VERWENDET WERDEN.  MERKEN SIE SICH DAHER UNBEDINGT IHR LOKALES ADMINISTRATORKENNWORT.**</span><span class="sxs-lookup"><span data-stu-id="976d8-116">**AUTHOR'S NOTE: THERE IS A KNOWN ISSUE WITH THE CREDENTIALS PROVIDED NOT BEING USED.  TO BE SAFE, DON'T FORGET YOUR LOCAL ADMIN PASSWORD.**</span></span>

```PowerShell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value $env:COMPUTERNAME -Force

# This "MetaConfiguration" sets the DSC Engine to automatically reboot if required
[DscLocalConfigurationManager()]
Configuration MetaConfiguration
{
    Node $env:Computername
    {
        Settings
        {
            RebootNodeIfNeeded = $true
        }
    }

}

MetaConfiguration
# Apply the MetaConfiguration
Set-DscLocalConfigurationManager .\MetaConfiguration

# Configure a domain controller of a new "Contoso" domain
configuration DomainController
{
    param
    (
        $node,
        $cred
    )
    Import-DscResource -ModuleName xActiveDirectory

    Node $node
    {
        WindowsFeature ADDS
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain Contoso
        {
            DomainName = 'contoso.com'
            DomainAdministratorCredential = $cred
            SafemodeAdministratorPassword = $cred
            DependsOn = '[WindowsFeature]ADDS'
        }

        file temp
        {
            DestinationPath = 'C:\temp.txt'
            Contents = 'Domain has been created'
            DependsOn = '[xADDomain]Contoso'
        }
    }
}

$ConfigData = @{
    AllNodes = @(
        @{
            NodeName = $env:Computername
            PSDscAllowPlainTextPassword = $true
        }
    )
}

# Enter your desired password for the domain administrator (note, this will be stored as plain text)
DomainController -cred (Get-Credential -Message "Enter desired credential for domain administrator") -node $env:Computername -configurationData $ConfigData

# Apply the configuration to create the domain controller
Start-DSCConfiguration -path .\DomainController -ComputerName $env:Computername -Wait -Force -Verbose
```
<span data-ttu-id="976d8-117">Ihr Computer wird mehrmals neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="976d8-117">Your machine will restart a few times.</span></span>
<span data-ttu-id="976d8-118">Sobald Sie eine Datei namens „C:\temp.txt“ mit dem Inhalt „Domain has been created.“ sehen, wissen Sie, dass der Vorgang abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="976d8-118">You will know the process is complete once you see a file called "C:\temp.txt" containing "Domain has been created."</span></span>

#### <a name="set-up-users-and-groups"></a><span data-ttu-id="976d8-119">Einrichten von Benutzern und Gruppen</span><span class="sxs-lookup"><span data-stu-id="976d8-119">Set up Users and Groups</span></span>
<span data-ttu-id="976d8-120">Mit den folgenden Befehlen richten Sie eine Gruppe „Helpdesk“ und eine Gruppe „Operator“ sowie jeweils einen entsprechenden Benutzer ohne Administratorrechte in Ihrer Domäne ein, der Mitglied der jeweiligen Gruppe ist.</span><span class="sxs-lookup"><span data-stu-id="976d8-120">The following commands will set up an Operator and Helpdesk group in your domain and a corresponding non-administrator user who is a member of that group.</span></span>
```PowerShell
# Make Groups
$NonAdminOperatorGroup = New-ADGroup -Name "JEA_NonAdmin_Operator" -GroupScope DomainLocal -PassThru
$NonAdminHelpDeskGroup = New-ADGroup -Name "JEA_NonAdmin_HelpDesk" -GroupScope DomainLocal -PassThru
$TestGroup = New-ADGroup -Name "Test_Group" -GroupScope DomainLocal -PassThru

# Make Users
$OperatorUser = New-ADUser -Name "OperatorUser" -AccountPassword (ConvertTo-SecureString 'pa$$w0rd' -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $OperatorUser

$HelpDeskUser = New-ADUser -name "HelpDeskUser" -AccountPassword (ConvertTo-SecureString 'pa$$w0rd' -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $HelpDeskUser

# Add Users to Groups
Add-ADGroupMember -Identity $NonAdminOperatorGroup -Members $OperatorUser
Add-ADGroupMember -Identity $NonAdminHelpDeskGroup -Members $HelpDeskUser
```

