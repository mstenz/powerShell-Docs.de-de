---
ms.date: 3/18/2019
title: Erstellen von Get-WinEvent-Abfragen mit FilterHashtable
ms.openlocfilehash: 28ba3c99a297944003a28eaba7de34b77d9df536
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293281"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a>Erstellen von Get-WinEvent-Abfragen mit FilterHashtable

Den **Scripting Guy**-Original-Blogbeitrag vom 3. Juni 2014 können Sie unter [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/) (Verwenden von FilterHashTable zum Filtern des Ereignisprotokolls mit PowerShell) lesen.

Dieser Artikel ist ein Auszug des ursprünglichen Blogbeitrags und erläutert die Verwendung des **FilterHashtable**-Parameters des `Get-WinEvent`-Cmdlets zum Filtern von Ereignisprotokollen. Das PowerShell `Get-WinEvent`-Cmdlet bietet ein leistungsstarkes Verfahren zum Filtern von Windows-Ereignis- und Diagnoseprotokollen. Die Leistung wird besser, wenn eine `Get-WinEvent`-Abfrage den **FilterHashtable**-Parameter nutzt.

Bei der Arbeit mit großen Ereignisprotokollen ist es nicht effizient, Objekte die Pipeline hinab an einen `Where-Object`-Befehl zu senden. Vor PowerShell 6 war das `Get-EventLog`-Cmdlet eine weitere Option, Protokolldaten abzurufen. Beispielsweise sind die folgenden Befehle zum Filtern der **Microsoft-Windows-Defrag**-Protokolle ineffizient:

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

Der folgende Befehl verwendet eine Hashtabelle, die die Leistung steigert:

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a>Blogbeiträge zur Enumeration

Dieser Artikel enthält Informationen zur Verwendung von Enumerationswerten in einer Hashtabelle. Weitere Informationen über Enumeration finden Sie in diesen **Scripting Guy**-Blogbeiträgen. Um eine Funktion zu erstellen, die die Enumerationswerte zurückgibt, lesen Sie [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values) (Enumerationen und Werte).
Weitere Informationen finden Sie in der [Scripting Guy-Reihe von Blogbeiträgen zur Enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).

## <a name="hash-table-keyvalue-pairs"></a>Hashtabellen-Schlüssel/Wert-Paare

Um effiziente Abfragen zu erstellen, verwenden Sie das `Get-WinEvent`-Cmdlet mit dem **FilterHashtable**-Parameter.
**FilterHashtable** akzeptiert eine Hashtabelle als Filter, um bestimmte Informationen aus Windows-Ereignisprotokollen abzurufen. Eine Hashtabelle verwendet **Schlüssel/Wert-Paare**. Weitere Informationen zu Hashtabellen finden Sie unter [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables) (Informationen zu Hashtabellen).

Wenn sich die **Schlüssel/Wert**-Paare in der gleichen Zeile befinden, müssen sie durch ein Semikolon getrennt werden. Wenn sich jedes **Schlüssel/Wert**-Paar in einer separaten Zeile befindet, ist kein Semikolon erforderlich. Beispielsweise werden in diesem Artikel **Schlüssel/Wert**-Paare in separaten Zeilen angeordnet und keine Semikola verwendet.

Dieses Beispiel nutzt mehrere der **Schlüssel/Wert**-Paare des **FilterHashtable**-Parameters. Die vollständige Abfrage beinhaltet **LogName**, **ProviderName**, **Keywords**, **ID** und **Level**.

Die akzeptierten **Schlüssel/Wert**-Paare sind in der folgenden Tabelle dargestellt und in der Dokumentation für den [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable**-Parameter enthalten.

In der folgenden Tabelle sind die Schlüsselnamen und Datentypen aufgelistet und ob für einen Datenwert Platzhalterzeichen akzeptiert werden.

| Schlüsselname     | Wertdatentyp    | Platzhalterzeichen akzeptiert? |
|------------- | ------------------ | ---------------------------- |
| LogName      | `<String[]>`       | Ja |
| ProviderName | `<String[]>`       | Ja |
| Pfad         | `<String[]>`       | Nein  |
| Keywords     | `<Long[]>`         | Nein  |
| ID           | `<Int32[]>`        | Nein  |
| Ebene        | `<Int32[]>`        | Nein  |
| StartTime    | `<DateTime>`       | Nein  |
| EndTime      | `<DateTime>`       | Nein  |
| UserID       | `<SID>`            | Nein  |
| Daten         | `<String[]>`       | Nein  |
| *            | `<String[]>`       | Nein  |

## <a name="building-a-query-with-a-hash-table"></a>Erstellen einer Abfrage mit einer Hashtabelle

Um die Ergebnisse zu überprüfen und Probleme zu behandeln, ist es sinnvoll, die Hashtabelle aus jeweils einzelnen **Schlüssel/Wert**-Paaren aufzubauen. Die Abfrage ruft Daten aus dem **Anwendungsprotokoll** ab. Die Hashtabelle ist gleichbedeutend mit `Get-WinEvent –LogName Application`.

Erstellen Sie zunächst die `Get-WinEvent`-Abfrage. Verwenden Sie das **Schlüssel/Wert**-Paar des **FilterHashtable**-Parameters mit dem Schlüssel **LogName** und dem Wert **Application**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

Setzen Sie den Aufbau der Hashtabelle mit dem Schlüssel **ProviderName** fort. Der **ProviderName** ist der Name, der im Feld **Source** in der **Windows-Ereignisanzeige** angezeigt wird. Beispielsweise **.NET Runtime** im folgenden Screenshot:

![Abbildung der Quellen der Windows-Ereignisanzeige.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

Aktualisieren Sie die Hashtabelle, und schließen Sie das **Schlüssel/Wert**-Paar mit dem Schlüssel **ProviderName** und dem Wert **.NET Runtime** ein.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

Wenn Ihre Abfrage Daten aus archivierten Ereignisprotokollen abrufen muss, verwenden Sie den Schlüssel **Path**. Der Wert von **Path** gibt den vollständigen Pfad zur Protokolldatei an. Weitere Informationen finden Sie im **Scripting Guy**-Blogbeitrag [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors) (Verwenden von PowerShell zum Analysieren von gespeicherten Ereignisprotokollen auf Fehler).

## <a name="using-enumerated-values-in-a-hash-table"></a>Verwenden von Enumerationswerten in einer Hashtabelle

**Keywords** ist der nächste Schlüssel in der Hashtabelle. Der Datentyp **Keywords** ist ein Array vom Werttyp `[long]`, der eine große Zahl enthält. Verwenden Sie den folgenden Befehl, um den Maximalwert von `[long]` zu ermitteln:

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

Für den Schlüssel **Keywords** verwendet PowerShell eine Zahl, nicht eine Zeichenfolge, wie etwa **Security**. In der **Windows-Ereignisanzeige** werden die **Schlüsselwörter** als Zeichenfolgen dargestellt, sie sind jedoch Enumerationswerte. Wenn Sie in der Hashtabelle den Schlüssel **Keywords** zusammen mit einem Zeichenfolgenwert verwenden, wird eine Fehlermeldung angezeigt.

Öffnen Sie die **Windows-Ereignisanzeige**, und klicken Sie im Bereich **Aktionen** auf **Aktuelles Protokoll filtern**.
Im Dropdownmenü **Schlüsselwörter** werden die verfügbaren Schlüsselwörter angezeigt, wie im folgenden Screenshot zu sehen:

![Abbildung der Schlüsselwörter der Windows-Ereignisanzeige.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

Verwenden Sie den folgenden Befehl, um die `StandardEventKeywords`-Eigenschaftsnamen anzuzeigen.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

Die aufgezählten Werte sind im **.NET Framework** dokumentiert. Weitere Informationen finden Sie unter [StandardEventKeywords Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).

Die Namen und Enumerationswerte der **Schlüsselwörter** sind wie folgt:

| Name             |  Wert            |
| ---------------- | ------------------|
| AuditFailure     | 4503599627370496  |
| AuditSuccess     | 9007199254740992  |
| CorrelationHint2 | 18014398509481984 |
| EventLogClassic  | 36028797018963968 |
| Sqm              | 2251799813685248  |
| WdiDiagnostic    | 1125899906842624  |
| WdiContext       | 562949953421312   |
| ResponseTime     | 281474976710656   |
| Keine             | 0                 |

Aktualisieren Sie die Hashtabelle, und schließen Sie das **Schlüssel/Wert**-Paar mit dem Schlüssel **Keywords**und dem **EventLogClassic**-Aufzählungswert **36028797018963968** ein.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a>Statischer Eigenschaftswert der Keywords-Eigenschaft (optional)

Der Schlüssel **Keywords** ist aufgezählt, Sie können in der Hashtabellenabfrage aber einen statischen Eigenschaftsnamen verwenden.
Anstatt die zurückgegebene Zeichenfolge zu verwenden, muss der Eigenschaftsname mit der Eigenschaft **Value__** in einen Wert konvertiert werden.

Beispielsweise verwendet das folgende Skript die Eigenschaft **Value__**.

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a>Filtern nach Ereignis-ID

Um spezifischere Daten zu erhalten, werden die Ergebnisse der Abfrage nach der **Ereignis-ID** gefiltert. Auf die **Ereignis-ID** wird in der Hashtabelle in Form des Schlüssels **ID** Bezug genommen, und der Wert ist eine spezifische **Ereignis-ID**. In der **Windows-Ereignisanzeige** wird die **Ereignis-ID** angezeigt. In diesem Beispiel wird die **Ereignis-ID 1023** verwendet.

Aktualisieren Sie die Hashtabelle, und schließen Sie das **Schlüssel/Wert**-Paar mit dem Schlüssel **ID** und dem Wert **1023** ein.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a>Filtern nach Ebene

Um die Ergebnisse weiter einzugrenzen und nur Ereignisse aufzunehmen, die Fehler darstellen, verwenden Sie den Schlüssel **Level**.
In der **Windows-Ereignisanzeige** wird der **Level** als Zeichenfolgenwert dargestellt, es handelt sich jedoch um Enumerationswerte. Wenn Sie in der Hashtabelle den Schlüssel **Level** zusammen mit einem Zeichenfolgenwert verwenden, wird eine Fehlermeldung angezeigt.

**Level** weist Werte wie **Error**, **Warning** oder **Informational** auf. Verwenden Sie den folgenden Befehl, um die Eigenschaftsnamen für `StandardEventLevel` anzuzeigen.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

Die aufgezählten Werte sind im **.NET Framework** dokumentiert. Weitere Informationen finden Sie unter [StandardEventLevel Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).

Die Namen und Enumerationswerte von **Level** sind wie folgt:

| Name           | Wert |
| -------------- | ----- |
| Ausführlich        |   5   |
| Informational  |   4   |
| Warning        |   3   |
| Fehler          |   2   |
| Kritisch       |   1   |
| LogAlways      |   0   |

Die Hash-Tabelle für die vollständige Abfrage enthält den Schlüssel **Level** und den Wert **2**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a>Statische Level-Eigenschaft in der Enumeration (optional)

Der Schlüssel **Level** ist aufgezählt, Sie können in der Hashtabellenabfrage aber einen statischen Eigenschaftsnamen verwenden.
Anstatt die zurückgegebene Zeichenfolge zu verwenden, muss der Eigenschaftsname mit der Eigenschaft **Value__** in einen Wert konvertiert werden.

Beispielsweise verwendet das folgende Skript die Eigenschaft **Value__**.

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```