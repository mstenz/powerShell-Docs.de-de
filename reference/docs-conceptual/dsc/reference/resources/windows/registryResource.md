---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC-Ressource „Registry“
ms.openlocfilehash: be2f9134368784ad2d208362104ce046c49492e0
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953077"
---
# <a name="dsc-registry-resource"></a>DSC-Ressource „Registry“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.x

Die Ressource **Registry** in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten von Registrierungsschlüsseln und -werten auf einem Zielknoten.

## <a name="syntax"></a>Syntax

```Syntax
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Present | Absent }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschaften

|Eigenschaft |BESCHREIBUNG |
|---|---|
|Schlüssel |Gibt den Pfad des Registrierungsschlüssels an, für den Sie einen bestimmten Zustand sicherstellen möchten. Dieser Pfad muss die Struktur enthalten. |
|ValueName |Gibt den Namen des Registrierungswerts an. Um einen Registrierungsschlüssel hinzuzufügen oder zu entfernen, geben Sie diese Eigenschaft als leere Zeichenfolge ohne Angabe von **ValueType** oder **ValueData** an. Um den Standardwert eines Registrierungsschlüssels zu ändern oder zu entfernen, geben Sie diese Eigenschaft als leere Zeichenfolge an und legen gleichzeitig **ValueType** oder **ValueData** fest. |
|Force |Wenn der angegebene Registrierungsschlüssel vorhanden ist, wird dieser von **Force** mit dem neuen Wert überschrieben. Beim Löschen eines Registrierungsschlüssels mit Unterschlüsseln muss dieser Wert `$true` lauten. |
|Hex |Gibt an, ob Daten im Hexadezimalformat ausgedrückt werden. Falls angegeben, werden die DWORD/QWORD-Wertdaten im Hexadezimalformat angezeigt. Gilt nicht für andere Typen. Standardwert: `$false`. |
|ValueData |Die Daten des Registrierungswerts. |
|ValueType |Gibt den Typ des Werts an. Die unterstützten Typen sind: **Zeichenfolge** (REG_SZ), **Binär** (REG-BINARY), **Dword** (32-Bit REG_DWORD), **Qword** (64-Bit REG_QWORD), **mehrteilige Zeichenfolge** (REG_MULTI_SZ), **erweiterbare Zeichenfolge** (REG_EXPAND_SZ). |

## <a name="common-properties"></a>Allgemeine Eigenschaften

|Eigenschaft |BESCHREIBUNG |
|---|---|
|DependsOn |Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Gibt an, ob Schlüssel und Wert vorhanden sind. Um dies sicherzustellen, legen Sie diese Eigenschaft auf **Present** fest. Um sicherzustellen, dass sie nicht vorhanden sind, legen Sie die Eigenschaft auf **Absent** fest. Der Standardwert ist **Present**. |
|PsDscRunAsCredential |Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest. |

> [!NOTE]
> Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen. Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).

## <a name="example"></a>Beispiel

In diesem Beispiel wird sichergestellt, dass ein Schlüssel mit dem Namen „ExampleKey“ in der Struktur **HKEY\_LOCAL\_MACHINE** vorhanden ist.

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> Das Ändern einer Registrierungseinstellung in der Struktur `HKEY_CURRENT_USER` erfordert, dass die Konfiguration mit Benutzeranmeldeinformationen anstatt mit Anmeldeinformationen des Systems ausgeführt wird. Sie können die **PsDscRunAsCredential**-Eigenschaft verwenden, um die Benutzeranmeldeinformationen für die Konfiguration anzugeben. Ein Beispiel finden Sie unter [Ausführen von DSC mit Benutzeranmeldeinformationen](../../../configurations/runAsUser.md).