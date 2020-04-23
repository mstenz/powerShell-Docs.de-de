---
title: Supportlebenszyklus von PowerShell Core
description: Richtlinien für die Unterstützung von PowerShell Core
ms.date: 03/09/2020
ms.openlocfilehash: c319371778eb4615559ae12e0cd153a535ed22bf
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500992"
---
# <a name="powershell-support-lifecycle"></a>Supportlebenszyklus von PowerShell

PowerShell ist eine Zusammenstellung von Tools und Komponenten, die separat von Windows PowerShell bereitgestellt, installiert und konfiguriert wird. PowerShell wird nicht in den Windows-Lizenzverträgen aufgeführt.

PowerShell wird von herkömmlichen Microsoft-Supportvereinbarungen abgedeckt, darunter [kostenpflichtiger Support][], [Microsoft Enterprise Agreements][enterprise-agreement] und [Microsoft Software Assurance][assurance].
Sie können auch Hilfe bei der kostenpflichtigen [unterstützten Support][] für PowerShell anfordern.

## <a name="community-support"></a>Communitysupport

Auf GitHub wird Ihnen auch [Communitysupport][] geboten. Dort können Sie Tickets zu Problemen, Fehlern oder Funktionsanfragen stellen.
Außerdem finden Sie Unterstützung von anderen Mitgliedern der Community in der Microsoft [PowerShell Tech Community][] oder in einem der Foren, die im Communityabschnitt der [PowerShell][pshub]-Hubseite aufgeführt sind. Wir bieten keine Garantie, dass die Community Ihr Problem zügig behandelt oder behebt. Wenn Sie ein Problem haben, das unmittelbar Aufmerksamkeit erfordert, sollten Sie sich an die herkömmlichen kostenpflichtigen Supportoptionen wenden.

## <a name="lifecycle-of-powershell-7"></a>Lebenszyklus von PowerShell 7

Mit der Veröffentlichung von PowerShell 7 wird PowerShell weiterhin im Rahmen der [Microsoft Modern Lifecycle-Richtlinie][modern]unterstützt, die Datumsfestlegungen für den Support sind jedoch an den [.NET Core][Long-Term]-Supportlebenszyklus geknüpft. Bei diesem Serviceansatz können Kunden zwischen LTS-Releases (Long-Term Support) und aktuellen Releases auswählen. PowerShell 7.0 ist ein LTS-Release. Der Support endet mit dem Support von .NET Core 3.1. Das nächste LTS-Release folgt dem nächsten LTS-Release von .NET Core. Aktuelle Datumsangaben für das Supportende finden Sie in der [Tabelle zum Ende der Lebensdauer von PowerShell-Releases](#powershell-releases-end-of-life). Updates für LTS-Releases enthalten nur kritische Sicherheits- und Wartungsupdates sowie Korrekturen, die entwickelt wurden, um Auswirkungen auf vorhandene Workloads zu vermeiden oder auf ein Mindestmaß zu beschränken.

Ein aktuelles Release ist ein Release, das zwischen LTS-Releases erfolgt. Aktuelle Releases können wichtige Korrekturen, Neuerungen und neue Features enthalten. Ein aktuelles Release wird nach nachfolgenden aktuellen oder LTS-Releases für drei Monate unterstützt.

> [!IMPORTANT]
> Sie müssen das neueste Patchupdate installiert haben, um Anspruch auf Support zu erhalten. Wenn Sie z. B. PowerShell 7.0 ausführen und 7.0.1 veröffentlicht wurde, müssen Sie auf 7.0.1 aktualisieren, um Support beanspruchen zu können.

## <a name="lifecycle-of-powershell-core-6x"></a>Lebenszyklus von PowerShell Core 6.x

PowerShell Core verwendet die [Microsoft Modern Lifecycle-Richtlinie][modern]. Dieser Supportlebenszyklus soll Kunden mit den aktuellsten Versionen auf dem neuesten Stand halten.

Der Version 6.x-Branch von PowerShell Core wurde ungefähr alle sechs Monate aktualisiert (Beispiele: 6.0, 6.1, 6.2 etc.). Mit dem Release von PowerShell 7 werden jedoch keine weiteren Nebenversionen von 6.x veröffentlicht. PowerShell 6.2.x erhält weiterhin Wartungsupdates, solange es noch unterstützt wird.

> [!IMPORTANT]
> Nach jeder neuen kleinen Versionsfreigabe müssen Sie PowerShell Core innerhalb von sechs Monaten aktualisieren, um weiterhin Unterstützung zu erhalten.

Beispiel: Wenn PowerShell Core 6.1 am 1. Juli 2018 freigegeben wird, würde von Ihnen erwartet werden, dass Sie das Update auf PowerShell Core 6.1 bis zum 1. Januar 2019 ausgeführt haben, damit die Unterstützung aufrecht erhalten wird.

> [!IMPORTANT]
> Nach jeder Veröffentlichung einer neuen Patchversion müssen Sie PowerShell Core innerhalb von 30 Tagen aktualisieren, um weiterhin Unterstützung zu erhalten.

Wenn Sie beispielsweise PowerShell Core 6.1 ausführen, und am 19. Februar 2019 wird Version 6.1.3 veröffentlicht, würde von Ihnen erwartet, PowerShell Core 6.1.3 bis zum 21. März 2019 zu aktualisieren – also 30 Tage nach der Veröffentlichung – um Support zu erhalten. Als erforderlich eingestufte Fixes werden in unserem nächsten kumulativen Update veröffentlicht.

Die Modern Lifecycle-Richtlinie gibt auch vor, dass Microsoft 12 Monate im Voraus bekannt geben muss, wenn die Unterstützung eines Produkts (d.h. PowerShell Core) beendet wird.

## <a name="supported-platforms"></a>Unterstützte Plattformen

Um zu bestätigen, ob Ihre Plattform und Ihre Version von PowerShell Core offiziell unterstützt werden, lesen Sie die folgende Tabelle.

Unsere Community hat außerdem Pakete für einige Plattformen beigesteuert, die jedoch nicht offiziell unterstützt werden. Diese Pakete sind in der Tabelle mit `Community` gekennzeichnet.

Plattformen, die als `Experimental` gekennzeichnet sind, werden nicht offiziell unterstützt, stehen aber zu Test- und Feedbackzwecken zur Verfügung.

| Plattform                                          |      6.2      |    7.0    |
| ------------------------------------------------- | :-----------: | :-------: |
| Windows 8.1 und 10                               |   Unterstützt   | Unterstützt |
| Windows Server 2012 R2, 2016                      |   Unterstützt   | Unterstützt |
| [Halbjährlicher Kanal von Windows Server][semi-annual] |   Unterstützt   | Unterstützt |
| Ubuntu 16.04 und 18.04                            |   Unterstützt   | Unterstützt |
| Ubuntu 19.10 (über Snap-Pakete)                   |   Community   | Community |
| Ubuntu 20.04 (über Snap-Pakete)                   |   Community   | Community |
| Debian 9                                          |   Unterstützt   | Unterstützt |
| Debian 10                                         | Nicht unterstützt | Unterstützt |
| CentOS 7:                                          |   Unterstützt   | Unterstützt |
| CentOS 8                                          | Nicht unterstützt | Unterstützt |
| Red Hat Enterprise Linux 7                        |   Unterstützt   | Unterstützt |
| Red Hat Enterprise Linux 8                        | Nicht unterstützt | Unterstützt |
| Fedora 30                                         | Nicht unterstützt | Unterstützt |
| Alpine 3.8                                        |   Siehe Hinweis    | Siehe Hinweis  |
| Alpine 3.9 und 3.10                               | Nicht unterstützt | Siehe Hinweis  |
| macOS 10.12 oder höher                                      |   Unterstützt   | Unterstützt |
| Arch                                              |   Community   | Community |
| Raspbian                                          |   Community   | Community |
| Kali                                              |   Community   | Community |
| AppImage (funktioniert auf verschiedenen Linux-Plattformen)      |   Community   | Community |
| [Snap-Paket](https://snapcraft.io/powershell)   |   Siehe Hinweis    | Siehe Hinweis  |

> [!NOTE]
> Snap-Pakete werden genauso unterstützt wie die Distribution, auf der Sie das Paket ausführen.

> [!NOTE]
> CIM, PowerShell-Remoting und DSC werden in Alpine nicht unterstützt.

## <a name="powershell-releases-end-of-life"></a>Ende der Lebensdauer von PowerShell-Releases

Basierend auf dem [Lebenszyklus von PowerShell](#lifecycle-of-powershell-7) wird in der folgenden Tabelle für verschiedene Releases das Datum angegeben, ab dem sie nicht mehr unterstützt werden.

| Version |    Ende der Lebensdauer     |
| :-----: | ------------------ |
|   7.0   | 3\. Dezember 2022   |
|   6.2   | 4\. September 2020  |
|   6.1   | 28. September 2019 |
|   6.0   | 13. Februar 2019  |

## <a name="unsupported-platforms"></a>Nicht unterstützte Plattformen

Wenn eine Plattformversion das Ende ihrer Lebensdauer (wie vom Plattformbesitzer festgelegt) erreicht, endet auch die Unterstützung von PowerShell Core für diese Plattformversion. Bereits veröffentlichte Pakete bleiben weiterhin für Kunden verfügbar, die Zugriff benötigen. Die formelle Unterstützung und reguläre Updates jeglicher Art werden nicht mehr veröffentlicht.

Deshalb haben die Distributionsbesitzer die Unterstützung für die folgenden Versionen beendet.

|    Plattform    | Version |                                                         Ende der Lebensdauer                                                          |
| -------------- | :-----: | ---------------------------------------------------------------------------------------------------------------------------- |
| Debian         |    8    | [Juni 2018](https://lists.debian.org/debian-security-announce/2018/msg00132.html)                                            |
| Fedora         |   24    | [August 2017](https://fedoramagazine.org/fedora-24-eol/)                                                                     |
| Fedora         |   25    | [Dezember 2017](https://fedoramagazine.org/fedora-25-end-life/)                                                              |
| Fedora         |   26    | [Mai 2018](https://fedoramagazine.org/fedora-26-end-life/)                                                                   |
| Fedora         |   27    | [November 2018](https://fedoramagazine.org/fedora-27-end-of-life/)                                                           |
| Fedora         |   28    | [Mai 2019](https://fedoramagazine.org/fedora-28-end-of-life/)                                                                |
| openSUSE       |  42.1   | [Mai 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)                                      |
| openSUSE       |  42.2   | [Januar 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html)                                  |
| openSUSE       |  42.3   | [Juli 2019](https://lists.opensuse.org/opensuse-security-announce/2019-07/msg00000.html)                                     |
| Ubuntu         |  14.04  | [April 2019](https://wiki.ubuntu.com/Releases)                                                                               |
| Ubuntu         |  16.10  | [Juli 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)                                         |
| Ubuntu         |  17.04  | [Januar 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)                                           |
| Ubuntu         |  17.10  | [Juli 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)                                         |
| Windows        |    7    | [Januar 2020](https://support.microsoft.com/help/4057281/windows-7-support-ended-on-january-14-2020)                        |
| Windows Server | 2008 R2 | [Januar 2020](https://support.microsoft.com/help/4456235/end-of-support-for-windows-server-2008-and-windows-server-2008-r2) |

## <a name="notes-on-licensing"></a>Hinweise zur Lizenzierung

PowerShell Core wird unter der [MIT-Lizenz][] veröffentlicht. Unter dieser Lizenz und ohne kostenpflichtige Supportvereinbarung gibt es für die Benutzer nur den [Communitysupport][]. Beim Support durch die Community gibt Microsoft keine Garantien zur Schnelligkeit der Reaktion auf Ihre Tickets oder der Problembehandlung.

## <a name="windows-powershell-compatibility"></a>Windows PowerShell-Kompatibilität

Der Supportlebenszyklus für PowerShell deckt keine Module ab, die außerhalb des PowerShell 7-Releasepakets bereitgestellt werden. Zum Beispiel wird das Modul `ActiveDirectory`, das als Teil von Windows Server bereitgestellt wird, nicht im Rahmen des [Windows-Supportlebenszyklus][] unterstützt.

PowerShell 7 verbessert die Kompatibilität mit vorhandenen PowerShell-Modulen, die für Windows PowerShell geschrieben wurden.
Weitere Informationen finden Sie im Artikel [about_Windows_Compatibility][] und in der [Modulkompatibilitätsliste][].

> [!NOTE]
> Das Modul [**WindowsPSModulePath**](https://www.powershellgallery.com/packages/WindowsPSModulePath) ist in PowerShell 7 nicht mehr erforderlich und wird nicht unterstützt.

## <a name="experimental-features"></a>Experimentelle Features

[Experimentelle Features][] sind auf [Communitysupport](#community-support) begrenzt.

## <a name="release-history"></a>Releaseverlauf

Die folgende Tabelle enthält die Hauptversionen von PowerShell im Zeitverlauf. Diese Tabelle wird als historische Referenz bereitgestellt. Sie eignet sich nicht zur Bestimmung des Supportlebenszyklus.

|       Version        | Veröffentlichungsdatum |                                                                     Hinweis                                                                      |
| -------------------- | :----------: | --------------------------------------------------------------------------------------------------------------------------------------------- |
| PowerShell 7.0 (LTS) |   März 2020   | Basiert auf .NET Core 3.1 (LTS).                                                                                                                  |
| PowerShell 6.0       |   Januar 2018   | Erstes Release, basiert auf .NET Core 2.1. Installierbar unter Windows, Linux und macOS.                                                              |
| PowerShell 5.1       |   August 2016   | Veröffentlicht in Windows 10 Anniversary Update und Windows Server 2016.                                                                             |
| PowerShell 5.0       |   Februar 2016   | Veröffentlicht in Windows Management Framework (WMF) 5.0.                                                                                            |
| PowerShell 4.0       |   Oktober 2013   | Integriert in Windows 8.1 und Windows Server 2012 R2. Installierbar unter Windows 7 SP1, Windows Server 2008 R2 SP1 und Windows Server 2012. |
| PowerShell 3.0       |   Oktober 2012   | Integriert in Windows 8 und Windows Server 2012. Installierbar unter Windows 7 SP1, Windows Server 2008 SP1 und Windows Server 2008 R2 SP1.  |
| PowerShell 2.0       |   Juli 2009   | Integriert in Windows 7 und Windows Server 2008 R2. Installierbar unter Windows XP SP3, Windows Server 2003 SP2 und Windows Vista SP1.            |
| PowerShell 1.0       |   November 2006   | Installierbar unter Windows XP SP2, Windows Server 2003 SP1 und Windows Vista. Optionale Komponente von Windows Server 2008.                          |

<!-- hyperlink references -->
[Kostenpflichtiger Support]: https://support.microsoft.com/hub/4343728/support-for-business
[enterprise-agreement]: https://www.microsoft.com/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx
[Communitysupport]: /powershell/scripting/community/community-support
[pshub]: /powershell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[unterstützten Support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[Long-Term]: https://dotnet.microsoft.com/platform/support/policy/dotnet-core
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: /windows-server/get-started/semi-annual-channel-overview
[MIT-Lizenz]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[about_Windows_Compatibility]: /powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility
[Windows-Supportlebenszyklus]: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet
[Modulkompatibilitätsliste]: /powershell/scripting/whats-new/module-compatibility
[WindowsPSModulePath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Experimentelle Features]: /powershell/module/microsoft.powershell.core/about/about_powershell_config#experimentalfeatures
