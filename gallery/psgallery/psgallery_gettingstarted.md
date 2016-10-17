# Erste Schritte mit dem PowerShell-Katalog

## Was ist der PowerShell-Katalog?

Der PowerShell-Katalog ist das zentrale Repository für PowerShell-Inhalte.
Sie finden darin nützliche PowerShell-Module, die PowerShell-Befehle und Desired State Configuration-Ressourcen (DSC) enthalten. Sie finden dort auch PowerShell-Skripts, von denen einige PowerShell-Workflows enthalten, eine Reihe von Aufgaben umreißen und Sequenzierungen für diese Aufgaben bereitstellen.
Einige dieser Elemente wurden von Microsoft erstellt, andere stammen aus der PowerShell-Community.

## Anforderungen

Das Herunterladen von Elementen aus dem PowerShell-Katalog auf Ihr System erfordert das [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)-Modul. Das PowerShellGet-Modul ist in jedem der folgenden Downloads enthalten. Um diese Elemente aus dem PowerShell-Katalog herunterzuladen, müssen Sie sich nicht anmelden.

-   [Windows 10](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)
-   [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkId=398175)
-   [MSI Installer (für PowerShell 3 und 4)](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

PowerShellGet erfordert außerdem den [NuGet-Anbieter](http://go.microsoft.com/fwlink/?LinkId=722208), um mit dem PowerShell-Katalog zu funktionieren. Sie werden aufgefordert, den NuGet-Anbieter automatisch bei der ersten Verwendung von PowerShellGet zu installieren, wenn der NuGet-Anbieter sich nicht an einem der folgenden Speicherorte befindet:

-   $env:ProgramFiles\\PackageManagement\\ProviderAssemblies
-   $env:LOCALAPPDATA\\PackageManagement\\ProviderAssemblies

Alternativ können Sie **Install-PackageProvider -Name NuGet -Force** ausführen, um den Download und die Installation des NuGet-Anbieters zu automatisieren.

  
Wenn Sie eine älteren Version von NuGet als 2.8.5.201 besitzen, müssen Sie die folgenden PowerShell-Cmdlets aufrufen, um die neueste Version von NuGet zu installieren.

1.  Install-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force
2.  Import-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force
3.  Löschen Sie die ältere Version von NuGet aus dem obigen Installationsverzeichnis.

Weitere Informationen hierzu finden Sie unter <http://oneget.org/>.

  
Hinweis: Aufgrund von Änderungen an den Paketerstellungsformaten empfehlen wir, dass Sie auf die neueste Version von PowerShellGet und PackageManagement zu aktualisieren, um Elemente zu installieren, die kürzlich aktualisiert wurden. PowerShellGet ist im Lieferumfang von Windows 10 mit inbegriffen. [Hier](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409) können Sie mehr darüber erfahren.
PowerShellGet ist auch ein Teil des Windows Management Framework (WMF) 5.0, das Sie [hier](http://go.microsoft.com/fwlink/?LinkId=398175) herunterladen können.

## Suchen von Elementen im PowerShell-Katalog

Sie können Elemente im PowerShell-Katalog mithilfe des Steuerelements **Suchen** auf dieser Website suchen. Alternativ können Sie die Seiten zu Modulen und Skripts durchsuchen. Sie können Elemente im PowerShell-Katalog je nach Elementtyp auch mit **-Repository PSGallery**über die Cmdlets [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) und [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)

Das Filtern von Ergebnissen im Katalog kann über die folgenden Parameter von [Find-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) und [Find-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) erfolgen:

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

Wenn Sie nur spezifische DSC-Ressourcen im Katalog suchen, können Sie das Cmdlet [**Find-DscResource**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) ausführen.
[**Find-DscResource**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) gibt Daten zu DSC-Ressourcen zurück, die im Katalog enthalten sind. Da DSC-Ressourcen immer als Teil eines Moduls geliefert werden, müssen Sie [Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) ausführen, um diese DSC-Ressourcen zu installieren.

## Informationen zu den Elementen im PowerShell-Katalog

Wenn Sie ein Element ermittelt haben, an dem Sie interessiert sind, möchten Sie möglicherweise weitere Informationen erhalten. Diese finden Sie auf der Katalogseite dieses bestimmten Elements. Dort finden Sie alle Metadaten, die mit dem Element hochgeladen wurden. Diese Metadaten eines Elements werden von dem jeweiligen Autoren bereitgestellt und nicht von Microsoft überprüft. Der Besitzer des Elements ist eng an das Katalog-Konto gebunden, das für die Veröffentlichung des Elements verwendet wurde, und ist vertrauenswürdiger als das Feld „Autor“.

Wenn Sie ein Element entdecken, das Ihrer Meinung nach nicht mit guten Absichten veröffentlicht wurde, klicken Sie auf der Elementseite auf **Report Abuse** (Missbrauch melden).

Wenn Sie [Find-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) oder [Find-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) ausführen, können Sie diese Daten im zurückgegebenen PSGetModuleInfo-Objekt anzeigen. Die Ausführung von [**Find-Module -Name PSReadLine -Repository PSGallery | Get-Member**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) gibt beispielsweise Daten zum PSReadLine-Modul im Katalog zurück.

## Herunterladen von Elementen aus dem PowerShell-Katalog

Wir empfehlen den folgenden Prozess für das Herunterladen von Elementen aus dem PowerShell-Katalog:

### Überprüfen

Führen Sie zum Herunterladen eines Elements aus dem Katalog für die Überprüfung je nach Elementtyp die Cmdlets [**Save-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) oder [**Save-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). Dadurch können Sie das Element lokal speichern, ohne es zu installieren, und den Inhalt des Elements überprüfen. Denken Sie daran, das gespeicherte Element manuell löschen.

Einige dieser Elemente wurden von Microsoft erstellt, andere stammen aus der PowerShell-Community. Microsoft empfiehlt, dass Sie den Inhalt und den Code der Elemente in diesem Katalog vor der Installation überprüfen.

Wenn Sie ein Element entdecken, das Ihrer Meinung nach nicht mit guten Absichten veröffentlicht wurde, klicken Sie auf der Elementseite auf **Report Abuse** (Missbrauch melden).

### Installation

Führen Sie je nach Elementtyp die Cmdlets [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) oder [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), um ein Element aus dem Katalog für die Verwendung zu installieren.

[Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) installiert das Modul standardmäßig in $env:ProgramFiles\\WindowsPowerShell\\Modules. Dafür ist ein Administratorkonto erforderlich. Wenn Sie den Parameter **-Scope CurrentUser** hinzufügen, wird das Modul nach $env:USERPROFILE\\Documents\\WindowsPowerShell\\Modules installiert.

[Install-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) installiert das Skript standardmäßig nach $env:ProgramFiles\\WindowsPowerShell\\Scripts. Dafür ist ein Administratorkonto erforderlich. Wenn Sie den Parameter **-Scope CurrentUser** hinzufügen, wird das Skript nach $env:USERPROFILE\\Documents\\WindowsPowerShell\\Scripts installiert.

[Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) und [Install-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) installieren standardmäßig die aktuellste Version eines Elements. Fügen Sie zum Installieren einer älteren Version des Elements den Parameter **-RequiredVersion** hinzu.

### Stellen Sie

Klicken Sie auf der Detailseite des Elements auf **Deploy to Azure Automation** (Bereitstellen in Azure Automation), um ein Element aus dem Katalog in Azure Automation bereitzustellen. Sie werden zum Azure-Verwaltungsportal umgeleitet, wo Sie sich mit den Anmeldeinformationen Ihres Azure-Kontos anmelden. Beachten Sie, dass das Bereitstellen von Elementen mit Abhängigkeiten alle Abhängigkeiten in Azure Automation bereitstellt. Sie können die Schaltfläche „Deploy to Azure Automation“ (Bereitstellen in Azure Automation) deaktivieren, indem Sie Ihren Elementmetadaten das Tag **AzureAutomationNotSupported** hinzufügen.

Weitere Informationen zu Azure Automation finden Sie auf der [Azure Automation-Website](http://azure.microsoft.com/en-us/services/automation/).

## Aktualisieren von Elementen aus dem PowerShell-Katalog

Führen Sie zum Aktualisieren der installierten Elemente aus dem PowerShell-Katalog die Cmdlets [Update-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) oder [Update-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) aus. [Update-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) versucht, jedes mithilfe von [Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) installierte Modul zu aktualisieren, wenn es ohne zusätzliche Parameter ausgeführt wird.
Um Module einzeln zu aktualisieren, fügen die **-Namen** Parameter.

Ebenso versucht [Update-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), jedes mithilfe von [Install-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) installierte Script zu aktualisieren, wenn es ohne zusätzliche Parameter ausgeführt wird.
Fügen Sie den Parameter **-Name** hinzu, um Skripts selektiv zu aktualisieren.

## Listenelemente, die Sie aus dem PowerShell-Katalog installiert haben

Führen Sie das Cmdlet [**Get-InstalledModule**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) aus, um herauszufinden, welche Module Sie aus dem PowerShell-Katalog installiert haben. Dieser Befehl listet alle Module auf, die direkt aus dem PowerShell-Katalog auf Ihrem System installiert wurden.

Um herauszufinden, welche Skripts Sie aus dem PowerShell-Katalog installiert haben, führen Sie das Cmdlet [**Get-InstalledScript**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) aus. Dieser Befehl listet alle Skripts auf, die direkt aus dem PowerShell-Katalog auf Ihrem System installiert wurden.


<!--HONumber=Aug16_HO3-->


