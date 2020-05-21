---
title: Öffentliches Ressourcen Schema | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: 52244ee7496b99e11f0306e93728736fc9c51be5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564702"
---
# <a name="public-resource-schema"></a><span data-ttu-id="dc875-102">Schema für öffentliche Ressourcen</span><span class="sxs-lookup"><span data-stu-id="dc875-102">Public Resource Schema</span></span>

<span data-ttu-id="dc875-103">Management odata verwendet MOF, um Ressourcen und deren Eigenschaften zu definieren.</span><span class="sxs-lookup"><span data-stu-id="dc875-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="dc875-104">Die Eigenschaften einer odata-Entität vom Typ "Management" entsprechen direkt den Eigenschaften des verwalteten Typs, der vom zugrunde liegenden Cmdlet zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="dc875-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="dc875-105">Definieren einer Ressource</span><span class="sxs-lookup"><span data-stu-id="dc875-105">Defining a resource</span></span>

<span data-ttu-id="dc875-106">Jede Ressource entspricht einem Objekt, das von einem Windows PowerShell-Cmdlet zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="dc875-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="dc875-107">In der MOF-Datei der öffentlichen Ressource definieren Sie eine Ressource, indem Sie eine Klasse deklarieren.</span><span class="sxs-lookup"><span data-stu-id="dc875-107">In the public resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="dc875-108">Die-Klasse besteht aus Eigenschaften, die den Eigenschaften des-Objekts entsprechen.</span><span class="sxs-lookup"><span data-stu-id="dc875-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="dc875-109">Beispielsweise wird im folgenden Beispiel die [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Klasse durch den folgenden MOF dargestellt.</span><span class="sxs-lookup"><span data-stu-id="dc875-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

```csharp
class PswsTest_Process
{
    [Key] SInt32 Id;
    [Required] SInt32 BasePriority;
    [Required] SInt32 HandleCount;
    [Required] string MachineName;
    [Required] SInt32 MainWindowHandle;

    ...
};
```

<span data-ttu-id="dc875-110">Jedem Eigenschaftsnamen wird ein Datentyp vorangestellt.</span><span class="sxs-lookup"><span data-stu-id="dc875-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="dc875-111">Die Datentypen in diesem Beispiel entsprechen primitiven CLR-Datentypen in den .NET-Frameworks, aber Eigenschaften können auch Verweise auf andere Ressourcen oder komplexe Typen sein, die beide später beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="dc875-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="dc875-112">Der `Key` Qualifizierer gibt an, dass eine Eigenschaft zur eindeutigen Identifizierung einer Ressourcen Instanz verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="dc875-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="dc875-113">Eine Ressource kann über mehr als einen Schlüssel verfügen.</span><span class="sxs-lookup"><span data-stu-id="dc875-113">A resource can have more than one key.</span></span>

<span data-ttu-id="dc875-114">Der `Required` Qualifizierer gibt an, dass die Eigenschaft erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="dc875-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="dc875-115">Wenn eine Eigenschaft mit dem Qualifizierer gekennzeichnet ist `Key` , wird Sie als erforderlich angesehen, und der `Required` Qualifizierer ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="dc875-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="dc875-116">Komplexe Datentypen</span><span class="sxs-lookup"><span data-stu-id="dc875-116">Complex data types</span></span>

<span data-ttu-id="dc875-117">Eigenschaften von Entitäten können komplexe Datentypen aufweisen.</span><span class="sxs-lookup"><span data-stu-id="dc875-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="dc875-118">Komplexe Datentypen sind Typen, die aus anderen Typen bestehen, ähnlich wie Strukturen in der Programmiersprache C.</span><span class="sxs-lookup"><span data-stu-id="dc875-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="dc875-119">Ein komplexer Typ wird in der MOF-Datei als Klasse mit dem `ComplexType` Qualifizierer deklariert, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="dc875-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="dc875-120">Um eine Entitäts Eigenschaft als komplexen Typ zu deklarieren, deklarieren Sie Sie als `string` Typ mit dem `EmbeddedInstance` Qualifizierer, einschließlich des Namens des komplexen Typs.</span><span class="sxs-lookup"><span data-stu-id="dc875-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="dc875-121">Das folgende Beispiel zeigt die Deklaration einer Eigenschaft des `PswsTest_ProcessModule` im vorherigen Beispiel deklarierten Typs.</span><span class="sxs-lookup"><span data-stu-id="dc875-121">The following example shows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="dc875-122">Zuordnen von Entitäten</span><span class="sxs-lookup"><span data-stu-id="dc875-122">Associating entities</span></span>

<span data-ttu-id="dc875-123">Sie können zwei Entitäten mithilfe der Qualifizierer Association und associationclass verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="dc875-123">You can associate two entities by using the Association and AssociationClass qualifiers.</span></span> <span data-ttu-id="dc875-124">Weitere Informationen finden Sie unter [Zuordnen von Verwaltungs-odata-Entitäten](./associating-management-odata-entities.md).</span><span class="sxs-lookup"><span data-stu-id="dc875-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="dc875-125">Abgeleitete Typen</span><span class="sxs-lookup"><span data-stu-id="dc875-125">Derived types</span></span>

<span data-ttu-id="dc875-126">Sie können einen Typ von einem anderen Typ ableiten.</span><span class="sxs-lookup"><span data-stu-id="dc875-126">You can derive a type from another type.</span></span> <span data-ttu-id="dc875-127">Der abgeleitete Typ erbt alle Eigenschaften des Typs, von dem er abgeleitet wurde, zusätzlich zu den explizit abgeleiteten Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="dc875-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="dc875-128">Das folgende Beispiel zeigt eine Typdeklaration und dann eine Deklaration zweier Typen, die von diesem Typ abgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="dc875-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

```csharp
Class Product {

    [Key] String ProductName;

};

Class DairyProduct : Product {

    Uint16 PercentFat;
};
Class POPProduct : Product {

    Boolean IsCarbonated;
};
```
