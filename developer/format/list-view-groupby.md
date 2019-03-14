---
title: Listenansicht (-GroupBy) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: c178c4a48f9595001bcc249d5f55886fa54bb9f2
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794439"
---
# <a name="list-view-groupby"></a><span data-ttu-id="d8441-102">Listenansicht (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="d8441-102">List View (GroupBy)</span></span>

<span data-ttu-id="d8441-103">Dieses Beispiel zeigt, wie Sie eine Listenansicht zu implementieren, die die Zeilen aus der Liste in Gruppen unterteilt.</span><span class="sxs-lookup"><span data-stu-id="d8441-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="d8441-104">Diese Liste zeigt der Eigenschaften der [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) zurückgegebenen Objekte die [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d8441-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="d8441-105">Weitere Informationen zu den Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="d8441-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="d8441-106">Laden Sie diese Formatierungsdatei</span><span class="sxs-lookup"><span data-stu-id="d8441-106">To load this formatting file</span></span>

1. <span data-ttu-id="d8441-107">Kopieren Sie den XML-Code in eine Textdatei aus dem Abschnitt "Beispiel" dieses Themas.</span><span class="sxs-lookup"><span data-stu-id="d8441-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="d8441-108">Speichern Sie die Textdatei ein.</span><span class="sxs-lookup"><span data-stu-id="d8441-108">Save the text file.</span></span> <span data-ttu-id="d8441-109">Achten Sie darauf, dass Sie zum Hinzufügen der `format.ps1xml` Erweiterung der Datei, die sie als eine Formatierungsdatei zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="d8441-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="d8441-110">Öffnen Sie Windows PowerShell, und führen Sie den folgenden Befehl aus, um die Formatierungsdatei in der aktuellen Sitzung zu laden: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="d8441-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="d8441-111">Diese Formatierung Datei definiert die Anzeige eines Objekts, das bereits von einer Windows PowerShell-Formatierung-Datei definiert ist.</span><span class="sxs-lookup"><span data-stu-id="d8441-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="d8441-112">Verwenden Sie die `prependPath` Parameter an, wenn Sie das Cmdlet ausführen, und Sie nicht werden diese Formatierung geladen können Datei als Modul.</span><span class="sxs-lookup"><span data-stu-id="d8441-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d8441-113">Veranschaulicht</span><span class="sxs-lookup"><span data-stu-id="d8441-113">Demonstrates</span></span>

<span data-ttu-id="d8441-114">Diese Formatierung Datei veranschaulicht die folgenden XML-Elemente:</span><span class="sxs-lookup"><span data-stu-id="d8441-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="d8441-115">Die [Namen](./name-element-for-view-format.md) -Element für die Ansicht.</span><span class="sxs-lookup"><span data-stu-id="d8441-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="d8441-116">Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element, das definiert, welche Objekte von der Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d8441-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="d8441-117">Die [GroupBy](./viewselectedby-element-format.md) -Element, das definiert, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d8441-117">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="d8441-118">Die [ListControl](./listcontrol-element-format.md) -Element, das definiert, welche Eigenschaft von der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d8441-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="d8441-119">Die [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) Element, das definiert, was in einer Zeile in der Listenansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d8441-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="d8441-120">Die [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) -Element, das definiert, welche Eigenschaft angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d8441-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="d8441-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d8441-121">Example</span></span>

<span data-ttu-id="d8441-122">Die folgende XML-Code definiert eine Listenansicht, die einen neuen startet Gruppe jedes Mal, wenn der Wert des der [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) eigenschaftenänderungen.</span><span class="sxs-lookup"><span data-stu-id="d8441-122">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="d8441-123">Wenn jede Gruppe gestartet wird, wird eine benutzerdefinierte Bezeichnung angezeigt, die den neuen Wert der Eigenschaft enthält.</span><span class="sxs-lookup"><span data-stu-id="d8441-123">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.ServiceProcess.ServiceController</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>Status</PropertyName>
        <Label>New Service Status</Label>
      </GroupBy>
      <ListControl>
        <ListEntries>
          <ListEntry>
            <ListItems>
              <ListItem>
                <PropertyName>Name</PropertyName>
              </ListItem>
              <ListItem>
                <PropertyName>DisplayName</PropertyName>
              </ListItem>
              <ListItem>
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

<span data-ttu-id="d8441-124">Das folgende Beispiel zeigt, wie Windows PowerShell zeigt den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) Objekte nach dem Laden dieser Formatdatei.</span><span class="sxs-lookup"><span data-stu-id="d8441-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="d8441-125">Die leeren Zeilen hinzugefügt werden, vor und nach der datenreihengruppenbeschriftung werden von Windows PowerShell automatisch hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d8441-125">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

```powershell
Get-Service f*
```

```output
   New Service Status: Stopped

Name        : Fax
DisplayName : Fax
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
ServiceType : Win32OwnProcess

   New Service Status: Stopped

Name        : fdPHost
DisplayName : Function Discovery Provider Host
ServiceType : Win32ShareProcess

   New Service Status: Running

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
ServiceType : Win32ShareProcess

   New Service Status: Stopped

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="d8441-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d8441-126">See Also</span></span>

[<span data-ttu-id="d8441-127">Beispiele für die Formatierungsdateien</span><span class="sxs-lookup"><span data-stu-id="d8441-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="d8441-128">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="d8441-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
