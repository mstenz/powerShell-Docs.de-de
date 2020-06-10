---
title: Formatierung, Aliase, Anbieter, Vergleich
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: eb23b048a50f10ea83d156c0499772b1be439336
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438001"
---
# <a name="chapter-5---formatting-aliases-providers-comparison"></a>Kapitel 5: Formatierung, Aliase, Anbieter, Vergleich

## <a name="requirements"></a>Requirements (Anforderungen)

Das SQL Server PowerShell-Modul ist für einige der in diesem Kapitel gezeigten Beispiele erforderlich. Das Modul wird als Bestandteil von [SQL Server Management Studio (SSMS)][SMSS] installiert. Es wird auch in nachfolgenden Kapiteln verwendet. Laden Sie es auf Ihren Windows 10-Laborumgebungscomputer herunter, und installieren Sie es.

## <a name="format-right"></a>Rechts formatieren

In Kapitel 4 haben Sie gelernt, so weit wie möglich nach links zu filtern. Die Regel für manuelles Formatieren der Ausgabe eines Befehls ähnelt dieser Regel, außer dass sie so weit wie möglich auf der rechten Seite vorkommen muss.

Die gängigsten Formatierungsbefehle sind `Format-Table` und `Format-List`. `Format-Wide` und `Format-Custom` können auch verwendet werden, sind jedoch weniger gängig.

Wie in Kapitel 3 erwähnt, wird ein Befehl, der mehr als vier Eigenschaften zurückgibt, standardmäßig zu einer Liste, wenn keine benutzerdefinierte Formatierung verwendet wird.

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```Output
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

Verwenden Sie das Cmdlet `Format-Table`, um die Formatierung manuell außer Kraft zu setzen und die Ausgabe in einer Tabelle anstatt in einer Liste anzuzeigen.

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can* |
Format-Table
```

```Output
 Status DisplayName  CanPauseAndContinue CanShutdown CanStop
 ------ -----------  ------------------- ----------- -------
Running Windows Time               False        True    True
```

Die Standardausgabe für `Get-Service` sind drei Eigenschaften in einer Tabelle.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

Verwenden Sie das Cmdlet `Format-List`, um die Standardformatierung außer Kraft zu setzen und die Ergebnisse in einer Liste zurückzugeben.

```powershell
Get-Service -Name w32time | Format-List
```

```Output
Name                : w32time
DisplayName         : Windows Time
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
ServiceType         : Win32ShareProcess
```

Beachten Sie, dass durch das einfache Weiterleiten von `Get-Service` an `Format-List` per Pipeline zusätzliche Eigenschaften zurückgegeben wurden. Dies tritt nicht bei jedem Befehl auf, was an der Weise liegt, in der die Art der Formatierung für diesen bestimmten Befehl im Hintergrund eingerichtet ist.

Die Hauptsache, derer Sie sich bei den Formatierungs-Cmdlets bewusst sein sollten, ist, dass sie Formatobjekte erzeugen, die sich von normalen Objekten in PowerShell unterscheiden.

```powershell
Get-Service -Name w32time | Format-List | Get-Member
```

```Output
   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
autosizeInfo                            Property   Microsoft.PowerShell.Commands.Inter...
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
pageFooterEntry                         Property   Microsoft.PowerShell.Commands.Inter...
pageHeaderEntry                         Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEntryData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
formatEntryInfo                         Property   Microsoft.PowerShell.Commands.Inter...
outOfBand                               Property   bool outOfBand {get;set;}
writeStream                             Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
```

Dies bedeutet, dass Formatierungsbefehle nicht per Pipeline an die meisten anderen Befehle weitergeleitet werden können. Sie können per Pipeline an einige der `Out-*`-Befehle weitergeleitet werden, aber das ist es auch schon. Aus diesem Grund sollten Sie jegliche Formatierung am Ende der Zeile (rechts formatieren) vornehmen.

## <a name="aliases"></a>Aliase

Ein Alias ist in PowerShell ein kürzerer Name für einen Befehl. PowerShell umfasst eine Reihe von integrierten Aliasnamen, doch Sie können auch eigene Aliase definieren.

Mit dem Cmdlet `Get-Alias` können Sie Aliase abrufen. Wenn Sie den Alias für einen Befehl bereits kennen, wird der Parameter **Name** verwendet, um zu bestimmen, welchem Befehl der Alias zugeordnet ist.

```powershell
Get-Alias -Name gcm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
```

Für den Wert des Parameters **Name** können mehrere Aliase angegeben werden.

```powershell
Get-Alias -Name gcm, gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

Sie werden häufig feststellen, dass der Parameter **Name** ausgelassen wird, weil es sich um einen Positionsparameter handelt.

```powershell
Get-Alias gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gm -> Get-Member
```

Wenn Sie Aliase für einen Befehl suchen möchten, müssen Sie den Parameter **Definition** verwenden.

```powershell
Get-Alias -Definition Get-Command, Get-Member
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

Der Parameter **Definition-** kann nicht als Positionsparameter verwendet werden, weshalb er angegeben werden muss.

Aliase können Ihnen ein paar Tastatureingaben ersparen und sind gut geeignet, wenn Sie Befehle in die Konsole eingeben.
Sie sollten nicht in Skripts oder Code verwendet werden, die bzw. den Sie speichern oder mit anderen teilen. Wie in diesem Buch bereits erwähnt, ist die Verwendung vollständiger Cmdlet- und Parameternamen selbsterklärend und leichter zu verstehen.

Gehen Sie beim Erstellen Ihrer eigenen Aliase mit Bedacht vor, da Sie nur in Ihrer aktuellen PowerShell-Sitzung auf Ihrem Computer existieren.

## <a name="providers"></a>Anbieter

Ein Anbieter ist in PowerShell eine Schnittstelle, die einen dateisystemähnlichen Zugriff auf einen Datenspeicher zulässt. Es gibt eine Reihe integrierter Anbieter in PowerShell.

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
Certificate          ShouldProcess                      {Cert}
WSMan                Credentials                        {WSMan}
```

Wie Sie in den vorherigen Ergebnissen sehen können, gibt es integrierte Anbieter für die Registrierung, für Aliase, Umgebungsvariablen, das Dateisystem, Funktionen, Variablen, Zertifikate und WSMan.

Die tatsächlichen Laufwerke, die diese Anbieter verwenden, um Ihren jeweiligen Datenspeicher verfügbar zu machen, können Sie mit dem Cmdlet `Get-PSDrive` ermitteln. Das Cmdlet `Get-PSDrive` zeigt nicht nur Laufwerke an, die von Anbietern verfügbar gemacht werden, sondern auch logische Windows-Laufwerke, einschließlich Laufwerken, die Netzwerkfreigaben zugeordnet sind.

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
Alias                                  Alias
C                  14.41        112.10 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
WSMan                                  WSMan
```

Module von Drittanbietern wie das Active Directory PowerShell-Modul und das SQLServer PowerShell-Modul fügen sowohl einen eigenen PowerShell-Anbieter als auch ein PSDrive hinzu.

Importieren Sie die Active Directory- und SQL Server PowerShell-Module.

```powershell
Import-Module -Name ActiveDirectory, SQLServer
```

Überprüfen Sie, ob zusätzliche PowerShell-Anbieter hinzugefügt wurden.

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
ActiveDirectory      Include, Exclude, Filter, Shoul... {AD}
SqlServer            Credentials                        {SQLSERVER}
```

Beachten Sie, dass im vorherigen Resultset jetzt zwei neue PowerShell-Anbieter vorhanden sind, einer für Active Directory und einer für SQL Server.

Ein PSDrive für jedes dieser Module wurde ebenfalls hinzugefügt.

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
AD                                     ActiveDire... //RootDSE/
Alias                                  Alias
C                  19.38        107.13 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
SQLSERVER                              SqlServer     SQLSERVER:\
Variable                               Variable
WSMan                                  WSMan
```

Der Zugriff auf PSDrives erfolgt genauso wie auf ein herkömmliches Dateisystem.

```powershell
Get-ChildItem -Path Cert:\LocalMachine\CA
```

```Output
   PSParentPath: Microsoft.PowerShell.Security\Certificate::LocalMachine\CA

Thumbprint                                Subject
----------                                -------
FEE449EE0E3965A5246F000E87FDE2A065FD89D4  CN=Root Agency
D559A586669B08F46A30A133F8A9ED3D038E2EA8  OU=www.verisign.com/CPS Incorporated LIABI...
109F1CAED645BB78B3EA2B94C0697C740733031C  CN=Microsoft Windows Hardware Compatibility,...
```

## <a name="comparison-operators"></a>Vergleichsoperatoren

PowerShell enthält eine Reihe von Vergleichsoperatoren, die verwendet werden, um Werte zu vergleichen oder um Werte zu suchen, die bestimmten Mustern entsprechen. Tabelle 5-1 enthält eine Liste der Vergleichsoperatoren in PowerShell.

|    Operator    |                          Definition                          |
| -------------- | ------------------------------------------------------------ |
| `-eq`          | Gleich                                                     |
| `-ne`          | Ungleich                                                 |
| `-gt`          | Größer als                                                 |
| `-ge`          | Größer als oder gleich                                     |
| `-lt`          | Kleiner als                                                    |
| `-le`          | Kleiner als oder gleich                                        |
| `-Like`        | Entspricht unter Verwendung des Platzhalterzeichens `*`                       |
| `-NotLike`     | Entspricht nicht unter Verwendung des Platzhalterzeichens `*`              |
| `-Match`       | Entspricht dem angegebenen regulären Ausdruck.                     |
| `-NotMatch`    | Entspricht nicht dem angegebenen regulären Ausdruck.              |
| `-Contains`    | Bestimmt, ob eine Sammlung einen angegebenen Wert enthält.        |
| `-NotContains` | Bestimmt, ob die Auflistung einen bestimmten Wert nicht enthält. |
| `-In`          | Bestimmt, ob sich ein angegebener Wert in einer Sammlung befindet.           |
| `-NotIn`       | Bestimmt, ob sich ein angegebener Wert nicht in einer Sammlung befindet.       |
| `-Replace`     | Ersetzt den angegebenen Wert.                                 |

Bei allen in Tabelle 5-1 aufgelisteten Operatoren wird die Groß-/Kleinschreibung nicht beachtet. Stellen Sie dem in Tabelle 5-1 aufgelisteten Operator ein `c` voran, damit die Groß-/Kleinschreibung beachtet wird. Beispielsweise ist `-ceq` die Version des Vergleichsoperators `-eq`, bei der die Groß-/Kleinschreibung beachtet wird.

„PowerShell“ in gemischter Schreibweise ist gleich der Variante in Kleinbuchstaben „powershell“, wenn der Vergleichsoperator „ gleich“ verwendet wird.

```powershell
'PowerShell' -eq 'powershell'
```

```Output
True
```

Es ist nicht gleich, wenn die Variante des Vergleichsoperators „gleich“ mit Beachtung der Groß-/Kleinschreibung verwendet wird.

```powershell
'PowerShell' -ceq 'powershell'
```

```Output
False
```

Der Vergleichsoperator „ungleich“ kehrt die Bedingung um.

```powershell
'PowerShell' -ne 'powershell'
```

```Output
False
```

„Größer als“, „Größer als oder gleich“, „Kleiner als“ und „Kleiner als oder gleich“ funktionieren alle mit Zeichenfolgen- und mit Zahlenwerten.

```powershell
5 -gt 5
```

```Output
False
```

Die Verwendung von „Größer als oder gleich“ anstelle von „Größer als“ im vorherigen Beispiel gibt den **booleschen Wert** „true“ zurück, da fünf gleich fünf ist.

```powershell
5 -ge 5
```

```Output
True
```

Basierend auf den Ergebnissen der beiden vorherigen Beispiele können Sie wahrscheinlich erraten, wie die Operatoren „Kleiner als“ und „Kleiner als oder gleich“ funktionieren.

```powershell
5 -lt 10
```

```Output
True
```

Die Operatoren `-Like` und `-Match` können verwirrend sein, selbst für erfahrene PowerShell-Benutzer. `-Like` wird mit den Platzhalterzeichen `*` und `?` verwendet, um „wie“-Vergleiche auszuführen.

```powershell
'PowerShell' -like '*shell'
```

```Output
True
```

`-Match` verwendet einen regulären Ausdruck, um den Vergleich durchzuführen.

```powershell
'PowerShell' -match '^*.shell$'
```

```Output
True
```

Verwenden Sie den Bereichsoperator (range), um die Zahlen 1 bis 10 in einer Variablen zu speichern.

```powershell
$Numbers = 1..10
```

```Output
```

Bestimmen Sie, ob die Variable `$Numbers` 15 enthält.

```powershell
$Numbers -contains 15
```

```Output
False
```

Bestimmen Sie, ob sie die Zahl 10 enthält.

```powershell
$Numbers -contains 10
```

```Output
True
```

`-NotContains` kehrt die Logik um, um festzustellen, ob die `$Numbers` Variable einen Wert nicht enthält.

```powershell
$Numbers -notcontains 15
```

```Output
True
```

Im vorherigen Beispiel wird der **boolesche Wert** „true“ zurückgegeben, da es zutrifft, dass die Variable `$Numbers` 15 nicht enthält. Sie enthält jedoch die Zahl 10, sodass beim Testen das Ergebnis „false“ ist.

```powershell
$Numbers -notcontains 10
```

```Output
False
```

Der Vergleichsoperator „in“ wurde erstmals in PowerShell-Version 3.0 eingeführt. Er wird verwendet, um zu bestimmen, ob sich ein Wert in einem Array befindet. Die Variable `$Numbers` ist ein Array, da sie mehrere Werte enthält.

```powershell
15 -in $Numbers
```

```Output
False
```

Mit anderen Worten: `-in` führt denselben Test wie der Vergleichsoperator „enthält“ (contains) aus, mit der Ausnahme, dass er von der entgegengesetzten Richtung aus arbeitet.

```powershell
10 -in $Numbers
```

```Output
True
```

15 befindet sich nicht im Array `$Numbers`, weshalb im folgenden Beispiel „false“ zurückgegeben wird.

```powershell
15 -in $Numbers
```

```Output
False
```

Ebenso wie der Operator `-contains`, kehrt `not` die Logik für den Operator `-in` um.

```powershell
10 -notin $Numbers
```

```Output
False
```

Im vorherigen Beispiel wird „false“ zurückgegeben, weil das Array `$Numbers` 10 enthält und die Bedingung in einem Test bestand, um zu ermitteln, ob es 10 nicht enthält.

15 befindet sich „nicht in“ dem Array `$Numbers`, weshalb der **boolesche Wert** „true“ zurückgegeben wird.

```powershell
15 -notin $Numbers
```

```Output
True
```

Der Operator `-replace` macht genau das, woran Sie denken. Er wird verwendet, um etwas zu ersetzen. Wenn Sie nur einen Wert angeben, wird dieser Wert durch nichts ersetzt. Im folgenden Beispiel wird „Shell“ durch nichts ersetzt.

```powershell
'PowerShell' -replace 'Shell'
```

```Output
Power
```

Wenn Sie einen Wert durch einen anderen Wert ersetzen möchten, geben Sie den neuen Wert hinter dem Muster an, das Sie ersetzen möchten. „SQL Saturday in Baton Rouge“ ist ein Ereignis, bei dem ich jedes Jahr versuche, zu sprechen. Im folgenden Beispiel ersetze ich das Wort „Saturday“ durch die Abkürzung „Sat“.

```powershell
'SQL Saturday - Baton Rouge' -Replace 'saturday','Sat'
```

```Output
SQL Sat - Baton Rouge
```

Es gibt auch Methoden wie **Replace()** , die zum Ersetzen von Elementen verwendet werden können, die der Art und Weise ähneln, wie der replace-Operator funktioniert. Der Operator `-Replace` beachtet jedoch standardmäßig nicht die Groß-und Kleinschreibung, die **Replace()** -Methode hingegen berücksichtigt die Groß-/Kleinschreibung.

```powershell
'SQL Saturday - Baton Rouge'.Replace('saturday','Sat')
```

```Output
SQL Saturday - Baton Rouge
```

Beachten Sie, dass das Wort „Saturday“ im vorherigen Beispiel nicht ersetzt wurde. Dies liegt daran, dass es mit anderer Groß-/Kleinschreibung als das Original angegeben wurde. Wenn das Wort „Saturday“ in derselben Groß-/Kleinschreibung wie das Original angegeben wird, ersetzt die **Replace()** -Methode es wie erwartet.

```powershell
'SQL Saturday - Baton Rouge'.Replace('Saturday','Sat')
```

```Output
SQL Sat - Baton Rouge
```

Gehen Sie bei der Verwendung von Methoden zum Transformieren von Daten vorsichtig vor, da Sie auf unvorhergesehene Probleme stoßen können, z. B. das Nichtbestehen des _Turkey-Tests_. Ein Beispiel finden Sie in dem Blogartikel [Verwenden von Pester zum Testen von PowerShell-Code mit anderen Kulturen][]. Meine Empfehlung ist es, einen Operator anstelle einer Methode zu verwenden, wenn dies möglich ist, um diese Art von Problemen zu vermeiden.

Obwohl die Vergleichsoperatoren wie in den vorherigen Beispielen gezeigt verwendet werden können, verwende ich sie doch in der Regel mit dem Cmdlet `Where-Object`, um eine Art von Filterung durchzuführen.

## <a name="summary"></a>Zusammenfassung

In diesem Kapitel haben Sie eine Reihe unterschiedlicher Themen kennengelernt, nämlich „Rechts formatieren“, „Aliase“, „Anbieter“ und „Vergleichsoperatoren“.

## <a name="review"></a>Überprüfung

1. Warum ist es notwendig, die Formatierung so weit wie möglich rechts durchzuführen?
1. Wie bestimmen Sie, wie das tatsächliche Cmdlet zum Alias `%` lautet?
1. Warum sollten Sie keine Aliase in Skripts verwenden, die Sie speichern, oder in Code, den Sie mit anderen teilen?
1. Führen Sie eine Verzeichnisauflistung auf den Laufwerken durch, die einem der Registrierungsanbieter zugeordnet sind.
1. Was ist einer der Hauptvorteile bei der Verwendung des replace-Operators anstelle der Replace-Methode?

## <a name="recommended-reading"></a>Empfohlene Lektüre

- [Format-Table][]
- [Format-List][]
- [Format-Wide][]
- [about_Aliases][]
- [about_Providers][]
- [about_Comparison_Operators][]
- [about_Arrays][]

<!-- link references -->
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
[Format-Table]: /powershell/module/microsoft.powershell.utility/format-table
[Format-List]: /powershell/module/microsoft.powershell.utility/format-list
[Format-Wide]: /powershell/module/microsoft.powershell.utility/format-wide
[about_Aliases]: /powershell/module/microsoft.powershell.core/about/about_aliases
[about_Providers]: /powershell/module/microsoft.powershell.core/about/about_providers
[about_Comparison_Operators]: /powershell/module/microsoft.powershell.core/about/about_comparison_operators
[about_Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Verwenden von Pester zum Testen von PowerShell-Code mit anderen Kulturen]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/
