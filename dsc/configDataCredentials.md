---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Optionen für Anmeldeinformationen in den Konfigurationsdaten"
ms.openlocfilehash: ec4eeb8e519158b2bf929b949e381cdba54f8928
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2017
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="290f9-103">Optionen für Anmeldeinformationen in den Konfigurationsdaten</span><span class="sxs-lookup"><span data-stu-id="290f9-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="290f9-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="290f9-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="290f9-105">Nur-Text-Kennwörter und Domänenbenutzer</span><span class="sxs-lookup"><span data-stu-id="290f9-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="290f9-106">DSC-Konfigurationen mit unverschlüsselten Anmeldeinformationen generieren eine Fehlermeldung zu Nur-Text-Kennwörtern.</span><span class="sxs-lookup"><span data-stu-id="290f9-106">DSC configurations containing a credential without encryption will generate an error messages about plain text passwords.</span></span>
<span data-ttu-id="290f9-107">DSC generiert außerdem bei Verwendung von Domänenanmeldeinformationen eine Warnung.</span><span class="sxs-lookup"><span data-stu-id="290f9-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="290f9-108">Um diese Fehler- und Warnmeldungen zu unterdrücken, verwenden Sie die DSC-Konfigurationsdaten-Schlüsselwörter.</span><span class="sxs-lookup"><span data-stu-id="290f9-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="290f9-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="290f9-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="290f9-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="290f9-110">**PsDscAllowDomainUser**</span></span>

><span data-ttu-id="290f9-111">**Hinweis:** Das Verwenden von Nur-Text-Kennwörter ist nicht sicher.</span><span class="sxs-lookup"><span data-stu-id="290f9-111">**Note:** Using plaintext passwords is not secure.</span></span> <span data-ttu-id="290f9-112">Das Sichern von Anmeldeinformationen mithilfe der weiter unten in diesem Thema behandelten Verfahren wird empfohlen.</span><span class="sxs-lookup"><span data-stu-id="290f9-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>

<span data-ttu-id="290f9-113">Im Folgenden finden ein Beispiel für die Weitergabe von Nur-Text-Anmeldeinformationen:</span><span class="sxs-lookup"><span data-stu-id="290f9-113">The following is an example of passing plain text credentials:</span></span>

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
        $password = $Node.LocalPass | ConvertTo-SecureString -asPlainText -Force
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
            Credential = $domain
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }

}
# We declared the ConfigurationData in a local variable, but we need to pass it in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData
# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="290f9-114">Behandeln von Anmeldeinformationen in DSC</span><span class="sxs-lookup"><span data-stu-id="290f9-114">Handling Credentials in DSC</span></span>

<span data-ttu-id="290f9-115">DSC-Konfigurationsressourcen werden standardmäßig als `Local System` ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="290f9-115">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="290f9-116">Einige Ressourcen benötigen jedoch Anmeldeinformationen, z. B. wenn die `Package`-Ressource Software unter einem bestimmten Benutzerkonto installieren muss.</span><span class="sxs-lookup"><span data-stu-id="290f9-116">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="290f9-117">Frühere Ressourcen verwendeten in diesem Fall einen hartcodierten `Credential`-Eigenschaftennamen.</span><span class="sxs-lookup"><span data-stu-id="290f9-117">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="290f9-118">In WMF 5.0 wurde eine automatische `PsDscRunAsCredential`-Eigenschaft für alle Ressourcen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="290f9-118">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span> <span data-ttu-id="290f9-119">Weitere Informationen zur Verwendung von `PsDscRunAsCredential`, finden Sie unter [Ausführen von DSC mit Benutzeranmeldeinformationen](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="290f9-119">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="290f9-120">Neuere und benutzerdefinierte Ressourcen können diese automatische Eigenschaft verwenden, anstatt eine eigene Eigenschaften für Anmeldeinformationen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="290f9-120">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

<span data-ttu-id="290f9-121">*Beachten Sie, dass einige Ressourcen so angelegt wurden, dass sie aus einem bestimmten Grund mehrere Sätze von Anmeldeinformationen verwenden und über eigene Eigenschaften für Anmeldeinformationen verfügen.*</span><span class="sxs-lookup"><span data-stu-id="290f9-121">*Note that the design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.*</span></span>

<span data-ttu-id="290f9-122">Um die verfügbaren Eigenschaften für Anmeldeinformationen für eine Ressource zu finden, verwenden Sie entweder `Get-DscResource -Name ResourceName -Syntax` oder Intellisense in der ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="290f9-122">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="290f9-123">In diesem Beispiel wird eine [Group](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource)-Ressource aus dem integrierten DSC-Ressourcenmodul `PSDesiredStateConfiguration` verwendet.</span><span class="sxs-lookup"><span data-stu-id="290f9-123">This example uses a [Group](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="290f9-124">Damit können lokale Gruppen erstellt oder Member hinzugefügt bzw. entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="290f9-124">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="290f9-125">Es wird sowohl die Eigenschaft `Credential` als auch die automatische Eigenschaft `PsDscRunAsCredential` akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="290f9-125">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="290f9-126">Allerdings verwendet die Ressource nur die Eigenschaft `Credential`.</span><span class="sxs-lookup"><span data-stu-id="290f9-126">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="290f9-127">Weitere Informationen über die Eigenschaft `PsDscRunAsCredential` finden Sie unter [Ausführen von DSC mit Benutzeranmeldeinformationen](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="290f9-127">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="290f9-128">Beispiel: Die Eigenschaft „Credential“ der Ressource „Group“</span><span class="sxs-lookup"><span data-stu-id="290f9-128">Example: The Group resource Credential property</span></span>

<span data-ttu-id="290f9-129">Der DSC-Dienst wird unter `Local System` ausgeführt, sodass er bereits über Berechtigungen zum Ändern lokaler Benutzer und Gruppen verfügt.</span><span class="sxs-lookup"><span data-stu-id="290f9-129">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="290f9-130">Wenn es sich bei dem hinzugefügten Member um ein lokales Konto handelt, sind keine Anmeldeinformationen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="290f9-130">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="290f9-131">Wenn die Ressource `Group` ein Domänenkonto zur lokalen Gruppe hinzufügt, sind Anmeldeinformationen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="290f9-131">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="290f9-132">Anonyme Abfragen an Active Directory sind nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="290f9-132">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="290f9-133">Die Eigenschaft `Credential` der Ressource `Group`ist das zum Abfragen von Active Directory verwendete Domänenkonto.</span><span class="sxs-lookup"><span data-stu-id="290f9-133">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="290f9-134">In den meisten Fällen könnte es sich dabei um ein allgemeines Benutzerkonto handeln, da Benutzer standardmäßig über *Lesezugriff* auf die meisten Objekte in Active Directory verfügen.</span><span class="sxs-lookup"><span data-stu-id="290f9-134">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="290f9-135">Beispielkonfiguration</span><span class="sxs-lookup"><span data-stu-id="290f9-135">Example Configuration</span></span>

<span data-ttu-id="290f9-136">Der folgende Beispielcode verwendet DSC zum Auffüllen einer lokalen Gruppen mit einem Domänenbenutzer:</span><span class="sxs-lookup"><span data-stu-id="290f9-136">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="290f9-137">Dieser Code generiert eine Fehler- und eine Warnmeldung:</span><span class="sxs-lookup"><span data-stu-id="290f9-137">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="290f9-138">In diesem Beispiel gibt es zwei Probleme:</span><span class="sxs-lookup"><span data-stu-id="290f9-138">This example has two issues:</span></span>
1.  <span data-ttu-id="290f9-139">Ein Fehler zeigt an, dass Nur-Text-Kennwörter nicht empfohlen werden.</span><span class="sxs-lookup"><span data-stu-id="290f9-139">An error explains that plain text passwords are not recommended</span></span>
2.  <span data-ttu-id="290f9-140">Eine Warnung rät davon ab, Domänenanmeldeinformationen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="290f9-140">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="290f9-141">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="290f9-141">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="290f9-142">Die erste Fehlermeldung enthält eine URL zur Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="290f9-142">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="290f9-143">Unter diesem Link wird erläutert, wie Kennwörtern mit einer [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata)-Struktur und einem Zertifikat verschlüsselt werden.</span><span class="sxs-lookup"><span data-stu-id="290f9-143">This link explains how to encrypt passwords using a [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) structure and a certificate.</span></span>
<span data-ttu-id="290f9-144">Weitere Informationen zu Zertifikaten und DSC [erhalten Sie in diesen Beitrag](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="290f9-144">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="290f9-145">Um ein Nur-Text-Kennwort zu erzwingen, muss im Konfigurationsdatenabschnitt der Ressource das Schlüsselwort `PsDscAllowPlainTextPassword` wie folgt enthalten sein:</span><span class="sxs-lookup"><span data-stu-id="290f9-145">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

<span data-ttu-id="290f9-146">*Beachten Sie, dass für `NodeName` kein Sternchen angegeben werden darf, sondern der Name eines bestimmten Knotens obligatorisch ist.*</span><span class="sxs-lookup"><span data-stu-id="290f9-146">*Note that `NodeName` cannot equal asterisk, a specific node name is mandatory.*</span></span>

<span data-ttu-id="290f9-147">**Microsoft empfiehlt, Nur-Text-Kennwörter aufgrund des hohen Sicherheitsrisikos zu vermeiden.**</span><span class="sxs-lookup"><span data-stu-id="290f9-147">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="290f9-148">Domänenanmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="290f9-148">Domain Credentials</span></span>

<span data-ttu-id="290f9-149">Wenn Sie das Beispielkonfigurationsskript erneut ausführen (mit oder ohne Verschlüsselung), wird weiterhin die Warnung generiert, dass die Verwendung von Anmeldeinformationen eines Domänenkontos nicht empfohlen wird.</span><span class="sxs-lookup"><span data-stu-id="290f9-149">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="290f9-150">Durch Verwendung eines lokalen Kontos wird verhindert, dass Domänenanmeldeinformationen, die auf anderen Servern verwendet werden könnten, offengelegt werden.</span><span class="sxs-lookup"><span data-stu-id="290f9-150">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="290f9-151">**Bei Verwendung von Anmeldeinformationen mit DSC-Ressourcen ziehen Sie, wenn möglich, ein lokales Konto einem Domänenkonto vor.**</span><span class="sxs-lookup"><span data-stu-id="290f9-151">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="290f9-152">Enthält die Eigenschaft `Username` der Anmeldeinformationen einen „\'“ oder ein „@“, behandelt DSC das Konto als Domänenkonto.</span><span class="sxs-lookup"><span data-stu-id="290f9-152">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="290f9-153">Ausnahmen machen „Localhost“, „127.0.0.1“ und „:: 1“ im Domänenteil des Benutzernamens.</span><span class="sxs-lookup"><span data-stu-id="290f9-153">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="290f9-154">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="290f9-154">PSDscAllowDomainUser</span></span>

<span data-ttu-id="290f9-155">Im oben stehenden Beispiel zur DSC-Ressourcen `Group` ist zum Abfragen einer Active Directory-Domäne ein Domänenkonto *erforderlich*.</span><span class="sxs-lookup"><span data-stu-id="290f9-155">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="290f9-156">Fügen Sie in diesem Fall die Eigenschaft `PSDscAllowDomainUser` wie folgt zum Block `ConfigurationData` hinzu:</span><span class="sxs-lookup"><span data-stu-id="290f9-156">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="290f9-157">Nun generiert das Konfigurationsskript die MOF-Datei ohne Fehler oder Warnungen.</span><span class="sxs-lookup"><span data-stu-id="290f9-157">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>

