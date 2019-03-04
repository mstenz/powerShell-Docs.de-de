---
title: Dynamische Parameter für ein Hilfethema Anbieter hinzufügen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859876"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="d0679-102">Hinzufügen von dynamischen Parametern zu einem Anbieterhilfethema</span><span class="sxs-lookup"><span data-stu-id="d0679-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="d0679-103">In diesem Abschnitt wird erläutert, wie zum Auffüllen der **dynamische Parameter** Abschnitt eines Hilfethemas für den Anbieter.</span><span class="sxs-lookup"><span data-stu-id="d0679-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="d0679-104">*Dynamische Parameter* sind Parametern eines Cmdlets oder Funktion, die verfügbar sind, nur unter angegebenen Bedingungen.</span><span class="sxs-lookup"><span data-stu-id="d0679-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="d0679-105">Die dynamischen Parameter, die in einem Hilfethema Anbieter dokumentiert sind, sind die dynamischen Parameter, die der Anbieter das-Cmdlet oder einer Funktion hinzufügt, wenn das Cmdlet oder eine Funktion in einem Laufwerk für den Anbieter verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d0679-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="d0679-106">Dynamische Parameter können auch in benutzerdefinierte Cmdlet-Hilfe für einen Anbieter dokumentiert werden.</span><span class="sxs-lookup"><span data-stu-id="d0679-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="d0679-107">Wenn sowohl Hilfe durch Anbieter als auch benutzerdefinierte Cmdlet-Hilfe für einen Anbieter schreiben, werden enthalten Sie die dynamischen Parameter-Dokumentation in beiden Dokumenten.</span><span class="sxs-lookup"><span data-stu-id="d0679-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="d0679-108">Weitere Informationen über benutzerdefinierte Cmdlet-Hilfe finden Sie unter [Schreiben von Windows PowerShell benutzerdefinierte Cmdlet-Hilfe für Anbieter](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span><span class="sxs-lookup"><span data-stu-id="d0679-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="d0679-109">Wenn ein Anbieter keine dynamischen Parameter implementiert, enthält das Thema Anbieter eine leere `DynamicParameters` Element.</span><span class="sxs-lookup"><span data-stu-id="d0679-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="d0679-110">Dynamische Parameter hinzufügen</span><span class="sxs-lookup"><span data-stu-id="d0679-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="d0679-111">In der *AssemblyName*help.xml-DLL-Datei, in der `providerHelp` -Element, Hinzufügen einer `DynamicParameters` Element.</span><span class="sxs-lookup"><span data-stu-id="d0679-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="d0679-112">Die `DynamicParameters` Element sollte angezeigt werden, nachdem die `Tasks` Element und vor der `RelatedLinks` Element.</span><span class="sxs-lookup"><span data-stu-id="d0679-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="d0679-113">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d0679-113">For example:</span></span>

    ```xml
    <providerHelp>
        <Tasks>
        </Tasks>
        <DynamicParameters>
        </DynamicParameters>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

   <span data-ttu-id="d0679-114">Wenn der Anbieter keine dynamischen Parameter, implementiert die `DynamicParameters` Element kann leer sein.</span><span class="sxs-lookup"><span data-stu-id="d0679-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="d0679-115">In der `DynamicParameters` -Element, für jeden dynamischen Parameter Hinzufügen einer `DynamicParameter` Element.</span><span class="sxs-lookup"><span data-stu-id="d0679-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="d0679-116">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d0679-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="d0679-117">In den einzelnen `DynamicParameter` -Element, Hinzufügen einer `Name` und `CmdletSupported` Element.</span><span class="sxs-lookup"><span data-stu-id="d0679-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="d0679-118">Elementname</span><span class="sxs-lookup"><span data-stu-id="d0679-118">Element Name</span></span>|<span data-ttu-id="d0679-119">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d0679-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="d0679-120">Name</span><span class="sxs-lookup"><span data-stu-id="d0679-120">Name</span></span>|<span data-ttu-id="d0679-121">Gibt den Namen des Parameters an.</span><span class="sxs-lookup"><span data-stu-id="d0679-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="d0679-122">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="d0679-122">CmdletSupported</span></span>|<span data-ttu-id="d0679-123">Gibt die Cmdlets, die in denen der Parameter gültig ist.</span><span class="sxs-lookup"><span data-stu-id="d0679-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="d0679-124">Geben Sie eine durch Trennzeichen getrennte Liste von Cmdlet-Namen ein.</span><span class="sxs-lookup"><span data-stu-id="d0679-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="d0679-125">Z. B. den folgenden XML-Dokumenten die `Encoding` dynamischer Parameter, die der Windows PowerShell-FileSystem-Anbieter hinzufügt der `Add-Content`, `Get-Content`, `Set-Content` Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d0679-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="d0679-126">In den einzelnen `DynamicParameter` -Element, Hinzufügen einer `Type` Element.</span><span class="sxs-lookup"><span data-stu-id="d0679-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="d0679-127">Die `Type` Element ist ein Container für die `Name` Element, das den Typ .NET den Wert, der den dynamischen Parameter enthält.</span><span class="sxs-lookup"><span data-stu-id="d0679-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="d0679-128">Z. B. das folgende XML zeigt, die den .NET-Typ, der die `Encoding` dynamischer Parameter ist der [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) Enumeration.</span><span class="sxs-lookup"><span data-stu-id="d0679-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
    ...
    </DynamicParameters>
    ```

5. <span data-ttu-id="d0679-129">Hinzufügen der `Description` -Element, das eine kurze Beschreibung der dynamische Parameter enthält.</span><span class="sxs-lookup"><span data-stu-id="d0679-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="d0679-130">Beim Erstellen der Beschreibung verwenden Sie die Richtlinien, die für alle cmdletparameter im vorgeschriebenen [wie Hinzufügen von Parameterinformationen](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="d0679-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="d0679-131">Das folgende XML enthält beispielsweise die Beschreibung des der `Encoding` dynamischer Parameter.</span><span class="sxs-lookup"><span data-stu-id="d0679-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
            <Description> Specifies the encoding of the output file that contains the content. </Description>
    ...
    </DynamicParameters>
    ```

6. <span data-ttu-id="d0679-132">Hinzufügen der `PossibleValues` -Element und seine untergeordneten Elemente.</span><span class="sxs-lookup"><span data-stu-id="d0679-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="d0679-133">Zusammen beschreiben diese Elemente die Werte von den dynamischen Parameter.</span><span class="sxs-lookup"><span data-stu-id="d0679-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="d0679-134">Dieses Element dient zur aufgezählte Werte.</span><span class="sxs-lookup"><span data-stu-id="d0679-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="d0679-135">Wenn der dynamische Parameter nicht über einen Wert akzeptiert, wie z. B. bei einer Switch-Parameter der Fall ist, oder die Werte können nicht aufgezählt werden, fügen Sie eine leere `PossibleValues` Element.</span><span class="sxs-lookup"><span data-stu-id="d0679-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="d0679-136">In der folgende Tabelle aufgelistet und beschrieben die `PossibleValues` -Element und seine untergeordneten Elemente.</span><span class="sxs-lookup"><span data-stu-id="d0679-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="d0679-137">Elementname</span><span class="sxs-lookup"><span data-stu-id="d0679-137">Element Name</span></span>|<span data-ttu-id="d0679-138">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d0679-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="d0679-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="d0679-139">PossibleValues</span></span>|<span data-ttu-id="d0679-140">Dieses Element ist ein Container.</span><span class="sxs-lookup"><span data-stu-id="d0679-140">This element is a container.</span></span> <span data-ttu-id="d0679-141">Die untergeordneten Elemente werden nachfolgend beschrieben.</span><span class="sxs-lookup"><span data-stu-id="d0679-141">Its child elements are described below.</span></span> <span data-ttu-id="d0679-142">Fügen Sie eine `PossibleValues` Element jedes Hilfethemas für den Anbieter.</span><span class="sxs-lookup"><span data-stu-id="d0679-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="d0679-143">Das Element kann leer sein.</span><span class="sxs-lookup"><span data-stu-id="d0679-143">The element can be empty.</span></span>|
   |<span data-ttu-id="d0679-144">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="d0679-144">PossibleValue</span></span>|<span data-ttu-id="d0679-145">Dieses Element ist ein Container.</span><span class="sxs-lookup"><span data-stu-id="d0679-145">This element is a container.</span></span> <span data-ttu-id="d0679-146">Die untergeordneten Elemente werden nachfolgend beschrieben.</span><span class="sxs-lookup"><span data-stu-id="d0679-146">Its child elements are described below.</span></span> <span data-ttu-id="d0679-147">Fügen Sie eine `PossibleValue` -Element für jeden Wert von den dynamischen Parameter.</span><span class="sxs-lookup"><span data-stu-id="d0679-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="d0679-148">Wert</span><span class="sxs-lookup"><span data-stu-id="d0679-148">Value</span></span>|<span data-ttu-id="d0679-149">Gibt den Namen des Werts an.</span><span class="sxs-lookup"><span data-stu-id="d0679-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="d0679-150">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d0679-150">Description</span></span>|<span data-ttu-id="d0679-151">Dieses Element enthält eine `Para` Element.</span><span class="sxs-lookup"><span data-stu-id="d0679-151">This element contains a `Para` element.</span></span> <span data-ttu-id="d0679-152">Der Text in die `Para` -Element beschreibt den Wert mit dem Namen in der `Value` Element.</span><span class="sxs-lookup"><span data-stu-id="d0679-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="d0679-153">Das folgende XML zeigt beispielsweise eine `PossibleValue` Element der `Encoding` dynamischer Parameter.</span><span class="sxs-lookup"><span data-stu-id="d0679-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
    ...
            <Description> Specifies the encoding of the output file that contains the content. </Description>
            <PossibleValues>
                <PossibleValue>
                    <Value> ASCII </Value>
                    <Description>
                        <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                    </Description>
                </PossibleValue>
    ...
            </PossibleValues>
    </DynamicParameters>
    ```

## <a name="example"></a><span data-ttu-id="d0679-154">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d0679-154">Example</span></span>

<span data-ttu-id="d0679-155">Das folgende Beispiel zeigt die `DynamicParameters` Element der `Encoding` dynamischer Parameter.</span><span class="sxs-lookup"><span data-stu-id="d0679-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

```xml
<DynamicParameters/>
    <DynamicParameter>
        <Name> Encoding </Name>
        <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
        <Type>
            <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
        <Type>
        <Description> Specifies the encoding of the output file that contains the content. </Description>
        <PossibleValues>
            <PossibleValue>
                <Value> ASCII </Value>
                <Description>
                    <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                </Description>
            </PossibleValue>
            <PossibleValue>
                <Value> Unicode </Value>
                <Description>
                    <para> Encodes in UTF-16 format using the little-endian byte order. </para>
                </Description>
            </PossibleValue>
        </PossibleValues>
</DynamicParameters>
```