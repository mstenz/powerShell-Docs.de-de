---
title: Erweitern von Ausgabe Objekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 12a826363221b8a7ce06245c787a7bd0529e42f8
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83690898"
---
# <a name="extending-output-objects"></a><span data-ttu-id="07174-102">Erweitern von Ausgabeobjekten</span><span class="sxs-lookup"><span data-stu-id="07174-102">Extending Output Objects</span></span>

<span data-ttu-id="07174-103">Sie können die .NET Framework Objekte, die von Cmdlets, Funktionen und Skripts zurückgegeben werden, mithilfe von Typen Dateien (. ps1xml) erweitern.</span><span class="sxs-lookup"><span data-stu-id="07174-103">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="07174-104">Typen Dateien sind XML-basierte Dateien, mit denen Sie vorhandenen Objekten Eigenschaften und Methoden hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="07174-104">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="07174-105">Windows PowerShell stellt z. b. die Datei Types. ps1xml bereit, die mehreren vorhandenen .NET Framework Objekten Elemente hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="07174-105">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="07174-106">Die Datei Types. ps1xml befindet sich im Windows PowerShell-Installationsverzeichnis ( `$pshome` ).</span><span class="sxs-lookup"><span data-stu-id="07174-106">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="07174-107">Sie können Ihre eigene Typen Datei erstellen, um diese Objekte weiter zu erweitern oder andere Objekte zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="07174-107">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="07174-108">Wenn Sie ein Objekt mithilfe einer Typen Datei erweitern, wird jede Instanz des Objekts mit den neuen Elementen erweitert.</span><span class="sxs-lookup"><span data-stu-id="07174-108">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="07174-109">Erweitern des System. Array-Objekts</span><span class="sxs-lookup"><span data-stu-id="07174-109">Extending the System.Array Object</span></span>

<span data-ttu-id="07174-110">Das folgende Beispiel zeigt, wie Windows PowerShell das [System. Array](/dotnet/api/System.Array) -Objekt in der Datei Types. ps1xml erweitert.</span><span class="sxs-lookup"><span data-stu-id="07174-110">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="07174-111">Standardmäßig verfügen [System. Array](/dotnet/api/System.Array) -Objekte über eine `Length` Eigenschaft, die die Anzahl der Objekte im Array auflistet.</span><span class="sxs-lookup"><span data-stu-id="07174-111">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="07174-112">Da der Name "length" die Eigenschaft jedoch nicht eindeutig beschreibt, fügt Windows PowerShell die Alias- `Count` Eigenschaft hinzu, die denselben Wert wie die Eigenschaft anzeigt `Length` .</span><span class="sxs-lookup"><span data-stu-id="07174-112">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="07174-113">Im folgenden XML-Code wird die- `Count` Eigenschaft dem [System. Array](/dotnet/api/System.Array) -Typ hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="07174-113">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

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

<span data-ttu-id="07174-114">Um diese neue Alias Eigenschaft anzuzeigen, verwenden [Sie einen Get-Member-](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) Befehl für ein beliebiges Array, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="07174-114">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="07174-115">Der Befehl gibt die folgenden Ergebnisse zurück.</span><span class="sxs-lookup"><span data-stu-id="07174-115">The command returns the following results.</span></span>

```output
Name           MemberType    Definition
----           ----------    ----------
Count          AliasProperty Count = Length
Address        Method        System.Object& Address(Int32 )
Clone          Method        System.Object Clone()
CopyTo         Method        System.Void CopyTo(Array array, Int32 index):
Equals         Method        System.Boolean Equals(Object obj)
Get            Method        System.Object Get(Int32 )
...
Length         Property      System.Int32 Length {get;}
```

<span data-ttu-id="07174-116">Sie können entweder die- `Count` Eigenschaft oder die- `Length` Eigenschaft verwenden, um zu bestimmen, wie viele Objekte in einem Array sind.</span><span class="sxs-lookup"><span data-stu-id="07174-116">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="07174-117">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="07174-117">For example:</span></span>

```powershell
PS> (1, 2, 3, 4).Count
```

```output
4
```

```powershell
PS> (1, 2, 3, 4).Length
```

```output
4
```

## <a name="custom-types-files"></a><span data-ttu-id="07174-118">Benutzerdefinierte Typen Dateien</span><span class="sxs-lookup"><span data-stu-id="07174-118">Custom Types Files</span></span>

<span data-ttu-id="07174-119">Wenn Sie eine benutzerdefinierte Typen Datei erstellen möchten, kopieren Sie zunächst eine vorhandene Typen Datei.</span><span class="sxs-lookup"><span data-stu-id="07174-119">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="07174-120">Die neue Datei kann einen beliebigen Namen haben, Sie muss jedoch über die Dateinamenerweiterung. ps1xml verfügen.</span><span class="sxs-lookup"><span data-stu-id="07174-120">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="07174-121">Wenn Sie die Datei kopieren, können Sie die neue Datei in einem beliebigen Verzeichnis platzieren, das für Windows PowerShell zugänglich ist, aber es ist hilfreich, die Dateien im Windows PowerShell-Installationsverzeichnis ( `$pshome` ) oder in einem Unterverzeichnis des-Installationsverzeichnisses zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="07174-121">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="07174-122">Fügen Sie für jedes Objekt, das Sie erweitern möchten, ein Types-Element hinzu, um der Datei eigene erweiterte Typen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="07174-122">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="07174-123">In den folgenden Themen werden Beispiele bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="07174-123">The following topics provide examples.</span></span>

- <span data-ttu-id="07174-124">Weitere Informationen zum Hinzufügen von Eigenschaften und Eigenschafts Sätzen finden Sie unter [Erweiterte Eigenschaften](./extending-properties-for-objects.md) .</span><span class="sxs-lookup"><span data-stu-id="07174-124">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="07174-125">Weitere Informationen zum Hinzufügen von Methoden finden Sie unter [Erweiterte Methoden](./defining-default-methods-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="07174-125">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="07174-126">Weitere Informationen zum Hinzufügen von Element Sätzen finden Sie unter [Erweiterte Element Sätze](./defining-default-member-sets-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="07174-126">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="07174-127">Nachdem Sie Ihre eigenen erweiterten Typen definiert haben, verwenden Sie eine der folgenden Methoden, um die erweiterten Objekte verfügbar zu machen:</span><span class="sxs-lookup"><span data-stu-id="07174-127">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="07174-128">Verwenden Sie das [Update-typedata-](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) Cmdlet, um die Datei mit erweiterten Typen für die aktuelle Sitzung verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="07174-128">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="07174-129">Wenn Sie möchten, dass Ihre Typen Vorrang vor den Typen haben, die in anderen Typen Dateien (einschließlich der Types. ps1xml-Datei) definiert sind, verwenden Sie den- `PrependData` Parameter des [Update-typedata-](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="07174-129">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="07174-130">Um die Datei mit erweiterten Typen für alle zukünftigen Sitzungen verfügbar zu machen, fügen Sie die Typdatei einem Modul hinzu, exportieren die aktuelle Sitzung oder fügen den [Update-typedata-](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) Befehl zu Ihrem Windows PowerShell-Profil hinzu.</span><span class="sxs-lookup"><span data-stu-id="07174-130">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="07174-131">Signierungs Typen Dateien</span><span class="sxs-lookup"><span data-stu-id="07174-131">Signing Types Files</span></span>

<span data-ttu-id="07174-132">Typen Dateien sollten digital signiert werden, um Manipulationen zu verhindern, da XML Skriptblöcke enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="07174-132">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="07174-133">Weitere Informationen zum Hinzufügen digitaler Signaturen finden Sie unter [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="07174-133">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="07174-134">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="07174-134">See Also</span></span>

[<span data-ttu-id="07174-135">Definieren von Standardeigenschaften für Objekte</span><span class="sxs-lookup"><span data-stu-id="07174-135">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="07174-136">Definieren von Standardmethoden für Objekte</span><span class="sxs-lookup"><span data-stu-id="07174-136">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="07174-137">Definieren von Standardelementgruppen für Objekte</span><span class="sxs-lookup"><span data-stu-id="07174-137">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="07174-138">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="07174-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
