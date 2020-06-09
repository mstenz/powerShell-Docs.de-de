---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC-Ressource „Registry“
ms.openlocfilehash: 3acd79fa81bc731f344d810371b961dc3af3a11d
ms.sourcegitcommit: 1ab59991c18e1b9692333d5e58ce649eaa75594f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2020
ms.locfileid: "84203646"
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

## <a name="examples"></a>Beispiele

### <a name="example-1-ensure-specified-value-and-data-under-specified-registry-key"></a>Beispiel 1: Sicherstellen, dass der angegebene Wert und die angegebenen Daten unter dem angegebenen Registrierungsschlüssel vorhanden sind

In diesem Beispiel wird sichergestellt, dass der Registrierungswert „TestValue“ unter dem Schlüssel „ExampleKey1“ in der Struktur `HKEY\_LOCAL\_MACHINE` vorhanden ist und über die Daten „TestData“ verfügt.

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey1"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

### <a name="example-2-ensure-specified-registry-key-exists"></a>Beispiel 2: Sicherstellen, dass der angegebene Registrierungsschlüssel vorhanden ist

In diesem Beispiel wird sichergestellt, dass der Schlüssel „ExampleKey2“ in der Struktur **HKEY\_LOCAL\_MACHINE** vorhanden ist.

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey2"
        ValueName   = ""
    }
}
```

> [!NOTE]
> Das Ändern einer Registrierungseinstellung in der Struktur `HKEY_CURRENT_USER` erfordert, dass die Konfiguration mit Benutzeranmeldeinformationen anstatt mit Anmeldeinformationen des Systems ausgeführt wird. Sie können die **PsDscRunAsCredential**-Eigenschaft verwenden, um die Benutzeranmeldeinformationen für die Konfiguration anzugeben. Ein Beispiel finden Sie unter [Ausführen von DSC mit Benutzeranmeldeinformationen](../../../configurations/runAsUser.md).
