---
title: View-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361459"
---
# <a name="view-element-format"></a>Element „View“ (Format)

Definiert eine Ansicht, in der ein oder mehrere .NET-Objekte angezeigt werden. Es gibt keine Beschränkung für die Anzahl der Sichten, die in einer Formatierungs Datei definiert werden können.

Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format)

## <a name="syntax"></a>Syntax

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `View`-Elements beschrieben. Sie müssen nur eines der untergeordneten Steuerelemente des Steuer Elements angeben, und Sie müssen den Namen der Ansicht und die Objekte, die die Sicht verwenden, angeben. Definieren von benutzerdefinierten Steuerelementen, Gruppieren von Objekten und angeben, ob die Ansicht out-of-Band ist, sind optional.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Controls-Element für View (Format)](./controls-element-for-view-format.md)|Optionales Element.<br /><br /> Definiert eine Gruppe von Steuerelementen, auf die über Ihren Namen in der Ansicht verwiesen werden kann.|
|[CustomControl-Element (Format)](./customcontrol-element-for-groupby-format.md)|Optionales Element.<br /><br /> Definiert ein benutzerdefiniertes Steuerelement Format für die Ansicht.|
|[GroupBy-Element für Ansicht (Format)](./groupby-element-for-view-format.md)|Optionales Element.<br /><br /> Definiert, wie die Member der .NET-Objekte gruppiert werden.|
|[ListControl-Element (Format)](./listcontrol-element-format.md)|Optionales Element.<br /><br /> Definiert ein Listenformat für die Sicht.|
|[Name-Element für View (Format)](./name-element-for-view-format.md)|Erforderliches Element.<br /><br /> Gibt den Namen an, der zum Verweisen auf die Sicht verwendet wird.|
|[Tablecontrol-Element (Format)](./tablecontrol-element-format.md)|Optionales Element.<br /><br /> Definiert ein Tabellenformat für die Sicht.|
|[Viewselectedby-Element für Ansicht (Format)](./viewselectedby-element-format.md)|Erforderliches Element.<br /><br /> Definiert die .NET-Objekte, die in dieser Ansicht angezeigt werden.|
|[Widecontrol-Element (Format)](./widecontrol-element-format.md)|Optionales Element.<br /><br /> Definiert ein breites Listenformat (Einzelwert) für die Sicht.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Viewdefinitions-Element (Format)](./viewdefinitions-element-format.md)|Definiert die Sichten, die zum Anzeigen von Objekten verwendet werden.|

## <a name="remarks"></a>Hinweise

Weitere Informationen zu den Komponenten verschiedener Sichten und benutzerdefinierte Steuerelemente finden Sie in den folgenden Themen:

- [Tabellen Ansichts Komponenten](./creating-a-table-view.md)

- [Listen Ansichts Komponenten](./creating-a-list-view.md)

- [Breite Ansichts Komponenten](./creating-a-wide-view.md)

- [Benutzerdefinierte Steuerelemente](./creating-custom-controls.md)

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt ein `View`-Element, das eine Tabellenansicht für das [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) -Objekt definiert.

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Weitere Informationen

[Viewdefinitions-Element (Format)](./viewdefinitions-element-format.md)

[Name-Element für View (Format)](./name-element-for-view-format.md)

[Viewselectedby-Element (Format)](./viewselectedby-element-format.md)

[Controls-Element für View (Format)](./controls-element-for-view-format.md)

[GroupBy-Element für Ansicht (Format)](./groupby-element-for-view-format.md)

[Tablecontrol-Element (Format)](./tablecontrol-element-format.md)

[ListControl-Element (Format)](./listcontrol-element-format.md)

[Widecontrol-Element (Format)](./widecontrol-element-format.md)

[CustomControl-Element (Format)](./customcontrol-element-for-groupby-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
