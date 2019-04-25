---
title: Breite Ansicht (-GroupBy) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083653"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="78b8b-102">Breite Ansicht (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="78b8b-102">Wide View (GroupBy)</span></span>

<span data-ttu-id="78b8b-103">Dieses Beispiel zeigt, wie Sie eine Breite Ansicht zu implementieren, die Gruppen von anzeigt [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) zurückgegebenen Objekte die `Get-Service` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="78b8b-103">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="78b8b-104">Weitere Informationen zu den Komponenten der eine Breite Ansicht, finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="78b8b-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="78b8b-105">Laden Sie diese Formatierungsdatei</span><span class="sxs-lookup"><span data-stu-id="78b8b-105">To load this formatting file</span></span>

1. <span data-ttu-id="78b8b-106">Kopieren Sie den XML-Code in eine Textdatei aus dem Abschnitt "Beispiel" dieses Themas.</span><span class="sxs-lookup"><span data-stu-id="78b8b-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="78b8b-107">Speichern Sie die Textdatei ein.</span><span class="sxs-lookup"><span data-stu-id="78b8b-107">Save the text file.</span></span> <span data-ttu-id="78b8b-108">Achten Sie darauf, dass Sie zum Hinzufügen der `format.ps1xml` Erweiterung der Datei, die sie als eine Formatierungsdatei zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="78b8b-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="78b8b-109">Öffnen Sie Windows PowerShell, und führen Sie den folgenden Befehl aus, um die Formatierungsdatei in der aktuellen Sitzung zu laden: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="78b8b-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="78b8b-110">Diese Formatierung Datei definiert die Anzeige eines Objekts, das bereits von einer Windows PowerShell-Formatierungsdateien definiert ist.</span><span class="sxs-lookup"><span data-stu-id="78b8b-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="78b8b-111">Verwenden Sie die `prependPath` Parameter an, wenn Sie das Cmdlet ausführen, und Sie nicht werden diese Formatierung geladen können Datei als Modul.</span><span class="sxs-lookup"><span data-stu-id="78b8b-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="78b8b-112">Zeigt</span><span class="sxs-lookup"><span data-stu-id="78b8b-112">Demonstrates</span></span>

<span data-ttu-id="78b8b-113">Diese Formatierung Datei veranschaulicht die folgenden XML-Elemente:</span><span class="sxs-lookup"><span data-stu-id="78b8b-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="78b8b-114">Die [Namen](./name-element-for-view-format.md) -Element für die Ansicht.</span><span class="sxs-lookup"><span data-stu-id="78b8b-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="78b8b-115">Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element, das definiert, welche Objekte von der Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="78b8b-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="78b8b-116">Die [GroupBy](./groupby-element-for-view-format.md) Element, das definiert, wenn eine neue Gruppe angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="78b8b-116">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="78b8b-117">Die [WideItem](./wideitem-element-for-widecontrol-format.md) -Element, das definiert, welche Eigenschaft von der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="78b8b-117">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="78b8b-118">Beispiel</span><span class="sxs-lookup"><span data-stu-id="78b8b-118">Example</span></span>

<span data-ttu-id="78b8b-119">Das folgende XML definiert eine Breite Ansicht, in dem Gruppen von Objekten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="78b8b-119">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="78b8b-120">Jede neue Gruppe wird gestartet. wenn der Wert des der [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) eigenschaftenänderungen.</span><span class="sxs-lookup"><span data-stu-id="78b8b-120">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

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

<span data-ttu-id="78b8b-121">Das folgende Beispiel zeigt, wie Windows PowerShell zeigt den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) Objekte nach dem Laden dieser Formatdatei.</span><span class="sxs-lookup"><span data-stu-id="78b8b-121">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="78b8b-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="78b8b-122">See Also</span></span>

[<span data-ttu-id="78b8b-123">Beispiele für die Formatierungsdateien</span><span class="sxs-lookup"><span data-stu-id="78b8b-123">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="78b8b-124">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="78b8b-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
