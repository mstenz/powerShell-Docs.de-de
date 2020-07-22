---
title: Hinzufügen von Beispielen zu einem Cmdlet-Hilfethema
ms.date: 09/12/2016
ms.openlocfilehash: 33a1726f9d52b5a368d5df7962cc17ba9c45246a
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893440"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>Hinzufügen von Beispielen zu einem Cmdlet-Hilfethema

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Informationen zu Beispielen in der Cmdlet-Hilfe

- Listet alle Parameternamen im Befehl auf, auch wenn die Parameternamen optional sind. Dies unterstützt den Benutzer dabei, den Befehl problemlos zu interpretieren.

- Vermeiden Sie Aliase und partielle Parameternamen, auch wenn Sie in PowerShell funktionieren.

- Erläutern Sie in der Beispiel Beschreibung das rationale für die Konstruktion des Befehls. Erläutern Sie, warum Sie bestimmte Parameter und Werte ausgewählt haben und wie Sie Variablen verwenden.

- Wenn der Befehl Ausdrücke verwendet, erklären Sie diese ausführlich.

- Wenn der Befehl Eigenschaften und Methoden von Objekten verwendet, insbesondere Eigenschaften, die nicht in der Standard Anzeige angezeigt werden, verwenden Sie das Beispiel als Gelegenheit, um den Benutzer über das Objekt zu informieren.

## <a name="help-views-that-display-examples"></a>Hilfe Ansichten, in denen Beispiele angezeigt werden

Beispiele werden nur in den ausführlichen und vollständigen Ansichten der Cmdlet-Hilfe angezeigt.

## <a name="adding-an-examples-node"></a>Hinzufügen eines Knotens für Beispiele

Der folgende XML-Code zeigt, wie ein **Beispiele** -Knoten hinzugefügt wird, der einen einzelnen **Beispiel** Knoten enthält. Fügen Sie zusätzliche Beispiel Knoten für die einzelnen Beispiele hinzu, die Sie in das Thema einschließen möchten.

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>Hinzufügen eines Beispiel Titels

Der folgende XML-Code zeigt, wie Sie einen **Titel** für das Beispiel hinzufügen. Der **Titel** wird verwendet, um das Beispiel von anderen Beispielen zu unterscheiden. PowerShell verwendet einen Standard Header, der eine sequenzielle Beispiel Zahl enthält.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>Hinzufügen vorheriger Zeichen

Der folgende XML-Code zeigt, wie Sie Zeichen hinzufügen, z. b. die Windows PowerShell-Eingabeaufforderung, die unmittelbar vor dem Beispiel Befehl (ohne dazwischen liegende Leerzeichen) angezeigt werden. PowerShell verwendet die Windows PowerShell-Eingabeaufforderung: `C:\PS>` .

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a>Hinzufügen des Befehls

Der folgende XML-Code zeigt, wie der tatsächliche Befehl des Beispiels hinzugefügt wird. Wenn Sie den Befehl hinzufügen, geben Sie den vollständigen Namen (keinen Alias verwenden) von Cmdlets und Parametern ein. Verwenden Sie nach Möglichkeit auch Kleinbuchstaben.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a>Hinzufügen einer Beschreibung

Der folgende XML-Code zeigt, wie eine Beschreibung für das Beispiel hinzugefügt wird. PowerShell verwendet einen einzelnen Satz von `<maml:para>` Tags für die Beschreibung, auch wenn mehrere `<maml:para>` Tags verwendet werden können.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a>Hinzufügen einer Beispielausgabe

Der folgende XML-Code zeigt, wie die Ausgabe des Befehls hinzugefügt wird. Die Befehls Ergebnisinformationen sind optional, aber in einigen Fällen ist es hilfreich, die Auswirkungen der Verwendung bestimmter Parameter zu veranschaulichen.
PowerShell verwendet zwei Sätze von leeren `<maml:para>` Tags, um die Befehlsausgabe des Befehls zu trennen.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```
