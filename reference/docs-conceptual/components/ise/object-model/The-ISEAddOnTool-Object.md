---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Das ISEAddOnTool-Objekt
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
ms.openlocfilehash: e091f37601c7a4fdaf5deff8c668b18ee7369e74
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086798"
---
# <a name="the-iseaddontool-object"></a>Das ISEAddOnTool-Objekt

Ein **ISEAddonTool**-Objekt stellt ein installiertes Add-On-Tool dar, das zusätzliche Funktionen für Windows PowerShell ISE bereitstellt. Ein Beispiel ist das Tool **Befehle**, das Sie anzeigen können, indem Sie auf **Ansicht** und dann auf **Befehl-Add-On anzeigen** klicken. Sie können dann auf dieses Tool zugreifen, indem Sie die verschiedenen verfügbaren **ISEAddOnTool**-Objekte bearbeiten.

Jedes Add-On-Tool kann dem vertikalen oder horizontalen Bereich zugeordnet werden. Der vertikale Bereich ist an den rechten Rand von Windows PowerShell ISE angedockt. Der horizontale Bereich wird am unteren Rand angedockt.

Für jede PowerShell-Registerkarte in Windows PowerShell ISE kann ein eigener Satz von Add-On-Tools installiert werden. Mit [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) und [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) können Sie auf die Sammlung der auf der derzeit ausgewählten Registerkarte verfügbaren Tools zugreifen oder die gleichen Eigenschaften für eines der **PowerShellTab**-Objekte im [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)-Sammlungsobjekt verwenden.

## <a name="methods"></a>Methoden

Es sind keine Windows PowerShell ISE-spezifischen Methoden für Objekte dieser Klasse verfügbar.

## <a name="properties"></a>Eigenschaften

### <a name="control"></a>Control

In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.

Die **Control**-Eigenschaft stellt Lesezugriff für viele der Details des Add-On-Tools „Befehle“ bereit.

```powershell
# View the properties of the Commands add-on tool.
# (assumes that it is visible in the vertical pane)
$psISE.CurrentVisibleVerticalTool.Control
HostObject                  : Microsoft.PowerShell.Host.ISE.ObjectModelRoot
Content                     :
HasContent                  :
ContentTemplate             :
ContentTemplateSelector     :
ContentStringFormat         :
BorderBrush                 :
BorderThickness             :
Background                  :
Foreground                  :
FontFamily                  :
FontSize                    :
FontStretch                 :
FontStyle                   :
FontWeight                  :
HorizontalContentAlignment  :
VerticalContentAlignment    :
TabIndex                    :
IsTabStop                   :
Padding                     :
Template                    : System.Windows.Controls.ControlTemplate
Style                       :
OverridesDefaultStyle       :
UseLayoutRounding           :
Triggers                    : {}
TemplatedParent             :
Resources                   : {System.Windows.Controls.TabItem}
DataContext                 :
BindingGroup                :
Language                    :
Name                        :
Tag                         :
InputScope                  :
ActualWidth                 : 370.75
ActualHeight                : 676.559097412109
LayoutTransform             :
Width                       :
MinWidth                    :
MaxWidth                    :
Height                      :
MinHeight                   :
MaxHeight                   :
FlowDirection               : LeftToRight
Margin                      :
HorizontalAlignment         :
VerticalAlignment           :
FocusVisualStyle            :
Cursor                      :
ForceCursor                 :
IsInitialized               : True
IsLoaded                    :
ToolTip                     :
ContextMenu                 :
Parent                      :
HasAnimatedProperties       :
InputBindings               :
CommandBindings             :
AllowDrop                   :
DesiredSize                 : 227.66,676.559097412109
IsMeasureValid              : True
IsArrangeValid              : True
RenderSize                  : 370.75,676.559097412109
RenderTransform             :
RenderTransformOrigin       :
IsMouseDirectlyOver         : False
IsMouseOver                 : False
IsStylusOver                : False
IsKeyboardFocusWithin       : False
IsMouseCaptured             :
IsMouseCaptureWithin        : False
IsStylusDirectlyOver        : False
IsStylusCaptured            :
IsStylusCaptureWithin       : False
IsKeyboardFocused           : False
IsInputMethodEnabled        :
Opacity                     :
OpacityMask                 :
BitmapEffect                :
Effect                      :
BitmapEffectInput           :
CacheMode                   :
Uid                         :
Visibility                  : Visible
ClipToBounds                : False
Clip                        :
SnapsToDevicePixels         : False
IsFocused                   :
IsEnabled                   :
IsHitTestVisible            :
IsVisible                   : True
Focusable                   :
PersistId                   : 1
IsManipulationEnabled       :
AreAnyTouchesOver           : False
AreAnyTouchesDirectlyOver   :
AreAnyTouchesCapturedWithin : False
AreAnyTouchesCaptured       :
TouchesCaptured             : {}
TouchesCapturedWithin       : {}
TouchesOver                 : {}
TouchesDirectlyOver         : {}
DependencyObjectType        : System.Windows.DependencyObjectType
IsSealed                    : False
Dispatcher                  : System.Windows.Threading.Dispatcher
```

### <a name="isvisible"></a>IsVisible

In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.

Die boolesche Eigenschaft, die angibt, ob das Add-On-Tool derzeit im zugewiesenen Bereich sichtbar ist. Wenn es sichtbar ist, können Sie die **IsVisible**-Eigenschaft auf **$false** festlegen, um das Tool auszublenden, oder die **IsVisible**-Eigenschaft auf **$true** festlegen, um ein Add-On-Tool auf der entsprechenden PowerShell-Registerkarte sichtbar zu machen. Wenn ein Add-On-Tool ausgeblendet wurde, kann darauf nicht mehr über das **CurrentVisibleHorizontalTool**-Objekt oder das **CurrentVisibleVerticalTool**-Objekt zugegriffen werden. Daher kann es auch nicht mehr mit dieser Eigenschaft für dieses Objekt sichtbar gemacht werden.

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a>Name

In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.

Die schreibgeschützte Eigenschaft, die den Namen des Add-On-Tools abruft.

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
Commands
```

## <a name="see-also"></a>Weitere Informationen

- [Das ISEAddOnToolCollection-Objekt](The-ISEAddOnToolCollection-Object.md)
- [Zweck des Windows PowerShell ISE-Skriptobjektmodells](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)