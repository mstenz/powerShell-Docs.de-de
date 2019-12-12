---
title: Breite Ansicht (GroupBy) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367949"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="fd14c-102">Breite Ansicht (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="fd14c-102">Wide View (GroupBy)</span></span>

<span data-ttu-id="fd14c-103">In diesem Beispiel wird gezeigt, wie eine breite Ansicht implementiert wird, in der Gruppen von [System. ServiceProcess. ServiceController angezeigt werden. Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -Objekte, die vom Cmdlet "`Get-Service`" zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="fd14c-103">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="fd14c-104">Weitere Informationen zu den Komponenten einer breiten Ansicht finden Sie unter [Erstellen einer breiten Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="fd14c-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="fd14c-105">So laden Sie diese Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="fd14c-105">To load this formatting file</span></span>

1. <span data-ttu-id="fd14c-106">Kopieren Sie den XML-Code aus dem Beispiel Abschnitt dieses Themas in eine Textdatei.</span><span class="sxs-lookup"><span data-stu-id="fd14c-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="fd14c-107">Speichern Sie die Textdatei.</span><span class="sxs-lookup"><span data-stu-id="fd14c-107">Save the text file.</span></span> <span data-ttu-id="fd14c-108">Stellen Sie sicher, dass Sie die `format.ps1xml` Erweiterung der Datei hinzufügen, um Sie als Formatierungs Datei zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="fd14c-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="fd14c-109">Öffnen Sie Windows PowerShell, und führen Sie den folgenden Befehl aus, um die Formatierungs Datei in die aktuelle Sitzung zu laden: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="fd14c-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="fd14c-110">Mit dieser Formatierungs Datei wird die Anzeige eines Objekts definiert, das bereits von Windows PowerShell-Formatierungs Dateien definiert wird.</span><span class="sxs-lookup"><span data-stu-id="fd14c-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="fd14c-111">Sie müssen den `prependPath`-Parameter verwenden, wenn Sie das Cmdlet ausführen, und Sie können diese Formatierungs Datei nicht als Modul laden.</span><span class="sxs-lookup"><span data-stu-id="fd14c-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="fd14c-112">Gegenstand</span><span class="sxs-lookup"><span data-stu-id="fd14c-112">Demonstrates</span></span>

<span data-ttu-id="fd14c-113">Diese Formatierungs Datei veranschaulicht die folgenden XML-Elemente:</span><span class="sxs-lookup"><span data-stu-id="fd14c-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="fd14c-114">Das [Name](./name-element-for-view-format.md) -Element für die Sicht.</span><span class="sxs-lookup"><span data-stu-id="fd14c-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="fd14c-115">Das [viewselectedby](./viewselectedby-element-format.md) -Element, das definiert, welche Objekte von der Sicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="fd14c-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="fd14c-116">Das [GroupBy](./groupby-element-for-view-format.md) -Element, das definiert, wann eine neue Gruppe angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="fd14c-116">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="fd14c-117">Das [wideitem](./wideitem-element-for-widecontrol-format.md) -Element, das definiert, welche Eigenschaft von der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="fd14c-117">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="fd14c-118">Beispiel</span><span class="sxs-lookup"><span data-stu-id="fd14c-118">Example</span></span>

<span data-ttu-id="fd14c-119">Der folgende XML-Code definiert eine breite Ansicht, in der Gruppen von Objekten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="fd14c-119">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="fd14c-120">Jede neue Gruppe wird gestartet, wenn sich der Wert der [System. ServiceProcess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) -Eigenschaft ändert.</span><span class="sxs-lookup"><span data-stu-id="fd14c-120">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="fd14c-121">Das folgende Beispiel zeigt, wie Windows PowerShell [System. ServiceProcess. ServiceController anzeigt? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -Objekte, nachdem diese Format Datei geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="fd14c-121">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="fd14c-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fd14c-122">See Also</span></span>

[<span data-ttu-id="fd14c-123">Beispiele für das Formatieren von Dateien</span><span class="sxs-lookup"><span data-stu-id="fd14c-123">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="fd14c-124">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="fd14c-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
