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
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Hinzufügen von dynamischen Parametern zu einem Anbieterhilfethema

In diesem Abschnitt wird erläutert, wie zum Auffüllen der **dynamische Parameter** Abschnitt eines Hilfethemas für den Anbieter.

*Dynamische Parameter* sind Parametern eines Cmdlets oder Funktion, die verfügbar sind, nur unter angegebenen Bedingungen.

Die dynamischen Parameter, die in einem Hilfethema Anbieter dokumentiert sind, sind die dynamischen Parameter, die der Anbieter das-Cmdlet oder einer Funktion hinzufügt, wenn das Cmdlet oder eine Funktion in einem Laufwerk für den Anbieter verwendet wird.

Dynamische Parameter können auch in benutzerdefinierte Cmdlet-Hilfe für einen Anbieter dokumentiert werden. Wenn sowohl Hilfe durch Anbieter als auch benutzerdefinierte Cmdlet-Hilfe für einen Anbieter schreiben, werden enthalten Sie die dynamischen Parameter-Dokumentation in beiden Dokumenten. Weitere Informationen über benutzerdefinierte Cmdlet-Hilfe finden Sie unter [Schreiben von Windows PowerShell benutzerdefinierte Cmdlet-Hilfe für Anbieter](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).

Wenn ein Anbieter keine dynamischen Parameter implementiert, enthält das Thema Anbieter eine leere `DynamicParameters` Element.

### <a name="to-add-dynamic-parameters"></a>Dynamische Parameter hinzufügen

1. In der *AssemblyName*help.xml-DLL-Datei, in der `providerHelp` -Element, Hinzufügen einer `DynamicParameters` Element. Die `DynamicParameters` Element sollte angezeigt werden, nachdem die `Tasks` Element und vor der `RelatedLinks` Element.

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

   Wenn der Anbieter keine dynamischen Parameter, implementiert die `DynamicParameters` Element kann leer sein.

2. In der `DynamicParameters` -Element, für jeden dynamischen Parameter Hinzufügen einer `DynamicParameter` Element.

   Beispiel:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. In den einzelnen `DynamicParameter` -Element, Hinzufügen einer `Name` und `CmdletSupported` Element.

   |Elementname|Beschreibung|
   |------------------|-----------------|
   |Name|Gibt den Namen des Parameters an.|
   |CmdletSupported|Gibt die Cmdlets, die in denen der Parameter gültig ist. Geben Sie eine durch Trennzeichen getrennte Liste von Cmdlet-Namen ein.|

   Z. B. den folgenden XML-Dokumenten die `Encoding` dynamischer Parameter, die der Windows PowerShell-FileSystem-Anbieter hinzufügt der `Add-Content`, `Get-Content`, `Set-Content` Cmdlets.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. In den einzelnen `DynamicParameter` -Element, Hinzufügen einer `Type` Element. Die `Type` Element ist ein Container für die `Name` Element, das den Typ .NET den Wert, der den dynamischen Parameter enthält.

   Z. B. das folgende XML zeigt, die den .NET-Typ, der die `Encoding` dynamischer Parameter ist der [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) Enumeration.

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

5. Hinzufügen der `Description` -Element, das eine kurze Beschreibung der dynamische Parameter enthält. Beim Erstellen der Beschreibung verwenden Sie die Richtlinien, die für alle cmdletparameter im vorgeschriebenen [wie Hinzufügen von Parameterinformationen](./how-to-add-parameter-information.md).

   Das folgende XML enthält beispielsweise die Beschreibung des der `Encoding` dynamischer Parameter.

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

6. Hinzufügen der `PossibleValues` -Element und seine untergeordneten Elemente. Zusammen beschreiben diese Elemente die Werte von den dynamischen Parameter. Dieses Element dient zur aufgezählte Werte. Wenn der dynamische Parameter nicht über einen Wert akzeptiert, wie z. B. bei einer Switch-Parameter der Fall ist, oder die Werte können nicht aufgezählt werden, fügen Sie eine leere `PossibleValues` Element.

   In der folgende Tabelle aufgelistet und beschrieben die `PossibleValues` -Element und seine untergeordneten Elemente.

   |Elementname|Beschreibung|
   |------------------|-----------------|
   |PossibleValues|Dieses Element ist ein Container. Die untergeordneten Elemente werden nachfolgend beschrieben. Fügen Sie eine `PossibleValues` Element jedes Hilfethemas für den Anbieter. Das Element kann leer sein.|
   |PossibleValue|Dieses Element ist ein Container. Die untergeordneten Elemente werden nachfolgend beschrieben. Fügen Sie eine `PossibleValue` -Element für jeden Wert von den dynamischen Parameter.|
   |Wert|Gibt den Namen des Werts an.|
   |Beschreibung|Dieses Element enthält eine `Para` Element. Der Text in die `Para` -Element beschreibt den Wert mit dem Namen in der `Value` Element.|

   Das folgende XML zeigt beispielsweise eine `PossibleValue` Element der `Encoding` dynamischer Parameter.

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

Das folgende Beispiel zeigt die `DynamicParameters` Element der `Encoding` dynamischer Parameter.

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