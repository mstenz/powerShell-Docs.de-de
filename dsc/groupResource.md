---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC-Ressource „Group“"
ms.openlocfilehash: 6fb6c5f9593687d7204ff31fddd9bca978ed2707
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="dsc-group-resource" class="xliff"></a>
# DSC-Ressource „Group“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource „Group“ in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten lokaler Gruppen auf dem Zielknoten.

<a id="syntax" class="xliff"></a>
## Syntax
```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

<a id="properties" class="xliff"></a>
## Eigenschaften

|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| GroupName| Der Name der Gruppe, für die Sie einen bestimmten Zustand sicherstellen möchten.| 
| Credential| Die Anmeldeinformationen für den Zugriff auf Remoteressourcen. **Hinweis**: Dieses Konto muss die entsprechenden Active Directory-Berechtigungen aufweisen, um alle nicht lokalen Konten zur Gruppe hinzuzufügen. Andernfalls tritt ein Fehler auf, wenn die Konfiguration auf dem Zielknoten ausgeführt wird.  
| Beschreibung| Die Beschreibung der Gruppe.| 
| Ensure| Gibt an, ob die Gruppe vorhanden ist. Legen Sie diese Eigenschaft auf „Absent“ fest, um sicherzustellen, dass die Gruppe nicht vorhanden ist. Das Festlegen auf „Present“ (den Standardwert) stellt sicher, dass die Gruppe vorhanden ist.| 
| Mitglieder| Verwenden Sie diese Eigenschaft, um die aktuelle Gruppenmitgliedschaft durch die angegebenen Member zu ersetzen. Der Wert dieser Eigenschaft ist ein Zeichenfolgenarray im Format *Domäne*\\*Benutzername*. Wenn Sie diese Eigenschaft in einer Konfiguration festlegen, verwenden Sie weder die Eigenschaft **MembersToExclude** noch die Eigenschaft **MembersToInclude**. Andernfalls kommt es zu einem Fehler.| 
| MembersToExclude| Verwenden Sie diese Eigenschaft, um Member aus der vorhandenen Gruppenmitgliedschaft zu entfernen. Der Wert dieser Eigenschaft ist ein Zeichenfolgenarray im Format *Domäne*\\*Benutzername*. Wenn Sie diese Eigenschaft in einer Konfiguration festgelegt haben, verwenden Sie die Eigenschaft **Members** nicht. Andernfalls kommt es zu einem Fehler.| 
| MembersToInclude| Verwenden Sie diese Eigenschaft, um Member zur vorhandenen Gruppenmitgliedschaft hinzuzufügen. Der Wert dieser Eigenschaft ist ein Zeichenfolgenarray im Format *Domäne*\\*Benutzername*. Wenn Sie diese Eigenschaft in einer Konfiguration festgelegt haben, verwenden Sie die Eigenschaft **Members** nicht. Andernfalls wird ein Fehler generiert.| 
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft „DependsOn = „[ResourceType]ResourceName“.| 

<a id="example-1" class="xliff"></a>
## Beispiel 1

Im folgenden Beispiel wird veranschaulicht, wie sichergestellt wird, dass eine Gruppe namens „TestGroup“ nicht vorhanden ist. 

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
<a id="example-2" class="xliff"></a>
## Beispiel 2
Im folgenden Beispiel wird veranschaulicht, wie Sie einen Active Directory-Benutzer der lokalen Administratorengruppe als Teil eines Testbuilds für mehrere Computer hinzufügen, bei dem Sie bereits PS-Anmeldeinformationen (PSCredential) für das Konto „Lokaler Administrator“ verwenden. Da diese auch für das Domänenadministratorkonto (nach der Domänenhöherstufung) verwendet werden, müssen wir diese vorhandenen PSCredential dann in domänenkompatible Anmeldeinformationen konvertieren, um es uns zu ermöglichen, der Gruppe „Lokale Administratoren“ auf dem Mitgliedsserver einen Domänenbenutzer hinzuzufügen.

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
     @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'   
      }    
    )
}
                  
$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup
        {
            GroupName='Administrators'   
            Ensure= 'Present'             
            MembersToInclude= "$domain\$($Node.AdminAccount)"
            Credential = $dCredential    
            PsDscRunAsCredential = $DCredential
        }
```

<a id="example-3" class="xliff"></a>
## Beispiel 3
Das folgende Beispiel zeigt, wie sichergestellt wird, dass die lokale Gruppe „TigerTeamAdmins“ auf dem Server „TigerTeamSource.Contoso.Com“ ein bestimmtes Domänenkonto, „Contoso\JerryG“, nicht enthält.  

```powershell

Configuration SecureTigerTeamSrouce 
{
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'
  
  Node TigerTeamSource.Contoso.Com {
  Group TigerTeamAdmins
    {
       GroupName        = 'TigerTeamAdmins'   
       Ensure           = 'Absent'             
       MembersToInclude = "Contoso\JerryG"
    }
  }
}
```

