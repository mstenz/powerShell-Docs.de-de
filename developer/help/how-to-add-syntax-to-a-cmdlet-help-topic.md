---
title: Hinzufügen von Syntax zu einem Cmdlet-Hilfethemas | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 2e9dbc9ff8f9507f2008cd6e114ba6fec36b10bf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054610"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>Hinzufügen einer Syntax zu einem Cmdlet-Hilfethema

- [Parameterattribute](#Parameter-Attributes)

- [Parameterattribute-Wert](#Parameter-Value-Attributes)

- [Informationen über die Syntax werden ermittelt.](#Gathering-Syntax-Information)

- [Das Syntaxdiagramm XML-Codierung](#Coding-the-Syntax-Diagram-XML)

## <a name="things-to-know-about-the-syntax-diagram-in-cmdlet-help"></a>Wissenswerte Fakten über das Syntaxdiagramm in der Cmdlet-Hilfe

Lesen Sie diesen Abschnitt rufen Sie ein klares Bild von der Art der Daten, die Sie bereitstellen müssen, z. B. die Parameterattribute und wie diese Daten in das Syntaxdiagramm angezeigt werden, bevor Sie beginnen, den XML-Code für das Syntaxdiagramm in der Cmdlet-Hilfedatei zu codieren...

### <a name="parameter-attributes"></a>Parameterattribute

- Erforderlich

  - Bei "true", muss der Parameter in allen Befehlen angezeigt, die den Parametersatz verwenden.

  - Wenn "false" ist der Parameter optional in allen Befehlen, die den Parametersatz verwenden.

- Position

  - Der Parametername ist erforderlich, wenn mit dem Namen.

  - Wenn Sie mit Feldern fester Breite, ist der Name des Parameters optional. Wenn sie weggelassen wird, muss der Wert des Parameters in der angegebenen Position im Befehl sein. Z. B. wenn der Wert Position = "1", der Wert des Parameters muss die erste oder einzige unbenannte Parameterwert im Befehl.

- Pipeline-Eingabe

  - Bei "true" (ByValue), können Sie Eingabe für den Parameter übergeben. Die Eingabe ist verknüpft mit ("gebunden an") der Parameter, auch wenn die Eigenschaftennamen und den Objekttyp nicht dem erwarteten Typ überein. Die Windows PowerShell? Parameter Bindung von Komponenten sollten Sie die Eingabe in den richtigen Typ zu konvertieren und den Befehl fehl, nur, wenn der Typ kann nicht konvertiert werden. Nur ein Parameter in einem Parametersatz kann als Wert zugeordnet werden.

  - Bei "true" (ByPropertyName), können Sie Eingabe für den Parameter übergeben. Allerdings ist die Eingabe mit dem Parameter verknüpft nur, wenn der Name des Parameters auf den Namen einer Eigenschaft des Eingabeobjekts entspricht. Wenn der Parametername ist z. B. `Path`, nur, wenn das Objekt eine Eigenschaft namens Pfad hat, werden Objekte, die über die Pipeline an das Cmdlet diesen Parameter zugeordnet.

  - Wenn "true" (ByValue, ByPropertyName), Sie können die Eingabe für den Parameter übergeben, entweder durch den Namen oder Wert. Nur ein Parameter in einem Parametersatz kann als Wert zugeordnet werden.

  - False gibt an, können keine Sie Eingaben für diesen Parameter übergeben.

- Verwendung von Platzhaltern

  - Bei "true", kann der Text, dass der Benutzer, für den Parameterwert eingibt Platzhalterzeichen enthalten.

  - Wenn "false" kann nicht der Text an, dass der Benutzer, für den Parameterwert eingibt Platzhalterzeichen enthalten.

### <a name="parameter-value-attributes"></a>Parameterattribute-Wert

- Erforderlich

  - Bei "true", muss der angegebene Wert verwendet werden, wenn den Parameter in einem Befehl verwenden.

  - Wenn "false" ist der Wert des Parameters optional. In der Regel ist ein Wert optional, nur, wenn es mehrere gültige Werte für einen Parameter, wie z. B. ein enumerierter Typ ist.

Das erforderliche Attribut eines Parameterwerts unterscheidet sich von das erforderliche Attribut eines Parameters.

Das required-Attribut eines Parameters gibt an, ob der Parameter (und sein Wert) eingeschlossen werden müssen, mit dem-Cmdlet aufrufen. Im Gegensatz dazu wird das erforderliche Attribut eines Parameterwerts verwendet, nur, wenn der Parameter im Befehl enthalten ist. Er gibt an, ob es sich bei diesen bestimmte Wert mit dem Parameter verwendet werden muss.

Klicken Sie in der Regel Parameterwerte, die Platzhalter sind erforderlich, und Parameterwerte Literale sind nicht erforderlich, da sie einen der folgenden Werte sind, die mit dem Parameter verwendet werden kann.

### <a name="gathering-syntax-information"></a>Informationen über die Syntax werden ermittelt.

1. Beginnen Sie mit den Cmdlet-Namen.

   ```
   SYNTAX
       Get-Tech
   ```

2. Listen Sie alle Parameter des Cmdlets. Geben Sie einen Bindestrich (auch bekannt als "Dash" oder "Minuszeichen (-)" (ASCII-45) vor jedem Parameternamen. Trennen Sie die Parameter in Parametersätze (einige Cmdlets kann nur ein Parameter festgelegt haben). In diesem Beispiel das Get-Tech-Cmdlet verfügt über zwei Parametersätze.

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   Starten Sie jeden Parameter mit dem cmdletnamen festgelegt.

   Listen Sie den Standardparameter, legen Sie zuerst fest auf. Der Standardparameter wird von der Cmdlet-Klasse angegeben.

   Listen Sie für jeden Parameter als eindeutige Parameter zuerst, es sei denn, es sind Positionsparameter, die zuerst angezeigt werden müssen. Im vorherigen Beispiel werden die Namen und ID-Parameter eindeutige Parameter für die beiden Parameter (jeder Parametersatz müssen einen Parameter, der auf die jeweiligen Parameter eindeutig ist). Dies erleichtert es Benutzern, zu identifizieren, welche Parameter, die sie benötigen, geben Sie für den Parameter festgelegt.

   Listet die Parameter in der Reihenfolge, die sie im Befehl angezeigt werden sollen. Wenn die Reihenfolge keine Rolle spielt, Listen Sie die entsprechenden Parameter zusammen oder Listen Sie zuerst die am häufigsten verwendeten Parameter.

   Achten Sie darauf, dass die WhatIf und Confirm-Parameter aufgelistet, wenn das Cmdlet ShouldProcess unterstützt.

   Listen Sie die allgemeinen Parameter (z. B. "Verbose", "Debug" und "ErrorAction") in Ihrem Syntaxdiagramm. Die `Get-Help` Cmdlet fügt diese Informationen für Sie hinzu, wenn sie das Hilfethema angezeigt wird.

3. Fügen Sie die Parameterwerte hinzu. In Windows PowerShell?, Parameterwerte werden anhand ihres Typs .NET dargestellt. Allerdings kann der Typname abgekürzt werden, z. B. "String" für System.String.

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   Abkürzen Sie-Typen, solange ihre Bedeutung klar, wie z. B. "String" für System.String und "Int" für System. Int32 ist.

   Liste aller Werte von Enumerationen, z. B. der - Typparameter in der im vorherigen Beispiel, das "basic" oder "advanced" festgelegt werden kann.

   Switch-Parameter, z. B. - Liste im vorherigen Beispiel, die keinen Wert.

4. Fügen Sie Parameterwerte, Platzhalter im Vergleich zu den Parameterwerten, die Literale sind spitzen Klammern hinzu.

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. Schließen Sie optionale Parameter und deren Werte in eckige Klammern ein.

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. Schließen Sie optionale Parameter-Namen (für Positionsparameter) in eckige Klammern ein. Der Name für den Parameter, die mit Feldern fester Breite, z. B. den Name-Parameter im folgenden Beispiel sind keine im Befehl enthalten sein.

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. Fügen Sie ein paar eckige Klammern direkt nach der Wert des Parameters hinzu, wenn ein Parameterwert z. B. eine Liste von Namen in den Name-Parameter mehrere Werte enthalten kann.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. Wenn der Benutzer Parameter oder Parameterwerte auswählen kann, schließen Sie die Optionen wie des Typparameters in geschweiften Klammern einfügen, und trennen Sie diese durch die exklusive OR-symbol(;).

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. Wenn der Wert des Parameters bestimmte Formatierung verwenden muss, z. B. Anführungszeichen oder Klammern, zeigen Sie das Format, in der Syntax.

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>Das Syntaxdiagramm XML-Codierung

Der syntaxknoten des XML-beginnt sofort nach der Beschreibung-Knoten, die mit endet die \</maml:description > Tag. Informationen zum Erfassen der Daten, die im Syntax verwendet, finden Sie unter [Sammeln von Informationen über die Syntax](#Gathering-Syntax-Information).

### <a name="adding-a-syntax-node"></a>Hinzufügen eines Syntaxknotens

Das Syntaxdiagramm, die in der Cmdlet-Hilfethemas angezeigt wird aus den Daten im Knoten "Syntax" von der XML-Code generiert. Der syntaxknoten wird in ein paar eingeschlossen, wenn \<Befehlssyntax: > Tags. Mit jeder Parametersatz des-Cmdlets in einem Paar von eingeschlossen \<-Befehl: Syntaxitem > Tags. Es gibt keine Beschränkung der Anzahl der \<-Befehl: Syntaxitem >-Tags, die Sie hinzufügen können.

Das folgende Beispiel zeigt einen syntaxknoten, der Syntax-Element-Knoten für zwei Parametersätze aufweist.

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>Hinzufügen von Cmdlet-Namen für den Parameter festlegen, dass Daten

Jeder Parametersatz, der dem-Cmdlet wird in einen syntaxknoten für das Element angegeben. Jedes Element syntaxknoten beginnt mit einem Paar von \<Maml:name >-Tags, die den Namen des Cmdlets enthalten.

Das folgende Beispiel enthält einen syntaxknoten, der Syntax-Element-Knoten für zwei Parametersätze aufweist.

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

Jeder Parameter der syntaxknoten für das Element hinzugefügt wird angegeben, in ein Paar \<Befehlsparameter: > Tags. Sie benötigen ein Paar von \<Befehlsparameter: >-Tags für jeden Parameter in den Parametersatz, mit Ausnahme von der allgemeinen Parameter, die von Windows PowerShell bereitgestellt werden.

Die Attribute des das öffnendes \<Befehlsparameter: > Tag zu ermitteln, wie der Parameter in der Syntaxdiagramm wird angezeigt. Informationen zu Attributen der Parameter finden Sie unter [Parameterattribute](#Parameter-Attributes).

> [!NOTE]
> Die \<Befehlsparameter: > Tag unterstützt ein untergeordnetes Element \<Maml:description >, dessen Inhalt wird nicht angezeigt. Die Beschreibung der Parameter werden im Knoten "Parameter" des XML-angegeben. Bodes, die Informationen in der Syntaxelement auf Inkonsistenzen zu vermeiden und die Parameterknoten, und lassen Sie die (\<Maml:description > oder leer bleiben.

Das folgende Beispiel enthält einen syntaxknoten-Element für einen Parameter mit zwei Parametern festgelegt.

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
