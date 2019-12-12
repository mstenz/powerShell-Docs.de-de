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
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366269"
---
# <a name="public-resource-schema"></a>Schema für öffentliche Ressourcen

Management odata verwendet MOF, um Ressourcen und deren Eigenschaften zu definieren. Die Eigenschaften einer odata-Entität vom Typ "Management" entsprechen direkt den Eigenschaften des verwalteten Typs, der vom zugrunde liegenden Cmdlet zurückgegeben wird.

## <a name="defining-a-resource"></a>Definieren einer Ressource

Jede Ressource entspricht einem Objekt, das von einem Windows PowerShell-Cmdlet zurückgegeben wird. In der MOF-Datei der öffentlichen Ressource definieren Sie eine Ressource, indem Sie eine Klasse deklarieren. Die-Klasse besteht aus Eigenschaften, die den Eigenschaften des-Objekts entsprechen. Beispielsweise wird im folgenden Beispiel die [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Klasse durch den folgenden MOF dargestellt.

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

Jedem Eigenschaftsnamen wird ein Datentyp vorangestellt. Die Datentypen in diesem Beispiel entsprechen primitiven CLR-Datentypen in den .NET-Frameworks, aber Eigenschaften können auch Verweise auf andere Ressourcen oder komplexe Typen sein, die beide später beschrieben werden.

Der `Key`-Qualifizierer gibt an, dass eine Eigenschaft zur eindeutigen Identifizierung einer Ressourcen Instanz verwendet wird. Eine Ressource kann über mehr als einen Schlüssel verfügen.

Der `Required`-Qualifizierer gibt an, dass die Eigenschaft erforderlich ist. Wenn eine Eigenschaft mit dem `Key` Qualifizierer gekennzeichnet ist, wird Sie als erforderlich angesehen, und der `Required` Qualifizierer ist nicht erforderlich.

### <a name="complex-data-types"></a>Komplexe Datentypen

Eigenschaften von Entitäten können komplexe Datentypen aufweisen. Komplexe Datentypen sind Typen, die aus anderen Typen bestehen, ähnlich wie Strukturen in der Programmiersprache C. Ein komplexer Typ wird in der MOF-Datei als Klasse mit dem `ComplexType` Qualifizierer deklariert, wie im folgenden Beispiel gezeigt.

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

Um eine Entitäts Eigenschaft als komplexen Typ zu deklarieren, deklarieren Sie Sie als `string` Typ mit dem `EmbeddedInstance`-Qualifizierer, einschließlich des Namens des komplexen Typs. Im folgenden Beispiel wird die Deklaration einer Eigenschaft des im vorherigen Beispiel deklarierten `PswsTest_ProcessModule` Typs veranschaulicht.

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>Zuordnen von Entitäten

Sie können zwei Entitäten mithilfe der Qualifizierer Association und associationclass verknüpfen. Weitere Informationen finden Sie unter [Zuordnen von Verwaltungs-odata-Entitäten](./associating-management-odata-entities.md).

### <a name="derived-types"></a>Abgeleitete Typen

Sie können einen Typ von einem anderen Typ ableiten. Der abgeleitete Typ erbt alle Eigenschaften des Typs, von dem er abgeleitet wurde, zusätzlich zu den explizit abgeleiteten Eigenschaften. Das folgende Beispiel zeigt eine Typdeklaration und dann eine Deklaration zweier Typen, die von diesem Typ abgeleitet werden.

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