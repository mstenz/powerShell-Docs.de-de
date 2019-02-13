---
title: Supportlebenszyklus von PowerShell Core
description: Richtlinien für die Unterstützung von PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: cb1daf953b11ffba8f39bcc05a8b122350c497eb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679453"
---
# <a name="powershell-core-support-lifecycle"></a>Supportlebenszyklus von PowerShell Core

PowerShell Core ist eine Zusammenstellung von Tools und Komponenten, die separat von Windows PowerShell bereitgestellt, installiert und konfiguriert wird.
PowerShell Core ist daher nicht in die Windows 7/8.1/10 oder Windows Server-Lizenzbedingungen enthalten.

PowerShell Core wird jedoch von herkömmlichen Microsoft-Supportvereinbarungen unterstützt, einschließlich [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement] und [Microsoft Software Assurance][assurance].
Sie können auch Hilfe bei der kostenpflichtigen [unterstützten Support][] für PowerShell Core anfordern.

Auf GitHub wird Ihnen auch [Communitysupport][] geboten. Dort können Sie Tickets zu Problemen, Fehlern oder Funktionsanfragen stellen.
Darüber hinaus können Sie Hilfe von anderen Mitgliedern der Community finden Sie auf der Seite Allgemein [Microsoft Community][] oder der Microsoft [PowerShell Tech Community][].
Wir bieten keine Garantie, dass die Community zu beheben oder Ihr Problem zu, rechtzeitig beheben wird.
Wenn Sie ein Problem haben, das unmittelbar Aufmerksamkeit erfordert, sollten Sie sich an die herkömmlichen kostenpflichtigen Supportoptionen wenden.

## <a name="lifecycle-of-powershell-core"></a>Lebenszyklus von PowerShell Core

PowerShell Core übernimmt die [Modern Lifecycle-Richtlinie von Microsoft][modern].
Dieser Supportlebenszyklus soll Kunden mit den aktuellsten Versionen auf dem neuesten Stand halten.

Branch von Version 6.x von PowerShell Core wird ungefähr alle sechs Monate aktualisiert (Beispiele: 6.0, 6.1, 6.2, usw..)

> [!IMPORTANT]
> Nach jeder neuen kleinen Versionsfreigabe müssen Sie PowerShell Core innerhalb von sechs Monaten aktualisieren, um weiterhin Unterstützung zu erhalten.

Z. B. Wenn Sie PowerShell Core 6.1 am 1. Juli 2018 veröffentlicht wird würde von Ihnen erwartet werden zum Aktualisieren von auf PowerShell Core 6.1 am 1. Januar 2019 um Support zu erhalten.

![Lebenszyklus des PowerShell Core-Branchs][lifecycle-chart]

Modern Lifecycle-Richtlinie erfordert auch, dass Microsoft Kunden 12 Monate im Voraus geben vor, stellt die Unterstützung für ein Produkt (d.h. PowerShell Core).

Schließlich wir erwarten, dass PowerShell Core übernimmt der "langfristigen Wartung" Ansatz.
Bei diesem Ansatz servicing müssten wir nur Wartungs- und Sicherheitsupdates Updates, bei der Unterstützung von einer bestimmten Branch/Version von 6.x aufrecht zu bleiben.

## <a name="supported-platforms"></a>Unterstützte Plattformen

Auf welcher Plattform, die Sie verwenden die Version von PowerShell Core finden in der folgende Tabelle wird offiziell unterstützt.

Unsere Community hat außerdem Pakete für einige Plattformen beigesteuert, die jedoch nicht offiziell unterstützt werden.
Diese Pakete sind in der Tabelle mit `Community` gekennzeichnet.

Plattformen, die als `Experimental` gekennzeichnet sind, werden nicht offiziell unterstützt, stehen aber aus Test- und Feedbackzwecken zur Verfügung.

|                                                   | 6.0         | 6.1         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 und 10                            | Unterstützt   | Unterstützt   |
| Windows Server 2008 R2, 2012 R2, 2016             | Unterstützt   | Unterstützt   |
| [Halbjährlicher Kanal von Windows Server][semi-annual] | Unterstützt   | Unterstützt   |
| Ubuntu 14.04 und 16.04                           | Unterstützt   | Unterstützt   |
| Ubuntu 18.04                                      |             | Unterstützt   |
| Ubuntu 18.10 (über Snap-Pakete)                   |             | Community   |
| Debian 9                                          | Unterstützt   | Unterstützt   |
| CentOS 7                                          | Unterstützt   | Unterstützt   |
| Red Hat Enterprise Linux 7                        | Unterstützt   | Unterstützt   |
| openSUSE 42.3                                     | Unterstützt   | Unterstützt   |
| Fedora 28                                         |             | Unterstützt   |
| macOS 10.12 und höher                                      | Unterstützt   | Unterstützt   |
| Arch                                              | Community   | Community   |
| Raspbian                                          | Experimentell| Community   |
| Kali                                              | Community   | Community   |
| AppImage (funktioniert auf verschiedenen Linux-Plattformen)     | Community   | Community   |
| [Snap-Paket](https://snapcraft.io/powershell)   | Siehe Hinweis    | Siehe Hinweis    |

> [!NOTE]
> Die Verwendung von Snap-Paketen wird für einen gewissen Zeitraum getestet.
> Nach dieser Testphase sollten Snap-Pakete nicht zu neuen Supportanfragen führen. Die Unterstützung richtet sich nach der Distribution, auf der Sie das Paket ausführen.

## <a name="powershell-release-end-of-life"></a>PowerShell Version Ende ihrer Lebensdauer

Basierend auf [Lebenszyklus von PowerShell Core](#lifecycle-of-powershell-core), die folgende Tabelle enthält die Datumsangaben, die bei verschiedenen Version wird nicht mehr unterstützt.

| Version | Ende der Lebensdauer                   |
|---------|-------------------------------|
| 6.0     | 13 Februar 2019             |
| 6.1     | 6 Monate nach 6.2-Versionen   |

## <a name="platforms-which-are-out-of-support"></a>Plattformen, die nicht mehr unterstützt werden

Wenn eine Version der End-of-Life-erreicht, gemäß der durch den Besitzer der Plattform, beendet auch PowerShell Core unterstützt diese Plattformversion.
Bereits veröffentlichte Pakete bleiben weiterhin für Kunden verfügbar, die Zugriff benötigen. Die formelle Unterstützung und reguläre Updates jeglicher Art werden nicht mehr veröffentlicht.

Die Besitzer der Verteilung wird also beendet die Unterstützung für die folgenden Versionen und werden nicht unterstützt.

| Betriebssystem       | Version | Ende der Lebensdauer                                                                                 |
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

## <a name="notes-on-licensing"></a>Hinweise zur Lizenzierung

PowerShell Core wird unter der [MIT-Lizenz][] veröffentlicht.
Unter dieser Lizenz und ohne einer kostenpflichtigen supportvereinbarung, sind Benutzer auf [Communitysupport][].
Beim Support durch die Community gibt Microsoft keine Garantien zur Schnelligkeit der Reaktion auf Ihre Tickets oder der Problembehandlung.

## <a name="windows-powershell-module"></a>Windows PowerShell-Modul

Unterstützung für PowerShell Core die Produktmodule, es sei denn, diese Module PowerShell Core ausdrücklich unterstützen nicht enthalten ist.
Zum Beispiel wird das Modul `ActiveDirectory`, das als Teil von Windows Server bereitgestellt wird, nicht unterstützt.

Allerdings können auch Module, die PowerShell Core nicht explizit unterstützen, in manchen Fällen kompatibel sein.
Durch die Installation der [ `WindowsPSModulePath` ][] -Modul können Sie die Windows PowerShell hinzufügen `PSModulePath` in Ihre PowerShell Core `PSModulePath`.

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
[Communitysupport]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[unterstützten Support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT-Lizenz]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
