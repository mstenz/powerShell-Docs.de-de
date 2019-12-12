---
title: Listenansicht (GroupBy) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: c178c4a48f9595001bcc249d5f55886fa54bb9f2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365139"
---
# <a name="list-view-groupby"></a><span data-ttu-id="8ee55-102">Listenansicht (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="8ee55-102">List View (GroupBy)</span></span>

<span data-ttu-id="8ee55-103">In diesem Beispiel wird gezeigt, wie eine Listenansicht implementiert wird, die die Zeilen der Liste in Gruppen trennt.</span><span class="sxs-lookup"><span data-stu-id="8ee55-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="8ee55-104">Diese Listenansicht zeigt die Eigenschaften des [System. ServiceProcess. ServiceController an? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -Objekte, die vom Cmdlet " [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) " zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="8ee55-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="8ee55-105">Weitere Informationen zu den Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="8ee55-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="8ee55-106">So laden Sie diese Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="8ee55-106">To load this formatting file</span></span>

1. <span data-ttu-id="8ee55-107">Kopieren Sie den XML-Code aus dem Beispiel Abschnitt dieses Themas in eine Textdatei.</span><span class="sxs-lookup"><span data-stu-id="8ee55-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="8ee55-108">Speichern Sie die Textdatei.</span><span class="sxs-lookup"><span data-stu-id="8ee55-108">Save the text file.</span></span> <span data-ttu-id="8ee55-109">Stellen Sie sicher, dass Sie die `format.ps1xml` Erweiterung der Datei hinzufügen, um Sie als Formatierungs Datei zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="8ee55-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="8ee55-110">Öffnen Sie Windows PowerShell, und führen Sie den folgenden Befehl aus, um die Formatierungs Datei in die aktuelle Sitzung zu laden: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="8ee55-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="8ee55-111">Mit dieser Formatierungs Datei wird die Anzeige eines Objekts definiert, das bereits durch eine Windows PowerShell-Formatierungs Datei definiert ist.</span><span class="sxs-lookup"><span data-stu-id="8ee55-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="8ee55-112">Sie müssen den `prependPath`-Parameter verwenden, wenn Sie das Cmdlet ausführen, und Sie können diese Formatierungs Datei nicht als Modul laden.</span><span class="sxs-lookup"><span data-stu-id="8ee55-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8ee55-113">Gegenstand</span><span class="sxs-lookup"><span data-stu-id="8ee55-113">Demonstrates</span></span>

<span data-ttu-id="8ee55-114">Diese Formatierungs Datei veranschaulicht die folgenden XML-Elemente:</span><span class="sxs-lookup"><span data-stu-id="8ee55-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="8ee55-115">Das [Name](./name-element-for-view-format.md) -Element für die Sicht.</span><span class="sxs-lookup"><span data-stu-id="8ee55-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="8ee55-116">Das [viewselectedby](./viewselectedby-element-format.md) -Element, das definiert, welche Objekte von der Sicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8ee55-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="8ee55-117">Das [GroupBy](./viewselectedby-element-format.md) -Element, das definiert, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8ee55-117">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="8ee55-118">Das [ListControl](./listcontrol-element-format.md) -Element, das definiert, welche Eigenschaft von der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8ee55-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="8ee55-119">Das [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -Element, das definiert, was in einer Zeile der Listenansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8ee55-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="8ee55-120">Das [propertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) -Element, das definiert, welche Eigenschaft angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8ee55-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="8ee55-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8ee55-121">Example</span></span>

<span data-ttu-id="8ee55-122">Der folgende XML-Code definiert eine Listenansicht, die eine neue Gruppe startet, wenn der Wert der [System. ServiceProcess. ServiceController. Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) -Eigenschaft geändert wird.</span><span class="sxs-lookup"><span data-stu-id="8ee55-122">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="8ee55-123">Wenn jede Gruppe gestartet wird, wird eine benutzerdefinierte Bezeichnung angezeigt, die den neuen Wert der Eigenschaft enthält.</span><span class="sxs-lookup"><span data-stu-id="8ee55-123">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

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

<span data-ttu-id="8ee55-124">Das folgende Beispiel zeigt, wie Windows PowerShell [System. ServiceProcess. ServiceController anzeigt? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -Objekte, nachdem diese Format Datei geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="8ee55-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="8ee55-125">Die leeren Zeilen, die vor und nach der Gruppen Bezeichnung hinzugefügt werden, werden automatisch von Windows PowerShell hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8ee55-125">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8ee55-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8ee55-126">See Also</span></span>

[<span data-ttu-id="8ee55-127">Beispiele für das Formatieren von Dateien</span><span class="sxs-lookup"><span data-stu-id="8ee55-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="8ee55-128">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="8ee55-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
