---
title: Vorgehensweise beim Hinzufügen von Syntax zu einem Cmdlet-Hilfethema | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 0210b5ed3104777541692a0e78e7d3b16f9c8256
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361209"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="27b11-102">Hinzufügen einer Syntax zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="27b11-102">How to Add Syntax to a Cmdlet Help Topic</span></span>

<span data-ttu-id="27b11-103">Bevor Sie beginnen, den XML-Code für das Syntax Diagramm in der Cmdlet-Hilfedatei zu codieren, lesen Sie diesen Abschnitt, um einen Überblick über die Art der Daten zu erhalten, die Sie bereitstellen müssen, wie z. b. die Parameter Attribute und die Art und Weise, wie diese Daten im Syntax Diagramm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="27b11-103">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

### <a name="parameter-attributes"></a><span data-ttu-id="27b11-104">Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="27b11-104">Parameter Attributes</span></span>

- <span data-ttu-id="27b11-105">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="27b11-105">Required</span></span>

  - <span data-ttu-id="27b11-106">Wenn der Wert true ist, muss der Parameter in allen Befehlen angezeigt werden, die den Parametersatz verwenden.</span><span class="sxs-lookup"><span data-stu-id="27b11-106">If true, the parameter must appear in all commands that use the parameter set.</span></span>

  - <span data-ttu-id="27b11-107">Wenn der Wert false ist, ist der Parameter in allen Befehlen, die den Parametersatz verwenden, optional.</span><span class="sxs-lookup"><span data-stu-id="27b11-107">If false, the parameter is optional in all commands that use the parameter set.</span></span>

- <span data-ttu-id="27b11-108">Ort</span><span class="sxs-lookup"><span data-stu-id="27b11-108">Position</span></span>

  - <span data-ttu-id="27b11-109">Wenn benannt, ist der Parameter Name erforderlich.</span><span class="sxs-lookup"><span data-stu-id="27b11-109">If named, the parameter name is required.</span></span>

  - <span data-ttu-id="27b11-110">Wenn der Positionswert ist, ist der Parameter Name optional.</span><span class="sxs-lookup"><span data-stu-id="27b11-110">If positional, the parameter name is optional.</span></span> <span data-ttu-id="27b11-111">Wenn Sie weggelassen wird, muss der Parameterwert an der angegebenen Position im Befehl liegen.</span><span class="sxs-lookup"><span data-stu-id="27b11-111">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="27b11-112">Wenn der Wert z. b. Position = "1" ist, muss der Parameterwert der erste oder einzige unbenannte Parameterwert im Befehl sein.</span><span class="sxs-lookup"><span data-stu-id="27b11-112">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>

- <span data-ttu-id="27b11-113">Pipeline Eingabe</span><span class="sxs-lookup"><span data-stu-id="27b11-113">Pipeline Input</span></span>

  - <span data-ttu-id="27b11-114">Wenn true (byvalue), können Sie die Eingabe an den-Parameter übergeben.</span><span class="sxs-lookup"><span data-stu-id="27b11-114">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="27b11-115">Die Eingabe wird dem Parameter zugeordnet ("gebunden"), auch wenn der Eigenschaftsname und der Objekttyp nicht dem erwarteten Typ entsprechen.</span><span class="sxs-lookup"><span data-stu-id="27b11-115">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span> <span data-ttu-id="27b11-116">Windows PowerShell? Parameter Bindungskomponenten versuchen, die Eingabe in den richtigen Typ zu konvertieren, und schlagen den Befehl nur fehl, wenn der Typ nicht konvertiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="27b11-116">The Windows PowerShell? parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="27b11-117">Nur ein Parameter in einem Parametersatz kann nach Wert zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="27b11-117">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="27b11-118">Wenn true (bypropertyname), können Sie die Eingabe an den-Parameter übergeben.</span><span class="sxs-lookup"><span data-stu-id="27b11-118">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="27b11-119">Die Eingabe wird jedoch nur mit dem-Parameter verknüpft, wenn der Parameter Name mit dem Namen einer Eigenschaft des Eingabe Objekts übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="27b11-119">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="27b11-120">Wenn der Parameter Name beispielsweise `Path`ist, werden Objekte, die an das Cmdlet weitergeleitet werden, diesem Parameter nur dann zugeordnet, wenn das Objekt über eine Eigenschaft mit dem Namen Path verfügt.</span><span class="sxs-lookup"><span data-stu-id="27b11-120">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>

  - <span data-ttu-id="27b11-121">Wenn true (byvalue, bypropertyname), können Sie die Eingabe an den-Parameter übergeben, indem Sie den Eigenschaftsnamen oder den Wert angeben.</span><span class="sxs-lookup"><span data-stu-id="27b11-121">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="27b11-122">Nur ein Parameter in einem Parametersatz kann nach Wert zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="27b11-122">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="27b11-123">Wenn der Wert false ist, können Sie keine Eingaben an diesen Parameter übergeben.</span><span class="sxs-lookup"><span data-stu-id="27b11-123">If false, you cannot pipe input to this parameter.</span></span>

- <span data-ttu-id="27b11-124">Platzhalter</span><span class="sxs-lookup"><span data-stu-id="27b11-124">Globbing</span></span>

  - <span data-ttu-id="27b11-125">True gibt an, dass der Text, den der Benutzer für den Parameterwert eingegeben hat, Platzhalter Zeichen enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="27b11-125">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>

  - <span data-ttu-id="27b11-126">False gibt an, dass der Text, den der Benutzer für den Parameterwert eingegeben hat, keine Platzhalter Zeichen enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="27b11-126">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="27b11-127">Parameter Wert Attribute</span><span class="sxs-lookup"><span data-stu-id="27b11-127">Parameter Value Attributes</span></span>

- <span data-ttu-id="27b11-128">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="27b11-128">Required</span></span>

  - <span data-ttu-id="27b11-129">Wenn true, muss der angegebene Wert immer verwendet werden, wenn der-Parameter in einem-Befehl verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="27b11-129">If true, the specified value must be used whenever using the parameter in a command.</span></span>

  - <span data-ttu-id="27b11-130">False gibt an, dass der Parameterwert optional ist.</span><span class="sxs-lookup"><span data-stu-id="27b11-130">If false, the parameter value is optional.</span></span> <span data-ttu-id="27b11-131">In der Regel ist ein Wert nur optional, wenn er einer von mehreren gültigen Werten für einen Parameter ist, z. b. in einem enumerierten Typ.</span><span class="sxs-lookup"><span data-stu-id="27b11-131">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="27b11-132">Das erforderliche-Attribut eines Parameter Werts unterscheidet sich vom erforderlichen-Attribut eines-Parameters.</span><span class="sxs-lookup"><span data-stu-id="27b11-132">The Required attribute of a parameter value is different from the Required attribute of a parameter.</span></span>

<span data-ttu-id="27b11-133">Das erforderliche-Attribut eines-Parameters gibt an, ob der Parameter (und sein Wert) beim Aufrufen des Cmdlets eingeschlossen werden muss.</span><span class="sxs-lookup"><span data-stu-id="27b11-133">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="27b11-134">Im Gegensatz dazu wird das erforderliche Attribut eines Parameter Werts nur verwendet, wenn der Parameter im Befehl enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="27b11-134">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="27b11-135">Gibt an, ob dieser bestimmte Wert mit dem-Parameter verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="27b11-135">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="27b11-136">Normalerweise sind Parameterwerte, die Platzhalter sind, erforderlich, und Parameterwerte, die Literale sind, sind nicht erforderlich, da es sich um einen von mehreren Werten handelt, die mit dem-Parameter verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="27b11-136">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="27b11-137">Sammeln von Syntax Informationen</span><span class="sxs-lookup"><span data-stu-id="27b11-137">Gathering Syntax Information</span></span>

1. <span data-ttu-id="27b11-138">Beginnen Sie mit dem Cmdlet-Namen.</span><span class="sxs-lookup"><span data-stu-id="27b11-138">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

2. <span data-ttu-id="27b11-139">Listet alle Parameter des Cmdlets auf.</span><span class="sxs-lookup"><span data-stu-id="27b11-139">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="27b11-140">Geben Sie vor jedem Parameternamen einen Bindestrich (auch als "Bindestrich" oder "Minuszeichen" (ASCII 45) ein.</span><span class="sxs-lookup"><span data-stu-id="27b11-140">Type a dash (also known as a "dash" or "minus sign" (ASCII 45) before each parameter name.</span></span> <span data-ttu-id="27b11-141">Trennen Sie die Parameter in Parametersätze (für einige Cmdlets ist möglicherweise nur ein Parameter festgelegt).</span><span class="sxs-lookup"><span data-stu-id="27b11-141">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="27b11-142">In diesem Beispiel verfügt das Get-Tech-Cmdlet über zwei Parametersätze.</span><span class="sxs-lookup"><span data-stu-id="27b11-142">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="27b11-143">Starten Sie jeden Parametersatz mit dem Namen des Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="27b11-143">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="27b11-144">Listet den Standardparameter Satz zuerst auf.</span><span class="sxs-lookup"><span data-stu-id="27b11-144">List the default parameter set first.</span></span> <span data-ttu-id="27b11-145">Der Standardparameter wird durch die Cmdlet-Klasse angegeben.</span><span class="sxs-lookup"><span data-stu-id="27b11-145">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="27b11-146">Listen Sie für jeden Parametersatz zuerst den eindeutigen Parameter auf, es sei denn, es sind Positions Parameter vorhanden, die zuerst angezeigt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="27b11-146">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="27b11-147">Im vorherigen Beispiel handelt es sich bei den Parametern Name und ID um eindeutige Parameter für die beiden Parametersätze (jeder Parametersatz muss über einen Parameter verfügen, der für diesen Parametersatz eindeutig ist).</span><span class="sxs-lookup"><span data-stu-id="27b11-147">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="27b11-148">Dies erleichtert es Benutzern, den Parameter zu identifizieren, den Sie für den Parametersatz angeben müssen.</span><span class="sxs-lookup"><span data-stu-id="27b11-148">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="27b11-149">Listen Sie die Parameter in der Reihenfolge auf, in der Sie im Befehl angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="27b11-149">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="27b11-150">Wenn die Reihenfolge keine Rolle spielt, können Sie verwandte Parameter zusammen auflisten oder die am häufigsten verwendeten Parameter zuerst auflisten.</span><span class="sxs-lookup"><span data-stu-id="27b11-150">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="27b11-151">Stellen Sie sicher, dass Sie die Parameter "WhatIf" und "Confirm" auflisten, wenn das Cmdlet "Schulter verarbeiten"</span><span class="sxs-lookup"><span data-stu-id="27b11-151">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="27b11-152">Listen Sie die allgemeinen Parameter (z. b. "Verbose", "Debug" und "ErrorAction") nicht in Ihrem Syntax Diagramm auf.</span><span class="sxs-lookup"><span data-stu-id="27b11-152">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="27b11-153">Mit dem `Get-Help`-Cmdlet werden diese Informationen für Sie hinzugefügt, wenn das Hilfethema angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="27b11-153">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

3. <span data-ttu-id="27b11-154">Fügen Sie die Parameterwerte hinzu.</span><span class="sxs-lookup"><span data-stu-id="27b11-154">Add the parameter values.</span></span> <span data-ttu-id="27b11-155">In Windows PowerShell werden Parameterwerte durch ihren .NET-Typ dargestellt.</span><span class="sxs-lookup"><span data-stu-id="27b11-155">In Windows PowerShell?, parameter values are represented by their .NET type.</span></span> <span data-ttu-id="27b11-156">Allerdings kann der Typname abgekürzt werden, z. b. "String" für System. String.</span><span class="sxs-lookup"><span data-stu-id="27b11-156">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="27b11-157">Abkürzen von Typen, solange ihre Bedeutung klar ist, z. b. "String" für System. String und "int" für System. Int32.</span><span class="sxs-lookup"><span data-stu-id="27b11-157">Abbreviate types as long as their meaning is clear, such as "string" for System.String and "int" for System.Int32.</span></span>

   <span data-ttu-id="27b11-158">Listet alle Werte von Enumerationen auf, wie z. b. den-Type-Parameter im vorherigen Beispiel, das auf "Basic" oder "Advanced" festgelegt werden kann.</span><span class="sxs-lookup"><span data-stu-id="27b11-158">List all values of enumerations, such as the -type parameter in the previous example, which can be set to "basic" or "advanced".</span></span>

   <span data-ttu-id="27b11-159">Switch-Parameter, wie z. b.-List im vorherigen Beispiel, haben keine Werte.</span><span class="sxs-lookup"><span data-stu-id="27b11-159">Switch parameters, such as -list in the previous example, do not have values.</span></span>

4. <span data-ttu-id="27b11-160">Fügen Sie Parameterwerten, bei denen es sich um Platzhalter handelt, zu Parameterwerten, die Literale sind, Spitze Klammern hinzu.</span><span class="sxs-lookup"><span data-stu-id="27b11-160">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. <span data-ttu-id="27b11-161">Schließen Sie optionale Parameter und deren Werte in eckige Klammern ein.</span><span class="sxs-lookup"><span data-stu-id="27b11-161">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. <span data-ttu-id="27b11-162">Schließen Sie optionale Parameternamen (für Positions Parameter) in eckige Klammern ein.</span><span class="sxs-lookup"><span data-stu-id="27b11-162">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="27b11-163">Der Name für Parameter, die Positionswerte sind, wie z. b. der Name-Parameter im folgenden Beispiel, muss nicht in den-Befehl eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="27b11-163">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. <span data-ttu-id="27b11-164">Wenn ein Parameterwert mehrere Werte enthalten kann, z. b. eine Liste von Namen im Name-Parameter, fügen Sie ein paar von eckigen Klammern direkt nach dem Parameterwert hinzu.</span><span class="sxs-lookup"><span data-stu-id="27b11-164">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. <span data-ttu-id="27b11-165">Wenn der Benutzer eine Auswahl aus Parametern oder Parameterwerten, wie z. b. dem Typparameter, treffen kann, schließen Sie die Optionen in geschweiften Klammern ein, und trennen Sie Sie durch das exklusive Symbol oder (;).</span><span class="sxs-lookup"><span data-stu-id="27b11-165">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. <span data-ttu-id="27b11-166">Wenn für den Parameterwert eine bestimmte Formatierung verwendet werden muss, z. b. Anführungszeichen oder Klammern, wird das Format in der Syntax angezeigt.</span><span class="sxs-lookup"><span data-stu-id="27b11-166">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="27b11-167">Codieren des Syntax Diagramm-XML</span><span class="sxs-lookup"><span data-stu-id="27b11-167">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="27b11-168">Der Syntax Knoten des XML-Codes beginnt unmittelbar nach dem Beschreibungs Knoten, der mit dem \</MAML: Description >-Tag endet.</span><span class="sxs-lookup"><span data-stu-id="27b11-168">The syntax node of the XML begins immediately after the description node, which ends with the \</maml:description> tag.</span></span> <span data-ttu-id="27b11-169">Informationen zum Sammeln von Daten, die im Syntax Diagramm verwendet werden, finden Sie unter [Sammeln von Syntax Informationen](#gathering-syntax-information).</span><span class="sxs-lookup"><span data-stu-id="27b11-169">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#gathering-syntax-information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="27b11-170">Hinzufügen eines Syntax Knotens</span><span class="sxs-lookup"><span data-stu-id="27b11-170">Adding a Syntax Node</span></span>

<span data-ttu-id="27b11-171">Das im Cmdlet-Hilfethema angezeigte Syntax Diagramm wird aus den Daten im Knoten Syntax der XML-Datei generiert.</span><span class="sxs-lookup"><span data-stu-id="27b11-171">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="27b11-172">Der Syntax Knoten ist in ein paar eingeschlossen, wenn \<Befehl: Syntax > Tags.</span><span class="sxs-lookup"><span data-stu-id="27b11-172">The syntax node is enclosed in a pair if \<command:syntax> tags.</span></span> <span data-ttu-id="27b11-173">Mit jedem Parametersatz des Cmdlets, der in ein paar von \<Befehl eingeschlossen ist: syntaxitem > Tags.</span><span class="sxs-lookup"><span data-stu-id="27b11-173">With each parameter set of the cmdlet enclosed in a pair of \<command:syntaxitem> tags.</span></span> <span data-ttu-id="27b11-174">Es gibt keine Beschränkung für die Anzahl \<Befehls: syntaxitem > Tags, die Sie hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="27b11-174">There is no limit to the number of \<command:syntaxitem> tags that you can add.</span></span>

<span data-ttu-id="27b11-175">Das folgende Beispiel zeigt einen Syntax Knoten, der über Syntax Elementknoten für zwei Parametersätze verfügt.</span><span class="sxs-lookup"><span data-stu-id="27b11-175">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

```xml
<command:syntax>
  <command:syntaxItem>
    ...
    <!--Parameter Set 1 (default parameter set) parameters go here-->
    ...
  </command:syntaxItem>
  <command:syntaxItem>
    ...
    <!--Parameter Set 2 parameters go here-->
    ...
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="27b11-176">Hinzufügen des Cmdlet-namens zu den Parameter Satz Daten</span><span class="sxs-lookup"><span data-stu-id="27b11-176">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="27b11-177">Jeder Parametersatz des Cmdlets wird in einem Syntax Elementknoten angegeben.</span><span class="sxs-lookup"><span data-stu-id="27b11-177">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="27b11-178">Jeder Syntax Elementknoten beginnt mit einem Paar aus \<MAML: Name > Tags, die den Namen des Cmdlets enthalten.</span><span class="sxs-lookup"><span data-stu-id="27b11-178">Each syntax item node begins with a pair of \<maml:name> tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="27b11-179">Das folgende Beispiel schließt einen Syntax Knoten ein, der über Syntax Elementknoten für zwei Parametersätze verfügt.</span><span class="sxs-lookup"><span data-stu-id="27b11-179">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

```xml
<command:syntax>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-parameters"></a><span data-ttu-id="27b11-180">Hinzufügen von Parametern</span><span class="sxs-lookup"><span data-stu-id="27b11-180">Adding Parameters</span></span>

<span data-ttu-id="27b11-181">Jeder Parameter, der dem Knoten Syntax Element hinzugefügt wird, wird in einem Paar von \<Befehl: Parameter > Tags angegeben.</span><span class="sxs-lookup"><span data-stu-id="27b11-181">Each parameter added to the syntax item node is specified within a pair of \<command:parameter> tags.</span></span> <span data-ttu-id="27b11-182">Sie benötigen ein paar von \<Befehl: Parameter > Tags für jeden Parameter, der im Parametersatz enthalten ist, mit Ausnahme der allgemeinen Parameter, die von Windows PowerShell bereitgestellt werden?.</span><span class="sxs-lookup"><span data-stu-id="27b11-182">You need a pair of \<command:parameter> tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by Windows PowerShell?.</span></span>

<span data-ttu-id="27b11-183">Die Attribute des öffnenden \<Command: Parameter >-Tags bestimmen, wie der Parameter im Syntax Diagramm angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="27b11-183">The attributes of the opening \<command:parameter> tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="27b11-184">Weitere Informationen zu Parameter Attributen finden Sie unter [Parameter Attribute](#parameter-attributes).</span><span class="sxs-lookup"><span data-stu-id="27b11-184">For information on parameter attributes, see [Parameter Attributes](#parameter-attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="27b11-185">Der \<Befehl: Parameter > Tag unterstützt ein untergeordnetes Element \<MAML: Description->, dessen Inhalt nie angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="27b11-185">The \<command:parameter> tag supports a child element \<maml:description> whose content is never displayed.</span></span> <span data-ttu-id="27b11-186">Die Parameter Beschreibungen werden im Parameter Knoten der XML-Datei angegeben.</span><span class="sxs-lookup"><span data-stu-id="27b11-186">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="27b11-187">Um Inkonsistenzen zwischen den Informationen im Syntax Element verheißen und dem Parameter Knoten zu vermeiden, lassen Sie das (\<MAML: Description >, oder lassen Sie es leer.</span><span class="sxs-lookup"><span data-stu-id="27b11-187">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (\<maml:description> or leave it empty.</span></span>

<span data-ttu-id="27b11-188">Das folgende Beispiel schließt einen Syntax Elementknoten für einen Parametersatz mit zwei Parametern ein.</span><span class="sxs-lookup"><span data-stu-id="27b11-188">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

```xml
<command:syntaxItem>
  <maml:name>Cmdlet-Name</maml:name>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByValue)" position="1">
    <maml:name>ParameterName1</maml:name>
    <command:parameterValue required="true">
      string[]
    </command:parameterValue>
  </command:parameter>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByPropertyName)">
    <maml:name>ParameterName2</maml:name>
    <command:parameterValue required="true">
      int32[]
    </command:parameterValue>
  </command:parameter>
</command:syntaxItem>
```
