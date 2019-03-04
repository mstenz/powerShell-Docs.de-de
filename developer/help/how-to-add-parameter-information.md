---
title: 'Gewusst wie: Hinzufügen von Informationen zu den Parametern | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863326"
---
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="22d06-102">Hinzufügen von Parameterinformationen</span><span class="sxs-lookup"><span data-stu-id="22d06-102">How to Add Parameter Information</span></span>

<span data-ttu-id="22d06-103">Dieser Abschnitt beschreibt, wie Sie Inhalte hinzufügen, die im Abschnitt "PARAMETERS" von der Cmdlet-Hilfethemas angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="22d06-103">This section describes how to add content that is displayed in the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="22d06-104">Der Parameterabschnitt des Hilfethemas enthält alle Parameter des Cmdlets und enthält eine ausführliche Beschreibung der einzelnen Parameter.</span><span class="sxs-lookup"><span data-stu-id="22d06-104">The PARAMETERS section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="22d06-105">Der Inhalt von den Abschnitt "PARAMETERS" sollte mit dem Inhalt der im Abschnitt "SYNTAX" des Hilfethemas entsprechen.</span><span class="sxs-lookup"><span data-stu-id="22d06-105">The content of the PARAMETERS section should be consistent with the content of the SYNTAX section of the Help topic.</span></span> <span data-ttu-id="22d06-106">Es ist die Verantwortung für den Autor der Hilfe, um sicherzustellen, dass sowohl die Syntax und Parameter-Knoten wie XML-Elemente enthalten.</span><span class="sxs-lookup"><span data-stu-id="22d06-106">It is the responsibility of the Help author to make sure that both the Syntax and Parameters node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="22d06-107">Eine vollständige Übersicht der eine Hilfedatei öffnen eine der Dll-Help.xml Dateien im Installationsverzeichnis von Windows PowerShell gefunden.</span><span class="sxs-lookup"><span data-stu-id="22d06-107">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="22d06-108">Beispielsweise enthält die Microsoft.PowerShell.Commands.Management.dll-Help.xml-Datei Inhalte für eine Reihe von Windows PowerShell-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="22d06-108">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="22d06-109">Hinzufügen von Parametern</span><span class="sxs-lookup"><span data-stu-id="22d06-109">To Add Parameters</span></span>

1. <span data-ttu-id="22d06-110">Öffnen Sie die Cmdlet-Hilfedatei, und suchen Sie den befehlsknoten für das Cmdlet aus, das Sie dokumentieren.</span><span class="sxs-lookup"><span data-stu-id="22d06-110">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="22d06-111">Wenn Sie ein neues Cmdlet hinzufügen möchten, das Sie einen neuen befehlsknoten zu erstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="22d06-111">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="22d06-112">Die Hilfedatei enthält einen befehlsknoten, für die einzelnen Cmdlets, die Sie Hilfeinhalte zu sorgen.</span><span class="sxs-lookup"><span data-stu-id="22d06-112">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="22d06-113">Hier ist ein Beispiel für einen leeren befehlsknoten.</span><span class="sxs-lookup"><span data-stu-id="22d06-113">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

2. <span data-ttu-id="22d06-114">Klicken Sie im befehlsknoten suchen Sie den Knoten für die Beschreibung, und fügen Sie einen Parameterknoten, wie unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="22d06-114">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span> <span data-ttu-id="22d06-115">Knoten der einzige Parameter zulässig ist und sie sollten sofort den syntaxknoten befolgen.</span><span class="sxs-lookup"><span data-stu-id="22d06-115">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. <span data-ttu-id="22d06-116">Fügen Sie in den Knoten Parameter einen Parameterknoten für jeden Parameter des Cmdlets, wie unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="22d06-116">Within the Parameters node, add a Parameter node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="22d06-117">In diesem Beispiel wird ein Parameterknoten für drei Parameter hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="22d06-117">In this example, a Parameter node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="22d06-118">Da diese die gleiche XML-Tags, die in den syntaxknoten verwendet werden sind, und, da die Parameter hier angegeben, muss den Parametern, die gemäß des syntaxknotens entsprechen, können Sie kopieren die Parameter-Knoten aus dem syntaxknoten und fügen Sie sie in den Knoten Parameter.</span><span class="sxs-lookup"><span data-stu-id="22d06-118">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="22d06-119">Achten Sie jedoch nur eine Instanz eines Parameter-Knotens kopiert, auch wenn der Parameter angegeben wird, in mehrere Parameter legt fest, in der Syntax.</span><span class="sxs-lookup"><span data-stu-id="22d06-119">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

4. <span data-ttu-id="22d06-120">Legen Sie für jeden Knoten Parameter die Attributwerte, die die Merkmale der einzelnen Parameter zu definieren.</span><span class="sxs-lookup"><span data-stu-id="22d06-120">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="22d06-121">Diese Attribute umfassen Folgendes: Verwendung von Platzhaltern, Pipelineinput und eine Position erforderlich.</span><span class="sxs-lookup"><span data-stu-id="22d06-121">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

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

5. <span data-ttu-id="22d06-122">Fügen Sie für jeden Knoten Parameter den Namen des Parameters ein.</span><span class="sxs-lookup"><span data-stu-id="22d06-122">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="22d06-123">Hier ist ein Beispiel für den Namen des Parameters auf den Knoten Parameter hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="22d06-123">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. <span data-ttu-id="22d06-124">Fügen Sie für jeden Knoten Parameter die Beschreibung des Parameters ein.</span><span class="sxs-lookup"><span data-stu-id="22d06-124">For each Parameter node, add the description of the parameter.</span></span> <span data-ttu-id="22d06-125">Hier ist ein Beispiel für die Beschreibung des Parameters auf den Knoten Parameter hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="22d06-125">Here is an example of the parameter description added to the Parameter node.</span></span>

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

7. <span data-ttu-id="22d06-126">Fügen Sie für jeden Knoten Parameter die .NET Framework-Typ des Parameters ein.</span><span class="sxs-lookup"><span data-stu-id="22d06-126">For each Parameter node, add the .NET Framework type of the parameter.</span></span> <span data-ttu-id="22d06-127">Der Parametertyp wird zusammen mit den Namen des Parameters angezeigt.</span><span class="sxs-lookup"><span data-stu-id="22d06-127">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="22d06-128">Hier ist ein Beispiel für den .NET Framework-Parametertyp, die auf den Knoten Parameter hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="22d06-128">Here is an example of the parameter .NET Framework type added to the Parameter node.</span></span>

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

8. <span data-ttu-id="22d06-129">Fügen Sie für jeden Knoten Parameter den Standardwert des Parameters ein.</span><span class="sxs-lookup"><span data-stu-id="22d06-129">For each Parameter node, add the default value of the parameter.</span></span> <span data-ttu-id="22d06-130">Der folgende Satz wird die parameterbeschreibung hinzugefügt, wenn der Inhalt angezeigt wird: "DefaultValue" ist die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="22d06-130">The following sentence is added to the parameter description when the content is displayed: "DefaultValue" is the default.</span></span>

   <span data-ttu-id="22d06-131">Hier ist ein Beispiel für den Standardwert des Parameters auf den Knoten Parameter hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="22d06-131">Here is an example of the parameter default value is added to the Parameter node.</span></span>

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

9. <span data-ttu-id="22d06-132">Fügen Sie einen Knoten möglichen Werte für jeden Parameter, die mehrere Werte enthält, hinzu.</span><span class="sxs-lookup"><span data-stu-id="22d06-132">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="22d06-133">Hier ist ein Beispiel für die eines Knotens möglichen Werte, der zwei mögliche Werte für den Parameter definiert.</span><span class="sxs-lookup"><span data-stu-id="22d06-133">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

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

<span data-ttu-id="22d06-134">Hier sind einige wichtige Aspekte beim Hinzufügen von Parametern aus.</span><span class="sxs-lookup"><span data-stu-id="22d06-134">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="22d06-135">Die Attribute des Parameters werden nicht in allen Ansichten des Cmdlet-Hilfethemas angezeigt.</span><span class="sxs-lookup"><span data-stu-id="22d06-135">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="22d06-136">Allerdings werden sie in einer Tabelle, die nach der Beschreibung des Parameters, wenn der Benutzer gefragt, für das vollständige werden angezeigt (Get-Help \<%CmdletName >-full) oder einen Parameter (Get-Help \<%CmdletName >-Parameter) Ansicht des Themas.</span><span class="sxs-lookup"><span data-stu-id="22d06-136">However, they are displayed in a table following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

- <span data-ttu-id="22d06-137">Die Beschreibung des Parameters ist einer der wichtigsten Teile eines Cmdlet-Hilfethemas.</span><span class="sxs-lookup"><span data-stu-id="22d06-137">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="22d06-138">Die Beschreibung sollte es sich um kurze sowie umfassende sein.</span><span class="sxs-lookup"><span data-stu-id="22d06-138">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="22d06-139">Beachten Sie außerdem, wenn die Beschreibung des Parameters zu lang ist ist, z. B. wenn die beiden Parameter miteinander interagieren, können Sie weitere Inhalte im Abschnitt "Hinweise" des Cmdlet-Hilfethemas hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="22d06-139">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="22d06-140">Die parameterbeschreibung bietet zwei Arten von Informationen.</span><span class="sxs-lookup"><span data-stu-id="22d06-140">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="22d06-141">Was das Cmdlet durchführt, wenn der Parameter verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="22d06-141">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="22d06-142">Welche ein zulässiger Wert für den Parameter ist.</span><span class="sxs-lookup"><span data-stu-id="22d06-142">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="22d06-143">Da die Werte der Parameter als .NET Framework-Objekten ausgedrückt werden, benötigen Benutzer Weitere Informationen zu diesen Werten in einer herkömmlichen Befehlszeilenhilfe nutzen.</span><span class="sxs-lookup"><span data-stu-id="22d06-143">Because the parameter values are expressed as .NET Framework objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="22d06-144">Dem Benutzer mitgeteilt, welche Art von Daten, die der Parameter akzeptiert werden sollen, und Beispiele enthalten.</span><span class="sxs-lookup"><span data-stu-id="22d06-144">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="22d06-145">Der Standardwert des Parameters ist der Wert, der verwendet wird, wenn der Parameter in der Befehlszeile nicht angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="22d06-145">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="22d06-146">Beachten Sie, dass der Standardwert optional ist und wird für einige Parameter, z. B. erforderlichen Parameter nicht benötigt.</span><span class="sxs-lookup"><span data-stu-id="22d06-146">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="22d06-147">Allerdings sollten Sie einen Standardwert für die meisten optionale Parameter angeben.</span><span class="sxs-lookup"><span data-stu-id="22d06-147">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="22d06-148">Der Standardwert der hilft Benutzern dabei, die Auswirkungen der nicht mit dem Parameter zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="22d06-148">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="22d06-149">Beschrieben Sie den Standardwert wird ganz spezifisch, wie z. B. "Current Directory" oder "Windows PowerShell Installationsverzeichnis ($pshome)" für einen optionalen Pfad.</span><span class="sxs-lookup"><span data-stu-id="22d06-149">Describe the default value very specifically, such as the "Current directory" or the "Windows PowerShell installation directory ($pshome)" for an optional path.</span></span> <span data-ttu-id="22d06-150">Sie können auch einen Satz, der beschreibt, den Standardwert, wie z. B. den folgenden Satz, der zum Schreiben der `PassThru` Parameter: "Wenn PassThru nicht angegeben ist, wird das Cmdlet keine Objekte über die Pipeline übergeben."</span><span class="sxs-lookup"><span data-stu-id="22d06-150">You can also write a sentence that describes the default, such as the following sentence used for the `PassThru` parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span>  <span data-ttu-id="22d06-151">Darüber hinaus, da der Wert, gegenüber der Name des Felds angezeigt wird "**Standardwert**", Sie müssen nicht den Begriff "Default Value" im Eintrag enthalten.</span><span class="sxs-lookup"><span data-stu-id="22d06-151">Also, because the value is displayed opposite the field name "**Default value**", you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="22d06-152">Der Standardwert des Parameters wird nicht in allen Ansichten des Cmdlet-Hilfethemas angezeigt.</span><span class="sxs-lookup"><span data-stu-id="22d06-152">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="22d06-153">Es wird jedoch angezeigt, in einer Tabelle (zusammen mit dem Parameterattribute), befolgen die Beschreibung des Parameters, wenn der Benutzer gefragt, für das vollständige werden (Get-Help \<%CmdletName >-full) oder einen Parameter (Get-Help \<%CmdletName >-Parameter) anzeigen im Thema.</span><span class="sxs-lookup"><span data-stu-id="22d06-153">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

<span data-ttu-id="22d06-154">Das folgende XML zeigt ein Paar von `<dev:defaultValue>` Tags hinzugefügt wurden, um die `<command:parameter>` Knoten.</span><span class="sxs-lookup"><span data-stu-id="22d06-154">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span> <span data-ttu-id="22d06-155">Beachten Sie, die der Standardwert unmittelbar hinter dem schließenden folgt `</command:parameterValue>` Tag (wenn der Wert des Parameters angegeben ist) oder dem schließenden `</maml:description>` Tag, der die Beschreibung des Parameters.</span><span class="sxs-lookup"><span data-stu-id="22d06-155">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="22d06-156">Der Name.</span><span class="sxs-lookup"><span data-stu-id="22d06-156">name.</span></span>

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

<span data-ttu-id="22d06-157">Fügen Sie Werte für enumerierte Typen hinzu.</span><span class="sxs-lookup"><span data-stu-id="22d06-157">Add Values for Enumerated Types</span></span>

<span data-ttu-id="22d06-158">Wenn der Parameter mehrere Werte oder Werte, der ein enumerierter Typ aufweist, können Sie eine optionale \<Dev:possibleValues > Knoten.</span><span class="sxs-lookup"><span data-stu-id="22d06-158">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="22d06-159">Dieser Knoten können Sie einen Namen und eine Beschreibung für mehrere Werte angeben.</span><span class="sxs-lookup"><span data-stu-id="22d06-159">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="22d06-160">Beachten Sie, dass die Beschreibungen der aufgelisteten Werte nicht in Standard-angezeigt, indem Hilfeansichten erscheinen die `Get-Help` Cmdlet, aber andere Help Viewer können dieser Inhalt in ihren Sichten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="22d06-160">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="22d06-161">Das folgende XML zeigt ein `<dev:possibleValues>` Knoten mit zwei angegebenen Werten.</span><span class="sxs-lookup"><span data-stu-id="22d06-161">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

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