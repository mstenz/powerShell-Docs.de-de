---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Erste Schritte mit dem PowerShell-Katalog
ms.openlocfilehash: 83974698152e75efac66ea725a9c220486676d6f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190161"
---
# <a name="get-started-with-the-powershell-gallery"></a>Erste Schritte mit dem PowerShell-Katalog

Das Herunterladen von Elementen aus dem PowerShell-Katalog auf Ihr System erfordert das [PowerShellGet](/powershell/module/powershellget)-Modul. Das PowerShellGet-Modul ist in jedem der folgenden Downloads enthalten. Um diese Elemente aus dem PowerShell-Katalog herunterzuladen, müssen Sie sich nicht anmelden.

## <a name="discovering-items-from-the-powershell-gallery"></a>Suchen von Elementen im PowerShell-Katalog

Sie können Elemente im PowerShell-Katalog mithilfe des Steuerelements **Suchen** auf dieser Website suchen. Alternativ können Sie die Seiten zu Modulen und Skripts durchsuchen. Sie können auch nach Elementen im PowerShell-Katalog suchen, indem Sie die Cmdlets [Find-Module][] und [Find-Script][] je nach Elementtyp mit `-Repository PSGallery` ausführen.

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

## <a name="learning-about-items-in-the-powershell-gallery"></a>Informationen zu den Elementen im PowerShell-Katalog

Wenn Sie ein Element ermittelt haben, an dem Sie interessiert sind, möchten Sie möglicherweise weitere Informationen erhalten. Diese finden Sie auf der Katalogseite dieses bestimmten Elements. Dort finden Sie alle Metadaten, die mit dem Element hochgeladen wurden. Diese Metadaten eines Elements werden von dem jeweiligen Autoren bereitgestellt und nicht von Microsoft überprüft. Der Besitzer des Elements ist eng an das Katalog-Konto gebunden, das für die Veröffentlichung des Elements verwendet wurde, und ist vertrauenswürdiger als das Feld „Autor“.

Wenn Sie ein Element entdecken, das Ihrer Meinung nach nicht mit guten Absichten veröffentlicht wurde, klicken Sie auf der Elementseite auf **Report Abuse** (Missbrauch melden).

Wenn Sie [Find-Module][] oder [Find-Script][] ausführen, können Sie diese Daten im zurückgegebenen PSGetModuleInfo-Objekt anzeigen. Die Ausführung von `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` gibt z.B. Daten für das PSReadLine-Modul im Katalog zurück.

## <a name="downloading-items-from-the-powershell-gallery"></a>Herunterladen von Elementen aus dem PowerShell-Katalog

Wir empfehlen den folgenden Prozess für das Herunterladen von Elementen aus dem PowerShell-Katalog:

### <a name="inspect"></a>Überprüfen

Führen Sie zum Herunterladen eines Elements aus dem Katalog für die Überprüfung je nach Elementtyp entweder das Cmdlet [Save-Module][] oder [Save-Script][] aus. Dadurch können Sie das Element lokal speichern, ohne es zu installieren, und den Inhalt des Elements überprüfen. Denken Sie daran, das gespeicherte Element manuell löschen.

Einige dieser Elemente wurden von Microsoft erstellt, andere stammen aus der PowerShell-Community.
Microsoft empfiehlt, dass Sie den Inhalt und den Code der Elemente in diesem Katalog vor der Installation überprüfen.

Wenn Sie ein Element entdecken, das Ihrer Meinung nach nicht mit guten Absichten veröffentlicht wurde, klicken Sie auf der Elementseite auf **Report Abuse** (Missbrauch melden).

### <a name="install"></a>Installation

Führen Sie je nach Elementtyp das Cmdlet [Install-Module][] oder [Install-Script][] aus, um ein Element aus dem Katalog für die Verwendung zu installieren.

[Install-Module][] installiert das Modul standardmäßig in `$env:ProgramFiles\WindowsPowerShell\Modules`.
Dafür ist ein Administratorkonto erforderlich. Wenn Sie den Parameter `-Scope CurrentUser` hinzufügen, wird das Modul in `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` installiert.

[Install-Script][] installiert das Skript standardmäßig in `$env:ProgramFiles\WindowsPowerShell\Scripts`.
Dafür ist ein Administratorkonto erforderlich. Wenn Sie den Parameter `-Scope CurrentUser` hinzufügen, wird das Skript in `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` installiert.

[Install-Module][] und [Install-Script][] installieren standardmäßig die aktuellste Version eines Elements.
Fügen Sie den Parameter `-RequiredVersion` hinzu, um eine ältere Version des Elements zu installieren.

### <a name="deploy"></a>Bereitstellen

Klicken Sie auf der Detailseite des Elements auf **Deploy to Azure Automation** (Bereitstellen in Azure Automation), um ein Element aus dem Katalog in Azure Automation bereitzustellen. Sie werden zum Azure-Verwaltungsportal umgeleitet, wo Sie sich mit den Anmeldeinformationen Ihres Azure-Kontos anmelden. Beachten Sie, dass das Bereitstellen von Elementen mit Abhängigkeiten alle Abhängigkeiten in Azure Automation bereitstellt. Sie können die Schaltfläche „Deploy to Azure Automation“ (Bereitstellen in Azure Automation) deaktivieren, indem Sie Ihren Elementmetadaten das Tag **AzureAutomationNotSupported** hinzufügen.

Weitere Informationen zu Azure Automation finden Sie in der [Azure Automation](/azure/automation)-Dokumentation.

## <a name="updating-items-from-the-powershell-gallery"></a>Aktualisieren von Elementen aus dem PowerShell-Katalog

Führen Sie zum Aktualisieren der installierten Elemente aus dem PowerShell-Katalog die Cmdlets [Update-Module][] oder [Update-Script][] aus. [Update-Module][] versucht, jedes mithilfe von [Install-Module][] installierte Modul zu aktualisieren, wenn es ohne zusätzliche Parameter ausgeführt wird. Um Module einzeln zu aktualisieren, fügen Sie den Parameter `-Name` hinzu.

Ähnlich versucht [Update-Script][], jedes durch Ausführung von [Install-Script][] installierte Skript zu aktualisieren, wenn es ohne zusätzliche Parameter ausgeführt wird. Um Skripts einzeln zu aktualisieren, fügen Sie den Parameter `-Name` hinzu.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>Listenelemente, die Sie aus dem PowerShell-Katalog installiert haben

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