---
title: Cmdlet-Fehlerberichterstattung | Microsoft-Dokumentation
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
ms.openlocfilehash: 5dfec318438ca139518c596011ac5e56445738ea
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365919"
---
# <a name="cmdlet-error-reporting"></a>Cmdlet-Fehlerberichterstattung

Cmdlets sollten Fehler unterschiedlich melden, je nachdem, ob Fehler durch das Beenden von Fehlern oder nicht abschließende Fehler verursacht werden. Abschließende Fehler sind Fehler, die dazu führen, dass die Pipeline sofort beendet wird, oder Fehler, die auftreten, wenn es keinen Grund gibt, die Verarbeitung fortzusetzen. Fehler, die nicht abgebrochen werden, sind die Fehler, die einen aktuellen Fehlerzustand melden, aber das Cmdlet kann die Verarbeitung von Eingabe Objekten fortsetzen. Bei nicht abschließenden Fehlern wird der Benutzer in der Regel über das Problem benachrichtigt, aber das Cmdlet verarbeitet weiterhin das nächste Eingabe Objekt.

## <a name="terminating-and-nonterminating-errors"></a>Abschließende und nicht abschließende Fehler

Die folgenden Richtlinien können verwendet werden, um zu bestimmen, ob eine Fehlerbedingung ein Abbruch Fehler oder ein Fehler ohne Abbruch ist.

- Verhindert die Fehlerbedingung, dass das Cmdlet keine weiteren Eingabe Objekte verarbeitet? Wenn dies der Fall ist, ist dies ein Abbruch Fehler.

- Handelt es sich um einen Fehlerzustand, der sich auf ein bestimmtes Eingabe Objekt oder eine Teilmenge von Eingabe Objekten bezieht? Wenn dies der Fall ist, ist dies ein Fehler ohne Abbruch.

- Akzeptiert das Cmdlet mehrere Eingabe Objekte, sodass die Verarbeitung für ein anderes Eingabe Objekt erfolgreich ist? Wenn dies der Fall ist, ist dies ein Fehler ohne Abbruch.

- Cmdlets, die mehrere Eingabe Objekte akzeptieren können, sollten zwischen den Fehlern beim Beenden und beim nicht beenden entscheiden, auch wenn eine bestimmte Situation nur für ein einzelnes Eingabe Objekt gilt.

- Cmdlets können eine beliebige Anzahl von Eingabe Objekten empfangen und eine beliebige Anzahl von Success-oder Error-Objekten senden, bevor eine Abbruch Ausnahme ausgelöst wird. Es gibt keine Beziehung zwischen der Anzahl der empfangenen Eingabe Objekte und der Anzahl der empfangenen Erfolgs-und Fehler Objekte.

- Cmdlets, die nur 0-1-Eingabe Objekte akzeptieren und nur 0-1 Output-Objekte generieren, sollten Fehler als Fehler beim Abbrechen behandeln und abschließende Ausnahmen generieren.

## <a name="reporting-nonterminating-errors"></a>Melden von nicht abschließenden Fehlern

Die Berichterstellung eines Fehlers ohne Abbruch sollte immer innerhalb der Cmdlet-Implementierung der [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -Methode, der [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode oder die [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode. Diese Fehlertypen werden gemeldet, indem die [System. Management. Automation. Cmdlet. Write error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode aufgerufen wird, die wiederum einen Fehler Daten Satz an den fehlerstream sendet.

## <a name="reporting-terminating-errors"></a>Melden von abschließenden Fehlern

Abschließende Fehler werden gemeldet, indem Ausnahmen ausgelöst oder die [System. Management. Automation. Cmdlet. ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) -Methode aufgerufen wird. Beachten Sie, dass Cmdlets Ausnahmen wie z. b. **oudefmemory**auch abfangen und erneut auslösen können, aber Sie müssen Ausnahmen nicht erneut auslösen, da Sie von der PowerShell-Laufzeit ebenfalls abgefangen werden.

Sie können auch eigene Ausnahmen für Probleme definieren, die für Ihre Situation spezifisch sind, oder einer vorhandenen Ausnahme mithilfe des Fehler Datensatzes zusätzliche Informationen hinzufügen.

## <a name="error-records"></a>Fehler Datensätze

PowerShell beschreibt eine nicht abschließende Fehlerbedingung mit [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -Objekten. Jedes-Objekt stellt Fehler Kategorieinformationen, ein optionales Zielobjekt und Details zum Fehlerzustand bereit.

### <a name="error-identifiers"></a>Fehler Bezeichner

Der Fehler Bezeichner ist eine einfache Zeichenfolge, die die Fehlerbedingung innerhalb des Cmdlets identifiziert.
PowerShell kombiniert diesen Bezeichner mit einem Cmdlet-Bezeichner, um einen voll qualifizierten Fehler Bezeichner zu erstellen, der später beim Filtern von Fehler Datenströmen oder Protokollierungs Fehlern, beim reagieren auf bestimmte Fehler oder bei anderen benutzerspezifischen Aktivitäten verwendet werden kann.

Beim Angeben von Fehler bezeichmern sollten die folgenden Richtlinien befolgt werden:

- Weisen Sie unterschiedliche, sehr spezifische Fehler Bezeichner unterschiedlichen Codepfade zu. Jeder Codepfad, der " [System. Management. Automation. Cmdlet. Write-error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) " oder " [System. Management. Automation. Cmdlet. ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) " aufruft, sollte über einen eigenen Fehler Bezeichner verfügen.

- Fehler Bezeichner sollten für Fehler beim Beenden und beim nicht beenden eindeutig für CLR-Ausnahme Typen (Common Language Runtime) gelten.

- Ändern Sie nicht die Semantik eines Fehler Bezeichners zwischen den Versionen des Cmdlets oder des PowerShell-Anbieters. Nachdem die Semantik eines Fehler Bezeichners festgelegt wurde, sollte Sie während des gesamten Lebenszyklus des Cmdlets konstant bleiben.

- Verwenden Sie für das Beenden von Fehlern einen eindeutigen Fehler Bezeichner für einen bestimmten CLR-Ausnahmetyp. Wenn sich der Ausnahmetyp ändert, verwenden Sie einen neuen Fehler Bezeichner.

- Verwenden Sie für nicht abschließende Fehler einen bestimmten Fehler Bezeichner für ein bestimmtes Eingabe Objekt.

- Wählen Sie Text für den Bezeichner aus, der dem gemeldeten Fehler entspricht. Verwenden Sie keine Leerzeichen oder Interpunktions Zeichen.

- Generieren Sie keine Fehler Bezeichner, die nicht reproduzierbar sind. Generieren Sie z. b. keine Bezeichner, die eine Prozess-ID enthalten. Fehler Bezeichner sind nur hilfreich, wenn Sie bezeichmern entsprechen, die von anderen Benutzern mit dem gleichen Problem erkannt werden.

### <a name="error-categories"></a>Fehlerkategorien

Fehlerkategorien werden zum Gruppieren von Fehlern für den Benutzer verwendet. PowerShell definiert diese Kategorien und Cmdlets, und PowerShell-Anbieter müssen bei der Erstellung des Fehler Datensatzes zwischen Ihnen wählen.

Eine Beschreibung der verfügbaren Fehlerkategorien finden Sie unter der [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) -Enumeration. Im Allgemeinen sollten Sie, wenn möglich, die Verwendung von " **noError**", " **undefinederror**" und " **genericerror** " vermeiden.

Benutzer können Fehler basierend auf der Kategorie anzeigen, wenn Sie `$ErrorView` auf **categoryview**festgelegt haben.

## <a name="see-also"></a>Siehe auch

[Cmdlet-Übersicht](./cmdlet-overview.md)

[Cmdlet-Ausgabetypen](./types-of-cmdlet-output.md)

[Windows PowerShell-Referenz](../windows-powershell-reference.md)
