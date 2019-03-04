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
ms.openlocfilehash: e8185eb7221a3be0445eddc537dbca89478c74f2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859796"
---
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="79335-102">Definieren von Standardelementgruppen für Objekte</span><span class="sxs-lookup"><span data-stu-id="79335-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="79335-103">Die Elementgruppe PSStandardMembers wird von Windows PowerShell verwendet, um die Standard-Eigenschaftensätze für ein Objekt zu definieren.</span><span class="sxs-lookup"><span data-stu-id="79335-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="79335-104">Die Standard-Eigenschaftensätze können durch Befehle wie z. B. der formatierungs-Cmdlets verwendet werden, um nur die Eigenschaften anzuzeigen, die von der festgelegten Eigenschaft definiert werden.</span><span class="sxs-lookup"><span data-stu-id="79335-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="79335-105">Die Standard-Eigenschaftensätzen enthalten DefaultDisplayProperty DefaultDisplayPropertySet und DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="79335-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="79335-106">Windows PowerShell ignoriert alle anderen Elementgruppen und alle anderen Eigenschaftensätze, die Elementgruppe PSStandardMembers hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="79335-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="79335-107">Elementgruppe für "System.Diagnostics.Process"</span><span class="sxs-lookup"><span data-stu-id="79335-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="79335-108">Im folgenden Beispiel definiert die Elementgruppe PSStandardMembers DefaultDisplayPropertySet Eigenschaftensatz für ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekte.</span><span class="sxs-lookup"><span data-stu-id="79335-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="79335-109">Diese Eigenschaft festgelegt ist, wird vom verwendet die [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="79335-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>
<span data-ttu-id="79335-110">Im folgenden Beispiel definiert die Elementgruppe PSStandardMembers DefaultDisplayPropertySet Eigenschaftensatz für ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekte.</span><span class="sxs-lookup"><span data-stu-id="79335-110">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="79335-111">Diese Eigenschaft festgelegt ist, wird vom verwendet die [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="79335-111">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

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

<span data-ttu-id="79335-112">Die folgende Ausgabe zeigt die Standardeigenschaften, die zurückgegeben werden, indem die [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="79335-112">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="79335-113">Nur die `Id`, `Handles`, `CPU`, und `Name` Eigenschaften werden für jedes Prozessobjekt zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="79335-113">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>
<span data-ttu-id="79335-114">Die folgende Ausgabe zeigt die Standardeigenschaften, die zurückgegeben werden, indem die [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="79335-114">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="79335-115">Nur die `Id`, `Handles`, `CPU`, und `Name` Eigenschaften werden für jedes Prozessobjekt zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="79335-115">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="79335-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="79335-116">See Also</span></span>

[<span data-ttu-id="79335-117">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="79335-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
