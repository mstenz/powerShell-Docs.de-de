---
title: Erweitern von Ausgabeobjekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068163"
---
# <a name="extending-output-objects"></a><span data-ttu-id="4ca6f-102">Erweitern von Ausgabeobjekten</span><span class="sxs-lookup"><span data-stu-id="4ca6f-102">Extending Output Objects</span></span>

<span data-ttu-id="4ca6f-103">Sie können die .NET Framework-Objekte erweitern, die von Cmdlets, Funktionen und Skripts mithilfe von Typdateien (. ps1xml) zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-103">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="4ca6f-104">Typen-Dateien sind XML-basierte Dateien, mit denen Sie die Eigenschaften und Methoden zu vorhandenen Objekten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-104">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="4ca6f-105">Windows PowerShell bietet z. B. die Types. ps1xml-Datei, die Elemente auf mehrere vorhandene .NET Framework-Objekte hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-105">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="4ca6f-106">Die Types. ps1xml-Datei befindet sich im Installationsverzeichnis von Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="4ca6f-106">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="4ca6f-107">Sie können Ihre eigene Typendatei erweitert diese Objekte oder andere Objekte erweitern erstellen.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-107">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="4ca6f-108">Wenn Sie ein Objekt mithilfe einer Typendatei erweitern, wird jede Instanz des Objekts mit der neuen Elemente erweitert.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-108">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="4ca6f-109">Erweitern Sie den System.Array-Objekt</span><span class="sxs-lookup"><span data-stu-id="4ca6f-109">Extending the System.Array Object</span></span>

<span data-ttu-id="4ca6f-110">Das folgende Beispiel zeigt, wie Windows PowerShell erweitert den [System.Array](/dotnet/api/System.Array) Objekt in der Types. ps1xml-Datei.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-110">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="4ca6f-111">In der Standardeinstellung [System.Array](/dotnet/api/System.Array) Objekte verfügen über eine `Length` -Eigenschaft, die die Anzahl der Objekte im Array auflistet.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-111">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="4ca6f-112">Jedoch, da der Name "Length" die Eigenschaft nicht klar beschreiben, Windows PowerShell fügt die `Count` aliaseigenschaft, die zeigt, an den gleichen Wert wie die `Length` Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-112">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="4ca6f-113">Das folgende XML fügt die `Count` Eigenschaft, um die [System.Array](/dotnet/api/System.Array) Typ.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-113">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

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

<span data-ttu-id="4ca6f-114">Um diese neue aliaseigenschaft anzuzeigen, verwenden eine [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) Befehl auf jedem Array ist, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-114">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="4ca6f-115">Der Befehl gibt die folgenden Ergebnisse zurück.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-115">The command returns the following results.</span></span>
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
<span data-ttu-id="4ca6f-116">Verwenden Sie entweder die `Count` Eigenschaft oder das `Length` Eigenschaft, um zu bestimmen, wie viele Objekte in einem Array sind.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-116">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="4ca6f-117">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="4ca6f-117">For example:</span></span>

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

## <a name="custom-types-files"></a><span data-ttu-id="4ca6f-118">Benutzerdefinierte Typen von Dateien</span><span class="sxs-lookup"><span data-stu-id="4ca6f-118">Custom Types Files</span></span>

<span data-ttu-id="4ca6f-119">Starten Sie zum Erstellen einer benutzerdefinierten Typen-Datei durch Kopieren einer vorhandenen Typendatei.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-119">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="4ca6f-120">Die neue Datei kann einen beliebigen Namen aufweisen, jedoch muss eine. ps1xml-Dateinamenerweiterung.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-120">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="4ca6f-121">Wenn Sie die Datei kopieren, setzen Sie die Datei in einem Verzeichnis, das Windows PowerShell zugegriffen werden kann, aber es sinnvoll ist, platzieren Sie die Dateien im Installationsverzeichnis von Windows PowerShell (`$pshome`) oder in einem Unterverzeichnis des Installationsverzeichnisses.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-121">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="4ca6f-122">Um Ihre eigenen erweiterte Typen in die Datei hinzuzufügen, fügen Sie eine Types-Element für jedes Objekt, das Sie erweitern möchten.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-122">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="4ca6f-123">In den folgenden Themen enthalten Beispiele für.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-123">The following topics provide examples.</span></span>

- <span data-ttu-id="4ca6f-124">Weitere Informationen zum Hinzufügen von Eigenschaften und-Eigenschaftensätzen finden Sie unter [erweiterte Eigenschaften](./extending-properties-for-objects.md)</span><span class="sxs-lookup"><span data-stu-id="4ca6f-124">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="4ca6f-125">Weitere Informationen zum Hinzufügen von Methoden finden Sie unter [erweiterte Methoden](./defining-default-methods-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="4ca6f-125">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="4ca6f-126">Weitere Informationen zum Hinzufügen von Elementgruppen finden Sie unter [Elementgruppen erweiterte](./defining-default-member-sets-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="4ca6f-126">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="4ca6f-127">Nachdem Sie Ihre eigenen erweiterte Typen definieren, verwenden Sie eine der folgenden Methoden, um die erweiterten Objekte verfügbar zu machen:</span><span class="sxs-lookup"><span data-stu-id="4ca6f-127">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="4ca6f-128">Um die erweiterten Typen-Datei mit der aktuellen Sitzung verfügbar zu machen, verwenden Sie die [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) Cmdlet, um die neue Datei hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-128">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="4ca6f-129">Wenn Sie möchten Ihre Typen, die Typen Vorrang vor, die definiert sind Typen andere Dateien (einschließlich der Types. ps1xml-Datei), verwenden Sie die `PrependData` Parameter, der die [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-129">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="4ca6f-130">Um die erweiterten Typen-Datei in alle zukünftigen Sitzungen verfügbar zu machen, fügen Sie die Typendatei auf ein Modul, exportieren Sie die aktuelle Sitzung oder Hinzufügen der [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) -Befehl zu Ihrem Windows PowerShell-Profil.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-130">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="4ca6f-131">Signieren von Dateien von Typen</span><span class="sxs-lookup"><span data-stu-id="4ca6f-131">Signing Types Files</span></span>

<span data-ttu-id="4ca6f-132">Typdateien müssen digital signiert werden, um zu verhindern, Manipulation, da der XML-Code Skriptblöcke enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="4ca6f-132">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="4ca6f-133">Weitere Informationen zum Hinzufügen von digitaler Signatures finden Sie unter [About_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="4ca6f-133">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="4ca6f-134">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4ca6f-134">See Also</span></span>

[<span data-ttu-id="4ca6f-135">Definieren von Standardeigenschaften für Objekte</span><span class="sxs-lookup"><span data-stu-id="4ca6f-135">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="4ca6f-136">Definieren von standardmäßigen Methoden für Objekte</span><span class="sxs-lookup"><span data-stu-id="4ca6f-136">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="4ca6f-137">Definieren von Elementgruppen Standard für Objekte</span><span class="sxs-lookup"><span data-stu-id="4ca6f-137">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="4ca6f-138">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="4ca6f-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
