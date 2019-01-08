---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Optionen für Anmeldeinformationen in den Konfigurationsdaten
ms.openlocfilehash: 10cf3456fcc7104b7dd779db30aebace54ba087a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046640"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="5e2fc-103">Optionen für Anmeldeinformationen in den Konfigurationsdaten</span><span class="sxs-lookup"><span data-stu-id="5e2fc-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="5e2fc-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5e2fc-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="5e2fc-105">Nur-Text-Kennwörter und Domänenbenutzer</span><span class="sxs-lookup"><span data-stu-id="5e2fc-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="5e2fc-106">DSC-Konfigurationen mit unverschlüsselten Anmeldeinformationen generieren eine Fehlermeldung zu Nur-Text-Kennwörtern.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="5e2fc-107">DSC generiert außerdem bei Verwendung von Domänenanmeldeinformationen eine Warnung.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="5e2fc-108">Um diese Fehler- und Warnmeldungen zu unterdrücken, verwenden Sie die DSC-Konfigurationsdaten-Schlüsselwörter.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="5e2fc-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="5e2fc-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="5e2fc-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="5e2fc-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="5e2fc-111">Das Speichern/Übertragen von unverschlüsselten Nur-Text-Kennwörtern ist in der Regel nicht sicher.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="5e2fc-112">Das Sichern von Anmeldeinformationen mithilfe der weiter unten in diesem Thema behandelten Verfahren wird empfohlen.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="5e2fc-113">Der Azure Automation DSC-Dienst erlaubt Ihnen, Ihre Anmeldeinformationen zentral zu verwalten, um sie in Konfigurationen zu kompilieren und sicher zu speichern.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="5e2fc-114">Weitere Informationen finden Sie unter: [Kompilieren von DSC-Konfigurationen / Anmeldeinformationsobjekte](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="5e2fc-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

<span data-ttu-id="5e2fc-115">Im Folgenden finden ein Beispiel für die Weitergabe von Nur-Text-Anmeldeinformationen:</span><span class="sxs-lookup"><span data-stu-id="5e2fc-115">The following is an example of passing plain text credentials:</span></span>

```powershell
#Prompt user for their credentials
#credentials will be unencrypted in the MOF
$promptedCreds = get-credential -Message "Please enter your credentials to generate a DSC MOF:"

# Store passwords in plaintext, in the document itself
# will also be stored in plaintext in the mof
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "User1"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

# DSC requires explicit confirmation before storing passwords insecurely
$ConfigurationData = @{
    AllNodes = @(
            @{
                # The "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
                NodeName="*"
                PSDscAllowPlainTextPassword = $true
            },
            #however, each node still needs to be explicitly defined for "*" to have meaning
            @{
                NodeName = "TestMachine1"
            },
            #we can also use a property to define node-specific passwords, although this is no more secure
            @{
                NodeName = "TestMachine2";
                UserName = "User2"
                LocalPassword = "ThisIsYetAnotherPlaintextPassword"
            }
        )
}

configuration unencryptedPasswordDemo
{
    Node "TestMachine1"
    {
        # We use the plaintext password to generate a new account
        User User1
        {
            UserName = $username
            Password = $credential
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }
        # We use the prompted password to add this account to the local admins group
        Group addToAdmin
        {
            # Ensure the user exists before we add the user to a group
            DependsOn = "[User]User1"
            Credential = $promptedCreds
            GroupName = "Administrators"
            Ensure = "Present"
            MembersToInclude = "User1"
        }
    }

    Node "TestMachine2"
    {
        # Now we'll use a node-specific password to this machine
        $password = $Node.LocalPassword | ConvertTo-SecureString -asPlainText -Force
        $username = $node.UserName
        [PSCredential] $nodeCred = New-Object System.Management.Automation.PSCredential($username,$password)

        User User2
        {
            UserName = $username
            Password = $nodeCred
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }

        Group addToAdmin
        {
            Credential = $promptedCreds
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }
}

# We declared the ConfigurationData in a local variable, but we need to pass it
# in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData

# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

<span data-ttu-id="5e2fc-116">Dies ist ein Auszug aus der "MOF"-Datei, die von der Konfiguration für "TestMachine1" generiert.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-116">This is an excerpt from the ".mof" file generated by the configuration for "TestMachine1".</span></span> <span data-ttu-id="5e2fc-117">Die `System.Security.SecureString` in verwendet die Konfiguration wurde in nur-Text konvertiert und gespeichert, in der Datei "MOF" als eine `MSF_Credential`.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-117">The `System.Security.SecureString` used in the configuration was converted to plain text and stored in the ".mof" file as a `MSF_Credential`.</span></span> <span data-ttu-id="5e2fc-118">Ein `SecureString` ist mit dem aktuellen Benutzerprofil verschlüsselt.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-118">A `SecureString` is encrypted with the current users profile.</span></span> <span data-ttu-id="5e2fc-119">Dies funktioniert gut mit allen Formen der PowerShell-Remoteverwaltung.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-119">This works well with all forms of PowerShell remote management.</span></span> <span data-ttu-id="5e2fc-120">Eine "MOF"-Datei fungiert als ein eigenständigen allein-Konfigurationsverfahren.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-120">A ".mof" file is designed to be a stand alone configuration mechanism.</span></span> <span data-ttu-id="5e2fc-121">Ab in PowerShell 5.0 ist werden "MOF"-Dateien auf einem Knoten verschlüsselt, im Ruhezustand, aber nicht in der Übertragung an den Knoten.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-121">Beginning in PowerShell 5.0, ".mof" files on a Node are encrypted at rest, but not in transit to the Node.</span></span> <span data-ttu-id="5e2fc-122">Dies bedeutet, dass Kennwörter in einem "MOF"-Datei als Klartext verfügbar gemacht werden, wenn Sie diese auf einen Knoten anwenden.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-122">This means that passwords in a ".mof" file are exposed as clear text when you apply them to a Node.</span></span> <span data-ttu-id="5e2fc-123">Um Anmeldeinformationen zu verschlüsseln, müssen Sie eine **Pull-Server**.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-123">To encrypt credentials, you need to use a **Pull Server**.</span></span> <span data-ttu-id="5e2fc-124">Weitere Informationen finden Sie unter [Sichern von MOF-Dateien mit Zertifikaten](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="5e2fc-124">For more information, see [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>

```syntax
instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsYetAnotherPlaintextPassword";
 UserName = "User2";

};

instance of MSFT_UserResource as $MSFT_UserResource1ref
{
ResourceID = "[User]User2";
 Description = "local account";
 UserName = "User2";
 Ensure = "Present";
 Password = $MSFT_Credential1ref;
 Disabled = False;
 SourceInfo = "::66::9::User";
 PasswordNeverExpires = True;
 ModuleName = "PsDesiredStateConfiguration";
 PasswordChangeRequired = False;

ModuleVersion = "1.0";

 ConfigurationName = "unencryptedPasswordDemo";

};
```

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="5e2fc-125">Behandeln von Anmeldeinformationen in DSC</span><span class="sxs-lookup"><span data-stu-id="5e2fc-125">Handling Credentials in DSC</span></span>

<span data-ttu-id="5e2fc-126">DSC-Konfigurationsressourcen werden standardmäßig als `Local System` ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-126">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="5e2fc-127">Einige Ressourcen benötigen jedoch Anmeldeinformationen, z. B. wenn die `Package`-Ressource Software unter einem bestimmten Benutzerkonto installieren muss.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-127">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="5e2fc-128">Frühere Ressourcen verwendeten in diesem Fall einen hartcodierten `Credential`-Eigenschaftennamen.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-128">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="5e2fc-129">In WMF 5.0 wurde eine automatische `PsDscRunAsCredential`-Eigenschaft für alle Ressourcen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-129">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="5e2fc-130">Weitere Informationen zur Verwendung von `PsDscRunAsCredential`, finden Sie unter [Ausführen von DSC mit Benutzeranmeldeinformationen](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="5e2fc-130">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="5e2fc-131">Neuere und benutzerdefinierte Ressourcen können diese automatische Eigenschaft verwenden, anstatt eine eigene Eigenschaften für Anmeldeinformationen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-131">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="5e2fc-132">Das Design einiger Ressourcen wurde so angelegt, dass sie aus einem bestimmten Grund mehrere Sätze von Anmeldeinformationen verwenden und über eigene Eigenschaften für Anmeldeinformationen verfügen.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-132">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="5e2fc-133">Um die verfügbaren Eigenschaften für Anmeldeinformationen für eine Ressource zu finden, verwenden Sie entweder `Get-DscResource -Name ResourceName -Syntax` oder Intellisense in der ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="5e2fc-133">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

```powershell
PS C:\> Get-DscResource -Name Group -Syntax
Group [String] #ResourceName
{
    GroupName = [string]
    [Credential = [PSCredential]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Members = [string[]]]
    [MembersToExclude = [string[]]]
    [MembersToInclude = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="5e2fc-134">In diesem Beispiel wird eine [Group](../resources/resources.md)-Ressource aus dem integrierten DSC-Ressourcenmodul `PSDesiredStateConfiguration` verwendet.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-134">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="5e2fc-135">Damit können lokale Gruppen erstellt oder Member hinzugefügt bzw. entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-135">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="5e2fc-136">Es wird sowohl die Eigenschaft `Credential` als auch die automatische Eigenschaft `PsDscRunAsCredential` akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-136">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="5e2fc-137">Allerdings verwendet die Ressource nur die Eigenschaft `Credential`.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-137">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="5e2fc-138">Weitere Informationen über die Eigenschaft `PsDscRunAsCredential` finden Sie unter [Ausführen von DSC mit Benutzeranmeldeinformationen](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="5e2fc-138">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="5e2fc-139">Beispiel: Die Ressource "Group" Credential-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="5e2fc-139">Example: The Group resource Credential property</span></span>

<span data-ttu-id="5e2fc-140">Der DSC-Dienst wird unter `Local System` ausgeführt, sodass er bereits über Berechtigungen zum Ändern lokaler Benutzer und Gruppen verfügt.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-140">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="5e2fc-141">Wenn es sich bei dem hinzugefügten Member um ein lokales Konto handelt, sind keine Anmeldeinformationen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-141">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="5e2fc-142">Wenn die Ressource `Group` ein Domänenkonto zur lokalen Gruppe hinzufügt, sind Anmeldeinformationen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-142">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="5e2fc-143">Anonyme Abfragen an Active Directory sind nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-143">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="5e2fc-144">Die Eigenschaft `Credential` der Ressource `Group`ist das zum Abfragen von Active Directory verwendete Domänenkonto.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-144">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="5e2fc-145">In den meisten Fällen könnte es sich dabei um ein allgemeines Benutzerkonto handeln, da Benutzer standardmäßig über *Lesezugriff* auf die meisten Objekte in Active Directory verfügen.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-145">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="5e2fc-146">Beispielkonfiguration</span><span class="sxs-lookup"><span data-stu-id="5e2fc-146">Example Configuration</span></span>

<span data-ttu-id="5e2fc-147">Der folgende Beispielcode verwendet DSC zum Auffüllen einer lokalen Gruppen mit einem Domänenbenutzer:</span><span class="sxs-lookup"><span data-stu-id="5e2fc-147">The following example code uses DSC to populate a local group with a domain user:</span></span>

```powershell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred
```

<span data-ttu-id="5e2fc-148">Dieser Code generiert eine Fehler- und eine Warnmeldung:</span><span class="sxs-lookup"><span data-stu-id="5e2fc-148">This code generates both an error and warning message:</span></span>

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing
property 'Credential' OF TYPE 'Group': Converting and storing encrypted
passwords as plain text is not recommended. For more information on securing
credentials in MOF file, please refer to MSDN blog:
http://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:297 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance

WARNING: It is not recommended to use domain credential for node 'localhost'.
In order to suppress the warning, you can add a property named
'PSDscAllowDomainUser' with a value of $true to your DSC configuration data
for node 'localhost'.
```

<span data-ttu-id="5e2fc-149">In diesem Beispiel gibt es zwei Probleme:</span><span class="sxs-lookup"><span data-stu-id="5e2fc-149">This example has two issues:</span></span>
1. <span data-ttu-id="5e2fc-150">Ein Fehler zeigt an, dass Nur-Text-Kennwörter nicht empfohlen werden.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-150">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="5e2fc-151">Eine Warnung rät davon ab, Domänenanmeldeinformationen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-151">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="5e2fc-152">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="5e2fc-152">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="5e2fc-153">Die erste Fehlermeldung enthält eine URL zur Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-153">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="5e2fc-154">Unter diesem Link wird erläutert, wie Kennwörtern mit einer [ConfigurationData](./configData.md)-Struktur und einem Zertifikat verschlüsselt werden.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-154">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span>
<span data-ttu-id="5e2fc-155">Weitere Informationen zu Zertifikaten und DSC [erhalten Sie in diesen Beitrag](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="5e2fc-155">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="5e2fc-156">Um ein Nur-Text-Kennwort zu erzwingen, muss im Konfigurationsdatenabschnitt der Ressource das Schlüsselwort `PsDscAllowPlainTextPassword` wie folgt enthalten sein:</span><span class="sxs-lookup"><span data-stu-id="5e2fc-156">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

```powershell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred -ConfigurationData $cd
```

> [!NOTE]
> <span data-ttu-id="5e2fc-157">`NodeName` kann kein Sternchen angegeben werden; der Name eines bestimmten Knotens ist obligatorisch.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-157">`NodeName` cannot equal asterisk, a specific node name is mandatory.</span></span>

<span data-ttu-id="5e2fc-158">**Microsoft empfiehlt, Nur-Text-Kennwörter aufgrund des hohen Sicherheitsrisikos zu vermeiden.**</span><span class="sxs-lookup"><span data-stu-id="5e2fc-158">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="5e2fc-159">Domänenanmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="5e2fc-159">Domain Credentials</span></span>

<span data-ttu-id="5e2fc-160">Wenn Sie das Beispielkonfigurationsskript erneut ausführen (mit oder ohne Verschlüsselung), wird weiterhin die Warnung generiert, dass die Verwendung von Anmeldeinformationen eines Domänenkontos nicht empfohlen wird.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-160">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="5e2fc-161">Durch Verwendung eines lokalen Kontos wird verhindert, dass Domänenanmeldeinformationen, die auf anderen Servern verwendet werden könnten, offengelegt werden.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-161">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="5e2fc-162">**Bei Verwendung von Anmeldeinformationen mit DSC-Ressourcen ziehen Sie, wenn möglich, ein lokales Konto einem Domänenkonto vor.**</span><span class="sxs-lookup"><span data-stu-id="5e2fc-162">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="5e2fc-163">Enthält die Eigenschaft `Username` der Anmeldeinformationen einen „\'“ oder ein „@“, behandelt DSC das Konto als Domänenkonto.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-163">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="5e2fc-164">Ausnahmen machen „Localhost“, „127.0.0.1“ und „:: 1“ im Domänenteil des Benutzernamens.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-164">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="5e2fc-165">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="5e2fc-165">PSDscAllowDomainUser</span></span>

<span data-ttu-id="5e2fc-166">Im oben stehenden Beispiel zur DSC-Ressourcen `Group` ist zum Abfragen einer Active Directory-Domäne ein Domänenkonto *erforderlich*.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-166">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="5e2fc-167">Fügen Sie in diesem Fall die Eigenschaft `PSDscAllowDomainUser` wie folgt zum Block `ConfigurationData` hinzu:</span><span class="sxs-lookup"><span data-stu-id="5e2fc-167">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

```powershell
$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            # PSDscAllowPlainTextPassword = $true
            CertificateFile = "C:\PublicKeys\server1.cer"
        }
    )
}
```

<span data-ttu-id="5e2fc-168">Nun generiert das Konfigurationsskript die MOF-Datei ohne Fehler oder Warnungen.</span><span class="sxs-lookup"><span data-stu-id="5e2fc-168">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
