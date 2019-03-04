---
title: Cmdlet-Windows-Fehlerberichterstattung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error records [PowerShell], terminating
- non-terminating errors [PowerShell]
- error records [PowerShell]
- terminating errors [PowerShell]
- error records [PowerShell], non-terminating
ms.assetid: 0b014035-52ea-44cb-ab38-bbe463c5465a
caps.latest.revision: 8
ms.openlocfilehash: 7b54fc220a66a47c25b3e8cba644882d31713cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857686"
---
# <a name="cmdlet-error-reporting"></a>Cmdlet-Fehlerberichterstattung

Cmdlets melden festgestellten Fehler unterschiedlich, abhängig davon, ob die Fehler Fehler beendet werden oder Fehler ohne Abbruch. Fehler mit Abbruch sind Fehler, die dazu führen, dass die Pipeline sofort beendet werden soll, oder Fehler, die auftreten, wenn es keinen Grund gibt, die Verarbeitung wird fortgesetzt. Fehler ohne Abbruch werden diese Fehler, die einen aktuellen Fehler gemeldet, aber das Cmdlet kann weiterhin Verarbeiten von Eingabeobjekten. Mit Fehler ohne Abbruch der Benutzer in der Regel eine Benachrichtigung des Problems, aber das-Cmdlet wird weiterhin das nächste Eingabeobjekt verarbeitet.

## <a name="terminating-and-nonterminating-errors"></a>Abbruch und ohne Abbruch-Fehler

Die folgenden Richtlinien können verwendet werden, um festzustellen, ob ein Fehlerzustand, einen Fehler mit Abbruch oder ein Fehler ohne Abbruch ist.

- Verhindert die fehlerbedingung Ihr Cmdlet Weitere Eingabeobjekten erfolgreich zu verarbeiten? Wenn dies der Fall ist, ist dies ein Fehler mit Abbruch.

- Bezieht sich die fehlerbedingung auf ein bestimmtes Objekt für die Eingabe oder eine Teilmenge der Eingabeobjekte? Wenn dies der Fall ist, ist dies ein Fehler ohne Abbruch.

- Akzeptiert das Cmdlet mehrere Eingabeobjekte, z. B. die Verarbeitung auf einem anderen Eingabeobjekt erfolgreich ausgeführt werden kann? Wenn dies der Fall ist, ist dies ein Fehler ohne Abbruch.

- Cmdlets, die mehrere Eingabeobjekte akzeptieren können sollten zwischen was beendet werden und Fehler ohne Abbruch, entscheiden, auch wenn nur ein einzelnes input-Objekt eine bestimmte Situation gilt.

- Cmdlets können erhalten eine beliebige Anzahl von Eingabeobjekten und senden eine beliebige Anzahl von Objekten von Erfolg oder Fehler, bevor eine abschließende Ausnahme auszulösen. Es gibt keine Beziehung zwischen der Anzahl von Eingabeobjekten empfangen und die Anzahl der erfolgreichen und fehlerhaften-Objekte, die gesendet werden.

- Cmdlets, die nur 0-1-Geben Sie die Objekte, und generieren nur 0 bis 1 annehmen kann Ausgabe Objekte sollten Fehler als Fehler behandeln und abschließende Ausnahmen zu generieren.

## <a name="reporting-nonterminating-errors"></a>Melden Sie Fehler ohne Abbruch

Die berichterstellung für einen Fehler ohne Abbruch sollte immer erfolgen, in der Cmdlet Implementierung des der [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -Methode, die [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode, oder die [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Methode. Diese Arten von Fehlern gemeldet werden, durch den Aufruf der [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode, die wiederum einen Fehlerdatensatz in den fehlerdatenstrom sendet.

## <a name="reporting-terminating-errors"></a>Melden Sie Fehler mit Abbruch

Fehler werden gemeldet, durch Auslösen von Ausnahmen oder durch Aufrufen der [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) Methode. Denken Sie daran, dass die Cmdlets können auch abfangen und lösen Sie Ausnahmen, z. B. OutOfMemory erneut aus, sie sind jedoch nicht erforderlich, die Ausnahmen erneut ausgelöst wird, wie die Windows PowerShell-Laufzeit sie ebenfalls abgefangen werden.

Sie können auch eigene Ausnahmen für Probleme für Ihre Situation zu definieren oder zusätzliche Informationen zu einer vorhandenen Ausnahme, die mit der Error-Datensatz hinzuzufügen.

## <a name="error-records"></a>Error-Datensätze

Windows PowerShell einen ohne Abbruch Fehlerzustand, durch die Verwendung von beschreibt [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) Objekte. Jede [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) Objekt enthält Fehlerinformationen für die Kategorie, eine optionale Zielobjekt und Details zur fehlerbedingung an.

### <a name="error-identifiers"></a>Fehler-IDs

Fehler-ID ist eine einfache Zeichenfolge, die die fehlerbedingung in das-Cmdlet identifiziert. Windows PowerShell kombiniert diesen Bezeichner mit einer Cmdlet-Bezeichner, der einen Bezeichner für den vollqualifizierten Fehler erstellen, der später verwendet werden kann, wenn fehlerdatenströmen oder Protokollieren von Fehlern, zu filtern, um die Reaktion auf bestimmte Fehler auf oder andere benutzerdefinierte Aktivitäten.

Beim Fehler-IDs angeben, sollten die folgenden Richtlinien eingehalten werden.

- Unterschiedliche Codepfade werden verschiedene, hoch bestimmte Fehler Bezeichner zuweisen. Jeder Codepfad, der Aufrufe [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) oder [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) muss über einen eigenen Fehler-ID verfügen.

- Fehler-IDs sollten für CLR-Ausnahmetypen für Abbruch und ohne Abbruch Fehler eindeutig sein.

- Ändern Sie die Semantik eines Bezeichners Fehler zwischen den Versionen der Cmdlets oder Windows PowerShell-Anbieter nicht. Nachdem die Semantik eines Bezeichners Fehler eingerichtet wurde, sollte es während des Lebenszyklus Ihres Cmdlets konstant.

- Verwenden Sie für Fehler mit Abbruch eine eindeutigen Fehler-ID für einen bestimmten Typ der CLR-Ausnahme aus. Wenn der Typ der Ausnahme geändert wird, verwenden Sie einen neuen fehlerbezeichner.

- Verwenden Sie für Fehler ohne Abbruch eine bestimmten Fehler-ID für ein bestimmtes Objekt für die Eingabe aus.

- Wählen Sie Text für den Bezeichner, der nur sehr knapp entspricht der Fehler gemeldet wird. Verwenden Sie keine leer- oder Interpunktionszeichen.

- Fehler-IDs, die nicht reproduzierbar sind keine generiert. Generieren Sie z. B. keine Bezeichner, die Prozess-ID enthalten. Fehler-IDs sind nützlich, nur dann, wenn diese Bezeichner entsprechen, die von anderen Benutzern angezeigt werden, die das gleiche Problem auftritt.

### <a name="error-categories"></a>Fehlerkategorien

Fehlerkategorien werden verwendet, um Fehler für den Endbenutzer zu gruppieren. Windows PowerShell definiert diese Kategorien und -Cmdlets und Windows PowerShell-Anbietern müssen sie auswählen, beim Generieren der Error-Datensatzes.

Eine Beschreibung der Fehlerkategorien, die verfügbar sind, finden Sie unter den [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) Enumeration. Im Allgemeinen sollten Sie mithilfe von "noError" zurückgegeben, UndefinedError und allgemeiner Fehler, wann immer möglich.

Benutzer können die Fehler basierend auf Kategorie, wenn sie festgelegt anzeigen "`$ErrorView`", "CategoryView".

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell-Cmdlets](./cmdlet-overview.md)

[Cmdlet-Ausgabe](./types-of-cmdlet-output.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
