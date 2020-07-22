---
title: Hinzufügen von dynamischen Parametern zu einem Anbieterhilfethema
ms.date: 09/13/2016
ms.openlocfilehash: ddf964292ee7bf477767a2ca17c717aef84bad51
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893457"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="8c7e0-102">Hinzufügen von dynamischen Parametern zu einem Anbieterhilfethema</span><span class="sxs-lookup"><span data-stu-id="8c7e0-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="8c7e0-103">In diesem Abschnitt wird erläutert, wie der Abschnitt **dynamische Parameter** eines Hilfe Themas für den Anbieter ausgefüllt wird.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="8c7e0-104">*Dynamische Parameter* sind Parameter eines Cmdlets oder einer Funktion, die nur unter den angegebenen Bedingungen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="8c7e0-105">Die dynamischen Parameter, die in einem Anbieter Hilfethema dokumentiert werden, sind die dynamischen Parameter, die der Anbieter dem Cmdlet oder der Funktion hinzufügt, wenn das Cmdlet oder die Funktion im Anbieter Laufwerk verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="8c7e0-106">Dynamische Parameter können auch in der benutzerdefinierten Cmdlet-Hilfe für einen Anbieter dokumentiert werden.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="8c7e0-107">Wenn Sie sowohl Anbieter Hilfe als auch benutzerdefinierte Cmdlet-Hilfe für einen Anbieter schreiben, fügen Sie die dynamische Parameter Dokumentation in beide Dokumente ein.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span>

<span data-ttu-id="8c7e0-108">Wenn ein Anbieter keine dynamischen Parameter implementiert, enthält das Hilfethema für den Anbieter ein leeres- `DynamicParameters` Element.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-108">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="8c7e0-109">So fügen Sie dynamische Parameter hinzu</span><span class="sxs-lookup"><span data-stu-id="8c7e0-109">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="8c7e0-110">Fügen Sie in der-Datei im- `<AssemblyName>.dll-help.xml` `providerHelp` Element ein- `DynamicParameters` Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-110">In the `<AssemblyName>.dll-help.xml` file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="8c7e0-111">Das `DynamicParameters` -Element sollte nach dem `Tasks` -Element und vor dem-Element angezeigt werden `RelatedLinks` .</span><span class="sxs-lookup"><span data-stu-id="8c7e0-111">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="8c7e0-112">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="8c7e0-112">For example:</span></span>

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

   <span data-ttu-id="8c7e0-113">Wenn der Anbieter keine dynamischen Parameter implementiert, `DynamicParameters` kann das Element leer sein.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-113">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

1. <span data-ttu-id="8c7e0-114">`DynamicParameters`Fügen Sie im-Element für jeden dynamischen Parameter ein- `DynamicParameter` Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-114">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="8c7e0-115">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="8c7e0-115">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

1. <span data-ttu-id="8c7e0-116">`DynamicParameter`Fügen Sie in jedem-Element `Name` ein-und ein- `CmdletSupported` Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-116">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   - <span data-ttu-id="8c7e0-117">Name: gibt den Parameternamen an.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-117">Name - Specifies the parameter name</span></span>
   - <span data-ttu-id="8c7e0-118">Cmdletsupported: gibt die Cmdlets an, in denen der Parameter gültig ist.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-118">CmdletSupported - Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="8c7e0-119">Geben Sie eine durch Trennzeichen getrennte Liste von Cmdlet-Namen ein.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-119">Type a comma-separated list of cmdlet names.</span></span>

   <span data-ttu-id="8c7e0-120">Der folgende XML-Code dokumentiert z `Encoding` . b. den dynamischen Parameter, den der Windows PowerShell-File System-Anbieter den `Add-Content` `Get-Content` `Set-Content` Cmdlets,, hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-120">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

1. <span data-ttu-id="8c7e0-121">Fügen Sie in jedem- `DynamicParameter` Element ein- `Type` Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-121">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="8c7e0-122">Das- `Type` Element ist ein Container für das- `Name` Element, das den .NET-Typ des Werts des dynamischen Parameters enthält.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-122">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="8c7e0-123">Der folgende XML-Code zeigt beispielsweise, dass der .NET-Typ des `Encoding` dynamischen Parameters die [filesystemcmdletproviderencoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) -Enumeration ist.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-123">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

1. <span data-ttu-id="8c7e0-124">Fügen Sie das- `Description` Element hinzu, das eine kurze Beschreibung des dynamischen Parameters enthält.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-124">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="8c7e0-125">Wenn Sie die Beschreibung verfassen, verwenden Sie die Richtlinien, die für alle Cmdlet-Parameter in [Hinzufügen von Parameterinformationen](./how-to-add-parameter-information.md)vorgeschrieben sind.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-125">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="8c7e0-126">Der folgende XML-Code enthält z. b. die Beschreibung des `Encoding` dynamischen Parameters.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-126">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

1. <span data-ttu-id="8c7e0-127">Fügen Sie das `PossibleValues` -Element und seine untergeordneten Elemente hinzu.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-127">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="8c7e0-128">Diese Elemente beschreiben gemeinsame Werte des dynamischen Parameters.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-128">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="8c7e0-129">Dieses Element ist für Enumerationswerte konzipiert.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-129">This element is designed for enumerated values.</span></span> <span data-ttu-id="8c7e0-130">Wenn der dynamische Parameter keinen Wert annimmt, wie z. b. bei einem Switch-Parameter, oder wenn die Werte nicht aufgelistet werden können, fügen Sie ein leeres- `PossibleValues` Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-130">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="8c7e0-131">In der folgenden Tabelle sind das- `PossibleValues` Element und seine untergeordneten Elemente aufgelistet und beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-131">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   - <span data-ttu-id="8c7e0-132">PossibleValues: dieses Element ist ein Container.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-132">PossibleValues - This element is a container.</span></span> <span data-ttu-id="8c7e0-133">Die untergeordneten Elemente werden unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-133">Its child elements are described below.</span></span> <span data-ttu-id="8c7e0-134">Fügen Sie `PossibleValues` jedem Anbieter Hilfethema ein-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-134">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="8c7e0-135">Das Element kann leer sein.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-135">The element can be empty.</span></span>
   - <span data-ttu-id="8c7e0-136">Possiblevalue: dieses Element ist ein Container.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-136">PossibleValue - This element is a container.</span></span> <span data-ttu-id="8c7e0-137">Die untergeordneten Elemente werden unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-137">Its child elements are described below.</span></span> <span data-ttu-id="8c7e0-138">Fügen Sie ein- `PossibleValue` Element für jeden Wert des dynamischen Parameters hinzu.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-138">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>
   - <span data-ttu-id="8c7e0-139">Value: gibt den Wertnamen an.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-139">Value - Specifies the value name.</span></span>
   - <span data-ttu-id="8c7e0-140">Description: dieses Element enthält ein- `Para` Element.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-140">Description - This element contains a `Para` element.</span></span> <span data-ttu-id="8c7e0-141">Der Text im- `Para` Element beschreibt den Wert, der im-Element benannt wird `Value` .</span><span class="sxs-lookup"><span data-stu-id="8c7e0-141">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>

   <span data-ttu-id="8c7e0-142">Der folgende XML-Code zeigt z `PossibleValue` . b. ein Element des `Encoding` dynamischen Parameters.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-142">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="8c7e0-143">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8c7e0-143">Example</span></span>

<span data-ttu-id="8c7e0-144">Das folgende Beispiel zeigt das- `DynamicParameters` Element des `Encoding` dynamischen Parameters.</span><span class="sxs-lookup"><span data-stu-id="8c7e0-144">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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
