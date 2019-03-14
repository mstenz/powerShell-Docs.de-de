---
title: Listenansicht (Bezeichnungen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 27de41c88e224f7610c10a764e51524016ecc8cb
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794823"
---
# <a name="list-view-labels"></a><span data-ttu-id="5355b-102">Listenansicht (Label)</span><span class="sxs-lookup"><span data-stu-id="5355b-102">List View (Labels)</span></span>

<span data-ttu-id="5355b-103">Dieses Beispiel zeigt, wie Sie eine Listenansicht zu implementieren, in dem eine benutzerdefinierte Bezeichnung für jede Zeile der Liste angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5355b-103">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="5355b-104">Diese Liste zeigt der Eigenschaften der [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) von zurückgegebene Objekt der [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5355b-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="5355b-105">Weitere Informationen zu den Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="5355b-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="5355b-106">Laden Sie diese Formatierungsdatei</span><span class="sxs-lookup"><span data-stu-id="5355b-106">To load this formatting file</span></span>

1. <span data-ttu-id="5355b-107">Kopieren Sie den XML-Code in eine Textdatei aus dem Abschnitt "Beispiel" dieses Themas.</span><span class="sxs-lookup"><span data-stu-id="5355b-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="5355b-108">Speichern Sie die Textdatei ein.</span><span class="sxs-lookup"><span data-stu-id="5355b-108">Save the text file.</span></span> <span data-ttu-id="5355b-109">Achten Sie darauf, dass Sie zum Hinzufügen der `format.ps1xml` Erweiterung der Datei, die sie als eine Formatierungsdatei zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="5355b-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="5355b-110">Öffnen Sie Windows PowerShell, und führen Sie den folgenden Befehl aus, um die Formatierungsdatei in der aktuellen Sitzung zu laden: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="5355b-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="5355b-111">Diese Formatierung Datei definiert die Anzeige eines Objekts, das bereits von einer Windows PowerShell-Formatierung-Datei definiert ist.</span><span class="sxs-lookup"><span data-stu-id="5355b-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="5355b-112">Verwenden Sie die `prependPath` Parameter an, wenn Sie das Cmdlet ausführen, und Sie nicht werden diese Formatierung geladen können Datei als Modul.</span><span class="sxs-lookup"><span data-stu-id="5355b-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="5355b-113">Veranschaulicht</span><span class="sxs-lookup"><span data-stu-id="5355b-113">Demonstrates</span></span>

<span data-ttu-id="5355b-114">Diese Formatierung Datei veranschaulicht die folgenden XML-Elemente:</span><span class="sxs-lookup"><span data-stu-id="5355b-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="5355b-115">Die [Namen](./name-element-for-view-format.md) -Element für die Ansicht.</span><span class="sxs-lookup"><span data-stu-id="5355b-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="5355b-116">Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element, das definiert, welche Objekte von der Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5355b-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="5355b-117">Die [ListControl](./listcontrol-element-format.md) -Element, das definiert, welche Eigenschaft von der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5355b-117">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="5355b-118">Die [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) Element, das definiert, was in einer Zeile in der Listenansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5355b-118">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="5355b-119">Die [Bezeichnung](./label-element-for-listitem-for-listcontrol-format.md) Element, das definiert, was in einer Zeile in der Listenansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5355b-119">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="5355b-120">Die [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) -Element, das definiert, welche Eigenschaft angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5355b-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="5355b-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="5355b-121">Example</span></span>

<span data-ttu-id="5355b-122">Das folgende XML definiert eine Listenansicht, in dem eine benutzerdefinierte Bezeichnung in jeder Zeile angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5355b-122">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="5355b-123">In diesem Fall enthält die Bezeichnung, des Eigenschaftsnamens mit jeder Buchstabe groß geschrieben und das Wort "Property".</span><span class="sxs-lookup"><span data-stu-id="5355b-123">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="5355b-124">In jeder Zeile wird der Name der Eigenschaft gefolgt vom Wert der Eigenschaft angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5355b-124">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>

  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="5355b-125">Das folgende Beispiel zeigt, wie Windows PowerShell zeigt den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) Objekte nach dem Laden dieser Formatdatei.</span><span class="sxs-lookup"><span data-stu-id="5355b-125">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="5355b-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5355b-126">See Also</span></span>

[<span data-ttu-id="5355b-127">Beispiele für die Formatierungsdateien</span><span class="sxs-lookup"><span data-stu-id="5355b-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="5355b-128">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="5355b-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
