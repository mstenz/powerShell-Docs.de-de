---
title: Zuordnen von Management OData-Entitäten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 44b718e024eb98ac562edb50076287a31f5edc6b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860826"
---
# <a name="associating-management-odata-entities"></a><span data-ttu-id="2e0e1-102">Zuordnen von Management OData-Entitäten</span><span class="sxs-lookup"><span data-stu-id="2e0e1-102">Associating Management OData Entities</span></span>

<span data-ttu-id="2e0e1-103">Es ist häufig nützlich, um eine Zuordnung zwischen zwei verschiedenen Management OData-Entitäten erstellen.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-103">It is often useful to create an association between two different Management OData entities.</span></span> <span data-ttu-id="2e0e1-104">Z. B. ein Management OData-Dienst haben Sie die Entitäten, die einen Katalog von Produkten zu verwalten, die in Kategorien organisiert werden konnte, und definieren Sie die Entitäten `Product` und `Category`.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-104">For example, a Management OData service could have entities that manage a catalogue of products that are organized in categories, and define the entities `Product` and `Category`.</span></span> <span data-ttu-id="2e0e1-105">Durch Zuordnen dieser zwei Entitäten, kann ein Client Informationen über alle Produkte in einer Kategorie mit einer einzelnen Anforderung an den Webdienst abrufen.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-105">By associating these two entities, a client can get information about all of the products in a category with a single request to the web service.</span></span>

<span data-ttu-id="2e0e1-106">Ein Beispiel, das zeigt, wie Sie Zuordnungen zwischen Entitäten erstellen kann heruntergeladen werden, am [Zuordnung Beispiel](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span><span class="sxs-lookup"><span data-stu-id="2e0e1-106">A sample that shows how to create associations between entities can be downloaded at [Association sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span></span>

## <a name="creating-the-association-in-the-resource-schema-file"></a><span data-ttu-id="2e0e1-107">Die Zuordnung in der Ressourcendatei für das Schema zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-107">Creating the Association in the resource schema file</span></span>

<span data-ttu-id="2e0e1-108">Die folgende MOF-Datei definiert zwei Entitäten.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-108">The following MOF defines two entities.</span></span> <span data-ttu-id="2e0e1-109">Wir erstellen eine Zuordnung zwischen ihnen.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-109">We will create an association between them.</span></span>

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

<span data-ttu-id="2e0e1-110">Die `Category` -Klasse definiert eine Eigenschaft, ein Array der Namen der Produkte, die zu dieser Kategorie gehören.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-110">The `Category` class defines a property that is an array of the names of the products that belong to that category.</span></span>

<span data-ttu-id="2e0e1-111">Um zwei Entitäten zu verknüpfen, müssen Sie definieren eine Klasse mit dem `Association` Attribut in der Ressourcendatei für die MOF-von-Schema für den Dienst.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-111">To associate two entities, you must define a class with the `Association` attribute in the resource schema MOF file for the service.</span></span> <span data-ttu-id="2e0e1-112">Definieren Sie die Klasse muss die beiden Entitäten verknüpft ist, wird aufgerufen, `ends` der Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-112">The class must define the two entities to be associated, called `ends` of the association.</span></span> <span data-ttu-id="2e0e1-113">Das folgende Beispiel zeigt eine Definition einer Klasse, die eine Zuordnung zwischen den Entitäten Category und Produkte definiert.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-113">The following example shows a definition of a class that defines an association between the Category and Products entities.</span></span>

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

<span data-ttu-id="2e0e1-114">Sie müssen auch die Deklaration der Products-Eigenschaft in der Kategorie-Klasse ändern.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-114">You must also change the declaration of the Products property in the Category class.</span></span> <span data-ttu-id="2e0e1-115">Sie verwenden die `AssociationClass` Schlüsselwort, um anzugeben, dass die Eigenschaft eines der Enden der Zuordnung ist.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-115">You use the `AssociationClass` keyword to specify that the property is one end of the association.</span></span> <span data-ttu-id="2e0e1-116">Die Eigenschaft muss auch als Verweis auf ein Array von Zeichenfolgen, anstatt eine separate Entität definiert werden.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-116">The property must also be defined as a reference to a separate entity, rather than an array of strings.</span></span> <span data-ttu-id="2e0e1-117">Verwenden Sie hierzu die `ref` Schlüsselwort.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-117">You do this by using the `ref` keyword.</span></span> <span data-ttu-id="2e0e1-118">Das folgende Beispiel zeigt die Eigenschaftsdefinition für die Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-118">The following example shows the property definition for the association.</span></span>

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

<span data-ttu-id="2e0e1-119">Abschließend müssen Sie das andere Ende der Zuordnung durch Hinzufügen der Definition einer zum Deklarieren der `Product` Klasse.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-119">Finally, you must declare the other end of the association by adding a property definition to the `Product` class.</span></span> <span data-ttu-id="2e0e1-120">Dies ist ein Verweis auf die entweder ein Array oder einer einzigen Entität.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-120">This is a reference to either an array or to a single entity.</span></span> <span data-ttu-id="2e0e1-121">Unter der Annahme, dass jedes Produkt nur eine Kategorie angehört, würde die Definition wie folgt lauten.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-121">Assuming that each product belongs to only one category, the definition would be as follows.</span></span>

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

<span data-ttu-id="2e0e1-122">Die Eigenschaften, die die beiden Enden der Zuordnung darstellen, werden Navigationseigenschaften aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-122">The properties that represent the two ends of the association are called navigation properties.</span></span>

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a><span data-ttu-id="2e0e1-123">Schritte zum Zuordnen von Entitäten in der Ressourcendatei für das schema</span><span class="sxs-lookup"><span data-stu-id="2e0e1-123">Steps for associating entities in the resource schema file</span></span>

- <span data-ttu-id="2e0e1-124">Definieren Sie die Zuordnung als eine Klasse mit dem `Association` Schlüsselwort.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-124">Define the association as a class by using the `Association` keyword.</span></span>

- <span data-ttu-id="2e0e1-125">Definieren Sie die Enden der Zuordnung mithilfe des Assoziationsklasse-Schlüsselworts verwenden, um die Eigenschaften der zugeordneten Entitäten zu qualifizieren.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-125">Define the ends of the association by using the AssociationClass keyword to qualify properties of the associated entities.</span></span>

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a><span data-ttu-id="2e0e1-126">Die Zuordnung in der Mapping-XML-Ressourcendatei zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-126">Creating the association in the resource mapping XML file</span></span>

<span data-ttu-id="2e0e1-127">Es gibt drei hauptfälle beim mapping einer Zuordnung in der Mapping-XML-Ressourcendatei zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-127">There are three different cases to consider when mapping an association in the resource mapping XML file.</span></span>

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a><span data-ttu-id="2e0e1-128">Gewusst wie: Zuordnen von Entitäten in der Ressourcendatei für die Zuordnung bestimmen</span><span class="sxs-lookup"><span data-stu-id="2e0e1-128">Determining how to associate entities in the resource mapping file</span></span>

- <span data-ttu-id="2e0e1-129">Wenn die Navigationseigenschaft in der zugrunde liegenden vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-129">If the navigation property is present in the underlying.</span></span> <span data-ttu-id="2e0e1-130">.NET Framework-Typ enthält dieser Eigenschaft die foreign key, ist keine explizite Zuordnung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-130">.NET Framework type, and that property contains foreign keys, no explicit mapping is necessary.</span></span>

- <span data-ttu-id="2e0e1-131">Wenn die Navigationseigenschaft nicht in den zugrunde liegenden .NET Framework-Typ vorhanden ist, müssen Sie ein Cmdlet angeben, die die Liste der Schlüssel, der die assoziierten Instanzen abruft.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-131">If the navigation property does not exist in the underlying .NET Framework type, you must specify a cmdlet that retrieves the list of keys of the associated instances.</span></span> <span data-ttu-id="2e0e1-132">Hierzu fügen eine `Association` Element geschachtelt unter der `CmdletImplementation` Element, und befolgen die Elemente, die definieren, die `cmdlets` für die anderen CRUD-Befehle.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-132">You do this by adding an `Association` element nested under the `CmdletImplementation` element, following the elements that define the `cmdlets` for the other CRUD commands.</span></span>

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

- <span data-ttu-id="2e0e1-133">Wenn die Navigationseigenschaft ist in der zugrunde liegenden .NET Framework-Typ vorhanden, aber sie Objektinstanzen anstelle von Fremdschlüsseln enthält, dann müssen Sie ein Cmdlet (durch Schreiben einer Windows PowerShell-Funktion oder einem Skript) erstellen die Fremdschlüssel abrufen.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-133">If the navigation property does exist in the underlying .NET Framework type, but it contains object instances instead of foreign keys, then you must create a cmdlet (by writing a Windows PowerShell function or script) to retrieve the foreign keys.</span></span> <span data-ttu-id="2e0e1-134">Anschließend geben Sie das Cmdlet in der Ressourcendatei für die Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-134">You then specify that cmdlet in the resource mapping file.</span></span> <span data-ttu-id="2e0e1-135">Beispielsweise würde das Skript zum Abrufen der Schlüssel wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-135">For example, the script to retrieve the keys would look like the following.</span></span>

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  <span data-ttu-id="2e0e1-136">Und der XML-Code in der Ressourcendatei für die Zuordnung sieht wie folgt.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-136">And the XML in the resource mapping file would look like the following.</span></span>

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

- <span data-ttu-id="2e0e1-137">Zusätzlich zum Angeben eines Cmdlets, um die zugeordneten Entitäten abzurufen, können Sie auch Cmdlets zum Hinzufügen und Entfernen von Verweisen aus der Auflistung angeben.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-137">In addition to specifying a cmdlet to retrieve the associated entities, you can also specify cmdlets to add and remove references from the collection.</span></span> <span data-ttu-id="2e0e1-138">Im folgende Beispiel wird davon ausgegangen, dass die Cmdlets Add-ProductToCategory und Remove-ProductFromCategory vorhanden sind (sie können auch definiert werden in einem Skript oder eine Funktion, wie im vorherigen Beispiel).</span><span class="sxs-lookup"><span data-stu-id="2e0e1-138">The following example assumes that the Add-ProductToCategory and Remove-ProductFromCategory cmdlets exist (they can also be defined in a script or function as in the previous example).</span></span>

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

## <a name="querying-associated-entities"></a><span data-ttu-id="2e0e1-139">Abfragen von zugehörigen Entitäten</span><span class="sxs-lookup"><span data-stu-id="2e0e1-139">Querying associated entities</span></span>

<span data-ttu-id="2e0e1-140">Der Client kann es sich um eine Liste der Instanzen einer Entität zugeordnet sind, mithilfe von bestimmten Abfragen abrufen.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-140">The client can retrieve a list of the instances associated with an entity by creating specific queries.</span></span>

#### <a name="constructing-queries-for-associated-entities"></a><span data-ttu-id="2e0e1-141">Erstellen von Abfragen für die zugeordneten Entitäten</span><span class="sxs-lookup"><span data-stu-id="2e0e1-141">Constructing queries for associated entities</span></span>

- <span data-ttu-id="2e0e1-142">Ein Client kann die Details einer Kategorie anfordern, ohne die zugehörigen Produkte abzurufen.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-142">A client can request the details of a category without retrieving its associated products.</span></span> <span data-ttu-id="2e0e1-143">Die folgende Anforderung ruft z. B. Details zu den `food` Kategorie.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-143">For example, the following request gets details of the `food` category.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  <span data-ttu-id="2e0e1-144">Um die zugehörigen Produkte in der Kategorie zu erhalten (jedoch nicht die Details der Kategorie, der Client gibt die Navigationseigenschaft in der Anforderung an.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-144">To get the associated products of the category (but not details of the category itself, the client specifies the navigation property in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- <span data-ttu-id="2e0e1-145">Um nur die URLs der Produkte abzurufen, verwenden die `$links` Qualifizierer in der Anforderung.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-145">To retrieve only URLs of the products, use the `$links` qualifier in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- <span data-ttu-id="2e0e1-146">Der Client erhalten sowohl die Kategoriedetails und die zugehörigen Produkte mithilfe der `$expand` Qualifizierer.</span><span class="sxs-lookup"><span data-stu-id="2e0e1-146">The client can get both the category details and its associated products by using the `$expand` qualifier.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a><span data-ttu-id="2e0e1-147">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2e0e1-147">See Also</span></span>

[<span data-ttu-id="2e0e1-148">Erstellen eines Webdiensts für Management OData IIS-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="2e0e1-148">Creating a Management OData IIS Extension Web Service</span></span>](./creating-a-management-odata-web-service.md)