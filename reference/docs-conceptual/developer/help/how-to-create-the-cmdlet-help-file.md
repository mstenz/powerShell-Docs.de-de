---
title: Erstellen der Hilfedatei für das Cmdlet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 652e095bcce606e47cb97658f79eaca34033b239
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "86953300"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="750d2-102">Erstellen der Cmdlet-Hilfedatei</span><span class="sxs-lookup"><span data-stu-id="750d2-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="750d2-103">In diesem Abschnitt wird beschrieben, wie Sie eine gültige XML-Datei erstellen, die Inhalt für Windows PowerShell-Cmdlet-Hilfe Themen enthält.</span><span class="sxs-lookup"><span data-stu-id="750d2-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="750d2-104">In diesem Abschnitt wird erläutert, wie Sie die Hilfedatei benennen, die entsprechenden XML-Header hinzufügen und Knoten hinzufügen, die die verschiedenen Abschnitte der Cmdlet-Hilfe Inhalte enthalten.</span><span class="sxs-lookup"><span data-stu-id="750d2-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="750d2-105">Eine umfassende Ansicht einer Hilfedatei erhalten Sie, indem Sie eine der `dll-Help.xml` Dateien öffnen, die sich im Windows PowerShell-Installationsverzeichnis befinden.</span><span class="sxs-lookup"><span data-stu-id="750d2-105">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="750d2-106">Die `Microsoft.PowerShell.Commands.Management.dll-Help.xml` Datei enthält z. b. Inhalte für mehrere PowerShell-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="750d2-106">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="750d2-107">Erstellen einer Cmdlet-Hilfedatei</span><span class="sxs-lookup"><span data-stu-id="750d2-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="750d2-108">Erstellen Sie eine Textdatei, und speichern Sie Sie mithilfe der UTF8-Codierung.</span><span class="sxs-lookup"><span data-stu-id="750d2-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="750d2-109">Der Dateiname muss das folgende Format aufweisen, damit Windows PowerShell ihn als Cmdlet-Hilfedatei erkennen kann.</span><span class="sxs-lookup"><span data-stu-id="750d2-109">The filename must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

1. <span data-ttu-id="750d2-110">Fügen Sie die folgenden XML-Header der Textdatei hinzu.</span><span class="sxs-lookup"><span data-stu-id="750d2-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="750d2-111">Beachten Sie, dass die Datei mit dem Schema der Microsoft-Unterstützung Markup Sprache (MAML) überprüft wird.</span><span class="sxs-lookup"><span data-stu-id="750d2-111">Be aware that the file will be validated against the Microsoft Assistance Markup Language (MAML) schema.</span></span> <span data-ttu-id="750d2-112">PowerShell stellt derzeit keine Tools zum Überprüfen der Datei bereit.</span><span class="sxs-lookup"><span data-stu-id="750d2-112">Currently, PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

1. <span data-ttu-id="750d2-113">Fügen Sie der Cmdlet-Hilfedatei einen **Befehls** Knoten für jedes Cmdlet in der Assembly hinzu.</span><span class="sxs-lookup"><span data-stu-id="750d2-113">Add a **Command** node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="750d2-114">Jeder Knoten im **Befehls** Knoten bezieht sich auf die verschiedenen Abschnitte des Cmdlet-Hilfe Themas.</span><span class="sxs-lookup"><span data-stu-id="750d2-114">Each node within the **Command** node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="750d2-115">In der folgenden Tabelle wird das XML-Element für jeden Knoten aufgeführt, gefolgt von einer Beschreibung der einzelnen Knoten.</span><span class="sxs-lookup"><span data-stu-id="750d2-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |           <span data-ttu-id="750d2-116">Node</span><span class="sxs-lookup"><span data-stu-id="750d2-116">Node</span></span>           |                                                                                                     <span data-ttu-id="750d2-117">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="750d2-117">Description</span></span>                                                                                                     |
   | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | `<details>`              | <span data-ttu-id="750d2-118">Fügt Inhalt für die Abschnitte "Name" und "Synopsis" des Cmdlet-Hilfe Themas hinzu.</span><span class="sxs-lookup"><span data-stu-id="750d2-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="750d2-119">Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen des Cmdlet-namens und der Synchronisierungs](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)Datei.</span><span class="sxs-lookup"><span data-stu-id="750d2-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span> |
   | `<maml:description>`     | <span data-ttu-id="750d2-120">Fügt Inhalt für den Beschreibungs Abschnitt des Cmdlet-Hilfe Themas hinzu.</span><span class="sxs-lookup"><span data-stu-id="750d2-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="750d2-121">Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen der ausführlichen Beschreibung zu einem Cmdlet-Hilfethema](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="750d2-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>                    |
   | `<command:syntax>`       | <span data-ttu-id="750d2-122">Fügt Inhalt für den Syntax Abschnitt des Cmdlet-Hilfe Themas hinzu.</span><span class="sxs-lookup"><span data-stu-id="750d2-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="750d2-123">Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen von Syntax zu einem Cmdlet-Hilfethema](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="750d2-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>                                  |
   | `<command:parameters>`   | <span data-ttu-id="750d2-124">Fügt Inhalt für den Parameter Abschnitt des Cmdlet-Hilfe Themas hinzu.</span><span class="sxs-lookup"><span data-stu-id="750d2-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="750d2-125">Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen von Parametern zu einem Cmdlet-Hilfethema](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="750d2-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>                                  |
   | `<command:inputTypes>`   | <span data-ttu-id="750d2-126">Fügt Inhalt für den Abschnitt Eingaben des Hilfe Themas für das Cmdlet hinzu.</span><span class="sxs-lookup"><span data-stu-id="750d2-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="750d2-127">Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen von Eingabetypen zu einem Cmdlet-Hilfethema](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="750d2-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>                        |
   | `<command:returnValues>` | <span data-ttu-id="750d2-128">Fügt Inhalt für den Abschnitt "Outputs" des Cmdlet-Hilfe Themas hinzu.</span><span class="sxs-lookup"><span data-stu-id="750d2-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="750d2-129">Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen von Rückgabe Werten zu einem Cmdlet-Hilfethema](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="750d2-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>                   |
   | `<maml:alertset>`        | <span data-ttu-id="750d2-130">Fügt Inhalt für den Abschnitt Notizen des Cmdlet-Hilfe Themas hinzu.</span><span class="sxs-lookup"><span data-stu-id="750d2-130">Adds content for the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="750d2-131">Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen von Notizen zu einem Cmdlet-Hilfethema](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="750d2-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>                                      |
   | `<command:examples>`     | <span data-ttu-id="750d2-132">Fügt Inhalt für den Abschnitt "Beispiele" des Cmdlet-Hilfe Themas hinzu.</span><span class="sxs-lookup"><span data-stu-id="750d2-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="750d2-133">Weitere Informationen finden Sie unter [Hinzufügen von Beispielen zu einem Cmdlet-Hilfethema](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="750d2-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>                            |
   | `<maml:relatedLinks>`    | <span data-ttu-id="750d2-134">Fügt Inhalt für den Abschnitt "Verwandte Links" des Cmdlet-Hilfe Themas hinzu.</span><span class="sxs-lookup"><span data-stu-id="750d2-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="750d2-135">Weitere Informationen finden Sie [unter Hinzufügen verwandter Links zu einem Cmdlet-Hilfethema](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="750d2-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>             |

## <a name="example"></a><span data-ttu-id="750d2-136">Beispiel</span><span class="sxs-lookup"><span data-stu-id="750d2-136">Example</span></span>

 <span data-ttu-id="750d2-137">Im folgenden finden Sie ein Beispiel für einen **Befehls** Knoten, der die Knoten für die verschiedenen Abschnitte des Cmdlet-Hilfe Themas enthält.</span><span class="sxs-lookup"><span data-stu-id="750d2-137">Here is an example of a **Command** node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a><span data-ttu-id="750d2-138">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="750d2-138">See Also</span></span>

 [<span data-ttu-id="750d2-139">Vorgehensweise beim Hinzufügen des Cmdlet-namens und der Synopsis</span><span class="sxs-lookup"><span data-stu-id="750d2-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="750d2-140">Vorgehensweise beim Hinzufügen der ausführlichen Beschreibung zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="750d2-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="750d2-141">Hinzufügen einer Syntax zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="750d2-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="750d2-142">Vorgehensweise beim Hinzufügen von Parametern zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="750d2-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="750d2-143">Hinzufügen von Eingabetypen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="750d2-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="750d2-144">Hinzufügen von Rückgabewerten zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="750d2-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="750d2-145">Vorgehensweise beim Hinzufügen von Notizen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="750d2-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="750d2-146">Hinzufügen von Beispielen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="750d2-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="750d2-147">Hinzufügen von zugehörigen Verknüpfungen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="750d2-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="750d2-148">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="750d2-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
