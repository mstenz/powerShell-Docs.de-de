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
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361229"
---
# <a name="how-to-add-parameter-information"></a>Hinzufügen von Parameterinformationen

In diesem Abschnitt wird beschrieben, wie Sie Inhalte hinzufügen, die im Abschnitt Parameters des Cmdlet-Hilfe Themas angezeigt werden. Der Abschnitt Parameters des Hilfe Themas Listet jeden Parameter des Cmdlets auf und stellt eine ausführliche Beschreibung der einzelnen Parameter bereit.

Der Inhalt des Parameters-Abschnitts sollte mit dem Inhalt des Syntax Abschnitts des Hilfe Themas konsistent sein. Der Autor der Hilfe ist dafür verantwortlich, sicherzustellen, dass der Knoten Syntax und Parameter ähnliche XML-Elemente enthalten.

> [!NOTE]
> Eine umfassende Übersicht über eine Hilfedatei erhalten Sie, indem Sie eine der dll-Help. XML-Dateien öffnen, die sich im Windows PowerShell-Installationsverzeichnis befinden. Beispielsweise enthält die Datei Microsoft. PowerShell. Commands. Management. dll-Help. XML Inhalte für mehrere der Windows PowerShell-Cmdlets.

### <a name="to-add-parameters"></a>So fügen Sie Parameter hinzu

1. Öffnen Sie die Cmdlet-Hilfedatei, und suchen Sie den Befehls Knoten für das Cmdlet, das Sie dokumentieren. Wenn Sie ein neues Cmdlet hinzufügen, müssen Sie einen neuen Befehls Knoten erstellen. Die Hilfedatei enthält einen Befehls Knoten für jedes Cmdlet, für das Sie Hilfe Inhalte bereitstellen. Im folgenden finden Sie ein Beispiel für einen leeren Befehls Knoten.

    ```xml
    <command:command>
    </command:command>
    ```

2. Suchen Sie im Befehls Knoten den Beschreibungs Knoten, und fügen Sie wie unten dargestellt einen Parameter Knoten hinzu. Es ist nur ein Parameter Knoten zulässig, der unmittelbar auf den Syntax Knoten folgt.

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. Fügen Sie im Knoten Parameter einen Parameter Knoten für jeden Parameter des Cmdlets hinzu, wie unten gezeigt.

   In diesem Beispiel wird ein Parameter Knoten für drei Parameter hinzugefügt.

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   Da es sich hierbei um dieselben XML-Tags handelt, die im Syntax Knoten verwendet werden, und da die hier angegebenen Parameter mit den Parametern übereinstimmen müssen, die durch den Syntax Knoten angegeben werden, können Sie die Parameter Knoten aus dem Syntax Knoten kopieren und in den Parameter Knoten einfügen. Achten Sie jedoch darauf, nur eine Instanz eines Parameter Knotens zu kopieren, auch wenn der Parameter in mehreren Parameter Sätzen in der Syntax angegeben wird.

4. Legen Sie für jeden Parameter Knoten die Attributwerte fest, die die Merkmale der einzelnen Parameter definieren. Diese Attribute umfassen Folgendes: required, Globin, pipelineinput und Position.

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

5. Fügen Sie für jeden Parameter Knoten den Namen des Parameters hinzu. Im folgenden finden Sie ein Beispiel für den Parameternamen, der dem Parameter Knoten hinzugefügt wird.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. Fügen Sie für jeden Parameter Knoten die Beschreibung des Parameters hinzu. Im folgenden finden Sie ein Beispiel für die Parameter Beschreibung, die dem Parameter-Knoten hinzugefügt wird.

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

7. Fügen Sie für jeden Parameter Knoten den .NET Framework Typ des Parameters hinzu. Der Parametertyp wird zusammen mit dem Parameternamen angezeigt.

   Im folgenden finden Sie ein Beispiel für den Parameter .NET Framework Typ, der dem Parameter Knoten hinzugefügt wird.

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

8. Fügen Sie für jeden Parameter Knoten den Standardwert des Parameters hinzu. Der folgende Satz wird der Parameter Beschreibung hinzugefügt, wenn der Inhalt angezeigt wird: "DefaultValue" ist die Standardeinstellung.

   Im folgenden finden Sie ein Beispiel für den Standardwert des Parameters, der dem Parameter Knoten hinzugefügt wird.

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

9. Fügen Sie für jeden Parameter mit mehreren Werten den Knoten mögliche Werte hinzu.

   Im folgenden finden Sie ein Beispiel für den eines möglichen Values-Knotens, der zwei mögliche Werte für den Parameter definiert.

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

Beachten Sie beim Hinzufügen von Parametern die folgenden Punkte.

- Die Attribute des-Parameters werden nicht in allen Ansichten des Hilfe Themas für das Cmdlet angezeigt. Sie werden jedoch in einer Tabelle nach der Parameter Beschreibung angezeigt, wenn der Benutzer die vollständige Ansicht (Get-Help \<cmdletname >-Full) oder den Parameter (Get-Help \<cmdletname >-Parameter) des Themas anfordert.

- Die Parameter Beschreibung ist einer der wichtigsten Teile eines Cmdlet-Hilfe Themas. Die Beschreibung sollte kurz und gründlich sein. Beachten Sie außerdem, dass Sie, wenn die Parameter Beschreibung zu lang wird, z. b. Wenn zwei Parameter miteinander interagieren, weitere Inhalte im Abschnitt "Hinweise" des Cmdlet-Hilfe Themas hinzufügen können.

  Die Parameter Beschreibung bietet zwei Arten von Informationen.

- Was das Cmdlet tut, wenn der-Parameter verwendet wird.

- Der zulässige Wert für den-Parameter.

- Da die Parameterwerte als .NET Framework Objekte ausgedrückt werden, benötigen die Benutzer mehr Informationen zu diesen Werten als in einer herkömmlichen Befehlszeilen Hilfe. Weisen Sie den Benutzer an, welche Art von Daten der Parameter akzeptieren soll, und fügen Sie Beispiele ein.

Der Standardwert des-Parameters ist der Wert, der verwendet wird, wenn der-Parameter nicht in der Befehlszeile angegeben wird. Beachten Sie, dass der Standardwert optional ist und für einige Parameter, wie z. b. erforderliche Parameter, nicht benötigt wird. Sie sollten jedoch einen Standardwert für die meisten optionalen Parameter angeben.

Der Standardwert unterstützt den Benutzer dabei, die Auswirkungen der Verwendung des-Parameters zu verstehen. Beschreiben Sie den Standardwert sehr spezifisch, z. b. "Aktuelles Verzeichnis" oder "Windows PowerShell-Installationsverzeichnis ($PSHome)", um einen optionalen Pfad zu erhalten. Sie können auch einen Satz schreiben, der den Standard beschreibt, z. b. den folgenden Satz, der für den `PassThru`-Parameter verwendet wird: "Wenn passthru nicht angegeben ist, übergibt das Cmdlet Objekte nicht in der Pipeline."  Außerdem müssen Sie den Begriff "Standardwert" nicht in den Eintrag einschließen, da der Wert dem Feldnamen "**Standardwert**" angezeigt wird.

Der Standardwert des-Parameters wird nicht in allen Ansichten des Hilfe Themas für das Cmdlet angezeigt. Sie wird jedoch in einer Tabelle (zusammen mit den Parameter Attributen) nach der Parameter Beschreibung angezeigt, wenn der Benutzer die vollständige Ansicht (Get-Help \<cmdletname >-Full) oder den Parameter (Get-Help \<cmdletname >-Parameter) des Themas anfordert.

Der folgende XML-Code zeigt ein paar `<dev:defaultValue>` Tags, die dem `<command:parameter>`-Knoten hinzugefügt wurden. Beachten Sie, dass der Standardwert unmittelbar nach dem schließenden `</command:parameterValue>`-Tag (wenn der Parameterwert angegeben ist) oder dem schließenden `</maml:description>`-Tag der Parameter Beschreibung folgt. name.

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

Werte für Enumerationstypen hinzufügen

Wenn der Parameter mehrere Werte oder Werte eines Enumerationstyps enthält, können Sie einen optionalen \<dev: PossibleValues-> Knoten verwenden. Mit diesem Knoten können Sie einen Namen und eine Beschreibung für mehrere Werte angeben.

Beachten Sie, dass die Beschreibungen der aufgelisteten Werte nicht in einer der Standard Hilfe Ansichten angezeigt werden, die vom Cmdlet "`Get-Help`" angezeigt werden, aber andere Help Viewer können diese Inhalte in ihren Ansichten anzeigen.

Der folgende XML-Code zeigt einen `<dev:possibleValues>` Knoten mit zwei angegebenen Werten.

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