---
title: Erweitern von Eigenschaften für Objekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 3b14007384cca0d0cfa35655aee437adf73b1ff0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364449"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="a5480-102">Erweitern Objekteigenschaften</span><span class="sxs-lookup"><span data-stu-id="a5480-102">Extending Properties for Objects</span></span>

<span data-ttu-id="a5480-103">Wenn Sie .NET Framework Objekte erweitern, können Sie den-Objekten Alias Eigenschaften, Code Eigenschaften, Notiz Eigenschaften, Skript Eigenschaften und Eigenschaften Sätze hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a5480-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="a5480-104">Die XML-Daten, die diese Eigenschaften definieren, werden in den folgenden Abschnitten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a5480-104">The XML that defines these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="a5480-105">Die Beispiele in den folgenden Abschnitten stammen aus der standardmäßigen `Types.ps1xml` Types-Datei im PowerShell-Installationsverzeichnis (`$PSHOME`).</span><span class="sxs-lookup"><span data-stu-id="a5480-105">The examples in the following sections are from the default `Types.ps1xml` types file in the PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="a5480-106">Weitere Informationen finden Sie unter [about Types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="a5480-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="a5480-107">Alias Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="a5480-107">Alias properties</span></span>

<span data-ttu-id="a5480-108">Eine Alias Eigenschaft definiert einen neuen Namen für eine vorhandene Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="a5480-108">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="a5480-109">Im folgenden Beispiel wird die **count** -Eigenschaft dem [System. Array](/dotnet/api/System.Array) -Typ hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a5480-109">In the following example, the **Count** property is added to the [System.Array](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="a5480-110">Das [aliasproperty](/dotnet/api/system.management.automation.psaliasproperty) -Element definiert die erweiterte Eigenschaft als Alias Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="a5480-110">The [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) element defines the extended property as an alias property.</span></span> <span data-ttu-id="a5480-111">Das [Name](/dotnet/api/system.management.automation.psmemberinfo.name) -Element gibt den neuen Namen an.</span><span class="sxs-lookup"><span data-stu-id="a5480-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the new name.</span></span> <span data-ttu-id="a5480-112">Und das [referencedmembership Name](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) -Element gibt die vorhandene Eigenschaft an, auf die vom Alias verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="a5480-112">And, the [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="a5480-113">Sie können auch das `AliasProperty`-Element den Membern des Members [-Elements hinzu](/dotnet/api/system.management.automation.psmemberset) fügen.</span><span class="sxs-lookup"><span data-stu-id="a5480-113">You can also add the `AliasProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

## <a name="code-properties"></a><span data-ttu-id="a5480-114">Code Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="a5480-114">Code properties</span></span>

<span data-ttu-id="a5480-115">Eine Code Eigenschaft verweist auf eine statische Eigenschaft eines .NET Framework Objekts.</span><span class="sxs-lookup"><span data-stu-id="a5480-115">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="a5480-116">Im folgenden Beispiel wird die **Mode** -Eigenschaft dem [System. IO. directoriyinfo](/dotnet/api/System.IO.DirectoryInfo) -Typ hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a5480-116">In the following example, the **Mode** property is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="a5480-117">Das [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) -Element definiert die erweiterte Eigenschaft als Code Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="a5480-117">The [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) element defines the extended property as a code property.</span></span> <span data-ttu-id="a5480-118">Das [Name](/dotnet/api/system.management.automation.psmemberinfo.name) -Element gibt den Namen der erweiterten Eigenschaft an.</span><span class="sxs-lookup"><span data-stu-id="a5480-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="a5480-119">Und das [getcodereferenzierungselement](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) definiert die statische Methode, auf die von der erweiterten Eigenschaft verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="a5480-119">And, the [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="a5480-120">Sie können auch das `CodeProperty`-Element den Membern des Members [-Elements hinzu](/dotnet/api/system.management.automation.psmemberset) fügen.</span><span class="sxs-lookup"><span data-stu-id="a5480-120">You can also add the `CodeProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>Microsoft.PowerShell.Commands.FileSystemProvider</TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

## <a name="note-properties"></a><span data-ttu-id="a5480-121">Eigenschaften notieren</span><span class="sxs-lookup"><span data-stu-id="a5480-121">Note properties</span></span>

<span data-ttu-id="a5480-122">Eine Hinweis Eigenschaft definiert eine Eigenschaft, die über einen statischen Wert verfügt.</span><span class="sxs-lookup"><span data-stu-id="a5480-122">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="a5480-123">Im folgenden Beispiel wird die **Status** -Eigenschaft, deren Wert immer **Erfolg**ist, dem [System. IO. directoriyinfo](/dotnet/api/System.IO.DirectoryInfo) -Typ hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a5480-123">In the following example, the **Status** property, whose value is always **Success**, is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="a5480-124">Das [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) -Element definiert die erweiterte Eigenschaft als Note-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="a5480-124">The [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) element defines the extended property as a note property.</span></span> <span data-ttu-id="a5480-125">Das [Name](/dotnet/api/system.management.automation.psmemberinfo.name) -Element gibt den Namen der erweiterten Eigenschaft an.</span><span class="sxs-lookup"><span data-stu-id="a5480-125">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="a5480-126">Das [value](/dotnet/api/system.management.automation.psnoteproperty.value) -Element gibt den statischen Wert der erweiterten Eigenschaft an.</span><span class="sxs-lookup"><span data-stu-id="a5480-126">The [Value](/dotnet/api/system.management.automation.psnoteproperty.value) element specifies the static value of the extended property.</span></span> <span data-ttu-id="a5480-127">Das `NoteProperty`-Element kann auch den Membern [des Elements Members](/dotnet/api/system.management.automation.psmemberset) hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="a5480-127">The `NoteProperty` element can also be added to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

## <a name="script-properties"></a><span data-ttu-id="a5480-128">Skript Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="a5480-128">Script properties</span></span>

<span data-ttu-id="a5480-129">Eine Skript Eigenschaft definiert eine Eigenschaft, deren Wert die Ausgabe eines Skripts ist.</span><span class="sxs-lookup"><span data-stu-id="a5480-129">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="a5480-130">Im folgenden Beispiel wird die **VERSIONINFO** -Eigenschaft dem [System. IO. FileInfo](/dotnet/api/System.IO.FileInfo) -Typ hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a5480-130">In the following example, the **VersionInfo** property is added to the [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="a5480-131">Das [scriptproperty](/dotnet/api/system.management.automation.psscriptproperty) -Element definiert die erweiterte Eigenschaft als Skript Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="a5480-131">The [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) element defines the extended property as a script property.</span></span> <span data-ttu-id="a5480-132">Das [Name](/dotnet/api/system.management.automation.psmemberinfo.name) -Element gibt den Namen der erweiterten Eigenschaft an.</span><span class="sxs-lookup"><span data-stu-id="a5480-132">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="a5480-133">Das [getscriptblock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) -Element gibt das Skript an, das den Eigenschafts Wert generiert.</span><span class="sxs-lookup"><span data-stu-id="a5480-133">And, the [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) element specifies the script that generates the property value.</span></span> <span data-ttu-id="a5480-134">Sie können auch das `ScriptProperty`-Element den Membern des Members [-Elements hinzu](/dotnet/api/system.management.automation.psmemberset) fügen.</span><span class="sxs-lookup"><span data-stu-id="a5480-134">You can also add the `ScriptProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
        [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

## <a name="property-sets"></a><span data-ttu-id="a5480-135">Eigenschaften Sätze</span><span class="sxs-lookup"><span data-stu-id="a5480-135">Property sets</span></span>

<span data-ttu-id="a5480-136">Ein Eigenschaften Satz definiert eine Gruppe erweiterter Eigenschaften, auf die durch den Namen des Satzes verwiesen werden kann.</span><span class="sxs-lookup"><span data-stu-id="a5480-136">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span>
<span data-ttu-id="a5480-137">Beispielsweise kann der [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**Property** -Parameter eine bestimmte Eigenschaft festlegen, die angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="a5480-137">For example, the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**Property** parameter can specify a specific property set to be displayed.</span></span> <span data-ttu-id="a5480-138">Wenn ein Eigenschaften Satz angegeben wird, werden nur die Eigenschaften angezeigt, die zum Satz gehören.</span><span class="sxs-lookup"><span data-stu-id="a5480-138">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="a5480-139">Es gibt keine Einschränkung hinsichtlich der Anzahl der Eigenschafts Sätze, die für ein Objekt definiert werden können.</span><span class="sxs-lookup"><span data-stu-id="a5480-139">There's no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="a5480-140">Die Eigenschaften Sätze, die zum Definieren der Standard Anzeigeeigenschaften eines Objekts verwendet werden, müssen jedoch innerhalb des **psstandardmembers** -Element Satzes angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="a5480-140">However, the property sets used to define the default display properties of an object must be specified within the **PSStandardMembers** member set.</span></span> <span data-ttu-id="a5480-141">In der Datei mit den `Types.ps1xml` Typen enthalten die standardmäßigen Eigenschaften Satz Namen " **defaultdisplayproperty**", " **defaultdisplaypropertyset**" und " **defaultkeypropertyset**".</span><span class="sxs-lookup"><span data-stu-id="a5480-141">In the `Types.ps1xml` types file, the default property set names include **DefaultDisplayProperty**, **DefaultDisplayPropertySet**, and **DefaultKeyPropertySet**.</span></span> <span data-ttu-id="a5480-142">Alle zusätzlichen Eigenschaften Sätze, die Sie dem **psstandardmembers** -Element Satz hinzufügen, werden ignoriert.</span><span class="sxs-lookup"><span data-stu-id="a5480-142">Any additional property sets that you add to the **PSStandardMembers** member set are ignored.</span></span>

<span data-ttu-id="a5480-143">Im folgenden Beispiel wird der Wert der **defaultdisplaypropertyset** -Eigenschaft dem **psstandardmembers** -Element Satz des Typs [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a5480-143">In the following example, the **DefaultDisplayPropertySet** property set is added to the **PSStandardMembers** member set of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="a5480-144">Das [PropertySet](/dotnet/api/system.management.automation.pspropertyset) -Element definiert die Gruppe von Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="a5480-144">The [PropertySet](/dotnet/api/system.management.automation.pspropertyset) element defines the group of properties.</span></span> <span data-ttu-id="a5480-145">Das [Name](/dotnet/api/system.management.automation.psmemberinfo.name) -Element gibt den Namen des Eigenschaften Satzes an.</span><span class="sxs-lookup"><span data-stu-id="a5480-145">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the property set.</span></span> <span data-ttu-id="a5480-146">Und das [referencedproperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) -Element gibt die Eigenschaften des Satzes an.</span><span class="sxs-lookup"><span data-stu-id="a5480-146">And, the [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) element specifies the properties of the set.</span></span> <span data-ttu-id="a5480-147">Sie können auch das `PropertySet`-Element den Membern des [Type](/dotnet/api/system.management.automation.pstypename) -Elements hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a5480-147">You can also add the `PropertySet` element to the members of the [Type](/dotnet/api/system.management.automation.pstypename) element.</span></span>

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
           <Name>DefaultDisplayPropertySet</Name>
           <ReferencedProperties>
            <Name>Status</Name
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

## <a name="see-also"></a><span data-ttu-id="a5480-148">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a5480-148">See also</span></span>

[<span data-ttu-id="a5480-149">Informationen zu Typen. ps1xml</span><span class="sxs-lookup"><span data-stu-id="a5480-149">About Types.ps1xml</span></span>](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[<span data-ttu-id="a5480-150">System. Management. Automation</span><span class="sxs-lookup"><span data-stu-id="a5480-150">System.Management.Automation</span></span>](/dotnet/api/System.Management.Automation)

[<span data-ttu-id="a5480-151">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="a5480-151">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
