---
title: 'Vorgehensweise: Erstellen Sie die Cmdlet-Hilfedatei | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858976"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="d4cf6-102">Erstellen der Cmdlet-Hilfedatei</span><span class="sxs-lookup"><span data-stu-id="d4cf6-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="d4cf6-103">In diesem Abschnitt wird beschrieben, wie Sie eine gültige XML-Datei zu erstellen, die Inhalt für Windows PowerShell-Cmdlet-Hilfethemen enthält.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="d4cf6-104">In diesem Abschnitt wird erläutert, wie Sie die Datei zu benennen, wie Sie die entsprechenden XML-Header hinzufügen und Gewusst wie: Hinzufügen von Knoten, die die verschiedenen Abschnitte der mit dem Cmdlet-Hilfe-Inhalt enthält.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="d4cf6-105">Eine vollständige Übersicht der eine Hilfedatei öffnen eine der Dll-Help.xml Dateien im Installationsverzeichnis von Windows PowerShell gefunden.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="d4cf6-106">Beispielsweise enthält die Microsoft.PowerShell.Commands.Management.dll-Help.xml-Datei Inhalte für eine Reihe von Windows PowerShell-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="d4cf6-107">Vorgehensweise: erstellen eine Cmdlet-Hilfedatei</span><span class="sxs-lookup"><span data-stu-id="d4cf6-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="d4cf6-108">Erstellen Sie eine Textdatei, und speichern sie die mit UTF8-Codierung.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="d4cf6-109">Der Dateiname muss das folgende Format aufweisen, so, dass Windows PowerShell als ein Cmdlet-Hilfedatei erkannt werden können.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-109">The file name must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. <span data-ttu-id="d4cf6-110">Fügen Sie die folgenden XML-Header in die Textdatei ein.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="d4cf6-111">Denken Sie daran, dass das Schema mit mehreren Agents Modeling Language (MAML) die Datei überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-111">Be aware that the file will be validated against the Multi-Agent Modeling Language (MAML) schema.</span></span> <span data-ttu-id="d4cf6-112">Windows PowerShell bietet derzeit keine Tools zum Überprüfen der das.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-112">Currently, Windows PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. <span data-ttu-id="d4cf6-113">Fügen Sie einen befehlsknoten der Cmdlet-Hilfedatei für die einzelnen Cmdlets in der Assembly hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-113">Add a Command node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="d4cf6-114">Jeder Knoten innerhalb des Knotens Befehl bezieht sich auf die verschiedenen Abschnitte der Cmdlet-Hilfethemas.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-114">Each node within the Command node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="d4cf6-115">Die folgende Tabelle enthält die XML-Element für jeden Knoten, gefolgt von einer Beschreibung der einzelnen Knoten.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |<span data-ttu-id="d4cf6-116">Knoten</span><span class="sxs-lookup"><span data-stu-id="d4cf6-116">Node</span></span>|<span data-ttu-id="d4cf6-117">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d4cf6-117">Description</span></span>|
   |----------|-----------------|
   |`<details>`|<span data-ttu-id="d4cf6-118">Fügt Inhalt für die Abschnitte Namen und eine Zusammenfassung der Cmdlet-Hilfethemas hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="d4cf6-119">Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen der Cmdlet-Namen und die Zusammenfassung](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="d4cf6-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:description>`|<span data-ttu-id="d4cf6-120">Fügt Inhalt für den Abschnitt "Beschreibung" der Cmdlet-Hilfethemas hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="d4cf6-121">Weitere Informationen finden Sie unter [die ausführliche Beschreibung zu einem Cmdlet-Hilfethemas hinzufügen](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="d4cf6-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>|
   |`<command:syntax>`|<span data-ttu-id="d4cf6-122">Fügt Inhalt für den Abschnitt "SYNTAX" von der Cmdlet-Hilfethemas hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="d4cf6-123">Weitere Informationen finden Sie unter [wie hinzufügen-Syntax zu einem Cmdlet-Hilfethemas](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="d4cf6-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:parameters>`|<span data-ttu-id="d4cf6-124">Fügt Inhalt für die Cmdlet-Hilfethemas im Parameter-Abschnitt hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="d4cf6-125">Weitere Informationen finden Sie unter [wie Hinzufügen von Parametern zu einem Cmdlet-Hilfethemas](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="d4cf6-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>|
   |`<command:inputTypes>`|<span data-ttu-id="d4cf6-126">Fügt Inhalt für den Abschnitt "EINGABEN" des Cmdlet-Hilfethemas hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="d4cf6-127">Weitere Informationen finden Sie unter [wie Eingabetypen hinzufügen zu einem Cmdlet-Hilfethemas](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="d4cf6-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:returnValues>`|<span data-ttu-id="d4cf6-128">Fügt Inhalt für den Abschnitt "OUTPUTS" der Cmdlet-Hilfethemas hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="d4cf6-129">Weitere Informationen finden Sie unter [wie Hinzufügen von Rückgabewerten zu einem Cmdlet-Hilfethemas](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="d4cf6-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:alertset>`|<span data-ttu-id="d4cf6-130">Abschnitt "Hinweise" des Cmdlet-Hilfethemas wird Inhalt hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-130">Adds content to the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="d4cf6-131">Weitere Informationen finden Sie unter [hinzufügen – Anmerkungen zu dieser zu einem Cmdlet-Hilfethemas](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="d4cf6-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:examples>`|<span data-ttu-id="d4cf6-132">Fügt Inhalt für den Beispielabschnitt des Cmdlet-Hilfethemas hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="d4cf6-133">Weitere Informationen finden Sie unter [wie Beispielen hinzufügen zu einem Cmdlet-Hilfethemas](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="d4cf6-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:relatedLinks>`|<span data-ttu-id="d4cf6-134">Fügt Inhalt für den Abschnitt "Verwandte LINKS" des Cmdlet-Hilfethemas hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="d4cf6-135">Weitere Informationen finden Sie unter [wie verwandte Links hinzufügen, eine Cmdlet-Hilfethemas](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="d4cf6-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>|

## <a name="example"></a><span data-ttu-id="d4cf6-136">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d4cf6-136">Example</span></span>

 <span data-ttu-id="d4cf6-137">Hier ist ein Beispiel für einen befehlsknoten, der die Knoten für die verschiedenen Abschnitte der Cmdlet-Hilfethemas enthält.</span><span class="sxs-lookup"><span data-stu-id="d4cf6-137">Here is an example of a Command node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d4cf6-138">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d4cf6-138">See Also</span></span>

 [<span data-ttu-id="d4cf6-139">So fügen Sie die Cmdlet-Namen und die Zusammenfassung hinzu</span><span class="sxs-lookup"><span data-stu-id="d4cf6-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="d4cf6-140">So fügen Sie die ausführliche Beschreibung zu einem Cmdlet-Hilfethema hinzu</span><span class="sxs-lookup"><span data-stu-id="d4cf6-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="d4cf6-141">So fügen Sie die Syntax für ein Cmdlet-Hilfethema hinzu</span><span class="sxs-lookup"><span data-stu-id="d4cf6-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="d4cf6-142">Gewusst wie: Hinzufügen von Parametern zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="d4cf6-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="d4cf6-143">Wie Sie eine Cmdlet-Hilfethemas Eingabetypen hinzufügen</span><span class="sxs-lookup"><span data-stu-id="d4cf6-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="d4cf6-144">Rückgabe von Werten für ein Cmdlet-Hilfethema hinzufügen</span><span class="sxs-lookup"><span data-stu-id="d4cf6-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="d4cf6-145">Gewusst wie: Hinzufügen – Anmerkungen dieser zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="d4cf6-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="d4cf6-146">Beispiele für ein Cmdlet-Hilfethema hinzufügen</span><span class="sxs-lookup"><span data-stu-id="d4cf6-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="d4cf6-147">Gewusst wie: Hinzufügen von Links zu verwandten Themen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="d4cf6-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="d4cf6-148">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d4cf6-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)