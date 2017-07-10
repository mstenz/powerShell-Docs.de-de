---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC-Ressource „User“"
ms.openlocfilehash: a4e4e8af4fcfe5c997c460613174d8583261dedf
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="dsc-user-resource" class="xliff"></a>
#DSC-Ressource „User“#

 
>Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0


Die Ressource __User__ in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten lokaler Benutzerkonten auf dem Zielknoten.


<a id="syntax" class="xliff"></a>
##Syntax##

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

<a id="properties" class="xliff"></a>
## Eigenschaften
|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| UserName| Gibt den Kontonamen an, für den Sie einen bestimmten Zustand sicherstellen möchten.| 
| Beschreibung| Gibt die Beschreibung an, die Sie für das Benutzerkonto verwenden möchten.| 
| Disabled| Gibt an, ob das Konto aktiviert ist. Legen Sie diese Eigenschaft auf __$true__ fest, um sicherzustellen, dass dieses Konto deaktiviert ist. Legen Sie sie auf __$false__ fest, um sicherzustellen, dass es aktiviert ist.| 
| Ensure| Gibt an, ob das Konto vorhanden ist. Legen Sie diese Eigenschaft auf „Present“ fest, um sicherzustellen, dass das Konto vorhanden ist. Legen Sie sie auf „Absent“ fest, um sicherzustellen, dass das Konto nicht vorhanden ist.| 
| FullName| Stellt eine Zeichenfolge mit dem vollständigen Namen dar, den Sie für das Benutzerkonto verwenden möchten.| 
| Password| Gibt das Kennwort an, das Sie für dieses Konto verwenden möchten. | 
| PasswordChangeNotAllowed| Gibt an, ob der Benutzer das Kennwort ändern kann. Legen Sie diese Eigenschaft auf __$true__ fest, um sicherzustellen, dass der Benutzer das Kennwort nicht ändern kann. Legen Sie es auf __$false__ fest, damit der Benutzer das Kennwort ändern kann. Der Standardwert ist __$false__.| 
| PasswordChangeRequired| Gibt an, ob der Benutzer sein Kennwort bei der nächsten Anmeldung ändern muss. Legen Sie diese Eigenschaft auf __$true__ fest, wenn der Benutzer das Kennwort ändern muss. Der Standardwert ist __$true__.| 
| PasswordNeverExpires| Gibt an, ob das Kennwort abläuft. Um sicherzustellen, dass das Kennwort für dieses Konto nicht abläuft, legen Sie diese Eigenschaft auf __$true__ fest. Legen Sie sie auf __$false__ fest, wenn das Kennwort abläuft. Der Standardwert ist __$false__.| 
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.| 

<a id="example" class="xliff"></a>
## Beispiel

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```

