---
ms.date: 08/23/2018
keywords: powershell,cmdlet
title: Grundlegendes zu PowerShell-Modulen
ms.openlocfilehash: 3033a4fe1a704fbbfa76e6d38662c8b22c3dbd9b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030380"
---
# <a name="understanding-pipelines"></a>Grundlegendes zu Pipelines

Eine Pipeline fungiert als eine Reihe von verbundenen Segmenten eines Rohrs. Elemente, die durch die Pipeline geleitet werden, durchlaufen jedes Segment. Um eine Pipeline in PowerShell zu erstellen, verbinden Sie Befehle mit dem Pipeoperator „|“. Die Ausgabe eines Befehls wird als Eingabe des nächsten Befehls verwendet.

Die Notation für Pipelines ist der Notation in anderen Shells ähnlich. Auf den ersten Blick ist es möglicherweise nicht offensichtlich, wie sich Pipelines in PowerShell unterscheiden. Obwohl Text auf dem Bildschirm angezeigt wird, leitet PowerShell Objekte und keinen Text zwischen Befehlen weiter.

## <a name="the-powershell-pipeline"></a>Die PowerShell-Pipeline

Pipelines sind wohl das wertvollste Konzept, das Befehlszeilenschnittstellen verwendet wird. Bei richtigem Einsatz verringern Pipelines den Aufwand durch die Verwendung von komplexen Befehlen und erleichtern es, den Ablauf der Befehle zu sehen. Jeder Befehl in einer Pipeline (wird als Pipelineelement bezeichnet) übergibt seine Ausgabe elementweise an den nächsten Befehl in der Pipeline. Befehle müssen jeweils nur ein Element zurzeit verarbeiten. Das Ergebnis ist eine verringerte Ressourcennutzung und die Möglichkeit, die Ausgabe unmittelbar zu erhalten.

Wenn Sie beispielsweise das Cmdlet `Out-Host` zum Erzwingen einer seitenweisen Anzeige der Ausgabe eines anderen Befehls verwenden, sieht die Ausgabe wie der normale auf dem Bildschirm gezeigte Text aus, der in Seiten unterteilt ist:

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

Durch die Einteilung in Seiten wird auch die CPU-Auslastung reduziert, da die Verarbeitung an das Cmdlet `Out-Host` übertragen wird, wenn eine vollständige Seite für die Anzeige bereit ist. Die Cmdlets, die sich in der Pipeline davor befinden, unterbrechen die Ausführung, bis die nächste Seite der Ausgabe verfügbar ist.

Sie können im Windows Task-Manager sehen, wie sich Piping auf die CPU- und Arbeitsspeicherauslastung auswirkt, indem Sie die folgenden Befehle vergleichen:

- `Get-ChildItem C:\Windows -Recurse`
- `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`

> [!NOTE]
> Der **Paging**-Parameter wird nicht von allen PowerShell-Hosts unterstützt. Wenn Sie z.B. versuchen, den **Paging**-Parameter in der PowerShell-ISE zu verwenden, wird folgende Fehlermeldung angezeigt:
>
> ```Output
> out-lineoutput : The method or operation is not implemented.
> At line:1 char:1
> + Get-ChildItem C:\Windows -Recurse | Out-Host -Paging
> + ~~~~~~~~~~~~~~~~~~~~~~~~~~~
>     + CategoryInfo          : NotSpecified: (:) [out-lineoutput], NotImplementedException
>     + FullyQualifiedErrorId : System.NotImplementedException,Microsoft.PowerShell.Commands.OutLineOutputCommand
> ```

## <a name="objects-in-the-pipeline"></a>Objekte in der Pipeline

Wenn Sie ein Cmdlet in PowerShell ausführen, sehen Sie eine Textausgabe, da es erforderlich ist, Objekte in einem Konsolenfenster als Text darzustellen. Die Textausgabe enthält möglicherweise nicht alle Eigenschaften des Objekts, das ausgegeben wird.

Betrachten Sie beispielsweise das Cmdlet `Get-Location`. Bei der Ausführung von `Get-Location`, während Ihr aktueller Speicherort der Stamm von Laufwerk C: ist, sehen Sie die folgende Ausgabe:

```
PS> Get-Location

Path
----
C:\
```

Die Textausgabe ist eine Zusammenfassung der Informationen, keine vollständige Darstellung des Objekts, das von `Get-Location` zurückgegeben wird. Die Überschrift in der Ausgabe wird durch den Prozess hinzugefügt, der die Daten für die Anzeige auf dem Bildschirm formatiert.

Wenn Sie die Ausgabe an das Cmdlet `Get-Member` weiterleiten, erhalten Sie Informationen über das Objekt, das von `Get-Location` zurückgegeben wird.

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

`Get-Location` gibt ein **PathInfo**-Objekt zurück, das den aktuellen Pfad und andere Informationen enthält.
