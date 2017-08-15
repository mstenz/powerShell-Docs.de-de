---
ms.date: 2017-06-12T00:00:00.000Z
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 7817769c3fc060a51c833b7469f7b556b9b40e87
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2017
---
# <a name="call-base-class-method"></a>Aufrufen der Basisklassenmethode

Sie können vorhandene Methoden in Unterklassen überschreiben. Deklarieren Sie dazu Methoden mit demselben Namen und derselben Signatur:

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

Zum Aufrufen von Basisklassemethoden aus überschriebenen Implementierungen der Basisklasse führen Sie beim Aufrufen eine Umwandlung in die Basisklasse ([baseClass]$this) durch.

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

Alle PowerShell-Methoden sind virtuell. Sie können nicht virtuelle .NET-Methoden in einer Unterklasse ausblenden, indem Sie dieselbe Syntax wie zum Überschreiben verwenden. Sie müssen bloß Methoden mit demselben Namen und derselben Signatur deklarieren.

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

