# <a name="powershell-core-support-lifecycle"></a>Supportlebenszyklus von PowerShell Core

PowerShell Core ist eine Zusammenstellung von Tools und Komponenten, die separat von Windows PowerShell bereitgestellt, installiert und konfiguriert wird.
PowerShell Core ist daher nicht in den Lizenzvereinbarungen für Windows 7/8.1/10 oder Windows Server enthalten.

PowerShell Core wird jedoch von herkömmlichen Microsoft-Supportvereinbarungen unterstützt, einschließlich [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement] und [Microsoft Software Assurance][assurance].
Sie können auch Hilfe bei der kostenpflichtigen [assisted support (Unterstützter Support)][] für PowerShell Core anfordern.

Auf GitHub wird Ihnen auch [community support (Communitysupport)][] geboten. Dort können Sie Tickets zu Problemen, Fehlern oder Funktionsanfragen stellen.
Alternativ haben Sie die Möglichkeit, sich von anderen Mitgliedern aus der allgemeinen [Microsoft Community][] oder der Microsoft [PowerShell Tech Community][] helfen zu lassen.
Wir bieten keine Garantie, dass ihr Problem zügig behandelt oder behoben wird.
Wenn Sie ein Problem haben, das unmittelbar Aufmerksamkeit erfordert, sollten Sie sich an die herkömmlichen kostenpflichtigen Supportoptionen wenden.

## <a name="lifecycle-of-powershell-core"></a>Lebenszyklus von PowerShell Core

PowerShell Core übernimmt die [Modern Lifecycle-Richtlinie von Microsoft][modern].
Dieser Supportlebenszyklus soll Kunden mit den aktuellsten Versionen auf dem neuesten Stand halten.

Der Branch von Version 6.x von PowerShell Core wird ungefähr alle sechs Monate aktualisiert (z.B. 6.0, 6.1, 6.2, usw.)

> [!IMPORTANT]
> Nach jeder neuen kleinen Versionsfreigabe müssen Sie PowerShell Core innerhalb von sechs Monaten aktualisieren, um weiterhin Unterstützung zu erhalten.

Beispiel: Wenn PowerShell Core 6.1 am 1. Juli 2018 freigegeben wird, würde von Ihnen erwartet werden, dass Sie das Update auf PowerShell Core 6.1 bis zum 1. Januar 2019 ausgeführt haben, damit die Unterstützung aufrecht erhalten wird.

![Lebenszyklus des PowerShell Core-Branchs][lifecycle-chart]

Die Modern Lifecycle-Richtlinie gibt auch vor, dass Microsoft 12 Monate im Voraus bekannt geben muss, wenn die Unterstützung eines Produkts beendet wird (d.h. PowerShell Core).

Letztendlich wird erwartet, dass PowerShell Core den Ansatz der „langfristigen Wartung“ übernimmt, wodurch nur Wartungs- und Sicherheitsupdates erfordert werden, um die Unterstützung eines bestimmten Branchs oder einer bestimmten Version von 6.x aufrecht zu erhalten.

## <a name="supported-platforms"></a>Unterstützte Plattformen

In der folgenden Tabelle erhalten Sie Informationen dazu, welche Plattform für die Version von PowerShell Core, die Sie verwenden, offiziell unterstützt wird.

Unsere Community hat außerdem Pakete für einige Plattformen beigesteuert, die jedoch nicht offiziell unterstützt werden.
Diese Pakete sind in der Tabelle mit `Community` gekennzeichnet.

Plattformen, die als `Experimental` gekennzeichnet sind, werden nicht offiziell unterstützt, stehen aber aus Test- und Feedbackzwecken zur Verfügung.

|                                                   | 6.0         | 6.1         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 und 10                            | Unterstützt   | Unterstützt   |
| Windows Server 2008 R2, 2012 R2, 2016             | Unterstützt   | Unterstützt   |
| [Halbjährlicher Kanal von Windows Server][semi-annual] | Unterstützt   | Unterstützt   |
| Ubuntu 14.04 und 16.04                           | Unterstützt   | Unterstützt   |
| Ubuntu 17.10 und 18.04                           |             | Unterstützt   |
| Debian 8.7 und höher sowie Debian 9                                | Unterstützt   | Unterstützt   |
| CentOS 7                                          | Unterstützt   | Unterstützt   |
| Red Hat Enterprise Linux 7                        | Unterstützt   | Unterstützt   |
| OpenSUSE 42.2                                     | Unterstützt   | Unterstützt   |
| Fedora 27                                         | Unterstützt   | Unterstützt   |
| Fedora 28                                         |             | Unterstützt   |
| macOS 10.12 und höher                                      | Unterstützt   | Unterstützt   |
| Arch                                              | Community   | Community   |
| Raspbian                                          | Experimentell| Community   |
| Kali                                              | Community   | Community   |
| AppImage (funktioniert auf verschiedenen Linux-Plattformen)     | Community   | Community   |

## <a name="platform-which-are-out-of-support"></a>Plattformen, die nicht mehr unterstützt werden

Wenn eine Plattformversion das Ende ihrer Lebensdauer (wie vom Plattformbesitzer festgelegt) erreicht, endet auch die Unterstützung von PowerShell Core für diese Plattformversion. Bereits veröffentlichte Pakete bleiben weiterhin für Kunden verfügbar, die Zugriff benötigen. Die formelle Unterstützung und reguläre Updates jeglicher Art werden nicht mehr veröffentlicht.

Deshalb wurde die Unterstützung für die folgenden Versionen vom Besitzer der Verteilung beendet. Diese werden nicht unterstützt.

| Betriebssystem       | Version | Ende der Lebensdauer                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 26      | [Mai 2018](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| Fedora   | 25      | [Dezember 2017](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 24      | [August 2017](https://fedoramagazine.org/fedora-24-eol/)                                    |
| openSUSE | 42.2    | [Januar 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| openSUSE | 42.1    | [Mai 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| Ubuntu   | 17.04   | [Januar 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 16.10   | [Juli 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |

## <a name="notes-on-licensing"></a>Hinweise zur Lizenzierung

PowerShell Core wird unter der [MIT license (MIT-Lizenz)][] veröffentlicht.
Unter dieser Lizenz und in Abwesenheit einer kostenpflichtigen Supportvereinbarung gibt es für die Benutzer nur den [community support (Communitysupport)][].
Beim Support durch die Community gibt Microsoft keine Garantien zur Schnelligkeit der Reaktion auf Ihre Tickets oder der Problembehandlung.

## <a name="windows-powershell-module"></a>Windows PowerShell-Modul

Die Unterstützung von PowerShell Core gilt nicht für andere Produktmodule, es sei denn, diese Module unterstützen PowerShell Core ausdrücklich.
Zum Beispiel wird das Modul `ActiveDirectory`, das als Teil von Windows Server bereitgestellt wird, nicht unterstützt.

Allerdings können auch Module, die PowerShell Core nicht explizit unterstützen, in manchen Fällen kompatibel sein.
Durch die Installation des Moduls [`WindowsPSModulePath`][] können Sie `PSModulePath` von Windows PowerShell an `PSModulePath` von PowerShell Core anfügen.

Installieren Sie zunächst das `WindowsPSModulePath`-Modul aus dem PowerShell-Katalog:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Führen Sie nach der Installation dieses Moduls das Cmdlet `Add-WindowsPSModulePath` aus, um `PSModulePath` aus Windows PowerShell zu PowerShell Core hinzuzufügen:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[community support (Communitysupport)]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[assisted support (Unterstützter Support)]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT license (MIT-Lizenz)]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
