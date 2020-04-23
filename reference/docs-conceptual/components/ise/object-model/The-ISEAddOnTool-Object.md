---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Das ISEAddOnTool-Objekt
ms.openlocfilehash: a5357005ec1a883f5a14882a42e3150e09ff33a2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736129"
---
# <a name="the-iseaddontool-object"></a><span data-ttu-id="a4b47-103">Das ISEAddOnTool-Objekt</span><span class="sxs-lookup"><span data-stu-id="a4b47-103">The ISEAddOnTool Object</span></span>

<span data-ttu-id="a4b47-104">Ein **ISEAddonTool**-Objekt stellt ein installiertes Add-On-Tool dar, das zusätzliche Funktionen für Windows PowerShell ISE bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="a4b47-104">An **ISEAddonTool** object represents an installed add-on tool that provides additional functionality toWindows PowerShell ISE.</span></span> <span data-ttu-id="a4b47-105">Ein Beispiel ist das Tool **Befehle**, das Sie anzeigen können, indem Sie auf **Ansicht** und dann auf **Befehl-Add-On anzeigen** klicken.</span><span class="sxs-lookup"><span data-stu-id="a4b47-105">An example is the **Commands** tool that you can display by clicking **View**, then **Show Command Add-on**.</span></span> <span data-ttu-id="a4b47-106">Sie können dann auf dieses Tool zugreifen, indem Sie die verschiedenen verfügbaren **ISEAddOnTool**-Objekte bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="a4b47-106">This tool is then accessible to you by manipulating the various available **ISEAddOnTool** objects.</span></span>

<span data-ttu-id="a4b47-107">Jedes Add-On-Tool kann dem vertikalen oder horizontalen Bereich zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="a4b47-107">Each add-on tool can be associated with either the vertical pane or the horizontal pane.</span></span> <span data-ttu-id="a4b47-108">Der vertikale Bereich ist an den rechten Rand von Windows PowerShell ISE angedockt.</span><span class="sxs-lookup"><span data-stu-id="a4b47-108">The vertical pane is docked to the right edge of Windows PowerShell ISE.</span></span> <span data-ttu-id="a4b47-109">Der horizontale Bereich wird am unteren Rand angedockt.</span><span class="sxs-lookup"><span data-stu-id="a4b47-109">The horizontal pane is docked to the bottom edge.</span></span>

<span data-ttu-id="a4b47-110">Für jede PowerShell-Registerkarte in Windows PowerShell ISE kann ein eigener Satz von Add-On-Tools installiert werden.</span><span class="sxs-lookup"><span data-stu-id="a4b47-110">Each PowerShell tab in Windows PowerShell ISE can have its own set of add-on tools installed.</span></span> <span data-ttu-id="a4b47-111">Mit [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) und [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) können Sie auf die Sammlung der auf der derzeit ausgewählten Registerkarte verfügbaren Tools zugreifen oder die gleichen Eigenschaften für eines der **PowerShellTab**-Objekte im [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)-Sammlungsobjekt verwenden.</span><span class="sxs-lookup"><span data-stu-id="a4b47-111">See [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) and [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) to access the collection of tools available to the currently selected tab or the same properties on any of the **PowerShellTab** objects in the [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) collection object.</span></span>

## <a name="methods"></a><span data-ttu-id="a4b47-112">Methoden</span><span class="sxs-lookup"><span data-stu-id="a4b47-112">Methods</span></span>

<span data-ttu-id="a4b47-113">Es sind keine Windows PowerShell ISE-spezifischen Methoden für Objekte dieser Klasse verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a4b47-113">There are no Windows PowerShell ISE-specific methods available for objects of this class.</span></span>

## <a name="properties"></a><span data-ttu-id="a4b47-114">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="a4b47-114">Properties</span></span>

### <a name="control"></a><span data-ttu-id="a4b47-115">Control</span><span class="sxs-lookup"><span data-stu-id="a4b47-115">Control</span></span>

<span data-ttu-id="a4b47-116">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="a4b47-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="a4b47-117">Die **Control**-Eigenschaft stellt Lesezugriff für viele der Details des Add-On-Tools „Befehle“ bereit.</span><span class="sxs-lookup"><span data-stu-id="a4b47-117">The **Control** property provides read access to many of the details of the Commands add-on tool.</span></span>

```powershell
# View the properties of the Commands add-on tool.
# (assumes that it is visible in the vertical pane)
$psISE.CurrentVisibleVerticalTool.Control
```

```Output
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

### <a name="isvisible"></a><span data-ttu-id="a4b47-118">Sichtbar</span><span class="sxs-lookup"><span data-stu-id="a4b47-118">IsVisible</span></span>

<span data-ttu-id="a4b47-119">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="a4b47-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="a4b47-120">Die boolesche Eigenschaft, die angibt, ob das Add-On-Tool derzeit im zugewiesenen Bereich sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="a4b47-120">The Boolean property that indicates whether the add-on tool is currently visible in its assigned pane.</span></span> <span data-ttu-id="a4b47-121">Sofern sichtbar, können Sie die **IsVisible**-Eigenschaft auf `$false` festlegen, um das Tool auszublenden. Oder Sie legen die **IsVisible**-Eigenschaft auf `$true` fest, um ein Add-On-Tool auf der zugehörigen PowerShell-Registerkarte anzuzeigen. Wenn ein Add-On-Tool ausgeblendet wurde, kann darauf nicht mehr über das **CurrentVisibleHorizontalTool**-Objekt oder das **CurrentVisibleVerticalTool**-Objekt zugegriffen werden. Daher kann es auch nicht mehr mit dieser Eigenschaft für dieses Objekt sichtbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="a4b47-121">If it is visible, you can set the **IsVisible** property to `$false` to hide the tool, or set the **IsVisible** property to `$true` to make an add-on tool visible on its PowerShell tab. Note that after an add-on tool is hidden, it is no longer accessible through the **CurrentVisibleHorizontalTool** or **CurrentVisibleVerticalTool** objects, and therefore cannot be made visible by using this property on that object.</span></span>

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a><span data-ttu-id="a4b47-122">Name</span><span class="sxs-lookup"><span data-stu-id="a4b47-122">Name</span></span>

<span data-ttu-id="a4b47-123">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="a4b47-123">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="a4b47-124">Die schreibgeschützte Eigenschaft, die den Namen des Add-On-Tools abruft.</span><span class="sxs-lookup"><span data-stu-id="a4b47-124">The read-only property that gets the name of the add-on tool.</span></span>

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
```

```Output
Commands
```

## <a name="see-also"></a><span data-ttu-id="a4b47-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a4b47-125">See Also</span></span>

- [<span data-ttu-id="a4b47-126">Das ISEAddOnToolCollection-Objekt</span><span class="sxs-lookup"><span data-stu-id="a4b47-126">The ISEAddOnToolCollection Object</span></span>](The-ISEAddOnToolCollection-Object.md)
- [<span data-ttu-id="a4b47-127">Zweck des Windows PowerShell ISE-Skriptobjektmodells</span><span class="sxs-lookup"><span data-stu-id="a4b47-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="a4b47-128">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="a4b47-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
