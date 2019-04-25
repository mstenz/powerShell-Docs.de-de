---
title: 'Gewusst wie: Hinzufügen von Informationen zu den Parametern | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083364"
---
# <a name="how-to-add-parameter-information"></a>Hinzufügen von Parameterinformationen

Dieser Abschnitt beschreibt, wie Sie Inhalte hinzufügen, die im Abschnitt "PARAMETERS" von der Cmdlet-Hilfethemas angezeigt wird. Der Parameterabschnitt des Hilfethemas enthält alle Parameter des Cmdlets und enthält eine ausführliche Beschreibung der einzelnen Parameter.

Der Inhalt von den Abschnitt "PARAMETERS" sollte mit dem Inhalt der im Abschnitt "SYNTAX" des Hilfethemas entsprechen. Es ist die Verantwortung für den Autor der Hilfe, um sicherzustellen, dass sowohl die Syntax und Parameter-Knoten wie XML-Elemente enthalten.

> [!NOTE]
> Eine vollständige Übersicht der eine Hilfedatei öffnen eine der Dll-Help.xml Dateien im Installationsverzeichnis von Windows PowerShell gefunden. Beispielsweise enthält die Microsoft.PowerShell.Commands.Management.dll-Help.xml-Datei Inhalte für eine Reihe von Windows PowerShell-Cmdlets.

### <a name="to-add-parameters"></a>Hinzufügen von Parametern

1. Öffnen Sie die Cmdlet-Hilfedatei, und suchen Sie den befehlsknoten für das Cmdlet aus, das Sie dokumentieren. Wenn Sie ein neues Cmdlet hinzufügen möchten, das Sie einen neuen befehlsknoten zu erstellen müssen. Die Hilfedatei enthält einen befehlsknoten, für die einzelnen Cmdlets, die Sie Hilfeinhalte zu sorgen. Hier ist ein Beispiel für einen leeren befehlsknoten.

    ```xml
    <command:command>
    </command:command>
    ```

2. Klicken Sie im befehlsknoten suchen Sie den Knoten für die Beschreibung, und fügen Sie einen Parameterknoten, wie unten dargestellt. Knoten der einzige Parameter zulässig ist und sie sollten sofort den syntaxknoten befolgen.

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. Fügen Sie in den Knoten Parameter einen Parameterknoten für jeden Parameter des Cmdlets, wie unten dargestellt.

   In diesem Beispiel wird ein Parameterknoten für drei Parameter hinzugefügt.

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   Da diese die gleiche XML-Tags, die in den syntaxknoten verwendet werden sind, und, da die Parameter hier angegeben, muss den Parametern, die gemäß des syntaxknotens entsprechen, können Sie kopieren die Parameter-Knoten aus dem syntaxknoten und fügen Sie sie in den Knoten Parameter. Achten Sie jedoch nur eine Instanz eines Parameter-Knotens kopiert, auch wenn der Parameter angegeben wird, in mehrere Parameter legt fest, in der Syntax.

4. Legen Sie für jeden Knoten Parameter die Attributwerte, die die Merkmale der einzelnen Parameter zu definieren. Diese Attribute umfassen Folgendes: Verwendung von Platzhaltern, Pipelineinput und eine Position erforderlich.

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

5. Fügen Sie für jeden Knoten Parameter den Namen des Parameters ein. Hier ist ein Beispiel für den Namen des Parameters auf den Knoten Parameter hinzugefügt.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. Fügen Sie für jeden Knoten Parameter die Beschreibung des Parameters ein. Hier ist ein Beispiel für die Beschreibung des Parameters auf den Knoten Parameter hinzugefügt.

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

7. Fügen Sie für jeden Knoten Parameter die .NET Framework-Typ des Parameters ein. Der Parametertyp wird zusammen mit den Namen des Parameters angezeigt.

   Hier ist ein Beispiel für den .NET Framework-Parametertyp, die auf den Knoten Parameter hinzugefügt.

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

8. Fügen Sie für jeden Knoten Parameter den Standardwert des Parameters ein. Der folgende Satz wird die parameterbeschreibung hinzugefügt, wenn der Inhalt angezeigt wird: "DefaultValue" ist die Standardeinstellung.

   Hier ist ein Beispiel für den Standardwert des Parameters auf den Knoten Parameter hinzugefügt wird.

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

9. Fügen Sie einen Knoten möglichen Werte für jeden Parameter, die mehrere Werte enthält, hinzu.

   Hier ist ein Beispiel für die eines Knotens möglichen Werte, der zwei mögliche Werte für den Parameter definiert.

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

Hier sind einige wichtige Aspekte beim Hinzufügen von Parametern aus.

- Die Attribute des Parameters werden nicht in allen Ansichten des Cmdlet-Hilfethemas angezeigt. Allerdings werden sie in einer Tabelle, die nach der Beschreibung des Parameters, wenn der Benutzer gefragt, für das vollständige werden angezeigt (Get-Help \<%CmdletName >-full) oder einen Parameter (Get-Help \<%CmdletName >-Parameter) Ansicht des Themas.

- Die Beschreibung des Parameters ist einer der wichtigsten Teile eines Cmdlet-Hilfethemas. Die Beschreibung sollte es sich um kurze sowie umfassende sein. Beachten Sie außerdem, wenn die Beschreibung des Parameters zu lang ist ist, z. B. wenn die beiden Parameter miteinander interagieren, können Sie weitere Inhalte im Abschnitt "Hinweise" des Cmdlet-Hilfethemas hinzufügen.

  Die parameterbeschreibung bietet zwei Arten von Informationen.

- Was das Cmdlet durchführt, wenn der Parameter verwendet wird.

- Welche ein zulässiger Wert für den Parameter ist.

- Da die Werte der Parameter als .NET Framework-Objekten ausgedrückt werden, benötigen Benutzer Weitere Informationen zu diesen Werten in einer herkömmlichen Befehlszeilenhilfe nutzen. Dem Benutzer mitgeteilt, welche Art von Daten, die der Parameter akzeptiert werden sollen, und Beispiele enthalten.

Der Standardwert des Parameters ist der Wert, der verwendet wird, wenn der Parameter in der Befehlszeile nicht angegeben ist. Beachten Sie, dass der Standardwert optional ist und wird für einige Parameter, z. B. erforderlichen Parameter nicht benötigt. Allerdings sollten Sie einen Standardwert für die meisten optionale Parameter angeben.

Der Standardwert der hilft Benutzern dabei, die Auswirkungen der nicht mit dem Parameter zu ermitteln. Beschrieben Sie den Standardwert wird ganz spezifisch, wie z. B. "Current Directory" oder "Windows PowerShell Installationsverzeichnis ($pshome)" für einen optionalen Pfad. Sie können auch einen Satz, der beschreibt, den Standardwert, wie z. B. den folgenden Satz, der zum Schreiben der `PassThru` Parameter: "Wenn PassThru nicht angegeben ist, wird das Cmdlet keine Objekte über die Pipeline übergeben."  Darüber hinaus, da der Wert, gegenüber der Name des Felds angezeigt wird "**Standardwert**", Sie müssen nicht den Begriff "Default Value" im Eintrag enthalten.

Der Standardwert des Parameters wird nicht in allen Ansichten des Cmdlet-Hilfethemas angezeigt. Es wird jedoch angezeigt, in einer Tabelle (zusammen mit dem Parameterattribute), befolgen die Beschreibung des Parameters, wenn der Benutzer gefragt, für das vollständige werden (Get-Help \<%CmdletName >-full) oder einen Parameter (Get-Help \<%CmdletName >-Parameter) anzeigen im Thema.

Das folgende XML zeigt ein Paar von `<dev:defaultValue>` Tags hinzugefügt wurden, um die `<command:parameter>` Knoten. Beachten Sie, die der Standardwert unmittelbar hinter dem schließenden folgt `</command:parameterValue>` Tag (wenn der Wert des Parameters angegeben ist) oder dem schließenden `</maml:description>` Tag, der die Beschreibung des Parameters. Der Name.

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

Fügen Sie Werte für enumerierte Typen hinzu.

Wenn der Parameter mehrere Werte oder Werte, der ein enumerierter Typ aufweist, können Sie eine optionale \<Dev:possibleValues > Knoten. Dieser Knoten können Sie einen Namen und eine Beschreibung für mehrere Werte angeben.

Beachten Sie, dass die Beschreibungen der aufgelisteten Werte nicht in Standard-angezeigt, indem Hilfeansichten erscheinen die `Get-Help` Cmdlet, aber andere Help Viewer können dieser Inhalt in ihren Sichten anzuzeigen.

Das folgende XML zeigt ein `<dev:possibleValues>` Knoten mit zwei angegebenen Werten.

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