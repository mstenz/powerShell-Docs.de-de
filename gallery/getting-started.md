---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Erste Schritte mit dem PowerShell-Katalog
ms.openlocfilehash: 85b0a754aba25d850dc918024419318554f92b33
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225674"
---
# <a name="getting-started-with-the-powershell-gallery"></a>Erste Schritte mit dem PowerShell-Katalog

Die richtige Vorgehensweise zum Installieren von Paketen aus dem PowerShell-Katalog ist die Verwendung der Cmdlets im Modul [PowerShellGet](/powershell/module/powershellget). Um diese Elemente aus dem PowerShell-Katalog herunterzuladen, müssen Sie sich nicht anmelden.

> [!NOTE]
> Zwar ist es möglich, ein Paket direkt aus dem PowerShell-Katalog herunterzuladen, diese Vorgehensweise wird aber nicht empfohlen.
> Weitere Informationen finden Sie unter [Manual Package Download (Paket manuell herunterladen)](/powershell/gallery/how-to/working-with-packages/manual-download).

## <a name="discovering-packages-from-the-powershell-gallery"></a>Ermitteln von Paketen im PowerShell-Katalog

Sie können Pakete im PowerShell-Katalog mithilfe des Steuerelements **Suchen** auf dieser Website suchen. Alternativ dazu können Sie die Seiten zu Modulen und Skripts durchsuchen. Sie können auch nach Paketen im PowerShell-Katalog suchen, indem Sie je nach Pakettyp die Cmdlets [Find-Module][] und [Find-Script][] mit `-Repository PSGallery` ausführen.

Das Filtern von Ergebnissen im Katalog kann über die folgenden Parameter erfolgen:

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

Wenn Sie nur spezifische DSC-Ressourcen im Katalog suchen, können Sie das Cmdlet [Find-DscResource] ausführen. „Find-DscResource“ gibt Daten zu DSC-Ressourcen zurück, die im Katalog enthalten sind.
Da DSC-Ressourcen immer als Teil eines Moduls geliefert werden, müssen Sie [Install-Module][] ausführen, um diese DSC-Ressourcen zu installieren.

## <a name="learning-about-packages-in-the-powershell-gallery"></a>Informationen Paketen im PowerShell-Katalog

Wenn Sie ein Paket ermittelt haben, an dem Sie interessiert sind, möchten Sie möglicherweise weitere Informationen dazu erhalten. Sehen Sie sich zu diesem Zweck die Katalogseite dieses bestimmten Pakets an. Dort finden Sie alle Metadaten, die mit dem Paket hochgeladen wurden. Diese Metadaten werden vom Autor des Pakets bereitgestellt und nicht von Microsoft überprüft. Der Besitzer des Pakets ist eng an das Katalog-Konto gebunden, das für die Veröffentlichung des Pakets verwendet wurde, und ist vertrauenswürdiger als das Feld „Autor“.

Wenn Sie ein Paket entdecken, das Ihrer Meinung nach nicht mit guten Absichten veröffentlicht wurde, klicken Sie auf der Seite dieses Pakets auf **Missbrauch melden**.

Wenn Sie [Find-Module][] oder [Find-Script][] ausführen, können Sie diese Daten im zurückgegebenen PSGetModuleInfo-Objekt anzeigen. Die Ausführung von `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` gibt beispielsweise
Daten für das PSReadLine-Modul im Katalog zurück.

## <a name="downloading-packages-from-the-powershell-gallery"></a>Herunterladen von Paketen aus dem PowerShell-Katalog

Wir empfehlen den folgenden Prozess für das Herunterladen von Paketen aus dem PowerShell-Katalog:

### <a name="inspect"></a>Überprüfen

Um ein Paket zur Überprüfung aus dem Katalog herunterzuladen, führen Sie je nach Pakettyp entweder das Cmdlet [Save-Module][] oder das Cmdlet [Save-Script][] aus. Dadurch können Sie das Paket lokal speichern, ohne es zu installieren, und den Paketinhalt überprüfen. Denken Sie daran, das gespeicherte Paket später manuell zu löschen.

Einige dieser Pakete wurden von Microsoft erstellt, andere stammen aus der PowerShell-Community.
Microsoft empfiehlt, dass Sie den Inhalt und den Code der Pakete in diesem Katalog vor der Installation überprüfen.

Wenn Sie ein Paket entdecken, das Ihrer Meinung nach nicht mit guten Absichten veröffentlicht wurde, klicken Sie auf der Seite dieses Pakets auf **Missbrauch melden**.

### <a name="install"></a>Installation

Um ein Paket aus dem Katalog für die Verwendung zu installieren, führen Sie je nach Pakettyp das Cmdlet [Install-Module][] oder das Cmdlet [Install-Script][] aus.

[Install-Module][] installiert das Modul standardmäßig in `$env:ProgramFiles\WindowsPowerShell\Modules`.
Dafür ist ein Administratorkonto erforderlich. Wenn Sie den Parameter `-Scope CurrentUser` hinzufügen, wird das Modul in `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` installiert.

[Install-Script][] installiert das Skript standardmäßig in `$env:ProgramFiles\WindowsPowerShell\Scripts`.
Dafür ist ein Administratorkonto erforderlich. Wenn Sie den Parameter `-Scope CurrentUser` hinzufügen, wird das Skript in `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` installiert.

[Install-Module][] und [Install-Script][] installieren standardmäßig die neueste Version eines Pakets.
Um eine ältere Version des Pakets zu installieren, fügen Sie den Parameter `-RequiredVersion` hinzu.

### <a name="deploy"></a>Bereitstellen

Klicken Sie auf der Detailseite des Pakets auf **In Azure Automation bereitstellen**, um ein Paket aus dem PowerShell-Katalog in Azure Automation bereitzustellen. Sie werden zum Azure-Verwaltungsportal umgeleitet, wo Sie sich mit den Anmeldeinformationen Ihres Azure-Kontos anmelden. Beachten Sie, dass das Bereitstellen von Paketen mit Abhängigkeiten alle Abhängigkeiten in Azure Automation bereitstellt. Sie können die Schaltfläche „In Azure Automation bereitstellen“ deaktivieren, indem Sie den Paketmetadaten das Tag **AzureAutomationNotSupported** hinzufügen.

Weitere Informationen zu Azure Automation finden Sie in der [Azure Automation](/azure/automation)-Dokumentation.

## <a name="updating-packages-from-the-powershell-gallery"></a>Aktualisieren von Paketen aus dem PowerShell-Katalog

Führen Sie zum Aktualisieren der aus dem PowerShell-Katalog installierten Pakete das Cmdlet [Update-Module][] oder das Cmdlet [Update-Script][] aus. [Update-Module][] versucht, jedes mithilfe von [Install-Module][] installierte Modul zu aktualisieren, wenn es ohne zusätzliche Parameter ausgeführt wird. Um Module einzeln zu aktualisieren, fügen Sie den Parameter `-Name` hinzu.

Ähnlich versucht [Update-Script][], jedes durch Ausführung von [Install-Script][] installierte Skript zu aktualisieren, wenn es ohne zusätzliche Parameter ausgeführt wird. Um Skripts einzeln zu aktualisieren, fügen Sie den Parameter `-Name` hinzu.

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a>Auflisten von aus dem PowerShell-Katalog installierten Paketen

Führen Sie das Cmdlet [Get-InstalledModule][] aus, um herauszufinden, welche Module Sie aus dem PowerShell-Katalog installiert haben. Dieser Befehl listet alle Module auf, die direkt aus dem PowerShell-Katalog auf Ihrem System installiert wurden.

Um herauszufinden, welche Skripts Sie aus dem PowerShell-Katalog installiert haben, führen Sie das Cmdlet [Get-InstalledScript][] aus. Dieser Befehl listet alle Skripts auf, die direkt aus dem PowerShell-Katalog auf Ihrem System installiert wurden.

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script
