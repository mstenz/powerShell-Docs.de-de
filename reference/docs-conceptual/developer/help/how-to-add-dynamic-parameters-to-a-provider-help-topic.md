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
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Hinzufügen von dynamischen Parametern zu einem Anbieterhilfethema

In diesem Abschnitt wird erläutert, wie der Abschnitt **dynamische Parameter** eines Hilfe Themas für den Anbieter ausgefüllt wird.

*Dynamische Parameter* sind Parameter eines Cmdlets oder einer Funktion, die nur unter den angegebenen Bedingungen verfügbar sind.

Die dynamischen Parameter, die in einem Anbieter Hilfethema dokumentiert werden, sind die dynamischen Parameter, die der Anbieter dem Cmdlet oder der Funktion hinzufügt, wenn das Cmdlet oder die Funktion im Anbieter Laufwerk verwendet wird.

Dynamische Parameter können auch in der benutzerdefinierten Cmdlet-Hilfe für einen Anbieter dokumentiert werden. Wenn Sie sowohl Anbieter Hilfe als auch benutzerdefinierte Cmdlet-Hilfe für einen Anbieter schreiben, fügen Sie die dynamische Parameter Dokumentation in beide Dokumente ein.

Wenn ein Anbieter keine dynamischen Parameter implementiert, enthält das Hilfethema für den Anbieter ein leeres `DynamicParameters`-Element.

### <a name="to-add-dynamic-parameters"></a>So fügen Sie dynamische Parameter hinzu

1. Fügen Sie in der Datei *AssemblyName*. dll-Help. XML innerhalb des `providerHelp`-Elements ein `DynamicParameters`-Element hinzu. Das `DynamicParameters`-Element sollte nach dem `Tasks`-Element und vor dem `RelatedLinks`-Element angezeigt werden.

   Beispiel:

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

   Wenn der Anbieter keine dynamischen Parameter implementiert, kann das `DynamicParameters`-Element leer sein.

2. Fügen Sie im `DynamicParameters`-Element für jeden dynamischen Parameter ein `DynamicParameter`-Element hinzu.

   Beispiel:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. Fügen Sie in jedem `DynamicParameter`-Element ein `Name`-und `CmdletSupported`-Element hinzu.

   |Elementname|Description|
   |------------------|-----------------|
   |Name|Gibt den Parameternamen an.|
   |Cmdletunter stützt|Gibt die Cmdlets an, in denen der Parameter gültig ist. Geben Sie eine durch Trennzeichen getrennte Liste von Cmdlet-Namen ein.|

   Im folgenden XML-Code wird beispielsweise der dynamische Parameter `Encoding` dokumentiert, den der Windows PowerShell-File System-Anbieter den `Add-Content`-, `Get-Content`-, `Set-Content`-Cmdlets hinzufügt.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. Fügen Sie in jedem `DynamicParameter`-Element ein `Type`-Element hinzu. Das `Type`-Element ist ein Container für das `Name`-Element, das den .NET-Typ des Werts des dynamischen Parameters enthält.

   Der folgende XML-Code zeigt beispielsweise, dass der .NET-Typ des dynamischen Parameters `Encoding` die [Microsoft. PowerShell. Commands. filesystemcmdletproviderencoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) -Enumeration ist.

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

5. Fügen Sie das `Description`-Element hinzu, das eine kurze Beschreibung des dynamischen Parameters enthält. Wenn Sie die Beschreibung verfassen, verwenden Sie die Richtlinien, die für alle Cmdlet-Parameter in [Hinzufügen von Parameterinformationen](./how-to-add-parameter-information.md)vorgeschrieben sind.

   Der folgende XML-Code enthält z. b. die Beschreibung des dynamischen Parameters `Encoding`.

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

6. Fügen Sie das `PossibleValues`-Element und seine untergeordneten Elemente hinzu. Diese Elemente beschreiben gemeinsame Werte des dynamischen Parameters. Dieses Element ist für Enumerationswerte konzipiert. Wenn der dynamische Parameter keinen Wert annimmt, wie z. b. den Fall mit einem Switch-Parameter, oder wenn die Werte nicht aufgelistet werden können, fügen Sie ein leeres `PossibleValues`-Element hinzu.

   In der folgenden Tabelle werden das `PossibleValues`-Element und seine untergeordneten Elemente aufgelistet und beschrieben.

   |Elementname|Description|
   |------------------|-----------------|
   |PossibleValues|Dieses Element ist ein Container. Die untergeordneten Elemente werden unten beschrieben. Fügen Sie jedem Anbieter Hilfethema ein `PossibleValues`-Element hinzu. Das Element kann leer sein.|
   |Possiblevalue|Dieses Element ist ein Container. Die untergeordneten Elemente werden unten beschrieben. Fügen Sie ein `PossibleValue`-Element für jeden Wert des dynamischen Parameters hinzu.|
   |Value|Gibt den Wertnamen an.|
   |Description|Dieses Element enthält ein `Para`-Element. Der Text im `Para`-Element beschreibt den Wert, der im `Value`-Element benannt ist.|

   Der folgende XML-Code zeigt z. b. ein `PossibleValue`-Element des dynamischen Parameters `Encoding` an.

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

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt das `DynamicParameters`-Element des dynamischen Parameters `Encoding`.

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