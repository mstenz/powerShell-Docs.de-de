---
title: Erweitern von Eigenschaften für Objekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: dcab755f565cd176c85ef6b9c719bceae10301b4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854526"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="b4718-102">Erweitern Objekteigenschaften</span><span class="sxs-lookup"><span data-stu-id="b4718-102">Extending Properties for Objects</span></span>

<span data-ttu-id="b4718-103">Wenn Sie .NET Framework-Objekten erweitern, können Sie die Eigenschaften, Codeeigenschaften, Note-Eigenschaften, Skripteigenschaften und Eigenschaftensätze alias für die Objekte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b4718-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="b4718-104">Der XML-Code, die zum Definieren der Eigenschaften verwendet wird, wird in den folgenden Abschnitten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b4718-104">The XML that is used to define these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="b4718-105">In die Beispielen in den folgenden Abschnitten werden der Standarddatei für die Typen von Types. ps1xml im Installationsverzeichnis von Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="b4718-105">The examples in the following sections are from the default Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="b4718-106">Aliaseigenschaften</span><span class="sxs-lookup"><span data-stu-id="b4718-106">Alias Properties</span></span>

<span data-ttu-id="b4718-107">Eine aliaseigenschaft definiert einen neuen Namen für eine vorhandene Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="b4718-107">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="b4718-108">Im folgenden Beispiel die `Count` Eigenschaft hinzugefügt wird die [System.Array? Displayproperty = Fullname](/dotnet/api/System.Array) Typ.</span><span class="sxs-lookup"><span data-stu-id="b4718-108">In the following example, the `Count` property is added to the [System.Array?Displayproperty=Fullname](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="b4718-109">Die [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) Element definiert die erweiterte Eigenschaft als aliaseigenschaft.</span><span class="sxs-lookup"><span data-stu-id="b4718-109">The [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) element defines the extended property as an alias property.</span></span> <span data-ttu-id="b4718-110">Die [Namen](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) Element gibt den neuen Namen.</span><span class="sxs-lookup"><span data-stu-id="b4718-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the new name.</span></span> <span data-ttu-id="b4718-111">Und der [referencedmembername-Eigenschaft](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) Element gibt an, die vorhandene Eigenschaft, die durch den Alias verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="b4718-111">And, the [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="b4718-112">(Sie können auch hinzufügen der [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) Element auf die Member des der [Elementgruppen](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) Element.)</span><span class="sxs-lookup"><span data-stu-id="b4718-112">(You can also add the [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="b4718-113">Codeeigenschaften</span><span class="sxs-lookup"><span data-stu-id="b4718-113">Code Properties</span></span>

<span data-ttu-id="b4718-114">Eine Eigenschaft verweist auf eine statische Eigenschaft von .NET Framework-Objekt.</span><span class="sxs-lookup"><span data-stu-id="b4718-114">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="b4718-115">Im folgenden Beispiel die `Node` Eigenschaft hinzugefügt wird die [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) Typ.</span><span class="sxs-lookup"><span data-stu-id="b4718-115">In the following example, the `Node` property is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="b4718-116">Die [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) Element definiert die erweiterte Eigenschaft als Eigenschaft Code.</span><span class="sxs-lookup"><span data-stu-id="b4718-116">The [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element defines the extended property as a code property.</span></span> <span data-ttu-id="b4718-117">Die [Namen](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) -Element gibt den Namen der erweiterten Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="b4718-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="b4718-118">Und der [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) -Element definiert die statische Methode, die von der erweiterten Eigenschaft verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="b4718-118">And, the [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="b4718-119">(Sie können auch hinzufügen der [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) Element auf die Member des der [Elementgruppen](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) Element.)</span><span class="sxs-lookup"><span data-stu-id="b4718-119">(You can also add the [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="note-properties"></a><span data-ttu-id="b4718-120">Eigenschaften notieren</span><span class="sxs-lookup"><span data-stu-id="b4718-120">Note Properties</span></span>

<span data-ttu-id="b4718-121">Eine hinweiseigenschaft definiert eine Eigenschaft mit einem statischen Wert an.</span><span class="sxs-lookup"><span data-stu-id="b4718-121">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="b4718-122">Im folgenden Beispiel die `Status` -Eigenschaft (, dessen Wert immer "Success") wurde die [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) Typ.</span><span class="sxs-lookup"><span data-stu-id="b4718-122">In the following example, the `Status` property (whose value is always "Success") is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="b4718-123">Die [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) -Element definiert die erweiterte Eigenschaft als eine hinweiseigenschaft; die [Namen](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) -Element gibt den Namen der erweiterten Eigenschaft; und die [Wert](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) Element Gibt an, der statische Wert der erweiterten Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="b4718-123">The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element defines the extended property as a note property; the [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property; and the [Value](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the static value of the extended property.</span></span> <span data-ttu-id="b4718-124">(Die [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) Element kann auch hinzugefügt werden, auf die Member des der [Elementgruppen](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) Element.)</span><span class="sxs-lookup"><span data-stu-id="b4718-124">(The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element can also be added to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="b4718-125">Skripteigenschaften</span><span class="sxs-lookup"><span data-stu-id="b4718-125">Script Properties</span></span>

<span data-ttu-id="b4718-126">Eine skripteigenschaft definiert eine Eigenschaft, deren Wert die Ausgabe eines Skripts.</span><span class="sxs-lookup"><span data-stu-id="b4718-126">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="b4718-127">Im folgenden Beispiel die `VersionInfo` Eigenschaft hinzugefügt wird die [System.IO.Fileinfo? Displayproperty = Fullname](/dotnet/api/System.IO.FileInfo) Typ.</span><span class="sxs-lookup"><span data-stu-id="b4718-127">In the following example, the `VersionInfo` property is added to the [System.IO.Fileinfo?Displayproperty=Fullname](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="b4718-128">Die [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) -Element definiert die erweiterte Eigenschaft als eine skripteigenschaft.</span><span class="sxs-lookup"><span data-stu-id="b4718-128">The [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element defines the extended property as a script property.</span></span> <span data-ttu-id="b4718-129">Die [Namen](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) -Element gibt den Namen der erweiterten Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="b4718-129">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="b4718-130">Und der [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) Element gibt an, das Skript, das den Wert der Eigenschaft generiert.</span><span class="sxs-lookup"><span data-stu-id="b4718-130">And, the [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the script that generates the property value.</span></span> <span data-ttu-id="b4718-131">(Sie können auch hinzufügen der [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) Element auf die Member des der [Elementgruppen](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) Element.)</span><span class="sxs-lookup"><span data-stu-id="b4718-131">(You can also add the [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="b4718-132">Eigenschaftensätze</span><span class="sxs-lookup"><span data-stu-id="b4718-132">Property Sets</span></span>

<span data-ttu-id="b4718-133">Ein Eigenschaftensatz definiert eine Gruppe von erweiterten Eigenschaften, die durch den Namen des Satzes verwiesen werden kann.</span><span class="sxs-lookup"><span data-stu-id="b4718-133">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span> <span data-ttu-id="b4718-134">Z. B. die `Property` Parameter, der die [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) Cmdlets können angeben, dass eine bestimmte Eigenschaft festlegen, die angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b4718-134">For example, the `Property` parameter of the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet can specify a specific property set to be displayed.</span></span> <span data-ttu-id="b4718-135">Wenn ein Eigenschaftensatz angegeben wird, werden nur die Eigenschaften, die zum Satz gehören angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b4718-135">When a property set is specified, only those properties that belong to the set are displayed.</span></span>
<span data-ttu-id="b4718-136">Ein Eigenschaftensatz definiert eine Gruppe von erweiterten Eigenschaften, die durch den Namen des Satzes verwiesen werden kann.</span><span class="sxs-lookup"><span data-stu-id="b4718-136">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span> <span data-ttu-id="b4718-137">Z. B. die `Property` Parameter, der die [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) Cmdlets können angeben, dass eine bestimmte Eigenschaft festlegen, die angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b4718-137">For example, the `Property` parameter of the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet can specify a specific property set to be displayed.</span></span> <span data-ttu-id="b4718-138">Wenn ein Eigenschaftensatz angegeben wird, werden nur die Eigenschaften, die zum Satz gehören angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b4718-138">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="b4718-139">Es gibt keine Einschränkung für die Anzahl der Eigenschaftensätze, die für ein Objekt definiert werden können.</span><span class="sxs-lookup"><span data-stu-id="b4718-139">There is no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="b4718-140">Jedoch müssen der-Eigenschaft wird verwendet, um die Standardeigenschaften für die Anzeige eines Objekts zu definieren, innerhalb der Elementgruppe PSStandardMembers angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="b4718-140">However, the property sets used to define the default display properties of an object must be specified within the PSStandardMembers member set.</span></span> <span data-ttu-id="b4718-141">In der Datei %% amp;quot;Types.ps1xml%%amp;quot; Typen umfassen die Namen der standardmäßigen Satz DefaultDisplayProperty, DefaultDisplayPropertySet und DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="b4718-141">In the Types.ps1xml types file, the default property set names include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="b4718-142">Alle zusätzlichen Eigenschaftensätze, die Sie für die Elementgruppe PSStandardMembers hinzufügen, werden ignoriert.</span><span class="sxs-lookup"><span data-stu-id="b4718-142">Any additional property sets that you add to the PSStandardMembers member set are ignored.</span></span>

<span data-ttu-id="b4718-143">Im folgenden Beispiel wird DefaultDisplayPropertySet Eigenschaftensatz enthalten hinzugefügt, auf die PSStandardMembers Member der [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) Typ.</span><span class="sxs-lookup"><span data-stu-id="b4718-143">In the following example, the DefaultDisplayPropertySet property set is added to the PSStandardMembers member set of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="b4718-144">Die [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) Element definiert die Gruppe von Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="b4718-144">The [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element defines the group of properties.</span></span> <span data-ttu-id="b4718-145">Die [Namen](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) Element gibt den Namen des Eigenschaftensatzes an.</span><span class="sxs-lookup"><span data-stu-id="b4718-145">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the property set.</span></span> <span data-ttu-id="b4718-146">Und der [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) Element gibt die Eigenschaften des Satzes an.</span><span class="sxs-lookup"><span data-stu-id="b4718-146">And, the [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) element specifies the properties of the set.</span></span> <span data-ttu-id="b4718-147">(Sie können auch hinzufügen der [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) Element, das Mitglied der [Typ](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) Element.)</span><span class="sxs-lookup"><span data-stu-id="b4718-147">(You can also add the [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element to the members of the [Type](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b4718-148">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b4718-148">See Also</span></span>

[<span data-ttu-id="b4718-149">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="b4718-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
