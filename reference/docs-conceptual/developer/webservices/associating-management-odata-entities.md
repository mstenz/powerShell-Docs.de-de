---
title: Zuordnen von Verwaltungs-odata-Entitäten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 4849735bf412497f5590b109c67760b6a197cb2b
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561728"
---
# <a name="associating-management-odata-entities"></a><span data-ttu-id="0646c-102">Zuordnen von Management OData-Entitäten</span><span class="sxs-lookup"><span data-stu-id="0646c-102">Associating Management OData Entities</span></span>

<span data-ttu-id="0646c-103">Es ist oft hilfreich, eine Zuordnung zwischen zwei verschiedenen odata-Verwaltungs Entitäten zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="0646c-103">It is often useful to create an association between two different Management OData entities.</span></span> <span data-ttu-id="0646c-104">Ein Verwaltungs-odata-Dienst könnte z. b. über Entitäten verfügen, die einen Produktkatalog verwalten, der in Kategorien organisiert ist, und die Entitäten `Product` und definieren `Category` .</span><span class="sxs-lookup"><span data-stu-id="0646c-104">For example, a Management OData service could have entities that manage a catalogue of products that are organized in categories, and define the entities `Product` and `Category`.</span></span> <span data-ttu-id="0646c-105">Wenn Sie diese beiden Entitäten zuordnen, kann ein Client Informationen zu allen Produkten in einer Kategorie mit einer einzelnen Anforderung an den Webdienst erhalten.</span><span class="sxs-lookup"><span data-stu-id="0646c-105">By associating these two entities, a client can get information about all of the products in a category with a single request to the web service.</span></span>

<span data-ttu-id="0646c-106">Ein Beispiel, das zeigt, wie Zuordnungen zwischen Entitäten erstellt werden können, finden Sie unter [Association Sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span><span class="sxs-lookup"><span data-stu-id="0646c-106">A sample that shows how to create associations between entities can be downloaded at [Association sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span></span>

## <a name="creating-the-association-in-the-resource-schema-file"></a><span data-ttu-id="0646c-107">Erstellen der Zuordnung in der Ressourcen Schema Datei</span><span class="sxs-lookup"><span data-stu-id="0646c-107">Creating the Association in the resource schema file</span></span>

<span data-ttu-id="0646c-108">Die folgende MOF definiert zwei Entitäten.</span><span class="sxs-lookup"><span data-stu-id="0646c-108">The following MOF defines two entities.</span></span> <span data-ttu-id="0646c-109">Wir erstellen eine Verknüpfung zwischen Ihnen.</span><span class="sxs-lookup"><span data-stu-id="0646c-109">We will create an association between them.</span></span>

```csharp
class Product {

[key] string ProductName;

// other fields ...
};

class Category {

[key] string CategoryName;

string Products[];

// other fields
}
```

<span data-ttu-id="0646c-110">Die- `Category` Klasse definiert eine Eigenschaft, bei der es sich um ein Array mit den Namen der Produkte handelt, die zu dieser Kategorie gehören.</span><span class="sxs-lookup"><span data-stu-id="0646c-110">The `Category` class defines a property that is an array of the names of the products that belong to that category.</span></span>

<span data-ttu-id="0646c-111">Um zwei Entitäten zuzuordnen, müssen Sie eine Klasse mit dem- `Association` Attribut in der MOF-Datei des Ressourcen Schemas für den Dienst definieren.</span><span class="sxs-lookup"><span data-stu-id="0646c-111">To associate two entities, you must define a class with the `Association` attribute in the resource schema MOF file for the service.</span></span> <span data-ttu-id="0646c-112">Die-Klasse muss die beiden zu zugeordneten Entitäten definieren, die als Zuordnung bezeichnet werden `ends` .</span><span class="sxs-lookup"><span data-stu-id="0646c-112">The class must define the two entities to be associated, called `ends` of the association.</span></span> <span data-ttu-id="0646c-113">Das folgende Beispiel zeigt eine Definition einer Klasse, die eine Zuordnung zwischen den Entitäten "Category" und "Products" definiert.</span><span class="sxs-lookup"><span data-stu-id="0646c-113">The following example shows a definition of a class that defines an association between the Category and Products entities.</span></span>

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

<span data-ttu-id="0646c-114">Außerdem müssen Sie die Deklaration der Products-Eigenschaft in der Category-Klasse ändern.</span><span class="sxs-lookup"><span data-stu-id="0646c-114">You must also change the declaration of the Products property in the Category class.</span></span> <span data-ttu-id="0646c-115">Verwenden Sie das- `AssociationClass` Schlüsselwort, um anzugeben, dass die Eigenschaft ein Ende der Zuordnung ist.</span><span class="sxs-lookup"><span data-stu-id="0646c-115">You use the `AssociationClass` keyword to specify that the property is one end of the association.</span></span> <span data-ttu-id="0646c-116">Die-Eigenschaft muss auch als Verweis auf eine separate Entität anstelle eines Arrays von Zeichen folgen definiert werden.</span><span class="sxs-lookup"><span data-stu-id="0646c-116">The property must also be defined as a reference to a separate entity, rather than an array of strings.</span></span> <span data-ttu-id="0646c-117">Verwenden Sie hierzu das- `ref` Schlüsselwort.</span><span class="sxs-lookup"><span data-stu-id="0646c-117">You do this by using the `ref` keyword.</span></span> <span data-ttu-id="0646c-118">Das folgende Beispiel zeigt die Eigenschaften Definition für die Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="0646c-118">The following example shows the property definition for the association.</span></span>

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

<span data-ttu-id="0646c-119">Schließlich müssen Sie das andere Ende der Zuordnung deklarieren, indem Sie der Klasse eine Eigenschafts Definition hinzufügen `Product` .</span><span class="sxs-lookup"><span data-stu-id="0646c-119">Finally, you must declare the other end of the association by adding a property definition to the `Product` class.</span></span> <span data-ttu-id="0646c-120">Dabei handelt es sich um einen Verweis auf ein Array oder eine einzelne Entität.</span><span class="sxs-lookup"><span data-stu-id="0646c-120">This is a reference to either an array or to a single entity.</span></span> <span data-ttu-id="0646c-121">Angenommen, jedes Produkt gehört nur zu einer Kategorie, die Definition sieht wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="0646c-121">Assuming that each product belongs to only one category, the definition would be as follows.</span></span>

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

<span data-ttu-id="0646c-122">Die Eigenschaften, die die beiden Enden der Zuordnung darstellen, werden als Navigations Eigenschaften bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="0646c-122">The properties that represent the two ends of the association are called navigation properties.</span></span>

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a><span data-ttu-id="0646c-123">Schritte zum Zuordnen von Entitäten in der Ressourcen Schema Datei</span><span class="sxs-lookup"><span data-stu-id="0646c-123">Steps for associating entities in the resource schema file</span></span>

- <span data-ttu-id="0646c-124">Definieren Sie die Zuordnung als Klasse, indem Sie das- `Association` Schlüsselwort verwenden.</span><span class="sxs-lookup"><span data-stu-id="0646c-124">Define the association as a class by using the `Association` keyword.</span></span>

- <span data-ttu-id="0646c-125">Definieren Sie die Enden der Zuordnung, indem Sie das associationclass-Schlüsselwort verwenden, um die Eigenschaften der zugeordneten Entitäten zu qualifizieren.</span><span class="sxs-lookup"><span data-stu-id="0646c-125">Define the ends of the association by using the AssociationClass keyword to qualify properties of the associated entities.</span></span>

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a><span data-ttu-id="0646c-126">Erstellen der Zuordnung in der XML-Datei der Ressourcen Zuordnung</span><span class="sxs-lookup"><span data-stu-id="0646c-126">Creating the association in the resource mapping XML file</span></span>

<span data-ttu-id="0646c-127">Beim Zuordnen einer Zuordnung in der XML-Datei der Ressourcen Zuordnung müssen drei verschiedene Fälle berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="0646c-127">There are three different cases to consider when mapping an association in the resource mapping XML file.</span></span>

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a><span data-ttu-id="0646c-128">Festlegen der Zuordnung von Entitäten in der Ressourcen Zuordnungs Datei</span><span class="sxs-lookup"><span data-stu-id="0646c-128">Determining how to associate entities in the resource mapping file</span></span>

- <span data-ttu-id="0646c-129">, Wenn die Navigations Eigenschaft im zugrunde liegenden vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="0646c-129">If the navigation property is present in the underlying.</span></span> <span data-ttu-id="0646c-130">.NET Framework Typ, und diese Eigenschaft enthält Fremdschlüssel, ist keine explizite Zuordnung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="0646c-130">.NET Framework type, and that property contains foreign keys, no explicit mapping is necessary.</span></span>

- <span data-ttu-id="0646c-131">Wenn die Navigations Eigenschaft nicht im zugrunde liegenden .NET Framework Typ vorhanden ist, müssen Sie ein Cmdlet angeben, das die Liste der Schlüssel der zugeordneten Instanzen abruft.</span><span class="sxs-lookup"><span data-stu-id="0646c-131">If the navigation property does not exist in the underlying .NET Framework type, you must specify a cmdlet that retrieves the list of keys of the associated instances.</span></span> <span data-ttu-id="0646c-132">Hierzu fügen Sie ein Element hinzu `Association` , das unter dem-Element unter dem- `CmdletImplementation` Element enthalten ist. Befolgen Sie dabei die Elemente, die `cmdlets` für die anderen CRUD-Befehle definieren.</span><span class="sxs-lookup"><span data-stu-id="0646c-132">You do this by adding an `Association` element nested under the `CmdletImplementation` element, following the elements that define the `cmdlets` for the other CRUD commands.</span></span>

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- <span data-ttu-id="0646c-133">Wenn die Navigations Eigenschaft im zugrunde liegenden .NET Framework-Typ vorhanden ist, aber anstelle von Fremdschlüsseln Objektinstanzen enthält, müssen Sie ein Cmdlet (durch Schreiben einer Windows PowerShell-Funktion oder eines Windows PowerShell-Skripts) erstellen, um die Fremdschlüssel abzurufen.</span><span class="sxs-lookup"><span data-stu-id="0646c-133">If the navigation property does exist in the underlying .NET Framework type, but it contains object instances instead of foreign keys, then you must create a cmdlet (by writing a Windows PowerShell function or script) to retrieve the foreign keys.</span></span> <span data-ttu-id="0646c-134">Anschließend geben Sie dieses Cmdlet in der Ressourcen Mapping-Datei an.</span><span class="sxs-lookup"><span data-stu-id="0646c-134">You then specify that cmdlet in the resource mapping file.</span></span> <span data-ttu-id="0646c-135">Beispielsweise würde das Skript zum Abrufen der Schlüssel wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="0646c-135">For example, the script to retrieve the keys would look like the following.</span></span>

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  <span data-ttu-id="0646c-136">Die XML-Datei in der Ressourcen Zuordnung würde wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="0646c-136">And the XML in the resource mapping file would look like the following.</span></span>

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory.ps1</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- <span data-ttu-id="0646c-137">Zusätzlich zur Angabe eines Cmdlets zum Abrufen der zugeordneten Entitäten können Sie auch Cmdlets zum Hinzufügen und Entfernen von verweisen aus der Sammlung angeben.</span><span class="sxs-lookup"><span data-stu-id="0646c-137">In addition to specifying a cmdlet to retrieve the associated entities, you can also specify cmdlets to add and remove references from the collection.</span></span> <span data-ttu-id="0646c-138">Im folgenden Beispiel wird davon ausgegangen, dass die Cmdlets "Add-productdecategory" und "Remove-productfromcategory" vorhanden sind (Sie können auch in einem Skript oder einer Funktion definiert werden, wie im vorherigen Beispiel gezeigt).</span><span class="sxs-lookup"><span data-stu-id="0646c-138">The following example assumes that the Add-ProductToCategory and Remove-ProductFromCategory cmdlets exist (they can also be defined in a script or function as in the previous example).</span></span>

  ```xml
  Class Name="Sample.Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
  ...
              </GetReference>
        <AddReference>
     <CmdletName>"Add-ProductToCategory"</>
     <ParameterForThisObject>"Product"</>
     <ParameterForReferredObject>"Category"</>
        </AddReference>
        <RemoveReference>
     <CmdletName="Remove-ProductFromCategory"/>
     <ParameterForThisObject >"Product"</>
     <ParameterForReferredObject >"Category"</>
        </RemoveReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

## <a name="querying-associated-entities"></a><span data-ttu-id="0646c-139">Abfragen von zugeordneten Entitäten</span><span class="sxs-lookup"><span data-stu-id="0646c-139">Querying associated entities</span></span>

<span data-ttu-id="0646c-140">Der Client kann eine Liste der Instanzen abrufen, die einer Entität zugeordnet sind, indem bestimmte Abfragen erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="0646c-140">The client can retrieve a list of the instances associated with an entity by creating specific queries.</span></span>

#### <a name="constructing-queries-for-associated-entities"></a><span data-ttu-id="0646c-141">Erstellen von Abfragen für zugehörige Entitäten</span><span class="sxs-lookup"><span data-stu-id="0646c-141">Constructing queries for associated entities</span></span>

- <span data-ttu-id="0646c-142">Ein Client kann die Details einer Kategorie anfordern, ohne die zugehörigen Produkte abzurufen.</span><span class="sxs-lookup"><span data-stu-id="0646c-142">A client can request the details of a category without retrieving its associated products.</span></span> <span data-ttu-id="0646c-143">Beispielsweise ruft die folgende Anforderung Details der Kategorie ab `food` .</span><span class="sxs-lookup"><span data-stu-id="0646c-143">For example, the following request gets details of the `food` category.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  <span data-ttu-id="0646c-144">Um die zugeordneten Produkte der Kategorie zu erhalten (aber keine Details der Kategorie selbst), gibt der Client die Navigations Eigenschaft in der Anforderung an.</span><span class="sxs-lookup"><span data-stu-id="0646c-144">To get the associated products of the category (but not details of the category itself, the client specifies the navigation property in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- <span data-ttu-id="0646c-145">Um nur URLs der Produkte abzurufen, verwenden Sie den `$links` Qualifizierer in der Anforderung.</span><span class="sxs-lookup"><span data-stu-id="0646c-145">To retrieve only URLs of the products, use the `$links` qualifier in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- <span data-ttu-id="0646c-146">Der Client kann die Kategoriedetails und die dazugehörigen Produkte mithilfe des- `$expand` Qualifizierers erhalten.</span><span class="sxs-lookup"><span data-stu-id="0646c-146">The client can get both the category details and its associated products by using the `$expand` qualifier.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a><span data-ttu-id="0646c-147">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0646c-147">See Also</span></span>

[<span data-ttu-id="0646c-148">Erstellen eines Webdiensts für die Verwaltung von odata IIS-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="0646c-148">Creating a Management OData IIS Extension Web Service</span></span>](./creating-a-management-odata-web-service.md)
