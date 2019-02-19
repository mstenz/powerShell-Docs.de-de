---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Optionen für Anmeldeinformationen in den Konfigurationsdaten
ms.openlocfilehash: 2a326e45bbbad7bd2362b66b88bf61b98df7b02e
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/18/2019
ms.locfileid: "55678550"
---
# <a name="credentials-options-in-configuration-data"></a>Optionen für Anmeldeinformationen in den Konfigurationsdaten

>Gilt für: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Nur-Text-Kennwörter und Domänenbenutzer

DSC-Konfigurationen mit unverschlüsselten Anmeldeinformationen generieren eine Fehlermeldung zu Nur-Text-Kennwörtern.
DSC generiert außerdem bei Verwendung von Domänenanmeldeinformationen eine Warnung.
Um diese Fehler- und Warnmeldungen zu unterdrücken, verwenden Sie die DSC-Konfigurationsdaten-Schlüsselwörter.

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> Das Speichern/Übertragen von unverschlüsselten Nur-Text-Kennwörtern ist in der Regel nicht sicher. Das Sichern von Anmeldeinformationen mithilfe der weiter unten in diesem Thema behandelten Verfahren wird empfohlen.
> Der Azure Automation DSC-Dienst erlaubt Ihnen, Ihre Anmeldeinformationen zentral zu verwalten, um sie in Konfigurationen zu kompilieren und sicher zu speichern.
> Informationen finden Sie unter: [Compiling DSC Configurations / Credential Assets (Kompilieren von DSC-Konfigurationen/Anmeldeinformationsassets)](/azure/automation/automation-dsc-compile#credential-assets)

## <a name="handling-credentials-in-dsc"></a>Behandeln von Anmeldeinformationen in DSC

DSC-Konfigurationsressourcen werden standardmäßig als `Local System` ausgeführt.
Einige Ressourcen benötigen jedoch Anmeldeinformationen, z. B. wenn die `Package`-Ressource Software unter einem bestimmten Benutzerkonto installieren muss.

Frühere Ressourcen verwendeten in diesem Fall einen hartcodierten `Credential`-Eigenschaftennamen.
In WMF 5.0 wurde eine automatische `PsDscRunAsCredential`-Eigenschaft für alle Ressourcen hinzugefügt.
Weitere Informationen zur Verwendung von `PsDscRunAsCredential`, finden Sie unter [Ausführen von DSC mit Benutzeranmeldeinformationen](runAsUser.md).
Neuere und benutzerdefinierte Ressourcen können diese automatische Eigenschaft verwenden, anstatt eine eigene Eigenschaften für Anmeldeinformationen zu erstellen.

> [!NOTE]
> Das Design einiger Ressourcen wurde so angelegt, dass sie aus einem bestimmten Grund mehrere Sätze von Anmeldeinformationen verwenden und über eigene Eigenschaften für Anmeldeinformationen verfügen.

Um die verfügbaren Eigenschaften für Anmeldeinformationen für eine Ressource zu finden, verwenden Sie entweder `Get-DscResource -Name ResourceName -Syntax` oder Intellisense in der ISE (`CTRL+SPACE`).

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

In diesem Beispiel wird eine [Group](../resources/resources.md)-Ressource aus dem integrierten DSC-Ressourcenmodul `PSDesiredStateConfiguration` verwendet.
Damit können lokale Gruppen erstellt oder Member hinzugefügt bzw. entfernt werden.
Es wird sowohl die Eigenschaft `Credential` als auch die automatische Eigenschaft `PsDscRunAsCredential` akzeptiert.
Allerdings verwendet die Ressource nur die Eigenschaft `Credential`.

Weitere Informationen über die Eigenschaft `PsDscRunAsCredential` finden Sie unter [Ausführen von DSC mit Benutzeranmeldeinformationen](runAsUser.md).

## <a name="example-the-group-resource-credential-property"></a>Beispiel: Die Eigenschaft „Credential“ der Ressource „Group“

Der DSC-Dienst wird unter `Local System` ausgeführt, sodass er bereits über Berechtigungen zum Ändern lokaler Benutzer und Gruppen verfügt.
Wenn es sich bei dem hinzugefügten Member um ein lokales Konto handelt, sind keine Anmeldeinformationen erforderlich.
Wenn die Ressource `Group` ein Domänenkonto zur lokalen Gruppe hinzufügt, sind Anmeldeinformationen erforderlich.

Anonyme Abfragen an Active Directory sind nicht zulässig.
Die Eigenschaft `Credential` der Ressource `Group`ist das zum Abfragen von Active Directory verwendete Domänenkonto.
In den meisten Fällen könnte es sich dabei um ein allgemeines Benutzerkonto handeln, da Benutzer standardmäßig über *Lesezugriff* auf die meisten Objekte in Active Directory verfügen.

## <a name="example-configuration"></a>Beispielkonfiguration

Der folgende Beispielcode verwendet DSC zum Auffüllen einer lokalen Gruppen mit einem Domänenbenutzer:

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

Dieser Code generiert eine Fehler- und eine Warnmeldung:

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing property 'Credential' OF
TYPE 'Group': Converting and storing encrypted passwords as plain text is not recommended.
For more information on securing credentials in MOF file, please refer to MSDN blog:
https://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:341 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance
WARNING: It is not recommended to use domain credential for node 'localhost'. In order to suppress
the warning, you can add a property named 'PSDscAllowDomainUser' with a value of $true to your DSC
configuration data for node 'localhost'.

Compilation errors occurred while processing configuration
'DomainCredentialExample'. Please review the errors reported in error stream and modify your
configuration code appropriately.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3917 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (DomainCredentialExample:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```

In diesem Beispiel gibt es zwei Probleme:

1. Ein Fehler zeigt an, dass Nur-Text-Kennwörter nicht empfohlen werden.
2. Eine Warnung rät davon ab, Domänenanmeldeinformationen zu verwenden.

Die Flags **PSDSCAllowPlainTextPassword** und **PSDSCAllowDomainUser** Unterdrücken der Fehler und Warnungen, die den Benutzer das Risiko zu informieren.

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

Die erste Fehlermeldung enthält eine URL zur Dokumentation.
Unter diesem Link wird erläutert, wie Kennwörtern mit einer [ConfigurationData](./configData.md)-Struktur und einem Zertifikat verschlüsselt werden.
Weitere Informationen zu Zertifikaten und DSC [erhalten Sie in diesen Beitrag](http://aka.ms/certs4dsc).

Um ein Nur-Text-Kennwort zu erzwingen, muss im Konfigurationsdatenabschnitt der Ressource das Schlüsselwort `PsDscAllowPlainTextPassword` wie folgt enthalten sein:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
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

DomainCredentialExample -ConfigurationData $cd
```

### <a name="localhostmof"></a>localhost.mof

Die **PSDSCAllowPlainTextPassword** Flag ist erforderlich, dass der Benutzer das Risiko der Speicherung von nur-Text-Kennwörtern in einer MOF-Datei bestätigen. In der generierten MOF-Datei Obwohl ein **PSCredential** Objekt mit einer **SecureString** verwendet wurde, werden die Kennwörter werden weiterhin angezeigt, als nur-Text. Dies ist nur dann, die die Anmeldeinformationen verfügbar gemacht werden. Erhalten Zugriff auf diese MOF-Datei gibt, die allen Benutzern Zugriff auf das Administratorkonto an.

```
/*
@TargetNode='localhost'
@GeneratedBy=Administrator
@GenerationDate=01/31/2019 06:43:13
@GenerationHost=Server01
*/

instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsAPlaintextPassword";
 UserName = "Administrator";

};

instance of MSFT_GroupResource as $MSFT_GroupResource1ref
{
ResourceID = "[Group]DomainUserToLocalGroup";
 MembersToInclude = {
    "contoso\\alice"
};
 Credential = $MSFT_Credential1ref;
 SourceInfo = "::11::9::Group";
 GroupName = "ApplicationAdmins";
 ModuleName = "PSDesiredStateConfiguration";

ModuleVersion = "1.0";

 ConfigurationName = "DomainCredentialExample";

};
```

### <a name="credentials-in-transit-and-at-rest"></a>Anmeldeinformationen, die während der Übertragung und im Ruhezustand

- Die **PSDscAllowPlainTextPassword** Flag ermöglicht, dass die Kompilierung von MOF-Dateien, die Kennwörter in Klartext enthalten.
  Vorsichtsmaßnahmen Sie beim Speichern der MOF-Dateien, die Kennwörter in Klartext enthält.
- Wann ist die MOF-Datei mit einem Knoten im übermittelt **Push** Modus WinRM verschlüsselt die Kommunikation, um die Klartext-Kennwort zu schützen, es sei denn, Sie den Standardwert außer Kraft setzen der **AllowUnencrypted** Parameter.
  - Verschlüsseln die MOF-Datei mit einem Zertifikat schützt die MOF-Datei im Ruhezustand, bevor es zu einem Knoten angewendet wurde.
- In **Pull** -Modus können Sie Windows-Pull-Server zur Verwendung von HTTPS zum Verschlüsseln des Datenverkehrs über das Protokoll angegeben, die in Internet Information Server konfigurieren. Weitere Informationen finden Sie in den Artikeln [zum Einrichten eines DSC-pullclients](../pull-server/pullclient.md) und [Sichern von MOF-Dateien mit Zertifikaten](../pull-server/secureMOF.md).
  - In der [Zustands für Azure Automation](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) service, Pull, Datenverkehr wird immer verschlüsselt.
- MOF-Dateien sind auf dem Knoten und im Ruhezustand verschlüsselt in PowerShell 5.0 ab.
  - In PowerShell 4.0 MOF sind Dateien unverschlüsselt im Ruhezustand, es sei denn, sie mit einem Zertifikat verschlüsselt sind, wenn sie mithilfe von Push übertragen oder auf den Knoten abgerufen.

**Microsoft empfiehlt, Nur-Text-Kennwörter aufgrund des hohen Sicherheitsrisikos zu vermeiden.**

## <a name="domain-credentials"></a>Domänenanmeldeinformationen

Wenn Sie das Beispielkonfigurationsskript erneut ausführen (mit oder ohne Verschlüsselung), wird weiterhin die Warnung generiert, dass die Verwendung von Anmeldeinformationen eines Domänenkontos nicht empfohlen wird.
Durch Verwendung eines lokalen Kontos wird verhindert, dass Domänenanmeldeinformationen, die auf anderen Servern verwendet werden könnten, offengelegt werden.

**Bei Verwendung von Anmeldeinformationen mit DSC-Ressourcen ziehen Sie, wenn möglich, ein lokales Konto einem Domänenkonto vor.**

Enthält die `Username`-Eigenschaft der Anmeldeinformationen die Zeichen „\\“ oder „\@“, behandelt DSC das Konto als Domänenkonto.
Ausnahmen machen „Localhost“, „127.0.0.1“ und „:: 1“ im Domänenteil des Benutzernamens.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

Im oben stehenden Beispiel zur DSC-Ressourcen `Group` ist zum Abfragen einer Active Directory-Domäne ein Domänenkonto *erforderlich*.
Fügen Sie in diesem Fall die Eigenschaft `PSDscAllowDomainUser` wie folgt zum Block `ConfigurationData` hinzu:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

Nun generiert das Konfigurationsskript die MOF-Datei ohne Fehler oder Warnungen.
