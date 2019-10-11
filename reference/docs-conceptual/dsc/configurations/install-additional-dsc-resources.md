---
ms.date: 12/12/2018
keywords: DSC,PowerShell,Ressource,Katalog,Setup
title: Installieren zusätzlicher DSC-Ressourcen
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954487"
---
# <a name="install-additional-dsc-resources"></a>Installieren zusätzlicher DSC-Ressourcen

PowerShell umfasst mehrere vorgefertigte Ressourcen für die Desired State Configuration (DSC). Das **PSDesiredStateConfiguration**-Modul enthält alle für Ihre spezifische Instanz von PowerShell verfügbaren OOB-DSC-Ressourcen.

Hier finden Sie eine Liste der in PowerShell 4.0 enthaltenen OOB-Ressourcen sowie Beschreibungen der Funktionen der Ressourcen.

> [!NOTE]
> Diese Liste ist unvollständig, da die Anzahl der OOB-Ressourcen mit jeder Version von PowerShell gewachsen ist.

|Ressource  |Beschreibung  |
|---------|---------|
|**File**|Steuert den Status der Dateien und Verzeichnisse. Kopiert Dateien aus einer **Quelle** in ein **Ziel** und aktualisiert sie bei Änderung der **Quelle** durch Vergleichen von Datumsangaben, Prüfsummen und Hashes.|
|**Archive**|Entpackt Archive an einem angegebenen Speicherort. Überprüft die Archive mit einer angegebenen **Prüfsumme**.|
|**Environment**|Verwaltet Umgebungsvariablen.|
|**Group**|Verwaltet lokale Gruppen und steuert die Gruppenmitgliedschaft.|
|**Log**|Schreibt Meldungen in das `Microsoft-Windows-Desired State Configuration/Analytic`-Ereignisprotokoll.|
|**Paket**|Installiert oder deinstalliert Pakete mit **Arguments**, **LogPath**, **ReturnCode** und anderen Einstellungen.|
|**Registry**|Verwaltet Registrierungsschlüssel und -werte.|
|**Script**|Ermöglicht Ihnen den Entwurf Ihrer eigenen [get-test-set](../resources/get-test-set.md)-Skriptblöcke.|
|**Service**|Konfiguriert Windows-Dienste.|
|**User** |Verwaltet lokale Benutzer und Attribute.|
|**WindowsFeature**|Verwaltet Rollen und Features.|
|**WindowsProcess**|Konfiguriert Windows-Prozesse.|

Die OOB-Ressourcen bieten einen guten Ausgangspunkt für allgemeine Vorgänge. Wenn die OOB-Ressourcen Ihre Anforderungen nicht erfüllen, können Sie Ihre eigene [benutzerdefinierte Ressource](../resources/authoringResource.md) schreiben. Bevor Sie eine benutzerdefinierte Ressource zur Behebung Ihres Problems schreiben, sollten Sie die große Anzahl von DSC-Ressourcen durchsehen, die bereits von Microsoft und der PowerShell-Community erstellt wurden.

DSC-Ressourcen finden Sie sowohl im [PowerShell-Katalog](https://www.powershellgallery.com/) als auch in [GitHub](https://github.com/). Sie können DSC-Ressourcen auch mit [PowerShellGet](/powershell/module/powershellget/) direkt über die PowerShell-Konsole installieren.

## <a name="installing-powershellget"></a>Installieren von PowerShellGet

Um festzustellen, ob Sie **PowerShell** bereits besitzen, oder um Hilfe bei der Installation zu erhalten, nutzen Sie die folgende Anleitung: [Installieren von PowerShellGet](/powershell/gallery/installing-psget).

## <a name="finding-dsc-resources-using-powershellget"></a>Suchen von DSC-Ressourcen mit PowerShellGet

Sobald **PowerShellGet** auf Ihrem System installiert ist, können Sie im [PowerShell-Katalog](https://www.powershellgallery.com/) gehostete DSC-Ressourcen ermitteln und installieren.

Suchen Sie zunächst mit dem [Find-DSCResource](/powershell/module/powershellget/find-dscresource)-Cmdlet DSC-Ressourcen. Wenn Sie `Find-DSCResource` erstmals ausführen, sehen Sie die folgende Aufforderung zum Installieren des „NuGet-Anbieters“.

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

Nach dem Drücken von „j“ wird der „NuGet“-Anbieter installiert, und Sie sehen eine Liste von DSC-Ressourcen, die Sie aus dem PowerShell-Katalog installieren können.

> [!NOTE]
> Die Liste wird hier nicht gezeigt, da sie sehr groß ist.

Sie können auch mithilfe von Platzhaltern den `-Name`-Parameter angeben, oder den `-Filter`-Parameter ohne Platzhalter, um Ihre Suche einzugrenzen. In diesem Beispiel wird versucht, eine DSC-Ressource „TimeZone“ mit Platzhaltern zu finden.

> [!IMPORTANT]
> Derzeit enthält das `Find-DSCResource`-Cmdlet jedoch einen Fehler, der sowohl im `-Name`- als auch im `-Filter`-Parameter die Suche mit Platzhaltern verhindert. Das zweite Beispiel zeigt eine Problemumgehung mit `Where-Object`.

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

Sie können auch mit `Where-Object` DSC-Ressourcen mit einer feiner abgestimmten Filterung suchen. Dieser Ansatz ist langsamer als die Verwendung der integrierten Filterparameter.

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

Weitere Informationen zur Filterung finden Sie unter [Where-Object](/powershell/module/microsoft.powershell.core/where-object).

## <a name="installing-dsc-resources-using-powershellget"></a>Installieren von DSC-Ressourcen mit PowerShellGet

Installieren Sie eine DSC-Ressource mit dem [Install-Module](/powershell/module/PowershellGet/Install-Module)-Cmdlet, wobei Sie den in den Suchergebnissen unter **ModuleName** angegebenen Namen des Moduls verwenden.

Da die Ressource „TimeZone“ sich im Modul „ComputerManagementDSC“ befindet, wird dieses Modul in diesem Beispiel installiert.

> [!NOTE]
> Wenn Sie den PowerShell-Katalog noch nicht als vertrauenswürdig eingestuft haben, sehen Sie die unten stehende Warnung mit der Aufforderung zur Bestätigung und Anleitungen, wie Sie nachfolgende Eingabeaufforderungen bei Installationen vermeiden können.

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Drücken Sie „j“, um mit dem Installieren des Moduls fortzufahren. Nach der Installation können Sie mit [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) überprüfen, ob die neue Ressource installiert ist.

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

Sie können mit Angabe des `-ModuleName`-Parameters auch andere Ressourcen in Ihrem neu installierten Modul anzeigen.

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a>Siehe auch

- [Was sind Ressourcen?](../resources/resources.md)
