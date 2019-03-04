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
ms.openlocfilehash: a9204ca7b28fc5792ef9bd18f6b0b24964de7386
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859546"
---
# <a name="public-resource-schema"></a>Schema für öffentliche Ressourcen

Management OData verwendet MOF, um Ressourcen und deren Eigenschaften zu definieren. Die Eigenschaften einer Management OData-Entität entsprechen direkt auf die Eigenschaften des verwalteten Typs, von dem zugrunde liegenden Cmdlet zurückgegeben.

## <a name="defining-a-resource"></a>Definieren eine Ressource

Jede Ressource entspricht ein durch ein Windows PowerShell-Cmdlet zurückgegebenes Objekt. In der Publc Ressourcen MOF-Datei definieren Sie eine Ressource durch Deklarieren einer Klasse. Die Klasse besteht aus Eigenschaften, die die Eigenschaften des Objekts entsprechen. Im folgenden Beispiel, z. B. die ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Klasse wird durch die folgende MOF-Datei dargestellt.

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

Jeder Eigenschaftsname ist ein Datentyp vorangestellt. Primitive CLR-Datentypen in den .NET Frameworks-entsprechen die Datentypen in diesem Beispiel können, aber Eigenschaften auch Verweise auf andere Ressourcen oder komplexe Typen, die beide weiter unten beschrieben werden.

Die `Key` Qualifizierer gibt an, dass eine Eigenschaft verwendet wird, um eine Ressourceninstanz eindeutig zu identifizieren. Eine Ressource kann mehr als ein Schlüssel aufweisen.

Die `Required` Qualifizierer gibt an, dass die Eigenschaft erforderlich ist. Wenn eine Eigenschaft mit mit der Bezeichnung der `Key` Qualifizierer, gilt dies erforderlich und die `Required` Qualifizierer ist nicht erforderlich.

### <a name="complex-data-types"></a>Komplexe Datentypen

Eigenschaften von Entitäten können komplexe Datentypen haben. Komplexe Datentypen sind Typen, die aus anderen Typen wie Strukturen in der Programmiersprache C bestehen. Ein komplexer Typ ist als eine Klasse mit in die MOF-Datei deklariert die `ComplexType` Qualifizierer, wie im folgenden Beispiel gezeigt.

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

Um eine Entitätseigenschaft als komplexer Typ deklarieren zu können, deklarieren Sie ihn als einen `string` Geben Sie mit der `EmbeddedInstance` Qualifizierer, einschließlich des Namens des komplexen Typs. Das folgende Beispiel Hshows die Deklaration einer Eigenschaft von der `PswsTest_ProcessModule` Typ deklariert wird, im vorherigen Beispiel.

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>Zuordnen von Entitäten

Sie können zwei Entitäten zuordnen, indem Sie die Zuordnung und AssocationClass Qualifizierer verwenden. Weitere Informationen finden Sie unter [Management OData-Entitäten zuordnen](./associating-management-odata-entities.md).

### <a name="derived-types"></a>Abgeleitete Typen

Sie können einen Typ von einem anderen Typ ableiten. Der abgeleitete Typ erbt alle Eigenschaften des Typs, von dem er sowie auf alle Eigenschaften, die explizit abgeleitet abgeleitet. Das folgende Beispiel zeigt eine Typdeklaration, und klicken Sie dann eine Deklaration von zwei Typen, die von diesem Typ abgeleitet.

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