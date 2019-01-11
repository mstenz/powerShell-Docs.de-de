---
ms.date: 12/12/2018
keywords: DSC, Powershell, Resource, Katalog, setup
title: Installieren zusätzlicher DSC-Ressourcen
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401694"
---
# <a name="install-additional-dsc-resources"></a>Installieren zusätzlicher DSC-Ressourcen

PowerShell umfasst mehrere Out-of-the-Box-Ressourcen für Desired State Configuration (DSC). Die **"psdesiredstateconfiguration"** -Modul enthält alle OOB-DSC-Ressourcen für Ihre spezifischen Instanz von PowerShell verfügbar.

Dies ist eine Liste mit den OOB-Ressourcen, die in PowerShell 4.0 und eine Beschreibung der Funktionen von der Ressource enthalten.

> [!NOTE]
> Dies ist eine unvollständige Liste, wie die Anzahl der OOB-Ressourcen mit jeder Version von PowerShell geworden ist.

|Ressource  |Beschreibung  |
|---------|---------|
|**File**|Steuert den Status der Dateien und Verzeichnisse. Kopiert Dateien aus einer **Quelle** auf eine **Ziel** und aktualisiert sie bei der **Quelle** Änderungen durch Vergleichen von Datumsangaben, Prüfsummen und Hashes.|
|**Archive**|Entpacken Archive und einer angegebenen Position. Überprüft die Archive mit einem angegebenen **Prüfsumme**.|
|**Environment**|Verwaltet Umgebungsvariablen.|
|**Gruppe**|Lokale Gruppen verwaltet und steuert die Gruppenmitgliedschaft.|
|**Log**|Schreibt Meldungen an die `Microsoft-Windows-Desired State Configuration/Analytic` Ereignisprotokoll.|
|**Paket**|Installiert oder deinstalliert Pakete mit **Argumente**, **LogPath**, **ReturnCode**, andere Einstellungen.|
|**Registry**|Verwaltet Registrierungsschlüssel und-Werte an.|
|**Script**|Können Sie entwerfen Ihre eigenen [Get-Test-Set](../resources/get-test-set.md) Skriptblöcken.|
|**Service**|Windows Services konfiguriert.|
|**User** |Verwaltet die lokale Benutzer und -Attribute.|
|**WindowsFeature**|Verwaltet die Rollen und Features.|
|**WindowsProcess**|Konfiguriert die Windows-Prozesse.|

Die OOB-Ressourcen können einen guten Ausgangspunkt für allgemeine Vorgänge. Wenn die OOB-Ressourcen Ihre Anforderungen nicht erfüllen, können Sie schreiben Ihre eigenen [benutzerdefinierte Ressource](../resources/authoringResource.md). Bevor Sie eine benutzerdefinierte Ressource zur Behebung Ihres Problems schreiben, sollten Sie über die große Anzahl von DSC-Ressourcen ansehen, die bereits von Microsoft und der PowerShell-Community erstellt wurden.

DSC-Ressourcen finden Sie in beiden die [PowerShell-Katalog](https://www.powershellgallery.com/) und [GitHub](https://github.com/). Sie können DSC-Ressourcen auch direkt über die PowerShell-Konsole mit installieren [PowerShellGet](/powershell/module/powershellget/).

## <a name="installing-powershellget"></a>Installieren von PowerShellGet

Um festzustellen, ob Sie bereits haben **PowerShell** erhalten, oder um Hilfe bei der Installation erhalten zu können, finden Sie unter der folgenden Anleitung: [Installieren von PowerShellGet](/powershell/gallery/installing-psget)

## <a name="finding-dsc-resources-using-powershellget"></a>Suchen von DSC-Ressourcen, die die Verwendung von PowerShellGet

Einmal **PowerShellGet** wird installiert auf Ihrem System können Sie ermitteln und installieren Sie die im gehosteten DSC-Ressourcen die [PowerShell-Katalog](https://www.powershellgallery.com/).

Verwenden Sie zunächst die [Find-DSCResource](/powershell/module/powershellget/find-dscresource) Cmdlet, um DSC-Ressourcen zu finden. Beim Ausführen von `Find-DSCResource` erstmals ausführen, finden Sie die folgende Aufforderung zum Installieren des Anbieters"NuGet".

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

Klicken Sie nach dem Drücken 'y' der "NuGet"-Anbieter installiert ist, finden Sie eine Liste von DSC-Ressourcen, die Sie aus dem PowerShell-Katalog installieren können.

> [!NOTE]
> Liste wird nicht angezeigt werden, da sie sehr groß ist.

Sie können auch angeben, die `-Name` mithilfe von Platzhaltern, Parameter oder `-Filter` Parameter ohne Platzhalter, um Ihre Suche einzugrenzen. In diesem Beispiel wird versucht, eine "Zeitzone" DSC-Ressource, die mit der die Platzhalter zu finden.

> [!IMPORTANT]
> Derzeit ist es jedoch ein Fehler in der `Find-DSCResource` -Cmdlet, das mithilfe von Platzhaltern in beiden verhindert, dass die `-Name` und `-Filter` Parameter. Das zweite Beispiel unten zeigt eine problemumgehung mithilfe `Where-Object`.

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

Sie können auch `Where-Object` zu DSC-Ressourcen über eine feiner abgestimmte Filtern zu suchen. Dieser Ansatz wird als unter Verwendung der integrierten Filterparameter langsamer sein.

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

Weitere Informationen zur Filterung finden Sie unter [Where-Object](/powershell/module/microsoft.powershell.core/where-object).

## <a name="installing-dsc-resources-using-powershellget"></a>Installieren von DSC-Ressourcen, die die Verwendung von PowerShellGet

Verwenden Sie zum Installieren einer DSC-Ressource die [Install-Module](/powershell/module/PowershellGet/Install-Module) Cmdlet angeben des Namens des Moduls angezeigt, die unter **Modul** Name in den Suchergebnissen.

Die Ressource "Zeitzone" ist also, d. h. das Modul in diesem Beispiel wird installiert im Modul "ComputerManagementDSC" vorhanden.

> [!NOTE]
> Wenn Sie nicht im PowerShell-Katalog vertrauenswürdige haben, Sie sehen, dass die Warnung unter der Aufforderung zur Bestätigung, und installiert, Sie anweisen, wie in nachfolgender eingabeaufforderungen zu vermeiden.

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Drücken Sie "y", um den Vorgang fortzusetzen, installieren das Modul aus. Nach der Installation können Sie überprüfen, ob mithilfe die neue Ressource installiert [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).

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

Sie können auch andere Ressourcen in Ihrem neu installierte Modul anzeigen, durch Angabe der `-ModuleName` Parameter.

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
