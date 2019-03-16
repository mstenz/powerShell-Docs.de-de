---
title: Windows PowerShell-Fehler zeichnet | Microsoft-Dokumentation
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
ms.openlocfilehash: f6f5e50c55b477cbbeeaaf4f3ea665d5dc07758c
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059761"
---
# <a name="windows-powershell-error-records"></a>Windows PowerShell-Fehlerdatensätze

Cmdlets übergeben muss ein [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) Objekt, das die fehlerbedingung und ohne Abbruch Fehler identifiziert.

Die [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) Objekt enthält die folgenden Informationen:

- Die Ausnahme, die den Fehler beschreibt. Dies ist häufig eine Ausnahme, die das Cmdlet erfasst und in einen Fehlerdatensatz konvertiert. Alle Error-Datensatzes muss es sich um eine Ausnahme enthalten.

Wenn das Cmdlet eine Ausnahme nicht abfängt, müssen sie eine neue Ausnahme zu erstellen und wählen Sie die Exception-Klasse, die am besten den Fehlerzustand beschreibt. Sie müssen allerdings nicht die Ausnahme ausgelöst, da er über zugegriffen werden kann die [System.Management.Automation.ErrorRecord.Exception](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) Eigenschaft der [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)Objekt.

- Eine Fehler-ID, die einem Ziel-Kennzeichner, die für Diagnosezwecke und von Windows PowerShell-Skripts verwendet werden können bereitstellt, um spezielle fehlerbedingungen mit bestimmten Fehler-Handler zu verarbeiten. Alle Error-Datensatzes muss eine Fehler-ID enthalten (Siehe Fehler-ID).

- Eine Fehlerkategorie, die eine allgemeine Kennzeichner bereitstellt, die zu Diagnosezwecken verwendet werden können. Alle Error-Datensatz muss eine Fehlerkategorie angeben (Siehe Fehlerkategorie).

- Einer optionalen Ersatz-Fehlermeldung und eine empfohlene Aktion (Siehe Ersatz-Fehlermeldung).

- Informationen zum optionalen Aufruf über das Cmdlet, das den Fehler ausgelöst hat. Diese Informationen werden von Windows PowerShell angegeben (Siehe Aufrufmeldung).

- Das Zielobjekt, das beim Auftreten des Fehlers verarbeitet wurde. Dies ist möglicherweise das Eingabeobjekt aus, oder es möglicherweise ein anderes Objekt, das Ihr Cmdlet verarbeitet wurde. Z. B. für den Befehl `remove-item -recurse c:\somedirectory`, der Fehler wird möglicherweise eine Instanz eines Objekts "FileInfo" für "c:\somedirectory\lockedfile". Die Informationen zum Objekt ist optional.

## <a name="error-identifier"></a>Fehler-ID

Geben Sie einen Bezeichner, der die fehlerbedingung in Ihrem Cmdlet festlegt, bei der Erstellung eines fehlerdatensatzes. Windows PowerShell kombiniert die gezielten Bezeichner, mit dem Namen, Ihre Cmdlets aus, um einen fehlerbezeichner den vollqualifizierten zu erstellen. Die vollqualifizierten Fehler-ID kann zugegriffen werden, über die [System.Management.Automation.ErrorRecord.FullyQualifiedErrorId](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId) Eigenschaft der [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)Objekt. Fehler-ID ist selbst nicht verfügbar. Es steht nur als Teil der vollqualifizierten fehlerbezeichner.

Verwenden Sie die folgenden Richtlinien, um Fehler-IDs zu generieren, bei der Erstellung von Datensätzen:

- Fehler-IDs an ein Fehlerzustand gemäß bestimmten vornehmen. Die Fehler-IDs als Ziel für Diagnosezwecke und von Skripts, die mit bestimmten Fehlerhandler bestimmte fehlerbedingungen zu behandeln. Ein Benutzer muss die Fehler-ID verwenden, um den Fehler und seine Quelle zu identifizieren. Fehler-IDs ermöglichen auch die berichterstellung für bestimmte fehlerbedingungen aus vorhandenen Ausnahmen, damit neue ausnahmeunterklassen nicht erforderlich sind.

- Unterschiedliche Codepfade in der Regel verschiedene Fehler Bezeichner zuweisen. Der Endbenutzer profitiert von bestimmte Bezeichner. Häufig jeden Codepfad, der Aufrufe [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) oder [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) verfügt über eine eigene Bezeichner. Als Faustregel gilt definieren Sie einen neuen Bezeichner, wenn Sie eine neue Vorlagenzeichenfolge für die Fehlermeldung, und umgekehrt definieren. Verwenden Sie die Fehlermeldung nicht als Bezeichner auf.

- Wenn Sie Code mit einem bestimmten Fehler-ID veröffentlichen, legen Sie fest, dass die Semantik von Fehlern mit diesem Bezeichner für das vollständige Produkt Lebenszyklus unterstützen. Nicht wiederverwendet werden sie in einem Kontext, der semantisch von den ursprünglichen Kontext ist. Wenn die Semantik für diesen Fehler ändern, erstellen Sie und verwenden Sie dann einen neuen Bezeichner.

- Sie sollten eine bestimmten Fehler-ID in der Regel nur für Ausnahmen von einem bestimmten CLR-Typ verwenden. Wenn der Typ der Ausnahme oder den Typ des Zielobjekts geändert wird, erstellen Sie und verwenden Sie dann einen neuen Bezeichner.

- Wählen Sie für Ihre Fehler-ID, die präzise zu dem Fehler entspricht, den Sie melden möchten. Verwenden Sie die standard Konventionen für die .NET Framework-benennungs- und Groß-/Kleinschreibung. Verwenden Sie keine leer- oder Interpunktionszeichen. Fehler-IDs dürfen nicht lokalisiert werden.

- Generieren Sie Fehler-IDs nicht dynamisch auf eine Weise nicht reproduziert werden kann. Integrieren Sie z. B. keine Fehlerinformationen wie z. B. eine Prozess-ID. Fehler-IDs sind nur hilfreich, wenn sie die Fehler-IDs angezeigt, die von anderen Benutzern, die die gleiche fehlerbedingung auftreten entsprechen.

## <a name="error-category"></a>Fehlerkategorie

Beim Erstellen eines fehlerdatensatzes Geben Sie die Kategorie des Fehlers mit einem der Konstanten definiert werden, indem die [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) Enumeration. Windows PowerShell verwendet die Fehlerkategorie, um Fehler anzuzeigen, wenn der Benutzer festlegen, die `$ErrorView` Variable `"CategoryView"`.

Vermeiden Sie die Verwendung der [System.Management.Automation.Errorcategory.Notspecified](/dotnet/api/System.Management.Automation.ErrorCategory.NotSpecified) Konstanten. Wenn Sie alle Informationen über den Fehler oder über den Vorgang, der den Fehler verursacht hat, wählen Sie die Kategorie, die den Fehler oder den Vorgang am besten beschreibt, auch wenn die Kategorie keine perfekte Übereinstimmung vorliegt.

Die Informationen von Windows PowerShell wird als die Kategorieansicht Zeichenfolge bezeichnet und basiert auf dem die Eigenschaften der [System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo) Klasse. (Diese Klasse erfolgt über den Fehler [System.Management.Automation.ErrorRecord.CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) Eigenschaft.)

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

Die folgende Liste beschreibt die Informationen angezeigt:

- Kategorie: Ein Windows PowerShell-definierten [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) Konstanten.

- TargetName: Standardmäßig den Namen des Objekts mit dem-Cmdlet verarbeitet hat, als der Fehler aufgetreten ist. Oder ein anderes Cmdlet definierte Zeichenfolge.

- TargetType: Standardmäßig wird der Typ des Zielobjekts. Oder ein anderes Cmdlet definierte Zeichenfolge.

- Aktivität: Standardmäßig ist der Name des-Cmdlets, die die Error-Datensatz erstellt. Oder eine andere Cmdlet definierte Zeichenfolge.

- Grund: Standardmäßig wird der Typ der Ausnahme. Oder ein anderes Cmdlet definierte Zeichenfolge.

## <a name="replacement-error-message"></a>Ersatz-Fehlermeldung

Wenn Sie einen Fehlerdatensatz für ein Cmdlet entwickeln, stammt die Standardfehlermeldung für den Fehler der Standardtext der Meldung in die [System.Exception.Message](/dotnet/api/System.Exception.Message) Eigenschaft. Dies ist eine schreibgeschützte Eigenschaft, die nur für Debugzwecke (gemäß der .NET Framework-Richtlinien), dessen Nachrichtentext dient. Es wird empfohlen, eine Fehlermeldung zu erstellen, die ersetzt oder erweitert der Standardtext der Meldung. Stellen Sie die Nachricht an das Cmdlet Benutzerfreundlicher und spezifischere.

Die Nachricht für die Ersetzung erfolgt über eine [System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) Objekt. Verwenden Sie einen der folgenden Konstruktoren dieses-Objekts, da sie zusätzliche Lokalisierungsinformationen bereitstellen, die von Windows PowerShell verwendet werden kann.

- [ErrorDetails.ErrorDetails (Objekt-Cmdlet, String, String,\[System.Management.Automation.ErrorDetails.%23Ctor%28System.Management.Automation.Cmdlet%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Management.Automation.Cmdlet%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29): Verwenden Sie diesen Konstruktor, wenn Ihre Vorlage enthält eine Ressourcenzeichenfolge in der gleichen Assembly ist in der das Cmdlet implementiert wird, oder wenn Sie, laden Sie die Vorlagenzeichenfolge über eine Überschreibung der möchten der [System.Management.Automation.Cmdlet.GetResourceString ](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString) Methode.

- [ErrorDetails.ErrorDetails (Objekt-Assembly, String, String,\[System.Management.Automation.ErrorDetails.%23Ctor%28System.Reflection.Assembly%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Reflection.Assembly%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29): Verwenden Sie diesen Konstruktor, wenn die Vorlagenzeichenfolge befindet sich in einer anderen Assembly, und Sie es nicht, in einer Überschreibung von geladen werden [System.Management.Automation.Cmdlet.GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString).

Die .NET Framework-Entwurfsrichtlinien für das Schreiben von ausnahmemeldungen einen kleinen Unterschied muss Ersatznachricht entsprechen. Der Status der Richtlinien, den ausnahmemeldungen, die für Entwickler geschrieben werden soll. Diese Nachrichten sollte für den Cmdlet-Benutzer geschrieben werden.

Die Fehlermeldung für den Austausch muss hinzugefügt werden, bevor die [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) oder [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) Methoden aufgerufen werden. Um eine Ersatznachricht hinzuzufügen, legen Sie die [System.Management.Automation.ErrorRecord.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails) Eigenschaft des Error-Datensatzes. Wenn diese Eigenschaft festgelegt ist, zeigt Windows PowerShell die [System.Management.Automation.ErrorDetails.Message*](/dotnet/api/System.Management.Automation.ErrorDetails.Message) -Eigenschaft anstelle der Standardtext der Meldung.

## <a name="recommended-action-information"></a>Informationen zur Aktion empfohlen

Die [System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) Objekt bieten auch Informationen, welche Aktionen empfohlen werden, wenn der Fehler auftritt.

## <a name="invocation-information"></a>Informationen zum Aufruf

Bei Verwendung von einem Cmdlet [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) oder [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) zum Melden eines fehlerdatensatzes, Windows PowerShell Fügt automatisch die Informationen, die den Befehl zu, der aufgerufen wurde beschreiben, wenn der Fehler aufgetreten ist. Diese Informationen werden bereitgestellt, indem eine [System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo) Objekt, das den Namen des Cmdlets enthält, die durch den Befehl aus, den Befehl selbst aufgerufen wurde und Informationen über die Pipeline oder das Skript. Diese Eigenschaft ist schreibgeschützt.

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)

[System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Windows PowerShell-Fehlerberichterstattung](./error-reporting-concepts.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
