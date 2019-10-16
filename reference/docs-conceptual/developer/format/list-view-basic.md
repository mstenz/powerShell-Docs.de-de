---
title: Listenansicht (Basic) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 3c94d8e98f179286112a417230fce659dc0b614c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362809"
---
# <a name="list-view-basic"></a><span data-ttu-id="e6d8d-102">Listenansicht (Basic)</span><span class="sxs-lookup"><span data-stu-id="e6d8d-102">List View (Basic)</span></span>

<span data-ttu-id="e6d8d-103">Dieses Beispiel zeigt, wie Sie eine einfache Listenansicht implementieren, in der [System. ServiceProcess. ServiceController angezeigt wird? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -Objekte, die vom Cmdlet " [Get-Service](/powershell/module/microsoft.powershell.management/get-service) " zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="e6d8d-103">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="e6d8d-104">Weitere Informationen zu den Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="e6d8d-104">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="e6d8d-105">So laden Sie diese Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="e6d8d-105">To load this formatting file</span></span>

1. <span data-ttu-id="e6d8d-106">Kopieren Sie den XML-Code aus dem Beispiel Abschnitt dieses Themas in eine Textdatei.</span><span class="sxs-lookup"><span data-stu-id="e6d8d-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="e6d8d-107">Speichern Sie die Textdatei.</span><span class="sxs-lookup"><span data-stu-id="e6d8d-107">Save the text file.</span></span> <span data-ttu-id="e6d8d-108">Stellen Sie sicher, dass Sie die Erweiterung "`format.ps1xml`" der Datei hinzufügen, um Sie als Formatierungs Datei zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="e6d8d-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="e6d8d-109">Öffnen Sie Windows PowerShell, und führen Sie den folgenden Befehl aus, um die Formatierungs Datei in die aktuelle Sitzung zu laden: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="e6d8d-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="e6d8d-110">Mit dieser Formatierungs Datei wird die Anzeige eines Objekts definiert, das bereits durch eine Windows PowerShell-Formatierungs Datei definiert ist.</span><span class="sxs-lookup"><span data-stu-id="e6d8d-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="e6d8d-111">Sie müssen den `prependPath`-Parameter verwenden, wenn Sie das Cmdlet ausführen, und Sie können diese Formatierungs Datei nicht als Modul laden.</span><span class="sxs-lookup"><span data-stu-id="e6d8d-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e6d8d-112">Deutlich</span><span class="sxs-lookup"><span data-stu-id="e6d8d-112">Demonstrates</span></span>

<span data-ttu-id="e6d8d-113">Diese Formatierungs Datei veranschaulicht die folgenden XML-Elemente:</span><span class="sxs-lookup"><span data-stu-id="e6d8d-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="e6d8d-114">Das [Name](./name-element-for-view-format.md) -Element für die Sicht.</span><span class="sxs-lookup"><span data-stu-id="e6d8d-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="e6d8d-115">Das [viewselectedby](./viewselectedby-element-format.md) -Element, das definiert, welche Objekte von der Sicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e6d8d-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="e6d8d-116">Das [ListControl](./listcontrol-element-format.md) -Element, das definiert, welche Eigenschaft von der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e6d8d-116">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="e6d8d-117">Das [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -Element, das definiert, was in einer Zeile der Listenansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e6d8d-117">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="e6d8d-118">Das [propertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) -Element, das definiert, welche Eigenschaft angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e6d8d-118">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="e6d8d-119">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e6d8d-119">Example</span></span>

<span data-ttu-id="e6d8d-120">Der folgende XML-Code definiert eine Listenansicht, in der vier Eigenschaften des [System. ServiceProcess. ServiceController angezeigt werden? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -Objekt.</span><span class="sxs-lookup"><span data-stu-id="e6d8d-120">The following XML defines a list view that displays four properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="e6d8d-121">In jeder Zeile wird der Name der Eigenschaft angezeigt, gefolgt vom Wert der-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="e6d8d-121">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
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
              <PropertyName>Name</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>DisplayName</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>Status</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>ServiceType</PropertyName>
            </ListItem>
          </ListItems>
        </ListEntry>
      </ListEntries>
    </ListControl>
  </View>
</Configuration>
```

<span data-ttu-id="e6d8d-122">Das folgende Beispiel zeigt, wie Windows PowerShell [System. ServiceProcess. ServiceController anzeigt? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -Objekte, nachdem diese Format Datei geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="e6d8d-122">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Name        : Fax
DisplayName : Fax
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
Status      : Running
ServiceType : Win32OwnProcess

Name        : fdPHost
DisplayName : Function Discovery Provider Host
Status      : Stopped
ServiceType : Win32ShareProcess

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
Status      : Running
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
Status      : Running
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="e6d8d-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e6d8d-123">See Also</span></span>

[<span data-ttu-id="e6d8d-124">Beispiele für das Formatieren von Dateien</span><span class="sxs-lookup"><span data-stu-id="e6d8d-124">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="e6d8d-125">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="e6d8d-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
