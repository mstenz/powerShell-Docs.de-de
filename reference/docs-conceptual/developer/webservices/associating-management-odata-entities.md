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
# <a name="associating-management-odata-entities"></a>Zuordnen von Management OData-Entitäten

Es ist oft hilfreich, eine Zuordnung zwischen zwei verschiedenen odata-Verwaltungs Entitäten zu erstellen. Ein Verwaltungs-odata-Dienst könnte z. b. über Entitäten verfügen, die einen Produktkatalog verwalten, der in Kategorien organisiert ist, und die Entitäten `Product` und definieren `Category` . Wenn Sie diese beiden Entitäten zuordnen, kann ein Client Informationen zu allen Produkten in einer Kategorie mit einer einzelnen Anforderung an den Webdienst erhalten.

Ein Beispiel, das zeigt, wie Zuordnungen zwischen Entitäten erstellt werden können, finden Sie unter [Association Sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).

## <a name="creating-the-association-in-the-resource-schema-file"></a>Erstellen der Zuordnung in der Ressourcen Schema Datei

Die folgende MOF definiert zwei Entitäten. Wir erstellen eine Verknüpfung zwischen Ihnen.

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

Die- `Category` Klasse definiert eine Eigenschaft, bei der es sich um ein Array mit den Namen der Produkte handelt, die zu dieser Kategorie gehören.

Um zwei Entitäten zuzuordnen, müssen Sie eine Klasse mit dem- `Association` Attribut in der MOF-Datei des Ressourcen Schemas für den Dienst definieren. Die-Klasse muss die beiden zu zugeordneten Entitäten definieren, die als Zuordnung bezeichnet werden `ends` . Das folgende Beispiel zeigt eine Definition einer Klasse, die eine Zuordnung zwischen den Entitäten "Category" und "Products" definiert.

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

Außerdem müssen Sie die Deklaration der Products-Eigenschaft in der Category-Klasse ändern. Verwenden Sie das- `AssociationClass` Schlüsselwort, um anzugeben, dass die Eigenschaft ein Ende der Zuordnung ist. Die-Eigenschaft muss auch als Verweis auf eine separate Entität anstelle eines Arrays von Zeichen folgen definiert werden. Verwenden Sie hierzu das- `ref` Schlüsselwort. Das folgende Beispiel zeigt die Eigenschaften Definition für die Zuordnung.

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

Schließlich müssen Sie das andere Ende der Zuordnung deklarieren, indem Sie der Klasse eine Eigenschafts Definition hinzufügen `Product` . Dabei handelt es sich um einen Verweis auf ein Array oder eine einzelne Entität. Angenommen, jedes Produkt gehört nur zu einer Kategorie, die Definition sieht wie folgt aus.

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

Die Eigenschaften, die die beiden Enden der Zuordnung darstellen, werden als Navigations Eigenschaften bezeichnet.

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>Schritte zum Zuordnen von Entitäten in der Ressourcen Schema Datei

- Definieren Sie die Zuordnung als Klasse, indem Sie das- `Association` Schlüsselwort verwenden.

- Definieren Sie die Enden der Zuordnung, indem Sie das associationclass-Schlüsselwort verwenden, um die Eigenschaften der zugeordneten Entitäten zu qualifizieren.

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>Erstellen der Zuordnung in der XML-Datei der Ressourcen Zuordnung

Beim Zuordnen einer Zuordnung in der XML-Datei der Ressourcen Zuordnung müssen drei verschiedene Fälle berücksichtigt werden.

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>Festlegen der Zuordnung von Entitäten in der Ressourcen Zuordnungs Datei

- , Wenn die Navigations Eigenschaft im zugrunde liegenden vorhanden ist. .NET Framework Typ, und diese Eigenschaft enthält Fremdschlüssel, ist keine explizite Zuordnung erforderlich.

- Wenn die Navigations Eigenschaft nicht im zugrunde liegenden .NET Framework Typ vorhanden ist, müssen Sie ein Cmdlet angeben, das die Liste der Schlüssel der zugeordneten Instanzen abruft. Hierzu fügen Sie ein Element hinzu `Association` , das unter dem-Element unter dem- `CmdletImplementation` Element enthalten ist. Befolgen Sie dabei die Elemente, die `cmdlets` für die anderen CRUD-Befehle definieren.

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

- Wenn die Navigations Eigenschaft im zugrunde liegenden .NET Framework-Typ vorhanden ist, aber anstelle von Fremdschlüsseln Objektinstanzen enthält, müssen Sie ein Cmdlet (durch Schreiben einer Windows PowerShell-Funktion oder eines Windows PowerShell-Skripts) erstellen, um die Fremdschlüssel abzurufen. Anschließend geben Sie dieses Cmdlet in der Ressourcen Mapping-Datei an. Beispielsweise würde das Skript zum Abrufen der Schlüssel wie folgt aussehen.

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  Die XML-Datei in der Ressourcen Zuordnung würde wie folgt aussehen.

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

- Zusätzlich zur Angabe eines Cmdlets zum Abrufen der zugeordneten Entitäten können Sie auch Cmdlets zum Hinzufügen und Entfernen von verweisen aus der Sammlung angeben. Im folgenden Beispiel wird davon ausgegangen, dass die Cmdlets "Add-productdecategory" und "Remove-productfromcategory" vorhanden sind (Sie können auch in einem Skript oder einer Funktion definiert werden, wie im vorherigen Beispiel gezeigt).

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

## <a name="querying-associated-entities"></a>Abfragen von zugeordneten Entitäten

Der Client kann eine Liste der Instanzen abrufen, die einer Entität zugeordnet sind, indem bestimmte Abfragen erstellt werden.

#### <a name="constructing-queries-for-associated-entities"></a>Erstellen von Abfragen für zugehörige Entitäten

- Ein Client kann die Details einer Kategorie anfordern, ohne die zugehörigen Produkte abzurufen. Beispielsweise ruft die folgende Anforderung Details der Kategorie ab `food` .

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  Um die zugeordneten Produkte der Kategorie zu erhalten (aber keine Details der Kategorie selbst), gibt der Client die Navigations Eigenschaft in der Anforderung an.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- Um nur URLs der Produkte abzurufen, verwenden Sie den `$links` Qualifizierer in der Anforderung.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- Der Client kann die Kategoriedetails und die dazugehörigen Produkte mithilfe des- `$expand` Qualifizierers erhalten.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>Weitere Informationen

[Erstellen eines Webdiensts für die Verwaltung von odata IIS-Erweiterungen](./creating-a-management-odata-web-service.md)
