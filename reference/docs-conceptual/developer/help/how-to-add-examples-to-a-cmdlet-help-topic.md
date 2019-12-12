---
title: Vorgehensweise beim Hinzufügen von Beispielen zu einem Cmdlet-Hilfethema | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368109"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>Hinzufügen von Beispielen zu einem Cmdlet-Hilfethema

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Informationen zu Beispielen in der Cmdlet-Hilfe

- Listet alle Parameternamen im Befehl auf, auch wenn die Parameternamen optional sind. Dies unterstützt den Benutzer dabei, den Befehl problemlos zu interpretieren.

- Vermeiden Sie Aliase und partielle Parameternamen, auch wenn Sie in Windows PowerShell® funktionieren.

- Erläutern Sie in der Beispiel Beschreibung das rationale für die Konstruktion des Befehls. Erläutern Sie, warum Sie bestimmte Parameter und Werte ausgewählt haben und wie Sie Variablen verwenden.

- Wenn der Befehl Ausdrücke verwendet, erklären Sie diese ausführlich.

- Wenn der Befehl Eigenschaften und Methoden von Objekten verwendet, insbesondere Eigenschaften, die nicht in der Standard Anzeige angezeigt werden, verwenden Sie das Beispiel als Gelegenheit, um den Benutzer über das Objekt zu informieren.

## <a name="help-views-that-display-examples"></a>Hilfe Ansichten, in denen Beispiele angezeigt werden

Beispiele werden nur in den ausführlichen und vollständigen Ansichten der Cmdlet-Hilfe angezeigt.

## <a name="adding-an-examples-node"></a>Hinzufügen eines Knotens für Beispiele

Der folgende XML-Code zeigt, wie ein Beispiele-Knoten hinzugefügt wird, der einen einzelnen Beispiel Knoten enthält. Fügen Sie zusätzliche Beispiel Knoten für die einzelnen Beispiele hinzu, die Sie in das Thema einschließen möchten.

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>Hinzufügen eines Beispiel Titels

Der folgende XML-Code zeigt, wie Sie einen Titel für das Beispiel hinzufügen. Der Titel wird verwendet, um das Beispiel von anderen Beispielen zu unterscheiden. Windows PowerShell® verwendet einen Standard Header, der eine sequenzielle Beispiel Nummer enthält.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>Hinzufügen vorheriger Zeichen

Der folgende XML-Code zeigt, wie Sie Zeichen hinzufügen, z. b. die Windows PowerShell-Eingabeaufforderung, die unmittelbar vor dem Beispiel Befehl (ohne dazwischen liegende Leerzeichen) angezeigt werden. Windows PowerShell® verwendet die Windows PowerShell-Eingabeaufforderung: c:\ps >.

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

Der folgende XML-Code zeigt, wie eine Beschreibung für das Beispiel hinzugefügt wird. Windows PowerShell® verwendet einen einzelnen Satz \<MAML: para > Tags für die Beschreibung, obwohl mehrere \<MAML: para > Tags verwendet werden können.

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

Der folgende XML-Code zeigt, wie die Ausgabe des Befehls hinzugefügt wird. Die Befehls Ergebnisinformationen sind optional, aber in einigen Fällen ist es hilfreich, die Auswirkungen der Verwendung bestimmter Parameter zu veranschaulichen. Windows PowerShell® verwendet zwei Sätze von leeren \<MAML: para >-Tags, um die Befehlsausgabe des Befehls zu trennen.

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