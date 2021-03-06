---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC-Ressource „WindowsFeature“
ms.openlocfilehash: 7f9b200b4d10aef6c8a3f76c497f4d60e8062cb5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557396"
---
# <a name="dsc-windowsfeature-resource"></a>DSC-Ressource „WindowsFeature“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.x

Die Ressource **WindowsFeature** in Windows PowerShell DSC (Desired State Configuration) bietet einen Mechanismus, um sicherzustellen, dass Rollen und Features einem Knoten hinzugefügt oder entfernt werden.

## <a name="syntax"></a>Syntax

```Syntax
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ Source = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschaften

|Eigenschaft |BESCHREIBUNG |
|---|---|
|Name |Gibt den Namen der Rolle oder des Features an, die/das hinzugefügt oder entfernt werden soll. Dies ist identisch mit der **Name**-Eigenschaft aus dem Cmdlet [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) und nicht mit dem Anzeigenamen der Rolle oder des Features. |
|Anmeldeinformationen |Gibt die Anmeldeinformationen zum Hinzufügen oder Entfernen der Rolle oder des Features an. |
|IncludeAllSubFeature |Legen Sie diese Eigenschaft auf `$true` fest, um den Status aller erforderlichen Teilfeatures mit dem Status des Features sicherzustellen, das Sie mit der **Name**-Eigenschaft angeben. |
|LogPath |Gibt den Pfad zu einer Protokolldatei an, in der der Ressourcenanbieter den Vorgang protokollieren soll. |
|`Source` |Gibt bei Bedarf den Speicherort der Quelldatei an, die für die Installation verwendet werden soll. |

## <a name="common-properties"></a>Allgemeine Eigenschaften

|Eigenschaft |BESCHREIBUNG |
|---|---|
|DependsOn |Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Gibt an, ob die Rolle oder das Feature hinzugefügt wird. Um sicherzustellen, dass die Rolle oder das Feature hinzugefügt wird, legen Sie diese Eigenschaft auf **Present** fest. Um sicherzustellen, dass die Rolle oder das Feature entfernt wird, legen Sie diese Eigenschaft auf **Absent** fest. Der Standardwert ist **Present**. |
|PsDscRunAsCredential |Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest. |

> [!NOTE]
> Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen. Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).

## <a name="example"></a>Beispiel

```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```
