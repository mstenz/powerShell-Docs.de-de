---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Anzeigen einer Objektstruktur (Get-Member)
ms.technology: powershell
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: f260db2ad638e8448198de43a348a879942f27dc
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="viewing-object-structure-get-member"></a>Anzeigen einer Objektstruktur (Get-Member)
Weil Objekte in Windows PowerShell eine so zentrale Rolle spielen, gibt es mehrere systemeigene Befehle, die zum Arbeiten mit beliebigen Objekttypen vorgesehen sind. Der wichtigste dieser Befehle ist der Befehl **Get-Member**.

Die einfachste Methode zum Analysieren der Objekte, die von einem Befehl zurückgegeben werden, besteht darin, die Ausgabe dieses Befehls an das Cmdlet **Get-Member** weiterzuleiten. Das Cmdlet **Get-Member** zeigt den formalen Objekttypnamen sowie eine vollständige Liste der Member des Objekts an. Die Anzahl von zurückgegebenen Elementen kann manchmal überwältigend sein. Beispielsweise kann ein Prozessobjekt mehr als 100 Member haben.

Wenn Sie alle Member eines Prozessobjekts anzeigen möchten und die Ausgabe seitenweise erfolgen soll, sodass Sie alle Daten sehen können, geben Sie Folgendes ein:

```
PS> Get-Process | Get-Member | Out-Host -Paging
```

Die Ausgabe dieses Befehls sieht in etwa wie folgt aus:

```
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

Diese lange Liste von Informationen lässt sich nutzbarer machen, indem Sie nach den jeweils gewünschten Elementen filtern. Der Befehl **Get-Member** ermöglicht es Ihnen, nur Member aufzulisten, die Eigenschaften sind. Es gibt mehrere Typen von Eigenschaften. Das Cmdlet zeigt die Eigenschaften eines beliebigen Typs an, wenn Sie den **MemberType**-Parameter von „Get-Member“ auf den Wert **Properties** festlegen. Die Ergebnisliste ist immer noch sehr lang, aber etwas besser zu handhaben:

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
> „MemberType“ hat die folgenden zulässigen Werte: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet und All.

Es gibt mehr als 60 Eigenschaften für einen Prozess. Der Grund, warum Windows PowerShell häufig nur wenige Eigenschaften für ein bekanntes Objekt anzeigt, liegt darin, dass ein Anzeigen aller Eigenschaften zu einer nicht handhabbaren Menge an Informationen führen würde.

> [!NOTE]
> Windows PowerShell bestimmt, wie ein Objekttyp angezeigt werden soll, anhand der Informationen, die in XML-Dateien gespeichert sind, deren Namen mit „.format.ps1xml“ enden. Die Formatierungsdaten für Prozessobjekte, die „.NET System.Diagnostics.Process“-Objekte sind, sind in „PowerShellCore.format.ps1xml“ gespeichert.

Wenn Sie Eigenschaften anzeigen müssen, die nicht standardmäßig von Windows PowerShell angezeigt werden, müssen Sie die Ausgabedaten selbst formatieren. Dazu können Sie die „Format“-Cmdlets verwenden.

