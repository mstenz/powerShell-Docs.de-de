---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC für Linux-Resource „nxScript“"
ms.openlocfilehash: 5fc448d15f9bec77be64b5f9ee801f6616cf7208
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="49f64-103">DSC für Linux-Resource „nxScript“</span><span class="sxs-lookup"><span data-stu-id="49f64-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="49f64-104">Die Ressource **nxScript** in PowerShell DSC bietet einen Mechanismus zum Ausführen von Linux-Skripts auf einem Linux-Knoten.</span><span class="sxs-lookup"><span data-stu-id="49f64-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="49f64-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="49f64-105">Syntax</span></span>

```
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

## <a name="properties"></a><span data-ttu-id="49f64-106">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="49f64-106">Properties</span></span>

|  <span data-ttu-id="49f64-107">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="49f64-107">Property</span></span> |  <span data-ttu-id="49f64-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="49f64-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="49f64-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="49f64-109">GetScript</span></span>| <span data-ttu-id="49f64-110">Bietet ein Skript, das beim Aufrufen des Cmdlets [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="49f64-110">Provides a script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span></span> <span data-ttu-id="49f64-111">Das Skript muss mit einem Shebang, z. B. „#!/bin/bash“, beginnen.</span><span class="sxs-lookup"><span data-stu-id="49f64-111">The script must begin with a shebang, such as #!/bin/bash.</span></span>| 
| <span data-ttu-id="49f64-112">SetScript</span><span class="sxs-lookup"><span data-stu-id="49f64-112">SetScript</span></span>| <span data-ttu-id="49f64-113">Stellt ein Skript bereit.</span><span class="sxs-lookup"><span data-stu-id="49f64-113">Provides a script.</span></span> <span data-ttu-id="49f64-114">Beim Aufruf des Cmdlets [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) wird **TestScript** zuerst ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="49f64-114">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** runs first.</span></span> <span data-ttu-id="49f64-115">Wenn der **TestScript**-Block einen Exitcode ungleich 0 zurückgibt, wird der **SetScript**-Block ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="49f64-115">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="49f64-116">Wenn der **TestScript**-Block den Exitcode 0 zurückgibt, wird der **SetScript**-Block nicht ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="49f64-116">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="49f64-117">Das Skript muss mit einem Shebang, z. B. `#!/bin/bash`, beginnen.</span><span class="sxs-lookup"><span data-stu-id="49f64-117">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>| 
| <span data-ttu-id="49f64-118">TestScript</span><span class="sxs-lookup"><span data-stu-id="49f64-118">TestScript</span></span>| <span data-ttu-id="49f64-119">Stellt ein Skript bereit.</span><span class="sxs-lookup"><span data-stu-id="49f64-119">Provides a script.</span></span> <span data-ttu-id="49f64-120">Beim Aufruf des Cmdlets [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) wird dieses Skript ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="49f64-120">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this script runs.</span></span> <span data-ttu-id="49f64-121">Wenn es einen Exitcode ungleich 0 zurückgibt, wird der „SetScript“-Block ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="49f64-121">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="49f64-122">Wenn es den Exitcode 0 zurückgibt, wird der **SetScript**-Block nicht ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="49f64-122">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="49f64-123">Der **TestScript**-Block wird auch ausgeführt, wenn Sie das Cmdlet[Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="49f64-123">The **TestScript** also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="49f64-124">In diesem Fall wird der **SetScript**-Block jedoch nicht ausgeführt, ganz gleich, welcher Exitcode vom **TestScript**-Block zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="49f64-124">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="49f64-125">Der **TestScript**-Block muss den Exitcode 0 zurückgeben, wenn die tatsächliche Konfiguration der aktuellen Konfiguration des gewünschten Zustands entspricht. Falls nicht, muss ein Exitcode ungleich 0 zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="49f64-125">The **TestScript** must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="49f64-126">(Die aktuelle Konfiguration des gewünschten Zustands ist die letzte Konfiguration, die auf den Knoten angewendet wurde, der DSC verwendet.)</span><span class="sxs-lookup"><span data-stu-id="49f64-126">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="49f64-127">Das Skript muss mit einem Shebang, z. B. „1#!/bin/bash.1“, beginnen.</span><span class="sxs-lookup"><span data-stu-id="49f64-127">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>| 
| <span data-ttu-id="49f64-128">User</span><span class="sxs-lookup"><span data-stu-id="49f64-128">User</span></span>| <span data-ttu-id="49f64-129">Der Benutzer, der das Skript ausführt.</span><span class="sxs-lookup"><span data-stu-id="49f64-129">The user to run the script as.</span></span>| 
| <span data-ttu-id="49f64-130">Group</span><span class="sxs-lookup"><span data-stu-id="49f64-130">Group</span></span>| <span data-ttu-id="49f64-131">Die Gruppe, die das Skript ausführt.</span><span class="sxs-lookup"><span data-stu-id="49f64-131">The group to run the script as.</span></span>| 
| <span data-ttu-id="49f64-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="49f64-132">DependsOn</span></span> | <span data-ttu-id="49f64-133">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="49f64-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="49f64-134">Wenn beispielsweise die **ID** des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="49f64-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="49f64-135">Beispiel</span><span class="sxs-lookup"><span data-stu-id="49f64-135">Example</span></span>

<span data-ttu-id="49f64-136">Das folgende Beispiel veranschaulicht die Verwendung der Ressource **nxScript**, um zusätzliche Konfigurationsschritte auszuführen.</span><span class="sxs-lookup"><span data-stu-id="49f64-136">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```
Import-DSCResource -Module nx 

Node $node {
nxScript KeepDirEmpty{

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

