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
ms.openlocfilehash: 1c683693c331ccfaf7355a0dd51801ed6fd39b3b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853306"
---
# <a name="list-view-basic"></a><span data-ttu-id="8b372-102">Listenansicht (Basic)</span><span class="sxs-lookup"><span data-stu-id="8b372-102">List View (Basic)</span></span>

<span data-ttu-id="8b372-103">Dieses Beispiel zeigt, wie Sie eine einfache Listenansicht zu implementieren, die zeigt die [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) zurückgegebenen Objekte die [Get-Service](/powershell/module/microsoft.powershell.management/get-service) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8b372-103">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="8b372-104">Weitere Informationen zu den Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="8b372-104">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>
<span data-ttu-id="8b372-105">Dieses Beispiel zeigt, wie Sie eine einfache Listenansicht zu implementieren, die zeigt die [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) zurückgegebenen Objekte die [Get-Service](/powershell/module/microsoft.powershell.management/get-service) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8b372-105">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="8b372-106">Weitere Informationen zu den Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="8b372-106">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="8b372-107">Laden Sie diese Formatierungsdatei</span><span class="sxs-lookup"><span data-stu-id="8b372-107">To load this formatting file</span></span>

1. <span data-ttu-id="8b372-108">Kopieren Sie den XML-Code in eine Textdatei aus dem Abschnitt "Beispiel" dieses Themas.</span><span class="sxs-lookup"><span data-stu-id="8b372-108">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="8b372-109">Speichern Sie die Textdatei ein.</span><span class="sxs-lookup"><span data-stu-id="8b372-109">Save the text file.</span></span> <span data-ttu-id="8b372-110">Achten Sie darauf, dass Sie zum Hinzufügen der `format.ps1xml` Erweiterung der Datei, die sie als eine Formatierungsdatei zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="8b372-110">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="8b372-111">Öffnen Sie Windows PowerShell, und führen Sie den folgenden Befehl aus, um die Formatierungsdatei in der aktuellen Sitzung zu laden: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="8b372-111">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="8b372-112">Diese Formatierung Datei definiert die Anzeige eines Objekts, das bereits von einer Windows PowerShell-Formatierung-Datei definiert ist.</span><span class="sxs-lookup"><span data-stu-id="8b372-112">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="8b372-113">Verwenden Sie die `prependPath` Parameter an, wenn Sie das Cmdlet ausführen, und Sie nicht werden diese Formatierung geladen können Datei als Modul.</span><span class="sxs-lookup"><span data-stu-id="8b372-113">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8b372-114">Veranschaulicht</span><span class="sxs-lookup"><span data-stu-id="8b372-114">Demonstrates</span></span>

<span data-ttu-id="8b372-115">Diese Formatierung Datei veranschaulicht die folgenden XML-Elemente:</span><span class="sxs-lookup"><span data-stu-id="8b372-115">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="8b372-116">Die [Namen](./name-element-for-view-format.md) -Element für die Ansicht.</span><span class="sxs-lookup"><span data-stu-id="8b372-116">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="8b372-117">Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element, das definiert, welche Objekte von der Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8b372-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="8b372-118">Die [ListControl](./listcontrol-element-format.md) -Element, das definiert, welche Eigenschaft von der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8b372-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="8b372-119">Die [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) Element, das definiert, was in einer Zeile in der Listenansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8b372-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="8b372-120">Die [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) -Element, das definiert, welche Eigenschaft angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8b372-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="8b372-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8b372-121">Example</span></span>

<span data-ttu-id="8b372-122">Das folgende XML definiert eine Listenansicht, in dem vier Eigenschaften angezeigt. die [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) Objekt.</span><span class="sxs-lookup"><span data-stu-id="8b372-122">The following XML defines a list view that displays four properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="8b372-123">In jeder Zeile wird der Name der Eigenschaft gefolgt vom Wert der Eigenschaft angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b372-123">In each row, the name of the property is displayed followed by the value of the property.</span></span>

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

<span data-ttu-id="8b372-124">Das folgende Beispiel zeigt, wie Windows PowerShell zeigt den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) Objekte nach dem Laden dieser Formatdatei.</span><span class="sxs-lookup"><span data-stu-id="8b372-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8b372-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8b372-125">See Also</span></span>

[<span data-ttu-id="8b372-126">Beispiele für die Formatierungsdateien</span><span class="sxs-lookup"><span data-stu-id="8b372-126">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="8b372-127">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b372-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
