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
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369719"
---
# <a name="extending-output-objects"></a>Erweitern von Ausgabeobjekten

Sie können die .NET Framework Objekte, die von Cmdlets, Funktionen und Skripts zurückgegeben werden, mithilfe von Typen Dateien (. ps1xml) erweitern. Typen Dateien sind XML-basierte Dateien, mit denen Sie vorhandenen Objekten Eigenschaften und Methoden hinzufügen können. Windows PowerShell stellt z. b. die Datei Types. ps1xml bereit, die mehreren vorhandenen .NET Framework Objekten Elemente hinzufügt. Die Datei Types. ps1xml befindet sich im Windows PowerShell-Installationsverzeichnis (`$pshome`). Sie können Ihre eigene Typen Datei erstellen, um diese Objekte weiter zu erweitern oder andere Objekte zu erweitern. Wenn Sie ein Objekt mithilfe einer Typen Datei erweitern, wird jede Instanz des Objekts mit den neuen Elementen erweitert.

## <a name="extending-the-systemarray-object"></a>Erweitern des System. Array-Objekts

Das folgende Beispiel zeigt, wie Windows PowerShell das [System. Array](/dotnet/api/System.Array) -Objekt in der Datei Types. ps1xml erweitert. Standardmäßig verfügen [System. Array](/dotnet/api/System.Array) -Objekte über eine `Length`-Eigenschaft, die die Anzahl der Objekte im Array auflistet. Da die Eigenschaft mit dem Namen "length" jedoch nicht eindeutig beschrieben wird, fügt Windows PowerShell die `Count` Alias Eigenschaft hinzu, die denselben Wert wie die Eigenschaft "`Length`" anzeigt. Im folgenden XML-Code wird dem [System. Array](/dotnet/api/System.Array) -Typ die `Count`-Eigenschaft hinzugefügt.

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

Um diese neue Alias Eigenschaft anzuzeigen, verwenden [Sie einen Get-Member-](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) Befehl für ein beliebiges Array, wie im folgenden Beispiel gezeigt.

```powershell
Get-Member -InputObject (1,2,3,4)
```

Der Befehl gibt die folgenden Ergebnisse zurück.
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
Sie können entweder die `Count`-Eigenschaft oder die `Length`-Eigenschaft verwenden, um zu bestimmen, wie viele Objekte in einem Array sind. Beispiel:

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

## <a name="custom-types-files"></a>Benutzerdefinierte Typen Dateien

Wenn Sie eine benutzerdefinierte Typen Datei erstellen möchten, kopieren Sie zunächst eine vorhandene Typen Datei. Die neue Datei kann einen beliebigen Namen haben, Sie muss jedoch über die Dateinamenerweiterung. ps1xml verfügen. Wenn Sie die Datei kopieren, können Sie die neue Datei in einem beliebigen Verzeichnis platzieren, das für Windows PowerShell zugänglich ist, aber es ist hilfreich, die Dateien im Windows PowerShell-Installationsverzeichnis (`$pshome`) oder in einem Unterverzeichnis des-Installationsverzeichnisses zu platzieren.

Fügen Sie für jedes Objekt, das Sie erweitern möchten, ein Types-Element hinzu, um der Datei eigene erweiterte Typen hinzuzufügen. In den folgenden Themen werden Beispiele bereitgestellt.

- Weitere Informationen zum Hinzufügen von Eigenschaften und Eigenschafts Sätzen finden Sie unter [Erweiterte Eigenschaften](./extending-properties-for-objects.md) .

- Weitere Informationen zum Hinzufügen von Methoden finden Sie unter [Erweiterte Methoden](./defining-default-methods-for-objects.md).

- Weitere Informationen zum Hinzufügen von Element Sätzen finden Sie unter [Erweiterte Element Sätze](./defining-default-member-sets-for-objects.md).

Nachdem Sie Ihre eigenen erweiterten Typen definiert haben, verwenden Sie eine der folgenden Methoden, um die erweiterten Objekte verfügbar zu machen:

- Verwenden Sie das [Update-typedata-](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) Cmdlet, um die Datei mit erweiterten Typen für die aktuelle Sitzung verfügbar zu machen. Wenn Sie möchten, dass Ihre Typen Vorrang vor den Typen haben, die in anderen Typen Dateien (einschließlich der Types. ps1xml-Datei) definiert sind, verwenden Sie den `PrependData`-Parameter des Cmdlets " [Update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) ".
- Um die Datei mit erweiterten Typen für alle zukünftigen Sitzungen verfügbar zu machen, fügen Sie die Typdatei einem Modul hinzu, exportieren die aktuelle Sitzung oder fügen den [Update-typedata-](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) Befehl zu Ihrem Windows PowerShell-Profil hinzu.

## <a name="signing-types-files"></a>Signierungs Typen Dateien

Typen Dateien sollten digital signiert werden, um Manipulationen zu verhindern, da XML Skriptblöcke enthalten kann. Weitere Informationen zum Hinzufügen digitaler Signaturen finden Sie unter [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>Weitere Informationen

[Definieren von Standardeigenschaften für Objekte](./extending-properties-for-objects.md)

[Definieren von Standardmethoden für Objekte](./defining-default-methods-for-objects.md)

[Definieren von Standardmember-Sätzen für Objekte](./defining-default-member-sets-for-objects.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
