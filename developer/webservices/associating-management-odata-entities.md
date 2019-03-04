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
# <a name="associating-management-odata-entities"></a>Zuordnen von Management OData-Entitäten

Es ist häufig nützlich, um eine Zuordnung zwischen zwei verschiedenen Management OData-Entitäten erstellen. Z. B. ein Management OData-Dienst haben Sie die Entitäten, die einen Katalog von Produkten zu verwalten, die in Kategorien organisiert werden konnte, und definieren Sie die Entitäten `Product` und `Category`. Durch Zuordnen dieser zwei Entitäten, kann ein Client Informationen über alle Produkte in einer Kategorie mit einer einzelnen Anforderung an den Webdienst abrufen.

Ein Beispiel, das zeigt, wie Sie Zuordnungen zwischen Entitäten erstellen kann heruntergeladen werden, am [Zuordnung Beispiel](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).

## <a name="creating-the-association-in-the-resource-schema-file"></a>Die Zuordnung in der Ressourcendatei für das Schema zu erstellen.

Die folgende MOF-Datei definiert zwei Entitäten. Wir erstellen eine Zuordnung zwischen ihnen.

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

Die `Category` -Klasse definiert eine Eigenschaft, ein Array der Namen der Produkte, die zu dieser Kategorie gehören.

Um zwei Entitäten zu verknüpfen, müssen Sie definieren eine Klasse mit dem `Association` Attribut in der Ressourcendatei für die MOF-von-Schema für den Dienst. Definieren Sie die Klasse muss die beiden Entitäten verknüpft ist, wird aufgerufen, `ends` der Zuordnung. Das folgende Beispiel zeigt eine Definition einer Klasse, die eine Zuordnung zwischen den Entitäten Category und Produkte definiert.

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

Sie müssen auch die Deklaration der Products-Eigenschaft in der Kategorie-Klasse ändern. Sie verwenden die `AssociationClass` Schlüsselwort, um anzugeben, dass die Eigenschaft eines der Enden der Zuordnung ist. Die Eigenschaft muss auch als Verweis auf ein Array von Zeichenfolgen, anstatt eine separate Entität definiert werden. Verwenden Sie hierzu die `ref` Schlüsselwort. Das folgende Beispiel zeigt die Eigenschaftsdefinition für die Zuordnung.

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

Abschließend müssen Sie das andere Ende der Zuordnung durch Hinzufügen der Definition einer zum Deklarieren der `Product` Klasse. Dies ist ein Verweis auf die entweder ein Array oder einer einzigen Entität. Unter der Annahme, dass jedes Produkt nur eine Kategorie angehört, würde die Definition wie folgt lauten.

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

Die Eigenschaften, die die beiden Enden der Zuordnung darstellen, werden Navigationseigenschaften aufgerufen.

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>Schritte zum Zuordnen von Entitäten in der Ressourcendatei für das schema

- Definieren Sie die Zuordnung als eine Klasse mit dem `Association` Schlüsselwort.

- Definieren Sie die Enden der Zuordnung mithilfe des Assoziationsklasse-Schlüsselworts verwenden, um die Eigenschaften der zugeordneten Entitäten zu qualifizieren.

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>Die Zuordnung in der Mapping-XML-Ressourcendatei zu erstellen.

Es gibt drei hauptfälle beim mapping einer Zuordnung in der Mapping-XML-Ressourcendatei zu berücksichtigen.

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>Gewusst wie: Zuordnen von Entitäten in der Ressourcendatei für die Zuordnung bestimmen

- Wenn die Navigationseigenschaft in der zugrunde liegenden vorhanden ist. .NET Framework-Typ enthält dieser Eigenschaft die foreign key, ist keine explizite Zuordnung erforderlich.

- Wenn die Navigationseigenschaft nicht in den zugrunde liegenden .NET Framework-Typ vorhanden ist, müssen Sie ein Cmdlet angeben, die die Liste der Schlüssel, der die assoziierten Instanzen abruft. Hierzu fügen eine `Association` Element geschachtelt unter der `CmdletImplementation` Element, und befolgen die Elemente, die definieren, die `cmdlets` für die anderen CRUD-Befehle.

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

- Wenn die Navigationseigenschaft ist in der zugrunde liegenden .NET Framework-Typ vorhanden, aber sie Objektinstanzen anstelle von Fremdschlüsseln enthält, dann müssen Sie ein Cmdlet (durch Schreiben einer Windows PowerShell-Funktion oder einem Skript) erstellen die Fremdschlüssel abrufen. Anschließend geben Sie das Cmdlet in der Ressourcendatei für die Zuordnung. Beispielsweise würde das Skript zum Abrufen der Schlüssel wie folgt aussehen.

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  Und der XML-Code in der Ressourcendatei für die Zuordnung sieht wie folgt.

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

- Zusätzlich zum Angeben eines Cmdlets, um die zugeordneten Entitäten abzurufen, können Sie auch Cmdlets zum Hinzufügen und Entfernen von Verweisen aus der Auflistung angeben. Im folgende Beispiel wird davon ausgegangen, dass die Cmdlets Add-ProductToCategory und Remove-ProductFromCategory vorhanden sind (sie können auch definiert werden in einem Skript oder eine Funktion, wie im vorherigen Beispiel).

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

## <a name="querying-associated-entities"></a>Abfragen von zugehörigen Entitäten

Der Client kann es sich um eine Liste der Instanzen einer Entität zugeordnet sind, mithilfe von bestimmten Abfragen abrufen.

#### <a name="constructing-queries-for-associated-entities"></a>Erstellen von Abfragen für die zugeordneten Entitäten

- Ein Client kann die Details einer Kategorie anfordern, ohne die zugehörigen Produkte abzurufen. Die folgende Anforderung ruft z. B. Details zu den `food` Kategorie.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  Um die zugehörigen Produkte in der Kategorie zu erhalten (jedoch nicht die Details der Kategorie, der Client gibt die Navigationseigenschaft in der Anforderung an.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- Um nur die URLs der Produkte abzurufen, verwenden die `$links` Qualifizierer in der Anforderung.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- Der Client erhalten sowohl die Kategoriedetails und die zugehörigen Produkte mithilfe der `$expand` Qualifizierer.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>Weitere Informationen

[Erstellen eines Webdiensts für Management OData IIS-Erweiterung](./creating-a-management-odata-web-service.md)