---
title: Definieren die Standardelement, für Objekte festlegt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: 2d634e7638ec0e0117d65ca0b2d08e68f0068a03
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794908"
---
# <a name="defining-default-member-sets-for-objects"></a>Definieren von Standardelementgruppen für Objekte

Die Elementgruppe PSStandardMembers wird von Windows PowerShell verwendet, um die Standard-Eigenschaftensätze für ein Objekt zu definieren. Die Standard-Eigenschaftensätze können durch Befehle wie z. B. der formatierungs-Cmdlets verwendet werden, um nur die Eigenschaften anzuzeigen, die von der festgelegten Eigenschaft definiert werden. Die Standard-Eigenschaftensätzen enthalten DefaultDisplayProperty DefaultDisplayPropertySet und DefaultKeyPropertySet. Windows PowerShell ignoriert alle anderen Elementgruppen und alle anderen Eigenschaftensätze, die Elementgruppe PSStandardMembers hinzugefügt.

## <a name="member-set-for-systemdiagnosticsprocess"></a>Elementgruppe für "System.Diagnostics.Process"

Im folgenden Beispiel definiert die Elementgruppe PSStandardMembers DefaultDisplayPropertySet Eigenschaftensatz für ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekte. Diese Eigenschaft festgelegt ist, wird vom verwendet die [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) Cmdlet.

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

Die folgende Ausgabe zeigt die Standardeigenschaften, die zurückgegeben werden, indem die [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) Cmdlet. Nur die `Id`, `Handles`, `CPU`, und `Name` Eigenschaften werden für jedes Prozessobjekt zurückgegeben.

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
