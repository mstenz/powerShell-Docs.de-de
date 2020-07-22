---
title: Hinzufügen von Parameterinformationen
ms.date: 09/12/2016
ms.openlocfilehash: 15d0194a1d5449c65977703faf245e449d75d176
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893389"
---
# <a name="how-to-add-parameter-information"></a>Hinzufügen von Parameterinformationen

In diesem Abschnitt wird beschrieben, wie Sie Inhalte hinzufügen, die im Abschnitt **Parameters** des Cmdlet-Hilfe Themas angezeigt werden. Der Abschnitt **para** meters des Hilfe Themas Listet jeden Parameter des Cmdlets auf und stellt eine ausführliche Beschreibung der einzelnen Parameter bereit.

Der Inhalt des **Parameters** -Abschnitts sollte mit dem Inhalt des **Syntax** Abschnitts des Hilfe Themas konsistent sein. Der Autor der Hilfe ist dafür verantwortlich, sicherzustellen, dass der Knoten **Syntax** und **Parameter** ähnliche XML-Elemente enthalten.

> [!NOTE]
> Eine umfassende Ansicht einer Hilfedatei erhalten Sie, indem Sie eine der `dll-Help.xml` Dateien im PowerShell-Installationsverzeichnis öffnen. Die `Microsoft.PowerShell.Commands.Management.dll-Help.xml` Datei enthält z. b. Inhalte für mehrere PowerShell-Cmdlets.

### <a name="to-add-parameters"></a>So fügen Sie Parameter hinzu

1. Öffnen Sie die Cmdlet-Hilfedatei, und suchen Sie den Befehls Knoten für das Cmdlet, das Sie dokumentieren. Wenn Sie ein neues Cmdlet hinzufügen, müssen Sie einen neuen Befehls Knoten erstellen. Die Hilfedatei enthält einen Befehls Knoten für jedes Cmdlet, für das Sie Hilfe Inhalte bereitstellen. Im folgenden finden Sie ein Beispiel für einen leeren Befehls Knoten.

    ```xml
    <command:command>
    </command:command>
    ```

1. Suchen Sie im Befehls Knoten den Beschreibungs Knoten, und fügen Sie wie unten dargestellt einen Parameter Knoten hinzu.
   Es ist nur ein Parameter Knoten zulässig, der unmittelbar auf den Syntax Knoten folgt.

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

1. Fügen Sie im Knoten Parameter einen **Parameter** Knoten für jeden Parameter des Cmdlets hinzu, wie unten gezeigt.

   In diesem Beispiel wird ein **Parameter** Knoten für drei Parameter hinzugefügt.

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   Da es sich hierbei um dieselben XML-Tags handelt, die im Syntax Knoten verwendet werden, und da die hier angegebenen Parameter mit den Parametern übereinstimmen müssen, die durch den Syntax Knoten angegeben werden, können Sie die Parameter Knoten aus dem Syntax Knoten kopieren und in den Parameter Knoten einfügen. Achten Sie jedoch darauf, nur eine Instanz eines Parameter Knotens zu kopieren, auch wenn der Parameter in mehreren Parameter Sätzen in der Syntax angegeben wird.

1. Legen Sie für jeden Parameter Knoten die Attributwerte fest, die die Merkmale der einzelnen Parameter definieren. Diese Attribute umfassen Folgendes: required, Globin, pipelineinput und Position.

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

1. Fügen Sie für jeden Parameter Knoten den Namen des Parameters hinzu. Im folgenden finden Sie ein Beispiel für den Parameternamen, der dem Parameter Knoten hinzugefügt wird.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

1. Fügen Sie für jeden **Parameter** Knoten die Beschreibung des Parameters hinzu. Im folgenden finden Sie ein Beispiel für die Parameter Beschreibung, die dem **Parameter** -Knoten hinzugefügt wird.

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

1. Fügen Sie für jeden **Parameter** Knoten den .NET-Typ des Parameters hinzu. Der Parametertyp wird zusammen mit dem Parameternamen angezeigt.

   Im folgenden finden Sie ein Beispiel für den .net-Parametertyp, der dem **Parameter** Knoten hinzugefügt wird.

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

1. Fügen Sie für jeden **Parameter** Knoten den Standardwert des Parameters hinzu. Der folgende Satz wird der Parameter Beschreibung hinzugefügt, wenn der Inhalt angezeigt wird: " **DefaultValue** " ist die Standardeinstellung.

   Im folgenden finden Sie ein Beispiel für den Standardwert des Parameters, der dem **Parameter** Knoten hinzugefügt wird.

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

1. Fügen Sie für jeden Parameter mit mehreren Werten den Knoten mögliche Werte hinzu.

   Im folgenden finden Sie ein Beispiel für den eines möglichen Values-Knotens, der zwei mögliche Werte für den Parameter definiert.

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

Beachten Sie beim Hinzufügen von Parametern die folgenden Punkte.

- Die Attribute des-Parameters werden nicht in allen Ansichten des Hilfe Themas für das Cmdlet angezeigt. Sie werden jedoch in einer Tabelle angezeigt, die der Parameter Beschreibung folgt, wenn der Benutzer die **vollständige** ( `Get-Help <cmdletname> -full` ) oder die **Parameter** `Get-Help <cmdletname> -parameter` Ansicht () des Themas anfordert.

- Die Parameter Beschreibung ist einer der wichtigsten Teile eines Cmdlet-Hilfe Themas. Die Beschreibung sollte kurz und gründlich sein. Beachten Sie außerdem, dass Sie, wenn die Parameter Beschreibung zu lang wird, z. b. Wenn zwei Parameter miteinander interagieren, weitere Inhalte im Abschnitt "Hinweise" des Cmdlet-Hilfe Themas hinzufügen können.

  Die Parameter Beschreibung bietet zwei Arten von Informationen.

- Was das Cmdlet tut, wenn der-Parameter verwendet wird.

- Der zulässige Wert für den-Parameter.

- Da die Parameterwerte als .NET-Objekte ausgedrückt werden, benötigen die Benutzer mehr Informationen zu diesen Werten als in einer herkömmlichen Befehlszeilen Hilfe. Weisen Sie den Benutzer an, welche Art von Daten der Parameter akzeptieren soll, und fügen Sie Beispiele ein.

Der Standardwert des-Parameters ist der Wert, der verwendet wird, wenn der-Parameter nicht in der Befehlszeile angegeben wird. Beachten Sie, dass der Standardwert optional ist und für einige Parameter, wie z. b. erforderliche Parameter, nicht benötigt wird. Sie sollten jedoch einen Standardwert für die meisten optionalen Parameter angeben.

Der Standardwert unterstützt den Benutzer dabei, die Auswirkungen der Verwendung des-Parameters zu verstehen. Beschreiben Sie den Standardwert sehr spezifisch, z. b. das "aktuelle Verzeichnis" oder "PowerShell-Installationsverzeichnis ( `$PSHOME` )", um einen optionalen Pfad zu erhalten. Sie können auch einen Satz schreiben, der den Standard beschreibt, z. b. den folgenden Satz, der für den **passthru** -Parameter verwendet wird: "Wenn passthru nicht angegeben ist, übergibt das Cmdlet Objekte nicht in der Pipeline." Da der Wert im Gegensatz zum **Standardwert**für den Feldnamen angezeigt wird, müssen Sie den Begriff "Standardwert" nicht in den Eintrag einschließen.

Der Standardwert des-Parameters wird nicht in allen Ansichten des Hilfe Themas für das Cmdlet angezeigt. Sie wird jedoch in einer Tabelle (zusammen mit den Parameter Attributen) nach der Parameter Beschreibung angezeigt, wenn der Benutzer die **vollständige** ( `Get-Help <cmdletname> -full` ) oder die **Parameter** `Get-Help
<cmdletname> -parameter` Ansicht () des Themas anfordert.

Der folgende XML-Code zeigt ein dem `<dev:defaultValue>` Knoten hinzugefügtes paar von Tags `<command:parameter>` .
Beachten Sie, dass der Standardwert direkt hinter das `</command:parameterValue>` Endtag (wenn der Parameterwert angegeben ist) oder das `</maml:description>` Endtag der Parameter Beschreibung folgt. name.

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

Wenn der Parameter mehrere Werte oder Werte eines enumerierten Typs aufweist, können Sie einen optionalen \<dev:possibleValues> Knoten verwenden. Mit diesem Knoten können Sie einen Namen und eine Beschreibung für mehrere Werte angeben.

Beachten Sie, dass die Beschreibungen der aufgelisteten Werte nicht in einer der vom Cmdlet angezeigten Standard Hilfe Ansichten angezeigt werden `Get-Help` , aber andere Help Viewer diesen Inhalt möglicherweise in ihren Ansichten anzeigen.

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
