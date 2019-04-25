---
title: Hinzufügen von Syntax zu einem Cmdlet-Hilfethemas | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 2e9dbc9ff8f9507f2008cd6e114ba6fec36b10bf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083381"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="b783a-102">Hinzufügen einer Syntax zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="b783a-102">How to Add Syntax to a Cmdlet Help Topic</span></span>

- [<span data-ttu-id="b783a-103">Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="b783a-103">Parameter Attributes</span></span>](#Parameter-Attributes)

- [<span data-ttu-id="b783a-104">Parameterattribute-Wert</span><span class="sxs-lookup"><span data-stu-id="b783a-104">Parameter Value Attributes</span></span>](#Parameter-Value-Attributes)

- [<span data-ttu-id="b783a-105">Informationen über die Syntax werden ermittelt.</span><span class="sxs-lookup"><span data-stu-id="b783a-105">Gathering Syntax Information</span></span>](#Gathering-Syntax-Information)

- [<span data-ttu-id="b783a-106">Das Syntaxdiagramm XML-Codierung</span><span class="sxs-lookup"><span data-stu-id="b783a-106">Coding the Syntax Diagram XML</span></span>](#Coding-the-Syntax-Diagram-XML)

## <a name="things-to-know-about-the-syntax-diagram-in-cmdlet-help"></a><span data-ttu-id="b783a-107">Wissenswerte Fakten über das Syntaxdiagramm in der Cmdlet-Hilfe</span><span class="sxs-lookup"><span data-stu-id="b783a-107">Things to Know About the Syntax Diagram in Cmdlet Help</span></span>

<span data-ttu-id="b783a-108">Lesen Sie diesen Abschnitt rufen Sie ein klares Bild von der Art der Daten, die Sie bereitstellen müssen, z. B. die Parameterattribute und wie diese Daten in das Syntaxdiagramm angezeigt werden, bevor Sie beginnen, den XML-Code für das Syntaxdiagramm in der Cmdlet-Hilfedatei zu codieren...</span><span class="sxs-lookup"><span data-stu-id="b783a-108">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

### <a name="parameter-attributes"></a><span data-ttu-id="b783a-109">Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="b783a-109">Parameter Attributes</span></span>

- <span data-ttu-id="b783a-110">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b783a-110">Required</span></span>

  - <span data-ttu-id="b783a-111">Bei "true", muss der Parameter in allen Befehlen angezeigt, die den Parametersatz verwenden.</span><span class="sxs-lookup"><span data-stu-id="b783a-111">If true, the parameter must appear in all commands that use the parameter set.</span></span>

  - <span data-ttu-id="b783a-112">Wenn "false" ist der Parameter optional in allen Befehlen, die den Parametersatz verwenden.</span><span class="sxs-lookup"><span data-stu-id="b783a-112">If false, the parameter is optional in all commands that use the parameter set.</span></span>

- <span data-ttu-id="b783a-113">Position</span><span class="sxs-lookup"><span data-stu-id="b783a-113">Position</span></span>

  - <span data-ttu-id="b783a-114">Der Parametername ist erforderlich, wenn mit dem Namen.</span><span class="sxs-lookup"><span data-stu-id="b783a-114">If named, the parameter name is required.</span></span>

  - <span data-ttu-id="b783a-115">Wenn Sie mit Feldern fester Breite, ist der Name des Parameters optional.</span><span class="sxs-lookup"><span data-stu-id="b783a-115">If positional, the parameter name is optional.</span></span> <span data-ttu-id="b783a-116">Wenn sie weggelassen wird, muss der Wert des Parameters in der angegebenen Position im Befehl sein.</span><span class="sxs-lookup"><span data-stu-id="b783a-116">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="b783a-117">Z. B. wenn der Wert Position = "1", der Wert des Parameters muss die erste oder einzige unbenannte Parameterwert im Befehl.</span><span class="sxs-lookup"><span data-stu-id="b783a-117">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>

- <span data-ttu-id="b783a-118">Pipeline-Eingabe</span><span class="sxs-lookup"><span data-stu-id="b783a-118">Pipeline Input</span></span>

  - <span data-ttu-id="b783a-119">Bei "true" (ByValue), können Sie Eingabe für den Parameter übergeben.</span><span class="sxs-lookup"><span data-stu-id="b783a-119">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="b783a-120">Die Eingabe ist verknüpft mit ("gebunden an") der Parameter, auch wenn die Eigenschaftennamen und den Objekttyp nicht dem erwarteten Typ überein.</span><span class="sxs-lookup"><span data-stu-id="b783a-120">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span> <span data-ttu-id="b783a-121">Die Windows PowerShell? Parameter Bindung von Komponenten sollten Sie die Eingabe in den richtigen Typ zu konvertieren und den Befehl fehl, nur, wenn der Typ kann nicht konvertiert werden.</span><span class="sxs-lookup"><span data-stu-id="b783a-121">The Windows PowerShell? parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="b783a-122">Nur ein Parameter in einem Parametersatz kann als Wert zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="b783a-122">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="b783a-123">Bei "true" (ByPropertyName), können Sie Eingabe für den Parameter übergeben.</span><span class="sxs-lookup"><span data-stu-id="b783a-123">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="b783a-124">Allerdings ist die Eingabe mit dem Parameter verknüpft nur, wenn der Name des Parameters auf den Namen einer Eigenschaft des Eingabeobjekts entspricht.</span><span class="sxs-lookup"><span data-stu-id="b783a-124">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="b783a-125">Wenn der Parametername ist z. B. `Path`, nur, wenn das Objekt eine Eigenschaft namens Pfad hat, werden Objekte, die über die Pipeline an das Cmdlet diesen Parameter zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="b783a-125">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>

  - <span data-ttu-id="b783a-126">Wenn "true" (ByValue, ByPropertyName), Sie können die Eingabe für den Parameter übergeben, entweder durch den Namen oder Wert.</span><span class="sxs-lookup"><span data-stu-id="b783a-126">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="b783a-127">Nur ein Parameter in einem Parametersatz kann als Wert zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="b783a-127">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="b783a-128">False gibt an, können keine Sie Eingaben für diesen Parameter übergeben.</span><span class="sxs-lookup"><span data-stu-id="b783a-128">If false, you cannot pipe input to this parameter.</span></span>

- <span data-ttu-id="b783a-129">Verwendung von Platzhaltern</span><span class="sxs-lookup"><span data-stu-id="b783a-129">Globbing</span></span>

  - <span data-ttu-id="b783a-130">Bei "true", kann der Text, dass der Benutzer, für den Parameterwert eingibt Platzhalterzeichen enthalten.</span><span class="sxs-lookup"><span data-stu-id="b783a-130">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>

  - <span data-ttu-id="b783a-131">Wenn "false" kann nicht der Text an, dass der Benutzer, für den Parameterwert eingibt Platzhalterzeichen enthalten.</span><span class="sxs-lookup"><span data-stu-id="b783a-131">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="b783a-132">Parameterattribute-Wert</span><span class="sxs-lookup"><span data-stu-id="b783a-132">Parameter Value Attributes</span></span>

- <span data-ttu-id="b783a-133">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b783a-133">Required</span></span>

  - <span data-ttu-id="b783a-134">Bei "true", muss der angegebene Wert verwendet werden, wenn den Parameter in einem Befehl verwenden.</span><span class="sxs-lookup"><span data-stu-id="b783a-134">If true, the specified value must be used whenever using the parameter in a command.</span></span>

  - <span data-ttu-id="b783a-135">Wenn "false" ist der Wert des Parameters optional.</span><span class="sxs-lookup"><span data-stu-id="b783a-135">If false, the parameter value is optional.</span></span> <span data-ttu-id="b783a-136">In der Regel ist ein Wert optional, nur, wenn es mehrere gültige Werte für einen Parameter, wie z. B. ein enumerierter Typ ist.</span><span class="sxs-lookup"><span data-stu-id="b783a-136">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="b783a-137">Das erforderliche Attribut eines Parameterwerts unterscheidet sich von das erforderliche Attribut eines Parameters.</span><span class="sxs-lookup"><span data-stu-id="b783a-137">The Required attribute of a parameter value is different from the Required attribute of a parameter.</span></span>

<span data-ttu-id="b783a-138">Das required-Attribut eines Parameters gibt an, ob der Parameter (und sein Wert) eingeschlossen werden müssen, mit dem-Cmdlet aufrufen.</span><span class="sxs-lookup"><span data-stu-id="b783a-138">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="b783a-139">Im Gegensatz dazu wird das erforderliche Attribut eines Parameterwerts verwendet, nur, wenn der Parameter im Befehl enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="b783a-139">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="b783a-140">Er gibt an, ob es sich bei diesen bestimmte Wert mit dem Parameter verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="b783a-140">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="b783a-141">Klicken Sie in der Regel Parameterwerte, die Platzhalter sind erforderlich, und Parameterwerte Literale sind nicht erforderlich, da sie einen der folgenden Werte sind, die mit dem Parameter verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="b783a-141">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="b783a-142">Informationen über die Syntax werden ermittelt.</span><span class="sxs-lookup"><span data-stu-id="b783a-142">Gathering Syntax Information</span></span>

1. <span data-ttu-id="b783a-143">Beginnen Sie mit den Cmdlet-Namen.</span><span class="sxs-lookup"><span data-stu-id="b783a-143">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

2. <span data-ttu-id="b783a-144">Listen Sie alle Parameter des Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b783a-144">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="b783a-145">Geben Sie einen Bindestrich (auch bekannt als "Dash" oder "Minuszeichen (-)" (ASCII-45) vor jedem Parameternamen.</span><span class="sxs-lookup"><span data-stu-id="b783a-145">Type a dash (also known as a "dash" or "minus sign" (ASCII 45) before each parameter name.</span></span> <span data-ttu-id="b783a-146">Trennen Sie die Parameter in Parametersätze (einige Cmdlets kann nur ein Parameter festgelegt haben).</span><span class="sxs-lookup"><span data-stu-id="b783a-146">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="b783a-147">In diesem Beispiel das Get-Tech-Cmdlet verfügt über zwei Parametersätze.</span><span class="sxs-lookup"><span data-stu-id="b783a-147">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="b783a-148">Starten Sie jeden Parameter mit dem cmdletnamen festgelegt.</span><span class="sxs-lookup"><span data-stu-id="b783a-148">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="b783a-149">Listen Sie den Standardparameter, legen Sie zuerst fest auf.</span><span class="sxs-lookup"><span data-stu-id="b783a-149">List the default parameter set first.</span></span> <span data-ttu-id="b783a-150">Der Standardparameter wird von der Cmdlet-Klasse angegeben.</span><span class="sxs-lookup"><span data-stu-id="b783a-150">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="b783a-151">Listen Sie für jeden Parameter als eindeutige Parameter zuerst, es sei denn, es sind Positionsparameter, die zuerst angezeigt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="b783a-151">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="b783a-152">Im vorherigen Beispiel werden die Namen und ID-Parameter eindeutige Parameter für die beiden Parameter (jeder Parametersatz müssen einen Parameter, der auf die jeweiligen Parameter eindeutig ist).</span><span class="sxs-lookup"><span data-stu-id="b783a-152">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="b783a-153">Dies erleichtert es Benutzern, zu identifizieren, welche Parameter, die sie benötigen, geben Sie für den Parameter festgelegt.</span><span class="sxs-lookup"><span data-stu-id="b783a-153">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="b783a-154">Listet die Parameter in der Reihenfolge, die sie im Befehl angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b783a-154">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="b783a-155">Wenn die Reihenfolge keine Rolle spielt, Listen Sie die entsprechenden Parameter zusammen oder Listen Sie zuerst die am häufigsten verwendeten Parameter.</span><span class="sxs-lookup"><span data-stu-id="b783a-155">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="b783a-156">Achten Sie darauf, dass die WhatIf und Confirm-Parameter aufgelistet, wenn das Cmdlet ShouldProcess unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b783a-156">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="b783a-157">Listen Sie die allgemeinen Parameter (z. B. "Verbose", "Debug" und "ErrorAction") in Ihrem Syntaxdiagramm.</span><span class="sxs-lookup"><span data-stu-id="b783a-157">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="b783a-158">Die `Get-Help` Cmdlet fügt diese Informationen für Sie hinzu, wenn sie das Hilfethema angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b783a-158">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

3. <span data-ttu-id="b783a-159">Fügen Sie die Parameterwerte hinzu.</span><span class="sxs-lookup"><span data-stu-id="b783a-159">Add the parameter values.</span></span> <span data-ttu-id="b783a-160">In Windows PowerShell?, Parameterwerte werden anhand ihres Typs .NET dargestellt.</span><span class="sxs-lookup"><span data-stu-id="b783a-160">In Windows PowerShell?, parameter values are represented by their .NET type.</span></span> <span data-ttu-id="b783a-161">Allerdings kann der Typname abgekürzt werden, z. B. "String" für System.String.</span><span class="sxs-lookup"><span data-stu-id="b783a-161">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="b783a-162">Abkürzen Sie-Typen, solange ihre Bedeutung klar, wie z. B. "String" für System.String und "Int" für System. Int32 ist.</span><span class="sxs-lookup"><span data-stu-id="b783a-162">Abbreviate types as long as their meaning is clear, such as "string" for System.String and "int" for System.Int32.</span></span>

   <span data-ttu-id="b783a-163">Liste aller Werte von Enumerationen, z. B. der - Typparameter in der im vorherigen Beispiel, das "basic" oder "advanced" festgelegt werden kann.</span><span class="sxs-lookup"><span data-stu-id="b783a-163">List all values of enumerations, such as the -type parameter in the previous example, which can be set to "basic" or "advanced".</span></span>

   <span data-ttu-id="b783a-164">Switch-Parameter, z. B. - Liste im vorherigen Beispiel, die keinen Wert.</span><span class="sxs-lookup"><span data-stu-id="b783a-164">Switch parameters, such as -list in the previous example, do not have values.</span></span>

4. <span data-ttu-id="b783a-165">Fügen Sie Parameterwerte, Platzhalter im Vergleich zu den Parameterwerten, die Literale sind spitzen Klammern hinzu.</span><span class="sxs-lookup"><span data-stu-id="b783a-165">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. <span data-ttu-id="b783a-166">Schließen Sie optionale Parameter und deren Werte in eckige Klammern ein.</span><span class="sxs-lookup"><span data-stu-id="b783a-166">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. <span data-ttu-id="b783a-167">Schließen Sie optionale Parameter-Namen (für Positionsparameter) in eckige Klammern ein.</span><span class="sxs-lookup"><span data-stu-id="b783a-167">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="b783a-168">Der Name für den Parameter, die mit Feldern fester Breite, z. B. den Name-Parameter im folgenden Beispiel sind keine im Befehl enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="b783a-168">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. <span data-ttu-id="b783a-169">Fügen Sie ein paar eckige Klammern direkt nach der Wert des Parameters hinzu, wenn ein Parameterwert z. B. eine Liste von Namen in den Name-Parameter mehrere Werte enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="b783a-169">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. <span data-ttu-id="b783a-170">Wenn der Benutzer Parameter oder Parameterwerte auswählen kann, schließen Sie die Optionen wie des Typparameters in geschweiften Klammern einfügen, und trennen Sie diese durch die exklusive OR-symbol(;).</span><span class="sxs-lookup"><span data-stu-id="b783a-170">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. <span data-ttu-id="b783a-171">Wenn der Wert des Parameters bestimmte Formatierung verwenden muss, z. B. Anführungszeichen oder Klammern, zeigen Sie das Format, in der Syntax.</span><span class="sxs-lookup"><span data-stu-id="b783a-171">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="b783a-172">Das Syntaxdiagramm XML-Codierung</span><span class="sxs-lookup"><span data-stu-id="b783a-172">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="b783a-173">Der syntaxknoten des XML-beginnt sofort nach der Beschreibung-Knoten, die mit endet die \</maml:description > Tag.</span><span class="sxs-lookup"><span data-stu-id="b783a-173">The syntax node of the XML begins immediately after the description node, which ends with the \</maml:description> tag.</span></span> <span data-ttu-id="b783a-174">Informationen zum Erfassen der Daten, die im Syntax verwendet, finden Sie unter [Sammeln von Informationen über die Syntax](#Gathering-Syntax-Information).</span><span class="sxs-lookup"><span data-stu-id="b783a-174">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#Gathering-Syntax-Information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="b783a-175">Hinzufügen eines Syntaxknotens</span><span class="sxs-lookup"><span data-stu-id="b783a-175">Adding a Syntax Node</span></span>

<span data-ttu-id="b783a-176">Das Syntaxdiagramm, die in der Cmdlet-Hilfethemas angezeigt wird aus den Daten im Knoten "Syntax" von der XML-Code generiert.</span><span class="sxs-lookup"><span data-stu-id="b783a-176">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="b783a-177">Der syntaxknoten wird in ein paar eingeschlossen, wenn \<Befehlssyntax: > Tags.</span><span class="sxs-lookup"><span data-stu-id="b783a-177">The syntax node is enclosed in a pair if \<command:syntax> tags.</span></span> <span data-ttu-id="b783a-178">Mit jeder Parametersatz des-Cmdlets in einem Paar von eingeschlossen \<-Befehl: Syntaxitem > Tags.</span><span class="sxs-lookup"><span data-stu-id="b783a-178">With each parameter set of the cmdlet enclosed in a pair of \<command:syntaxitem> tags.</span></span> <span data-ttu-id="b783a-179">Es gibt keine Beschränkung der Anzahl der \<-Befehl: Syntaxitem >-Tags, die Sie hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="b783a-179">There is no limit to the number of \<command:syntaxitem> tags that you can add.</span></span>

<span data-ttu-id="b783a-180">Das folgende Beispiel zeigt einen syntaxknoten, der Syntax-Element-Knoten für zwei Parametersätze aufweist.</span><span class="sxs-lookup"><span data-stu-id="b783a-180">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="b783a-181">Hinzufügen von Cmdlet-Namen für den Parameter festlegen, dass Daten</span><span class="sxs-lookup"><span data-stu-id="b783a-181">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="b783a-182">Jeder Parametersatz, der dem-Cmdlet wird in einen syntaxknoten für das Element angegeben.</span><span class="sxs-lookup"><span data-stu-id="b783a-182">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="b783a-183">Jedes Element syntaxknoten beginnt mit einem Paar von \<Maml:name >-Tags, die den Namen des Cmdlets enthalten.</span><span class="sxs-lookup"><span data-stu-id="b783a-183">Each syntax item node begins with a pair of \<maml:name> tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="b783a-184">Das folgende Beispiel enthält einen syntaxknoten, der Syntax-Element-Knoten für zwei Parametersätze aufweist.</span><span class="sxs-lookup"><span data-stu-id="b783a-184">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-parameters"></a><span data-ttu-id="b783a-185">Hinzufügen von Parametern</span><span class="sxs-lookup"><span data-stu-id="b783a-185">Adding Parameters</span></span>

<span data-ttu-id="b783a-186">Jeder Parameter der syntaxknoten für das Element hinzugefügt wird angegeben, in ein Paar \<Befehlsparameter: > Tags.</span><span class="sxs-lookup"><span data-stu-id="b783a-186">Each parameter added to the syntax item node is specified within a pair of \<command:parameter> tags.</span></span> <span data-ttu-id="b783a-187">Sie benötigen ein Paar von \<Befehlsparameter: >-Tags für jeden Parameter in den Parametersatz, mit Ausnahme von der allgemeinen Parameter, die von Windows PowerShell bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="b783a-187">You need a pair of \<command:parameter> tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by Windows PowerShell?.</span></span>

<span data-ttu-id="b783a-188">Die Attribute des das öffnendes \<Befehlsparameter: > Tag zu ermitteln, wie der Parameter in der Syntaxdiagramm wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b783a-188">The attributes of the opening \<command:parameter> tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="b783a-189">Informationen zu Attributen der Parameter finden Sie unter [Parameterattribute](#Parameter-Attributes).</span><span class="sxs-lookup"><span data-stu-id="b783a-189">For information on parameter attributes, see [Parameter Attributes](#Parameter-Attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="b783a-190">Die \<Befehlsparameter: > Tag unterstützt ein untergeordnetes Element \<Maml:description >, dessen Inhalt wird nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b783a-190">The \<command:parameter> tag supports a child element \<maml:description> whose content is never displayed.</span></span> <span data-ttu-id="b783a-191">Die Beschreibung der Parameter werden im Knoten "Parameter" des XML-angegeben.</span><span class="sxs-lookup"><span data-stu-id="b783a-191">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="b783a-192">Bodes, die Informationen in der Syntaxelement auf Inkonsistenzen zu vermeiden und die Parameterknoten, und lassen Sie die (\<Maml:description > oder leer bleiben.</span><span class="sxs-lookup"><span data-stu-id="b783a-192">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (\<maml:description> or leave it empty.</span></span>

<span data-ttu-id="b783a-193">Das folgende Beispiel enthält einen syntaxknoten-Element für einen Parameter mit zwei Parametern festgelegt.</span><span class="sxs-lookup"><span data-stu-id="b783a-193">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

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
