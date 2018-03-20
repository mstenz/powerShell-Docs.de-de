---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery,psget
title: Der PowerShell-Katalog | MSDN
ms.openlocfilehash: 7389ce8286c515b0bfc25f32634a482b060cb74c
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="the-powershell-gallery"></a>Der PowerShell-Katalog | MSDN

Der PowerShell-Katalog ist das zentrale Repository für PowerShell-Inhalte. Im Katalog finden Sie neue PowerShell-Befehle oder DSC-Ressourcen (Desired State Configuration).

## <a name="powershellget-overview"></a>Übersicht über PowerShellGet

Das PowerShellGet-Modul enthält Cmdlets zum Ermitteln, Installieren, Aktualisieren und Veröffentlichen von PowerShell-Artefakten wie Modulen, DSC-Ressourcen, Rollenfunktionen und Skripts über den [PowerShell-Katalog](https://www.PowerShellGallery.com) und andere private Repositorys.

## <a name="getting-started-with-the-gallery"></a>Erste Schritte mit dem Katalog

Für die Installation von Elementen über den Katalog ist die neueste Version des PowerShellGet-Moduls erforderlich, die in Windows 10, im Windows Management Framework (WMF) 5.0 oder im MSI-basierten Installer (für PowerShell 3 und 4) verfügbar ist.

- [**Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409) abrufen
- [**WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175) abrufen
- [**MSI-Installer abrufen**](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

Mit dem neuesten [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)-Modul haben Sie folgende Möglichkeiten:

-   Durchsuchen der Elemente im Katalog mit [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) und [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)
-   Speichern von Elementen aus dem Katalog in Ihrem System mit [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) und [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)
-   Installieren von Elementen aus dem Katalog mit [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) und [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)
-   Hochladen von Elementen im Katalog mit [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) und [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)
-   Hinzufügen Ihres eigenen benutzerdefinierten Repositorys mit [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)

Sehen Sie sich die Seite [Erste Schritte](psgallery/psgallery_gettingstarted.md) an, um weitere Informationen zur Verwendung von PowerShellGet-Befehlen mit dem Katalog zu erhalten. Sie können auch *Update-Help -Module PowerShellGet* ausführen, um die lokale Hilfe für diese Befehle zu installieren.

## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme

Für das **PowerShellGet**-Modul ist **PowerShell 3.0 oder neuer** erforderlich.

Aus diesem Grund erfordert **PowerShellGet** eines der folgenden Betriebssysteme:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

Für **PowerShellGet** ist außerdem .NET Framework 4.5 oder höher erforderlich. Von [hier](https://msdn.microsoft.com/library/5a4x27ek.aspx) können Sie .NET Framework 4.5 oder höher installieren.


## <a name="got-a-question-have-feedback"></a>Sie haben eine Frage? Haben Sie Feedback?

Weitere Informationen zum PowerShell-Katalog und zu PowerShellGet finden Sie auf der Seite [Erste Schritte](psgallery/psgallery_gettingstarted.md). Stellen Sie Feedback bereit, und melden Sie Probleme über [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).

