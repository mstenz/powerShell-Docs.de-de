---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: Erste Schritte mit dem PowerShell-Katalog | MSDN
ms.openlocfilehash: 599b148e141ba4205a7c774581e737a5d54bfae1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="get-started-with-the-powershell-gallery"></a>Erste Schritte mit dem PowerShell-Katalog

## <a name="what-is-the-powershell-gallery"></a>Was ist der PowerShell-Katalog?

Der PowerShell-Katalog ist das zentrale Repository für PowerShell-Inhalte.
Sie finden darin nützliche PowerShell-Module, die PowerShell-Befehle und Desired State Configuration-Ressourcen (DSC) enthalten. Sie finden dort auch PowerShell-Skripts, von denen einige PowerShell-Workflows enthalten, eine Reihe von Aufgaben umreißen und Sequenzierungen für diese Aufgaben bereitstellen.
Einige dieser Elemente wurden von Microsoft erstellt, andere stammen aus der PowerShell-Community.

## <a name="requirements"></a>Anforderungen

Das Herunterladen von Elementen aus dem PowerShell-Katalog auf Ihr System erfordert das [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)-Modul. Das PowerShellGet-Modul ist in jedem der folgenden Downloads enthalten. Um diese Elemente aus dem PowerShell-Katalog herunterzuladen, müssen Sie sich nicht anmelden.

-   [Windows 10](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)
-   [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkId=398175)
-   [MSI Installer (für PowerShell 3 und 4)](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

PowerShellGet erfordert außerdem den [NuGet-Anbieter](http://go.microsoft.com/fwlink/?LinkId=722208), um mit dem PowerShell-Katalog zu funktionieren. Sie werden aufgefordert, den NuGet-Anbieter automatisch bei der ersten Verwendung von PowerShellGet zu installieren, wenn der NuGet-Anbieter sich nicht an einem der folgenden Speicherorte befindet:

- `$env:ProgramFiles\PackageManagement\ProviderAssemblies`
- `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies`

Alternativ können Sie `Install-PackageProvider -Name NuGet -Force` ausführen, um den Download und die Installation des NuGet-Anbieters zu automatisieren.


Wenn Sie eine älteren Version von NuGet als 2.8.5.201 besitzen, müssen Sie die folgenden PowerShell-Cmdlets aufrufen, um die neueste Version von NuGet zu installieren.

1.  `Install-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
2.  `Import-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
3.  Löschen Sie die ältere Version von NuGet aus dem obigen Installationsverzeichnis.

Weitere Informationen finden Sie unter <http://oneget.org/>.


Hinweis: Aufgrund von Änderungen an den Paketerstellungsformaten empfehlen wir, dass Sie auf die neueste Version von PowerShellGet und PackageManagement zu aktualisieren, um Elemente zu installieren, die kürzlich aktualisiert wurden. PowerShellGet ist im Lieferumfang von Windows 10 mit inbegriffen. [Hier](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409) können Sie mehr darüber erfahren.
PowerShellGet ist auch ein Teil des Windows Management Framework (WMF) 5.0, das Sie [hier](http://go.microsoft.com/fwlink/?LinkId=398175) herunterladen können.

## <a name="discovering-items-from-the-powershell-gallery"></a>Suchen von Elementen im PowerShell-Katalog

Sie können Elemente im PowerShell-Katalog mithilfe des Steuerelements **Suchen** auf dieser Website suchen. Alternativ können Sie die Seiten zu Modulen und Skripts durchsuchen. Sie können auch nach Elementen im PowerShell-Katalog suchen, indem Sie die Cmdlets [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) und [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322) je nach Elementtyp mit `-Repository PSGallery` ausführen.

Das Filtern von Ergebnissen im Katalog kann über die folgenden Parameter von [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) und [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322) erfolgen:

- Name
- AllVersions
- MinimumVersion
- RequiredVersion
- Tag
- Includes
- DscResource
- RoleCapability
- Befehl
- Filter

Wenn Sie nur spezifische DSC-Ressourcen im Katalog suchen, können Sie das Cmdlet [Find-DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) ausführen.
[Find-DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) gibt Daten zu DSC-Ressourcen zurück, die im Katalog enthalten sind. Da DSC-Ressourcen immer als Teil eines Moduls geliefert werden, müssen Sie [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) ausführen, um diese DSC-Ressourcen zu installieren.

## <a name="learning-about-items-in-the-powershell-gallery"></a>Informationen zu den Elementen im PowerShell-Katalog

Wenn Sie ein Element ermittelt haben, an dem Sie interessiert sind, möchten Sie möglicherweise weitere Informationen erhalten. Diese finden Sie auf der Katalogseite dieses bestimmten Elements. Dort finden Sie alle Metadaten, die mit dem Element hochgeladen wurden. Diese Metadaten eines Elements werden von dem jeweiligen Autoren bereitgestellt und nicht von Microsoft überprüft. Der Besitzer des Elements ist eng an das Katalog-Konto gebunden, das für die Veröffentlichung des Elements verwendet wurde, und ist vertrauenswürdiger als das Feld „Autor“.

Wenn Sie ein Element entdecken, das Ihrer Meinung nach nicht mit guten Absichten veröffentlicht wurde, klicken Sie auf der Elementseite auf **Report Abuse** (Missbrauch melden).

Wenn Sie [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) oder [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322) ausführen, können Sie diese Daten im zurückgegebenen PSGetModuleInfo-Objekt anzeigen.
Die Ausführung von `Find-Module -Name PSReadLine -Repository PSGallery | Get-Member` gibt z.B. Daten für das PSReadLine-Modul im Katalog zurück.

## <a name="downloading-items-from-the-powershell-gallery"></a>Herunterladen von Elementen aus dem PowerShell-Katalog

Wir empfehlen den folgenden Prozess für das Herunterladen von Elementen aus dem PowerShell-Katalog:

### <a name="inspect"></a>Überprüfen

Führen Sie zum Herunterladen eines Elements aus dem Katalog für die Überprüfung je nach Elementtyp entweder das Cmdlet [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) oder [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334) aus. Dadurch können Sie das Element lokal speichern, ohne es zu installieren, und den Inhalt des Elements überprüfen. Denken Sie daran, das gespeicherte Element manuell löschen.

Einige dieser Elemente wurden von Microsoft erstellt, andere stammen aus der PowerShell-Community. Microsoft empfiehlt, dass Sie den Inhalt und den Code der Elemente in diesem Katalog vor der Installation überprüfen.

Wenn Sie ein Element entdecken, das Ihrer Meinung nach nicht mit guten Absichten veröffentlicht wurde, klicken Sie auf der Elementseite auf **Report Abuse** (Missbrauch melden).

### <a name="install"></a>Installation

Führen Sie je nach Elementtyp das Cmdlet [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) oder [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) aus, um ein Element aus dem Katalog für die Verwendung zu installieren.

[Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) installiert das Modul standardmäßig in `$env:ProgramFiles\WindowsPowerShell\Modules`. Dafür ist ein Administratorkonto erforderlich. Wenn Sie den Parameter `-Scope
CurrentUser` hinzufügen, wird das Modul in `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` installiert.

[Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) installiert das Skript standardmäßig in `$env:ProgramFiles\WindowsPowerShell\Scripts`. Dafür ist ein Administratorkonto erforderlich. Wenn Sie den Parameter `-Scope
CurrentUser` hinzufügen, wird das Skript in `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` installiert.

[Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) und [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) installieren standardmäßig die aktuellste Version eines Elements. Fügen Sie den Parameter `-RequiredVersion` hinzu, um eine ältere Version des Elements zu installieren.

### <a name="deploy"></a>Bereitstellen

Klicken Sie auf der Detailseite des Elements auf **Deploy to Azure Automation** (Bereitstellen in Azure Automation), um ein Element aus dem Katalog in Azure Automation bereitzustellen. Sie werden zum Azure-Verwaltungsportal umgeleitet, wo Sie sich mit den Anmeldeinformationen Ihres Azure-Kontos anmelden. Beachten Sie, dass das Bereitstellen von Elementen mit Abhängigkeiten alle Abhängigkeiten in Azure Automation bereitstellt. Sie können die Schaltfläche „Deploy to Azure Automation“ (Bereitstellen in Azure Automation) deaktivieren, indem Sie Ihren Elementmetadaten das Tag **AzureAutomationNotSupported** hinzufügen.

Weitere Informationen zu Azure Automation finden Sie auf der [Azure Automation-Website](http://azure.microsoft.com/services/automation/).

## <a name="updating-items-from-the-powershell-gallery"></a>Aktualisieren von Elementen aus dem PowerShell-Katalog

Führen Sie zum Aktualisieren der installierten Elemente aus dem PowerShell-Katalog die Cmdlets [Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576) oder [Update-Script](http://go.microsoft.com/fwlink/?LinkId=619787) aus. [Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576) versucht, jedes mithilfe von [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) installierte Modul zu aktualisieren, wenn es ohne zusätzliche Parameter ausgeführt wird.
Um Module einzeln zu aktualisieren, fügen Sie den Parameter `-Name` hinzu.

Ebenso versucht [Update-Script](http://go.microsoft.com/fwlink/?LinkId=619787), jedes mithilfe von [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) installierte Script zu aktualisieren, wenn es ohne zusätzliche Parameter ausgeführt wird.
Um Skripts einzeln zu aktualisieren, fügen Sie den Parameter `-Name` hinzu.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>Listenelemente, die Sie aus dem PowerShell-Katalog installiert haben

Führen Sie das Cmdlet [Get-InstalledModule](https://go.microsoft.com/fwlink/?LinkId=526863) aus, um herauszufinden, welche Module Sie aus dem PowerShell-Katalog installiert haben. Dieser Befehl listet alle Module auf, die direkt aus dem PowerShell-Katalog auf Ihrem System installiert wurden.

Um herauszufinden, welche Skripts Sie aus dem PowerShell-Katalog installiert haben, führen Sie das Cmdlet [Get-InstalledScript](https://go.microsoft.com/fwlink/?LinkId=619790) aus. Dieser Befehl listet alle Skripts auf, die direkt aus dem PowerShell-Katalog auf Ihrem System installiert wurden.