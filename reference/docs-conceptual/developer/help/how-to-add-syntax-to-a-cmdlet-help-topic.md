---
title: Hinzufügen einer Syntax zu einem Cmdlet-Hilfethema
ms.date: 09/12/2016
ms.openlocfilehash: 3457341a577b283bf3da5dc010de9bbbb36b78d2
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893049"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>Hinzufügen einer Syntax zu einem Cmdlet-Hilfethema

Bevor Sie beginnen, den XML-Code für das Syntax Diagramm in der Cmdlet-Hilfedatei zu codieren, lesen Sie diesen Abschnitt, um einen Überblick über die Art der Daten zu erhalten, die Sie bereitstellen müssen, wie z. b. die Parameter Attribute und die Art und Weise, wie diese Daten im Syntax Diagramm angezeigt werden.

## <a name="parameter-attributes"></a>Parameterattribute

- Erforderlich
  - Wenn der Wert true ist, muss der Parameter in allen Befehlen angezeigt werden, die den Parametersatz verwenden.
  - Wenn der Wert false ist, ist der Parameter in allen Befehlen, die den Parametersatz verwenden, optional.
- Position
  - Wenn benannt, ist der Parameter Name erforderlich.
  - Wenn der Positionswert ist, ist der Parameter Name optional. Wenn Sie weggelassen wird, muss der Parameterwert an der angegebenen Position im Befehl liegen. Wenn der Wert z. b. Position = "1" ist, muss der Parameterwert der erste oder einzige unbenannte Parameterwert im Befehl sein.
- Pipelineeingabe
  - Wenn true (byvalue), können Sie die Eingabe an den-Parameter übergeben. Die Eingabe wird dem Parameter zugeordnet ("gebunden"), auch wenn der Eigenschaftsname und der Objekttyp nicht dem erwarteten Typ entsprechen.
    Die PowerShell-Parameter Bindungskomponenten versuchen, die Eingabe in den richtigen Typ zu konvertieren, und führen den Befehl nur aus, wenn der Typ nicht konvertiert werden kann. Nur ein Parameter in einem Parametersatz kann nach Wert zugeordnet werden.
  - Wenn true (bypropertyname), können Sie die Eingabe an den-Parameter übergeben. Die Eingabe wird jedoch nur mit dem-Parameter verknüpft, wenn der Parameter Name mit dem Namen einer Eigenschaft des Eingabe Objekts übereinstimmt. Wenn der Parameter Name beispielsweise ist `Path` , werden Objekte, die an das Cmdlet weitergeleitet werden, diesem Parameter nur dann zugeordnet, wenn das Objekt über eine Eigenschaft mit dem Namen Path verfügt.
  - Wenn true (byvalue, bypropertyname), können Sie die Eingabe an den-Parameter übergeben, indem Sie den Eigenschaftsnamen oder den Wert angeben. Nur ein Parameter in einem Parametersatz kann nach Wert zugeordnet werden.
  - Wenn der Wert false ist, können Sie keine Eingaben an diesen Parameter übergeben.
- Platzhalter
  - True gibt an, dass der Text, den der Benutzer für den Parameterwert eingegeben hat, Platzhalter Zeichen enthalten kann.
  - False gibt an, dass der Text, den der Benutzer für den Parameterwert eingegeben hat, keine Platzhalter Zeichen enthalten kann.

### <a name="parameter-value-attributes"></a>Parameter Wert Attribute

- Erforderlich
  - Wenn true, muss der angegebene Wert immer verwendet werden, wenn der-Parameter in einem-Befehl verwendet wird.
  - False gibt an, dass der Parameterwert optional ist. In der Regel ist ein Wert nur optional, wenn er einer von mehreren gültigen Werten für einen Parameter ist, z. b. in einem enumerierten Typ.

Das **erforderliche** -Attribut eines Parameter Werts unterscheidet sich vom **erforderlichen** -Attribut eines-Parameters.

Das erforderliche-Attribut eines-Parameters gibt an, ob der Parameter (und sein Wert) beim Aufrufen des Cmdlets eingeschlossen werden muss. Im Gegensatz dazu wird das erforderliche Attribut eines Parameter Werts nur verwendet, wenn der Parameter im Befehl enthalten ist. Gibt an, ob dieser bestimmte Wert mit dem-Parameter verwendet werden muss.

Normalerweise sind Parameterwerte, die Platzhalter sind, erforderlich, und Parameterwerte, die Literale sind, sind nicht erforderlich, da es sich um einen von mehreren Werten handelt, die mit dem-Parameter verwendet werden können.

### <a name="gathering-syntax-information"></a>Sammeln von Syntax Informationen

1. Beginnen Sie mit dem Cmdlet-Namen.

   ```
   SYNTAX
       Get-Tech
   ```

1. Listet alle Parameter des Cmdlets auf. Geben Sie einen Bindestrich ( `-` ) (ASCII 45) vor jedem Parameternamen ein.
   Trennen Sie die Parameter in Parametersätze (für einige Cmdlets ist möglicherweise nur ein Parameter festgelegt). In diesem Beispiel verfügt das Get-Tech-Cmdlet über zwei Parametersätze.

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   Starten Sie jeden Parametersatz mit dem Namen des Cmdlets.

   Listet den Standardparameter Satz zuerst auf. Der Standardparameter wird durch die Cmdlet-Klasse angegeben.

   Listen Sie für jeden Parametersatz zuerst den eindeutigen Parameter auf, es sei denn, es sind Positions Parameter vorhanden, die zuerst angezeigt werden müssen. Im vorherigen Beispiel handelt es sich bei den Parametern Name und ID um eindeutige Parameter für die beiden Parametersätze (jeder Parametersatz muss über einen Parameter verfügen, der für diesen Parametersatz eindeutig ist). Dies erleichtert es Benutzern, den Parameter zu identifizieren, den Sie für den Parametersatz angeben müssen.

   Listen Sie die Parameter in der Reihenfolge auf, in der Sie im Befehl angezeigt werden sollen. Wenn die Reihenfolge keine Rolle spielt, können Sie verwandte Parameter zusammen auflisten oder die am häufigsten verwendeten Parameter zuerst auflisten.

   Stellen Sie sicher, dass Sie die Parameter "WhatIf" und "Confirm" auflisten, wenn das Cmdlet "Schulter verarbeiten"

   Listen Sie die allgemeinen Parameter (z. b. "Verbose", "Debug" und "ErrorAction") nicht in Ihrem Syntax Diagramm auf. Mit dem- `Get-Help` Cmdlet werden diese Informationen für Sie hinzugefügt, wenn das Hilfethema angezeigt wird.

1. Fügen Sie die Parameterwerte hinzu. In PowerShell werden Parameterwerte durch ihren .NET-Typ dargestellt.
   Allerdings kann der Typname abgekürzt werden, z. b. "String" für System. String.

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   Abkürzen von Typen, solange ihre Bedeutung klar ist, z. b. **Zeichenfolge** für **System. String** und **int** für **System. Int32**.

   Listet alle Werte von Enumerationen auf, wie z. b. den- `-type` Parameter im vorherigen Beispiel, der auf " **Basic** " oder " **Advanced**" festgelegt werden kann.

   Switch-Parameter, wie z `-list` . b. im vorherigen Beispiel, haben keine Werte.

1. Fügen Sie Parameterwerten, bei denen es sich um Platzhalter handelt, zu Parameterwerten, die Literale sind, Spitze Klammern hinzu.

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

1. Schließen Sie optionale Parameter und deren Werte in eckige Klammern ein.

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

1. Schließen Sie optionale Parameternamen (für Positions Parameter) in eckige Klammern ein. Der Name für Parameter, die Positionswerte sind, wie z. b. der Name-Parameter im folgenden Beispiel, muss nicht in den-Befehl eingeschlossen werden.

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

1. Wenn ein Parameterwert mehrere Werte enthalten kann, z. b. eine Liste von Namen im Name-Parameter, fügen Sie ein paar von eckigen Klammern direkt nach dem Parameterwert hinzu.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

1. Wenn der Benutzer eine Auswahl aus Parametern oder Parameterwerten, wie z. b. dem Typparameter, treffen kann, schließen Sie die Optionen in geschweiften Klammern ein, und trennen Sie Sie durch das exklusive Symbol oder (;).

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

1. Wenn für den Parameterwert eine bestimmte Formatierung verwendet werden muss, z. b. Anführungszeichen oder Klammern, wird das Format in der Syntax angezeigt.

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>Codieren des Syntax Diagramm-XML

Der Syntax Knoten des XML-Codes beginnt unmittelbar nach dem Beschreibungs Knoten, der mit dem- `</maml:description>` Tag endet. Informationen zum Sammeln von Daten, die im Syntax Diagramm verwendet werden, finden Sie unter [Sammeln von Syntax Informationen](#gathering-syntax-information).

### <a name="adding-a-syntax-node"></a>Hinzufügen eines Syntax Knotens

Das im Cmdlet-Hilfethema angezeigte Syntax Diagramm wird aus den Daten im Knoten Syntax der XML-Datei generiert. Der Syntax Knoten ist in ein paar eingeschlossen, wenn `<command:syntax>` Tags. Mit jedem Parametersatz des Cmdlets, der in ein Tagpaar eingeschlossen ist `<command:syntaxitem>` . Es gibt keine Beschränkung für die Anzahl der `<command:syntaxitem>` Tags, die Sie hinzufügen können.

Das folgende Beispiel zeigt einen Syntax Knoten, der über Syntax Elementknoten für zwei Parametersätze verfügt.

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>Hinzufügen des Cmdlet-namens zu den Parameter Satz Daten

Jeder Parametersatz des Cmdlets wird in einem Syntax Elementknoten angegeben. Jeder Syntax Elementknoten beginnt mit einem Paar von `<maml:name>` Tags, die den Namen des Cmdlets enthalten.

Das folgende Beispiel schließt einen Syntax Knoten ein, der über Syntax Elementknoten für zwei Parametersätze verfügt.

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

### <a name="adding-parameters"></a>Hinzufügen von Parametern

Jeder Parameter, der dem Knoten Syntax Element hinzugefügt wird, wird in einem Tagpaar angegeben `<command:parameter>` . Sie benötigen `<command:parameter>` für jeden Parameter, der im Parametersatz enthalten ist, ein paar Tags, mit Ausnahme der allgemeinen Parameter, die von PowerShell bereitgestellt werden.

Die Attribute des öffnenden `<command:parameter>` Tags bestimmen, wie der Parameter im Syntax Diagramm angezeigt wird. Weitere Informationen zu Parameter Attributen finden Sie unter [Parameter Attribute](#parameter-attributes).

> [!NOTE]
> Das- `<command:parameter>` Tag unterstützt ein untergeordnetes-Element, `<maml:description>` dessen Inhalt nie angezeigt wird. Die Parameter Beschreibungen werden im Parameter Knoten der XML-Datei angegeben. Um Inkonsistenzen zwischen den Informationen im Syntax Element verheißen und dem Parameter Knoten zu vermeiden, `<maml:description>` lassen Sie das aus (oder lassen Sie es leer.

Das folgende Beispiel schließt einen Syntax Elementknoten für einen Parametersatz mit zwei Parametern ein.

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
