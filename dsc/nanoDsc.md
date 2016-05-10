# Verwenden von DSC unter Nano Server

> Gilt für: Windows PowerShell 5.0

**DSC unter Nano Server** ist ein optionales Paket im Ordner `NanoServer\Packages` des Windows Server 2016-Mediums. Das Paket kann installiert werden, wenn Sie eine VHD (virtuelle Festplatte) für einen Nano Server erstellen, indem Sie
**Microsoft-NanoServer-DSC-Package** als Wert des Parameters **Packages** der Funktion **New-NanoServerImage** angeben. Wenn Sie beispielsweise eine virtuelle Festplatte für einen virtuellen
Computer erstellen, würde der Befehl wie folgt aussehen:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Informationen zum Installieren und Verwenden von Nano Server sowie zum Verwalten von Nano Server mit PowerShell-Remoting finden Sie unter 
[Erste Schritte mit Nano Server](https://technet.microsoft.com/en-us/library/mt126167.aspx).


## Unter Nano Server verfügbare DSC-Funktionen

 Da Nano Server im Vergleich mit einer Vollversion von Windows Server nur einen eingeschränkten Satz von APIs unterstützt, besitzt DSC zurzeit unter Nano Server nicht denselben, vollständigen Funktionsumfang wie DSC, das auf 
 vollständigen SKUs ausgeführt wird. DSC unter Nano Server befindet sich in der aktiven Entwicklung, und der Funktionsumfang ist noch nicht vollständig.
 
 Die folgenden DSC-Funktionen sind zurzeit unter Nano Server verfügbar: 


* Sowohl Push- als auch Pull-Modus
* Alle DSC-Cmdlets, die eine Vollversion von Windows Server beinhaltet, einschließlich der folgenden: 
  * [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx)
  * [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx)
        
  * [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx)
        
  * [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [Stop-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)      
  * [Publish-DscConfiguraiton](https://technet.microsoft.com/en-us/library/mt517875.aspx) 
  * [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [Restore-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407383.aspx)

  * [Remove-DscConfigurationDocument](https://technet.microsoft.com/en-us/library/mt143544.aspx)
    
  * [Get-DscConfigurationStatus](https://technet.microsoft.com/en-us/library/mt517868.aspx)
        
  * [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)

  * [New-DscChecksum](https://technet.microsoft.com/en-us/library/dn521622.aspx)
    
* Kompilieren von Konfigurationen (siehe [DSC-Konfigurationen](configurations.md))
* Kompilieren von Metakonfigurationen (siehe [Konfigurieren des lokalen Konfigurations-Managers](metaConfig.md))
* [Ausführen von DSC mit Benutzeranmeldeinformationen („Ausführen als“, RunAs)](runAsUser.md)
* Klassenbasierte Ressourcen (siehe [Schreiben einer benutzerdefinierten DSC-Ressource mit PowerShell-Klassen](authoringResourceClass.md))
* [Angeben knotenübergreifender Abhängigkeiten](crossNodeDependencies.md) 
* [Ressourcenversionsverwaltung](sxsResource.md)
* Ereignisse
* Pullclient (Konfigurationen und Ressourcen) (siehe [Einrichten eines Pullclients mithilfe von Konfigurationsnamen](pullClientConfigNames.md))
* [Teilkonfigurationen (Pull und Push)](partialConfigs.md)
* [Berichterstattung an Pullserver](reportServer.md) 
* MOF-Verschlüsselung
* Protokollierung
* Azure Automation-DSC-Berichte


* Ressourcen, die funktionieren
  * [Archive](archiveResource.md)
  * [Environment](environmentResource.md)
  * [File](fileResource.md)
  * [Group](groupResource.md)
  * GroupSet
  * [Log](logResource.md)
  * ProcessSet
  * [Registry](registryResource.md)
  * [Service](serviceResource.md)
  * ServiceSet
  * [Script](scriptResource.md)
  * [User](userResource.md)
  * WindowsPackageCab
  * [WindowsProcess](windowsProcessResource.md)

  * WaitForAll (siehe [Angeben knotenübergreifender Abhängigkeiten](crossNodeDependencies.md))
  * WaitForAny (siehe [Angeben knotenübergreifender Abhängigkeiten](crossNodeDependencies.md))
  * WaitForSome (siehe [Angeben knotenübergreifender Abhängigkeiten](crossNodeDependencies.md))

## Unter Nano Server nicht verfügbare DSC-Funktionen

Die folgenden DSC-Funktionen sind zurzeit unter Nano Server nicht verfügbar:

* Pullserver: Sie können zurzeit keinen Pullserver unter Nano Server einrichten.
* Alle Funktionen, die nicht in der Liste der Funktionen aufgeführt sind, funktionieren.

## Verwenden benutzerdefinierter DSC-Ressourcen unter Nano Server
 
Aufgrund eingeschränkter Sätze von Windows-APIs und CLR-Bibliotheken, die unter Nano Server verfügbar sind, funktionieren DSC-Ressourcen, die in der vollständigen CLR-Version von Windows funktionieren, nicht notwendigerweise auch unter Nano Server. 
Führen Sie zuerst End-to-End-Tests durch, bevor Sie benutzerdefinierte DSC-Ressourcen in einer Produktionsumgebung bereitstellen.

## Weitere Informationen
- [Erste Schritte mit Nano Server](https://technet.microsoft.com/en-us/library/mt126167.aspx)

<!--HONumber=Apr16_HO4-->


