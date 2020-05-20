---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Entfernen von Objekten aus der Pipeline – Where-Object
ms.openlocfilehash: 370e7745341b70c0794352a690d5750d21f53ac2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737184"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a>Entfernen von Objekten aus der Pipeline (Where-Object)

In PowerShell geschieht es häufig, dass Sie mehr Objekte als gewünscht generieren und an eine Pipeline übergeben. Mithilfe der `Format-*`-Cmdlets können Sie die anzuzeigenden Eigenschaften bestimmter Objekte angeben, aber auf diese Weise ist es nicht möglich, ganze Objekte aus der Anzeige zu entfernen. Möglicherweise möchten Sie die Objekte vor dem Ende einer Pipeline filtern, um nur für eine Teilmenge der ursprünglich generierten Objekte bestimmte Aktionen auszuführen.

PowerShell umfasst ein `Where-Object`-Cmdlet, mit dem Sie jedes Objekt in der Pipeline testen können, um es nur dann an die Pipeline zu übergeben, wenn es eine bestimmte Testbedingung erfüllt. Objekte, die den Test nicht bestehen, werden aus der Pipeline entfernt. Sie geben die Testbedingung als Wert des Parameters **FilterScript** an.

## <a name="performing-simple-tests-with-where-object"></a>Ausführen einfacher Tests mit „Where-Object“

Der Wert von **FilterScript** ist ein *Skriptblock* – d. h. mindestens ein in geschweiften Klammern eingeschlossener PowerShell-Befehl (`{}`) –, der als TRUE oder FALSE ausgewertet wird. Diese Skriptblöcke können sehr einfach sein, aber ihre Erstellung erfordert Kenntnisse eines anderen PowerShell-Konzepts: Vergleichsoperatoren. Mit einem Vergleichsoperator werden die Elemente auf den beiden Seiten des Operators verglichen. Vergleichsoperatoren beginnen mit einem Minuszeichen (`-`), gefolgt von einem Namen. Die grundlegenden Vergleichsoperatoren können für nahezu jede Art von Objekt verwendet werden. Die erweiterten Vergleichsoperatoren können möglicherweise nur mit Text oder Arrays verwendet werden.

> [!NOTE]
> Bei PowerShell-Vergleichsoperatoren wird beim Arbeiten mit Text die Groß-/Kleinschreibung standardmäßig nicht beachtet.

Aus Analysegründen werden Symbole wie `<`, `>` und `=` nicht als Vergleichsoperatoren verwendet. Stattdessen bestehen Vergleichsoperatoren aus Buchstaben. In der folgenden Tabelle sind die grundlegenden Vergleichsoperatoren aufgeführt.

| Vergleichsoperator |                  Bedeutung                   |    Beispiel (gibt „true“ zurück)    |
| ------------------- | ------------------------------------------ | ---------------------------- |
| -eq                 | Ist gleich                                | 1 -eq 1                      |
| -ne                 | Ist ungleich                            | 1 -ne 2                      |
| -lt                 | Ist kleiner als                               | 1 -lt 2                      |
| -le                 | Ist kleiner als oder gleich                   | 1 -le 2                      |
| -gt                 | Ist größer als                            | 2 -gt 1                      |
| -ge                 | Ist größer als oder gleich                | 2 -ge 1                      |
| -like               | Entspricht (Platzhaltervergleich für Text)     | "file.doc" -like "f*.do?"    |
| -notlike            | Entspricht nicht (Platzhaltervergleich für Text) | "file.doc" -notlike "p*.doc" |
| -contains           | Enthält                                   | 1,2,3 -contains 1            |
| -notcontains        | Enthält nicht                           | 1,2,3 -notcontains 4         |

In `Where-Object`-Skriptblöcken dient die spezielle Variable `$_` zum Verweisen auf das aktuelle Objekt in der Pipeline. Es folgt ein Beispiel für die Funktionsweise. Wenn Sie über eine Liste mit Zahlen verfügen und nur diejenigen zurückgegeben möchten, die kleiner als 3 sind, können Sie die Zahlen mit `Where-Object` folgendermaßen filtern:

```
1,2,3,4 | Where-Object {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a>Filtern basierend auf Objekteigenschaften

Da `$_` auf das aktuelle Pipelineobjekt verweist, können wir für unsere Tests auf seine Eigenschaften zugreifen.

Als Beispiel können wir uns die Klasse **Win32_SystemDriver** in WMI anschauen. Möglicherweise gibt es in einem bestimmten System Hunderte von Systemtreibern, Sie sind aber vielleicht nur an einer bestimmten Auswahl von Systemtreibern interessiert, z. B. an den Treibern, die gerade ausgeführt werden. Für die **Win32_SystemDriver**-Klasse lautet die relevante Eigenschaft **State**. Sie können die Systemtreiber so filtern, dass nur die ausgeführten Treiber ausgewählt werden. Geben Sie dazu Folgendes ein:

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq 'Running'}
```

Dies erzeugt immer noch eine lange Liste. Vielleicht möchten Sie die Liste weiter filtern, um nur die Treiber auszuwählen, die automatisch gestartet werden. Hierzu testen Sie zusätzlich den **StartMode**-Wert:

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Auto"}
```

```Output
DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
...
```

Dadurch erhalten Sie eine Vielzahl von Informationen, die Sie nicht mehr benötigen, da bekannt ist, dass die Treiber ausgeführt werden.
In der Tat sind die einzigen Informationen, die Sie an dieser Stelle wahrscheinlich benötigen, der Name und der Anzeigename. Der folgende Befehl enthält nur diese zwei Eigenschaften, wodurch eine wesentlich vereinfachte Ausgabe erzeugt wird:

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Manual"} |
      Format-Table -Property Name,DisplayName
```

```Output
Name              DisplayName
----              -----------
AsyncMac               RAS Asynchronous Media Driver
bindflt                Windows Bind Filter Driver
bowser                 Browser
CompositeBus           Composite Bus Enumerator Driver
condrv                 Console Driver
HdAudAddService        Microsoft 1.1 UAA Function Driver for High Definition Audio Service
HDAudBus               Microsoft UAA Bus Driver for High Definition Audio
HidUsb                 Microsoft HID Class Driver
HTTP                   HTTP Service
igfx                   igfx
IntcDAud               Intel(R) Display Audio
intelppm               Intel Processor Driver
...
```

Der Befehl oben umfasst zwei `Where-Object`-Elemente, die aber mithilfe des logischen Operators `-and` wie folgt in einem einzigen `Where-Object`-Element ausgedrückt werden können:

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual')} |
    Format-Table -Property Name,DisplayName
```

In der folgenden Tabelle sind die standardmäßigen logischen Operatoren aufgeführt.

| Logischer Operator |                 Bedeutung                  |  Beispiel (gibt „true“ zurück)  |
| ---------------- | ---------------------------------------- | ------------------------ |
| -and             | Logisches „Und“; „true“, wenn beide Seiten zutreffen | (1 -eq 1) -and (2 -eq 2) |
| -or              | Logisches „Oder“; „true“, wenn eine der beiden Seiten zutrifft  | (1 -eq 1) -or (1 -eq 2)  |
| -not             | Logisches „Nicht“; kehrt „true“ und „false“ um     | -not (1 -eq 2)           |
| \!               | Logisches „Nicht“; kehrt „true“ und „false“ um     | \!(1 -eq 2)              |
