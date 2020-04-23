---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC für Linux-Resource „nxScript“
ms.openlocfilehash: a7f2114aba47bb581cdd19168e784b79dfc5b6ad
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953187"
---
# <a name="dsc-for-linux-nxscript-resource"></a>DSC für Linux-Resource „nxScript“

Die Ressource **nxScript** in PowerShell DSC bietet einen Mechanismus zum Ausführen von Linux-Skripts auf einem Linux-Knoten.

## <a name="syntax"></a>Syntax

```Syntax
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>Eigenschaften

|Eigenschaft |BESCHREIBUNG |
|---|---|
|GetScript |Stellt ein Skript bereit, um den aktuellen Status des Computers zurückzugeben. Dieses Skript wird ausgeführt, wenn Sie das Skript [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) aufrufen. Das Skript muss mit einem Shebang, z. B. `#!/bin/bash`, beginnen. |
|SetScript |Stellt ein Skript bereit, das den Computer in den richtigen Zustand versetzt. Wenn Sie das Skript [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) aufrufen, wird **TestScript** zuerst ausgeführt. Wenn der **TestScript**-Block einen Exitcode ungleich 0 zurückgibt, wird der **SetScript**-Block ausgeführt. Wenn der **TestScript**-Block den Exitcode 0 zurückgibt, wird der **SetScript**-Block nicht ausgeführt. Das Skript muss mit einem Shebang, z. B. `#!/bin/bash`, beginnen. |
|TestScript |Stellt ein Skript bereit, das auswertet, ob sich der Knoten derzeit im richtigen Zustand befindet. Wenn Sie das Skript [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) aufrufen, wird dieses Skript ausgeführt. Wenn es einen Exitcode ungleich 0 zurückgibt, wird der **SetScript**-Block ausgeführt. Wenn es den Exitcode 0 zurückgibt, wird der **SetScript**-Block nicht ausgeführt. **TestScript** wird auch ausgeführt, wenn Sie das Skript [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) aufrufen. In diesem Fall wird der **SetScript**-Block jedoch nicht ausgeführt, ganz gleich, welcher Exitcode vom **TestScript**-Block zurückgegeben wird. **TestScript** muss Inhalte enthalten und den Exitcode 0 zurückgeben, wenn die tatsächliche Konfiguration der aktuellen Konfiguration des gewünschten Zustands entspricht. Andernfalls muss ein Exitcode ungleich 0 zurückgegeben werden. Die aktuelle Konfiguration des gewünschten Zustands ist die letzte Konfiguration, die auf den Knoten angewendet wurde, der DSC verwendet. Das Skript muss mit einem Shebang, z. B. `#!/bin/bash`, beginnen. |
|Benutzer |Der Benutzer, der das Skript ausführt. |
|Group |Die Gruppe, die das Skript ausführt. |

## <a name="common-properties"></a>Allgemeine Eigenschaften

|Eigenschaft |BESCHREIBUNG |
|---|---|
|DependsOn |Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`. |

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung der Ressource **nxScript**, um zusätzliche Konfigurationsschritte auszuführen.

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxScript KeepDirEmpty {

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
    }
}
```
