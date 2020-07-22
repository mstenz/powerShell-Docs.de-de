---
title: Schreiben von Hilfe für PowerShell-Cmdlets
ms.date: 09/13/2016
ms.openlocfilehash: 4e1070e90cf3ed83c1d97a3b620e00f65d09989e
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893083"
---
# <a name="writing-help-for-powershell-cmdlets"></a>Schreiben von Hilfe für PowerShell-Cmdlets

PowerShell-Cmdlets können nützlich sein, aber wenn in den Hilfe Themen nicht klar erklärt wird, was das Cmdlet tut und wie es verwendet werden kann, wird das Cmdlet möglicherweise nicht verwendet, oder es ist noch schlimmer, dass es die Benutzer beeinträchtigen könnte. Das XML-basierte Cmdlet-Hilfedatei Format erhöht die Konsistenz, aber die großartige Hilfe erfordert viel mehr.

Wenn Sie die Cmdlet-Hilfe noch nie geschrieben haben, überprüfen Sie die folgenden Richtlinien. Das XML-Schema, das zum Erstellen des Cmdlet-Hilfe Themas erforderlich ist, wird im folgenden Abschnitt beschrieben. Beginnen Sie mit [dem Erstellen der Cmdlet-Hilfedatei](./how-to-create-the-cmdlet-help-file.md). Dieses Thema enthält eine Beschreibung der XML-Knoten der obersten Ebene.

## <a name="writing-guidelines-for-cmdlet-help"></a>Schreiben von Richtlinien für die Cmdlet-Hilfe

### <a name="write-well"></a>Gut schreiben

Nothing ersetzt ein gut geschriebenes Thema. Wenn Sie kein professioneller Writer sind, finden Sie einen Writer oder Editor, der Ihnen hilft. Eine weitere Alternative besteht darin, den Hilfetext in Microsoft Word zu kopieren und die Grammatik-und Rechtschreibprüfungen zu verwenden, um Ihre Arbeit zu verbessern.

### <a name="write-simply"></a>Einfaches schreiben

Verwenden Sie einfache Wörter und Ausdrücke. Fachsprache vermeiden. Beachten Sie, dass viele Leser nur mit einem fremdsprachigen Wörterbuch und Ihrem Hilfethema ausgestattet sind.

### <a name="write-consistently"></a>Konsistentes schreiben

Die Hilfe zu verwandten Cmdlets sollte ähnlich sein (z. b. Get-x und Set-x). Verwenden Sie die Standard Beschreibungen für Standardparameter wie " **Force** " und " **Inputobject**". (Kopieren Sie Sie aus der Hilfe für die Core-Cmdlets.) Verwenden Sie die Standardbegriffe. Verwenden Sie z. b. "Parameter", nicht "Argument", und verwenden Sie "Cmdlet" nicht "Command" oder "Command-Let".

### <a name="start-the-synopsis-with-a-verb"></a>Starten der Synchronisierungs mit einem Verb

Das Feld Zusammenfassung informiert den Benutzer über das, was das Cmdlet tut, nicht über dessen Funktionsweise. Verben erstellen eine Task basierte-Anweisung, mit der Benutzer informiert werden, wenn dieses Cmdlet Ihre Anforderungen erfüllt. Verwenden Sie einfache Verben wie "Get", "Create" und "Change". Vermeiden Sie "Set", was vage und ausgefallene Wörter wie "Modify" sein kann.

### <a name="focus-on-objects"></a>Fokus auf Objekte

Die meisten Cmdlets "Get" zeigen etwas an, aber Ihre primäre Funktion ist das Abfangen eines Objekts. Konzentrieren Sie sich in der Hilfe auf das-Objekt, damit die Benutzer verstehen, dass die Standard Anzeige eine von vielen ist, und dass Sie die Methoden und Eigenschaften des Objekts, das Sie für Sie abgerufen haben, auf unterschiedliche Weise verwenden können.

### <a name="write-detailed-descriptions"></a>Ausführliche Beschreibungen schreiben

Listen Sie kurz alle Elemente auf, die das Cmdlet in der ausführlichen Beschreibung ausführen kann. Wenn die Main-Funktion eine Eigenschaft ändern soll, das Cmdlet jedoch alle Eigenschaften ändern kann, Listen Sie diese in der ausführlichen Beschreibung auf.

### <a name="use-conventional-syntax"></a>Konventionelle Syntax verwenden

Verwenden Sie das standardmäßige Backus-Naur-Format, das bei der Windows-und UNIX-Befehlszeilen Hilfe üblich ist.

### <a name="use-microsoft-net-types-for-parameter-values"></a>Verwenden von Microsoft .NET Typen für Parameterwerte

Die Platzhalter für Parameterwerte (in den Syntax-und Parameter Beschreibungen) zeigen die .NET Framework Typen der Objekte an, die der-Parameter akzeptiert. Das PowerShell-Team hat diese Konvention entwickelt, um Benutzern die .NET Framework zu vermitteln.

### <a name="write-complete-parameter-descriptions"></a>Schreiben von kompletten Parameter Beschreibungen

Parameter Beschreibungen müssen Benutzer über zwei Dinge informieren: wie der-Parameter (seine Auswirkung) und was Sie für die Parameterwerte eingeben müssen.

### <a name="write-practical-examples"></a>Praktische Beispiele schreiben

In den Beispielen sollte gezeigt werden, wie alle Parameter verwendet werden, aber es ist wichtig zu veranschaulichen, wie das Cmdlet in realen Aufgaben verwendet wird. Beginnen Sie mit einem einfachen Beispiel, und schreiben Sie immer komplexere Beispiele. Im letzten Beispiel wird gezeigt, wie das Cmdlet in einer Pipeline verwendet wird.

### <a name="use-the-notes-field"></a>Verwenden des Felds "Notizen"

Verwenden Sie das Feld Notizen, um die Konzepte zu erläutern, die Benutzer benötigen, um das Cmdlet zu verstehen. Sie können auch Notizen verwenden, um Benutzern zu helfen, häufige Fehler zu vermeiden. Vermeiden Sie URLs, wenn Sie sich ändern. Geben Sie stattdessen die zu suchenden Nutzungsbedingungen an.

### <a name="test-your-help"></a>Testen der Hilfe

Testen Sie die Hilfe wie beim Testen des Codes. Bitten Sie Freunde und Kollegen, Ihre Hilfe Inhalte zu lesen und Feedback zu geben. Sie können auch Feedback aus Newsgroups anfordern.

## <a name="see-also"></a>Weitere Informationen

 [Erstellen der Cmdlet-Hilfedatei](./how-to-create-the-cmdlet-help-file.md)

 [Hinzufügen von Cmdlet-Namen und -Übersicht zu einem Cmdlet-Hilfethema](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Vorgehensweise beim Hinzufügen der ausführlichen Beschreibung zu einem Cmdlet-Hilfethema](./how-to-add-a-cmdlet-description.md)

 [Hinzufügen einer Syntax zu einem Cmdlet-Hilfethema](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Vorgehensweise beim Hinzufügen von Parametern zu einem Cmdlet-Hilfethema](./how-to-add-parameter-information.md)

 [Vorgehensweise beim Hinzufügen von Eingabetypen zu einem Cmdlet-Hilfethema](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Hinzufügen von Rückgabewerten zu einem Cmdlet-Hilfethema](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Hinzufügen von Anmerkungen zu einem Cmdlet-Hilfethema](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Hinzufügen von Beispielen zu einem Cmdlet-Hilfethema](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Hinzufügen von zugehörigen Verknüpfungen zu einem Cmdlet-Hilfethema](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)
