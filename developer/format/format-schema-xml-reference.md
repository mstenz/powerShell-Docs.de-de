---
title: Formatieren von XML-Schemareferenz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac6f7aaa-d0cc-4c7b-a341-85e736174579
caps.latest.revision: 21
ms.openlocfilehash: 4dfe27a5105d82fa18e35f965f92fad16d390a2a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857786"
---
# <a name="format-schema-xml-reference"></a>Formatschema – XML-Referenz

Die Themen in diesem Abschnitt beschreiben, die XML-Elemente, die von den Formatierungsdateien (Format. ps1xml-Dateien) verwendet wird. Formatierungsdateien definieren, wie das .NET Objekt angezeigt wird; das Objekt selbst nicht geändert.

## <a name="in-this-section"></a>In diesem Abschnitt

[Alignment-Element für TableColumnHeader für TableControl (Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) definiert, wie die Daten in einem Spaltenheader angezeigt werden.

[Alignment-Element für TableColumnItem für TableControl (Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) definiert, wie die Daten in der Zeile angezeigt werden.

[AutoSize-Element für TableControl (Format)](./autosize-element-for-tablecontrol-format.md) gibt an, ob die Größe der Spalte und die Anzahl von Spalten angepasst werden basierend auf der Größe der Daten.

[AutoSize-Element für WideControl (Format)](./autosize-element-for-widecontrol-format.md) gibt an, ob die Größe der Spalte und die Anzahl von Spalten angepasst werden basierend auf der Größe der Daten.

[ColumnNumber-Element für WideControl (Format)](./columnnumber-element-for-widecontrol-format.md) gibt die Anzahl der Spalten in der Breite Ansicht angezeigt werden.

[Konfigurationselement (Format)](./configuration-element-format.md) Element das obersten Ebene die Formatierungsdatei darstellt.

[Control-Element für Controls für Konfiguration (Format)](./control-element-for-controls-for-configuration-format.md) definiert ein allgemeines Steuerelement, das von allen Ansichten die Formatierungsdatei und den Namen, die verwendet wird, verweisen auf das Steuerelement verwendet werden kann.

[Control-Element für Controls für Ansicht (Format)](./control-element-for-controls-for-view-format.md) definiert ein Steuerelement, das von der Ansicht und der Name, der verwendet wird, verweisen auf das Steuerelement verwendet werden kann.

[Controls-Element für Konfiguration (Format)](./controls-element-for-configuration-format.md) definiert die allgemeine Steuerelemente, die von allen Ansichten des die Formatierungsdatei verwendet werden können.

[Controls-Element für die Ansicht (Format)](./controls-element-for-view-format.md) definiert die Steuerelemente, die von einer bestimmten Ansicht verwendet werden können.

[CustomControl-Element für das Steuerelement für die Konfiguration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md) definiert ein Steuerelement. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[CustomControl-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md) definiert ein Steuerelement, das von der Sicht verwendet wird.

[CustomControl-Element für GroupBy (Format)](./customcontrol-element-for-groupby-format.md) definiert das benutzerdefinierte Steuerelement, das die neue Gruppe anzeigt.

[CustomControl-Element (Format)](./customcontrol-element-for-groupby-format.md) definiert ein benutzerdefiniertes Steuerelement-Format für die Ansicht.

[CustomControlName-Element für die ExpressionBinding für Steuerelemente für die Konfiguration (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md) gibt den Namen eines allgemeinen Steuerelements. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[CustomControlName-Element für ExpressionBindine für Steuerelemente für die Ansicht (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md) gibt den Namen eines allgemeinen Steuerelements oder einem Steuerelement. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[CustomControlName-Element der GroupBy (Format)](./customcontrolname-element-for-groupby-format.md) gibt den Namen eines benutzerdefinierten Steuerelements, die verwendet wird, um die neue Gruppe anzuzeigen. Dieses Element wird verwendet, bei der Definition einer Tabelle, Liste, breit oder benutzerdefiniertes Steuerelement anzeigen.

[CustomEntry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md) enthält eine Definition des allgemeinen-Steuerelements. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[CustomEntry-Element für CustomEntries für Steuerelemente für die Ansicht (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md) enthält eine Definition des Steuerelements. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[CustomEntry-Element für CustomEntries für Ansicht (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md) enthält eine Definition der benutzerdefinierten Steuerelements an.

[CustomEntry-Element für CustomControl für GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md) enthält eine Definition des Steuerelements. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[CustomEntries-Element für CustomControl für Konfiguration (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md) enthält die Definitionen von einem allgemeinen Steuerelement. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[CustomEntries-Element für CustomControl für Steuerelemente für die Ansicht (Format)](./customentries-element-for-customcontrol-for-controls-for-view-format.md) enthält die Definitionen für das Steuerelement. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[CustomEntries-Element für CustomControl für GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md) enthält die Definitionen für das Steuerelement. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[CustomEntries-Element für CustomControl für Ansicht (Format)](./customentries-element-for-customcontrol-for-view-format.md) enthält die Definitionen der benutzerdefinierten Steuerelements an. Die Ansicht benutzerdefiniertes Steuerelement muss eine oder mehrere Definitionen angegeben werden.

[CustomItem-Element für CustomEntry für Steuerelemente für die Konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md) definiert, welche Daten vom Steuerelement angezeigt werden und wie diese angezeigt wird. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[CustomItem-Element für CustomEntry für Steuerelemente für die Ansicht (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md) definiert, welche Daten vom Steuerelement angezeigt werden und wie diese angezeigt wird. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[CustomItem-Element für CustomEntry für Ansicht (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md) definiert, welche Daten von der Sicht des benutzerdefinierten Steuerelements angezeigt werden und wie diese angezeigt wird. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

[CustomItem-Element für CustomEntry für GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md) definiert, welche Daten von der Sicht des benutzerdefinierten Steuerelements angezeigt werden und wie diese angezeigt wird. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[DefaultSettings-Element (Format)](./defaultsettings-element-format.md) definiert allgemeine Einstellungen, die für alle Ansichten die Formatierungsdatei gelten. Allgemeine Einstellungen umfassen das Anzeigen von Fehlern, Umbrechen von Text in Tabellen, die definieren, wie Sammlungen erweitert werden, und vieles mehr.

[DisplayError-Element (Frmat)](./displayerror-element-format.md) gibt an, dass die Zeichenfolge #ERR angezeigt wird, wenn ein Fehler auftritt, Anzeigen von Daten.

[EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Konfiguration (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md) definiert .NET Typen, die die Definition eines allgemeinen Steuerelement oder die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Ansicht (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md) definiert .NET Typen, die diese Steuerelementdefinition oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[EntrySelectedBy-Element für CustomEntry für Ansicht (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) definiert .NET Typen, die dieser benutzerdefinierten Eintrag oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.

[EntrySelectedBy-Element für EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md) definiert .NET Typen, die diese Definition oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.

[EntrySelectedBy-Element für CustomEntry für GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md) definiert .NET Typen, die diese Steuerelementdefinition oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[EntrySelectedBy-Element für ListEntry für ListControl (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md) definiert .NET Typen, die diese Liste View Definition oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden. In den meisten Fällen ist nur eine Definition für eine Listenansicht erforderlich. Sie können jedoch mehrere Definitionen für die Listenansicht bereitstellen, sollten Sie die gleiche Listenansicht zu verwenden, um unterschiedliche Daten für verschiedene Objekte anzuzeigen.

[EntrySelectedBy-Element für TableRowEntry (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) definiert die Typen von .NET, dessen Eigenschaftswerte werden in der Zeile angezeigt.

[EntrySelectedBy-Element für WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md) definiert .NET Typen, die dieser Definition von der breiten Ansicht oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.

[EnumerableExpansion-Element (Format)](./enumerableexpansion-element-format.md) definiert, wie bestimmte .NET-Auflistung, die Objekte werden erweitert, wenn sie in einer Ansicht angezeigt werden.

[EnumerableExpansions-Element (Format)](./enumerableexpansions-element-format.md) definiert, wie .NET Auflistungsobjekte erweitert werden, wenn sie in einer Ansicht angezeigt werden.

[EnumerateCollection-Element für die ExpressionBinding für Steuerelemente für die Konfiguration (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md) angegeben, dass die Elemente der Auflistungen, die vom Steuerelement angezeigt werden. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[EnumerateCollection-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md) angegeben, dass die Elemente der Auflistungen angezeigt werden. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[EnumerateCollection-Element zum Binden von Expression für CustomControl für Ansicht (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md) gibt an, dass die Elemente der Auflistungen angezeigt werden. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

[EnumerateCollection-Element für die ExpressionBinding für GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) gibt an, dass die Elemente der Auflistungen angezeigt werden. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[Erweitern Sie (Format)-Element](./expand-element-format.md) gibt an, wie das Objekt für diese Definition erweitert wird.

[ExpressionBinding-Element für CustomItem für Steuerelemente für die Konfiguration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) definiert die Daten, die vom Steuerelement angezeigt wird. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) definiert die Daten, die vom Steuerelement angezeigt wird. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[ExpressionBinding-Element für CustomItem für CustomControl für Ansicht (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md) definiert die Daten, die vom Steuerelement angezeigt wird. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

[ExpressionBinding-Element für CustomItem für GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md) definiert die Daten, die vom Steuerelement angezeigt wird. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[FirstLineHanging-Element für Frame für Steuerelemente für die Konfiguration (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) gibt an, wie viele Zeichen, die die erste Zeile der Daten auf der linken Seite verschoben wird. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[FirstLineHanging Element in der Rahmen von Steuerelementen der Ansicht (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) gibt an, wie viele Zeichen, die die erste Zeile der Daten auf der linken Seite verschoben wird. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[FirstLineHanging-Element für Frame für CustomControl für Ansicht (Format)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) gibt an, wie viele Zeichen, die die erste Zeile der Daten auf der linken Seite verschoben wird. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

[FirstLineHanging-Element für Frame für GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md) gibt an, wie viele Zeichen, die die erste Zeile der Daten auf der linken Seite verschoben wird. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[FirstLineIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) gibt an, wie viele Zeichen, die die erste Zeile der Daten nach rechts verschoben wird. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[FirstLineIndent Element in der Rahmen von Steuerelementen der Ansicht (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md) gibt an, wie viele Zeichen, die die erste Zeile der Daten nach rechts verschoben wird. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[FirstLineIndent Element](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) gibt an, wie viele Zeichen, die die erste Zeile der Daten nach rechts verschoben wird. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

[FirstLineIndent-Element für Frame für GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md) gibt an, wie viele Zeichen, die die erste Zeile der Daten nach rechts verschoben wird. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[FormatString-Element für den ListItem (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md) gibt an, ein Formatmuster, das definiert, wie der Wert der Eigenschaft oder ein Skript angezeigt wird.

[FormatString-Element für TableColumnItem (Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md) gibt an, ein Formatmuster, das definiert, wie die Eigenschaft oder ein Skript-Wert, der in der Tabelle angezeigt wird.

[FormatString-Element für WideItem für WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md) gibt an, ein Formatmuster, das definiert, wie der Wert der Eigenschaft oder ein Skript in der Ansicht angezeigt wird.

[Frame-Element für CustomItem für Steuerelemente für die Konfiguration (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md) definiert, wie die Daten angezeigt werden, z. B. das Verschieben von Daten nach links oder rechts. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[Frame-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./frame-element-for-customitem-for-controls-for-view-format.md) definiert, wie die Daten angezeigt werden, z. B. das Verschieben von Daten nach links oder rechts. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[Frame-Element für CustomControl für Ansicht (Format) für CustomItem](./frame-element-for-customitem-for-customcontrol-for-view-format.md) definiert, wie die Daten angezeigt werden, z. B. das Verschieben von Daten nach links oder rechts. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

[Frame-Element für die GroupBy (Format) für CustomItem](./frame-element-for-customitem-for-groupby-format.md) definiert, wie die Daten angezeigt werden, z. B. das Verschieben von Daten nach links oder rechts. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[GroupBy-Element für die Ansicht (Format)](./groupby-element-for-view-format.md) definiert, wie Windows PowerShell eine neue Gruppe von Objekten angezeigt.

[HideTableHeaders-Element (Format)](./hidetableheaders-element-format.md) gibt an, dass die Header der Tabelle nicht angezeigt werden.

[ItemSelectionCondition-Element für die ExpressionBinding für Steuerelemente für die Konfiguration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md) definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[ItemSelectionCondition-Element des ExpressionBinding für Steuerelemente für die Ansicht (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md) definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[ItemSelectionCondition-Element zum Binden von Expression für CustomControl für Ansicht (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md) definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss. Es gibt keine Beschränkung der Anzahl der auswahlbedingungen, die für ein Steuerelement ein Element angegeben werden können. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

[ItemSelectionCondition-Element für die ExpressionBinding für GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md) definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss. Es gibt keine Beschränkung der Anzahl der auswahlbedingungen, die für ein Steuerelement ein Element angegeben werden können. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[ListItem (Format)-ItemSelectionCondition Element](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) definiert die Bedingung, die für dieses Listenelement zu verwendende vorhanden sein muss.

[Versehen Sie Element für den ListItem für ListControl(Format)](./label-element-for-listitem-for-listcontrol-format.md) die Bezeichnung für die Eigenschaft oder ein Skript-Wert in der Zeile angibt.

[Versehen Sie Element für GroupBy (Format)](./label-element-for-groupby-format.md) gibt eine Bezeichnung, die angezeigt wird, wenn eine neue Gruppe gefunden wird.

[Versehen Sie Element für TableColumnHeader (Format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) definiert die Bezeichnung, die am oberen Rand einer Spalte angezeigt wird.

[LeftIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md) gibt an, wie viele Zeichen, die die Daten von den linken Rand verschoben werden. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[LeftIndent Element in der Rahmen von Steuerelementen der Ansicht (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md) gibt an, wie viele Zeichen, die die Daten von den linken Rand verschoben werden. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[LeftIndent-Element für Frame für CustomControl für Ansicht (Format)](./leftindent-element-for-frame-for-customcontrol-for-view-format.md) gibt an, wie viele Zeichen, die die Daten von den linken Rand verschoben werden. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

[LeftIndent-Element für Frame für GroupBy (Format)](./leftindent-element-for-frame-for-groupby-format.md) gibt an, wie viele Zeichen, die die Daten von den linken Rand verschoben werden. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[ListControl-Element (Format)](./listcontrol-element-format.md) eine Liste an, für die Ansicht definiert.

[ListEntry-Element (Format)](./listentry-element-for-listcontrol-format.md) enthält eine Definition der Listenansicht angezeigt.

[ListEntries-Element (Format)](./listentries-element-for-listcontrol-format.md) definiert, wie die Zeilen der Listenansicht angezeigt werden.

[ListItem-Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md) definiert die Eigenschaft oder ein Skript, dessen Wert in einer Zeile in der Listenansicht angezeigt wird.

[ListItems-Element (Format)](./listitems-element-for-listentry-for-listcontrol-format.md) definiert die Eigenschaften und Skripts, die in der Listenansicht angezeigt werden.

[Benennen Sie Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md) gibt den Namen des Steuerelements. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[Namen von Element für SelectionSet (Format)](./name-element-for-selectionset-format.md) gibt den Namen verwendet, um den Auswahlsatz zu verweisen.

[Nennen Sie Element anzeigen (Format)](./name-element-for-view-format.md) gibt den Namen, die verwendet wird, um die Ansicht zu identifizieren.

[Neue-Zeile-Element für CustomItem für Steuerelemente für die Konfiguration (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md) eine leere Zeile eingefügt, um die Anzeige des Steuerelements. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[Neue-Zeile-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./newline-element-for-customitem-for-controls-for-view-format.md) eine leere Zeile eingefügt, um die Anzeige des Steuerelements. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[Neue-Zeile-Element für CustomItem für CustomControl für Ansicht (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md) eine leere Zeile eingefügt, um die Anzeige des Steuerelements. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

[Neue-Zeile-Element für CustomItem für GroupBy (Format)](./newline-element-for-customitem-for-groupby-format.md) eine leere Zeile eingefügt, um die Anzeige des Steuerelements. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[PropertyName-Element für die ExpressionBinding für Steuerelemente für die Konfiguration (Format)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md) gibt an, die .NET-Eigenschaft, deren Wert durch das allgemeine Steuerelement angezeigt wird. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[PropertyName-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md) gibt an, die .NET-Eigenschaft, deren Wert wird vom Steuerelement angezeigt. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[PropertyName-Element für die ExpressionBinding für CustomControl für Ansicht (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md) gibt an, die .NET-Eigenschaft, deren Wert wird vom Steuerelement angezeigt. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen

[PropertyName-Element für die ExpressionBinding für GroupBy (Format)](./propertyname-element-for-expressionbinding-for-groupby-format.md) gibt an, die .NET-Eigenschaft, deren Wert wird vom Steuerelement angezeigt. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[PropertyName-Element für GroupBy (Format)](./propertyname-element-for-groupby-format.md) gibt an, die .NET-Eigenschaft, eine neue Gruppe beginnt, wenn sich der Wert ändert.

[PropertyName-Element für ItemSeclectionCondition für Steuerelemente für die Konfiguration (Format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) gibt an, die .NET-Eigenschaft, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung ist erfüllt, und das Steuerelement wird verwendet. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[PropertyName-Element für ItemSelectionCondition für Steuerelemente für die Ansicht (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) gibt an, die .NET-Eigenschaft, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung ist erfüllt, und das Steuerelement wird verwendet. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[PropertyName-Element für ItemSelectionCondition für CustomControl für Ansicht (Format](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) gibt an, die .NET-Eigenschaft, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung ist erfüllt, und das Steuerelement wird verwendet. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

[PropertyName-Element für ItemSelectionCondition für GroupBy (Format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) gibt an, die .NET-Eigenschaft, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung ist erfüllt, und das Steuerelement wird verwendet. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[PropertyName-Element für ItemSelectionCondition für ListItem (Format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md) gibt an, die .NET-Eigenschaft, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und die Ansicht wird verwendet. Dieses Element wird verwendet, wenn Sie eine Ansicht zu definieren.

[PropertyName-Element für den ListItem für ListControl (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md) gibt an, die .NET-Eigenschaft, deren Wert in der Liste angezeigt wird.

[PropertyName-Element für SelectionCondition für EntrySelectedBy für ListEntry (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md) gibt an, die .NET-Eigenschaft, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und der Eintrag wird verwendet. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[PropertyName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md) gibt an, die .NET-Eigenschaft, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und der Eintrag wird verwendet. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[PropertyName-Element für SelectionCondition für CustomControl für Ansicht (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md) gibt an, die .NET-Eigenschaft, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und die Definition verwendet. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

[PropertyName-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) gibt an, die .NET-Eigenschaft, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und die Definition verwendet.

[PropertyName-Element für SelectionCondition für GroupBy (Format)](./propertyname-element-for-selectioncondition-for-groupby-format.md) gibt an, die .NET-Eigenschaft, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und die Definition verwendet. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[PropertyName-Element für SelectionCondition für EmtrySelectedBy für ListEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) gibt an, die .NET-Eigenschaft, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und der Listeneintrag wird verwendet.

[PropertyName-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md) gibt an, die .NET-Eigenschaft, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und der Tabelleneintrag wird verwendet.

[PropertyName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) gibt an, die .NET-Eigenschaft, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und die Definition verwendet.

[PropertyName-Element für TableColumnItem (Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) gibt die Eigenschaft, deren Wert in der Spalte der Zeile angezeigt wird.

[PropertyName-Element für WideItem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md) gibt die Eigenschaft des Objekts, dessen Wert in der breiten Ansicht angezeigt wird.

[RightIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md) gibt an, wie viele Zeichen, die die Daten von den rechten Rand verschoben werden. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[RightIndent Element in der Rahmen von Steuerelementen der Ansicht (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md) gibt an, wie viele Zeichen, die die Daten von den rechten Rand verschoben werden. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[RightIndent Element](./rightindent-element-for-frame-for-customcontrol-for-view-format.md) gibt an, wie viele Zeichen, die die Daten von den rechten Rand verschoben werden. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

[RightIndent-Element für Frame für GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md) gibt an, wie viele Zeichen, die die Daten von den rechten Rand verschoben werden. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[ScriptBlock-Element für die ExpressionBinding für Steuerelemente für die Konfiguration (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md) gibt das Skript an, dessen Wert durch das allgemeine Steuerelement angezeigt wird. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[ScriptBlock-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md) gibt das Skript an, deren Wert wird vom Steuerelement angezeigt. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[ScriptBlock-Element für die ExpressionBinding für CustomCustomControl für Ansicht (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md) gibt das Skript an, deren Wert wird vom Steuerelement angezeigt. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

[ScriptBlock-Element für die ExpressionBinding für GroupBy (Format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md) gibt das Skript an, deren Wert wird vom Steuerelement angezeigt. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[ScriptBlock-Element für GroupBy (Format)](./scriptblock-element-for-groupby-format.md) gibt an, das Skript, das eine neue Gruppe wird gestartet, wenn sich der Wert ändert.

[ScriptBlock-Element für ItemSelectionCondition für Steuerelemente für die Konfiguration (Format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) gibt das Skript an, die die Bedingung auslöst. Wenn dieses Skript ergab `true`, die Bedingung ist erfüllt, und das Steuerelement wird verwendet. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[ScriptBlock-Element für ItemSelectionCondition für Steuerelemente für die Ansicht (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) gibt das Skript an, die die Bedingung auslöst. Wenn dieses Skript ergab `true`, die Bedingung ist erfüllt, und das Steuerelement wird verwendet. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[ScriptBlock-Element für ItemSelectionCondition für CustomControl für Ansicht (Format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) gibt das Skript an, die die Bedingung auslöst. Wenn dieses Skript ergab `true`, die Bedingung ist erfüllt, und das Steuerelement wird verwendet. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

[ScriptBlock-Element für ItemSelectionCondition für GroupBy (Format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) gibt das Skript an, die die Bedingung auslöst. Wenn dieses Skript ergab `true`, die Bedingung ist erfüllt, und das Steuerelement wird verwendet. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[ScriptBlock-Element für ItemSelectionCondition für ListControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) gibt das Skript an, die die Bedingung auslöst. Wenn dieses Skript ergab `true`, die Bedingung erfüllt ist und das Element der Liste wird verwendet. Dieses Element wird verwendet, wenn Sie eine Ansicht zu definieren.

[ListItem (Format)-Element "scriptblock"](./scriptblock-element-for-listitem-for-listcontrol-format.md) gibt das Skript an, dessen Wert in die Zeile aus der Liste angezeigt wird.

[ScriptBlock-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md) gibt das Skript an, die die Bedingung auslöst. Wenn dieses Skript ergab `true`, die Bedingung erfüllt ist und die Definition verwendet. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[ScriptBlock-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md) gibt das Skript an, die die Bedingung auslöst. Wenn dieses Skript ergab `true`, die Bedingung erfüllt ist und die Definition verwendet. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[ScriptBlock-Element für SelectionCondition für CustomControl für Ansicht (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md) gibt das Skript an, die die Bedingung auslöst. Wenn dieses Skript ergab `true`, die Bedingung erfüllt ist und die Definition verwendet. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

[ScriptBlock-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) gibt das Skript an, die die Bedingung auslöst.

[ScriptBlock-Element für SelectionCondition für GroupBy (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md) gibt das Skript an, die die Bedingung auslöst. Wenn dieses Skript ergab `true`, die Bedingung erfüllt ist und die Definition verwendet. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[ScriptBlock-Element für SelectionCondition für EntrySelectedBy für ListEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) gibt das Skript an, die die Bedingung auslöst. Wenn dieses Skript ergab `true`, die Bedingung erfüllt ist und der Listeneintrag wird verwendet.

[ScriptBlock-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) gibt den Skriptblock, der die Bedingung auslöst. Wenn dieses Skript ergab `true`, die Bedingung erfüllt ist und der Tabelleneintrag wird verwendet.

[ScriptBlock-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) gibt das Skript an, die die Bedingung auslöst. Wenn dieses Skript ergab `true`, die Bedingung erfüllt ist und die Breite Eintrag-Definition verwendet.

[ScriptBlock-Element für TableColumnItem (Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) gibt das Skript an, dessen Wert in der Spalte der Zeile angezeigt wird.

[ScriptBlock-Element für WideItem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md) gibt das Skript an, dessen Wert in der breiten Ansicht angezeigt wird.

[SelectionCondition-Element für EntrySelectedBy für CustomEntry für Konfiguration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md) definiert eine Bedingung, die vorhanden sein muss, für die Steuerelementdefinition eines allgemeinen verwendet werden. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Ansicht (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md) definiert eine Bedingung, die vorhanden sein muss, für die Definition des Steuerelements verwendet werden. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[SelectionCondition-Element für EntrySelectedBy für CustomControl für Ansicht (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md) definiert eine Bedingung, die für die Steuerelementdefinition eines zu verwendenden vorhanden sein muss. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

[SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md) definiert die Bedingung, die vorhanden sein muss, um die Auflistungsobjekte dieser Definition zu erweitern.

[SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md) definiert eine Bedingung, die für die Steuerelementdefinition eines zu verwendenden vorhanden sein muss. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[SelectionCondition-Element für EntrySelectedBy für ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) definiert die Bedingung, die vorhanden sein muss, um diese Definition der Listenansicht zu verwenden. Es gibt keine Beschränkung der Anzahl der auswahlbedingungen, die für eine Listendefinition angegeben werden können.

[SelectionCondition-Element für EntrySelectedBy für TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md) definiert die Bedingung, die vorhanden sein muss, um für diese Definition der Tabellenansicht zu verwenden. Es gibt keine Beschränkung der Anzahl der auswahlbedingungen, die für eine Tabelle (Definition) angegeben werden können.

[SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden. Es gibt keine Beschränkung der Anzahl der auswahlbedingungen, die für eine große Eintrag Definition angegeben werden können.

[SelectionSet-Element (Format)](./selectionset-element-format.md) definiert einen Satz von .NET-Objekten, die durch den Namen des Satzes verwiesen werden kann.

[SelectionSetName-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) gibt einen Satz von .NET-Typen, die dieser Definition des Steuerelements verwenden. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[SelectionSetName-Element für EntrySelectedBy für Steuerelemente für die Ansicht (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md) gibt einen Satz von .NET-Typen, die dieser Definition des Steuerelements verwenden. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[SelectionSetName-Element für EntrySelectedBy für CustomEntry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md) gibt einen Satz von .NET-Objekten für den Listeneintrag. Es gibt keine Beschränkung der Anzahl der von Auswahlgruppen, die nach einem Eintrag angegeben werden können.

[SelectionSetName-Element für EntrySelectedBy für EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md) gibt den Satz von .NET-Typen, die nach dieser Definition erweitert werden.

[SelectionSetName-Element für EntrySelectedBy für GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md) gibt einen Satz von .NET-Objekten für den Listeneintrag. Es gibt keine Beschränkung der Anzahl der von Auswahlgruppen, die nach einem Eintrag angegeben werden können. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[SelectionSetName-Element für EntrySelectedBy für ListEntry (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) gibt einen Satz von .NET-Objekten für den Listeneintrag. Es gibt keine Beschränkung der Anzahl der von Auswahlgruppen, die nach einem Eintrag angegeben werden können.

[SelectionSetName-Element für EntrySelectedBy für TableRowEntry (Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md) gibt ein Satz von .NET Typen der Verwendung dieser Eintrag der Tabellenansicht. Es gibt keine Beschränkung der Anzahl der von Auswahlgruppen, die nach einem Eintrag angegeben werden können.

[SelectionSetName-Element für EntrySelectedBy für WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md) gibt einen Satz von .NET-Objekten für die Definition. Die Definition wird verwendet, wenn eines dieser Objekte angezeigt wird.

[SelectionSetName-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) gibt den Satz von .NET-Typen, die die Bedingung auslösen. Wenn alle Typen in dieser Gruppe vorhanden sind, die Bedingung ist erfüllt, und das Objekt mit diesem Steuerelement angezeigt wird. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[SelectionSetName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md) gibt den Satz von .NET-Typen, die die Bedingung auslösen. Wenn alle Typen in dieser Gruppe vorhanden sind, die Bedingung ist erfüllt, und das Objekt wird mit diesem Steuerelement angezeigt. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[EntrySelectedBy-Element für CustomEntry für Ansicht (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) gibt den Satz von .NET-Typen, die die Bedingung auslösen. Wenn alle Typen in dieser Gruppe vorhanden sind, die Bedingung ist erfüllt, und das Objekt wird mit diesem Steuerelement angezeigt. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

[SelectionSetName-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) gibt den Satz von .NET-Typen, die die Bedingung auslösen. Wenn alle Typen in dieser Gruppe vorhanden sind, wird die Bedingung erfüllt.

[SelectionSetName-Element für SelectionCondition für GroupBy (Format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md) gibt den Satz von .NET-Typen, die die Bedingung auslösen. Wenn alle Typen in dieser Gruppe vorhanden sind, die Bedingung ist erfüllt, und das Objekt mit diesem Steuerelement angezeigt wird. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[SelectionSetName-Element für SelectionCondition für EntrySelectedBy für ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md) gibt den Satz von .NET-Typen, die die Bedingung auslösen. Wenn alle Typen in dieser Gruppe vorhanden sind, die Bedingung ist erfüllt, und das Objekt wird mithilfe dieser Definition der Listenansicht angezeigt.

[SelectionSetName-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) gibt den Satz von .NET-Typen, die die Bedingung auslösen. Wenn alle Typen in dieser Gruppe vorhanden sind, die Bedingung ist erfüllt, und das Objekt wird mithilfe dieser Definition der Tabellenansicht angezeigt.

[SelectionSetName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) gibt den Satz von .NET-Typen, die die Bedingung auslösen. Wenn alle Typen in dieser Gruppe vorhanden sind, die Bedingung ist erfüllt, und das Objekt wird mithilfe dieser Definition der breiten Ansicht angezeigt.

[SelectionSetName-Element für ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md) gibt einen Satz von .NET-Objekten, die von der Ansicht angezeigt werden.

[SelectionSets-Element (Format)](./selectionsets-element-format.md) definiert die Sätze von .NET-Objekten, die von einzelnen Format Ansichten verwendet werden können.

[ShowError-Element (Format)](./showerror-element-format.md) gibt an, dass es sich bei der vollständigen Fehlerdatensatz angezeigt wird, tritt ein Fehler beim Anzeigen eines Datenelements.

[TableColumnHeader-Element für TableHeaders für TableControl (Format)](./tablecolumnheader-element-format.md) definiert die Bezeichnung, die die Breite der Spalte und die Ausrichtung der Beschriftung für eine Spalte der Tabelle.

[TableColumnItem-Element (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) definiert die Eigenschaft oder ein Skript, dessen Wert in der Spalte der Zeile angezeigt wird.

[TableColumnItems-Element (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) definiert die Eigenschaften oder Skripts, deren Werte werden in der Zeile angezeigt.

[TableControl-Element (Format)](./tablecontrol-element-format.md) Tabellenformat für eine Sicht definiert.

[TableHeaders-Element (Format)](./tableheaders-element-format.md) die Header für die Spalten einer Tabelle definiert.

[TableRowEntries-Element (Format)](./tablerowentries-element-for-tablecontrol-format.md) definiert, die Zeilen der Tabelle.

[TableRowEntry-Element (Format)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md) definiert die Daten, die in einer Zeile der Tabelle angezeigt wird.

[Text-Element für CustomItem für Steuerelemente für die Konfiguration (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md) Klammern schließen Sie die Daten und Leerzeichen für den Einzug der das gibt Text an, die die Daten hinzugefügt werden, die durch das Steuerelement wie z. B. einer Bezeichnung angezeigt wird. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[Text-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./text-element-for-customitem-for-controls-for-view-format.md) Klammern schließen Sie die Daten und Leerzeichen für den Einzug der das gibt Text an, die die Daten hinzugefügt werden, die durch das Steuerelement wie z. B. einer Bezeichnung angezeigt wird. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[Text-Element für CustomItem (Format)](./text-element-for-customitem-for-customview-for-view-format.md) Klammern schließen Sie die Daten und Leerzeichen für den Einzug der das gibt Text an, die die Daten hinzugefügt werden, die durch das Steuerelement wie z. B. einer Bezeichnung angezeigt wird. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

[Text-Element für CustomItem für GroupBy (Format)](./text-element-for-customitem-for-groupby-format.md) Klammern schließen Sie die Daten und Leerzeichen für den Einzug der das gibt Text an, die die Daten hinzugefügt werden, die durch das Steuerelement wie z. B. einer Bezeichnung angezeigt wird. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[TypeName-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md) gibt an, einen .NET-Typ, ein, die dieser Definition des Steuerelements verwendet. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[TypeName-Element für EntrySelectedBy für Steuerelemente für die Ansicht (Format)](./typename-element-for-entryselectedby-for-controls-for-view-format.md) gibt an, einen .NET-Typ, ein, die dieser Definition des Steuerelements verwendet. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[TypeName-Element für EntrySelectedBy für CustomEntry für Ansicht (Format)](./typename-element-for-entryselectedby-for-customentry-for-view-format.md) gibt an, einen .NET-Typ, ein, die dieser Definition der Sicht benutzerdefiniertes Steuerelement verwendet. Es gibt keine Beschränkung der Anzahl von Typen, die für eine Definition angegeben werden können.

[TypeName-Element für EntrySelectedBy für EnumerableExpansion (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md) ein .NET-Typs angesprochen, die von dieser Definition erweitert wird, angibt. Dieses Element wird verwendet, bei der Definition einer Standardeinstellungen.

[TypeName-Element für EntrySelectedBy für GroupBy (Format)](./typename-element-for-entryselectedby-for-groupby-format.md) gibt an, einen .NET-Typ, ein, die dieser Definition des benutzerdefinierten Steuerelements verwendet. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[TypeName-Element für EntrySelectedBy für ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md) gibt an, ein .NET-Typ, der diesen Eintrag der Listenansicht wird verwendet. Es gibt keine Beschränkung der Anzahl von Typen, die für einen Eintrag für eine angegeben werden können.

[TypeName-Element für EntrySelectedBy für TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md) gibt einen .NET-Typ, der dieser Eintrag der Tabellenansicht verwendet. Es gibt keine Beschränkung der Anzahl von Typen, die für einen Tabelleneintrag angegeben werden können.

[TypeName-Element für EntrySelectedBy für WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md) gibt einen Typ .NET für die Definition an. Die Definition wird verwendet, wenn dieses Objekt angezeigt wird.

[TypeName-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md) gibt ein .NET-Typs angesprochen, die die Bedingung auslöst. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

[TypeName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md) gibt ein .NET-Typs angesprochen, die die Bedingung auslöst. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

[TypeName-Element für SelectionCondition für CustomControl für Ansicht (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md) gibt ein .NET-Typs angesprochen, die die Bedingung auslöst. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

[TypeName-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) gibt ein .NET-Typs angesprochen, die die Bedingung auslöst.

[TypeName-Element für SelectionCondition für GroupBy (Format)](./typename-element-for-selectioncondition-for-groupby-format.md) gibt ein .NET-Typs angesprochen, die die Bedingung auslöst. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

[TypeName-Element für SelectionCondition für EntrySelectedBy für ListControl (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) gibt ein .NET-Typs angesprochen, die die Bedingung auslöst. Wenn dieses Typs vorhanden ist, wird der Listeneintrag verwendet.

[TypeName-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) gibt ein .NET-Typs angesprochen, die die Bedingung auslöst. Wenn dieses Typs vorhanden ist, die Bedingung ist erfüllt, und die Tabellenzeile verwendet wird.

[TypeName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) gibt ein .NET-Typs angesprochen, die die Bedingung auslöst. Wenn dieses Typs vorhanden ist, wird die Definition verwendet.

[TypeName-Element für Typen (Format)](./typename-element-for-types-format.md) gibt den Typ .NET eines Objekts, das auf die Auswahl gehört.

[TypeName-Element für ViewSelectedBy (Format)](./typename-element-for-viewselectedby-format.md) gibt ein .NET-Objekt, das von der Ansicht angezeigt wird.

[-Element (Format)-Typen](./types-element-for-selectionset-format.md) definiert die .NET Objekte, die in der Auswahl festgelegt werden.

[Anzeigen des Elements (Format)](./view-element-format.md) definiert eine Ansicht, die verwendet wird, um eine oder mehrere .NET Objekte anzuzeigen.

[ViewDefinitions-Element (Format)](./viewdefinitions-element-format.md) definiert die Ansichten verwendet, um die Objekte anzuzeigen.

[ViewSelectedBy-Element (Format)](./viewselectedby-element-format.md) definiert die .NET Objekte, die von der Ansicht angezeigt werden.

[WideControl-Element (Format)](./widecontrol-element-format.md) ein Listenformat Wide (Einzelwert) für die Ansicht definiert. Diese Ansicht zeigt eine einzelne Eigenschaft-Wert oder die Skriptwert für jedes Objekt.

[WideEntries-Element (Format)](./wideentries-element-for-widecontrol-format.md) enthält die Definitionen der breiten Ansicht. Die Breite Ansicht muss eine oder mehrere Definitionen angeben.

[WideEntry-Element (Format)](./wideentry-element-for-widecontrol-format.md) enthält eine Definition der breiten Ansicht.

[WideItem-Element (Format)](./wideitem-element-for-widecontrol-format.md) definiert die Eigenschaft oder ein Skript, dessen Wert angezeigt wird.

[Width-Element (Format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) definiert die Breite einer Spalte (in Zeichen).

[Umschließen Sie (Format)-Element](./wrap-element-for-tablerowentry-for-tablecontrl-format.md) gibt an, dass der Text, der die Spaltenbreite überschreitet, die in der nächsten Zeile angezeigt wird.

[WrapTables-Element (Format)](./wraptables-element-format.md) gibt an, dass die Daten in eine Tabellenzelle in der nächsten Zeile verschoben werden, wenn die Daten länger als die Breite der Spalte ist.

## <a name="see-also"></a>Weitere Informationen

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
