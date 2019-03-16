---
title: Öffentliche Ressourcenschema | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057245"
---
# <a name="public-resource-schema"></a><span data-ttu-id="681da-102">Schema für öffentliche Ressourcen</span><span class="sxs-lookup"><span data-stu-id="681da-102">Public Resource Schema</span></span>

<span data-ttu-id="681da-103">Management OData verwendet MOF, um Ressourcen und deren Eigenschaften zu definieren.</span><span class="sxs-lookup"><span data-stu-id="681da-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="681da-104">Die Eigenschaften einer Management OData-Entität entsprechen direkt auf die Eigenschaften des verwalteten Typs, von dem zugrunde liegenden Cmdlet zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="681da-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="681da-105">Definieren eine Ressource</span><span class="sxs-lookup"><span data-stu-id="681da-105">Defining a resource</span></span>

<span data-ttu-id="681da-106">Jede Ressource entspricht ein durch ein Windows PowerShell-Cmdlet zurückgegebenes Objekt.</span><span class="sxs-lookup"><span data-stu-id="681da-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="681da-107">In der öffentlichen Ressource MOF-Datei definieren Sie eine Ressource durch Deklarieren einer Klasse.</span><span class="sxs-lookup"><span data-stu-id="681da-107">In the public resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="681da-108">Die Klasse besteht aus Eigenschaften, die die Eigenschaften des Objekts entsprechen.</span><span class="sxs-lookup"><span data-stu-id="681da-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="681da-109">Im folgenden Beispiel, z. B. die ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Klasse wird durch die folgende MOF-Datei dargestellt.</span><span class="sxs-lookup"><span data-stu-id="681da-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

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

<span data-ttu-id="681da-110">Jeder Eigenschaftsname ist ein Datentyp vorangestellt.</span><span class="sxs-lookup"><span data-stu-id="681da-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="681da-111">Primitive CLR-Datentypen in den .NET Frameworks-entsprechen die Datentypen in diesem Beispiel können, aber Eigenschaften auch Verweise auf andere Ressourcen oder komplexe Typen, die beide weiter unten beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="681da-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="681da-112">Die `Key` Qualifizierer gibt an, dass eine Eigenschaft verwendet wird, um eine Ressourceninstanz eindeutig zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="681da-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="681da-113">Eine Ressource kann mehr als ein Schlüssel aufweisen.</span><span class="sxs-lookup"><span data-stu-id="681da-113">A resource can have more than one key.</span></span>

<span data-ttu-id="681da-114">Die `Required` Qualifizierer gibt an, dass die Eigenschaft erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="681da-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="681da-115">Wenn eine Eigenschaft mit mit der Bezeichnung der `Key` Qualifizierer, gilt dies erforderlich und die `Required` Qualifizierer ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="681da-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="681da-116">Komplexe Datentypen</span><span class="sxs-lookup"><span data-stu-id="681da-116">Complex data types</span></span>

<span data-ttu-id="681da-117">Eigenschaften von Entitäten können komplexe Datentypen haben.</span><span class="sxs-lookup"><span data-stu-id="681da-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="681da-118">Komplexe Datentypen sind Typen, die aus anderen Typen wie Strukturen in der Programmiersprache C bestehen.</span><span class="sxs-lookup"><span data-stu-id="681da-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="681da-119">Ein komplexer Typ ist als eine Klasse mit in die MOF-Datei deklariert die `ComplexType` Qualifizierer, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="681da-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="681da-120">Um eine Entitätseigenschaft als komplexer Typ deklarieren zu können, deklarieren Sie ihn als einen `string` Geben Sie mit der `EmbeddedInstance` Qualifizierer, einschließlich des Namens des komplexen Typs.</span><span class="sxs-lookup"><span data-stu-id="681da-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="681da-121">Das folgende Beispiel zeigt die Deklaration einer Eigenschaft der `PswsTest_ProcessModule` Typ deklariert wird, im vorherigen Beispiel.</span><span class="sxs-lookup"><span data-stu-id="681da-121">The following example shows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="681da-122">Zuordnen von Entitäten</span><span class="sxs-lookup"><span data-stu-id="681da-122">Associating entities</span></span>

<span data-ttu-id="681da-123">Sie können zwei Entitäten zuordnen, indem Sie die Zuordnung und Assoziationsklasse Qualifizierer verwenden.</span><span class="sxs-lookup"><span data-stu-id="681da-123">You can associate two entities by using the Association and AssociationClass qualifiers.</span></span> <span data-ttu-id="681da-124">Weitere Informationen finden Sie unter [Management OData-Entitäten zuordnen](./associating-management-odata-entities.md).</span><span class="sxs-lookup"><span data-stu-id="681da-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="681da-125">Abgeleitete Typen</span><span class="sxs-lookup"><span data-stu-id="681da-125">Derived types</span></span>

<span data-ttu-id="681da-126">Sie können einen Typ von einem anderen Typ ableiten.</span><span class="sxs-lookup"><span data-stu-id="681da-126">You can derive a type from another type.</span></span> <span data-ttu-id="681da-127">Der abgeleitete Typ erbt alle Eigenschaften des Typs, von dem er sowie auf alle Eigenschaften, die explizit abgeleitet abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="681da-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="681da-128">Das folgende Beispiel zeigt eine Typdeklaration, und klicken Sie dann eine Deklaration von zwei Typen, die von diesem Typ abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="681da-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

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