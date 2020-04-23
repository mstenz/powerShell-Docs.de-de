---
ms.date: 11/22/2019
keywords: powershell,cmdlet
title: Verwenden von „Format“-Befehlen zum Ändern der Ausgabeanzeige
ms.openlocfilehash: f270d5ec5efe5caf506d6a8a45285990996f6ae6
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "74417591"
---
# <a name="using-format-commands-to-change-output-view"></a>Verwenden von „Format“-Befehlen zum Ändern der Ausgabeanzeige

PowerShell umfasst eine Reihe von Cmdlets, mit denen Sie steuern können, wie Eigenschaften für bestimmte Objekte angezeigt werden. Der Name jedes dieser Cmdlets beginnt mit dem Verb `Format`. Mit diesen können Sie auswählen, welche Eigenschaften angezeigt werden sollen.

```powershell
Get-Command -Verb Format -Module Microsoft.PowerShell.Utility
```

```Output
CommandType     Name               Version    Source
-----------     ----               -------    ------
Cmdlet          Format-Custom      6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Hex         6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-List        6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Table       6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Wide        6.1.0.0    Microsoft.PowerShell.Utility
```

In diesem Artikel werden die Cmdlets `Format-Wide`, `Format-List` und `Format-Table` näher erläutert.

Jeder Objekttyp in PowerShell besitzt Standardeigenschaften, die verwendet werden, wenn Sie nicht festlegen, welche Eigenschaften angezeigt werden sollen. Für jedes Cmdlet wird außerdem derselbe **Property-Parameter** verwendet, um anzugeben, welche Eigenschaften angezeigt werden sollen. Weil `Format-Wide` nur eine einzelne Eigenschaft anzeigt, übernimmt deren **Property-Parameter** nur einen einzelnen Wert, wogegen die Property-Parameter von `Format-List` und `Format-Table` eine Liste von Eigenschaftsnamen akzeptieren.

In diesem Beispiel gibt die Standardausgabe des Cmdlets `Get-Process` an, dass zwei Instanzen von Internet Explorer ausgeführt werden.

```powershell
Get-Process -Name iexplore
```

Das Standardformat für **Prozessobjekte** zeigt die folgenden Eigenschaften an:

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     32    25.52      10.25      13.11   12808   1 iexplore
     52    11.46      26.46       3.55   21748   1 iexplore
```

## <a name="using-format-wide-for-single-item-output"></a>Verwenden von „Format-Wide“ für die Ausgabe eines einzelnen Elements

Das Cmdlet `Format-Wide` zeigt standardmäßig nur die Standardeigenschaft eines Objekts an. Die Informationen, die zu dem jeweiligen Objekt gehören, werden in einer einzelnen Spalte angezeigt:

```powershell
Get-Command -Verb Format | Format-Wide
```

```Output
Format-Custom          Format-Hex
Format-List            Format-Table
Format-Wide
```

Sie können auch eine nicht standardmäßige Eigenschaft angeben:

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```Output
Custom                 Hex
List                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a>Steuern der „Format-Wide“-Anzeige mit Spalte

Mit dem Cmdlet `Format-Wide` können Sie immer nur jeweils eine Eigenschaft anzeigen. Dadurch ist es zum Anzeigen großer Listen in mehreren Spalten nützlich.

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 3
```

```Output
Custom                 Hex                  List
Table                  Wide

```

## <a name="using-format-list-for-a-list-view"></a>Verwenden von „Format-List“ für eine Listenansicht

Das Cmdlet `Format-List` zeigt ein Objekt in Form einer Auflistung an, wobei jede Eigenschaft in einer eigenen Zeile beschriftet und angezeigt wird:

```powershell
Get-Process -Name iexplore | Format-List
```

```Output
Id      : 12808
Handles : 578
CPU     : 13.140625
SI      : 1
Name    : iexplore

Id      : 21748
Handles : 641
CPU     : 3.59375
SI      : 1
Name    : iexplore
```

Sie können Sie beliebig viele Eigenschaften angeben:

```powershell
Get-Process -Name iexplore | Format-List -Property ProcessName,FileVersion,StartTime,Id
```

```Output
ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:58 AM
Id          : 12808

ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:57 AM
Id          : 21748
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>Abrufen von ausführliche Informationen durch Verwenden von „Format-List“ mit Platzhaltern

Das Cmdlet `Format-List` ermöglicht es, einen Platzhalter als Wert für den **Property-Parameter** zu verwenden. Dies ermöglicht es Ihnen, ausführliche Informationen anzuzeigen. Häufig enthalten Objekte mehr Informationen als Sie benötigen. Dies ist der Grund, warum PowerShell nicht standardmäßig alle Eigenschaftswerte anzeigt. Verwenden Sie den Befehl `Format-List -Property *`, um alle Eigenschaften eines Objekts anzuzeigen. Der folgende Befehl generiert mehr als 60 Zeilen an Ausgabe für einen einzelnen Prozess:

```powershell
Get-Process -Name iexplore | Format-List -Property *
```

Obwohl der Befehl `Format-List` nützlich ist, um Details anzuzeigen, ist eine einfachere Tabellenansicht oft nützlicher, wenn Sie einen Überblick über eine Ausgabe wünschen, die viele Elemente enthält.

## <a name="using-format-table-for-tabular-output"></a>Verwenden von „Format-Table“ für tabellarische Ausgabe

Falls Sie die Ausgabe des Befehls `Format-Table` mit dem Cmdlet `Get-Process` ohne angegebene Eigenschaftennamen formatieren, erhalten Sie genau dieselbe Ausgabe wie ohne das Cmdlet `Format`. Standardmäßig zeigt PowerShell **Prozessobjekte** im Tabellenformat an.

```powershell
Get-Service -Name win* | Format-Table
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  WinHttpAutoProx... WinHTTP Web Proxy Auto-Discovery Se...
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Manag...
```

### <a name="improving-format-table-output-autosize"></a>Verbessern der „Format-Table“-Ausgabe (AutoSize)

Eine Tabellenansicht ist zwar zum Anzeigen großer Informationsmengen nützlich, kann aber zu Interpretationsschwierigkeiten führen, wenn die Anzeige zu schmal für die Daten ist. Im vorherigen Beispiel ist die Ausgabe abgeschnitten. Falls Sie den **AutoSize-Parameter** angeben, wenn Sie den Befehl `Format-Table` ausführen, berechnet PowerShell die Spaltenbreiten anhand der tatsächlich angezeigten Daten. Dadurch werden die Spalten lesbar.

```powershell
Get-Service -Name win* | Format-Table -AutoSize
```

```Output
Status  Name                DisplayName
------  ----                -----------
Running WinDefend           Windows Defender Antivirus Service
Running WinHttpAutoProxySvc WinHTTP Web Proxy Auto-Discovery Service
Running Winmgmt             Windows Management Instrumentation
Running WinRM               Windows Remote Management (WS-Management)
```

Im Cmdlet `Format-Table` werden möglicherweise weiterhin Daten abgeschnitten, aber nur am Ende des Bildschirms. Jede Eigenschaft außer der letzten angezeigten Eigenschaft erhält so viel Breite, wie erforderlich ist, damit ihr längstes Datenelement richtig angezeigt wird.

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -AutoSize
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc, iphl…
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms, TPHKLO…
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

Der Befehl `Format-Table` geht davon aus, dass Eigenschaften nach Wichtigkeit aufgelistet werden. Daher wird im Befehl versucht, die Eigenschaften, die dem Anfang am nächsten sind, vollständig anzuzeigen. Wenn der Befehl `Format-Table` nicht alle Eigenschaften anzeigen kann, entfernt er einige Spalten aus der Anzeige. Dieses Verhalten wird im vorherigen Beispiel mit der **DependentServices-Eigenschaft** veranschaulicht.

### <a name="wrapping-format-table-output-in-columns-wrap"></a>Umbrechen von „Format-Table“-Ausgabe in Spalten (Wrap)

Sie können erzwingen, dass zu lange `Format-Table`-Daten innerhalb ihrer Anzeigespalte umbrochen werden, indem Sie den **Wrap-Parameter** verwenden. Das Verwenden des **Wrap-Parameters** führt möglicherweise nicht zum von Ihnen erwarteten Ergebnis, weil die Standardeinstellungen verwendet werden, wenn Sie nicht auch **AutoSize** angeben:

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -Wrap
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc,
                                                                                iphlpsvc}
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms,
                                                                                TPHKLOAD,
                                                                                SUService,
                                                                                smstsmgr…}
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

Die Verwendung des **Wrap-Parameters** an sich verlangsamt die Verarbeitung kaum. Wenn Sie **AutoSize** für das Formatieren einer rekursiven Dateiliste einer großen Verzeichnisstruktur verwenden, kann dieser Vorgang viel Zeit und Arbeitsspeicher in Anspruch nehmen, bevor die ersten Ausgabeelemente angezeigt werden.

Wenn die Systemauslastung keine Rolle spielt, funktioniert **AutoSize** gut mit dem **Wrap-Parameter**.
Die ursprünglichen Spalten verwenden weiterhin so viel Breite wie erforderlich, um Elemente in einer Zeile anzuzeigen, aber die letzte Spalte wird ggf. umschlossen.

> [!NOTE]
> Einige Spalten werden möglicherweise nicht angezeigt, wenn Sie zuerst die breiteste Spalte angeben. Geben Sie für optimale Ergebnisse zuerst die kleinsten Datenelemente an.

Im folgenden Beispiel werden die breitesten Eigenschaften zuerst angegeben.

```powershell
Get-Process -Name iexplore | Format-Table -Wrap -AutoSize -Property FileVersion,Path,Name,Id
```

Selbst mit Umschließung wird die letzte **Id**-Spalte ausgelassen:

```Output
FileVersion                          Path                                                  Nam
                                                                                           e
-----------                          ----                                                  ---
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files (x86)\Internet Explorer\IEXPLORE.EXE iex
                                                                                           plo
                                                                                           re
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files\Internet Explorer\iexplore.exe       iex
                                                                                           plo
                                                                                           re
```

### <a name="organizing-table-output--groupby"></a>Ordnen von Tabellenausgabe (-GroupBy)

Eine weiterer nützlicher Parameter für das Steuern von tabellarischer Ausgabe ist **GroupBy**. Es kann insbesondere schwierig sein, längere tabellarische Auflistungen zu vergleichen. Mit dem **GroupBy**Parameter wird die Ausgabe anhand eines Eigenschaftswerts gruppiert. Beispielsweise können Dienste zur einfacheren Überprüfung nach **StartType** gruppiert werden. Dadurch wird der **StartType**-Wert aus der Eigenschaftenliste entfernt:

```powershell
Get-Service -Name win* | Sort-Object StartType | Format-Table -GroupBy StartType
```

```Output
   StartType: Automatic
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Managem…

   StartType: Manual
Status   Name               DisplayName
------   ----               -----------
Running  WinHttpAutoProxyS… WinHTTP Web Proxy Auto-Discovery Serv…
```
