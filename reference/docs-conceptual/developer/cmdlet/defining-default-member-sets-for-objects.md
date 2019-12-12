---
title: Definieren von Standardmember-Sätzen für Objekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: 2d634e7638ec0e0117d65ca0b2d08e68f0068a03
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369779"
---
# <a name="defining-default-member-sets-for-objects"></a>Definieren von Standardelementgruppen für Objekte

Der psstandardmembers-Member Satz wird von Windows PowerShell verwendet, um die Standardeigenschaften Sätze für ein Objekt zu definieren. Die Standardeigenschaften Sätze können von Befehlen wie z. b. den Formatierungs-Cmdlets verwendet werden, um nur die Eigenschaften anzuzeigen, die durch den Eigenschaften Satz definiert werden. Die Standard Eigenschafts Sätze umfassen defaultdisplayproperty, defaultdisplaypropertyset und defaultkeypropertyset. Windows PowerShell ignoriert alle anderen Element Sätze und alle anderen Eigenschaften Sätze, die dem psstandardmembers-Element Satz hinzugefügt werden.

## <a name="member-set-for-systemdiagnosticsprocess"></a>Member festgelegt für System. Diagnostics. Process

Im folgenden Beispiel definiert der psstandardmembers-Member Satz die defaultdisplaypropertyset-Eigenschaft, die für [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekte festgelegt ist. Dieser Eigenschaften Satz wird vom Cmdlet " [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) " verwendet.

```xml
<Type>
  <Name>System.Diagnostics.Process</Name>
  <Members>
    <MemberSet>
     <Name>PSStandardMembers</Name>
     <Members>
       <PropertySet>
         <Name>DefaultDisplayPropertySet</Name>
         <ReferencedProperties>
           <Name>Id</Name>
           <Name>Handles</Name>
           <Name>CPU</Name>
           <Name>Name</Name>
         </ReferencedProperties>
      </PropertySet>
    </Members>
  </MemberSet>
```

Die folgende Ausgabe zeigt die Standardeigenschaften, die vom Cmdlet " [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) " zurückgegeben werden. Für jedes Prozess Objekt werden nur die Eigenschaften `Id`, `Handles`, `CPU`und `Name` zurückgegeben.

```powershell
Get-Process | format-list
```

```output
Id      : 2036
Handles : 27
CPU     :
Name    : AEADISRV

Id      : 272
Handles : 38
CPU     :
Name    : agrsmsvc
...
```

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
