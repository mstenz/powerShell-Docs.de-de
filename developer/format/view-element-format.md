---
title: Anzeigen des Elements (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856146"
---
# <a name="view-element-format"></a>Element „View“ (Format)

Definiert eine Ansicht, in dem ein oder mehrere .NET Objekte angezeigt. Es gibt keine Beschränkung für die Anzahl der Aufrufe, die in einer Formatierungsdatei definiert werden können.

Konfiguration-Element (Format) ViewDefinitions-Element (Format)-View-Element (Format)

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

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `View` Element. Geben Sie nur eines der untergeordneten Steuerelemente, und Sie müssen den Namen der Sicht und die Objekte, die der Ansicht angeben. Definieren von benutzerdefinierten Steuerelementen zum Gruppieren von Objekten und angibt, ob die Sicht Out-of-Band-ist, sind optional.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Controls-Element für die Ansicht (Format)](./controls-element-for-view-format.md)|Optionales Element.<br /><br /> Definiert einen Satz von Steuerelementen, die durch ihren Namen aus, in der Ansicht verwiesen werden kann.|
|[CustomControl-Element (Format)](./customcontrol-element-for-groupby-format.md)|Optionales Element.<br /><br /> Definiert ein benutzerdefiniertes Steuerelement-Format für die Ansicht.|
|[GroupBy-Element für die Ansicht (Format)](./groupby-element-for-view-format.md)|Optionales Element.<br /><br /> Definiert, wie die Elemente der .NET Objekte gruppiert werden.|
|[ListControl-Element (Format)](./listcontrol-element-format.md)|Optionales Element.<br /><br /> Definiert eine Listenformat für die Ansicht.|
|[Name-Element für Ansicht (Format)](./name-element-for-view-format.md)|Erforderliches Element.<br /><br /> Gibt den Namen verwendet, um die Sicht verweisen.|
|[TableControl-Element (Format)](./tablecontrol-element-format.md)|Optionales Element.<br /><br /> Definiert ein Tabellenformat für die Ansicht an.|
|[ViewSelectedBy-Element für die Ansicht (Format)](./viewselectedby-element-format.md)|Erforderliches Element.<br /><br /> Definiert die .NET Objekte, die dieser Ansicht wird angezeigt.|
|[WideControl-Element (Format)](./widecontrol-element-format.md)|Optionales Element.<br /><br /> Definiert eine Vielzahl (Einzelwert) Listenformat für die Ansicht.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ViewDefinitions-Element (Format)](./viewdefinitions-element-format.md)|Definiert die Ansichten verwendet, um die Objekte anzuzeigen.|

## <a name="remarks"></a>Hinweise

Weitere Informationen zu den Komponenten von verschiedenen Ansichten und benutzerdefinierten Steuerelementen finden Sie unter den folgenden Themen:

- [Tabelle anzeigen von Komponenten](./creating-a-table-view.md)

- [Liste Anzeigen von Komponenten](./creating-a-list-view.md)

- [Breite Ansichtskomponenten](./creating-a-wide-view.md)

- [Benutzerdefinierte Steuerelemente](./creating-custom-controls.md)

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt eine `View` Element, das eine Tabellenansicht für definiert die [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) Objekt.

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

[ViewDefinitions-Element (Format)](./viewdefinitions-element-format.md)

[Name-Element für Ansicht (Format)](./name-element-for-view-format.md)

[ViewSelectedBy-Element (Format)](./viewselectedby-element-format.md)

[Controls-Element für die Ansicht (Format)](./controls-element-for-view-format.md)

[GroupBy-Element für die Ansicht (Format)](./groupby-element-for-view-format.md)

[TableControl-Element (Format)](./tablecontrol-element-format.md)

[ListControl-Element (Format)](./listcontrol-element-format.md)

[WideControl-Element (Format)](./widecontrol-element-format.md)

[CustomControl-Element (Format)](./customcontrol-element-for-groupby-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
