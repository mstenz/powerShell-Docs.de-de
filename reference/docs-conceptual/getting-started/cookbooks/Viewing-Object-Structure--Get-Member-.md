---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Anzeigen einer Objektstruktur (Get-Member)
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: cc93e45e4306b3d623c1d3d1096dd20c1afc59c8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="bcb6b-103">Anzeigen einer Objektstruktur (Get-Member)</span><span class="sxs-lookup"><span data-stu-id="bcb6b-103">Viewing Object Structure (Get-Member)</span></span>

<span data-ttu-id="bcb6b-104">Weil Objekte in Windows PowerShell eine so zentrale Rolle spielen, gibt es mehrere systemeigene Befehle, die zum Arbeiten mit beliebigen Objekttypen vorgesehen sind.</span><span class="sxs-lookup"><span data-stu-id="bcb6b-104">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="bcb6b-105">Der wichtigste dieser Befehle ist der Befehl **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="bcb6b-105">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="bcb6b-106">Die einfachste Methode zum Analysieren der Objekte, die von einem Befehl zurückgegeben werden, besteht darin, die Ausgabe dieses Befehls an das Cmdlet **Get-Member** weiterzuleiten.</span><span class="sxs-lookup"><span data-stu-id="bcb6b-106">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="bcb6b-107">Das Cmdlet **Get-Member** zeigt den formalen Objekttypnamen sowie eine vollständige Liste der Member des Objekts an.</span><span class="sxs-lookup"><span data-stu-id="bcb6b-107">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="bcb6b-108">Die Anzahl von zurückgegebenen Elementen kann manchmal überwältigend sein.</span><span class="sxs-lookup"><span data-stu-id="bcb6b-108">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="bcb6b-109">Beispielsweise kann ein Prozessobjekt mehr als 100 Member haben.</span><span class="sxs-lookup"><span data-stu-id="bcb6b-109">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="bcb6b-110">Wenn Sie alle Member eines Prozessobjekts anzeigen möchten und die Ausgabe seitenweise erfolgen soll, sodass Sie alle Daten sehen können, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="bcb6b-110">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="bcb6b-111">Die Ausgabe dieses Befehls sieht in etwa wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="bcb6b-111">The output from this command will look something like this:</span></span>

```output
TypeName: System.Diagnostics.Process

Name                           MemberType     Definition
----                           ----------     ----------
Handles                        AliasProperty  Handles = Handlecount
Name                           AliasProperty  Name = ProcessName
NPM                            AliasProperty  NPM = NonpagedSystemMemorySize
PM                             AliasProperty  PM = PagedMemorySize
VM                             AliasProperty  VM = VirtualMemorySize
WS                             AliasProperty  WS = WorkingSet
add_Disposed                   Method         System.Void add_Disposed(Event...
...
```

<span data-ttu-id="bcb6b-112">Diese lange Liste von Informationen lässt sich nutzbarer machen, indem Sie nach den jeweils gewünschten Elementen filtern.</span><span class="sxs-lookup"><span data-stu-id="bcb6b-112">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="bcb6b-113">Der Befehl **Get-Member** ermöglicht es Ihnen, nur Member aufzulisten, die Eigenschaften sind.</span><span class="sxs-lookup"><span data-stu-id="bcb6b-113">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="bcb6b-114">Es gibt mehrere Typen von Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="bcb6b-114">There are several forms of properties.</span></span> <span data-ttu-id="bcb6b-115">Das Cmdlet zeigt die Eigenschaften eines beliebigen Typs an, wenn Sie den **Get-Member MemberType**-Parameter auf den Wert **Eigenschaften** festlegen.</span><span class="sxs-lookup"><span data-stu-id="bcb6b-115">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties**.</span></span> <span data-ttu-id="bcb6b-116">Die Ergebnisliste ist immer noch sehr lang, aber etwas besser zu handhaben:</span><span class="sxs-lookup"><span data-stu-id="bcb6b-116">The resulting list is still very long, but a bit more manageable:</span></span>

```
PS> Get-Process | Get-Member -MemberType Properties

   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
...
ExitCode                   Property       System.Int32 ExitCode {get;}
...
Handle                     Property       System.IntPtr Handle {get;}
...
CPU                        ScriptProperty System.Object CPU {get=$this.Total...
...
Path                       ScriptProperty System.Object Path {get=$this.Main...
...
```

> [!NOTE]
> <span data-ttu-id="bcb6b-117">„MemberType“ hat die folgenden zulässigen Werte: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet und All.</span><span class="sxs-lookup"><span data-stu-id="bcb6b-117">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="bcb6b-118">Es gibt mehr als 60 Eigenschaften für einen Prozess.</span><span class="sxs-lookup"><span data-stu-id="bcb6b-118">There are over 60 properties for a process.</span></span> <span data-ttu-id="bcb6b-119">Der Grund, warum Windows PowerShell häufig nur wenige Eigenschaften für ein bekanntes Objekt anzeigt, liegt darin, dass ein Anzeigen aller Eigenschaften zu einer nicht handhabbaren Menge an Informationen führen würde.</span><span class="sxs-lookup"><span data-stu-id="bcb6b-119">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="bcb6b-120">Windows PowerShell bestimmt, wie ein Objekttyp angezeigt werden soll, anhand der Informationen, die in XML-Dateien gespeichert sind, deren Namen mit „.format.ps1xml“ enden.</span><span class="sxs-lookup"><span data-stu-id="bcb6b-120">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="bcb6b-121">Die Formatierungsdaten für Prozessobjekte, die „.NET System.Diagnostics.Process“-Objekte sind, sind in „DotNetTypes.ps1xml“ gespeichert.</span><span class="sxs-lookup"><span data-stu-id="bcb6b-121">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="bcb6b-122">Wenn Sie Eigenschaften anzeigen müssen, die nicht standardmäßig von Windows PowerShell angezeigt werden, müssen Sie die Ausgabedaten selbst formatieren.</span><span class="sxs-lookup"><span data-stu-id="bcb6b-122">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="bcb6b-123">Dazu können Sie die „Format“-Cmdlets verwenden.</span><span class="sxs-lookup"><span data-stu-id="bcb6b-123">This can be done by using the format cmdlets.</span></span>