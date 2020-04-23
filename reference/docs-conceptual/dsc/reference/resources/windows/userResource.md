---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC-Ressource „User“
ms.openlocfilehash: dec432c2ff1b4e4408165fef391e77cbf1d85ac4
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953007"
---
# <a name="dsc-user-resource"></a>DSC-Ressource „User“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.x

Die Ressource **User** in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten lokaler Benutzerkonten auf dem Zielknoten.

## <a name="syntax"></a>Syntax

```Syntax
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschaften

|Eigenschaft |BESCHREIBUNG |
|---|---|
|UserName |Gibt den Kontonamen an, für den Sie einen bestimmten Zustand sicherstellen möchten. |
|BESCHREIBUNG |Gibt die Beschreibung an, die Sie für das Benutzerkonto verwenden möchten. |
|Disabled |Gibt an, ob das Konto aktiviert ist. Legen Sie diese Eigenschaft auf `$true` fest, um sicherzustellen, dass dieses Konto deaktiviert ist. Legen Sie sie auf `$false` fest, um sicherzustellen, dass es aktiviert ist. |
|FullName |Stellt eine Zeichenfolge mit dem vollständigen Namen dar, den Sie für das Benutzerkonto verwenden möchten. |
|Kennwort |Gibt das Kennwort an, das Sie für dieses Konto verwenden möchten. |
|PasswordChangeNotAllowed |Gibt an, ob der Benutzer das Kennwort ändern kann. Legen Sie diese Eigenschaft auf `$true` fest, um sicherzustellen, dass der Benutzer das Kennwort nicht ändern kann. Legen Sie es auf `$false` fest, damit der Benutzer das Kennwort ändern kann. Standardwert: `$false`. |
|PasswordChangeRequired |Gibt an, ob der Benutzer sein Kennwort bei der nächsten Anmeldung ändern muss. Legen Sie diese Eigenschaft auf `$true` fest, wenn der Benutzer das Kennwort ändern muss. Standardwert: `$true`. |
|PasswordNeverExpires |Gibt an, ob das Kennwort abläuft. Um sicherzustellen, dass das Kennwort für dieses Konto nie abläuft, legen Sie diese Eigenschaft auf `$true` fest. Legen Sie sie auf `$false` fest, wenn das Kennwort ablaufen soll. Standardwert: `$false`. |

## <a name="common-properties"></a>Allgemeine Eigenschaften

|Eigenschaft |BESCHREIBUNG |
|---|---|
|DependsOn |Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Gibt an, ob das Konto vorhanden ist. Legen Sie diese Eigenschaft auf **Present** fest, um sicherzustellen, dass das Konto vorhanden ist. Legen Sie sie auf **Absent** fest, um sicherzustellen, dass das Konto nicht vorhanden ist. Der Standardwert ist **Present**. |
|PsDscRunAsCredential |Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest. |

> [!NOTE]
> Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen. Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).

## <a name="example"></a>Beispiel

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```