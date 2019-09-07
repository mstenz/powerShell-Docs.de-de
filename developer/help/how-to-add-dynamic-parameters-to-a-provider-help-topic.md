---
title: Vorgehensweise beim Hinzufügen von dynamischen Parametern zu einem Anbieter-Hilfethema | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: ffcc1c55f5b3adc063353cb75f2a2183acc2234a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2019
ms.locfileid: "70737603"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="4889e-102">Hinzufügen von dynamischen Parametern zu einem Anbieterhilfethema</span><span class="sxs-lookup"><span data-stu-id="4889e-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="4889e-103">In diesem Abschnitt wird erläutert, wie der Abschnitt **dynamische Parameter** eines Hilfe Themas für den Anbieter ausgefüllt wird.</span><span class="sxs-lookup"><span data-stu-id="4889e-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="4889e-104">*Dynamische Parameter* sind Parameter eines Cmdlets oder einer Funktion, die nur unter den angegebenen Bedingungen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="4889e-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="4889e-105">Die dynamischen Parameter, die in einem Anbieter Hilfethema dokumentiert werden, sind die dynamischen Parameter, die der Anbieter dem Cmdlet oder der Funktion hinzufügt, wenn das Cmdlet oder die Funktion im Anbieter Laufwerk verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="4889e-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="4889e-106">Dynamische Parameter können auch in der benutzerdefinierten Cmdlet-Hilfe für einen Anbieter dokumentiert werden.</span><span class="sxs-lookup"><span data-stu-id="4889e-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="4889e-107">Wenn Sie sowohl Anbieter Hilfe als auch benutzerdefinierte Cmdlet-Hilfe für einen Anbieter schreiben, fügen Sie die dynamische Parameter Dokumentation in beide Dokumente ein.</span><span class="sxs-lookup"><span data-stu-id="4889e-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="4889e-108">Weitere Informationen zu benutzerdefinierten Cmdlet-Hilfe finden Sie unter Erstellen einer [benutzerdefinierten Windows PowerShell-Cmdlet-Hilfe für Anbieter](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span><span class="sxs-lookup"><span data-stu-id="4889e-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="4889e-109">Wenn ein Anbieter keine dynamischen Parameter implementiert, enthält das Hilfethema für den Anbieter ein leeres `DynamicParameters` -Element.</span><span class="sxs-lookup"><span data-stu-id="4889e-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="4889e-110">So fügen Sie dynamische Parameter hinzu</span><span class="sxs-lookup"><span data-stu-id="4889e-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="4889e-111">Fügen Sie in der Datei `providerHelp` *AssemblyName*. dll-Help. XML im-Element ein `DynamicParameters` -Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="4889e-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="4889e-112">Das `DynamicParameters` -Element sollte nach dem `Tasks` -Element und vor `RelatedLinks` dem-Element angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="4889e-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="4889e-113">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="4889e-113">For example:</span></span>

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

   <span data-ttu-id="4889e-114">Wenn der Anbieter keine dynamischen Parameter implementiert, kann das `DynamicParameters` Element leer sein.</span><span class="sxs-lookup"><span data-stu-id="4889e-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="4889e-115">Fügen Sie im- `DynamicParameter` ElementfürjedendynamischenParameterein-Elementhinzu.`DynamicParameters`</span><span class="sxs-lookup"><span data-stu-id="4889e-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="4889e-116">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="4889e-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="4889e-117">Fügen Sie `DynamicParameter` in jedem-Element `Name` ein `CmdletSupported` -und ein-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="4889e-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="4889e-118">Elementname</span><span class="sxs-lookup"><span data-stu-id="4889e-118">Element Name</span></span>|<span data-ttu-id="4889e-119">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4889e-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="4889e-120">Name</span><span class="sxs-lookup"><span data-stu-id="4889e-120">Name</span></span>|<span data-ttu-id="4889e-121">Gibt den Parameternamen an.</span><span class="sxs-lookup"><span data-stu-id="4889e-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="4889e-122">Cmdletunter stützt</span><span class="sxs-lookup"><span data-stu-id="4889e-122">CmdletSupported</span></span>|<span data-ttu-id="4889e-123">Gibt die Cmdlets an, in denen der Parameter gültig ist.</span><span class="sxs-lookup"><span data-stu-id="4889e-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="4889e-124">Geben Sie eine durch Trennzeichen getrennte Liste von Cmdlet-Namen ein.</span><span class="sxs-lookup"><span data-stu-id="4889e-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="4889e-125">Der folgende XML-Code dokumentiert z. `Encoding` b. den dynamischen Parameter, den der Windows PowerShell- `Add-Content`File System `Set-Content` -Anbieter den Cmdlets, `Get-Content`, hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="4889e-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="4889e-126">Fügen Sie `DynamicParameter` in jedem-Element `Type` ein-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="4889e-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="4889e-127">Das `Type` -Element ist ein Container für `Name` das-Element, das den .NET-Typ des Werts des dynamischen Parameters enthält.</span><span class="sxs-lookup"><span data-stu-id="4889e-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="4889e-128">Der folgende XML-Code zeigt beispielsweise, dass der .net- `Encoding` Typ des dynamischen Parameters die [Microsoft. PowerShell. Commands. filesystemcmdletproviderencoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) -Enumeration ist.</span><span class="sxs-lookup"><span data-stu-id="4889e-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="4889e-129">Fügen Sie `Description` das-Element hinzu, das eine kurze Beschreibung des dynamischen Parameters enthält.</span><span class="sxs-lookup"><span data-stu-id="4889e-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="4889e-130">Wenn Sie die Beschreibung verfassen, verwenden Sie die Richtlinien, die für alle Cmdlet-Parameter in [Hinzufügen von Parameterinformationen](./how-to-add-parameter-information.md)vorgeschrieben sind.</span><span class="sxs-lookup"><span data-stu-id="4889e-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="4889e-131">Der folgende XML-Code enthält z. b. die `Encoding` Beschreibung des dynamischen Parameters.</span><span class="sxs-lookup"><span data-stu-id="4889e-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="4889e-132">Fügen Sie `PossibleValues` das-Element und seine untergeordneten Elemente hinzu.</span><span class="sxs-lookup"><span data-stu-id="4889e-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="4889e-133">Diese Elemente beschreiben gemeinsame Werte des dynamischen Parameters.</span><span class="sxs-lookup"><span data-stu-id="4889e-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="4889e-134">Dieses Element ist für Enumerationswerte konzipiert.</span><span class="sxs-lookup"><span data-stu-id="4889e-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="4889e-135">Wenn der dynamische Parameter keinen Wert annimmt, wie z. b. bei einem Switch-Parameter, oder wenn die Werte nicht aufgelistet werden können, fügen Sie ein `PossibleValues` leeres-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="4889e-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="4889e-136">In der folgenden Tabelle sind das- `PossibleValues` Element und seine untergeordneten Elemente aufgelistet und beschrieben.</span><span class="sxs-lookup"><span data-stu-id="4889e-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="4889e-137">Elementname</span><span class="sxs-lookup"><span data-stu-id="4889e-137">Element Name</span></span>|<span data-ttu-id="4889e-138">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4889e-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="4889e-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="4889e-139">PossibleValues</span></span>|<span data-ttu-id="4889e-140">Dieses Element ist ein Container.</span><span class="sxs-lookup"><span data-stu-id="4889e-140">This element is a container.</span></span> <span data-ttu-id="4889e-141">Die untergeordneten Elemente werden unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="4889e-141">Its child elements are described below.</span></span> <span data-ttu-id="4889e-142">Fügen Sie `PossibleValues` jedem Anbieter Hilfethema ein-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="4889e-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="4889e-143">Das Element kann leer sein.</span><span class="sxs-lookup"><span data-stu-id="4889e-143">The element can be empty.</span></span>|
   |<span data-ttu-id="4889e-144">Possiblevalue</span><span class="sxs-lookup"><span data-stu-id="4889e-144">PossibleValue</span></span>|<span data-ttu-id="4889e-145">Dieses Element ist ein Container.</span><span class="sxs-lookup"><span data-stu-id="4889e-145">This element is a container.</span></span> <span data-ttu-id="4889e-146">Die untergeordneten Elemente werden unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="4889e-146">Its child elements are described below.</span></span> <span data-ttu-id="4889e-147">Fügen Sie `PossibleValue` ein-Element für jeden Wert des dynamischen Parameters hinzu.</span><span class="sxs-lookup"><span data-stu-id="4889e-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="4889e-148">Wert</span><span class="sxs-lookup"><span data-stu-id="4889e-148">Value</span></span>|<span data-ttu-id="4889e-149">Gibt den Wertnamen an.</span><span class="sxs-lookup"><span data-stu-id="4889e-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="4889e-150">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4889e-150">Description</span></span>|<span data-ttu-id="4889e-151">Dieses Element enthält ein `Para` -Element.</span><span class="sxs-lookup"><span data-stu-id="4889e-151">This element contains a `Para` element.</span></span> <span data-ttu-id="4889e-152">Der Text im `Para` -Element beschreibt den Wert, der `Value` im-Element benannt wird.</span><span class="sxs-lookup"><span data-stu-id="4889e-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="4889e-153">Der folgende XML-Code zeigt z. `PossibleValue` b. ein `Encoding` Element des dynamischen Parameters.</span><span class="sxs-lookup"><span data-stu-id="4889e-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="4889e-154">Beispiel</span><span class="sxs-lookup"><span data-stu-id="4889e-154">Example</span></span>

<span data-ttu-id="4889e-155">Das folgende Beispiel zeigt das `DynamicParameters` -Element `Encoding` des dynamischen Parameters.</span><span class="sxs-lookup"><span data-stu-id="4889e-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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