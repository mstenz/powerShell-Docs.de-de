---
title: Vorgehensweise beim Hinzufügen von Parameter Informationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: b9ccca75c2d9126e84a7f486ffe803042a742b62
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565559"
---
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="1c8a5-102">Hinzufügen von Parameterinformationen</span><span class="sxs-lookup"><span data-stu-id="1c8a5-102">How to Add Parameter Information</span></span>

<span data-ttu-id="1c8a5-103">In diesem Abschnitt wird beschrieben, wie Sie Inhalte hinzufügen, die im Abschnitt Parameters des Cmdlet-Hilfe Themas angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-103">This section describes how to add content that is displayed in the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="1c8a5-104">Der Abschnitt Parameters des Hilfe Themas Listet jeden Parameter des Cmdlets auf und stellt eine ausführliche Beschreibung der einzelnen Parameter bereit.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-104">The PARAMETERS section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="1c8a5-105">Der Inhalt des Parameters-Abschnitts sollte mit dem Inhalt des Syntax Abschnitts des Hilfe Themas konsistent sein.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-105">The content of the PARAMETERS section should be consistent with the content of the SYNTAX section of the Help topic.</span></span> <span data-ttu-id="1c8a5-106">Der Autor der Hilfe ist dafür verantwortlich, sicherzustellen, dass der Knoten Syntax und Parameter ähnliche XML-Elemente enthalten.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-106">It is the responsibility of the Help author to make sure that both the Syntax and Parameters node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="1c8a5-107">Eine umfassende Übersicht über eine Hilfedatei erhalten Sie, indem Sie eine der dll-Help. XML-Dateien öffnen, die sich im Windows PowerShell-Installationsverzeichnis befinden.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-107">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="1c8a5-108">Beispielsweise enthält die Datei Microsoft. PowerShell. Commands. Management. dll-Help. XML Inhalte für mehrere der Windows PowerShell-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-108">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="1c8a5-109">So fügen Sie Parameter hinzu</span><span class="sxs-lookup"><span data-stu-id="1c8a5-109">To Add Parameters</span></span>

1. <span data-ttu-id="1c8a5-110">Öffnen Sie die Cmdlet-Hilfedatei, und suchen Sie den Befehls Knoten für das Cmdlet, das Sie dokumentieren.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-110">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="1c8a5-111">Wenn Sie ein neues Cmdlet hinzufügen, müssen Sie einen neuen Befehls Knoten erstellen.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-111">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="1c8a5-112">Die Hilfedatei enthält einen Befehls Knoten für jedes Cmdlet, für das Sie Hilfe Inhalte bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-112">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="1c8a5-113">Im folgenden finden Sie ein Beispiel für einen leeren Befehls Knoten.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-113">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

2. <span data-ttu-id="1c8a5-114">Suchen Sie im Befehls Knoten den Beschreibungs Knoten, und fügen Sie wie unten dargestellt einen Parameter Knoten hinzu.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-114">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span> <span data-ttu-id="1c8a5-115">Es ist nur ein Parameter Knoten zulässig, der unmittelbar auf den Syntax Knoten folgt.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-115">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. <span data-ttu-id="1c8a5-116">Fügen Sie im Knoten Parameter einen Parameter Knoten für jeden Parameter des Cmdlets hinzu, wie unten gezeigt.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-116">Within the Parameters node, add a Parameter node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="1c8a5-117">In diesem Beispiel wird ein Parameter Knoten für drei Parameter hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-117">In this example, a Parameter node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="1c8a5-118">Da es sich hierbei um dieselben XML-Tags handelt, die im Syntax Knoten verwendet werden, und da die hier angegebenen Parameter mit den Parametern übereinstimmen müssen, die durch den Syntax Knoten angegeben werden, können Sie die Parameter Knoten aus dem Syntax Knoten kopieren und in den Parameter Knoten einfügen.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-118">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="1c8a5-119">Achten Sie jedoch darauf, nur eine Instanz eines Parameter Knotens zu kopieren, auch wenn der Parameter in mehreren Parameter Sätzen in der Syntax angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-119">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

4. <span data-ttu-id="1c8a5-120">Legen Sie für jeden Parameter Knoten die Attributwerte fest, die die Merkmale der einzelnen Parameter definieren.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-120">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="1c8a5-121">Diese Attribute umfassen Folgendes: required, Globin, pipelineinput und Position.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-121">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named" ></command:parameter>
    </command:Parameters>
    ```

5. <span data-ttu-id="1c8a5-122">Fügen Sie für jeden Parameter Knoten den Namen des Parameters hinzu.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-122">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="1c8a5-123">Im folgenden finden Sie ein Beispiel für den Parameternamen, der dem Parameter Knoten hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-123">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. <span data-ttu-id="1c8a5-124">Fügen Sie für jeden Parameter Knoten die Beschreibung des Parameters hinzu.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-124">For each Parameter node, add the description of the parameter.</span></span> <span data-ttu-id="1c8a5-125">Im folgenden finden Sie ein Beispiel für die Parameter Beschreibung, die dem Parameter-Knoten hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-125">Here is an example of the parameter description added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
      </command:parameter>
    </command:parameters>
    ```

7. <span data-ttu-id="1c8a5-126">Fügen Sie für jeden Parameter Knoten den .NET Framework Typ des Parameters hinzu.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-126">For each Parameter node, add the .NET Framework type of the parameter.</span></span> <span data-ttu-id="1c8a5-127">Der Parametertyp wird zusammen mit dem Parameternamen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-127">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="1c8a5-128">Im folgenden finden Sie ein Beispiel für den Parameter .NET Framework Typ, der dem Parameter Knoten hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-128">Here is an example of the parameter .NET Framework type added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
      </command:parameter>
    </command:parameters>
    ```

8. <span data-ttu-id="1c8a5-129">Fügen Sie für jeden Parameter Knoten den Standardwert des Parameters hinzu.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-129">For each Parameter node, add the default value of the parameter.</span></span> <span data-ttu-id="1c8a5-130">Der folgende Satz wird der Parameter Beschreibung hinzugefügt, wenn der Inhalt angezeigt wird: "DefaultValue" ist die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-130">The following sentence is added to the parameter description when the content is displayed: "DefaultValue" is the default.</span></span>

   <span data-ttu-id="1c8a5-131">Im folgenden finden Sie ein Beispiel für den Standardwert des Parameters, der dem Parameter Knoten hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-131">Here is an example of the parameter default value is added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
        <dev:defaultvalue> Add default value...</dev:defaultvalue>
      </command:parameter>
    </command:parameters>
    ```

9. <span data-ttu-id="1c8a5-132">Fügen Sie für jeden Parameter mit mehreren Werten den Knoten mögliche Werte hinzu.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-132">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="1c8a5-133">Im folgenden finden Sie ein Beispiel für den eines möglichen Values-Knotens, der zwei mögliche Werte für den Parameter definiert.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-133">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      /dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

<span data-ttu-id="1c8a5-134">Beachten Sie beim Hinzufügen von Parametern die folgenden Punkte.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-134">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="1c8a5-135">Die Attribute des-Parameters werden nicht in allen Ansichten des Hilfe Themas für das Cmdlet angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-135">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="1c8a5-136">Sie werden jedoch in einer Tabelle nach der Parameter Beschreibung angezeigt, wenn der Benutzer die vollständige Ansicht (Get-Help \< cmdletname>-Full) oder den Parameter (Get-Help \< cmdletname>-Parameter) des Themas anfordert.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-136">However, they are displayed in a table following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

- <span data-ttu-id="1c8a5-137">Die Parameter Beschreibung ist einer der wichtigsten Teile eines Cmdlet-Hilfe Themas.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-137">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="1c8a5-138">Die Beschreibung sollte kurz und gründlich sein.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-138">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="1c8a5-139">Beachten Sie außerdem, dass Sie, wenn die Parameter Beschreibung zu lang wird, z. b. Wenn zwei Parameter miteinander interagieren, weitere Inhalte im Abschnitt "Hinweise" des Cmdlet-Hilfe Themas hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-139">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="1c8a5-140">Die Parameter Beschreibung bietet zwei Arten von Informationen.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-140">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="1c8a5-141">Was das Cmdlet tut, wenn der-Parameter verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-141">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="1c8a5-142">Der zulässige Wert für den-Parameter.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-142">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="1c8a5-143">Da die Parameterwerte als .NET Framework Objekte ausgedrückt werden, benötigen die Benutzer mehr Informationen zu diesen Werten als in einer herkömmlichen Befehlszeilen Hilfe.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-143">Because the parameter values are expressed as .NET Framework objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="1c8a5-144">Weisen Sie den Benutzer an, welche Art von Daten der Parameter akzeptieren soll, und fügen Sie Beispiele ein.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-144">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="1c8a5-145">Der Standardwert des-Parameters ist der Wert, der verwendet wird, wenn der-Parameter nicht in der Befehlszeile angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-145">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="1c8a5-146">Beachten Sie, dass der Standardwert optional ist und für einige Parameter, wie z. b. erforderliche Parameter, nicht benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-146">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="1c8a5-147">Sie sollten jedoch einen Standardwert für die meisten optionalen Parameter angeben.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-147">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="1c8a5-148">Der Standardwert unterstützt den Benutzer dabei, die Auswirkungen der Verwendung des-Parameters zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-148">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="1c8a5-149">Beschreiben Sie den Standardwert sehr spezifisch, z. b. "Aktuelles Verzeichnis" oder "Windows PowerShell-Installationsverzeichnis ($PSHome)", um einen optionalen Pfad zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-149">Describe the default value very specifically, such as the "Current directory" or the "Windows PowerShell installation directory ($pshome)" for an optional path.</span></span> <span data-ttu-id="1c8a5-150">Sie können auch einen Satz schreiben, der den Standard beschreibt, z. b. den folgenden Satz, der für den Parameter verwendet wird `PassThru` : "Wenn passthru nicht angegeben ist, übergibt das Cmdlet Objekte nicht in der Pipeline."</span><span class="sxs-lookup"><span data-stu-id="1c8a5-150">You can also write a sentence that describes the default, such as the following sentence used for the `PassThru` parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span>  <span data-ttu-id="1c8a5-151">Außerdem müssen Sie den Begriff "Standardwert" nicht in den Eintrag einschließen, da der Wert dem Feldnamen "**Standardwert**" angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-151">Also, because the value is displayed opposite the field name "**Default value**", you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="1c8a5-152">Der Standardwert des-Parameters wird nicht in allen Ansichten des Hilfe Themas für das Cmdlet angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-152">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="1c8a5-153">Sie wird jedoch in einer Tabelle (zusammen mit den Parameter Attributen) nach der Parameter Beschreibung angezeigt, wenn der Benutzer die vollständige Ansicht (Get-Help \< cmdletname>-Full) oder den Parameter (Get-Help \< cmdletname>-Parameter) des Themas anfordert.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-153">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

<span data-ttu-id="1c8a5-154">Der folgende XML-Code zeigt ein dem `<dev:defaultValue>` Knoten hinzugefügtes paar von Tags `<command:parameter>` .</span><span class="sxs-lookup"><span data-stu-id="1c8a5-154">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span> <span data-ttu-id="1c8a5-155">Beachten Sie, dass der Standardwert direkt hinter das `</command:parameterValue>` Endtag (wenn der Parameterwert angegeben ist) oder das `</maml:description>` Endtag der Parameter Beschreibung folgt.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-155">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="1c8a5-156">name.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-156">name.</span></span>

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
  </command:parameter>
</command:parameters>
```

<span data-ttu-id="1c8a5-157">Werte für Enumerationstypen hinzufügen</span><span class="sxs-lookup"><span data-stu-id="1c8a5-157">Add Values for Enumerated Types</span></span>

<span data-ttu-id="1c8a5-158">Wenn der Parameter mehrere Werte oder Werte eines enumerierten Typs aufweist, können Sie einen optionalen \< dev: PossibleValues-> Knoten verwenden.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-158">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="1c8a5-159">Mit diesem Knoten können Sie einen Namen und eine Beschreibung für mehrere Werte angeben.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-159">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="1c8a5-160">Beachten Sie, dass die Beschreibungen der aufgelisteten Werte nicht in einer der vom Cmdlet angezeigten Standard Hilfe Ansichten angezeigt werden `Get-Help` , aber andere Help Viewer diesen Inhalt möglicherweise in ihren Ansichten anzeigen.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-160">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="1c8a5-161">Der folgende XML-Code zeigt einen `<dev:possibleValues>` Knoten mit zwei angegebenen Werten.</span><span class="sxs-lookup"><span data-stu-id="1c8a5-161">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
    <dev:possibleValues>
      <dev:possibleValue>
        <dev:value> Value 1 </dev:value>
        <maml:description>
          <maml:para> Description 1 </maml:para>
        </maml:description>
      <dev:possibleValue>
      <dev:possibleValue>
        <dev:value> Value 2 </dev:value>
        <maml:description>
          <maml:para> Description 2 </maml:para>
        </maml:description>
      <dev:possibleValue>
    </dev:possibleValues>
  </command:parameter>
</command:parameters>
```
