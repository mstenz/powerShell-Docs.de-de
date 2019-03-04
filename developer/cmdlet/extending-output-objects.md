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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861926"
---
# <a name="extending-output-objects"></a>Erweitern von Ausgabeobjekten

Sie können die .NET Framework-Objekte erweitern, die von Cmdlets, Funktionen und Skripts mithilfe von Typdateien (. ps1xml) zurückgegeben werden. Typen-Dateien sind XML-basierte Dateien, mit denen Sie die Eigenschaften und Methoden zu vorhandenen Objekten hinzufügen. Windows PowerShell bietet z. B. die Types. ps1xml-Datei, die Elemente auf mehrere vorhandene .NET Framework-Objekte hinzugefügt. Die Types. ps1xml-Datei befindet sich im Installationsverzeichnis von Windows PowerShell (`$pshome`). Sie können Ihre eigene Typendatei erweitert diese Objekte oder andere Objekte erweitern erstellen. Wenn Sie ein Objekt mithilfe einer Typendatei erweitern, wird jede Instanz des Objekts mit der neuen Elemente erweitert.

## <a name="extending-the-systemarray-object"></a>Erweitern Sie den System.Array-Objekt

Das folgende Beispiel zeigt, wie Windows PowerShell erweitert den [System.Array](/dotnet/api/System.Array) Objekt in der Types. ps1xml-Datei. In der Standardeinstellung [System.Array](/dotnet/api/System.Array) Objekte verfügen über eine `Length` -Eigenschaft, die die Anzahl der Objekte im Array auflistet. Jedoch, da der Name "Length" die Eigenschaft nicht klar beschreiben, Windows PowerShell fügt die `Count` aliaseigenschaft, die zeigt, an den gleichen Wert wie die `Length` Eigenschaft. Das folgende XML fügt die `Count` Eigenschaft, um die [System.Array](/dotnet/api/System.Array) Typ.

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

Um diese neue aliaseigenschaft anzuzeigen, verwenden eine [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) Befehl auf jedem Array ist, wie im folgenden Beispiel gezeigt.

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
Verwenden Sie entweder die `Count` Eigenschaft oder das `Length` Eigenschaft, um zu bestimmen, wie viele Objekte in einem Array sind. Beispiel:

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

## <a name="custom-types-files"></a>Benutzerdefinierte Typen von Dateien

Starten Sie zum Erstellen einer benutzerdefinierten Typen-Datei durch Kopieren einer vorhandenen Typendatei. Die neue Datei kann einen beliebigen Namen aufweisen, jedoch muss eine. ps1xml-Dateinamenerweiterung. Wenn Sie die Datei kopieren, setzen Sie die Datei in einem Verzeichnis, das Windows PowerShell zugegriffen werden kann, aber es sinnvoll ist, platzieren Sie die Dateien im Installationsverzeichnis von Windows PowerShell (`$pshome`) oder in einem Unterverzeichnis des Installationsverzeichnisses.

Um Ihre eigenen erweiterte Typen in die Datei hinzuzufügen, fügen Sie eine Types-Element für jedes Objekt, das Sie erweitern möchten. In den folgenden Themen enthalten Beispiele für.

- Weitere Informationen zum Hinzufügen von Eigenschaften und-Eigenschaftensätzen finden Sie unter [erweiterte Eigenschaften](./extending-properties-for-objects.md)

- Weitere Informationen zum Hinzufügen von Methoden finden Sie unter [erweiterte Methoden](./defining-default-methods-for-objects.md).

- Weitere Informationen zum Hinzufügen von Elementgruppen finden Sie unter [Elementgruppen erweiterte](./defining-default-member-sets-for-objects.md).

Nachdem Sie Ihre eigenen erweiterte Typen definieren, verwenden Sie eine der folgenden Methoden, um die erweiterten Objekte verfügbar zu machen:

- Um die erweiterten Typen-Datei mit der aktuellen Sitzung verfügbar zu machen, verwenden Sie die [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) Cmdlet, um die neue Datei hinzuzufügen. Wenn Sie möchten Ihre Typen, die Typen Vorrang vor, die definiert sind Typen andere Dateien (einschließlich der Types. ps1xml-Datei), verwenden Sie die `PrependData` Parameter, der die [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) Cmdlet.
- Um die erweiterten Typen-Datei in alle zukünftigen Sitzungen verfügbar zu machen, fügen Sie die Typendatei auf ein Modul, exportieren Sie die aktuelle Sitzung oder Hinzufügen der [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) -Befehl zu Ihrem Windows PowerShell-Profil.

## <a name="signing-types-files"></a>Signieren von Dateien von Typen

Typdateien müssen digital signiert werden, um zu verhindern, Manipulation, da der XML-Code Skriptblöcke enthalten kann. Weitere Informationen zum Hinzufügen von digitaler Signatures finden Sie unter [About_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>Weitere Informationen

[Definieren von Standardeigenschaften für Objekte](./extending-properties-for-objects.md)

[Definieren von standardmäßigen Methoden für Objekte](./defining-default-methods-for-objects.md)

[Definieren von Elementgruppen Standard für Objekte](./defining-default-member-sets-for-objects.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
