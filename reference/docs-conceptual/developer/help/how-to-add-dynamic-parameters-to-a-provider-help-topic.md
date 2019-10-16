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
ms.openlocfilehash: 59839e9b8b6f2a56f2f1a9c755f2f1a85deb34aa
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361259"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="0ac96-102">Hinzufügen von dynamischen Parametern zu einem Anbieterhilfethema</span><span class="sxs-lookup"><span data-stu-id="0ac96-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="0ac96-103">In diesem Abschnitt wird erläutert, wie der Abschnitt **dynamische Parameter** eines Hilfe Themas für den Anbieter ausgefüllt wird.</span><span class="sxs-lookup"><span data-stu-id="0ac96-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="0ac96-104">*Dynamische Parameter* sind Parameter eines Cmdlets oder einer Funktion, die nur unter den angegebenen Bedingungen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="0ac96-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="0ac96-105">Die dynamischen Parameter, die in einem Anbieter Hilfethema dokumentiert werden, sind die dynamischen Parameter, die der Anbieter dem Cmdlet oder der Funktion hinzufügt, wenn das Cmdlet oder die Funktion im Anbieter Laufwerk verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0ac96-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="0ac96-106">Dynamische Parameter können auch in der benutzerdefinierten Cmdlet-Hilfe für einen Anbieter dokumentiert werden.</span><span class="sxs-lookup"><span data-stu-id="0ac96-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="0ac96-107">Wenn Sie sowohl Anbieter Hilfe als auch benutzerdefinierte Cmdlet-Hilfe für einen Anbieter schreiben, fügen Sie die dynamische Parameter Dokumentation in beide Dokumente ein.</span><span class="sxs-lookup"><span data-stu-id="0ac96-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span>

<span data-ttu-id="0ac96-108">Wenn ein Anbieter keine dynamischen Parameter implementiert, enthält das Hilfethema für den Anbieter ein leeres `DynamicParameters`-Element.</span><span class="sxs-lookup"><span data-stu-id="0ac96-108">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="0ac96-109">So fügen Sie dynamische Parameter hinzu</span><span class="sxs-lookup"><span data-stu-id="0ac96-109">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="0ac96-110">Fügen Sie in der Datei *AssemblyName*. dll-Help. XML innerhalb des `providerHelp`-Elements ein `DynamicParameters`-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="0ac96-110">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="0ac96-111">Das `DynamicParameters`-Element sollte nach dem `Tasks`-Element und vor dem `RelatedLinks`-Element angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="0ac96-111">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="0ac96-112">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="0ac96-112">For example:</span></span>

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

   <span data-ttu-id="0ac96-113">Wenn der Anbieter keine dynamischen Parameter implementiert, kann das `DynamicParameters`-Element leer sein.</span><span class="sxs-lookup"><span data-stu-id="0ac96-113">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="0ac96-114">Fügen Sie im `DynamicParameters`-Element für jeden dynamischen Parameter ein `DynamicParameter`-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="0ac96-114">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="0ac96-115">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="0ac96-115">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="0ac96-116">Fügen Sie in jedem `DynamicParameter`-Element ein `Name`-und `CmdletSupported`-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="0ac96-116">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="0ac96-117">Elementname</span><span class="sxs-lookup"><span data-stu-id="0ac96-117">Element Name</span></span>|<span data-ttu-id="0ac96-118">Description</span><span class="sxs-lookup"><span data-stu-id="0ac96-118">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="0ac96-119">Name</span><span class="sxs-lookup"><span data-stu-id="0ac96-119">Name</span></span>|<span data-ttu-id="0ac96-120">Gibt den Parameternamen an.</span><span class="sxs-lookup"><span data-stu-id="0ac96-120">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="0ac96-121">Cmdletunter stützt</span><span class="sxs-lookup"><span data-stu-id="0ac96-121">CmdletSupported</span></span>|<span data-ttu-id="0ac96-122">Gibt die Cmdlets an, in denen der Parameter gültig ist.</span><span class="sxs-lookup"><span data-stu-id="0ac96-122">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="0ac96-123">Geben Sie eine durch Trennzeichen getrennte Liste von Cmdlet-Namen ein.</span><span class="sxs-lookup"><span data-stu-id="0ac96-123">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="0ac96-124">Im folgenden XML-Code wird beispielsweise der dynamische Parameter `Encoding` dokumentiert, den der Windows PowerShell-File System-Anbieter den `Add-Content`-, `Get-Content`-, `Set-Content`-Cmdlets hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="0ac96-124">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="0ac96-125">Fügen Sie in jedem `DynamicParameter`-Element ein `Type`-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="0ac96-125">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="0ac96-126">Das `Type`-Element ist ein Container für das `Name`-Element, das den .NET-Typ des Werts des dynamischen Parameters enthält.</span><span class="sxs-lookup"><span data-stu-id="0ac96-126">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="0ac96-127">Der folgende XML-Code zeigt beispielsweise, dass der .NET-Typ des dynamischen Parameters `Encoding` die [Microsoft. PowerShell. Commands. filesystemcmdletproviderencoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) -Enumeration ist.</span><span class="sxs-lookup"><span data-stu-id="0ac96-127">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="0ac96-128">Fügen Sie das `Description`-Element hinzu, das eine kurze Beschreibung des dynamischen Parameters enthält.</span><span class="sxs-lookup"><span data-stu-id="0ac96-128">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="0ac96-129">Wenn Sie die Beschreibung verfassen, verwenden Sie die Richtlinien, die für alle Cmdlet-Parameter in [Hinzufügen von Parameterinformationen](./how-to-add-parameter-information.md)vorgeschrieben sind.</span><span class="sxs-lookup"><span data-stu-id="0ac96-129">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="0ac96-130">Der folgende XML-Code enthält z. b. die Beschreibung des dynamischen Parameters `Encoding`.</span><span class="sxs-lookup"><span data-stu-id="0ac96-130">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="0ac96-131">Fügen Sie das `PossibleValues`-Element und seine untergeordneten Elemente hinzu.</span><span class="sxs-lookup"><span data-stu-id="0ac96-131">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="0ac96-132">Diese Elemente beschreiben gemeinsame Werte des dynamischen Parameters.</span><span class="sxs-lookup"><span data-stu-id="0ac96-132">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="0ac96-133">Dieses Element ist für Enumerationswerte konzipiert.</span><span class="sxs-lookup"><span data-stu-id="0ac96-133">This element is designed for enumerated values.</span></span> <span data-ttu-id="0ac96-134">Wenn der dynamische Parameter keinen Wert annimmt, wie z. b. den Fall mit einem Switch-Parameter, oder wenn die Werte nicht aufgelistet werden können, fügen Sie ein leeres `PossibleValues`-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="0ac96-134">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="0ac96-135">In der folgenden Tabelle werden das `PossibleValues`-Element und seine untergeordneten Elemente aufgelistet und beschrieben.</span><span class="sxs-lookup"><span data-stu-id="0ac96-135">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="0ac96-136">Elementname</span><span class="sxs-lookup"><span data-stu-id="0ac96-136">Element Name</span></span>|<span data-ttu-id="0ac96-137">Description</span><span class="sxs-lookup"><span data-stu-id="0ac96-137">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="0ac96-138">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="0ac96-138">PossibleValues</span></span>|<span data-ttu-id="0ac96-139">Dieses Element ist ein Container.</span><span class="sxs-lookup"><span data-stu-id="0ac96-139">This element is a container.</span></span> <span data-ttu-id="0ac96-140">Die untergeordneten Elemente werden unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="0ac96-140">Its child elements are described below.</span></span> <span data-ttu-id="0ac96-141">Fügen Sie jedem Anbieter Hilfethema ein `PossibleValues`-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="0ac96-141">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="0ac96-142">Das Element kann leer sein.</span><span class="sxs-lookup"><span data-stu-id="0ac96-142">The element can be empty.</span></span>|
   |<span data-ttu-id="0ac96-143">Possiblevalue</span><span class="sxs-lookup"><span data-stu-id="0ac96-143">PossibleValue</span></span>|<span data-ttu-id="0ac96-144">Dieses Element ist ein Container.</span><span class="sxs-lookup"><span data-stu-id="0ac96-144">This element is a container.</span></span> <span data-ttu-id="0ac96-145">Die untergeordneten Elemente werden unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="0ac96-145">Its child elements are described below.</span></span> <span data-ttu-id="0ac96-146">Fügen Sie ein `PossibleValue`-Element für jeden Wert des dynamischen Parameters hinzu.</span><span class="sxs-lookup"><span data-stu-id="0ac96-146">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="0ac96-147">Value</span><span class="sxs-lookup"><span data-stu-id="0ac96-147">Value</span></span>|<span data-ttu-id="0ac96-148">Gibt den Wertnamen an.</span><span class="sxs-lookup"><span data-stu-id="0ac96-148">Specifies the value name.</span></span>|
   |<span data-ttu-id="0ac96-149">Description</span><span class="sxs-lookup"><span data-stu-id="0ac96-149">Description</span></span>|<span data-ttu-id="0ac96-150">Dieses Element enthält ein `Para`-Element.</span><span class="sxs-lookup"><span data-stu-id="0ac96-150">This element contains a `Para` element.</span></span> <span data-ttu-id="0ac96-151">Der Text im `Para`-Element beschreibt den Wert, der im `Value`-Element benannt ist.</span><span class="sxs-lookup"><span data-stu-id="0ac96-151">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="0ac96-152">Der folgende XML-Code zeigt z. b. ein `PossibleValue`-Element des dynamischen Parameters `Encoding` an.</span><span class="sxs-lookup"><span data-stu-id="0ac96-152">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="0ac96-153">Beispiel</span><span class="sxs-lookup"><span data-stu-id="0ac96-153">Example</span></span>

<span data-ttu-id="0ac96-154">Das folgende Beispiel zeigt das `DynamicParameters`-Element des dynamischen Parameters `Encoding`.</span><span class="sxs-lookup"><span data-stu-id="0ac96-154">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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