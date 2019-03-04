---
title: Schreiben von Hilfe für PowerShell-Cmdlets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857856"
---
# <a name="writing-help-for-powershell-cmdlets"></a>Schreiben von Hilfe für PowerShell-Cmdlets

PowerShell-Cmdlets kann nützlich sein, aber es sei denn, Ihre Hilfethemen eindeutig erläutern, was das Cmdlet durchführt und wie es verwendet, mit dem-Cmdlet kann nicht verwendet oder, schlimmer noch, kann er Benutzer frustrierend sein.
Das XML-basierten Cmdlet-Hilfe-Dateiformat verbessert die Konsistenz, aber große Hilfe erfordert viel mehr.

Wenn Sie Hilfe zu Cmdlets nie geschrieben haben, überprüfen Sie die folgenden Richtlinien.
Das XML-Schema erforderlich, um die Cmdlet-Hilfethemas zu erstellen, wird im folgenden Abschnitt beschrieben.
Beginnen Sie mit [erstellen die Cmdlet-Hilfedatei](./how-to-create-the-cmdlet-help-file.md).
Dieses Thema enthält eine Beschreibung der XML-Knoten der obersten Ebene.

## <a name="writing-guidelines-for-cmdlet-help"></a>Schreiben von Richtlinien für die Cmdlet-Hilfe

### <a name="write-well"></a>Schreiben Sie auch
"Nothing" wird eine gut geschriebene Thema ersetzt.
Wenn Sie nicht über ein professional Writer sind, finden Sie ein Writer oder den Editor, die Ihnen helfen.
Eine Alternative besteht darin, den Hilfetext in Microsoft Word kopieren und verwenden Sie die Grammatik und Rechtschreibung überprüft werden, um Ihre Arbeit zu verbessern.

### <a name="write-simply"></a>Einfach zu schreiben
Verwenden Sie einfache Wörter und Ausdrücke.
Vermeiden Sie Jargon.
Beachten Sie, dass viele Leser nur mit einem fremdsprachige Wörterbuch und Ihre Hilfethema ausgestattet sind.

### <a name="write-consistently"></a>Schreiben Sie konsistent
Hilfe zu verwandte Cmdlets (z. B. "," Get-X "und" Set-X ") ähneln sollte.
Verwenden Sie die standard-Beschreibungen für standard-Parameter, wie z. B. **Force** und **InputObject**.
(Kopieren sie aus der Hilfe für die Kern-Cmdlets.) Verwenden Sie die standard-Begriffe.
Z. B. "mit dem Parameter", nicht "Argument", und verwenden "Cmdlet" nicht "Befehl" oder "Command-Let".

### <a name="start-the-synopsis-with-a-verb"></a>Starten Sie die Übersicht mit einem verb
Das Feld "Zusammenfassung" wird der Benutzer informiert, welche das Cmdlet durchführt, nicht was, wie es funktioniert.
Verben erstellen Sie eine aufgabenbasierte-Anweisung, die Benutzer darüber informiert, wenn Sie dieses Cmdlet aus, um ihre Anforderungen erfüllt.
Verwenden Sie einfache Verben wie "get", "erstellen" und "ändern".
Vermeiden Sie "Set", und sein kann, und mit Effekten Wörter wie "ändern".

### <a name="focus-on-objects"></a>Konzentrieren Sie sich für Objekte
Die meisten "get" Anzeigen der Cmdlets etwas, aber die primäre Funktion zum Abrufen eines Objekts ist.
In der Ihre Hilfe konzentrieren Sie sich für das Objekt, damit Benutzer verstehen, dass die Standardanzeige eines von vielen ist und sie verwenden können, die Methoden und Eigenschaften des Objekts, das Sie für diese auf unterschiedliche Weise abgerufen.

### <a name="write-detailed-descriptions"></a>Schreiben Sie eine detaillierte Beschreibung
Kurze Listen Sie alle Elemente, die mit dem-Cmdlet in der ausführlichen Beschreibung ausführen kann.
Wenn die main-Funktion ist eine Eigenschaft zu ändern, aber das-Cmdlet kann alle Eigenschaften ändern, listet diese in der detaillierten Beschreibung.

### <a name="use-conventional-syntax"></a>Verwenden Sie herkömmliche Syntax.
Verwenden Sie das standardmäßige Backus-Naur-Format handelt es sich häufig für Windows und UNIX-Befehlszeilenhilfe zu erhalten.

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a>Verwenden Sie Microsoft .NET Framework-Typen für Parameterwerte
Die Platzhalter für Parameterwerte (in der Syntax- und parameterbeschreibungen) anzeigen, die .NET Framework-Typen der Objekte, die der Parameter akzeptiert wird.
Das PowerShell-Team entwickelt diese Konvention können Benutzer über die .NET Framework zu erfahren.

### <a name="write-complete-parameter-descriptions"></a>Schreiben Sie die vollständige parameterbeschreibungen.
Beschreibungen der Parameter müssen ein Benutzer zwei Möglichkeiten informieren: Welche Parameters (dessen Auswirkung) ist und was sie für die Parameterwerte eingeben müssen.

### <a name="write-practical-examples"></a>Praktische Beispiele zu schreiben
In den Beispielen sollte mit allen Parametern, aber das wichtigste ist veranschaulichen, wie Sie das Cmdlet in wirklichkeitsgetreue Aufgaben verwenden.
Beginnen Sie mit der ein einfaches Beispiel, und Schreiben Sie immer komplexere Beispiele.
Zeigen Sie im abschließenden Beispiel, wie Sie das Cmdlet in einer Pipeline verwenden.

### <a name="use-the-notes-field"></a>Verwenden Sie das Feld "Notizen"
Verwenden Sie das Feld "Notizen", um die Konzepte zu erläutern, die Benutzer das-Cmdlet zu verstehen müssen.
Sie können auch Anmerkungen zu dieser Version verwenden, können Benutzer, die häufige Fehler zu vermeiden.
Vermeiden Sie URLs, wie sie ändern.
Geben Sie stattdessen Benutzer Suchbegriffe für.

### <a name="test-your-help"></a>Testen Sie Ihre Hilfe
Testen Sie die Hilfe so, wie Sie den Code zu testen.
Freunden und Kollegen lesen Sie den Hilfeinhalt und Feedback geben.
Sie können auch Feedback aus die Newsgroups einzuholen.

## <a name="see-also"></a>Weitere Informationen

 [Vorgehensweise: Erstellen Sie die Cmdlet-Hilfedatei](./how-to-create-the-cmdlet-help-file.md)

 [Die Cmdlet-Namen und eine Zusammenfassung zu einem Cmdlet-Hilfethema hinzufügen](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [So fügen Sie die ausführliche Beschreibung zu einem Cmdlet-Hilfethema hinzu](./how-to-add-a-cmdlet-description.md)

 [So fügen Sie die Syntax für ein Cmdlet-Hilfethema hinzu](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Gewusst wie: Hinzufügen von Parametern zu einem Cmdlet-Hilfethema](./how-to-add-parameter-information.md)

 [So fügen Sie die zu einem Cmdlet-Hilfethemas Eingabetypen hinzu](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Rückgabe von Werten für ein Cmdlet-Hilfethema hinzufügen](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Gewusst wie: Hinzufügen von Notizen an ein Cmdlet-Hilfethema](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Beispiele für ein Cmdlet-Hilfethema hinzufügen](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Gewusst wie: Hinzufügen von Links zu verwandten Themen zu einem Cmdlet-Hilfethema](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)