# Verwenden eines DSC-Berichtsservers

> Gilt für: Windows PowerShell 5.0

> **Hinweis:** Der in diesem Thema beschriebene Berichtsserver ist in PowerShell 4.0 nicht verfügbar. Informationen zur Berichterstellung in PowerShell 4.0 finden Sie unter „Verwenden eines DSC-Kompatibilitätsservers“.

Die lokale Configuration Manager (LCM) eines Knotens kann so konfiguriert werden, dass Berichte zu seinem Konfigurationsstatus an einen Pullserver gesendet werden, der zum Abrufen dieser Daten abgefragt werden kann. Jedes Mal, wenn der Knoten eine Konfiguration überprüft und anwendet,
wird ein Bericht zum Berichtsserver gesendet. Diese Berichte werden in einer Datenbank auf dem Server gespeichert und können durch Aufrufen des Webdiensts für die Berichtserstellung abgerufen werden. Jeder Bericht enthält
Informationen zu den angewendeten Konfigurationen samt Zeitpunkt, verwendeten Ressourcen, ausgelösten Fehlern sowie Start- und Endzeiten.

## Konfigurieren eines Knotens zum Senden von Berichten

Sie weisen einen Knoten im **ReportServerWeb**-Block der LCM-Konfiguration des Knotens an, Berichte zu einem Server zu senden (weitere Informationen zum Konfigurieren des LCM
 finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](metaConfig.md)). Der Server, an den der Knoten Berichte sendet, muss als Pullwebserver eingerichtet werden (Sie können keine Berichte
 an eine SMB-Freigabe senden). Weitere Informationen zum Einrichten von Pullservern finden Sie unter [Einrichten eines DSC-Webpullservers](pullServer.md). Der Berichtsserver kann vom selben Dienst unterstützt werden,
 von dem der Knoten Konfigurationen und Ressourcen abruft. Es kann sich aber auch um einen anderen Dienst handeln.
 
 Im **ReportServerWeb**-Block geben Sie die URL des Pulldiensts
 und einen Registrierungsschlüssel an, der dem Server bekannt ist.
 
  Die folgende Konfiguration konfiguriert einen Knoten für das Abrufen von Konfiguration per Pull von einem Dienst und Senden von Berichten
 an einen Dienst auf einem anderen Server. 
 
```powershell
[DSCLocalConfigurationManager()]
configuration ReportClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PULL:8080/PSDSCPullServer.svc'
            RegistrationKey    = 'bbb9778f-43f2-47de-b61e-a0daff474c6d'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL               = 'http://CONTOSO-REPORT:8080/PSDSCReportServer.svc'
            RegistrationKey         = 'ba39daaa-96c5-4f2f-9149-f95c46460faa'
            AllowUnsecureConnection = $true
        }
    }
}
PullClientConfigID
```

## Abrufen von Berichtsdaten

Berichte, die zum Pullserver gesendet werden, gelangen in eine Datenbank auf dem Server. Die Berichte stehen über Aufrufe des Webdiensts zur Verfügung. Zum Abrufen von Berichten für einen bestimmten Knoten 
senden Sie eine HTTP-Anforderung an den Berichtswebdienst in der folgenden Form:
`http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentID = MyNodeAgentId)/Reports` 
`MyNodeAgentId` ist die Agent-ID des Knotens, für den Sie Berichte erhalten möchten. Durch Aufrufen von [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) auf einem Knoten können Sie die Agent-ID
dieses Knotens abrufen.

Die Berichte werden als ein Array von JSON-Objekten zurückgegeben.

Das folgende Skript gibt die Berichte für den Knoten zurück, auf dem es ausgeführt wird:

```powershell
function GetReport
{
    param($AgentId = "$((glcm).AgentId)", $serviceURL = "http://CONTOSO-REPORT:8080/PSDSCReportServer.svc")
    $requestUri = "$serviceURL/Nodes(AgentId= '$AgentId')/Reports"
    $request = Invoke-WebRequest -Uri $requestUri  -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" `
               -UseBasicParsing -Headers @{Accept = "application/json";ProtocolVersion = "2.0"} `
               -ErrorAction SilentlyContinue -ErrorVariable ev
    $object = ConvertFrom-Json $request.content
    return $object.value
}
```
    
## Anzeigen von Berichtsdaten

Wenn Sie eine Variable auf das Ergebnis der **GetReport**-Funktion festlegen, können Sie die einzelnen Felder in einem Element des Arrays anzeigen, das zurückgegeben wird:

```powershell
$reports = GetReport
$reports[1]

JobId                : 71515ae8-7294-40a3-8137-fc85bf4b678f
OperationType        : Consistency
RefreshMode          : 
Status               : 
ReportFormatVersion  : 1.0
ConfigurationVersion : 2.0.0
StartTime            : 02/08/2016 01:28:54
EndTime              : 02/08/2016 01:28:57
RebootRequested      : False
Errors               : {}
StatusData           : {{"NumberOfResources":"2","Locale":"en-US","ResourcesInDesiredState":[{"ResourceId":"[WindowsFeature]MyFeatureInstance","SourceI
                       nfo":"C:\\ReportTest\\ClientConfig.ps1::4::9::WindowsFeature","ModuleName":"PsDesiredStateConfiguration","ModuleVersion":"1.0","
                       ConfigurationName":"ClientConfig","ResourceName":"WindowsFeature"},{"ResourceId":"[WindowsFeature]My2ndFeatureInstance","SourceI
                       nfo":"C:\\ReportTest\\ClientConfig.ps1::8::9::WindowsFeature","ModuleName":"PsDesiredStateConfiguration","ModuleVersion":"1.0","
                       ConfigurationName":"ClientConfig","ResourceName":"WindowsFeature"}]}}
```

Beachten Sie, dass das Feld **StatusData** ein Objekt mit drei Eigenschaften ist: **NumberOfResources**, **Locale** und **ResourcesInDesiredState**. Die **ResourcesInDesiredState**-Eigenschaft
ist ein Array von Objekten, von denen jedes eine Reihe von Eigenschaften hat. Das folgende Skript verwendet einen einzelnen Bericht als Parameter, durchläuft dessen **ResourcesInDesiredState**-Array
und gibt das Ergebnis in der Konsole aus:
 
```powershell
function GetStatusData
{
    param ($Report)
    $statusData = $Report.StatusData | ConvertFrom-Json

    $Resources = $statusData.ResourcesInDesiredState

    Foreach ($Resource in $Resources)
    {
        Write-Host 'ResourceId: ' $Resource.ResourceId
        Write-Host 'SourceInfo: ' $Resource.SourceInfo
        Write-Host 'ModuleName: ' $Resource.ModuleName
        Write-Host 'ModuleVersion: ' $Resource.ModuleVersion
        Write-Host 'ConfigurationName: ' $Resource.ConfigurationName
        Write-Host 'ResourceName: ' $Resource.ResourceName
        Write-Host
    }
}
```

Hier eine Beispielausgabe nach Aufrufen der **GetStatusData**-Funktion:

```powershell
GetStatusData -Report $report[1]

ResourceId:  [WindowsFeature]MyFeatureInstance
SourceInfo:  C:\ReportTest\ClientConfig.ps1::4::9::WindowsFeature
ModuleName:  PsDesiredStateConfiguration
ModuleVersion:  1.0
ConfigurationName:  ClientConfig
ResourceName:  WindowsFeature

ResourceId:  [WindowsFeature]My2ndFeatureInstance
SourceInfo:  C:\ReportTest\ClientConfig.ps1::8::9::WindowsFeature
ModuleName:  PsDesiredStateConfiguration
ModuleVersion:  1.0
ConfigurationName:  ClientConfig
ResourceName:  WindowsFeature
```

Beachten Sie, dass diese Beispiele dazu dienen, Ihnen eine Vorstellung der Möglichkeiten von Berichtsdaten zu geben. Eine Einführung in das Arbeiten mit JSON in PowerShell finden Sie unter
[Arbeiten mit JSON und PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).

## Weitere Informationen
>[Konfigurieren des lokalen Konfigurations-Managers](metaConfig.md)
>[Einrichten eines DSC-Webpullservers](pullServer.md)
>[Einrichten eines DSC-Pullclients mithilfe von Konfigurationsnamen](pullClientConfigNames.md)
<!--HONumber=Feb16_HO4-->
