---
title: Supportlebenszyklus von PowerShell Core
description: Richtlinien für die Unterstützung von PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 60999ed54ca3be15232ffee3ab0c49cb94873a8f
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986747"
---
# <a name="powershell-core-support-lifecycle"></a>Supportlebenszyklus von PowerShell Core

PowerShell Core ist eine Zusammenstellung von Tools und Komponenten, die separat von Windows PowerShell bereitgestellt, installiert und konfiguriert wird. PowerShell Core wird daher nicht in den Lizenzvereinbarungen für Windows 7/8.1/10 oder Windows Server aufgeführt.

PowerShell Core wird jedoch von herkömmlichen Microsoft-Supportvereinbarungen abgedeckt, darunter [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement] und [Microsoft Software Assurance][assurance].
Sie können auch Hilfe bei der kostenpflichtigen [unterstützten Support][] für PowerShell Core anfordern.

## <a name="community-support"></a>Communitysupport

Auf GitHub wird Ihnen auch [Communitysupport][] geboten. Dort können Sie Tickets zu Problemen, Fehlern oder Funktionsanfragen stellen.
Sie haben auch die Möglichkeit, sich von anderen Mitgliedern aus der allgemeinen [Microsoft Community][] oder der Microsoft [PowerShell Tech Community][] helfen zu lassen. Wir bieten keine Garantie, dass die Community Ihr Problem zügig behandelt oder behebt. Wenn Sie ein Problem haben, das unmittelbar Aufmerksamkeit erfordert, sollten Sie sich an die herkömmlichen kostenpflichtigen Supportoptionen wenden.

## <a name="lifecycle-of-powershell-core"></a>Lebenszyklus von PowerShell Core

PowerShell Core übernimmt die [Modern Lifecycle-Richtlinie von Microsoft][modern]. Dieser Supportlebenszyklus soll Kunden mit den aktuellsten Versionen auf dem neuesten Stand halten.

Der Branch von Version 6.x von PowerShell Core wird ungefähr alle sechs Monate aktualisiert (z.B. 6.0, 6.1, 6.2, etc.).

> [!IMPORTANT]
> Nach jeder neuen kleinen Versionsfreigabe müssen Sie PowerShell Core innerhalb von sechs Monaten aktualisieren, um weiterhin Unterstützung zu erhalten.

Beispiel: Wenn PowerShell Core 6.1 am 1. Juli 2018 freigegeben wird, würde von Ihnen erwartet werden, dass Sie das Update auf PowerShell Core 6.1 bis zum 1. Januar 2019 ausgeführt haben, damit die Unterstützung aufrecht erhalten wird.

> [!IMPORTANT]
> Nach jeder Veröffentlichung einer neuen Patchversion müssen Sie PowerShell Core innerhalb von 30 Tagen aktualisieren, um weiterhin Unterstützung zu erhalten.

Wenn Sie beispielsweise PowerShell Core 6.1 ausführen, und am 19. Februar 2019 wird Version 6.1.3 veröffentlicht, würde von Ihnen erwartet, PowerShell Core 6.1.3 bis zum 21. März 2019 zu aktualisieren – also 30 Tage nach der Veröffentlichung – um Support zu erhalten. Als erforderlich eingestufte Fixes werden in unserem nächsten kumulativen Update veröffentlicht.

Die Modern Lifecycle-Richtlinie gibt auch vor, dass Microsoft 12 Monate im Voraus bekannt geben muss, wenn die Unterstützung eines Produkts (d.h. PowerShell Core) beendet wird.

Wir gehen davon aus, dass in Zukunft für PowerShell Core der Long-Term Servicing-Ansatz übernommen wird. Dieser Ansatz würde nur Wartungs- und Sicherheitsupdates erfordern, um die Unterstützung eines bestimmten Branchs oder einer bestimmten Version von 6.x aufrecht zu erhalten.

## <a name="supported-platforms"></a>Unterstützte Plattformen

Um zu bestätigen, ob Ihre Plattform und Ihre Version von PowerShell Core offiziell unterstützt werden, lesen Sie die folgende Tabelle.

Unsere Community hat außerdem Pakete für einige Plattformen beigesteuert, die jedoch nicht offiziell unterstützt werden. Diese Pakete sind in der Tabelle mit `Community` gekennzeichnet.

Plattformen, die als `Experimental` gekennzeichnet sind, werden nicht offiziell unterstützt, stehen aber zu Test- und Feedbackzwecken zur Verfügung.

| Plattform                                          | 6.1         | 6.2         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 und 10                            | Unterstützt   | Unterstützt   |
| Windows Server 2008 R2, 2012 R2, 2016             | Unterstützt   | Unterstützt   |
| [Halbjährlicher Kanal von Windows Server][semi-annual] | Unterstützt   | Unterstützt   |
| Ubuntu 16.04 und 18.04                            | Unterstützt   | Unterstützt   |
| Ubuntu 18.10 (über Snap-Pakete)                   | Community   | Community   |
| Ubuntu 19.04 (über Snap-Pakete)                   | Community   | Community   |
| Debian 9                                          | Unterstützt   | Unterstützt   |
| CentOS 7                                          | Unterstützt   | Unterstützt   |
| Red Hat Enterprise Linux 7                        | Unterstützt   | Unterstützt   |
| openSUSE 42.3                                     | Unterstützt   | Unterstützt   |
| Fedora 28                                         | Unterstützt   | Unterstützt   |
| macOS 10.12 und höher                                      | Unterstützt   | Unterstützt   |
| Arch                                              | Community   | Community   |
| Raspbian                                          | Community   | Community   |
| Kali                                              | Community   | Community   |
| AppImage (funktioniert auf verschiedenen Linux-Plattformen)      | Community   | Community   |
| [Snap-Paket](https://snapcraft.io/powershell)   | Siehe Hinweis    | Siehe Hinweis    |

> [!NOTE]
> Snap-Pakete werden genauso unterstützt wie die Distribution, auf der Sie das Paket ausführen.

## <a name="powershell-releases-end-of-life"></a>Ende der Lebensdauer von PowerShell-Versionen

Basierend auf dem [Lebenszyklus von PowerShell Core](#lifecycle-of-powershell-core) wird in der folgenden Tabelle für verschiedene Releases das Datum angegeben, ab dem sie nicht mehr unterstützt werden.

| Version | Ende der Lebensdauer                   |
|---------|-------------------------------|
| 6.0     | 13. Februar 2019             |
| 6.1     | 28. September 2019            |
| 6.2     | 6 Monate nach der Veröffentlichung von 7     |

## <a name="unsupported-platforms"></a>Nicht unterstützte Plattformen

Wenn eine Plattformversion das Ende ihrer Lebensdauer (wie vom Plattformbesitzer festgelegt) erreicht, endet auch die Unterstützung von PowerShell Core für diese Plattformversion. Bereits veröffentlichte Pakete bleiben weiterhin für Kunden verfügbar, die Zugriff benötigen. Die formelle Unterstützung und reguläre Updates jeglicher Art werden nicht mehr veröffentlicht.

Deshalb haben die Distributionsbesitzer die Unterstützung für die folgenden Versionen beendet.

| Plattform | Version | Ende der Lebensdauer                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [August 2017](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [Dezember 2017](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [Mai 2018](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| openSUSE | 42.1    | [Mai 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| openSUSE | 42.2    | [Januar 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16.10   | [Juli 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | 17.04   | [Januar 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17.10   | [Juli 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| Debian   | 8       | [Juni 2018](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| Fedora   | 27      | [November 2018](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| Ubuntu   | 14.04   | [April 2019](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a>Hinweise zur Lizenzierung

PowerShell Core wird unter der [MIT-Lizenz][] veröffentlicht. Unter dieser Lizenz und ohne kostenpflichtige Supportvereinbarung gibt es für die Benutzer nur den [Communitysupport][]. Beim Support durch die Community gibt Microsoft keine Garantien zur Schnelligkeit der Reaktion auf Ihre Tickets oder der Problembehandlung.

## <a name="windows-powershell-module"></a>Windows PowerShell-Modul

Der Support für PowerShell Core gilt nicht für andere Produktmodule, es sei denn, diese Module unterstützen PowerShell Core ausdrücklich. Zum Beispiel wird das Modul `ActiveDirectory`, das als Teil von Windows Server bereitgestellt wird, nicht unterstützt.

Allerdings können auch Module, die PowerShell Core nicht explizit unterstützen, in einigen Fällen kompatibel sein. Durch die Installation des Moduls [`WindowsPSModulePath`][] können Sie `PSModulePath` von Windows PowerShell an `PSModulePath` von PowerShell Core anfügen.

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

## <a name="experimental-features"></a>Experimentelle Features

[Experimentelle Features][] sind auf [Communitysupport](#community-support) begrenzt.

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[Communitysupport]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[unterstützten Support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT-Lizenz]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Experimentelle Features]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
