---
title: Windows PowerShell-Fehler Datensätze | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error category [PowerShell SDK]
- error identifier [PowerShell SDK]
- error records [PowerShell SDK]
- error category string [PowerShell SDK]
ms.assetid: bdd66fea-eb63-4bb6-9cbe-9a799e5e0db5
caps.latest.revision: 9
ms.openlocfilehash: 5412d88b690a1f5f1ef387416e3bf9da3a32c95d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369109"
---
# <a name="windows-powershell-error-records"></a>Windows PowerShell-Fehlerdatensätze

Cmdlets müssen ein [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -Objekt übergeben, das die Fehlerbedingung für das Beenden und das Abbrechen von Fehlern angibt, die nicht abgebrochen werden.

Das [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -Objekt enthält die folgenden Informationen:

- Die Ausnahme, die den Fehler beschreibt. Häufig handelt es sich hierbei um eine Ausnahme, die vom Cmdlet abgefangen und in einen Fehler Daten Satz konvertiert wurde. Jeder Fehler Daten Satz muss eine Ausnahme enthalten.

Wenn das Cmdlet eine Ausnahme nicht abfängt, muss eine neue Ausnahme erstellt und die Ausnahme Klasse ausgewählt werden, die die Fehlerbedingung am besten beschreibt. Sie müssen die Ausnahme jedoch nicht auslösen, da Sie über die [System. Management. Automation. ErrorRecord. Exception](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) -Eigenschaft des [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -Objekts aufgerufen werden kann.

- Ein Fehler Bezeichner, der einen Ziel Kenn Zeichner bereitstellt, der zu Diagnose Zwecken und von Windows PowerShell-Skripts verwendet werden kann, um bestimmte Fehlerbedingungen mit bestimmten Fehler Handlern zu verarbeiten. Jeder Fehler Daten Satz muss einen Fehler Bezeichner enthalten (siehe Fehler Bezeichner).

- Eine Fehler Kategorie, die einen allgemeinen Kenn Zeichner bereitstellt, der zu Diagnose Zwecken verwendet werden kann. Jeder Fehler Daten Satz muss eine Fehler Kategorie angeben (siehe Fehler Kategorie).

- Eine optionale Ersatz Fehlermeldung und eine empfohlene Aktion (siehe Ersatz Fehlermeldung).

- Optionale Aufruf Informationen über das Cmdlet, das den Fehler ausgelöst hat. Diese Informationen werden von Windows PowerShell angegeben (siehe Aufruf Nachricht).

- Das Zielobjekt, das beim Auftreten des Fehlers verarbeitet wurde. Dies kann das Eingabe Objekt sein, oder es kann ein anderes Objekt sein, das das Cmdlet verarbeitet hat. Beispielsweise kann für den Befehl `remove-item -recurse c:\somedirectory` der Fehler eine Instanz eines FileInfo-Objekts für "c:\somedirectory\lockedfile" sein. Die Zielobjekt Informationen sind optional.

## <a name="error-identifier"></a>Fehler Bezeichner

Wenn Sie einen Fehler Daten Satz erstellen, geben Sie einen Bezeichner an, der die Fehlerbedingung innerhalb des Cmdlets festlegt. Windows PowerShell kombiniert den Ziel Bezeichner mit dem Namen des Cmdlets, um einen voll qualifizierten Fehler Bezeichner zu erstellen. Der Zugriff auf den voll qualifizierten Fehler Bezeichner kann über die [System. Management. Automation. ErrorRecord. fullyqualifiederrorid-](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId) Eigenschaft des [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -Objekts erfolgen. Der Fehler Bezeichner ist allein nicht verfügbar. Sie ist nur als Teil des voll qualifizierten Fehler Bezeichners verfügbar.

Verwenden Sie die folgenden Richtlinien, um beim Erstellen von Fehler Datensätzen Fehler Bezeichner zu generieren:

- Machen Sie Fehler Bezeichner für einen Fehlerzustand spezifisch. Ziel der Fehler Bezeichner für Diagnosezwecke und für Skripts, die bestimmte Fehlerbedingungen mit bestimmten Fehler Handlern verarbeiten. Ein Benutzer sollte die Fehlerkennung verwenden können, um den Fehler und dessen Quelle zu identifizieren. Fehler Bezeichner ermöglichen auch die Berichterstellung für bestimmte Fehlerbedingungen aus vorhandenen Ausnahmen, sodass keine neuen Ausnahme Unterklassen erforderlich sind.

- Weisen Sie unterschiedliche Fehler Bezeichner unterschiedlichen Codepfade zu. Der Endbenutzer profitiert von bestimmten bezeichlern. Häufig hat jeder Codepfad, der " [System. Management. Automation. Cmdlet. Write-error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) " oder " [System. Management. Automation. Cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) " aufruft, einen eigenen Bezeichner. Definieren Sie als Regel einen neuen Bezeichner, wenn Sie eine neue Vorlagen Zeichenfolge für die Fehlermeldung definieren und umgekehrt. Verwenden Sie die Fehlermeldung nicht als Bezeichner.

- Wenn Sie Code mithilfe eines bestimmten Fehler Bezeichners veröffentlichen, legen Sie die Semantik von Fehlern mit diesem Bezeichner für den gesamten Lebenszyklus des Produkt Supports fest. Verwenden Sie Sie nicht in einem Kontext, der semantisch vom ursprünglichen Kontext abweicht. Wenn sich die Semantik dieses Fehlers ändert, erstellen Sie einen neuen Bezeichner, und verwenden Sie ihn.

- Sie sollten im Allgemeinen nur für Ausnahmen eines bestimmten CLR-Typs einen bestimmten Fehler Bezeichner verwenden. Wenn sich der Typ der Ausnahme oder der Typ des Zielobjekts ändert, erstellen Sie, und verwenden Sie dann einen neuen Bezeichner.

- Wählen Sie Text für die Fehler-ID aus, die dem von Ihnen Bericht Erstellungs Fehler entspricht. Verwenden Sie .NET Framework Benennungs-und Groß-/Kleinschreibung Verwenden Sie keine Leerzeichen oder Interpunktions Zeichen. Die Fehler Bezeichner können nicht lokalisiert werden.

- Generieren Sie Fehler Bezeichner nicht dynamisch auf nicht reproduzierbare Weise. Binden Sie z. b. keine Fehlerinformationen ein, z. b. eine Prozess-ID. Fehler Bezeichner sind nur hilfreich, wenn Sie den Fehler bezeichmern entsprechen, die von anderen Benutzern erkannt werden, die dieselbe Fehlerbedingung aufweisen.

## <a name="error-category"></a>Fehler Kategorie

Wenn Sie einen Fehler Daten Satz erstellen, geben Sie die Kategorie des Fehlers mithilfe einer der Konstanten an, die von der [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) -Enumeration definiert werden. Windows PowerShell verwendet die Fehler Kategorie, um Fehlerinformationen anzuzeigen, wenn Benutzer die `$ErrorView`-Variable auf `"CategoryView"` festlegen.

Vermeiden Sie die Verwendung der [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) **NotSet** -Konstante. Wenn Sie Informationen über den Fehler oder den Vorgang haben, der den Fehler verursacht hat, wählen Sie die Kategorie aus, die den Fehler oder den Vorgang am besten beschreibt, auch wenn die Kategorie nicht perfekt geeignet ist.

Die von Windows PowerShell angezeigten Informationen werden als Zeichenfolge für die Kategorieansicht bezeichnet und aus den Eigenschaften der [System. Management. Automation. errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo) -Klasse erstellt. (Auf diese Klasse wird durch die Error [System. Management. Automation. ErrorRecord. categoryinfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) -Eigenschaft zugegriffen.)

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

In der folgenden Liste werden die angezeigten Informationen beschrieben:

- Kategorie: eine Windows PowerShell-definierte [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) -Konstante.

- TargetName: standardmäßig der Name des Objekts, das das Cmdlet verarbeitet hat, als der Fehler aufgetreten ist. Oder eine andere Cmdlet-definierte Zeichenfolge.

- TargetType: standardmäßig der Typ des Zielobjekts. Oder eine andere Cmdlet-definierte Zeichenfolge.

- Aktivität: standardmäßig der Name des Cmdlets, von dem der Fehler Daten Satz erstellt wurde. Oder eine andere Cmdlet-definierte Zeichenfolge.

- Ursache: der Ausnahmetyp ist standardmäßig. Oder eine andere Cmdlet-definierte Zeichenfolge.

## <a name="replacement-error-message"></a>Ersetzungs Fehlermeldung

Wenn Sie einen Fehler Daten Satz für ein Cmdlet entwickeln, wird die Standard Fehlermeldung für den Fehler aus dem Standard Meldungs Text in der [System. Exception. Message](/dotnet/api/System.Exception.Message) -Eigenschaft ausgegeben. Dabei handelt es sich um eine schreibgeschützte Eigenschaft, deren Meldungs Text nur für Debuggingzwecke vorgesehen ist (gemäß den .NET Framework Richtlinien). Es wird empfohlen, dass Sie eine Fehlermeldung erstellen, die den Standard Nachrichtentext ersetzt oder erweitert. Machen Sie die Nachricht benutzerfreundlicher und spezifischere für das Cmdlet.

Die Ersetzungs Meldung wird von einem [System. Management. Automation. errorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) -Objekt bereitgestellt. Verwenden Sie einen der folgenden Konstruktoren dieses Objekts, da Sie zusätzliche Lokalisierungs Informationen bereitstellen, die von Windows PowerShell verwendet werden können.

- [ErrorDetails (Cmdlet, String, String, Object [])](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Management_Automation_Cmdlet_System_String_System_String_System_Object___): Verwenden Sie diesen Konstruktor, wenn die Vorlagen Zeichenfolge eine Ressourcen Zeichenfolge in derselben Assembly ist, in der das Cmdlet implementiert ist, oder wenn Sie die Vorlagen Zeichenfolge über eine außer Kraft setzung des [ System. Management. Automation. Cmdlet. GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString) -Methode.

- [ErrorDetails (Assembly, String, String, Object [])](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Reflection_Assembly_System_String_System_String_System_Object___): Verwenden Sie diesen Konstruktor, wenn sich die Vorlagen Zeichenfolge in einer anderen Assembly befindet, und Sie Sie nicht durch eine außer Kraft Setzung von [System. Management. Automation. Cmdlet. GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString)laden.

Die Ersetzungs Nachricht muss den .NET Framework Entwurfs Richtlinien entsprechen, um Ausnahme Meldungen mit geringem Unterschied zu schreiben. Die Richtlinien geben an, dass Ausnahme Meldungen für Entwickler geschrieben werden sollen. Diese Ersetzungs Nachrichten sollten für den Cmdlet-Benutzer geschrieben werden.

Die Ersetzungs Fehlermeldung muss hinzugefügt werden, bevor die Methoden " [System. Management. Automation. Cmdlet. Write-error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) " oder " [System. Management. Automation. Cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) " aufgerufen werden. Zum Hinzufügen einer Ersatz Meldung legen Sie die [System. Management. Automation. ErrorRecord. errorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails) -Eigenschaft des Fehler Datensatzes fest. Wenn diese Eigenschaft festgelegt ist, zeigt Windows PowerShell die [System. Management. Automation. errorDetails. Message *](/dotnet/api/System.Management.Automation.ErrorDetails.Message) -Eigenschaft anstelle des Standard Nachrichten Texts an.

## <a name="recommended-action-information"></a>Empfohlene Aktions Informationen

Das [System. Management. Automation. errorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) -Objekt kann auch Informationen darüber bereitstellen, welche Aktionen bei Auftreten des Fehlers empfohlen werden.

## <a name="invocation-information"></a>Aufruf Informationen

Wenn ein Cmdlet " [System. Management. Automation. Cmdlet. Write-error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) " oder " [System. Management. Automation. Cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) " verwendet, um einen Fehler Daten Satz zu melden, werden von Windows PowerShell automatisch Informationen hinzugefügt, die die der Befehl, der aufgerufen wurde, als der Fehler aufgetreten ist. Diese Informationen werden von einem [System. Management. Automation. invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo) -Objekt bereitgestellt, das den Namen des Cmdlets enthält, das vom Befehl aufgerufen wurde, dem Befehl selbst und Informationen zur Pipeline oder dem Skript. Diese Eigenschaft ist schreibgeschützt.

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. Cmdlet. Write error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System. Management. Automation. Cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0)

[System. Management. Automation. errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System. Management. Automation. errorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)

[System. Management. Automation. invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Windows PowerShell-Fehlerberichterstattung](./error-reporting-concepts.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
