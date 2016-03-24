# Bekannte Probleme und Einschränkungen bei DSC (Desired State Configuration)

Wichtige Änderung: Zertifikate zum Verschlüsseln und Entschlüsseln von Kennwörtern in DSC-Konfigurationen funktionieren nach der Installation von WMF 5.0 RTM ggf. nicht
--------------------------------------------------------------------------------------------------------------------------------

In den Versionen WMF 4.0 und WMF 5.0 Preview lässt DSC in der Konfiguration keine Kennwörter mit mehr als 121 Zeichen zu. DSC erzwang das Verwenden kurzer Kennwörter, auch wenn längere und sichere Kennwörter gewünscht waren. Dank dieser wichtigen Änderungen können Kennwörter in der DSC-Konfiguration nun eine beliebige Länge haben.

**Lösung:** Erstellen Sie das Zertifikat neu, indem Sie Data Encipherment oder Key Encipherment Key und Document Encryption Enhanced Key (1.3.6.1.4.1.311.80.1) verwenden. Im TechNet-Artikel <https://technet.microsoft.com/en-us/library/dn807171.aspx> finden Sie weitere Informationen.


DSC-Cmdlets funktionieren nach Installation von WMF 5.0 RTM ggf. nicht mehr
------------------------------------------------------------------------------------
„Start-DscConfiguration“ und andere DSC-Cmdlets funktionieren ggf. nach der Installation von WMF 5.0 RTM nicht mehr, und der folgende Fehler wird angezeigt:
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

**Lösung:** Löschen Sie „DSCEngineCache.mof“, indem Sie den folgenden Befehl mit erhöhten Rechten in einer PowerShell-Sitzung ausführen (Als Administrator ausführen):
    
```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```


DSC-Cmdlets funktionieren ggf. nicht, wenn die WMF 5.0 RTM-Version zusätzlich zur WMF 5.0 Production Preview-Version installiert wird
------------------------------------------------------
**Lösung:** Führen Sie den folgenden Befehl mit erhöhten Rechten in einer PowerShell-Sitzung aus (Als Administrator ausführen):
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```


Der LCM kann bei Verwenden von „Get-DscConfiguration“ im Debugmodus instabil werden
-------------------------------------------------------------------------------

Wenn der LCM im Debugmodus ist, kann das Drücken von STRG+C zum Bearbeiten von „Get-DscConfiguration“ bewirken, dass der LCM so instabil wird, dass die Mehrheit der DSC-Cmdlets nicht funktioniert.

**Lösung:** Drücken Sie während des Debuggens des Cmdlets „Get-DscConfiguration“ nicht STRG+C.


Stop-DscConfiguration bleibt ggf. im Debugmodus hängen
------------------------------------------------------------------------------------------------------------------------
Wenn der LCM im Debugmodus ist, kann „Stop-DscConfiguration“ möglicherweise beim Versuch hängenbleiben, einen Vorgang zu beenden, der mit „Get-DscConfiguration“ gestartet wurde.

**Lösung:** Beenden Sie das Debuggen des mit „Get-DscConfiguration“ gestarteten Vorgangs gemäß den Angaben im Abschnitt [Debuggen von DSC-Ressourcenskripts](#dsc-resource-script-debugging).


Im Debugmodus werden keine ausführlichen Fehlermeldungen angezeigt
-----------------------------------------------------------------------------------
Wenn der LCM im Debugmodus ist, werden von DSC-Ressourcen keine ausführlichen Fehlermeldungen angezeigt.

**Lösung:** Deaktivieren Sie den *Debugmodus*, um ausführliche Meldungen der Ressource anzuzeigen.


„Invoke-DscResource“-Vorgänge können vom Cmdlet „Get-DscConfigurationStatus“ nicht abgerufen werden
--------------------------------------------------------------------------------------
Nach Verwenden des Cmdlets „Invoke-DscResource“ zum direkten Aufrufen von Methoden einer Ressource können die Datensätze eines solchen Vorgangs später nicht mit „Get-DscConfigurationStatus“ abgerufen werden.

**Lösung:** Keine.


„Get-DscConfigurationStatus“ gibt Pullzyklusvorgänge mit dem Typ *Consistency* zurück
---------------------------------------------------------------------------------
Wenn ein Knoten auf den PULL-Aktualisierungsmodus festgelegt ist, meldet das Cmdlet „Get-DscConfigurationStatus“ den Vorgangstyp als *Consistency* anstatt als *Initial*.

**Lösung:** Keine.

Das Cmdlet „Invoke-DscResource“ gibt Meldungen nicht in der Reihenfolge ihrer Erstellung zurück
---------------------------------------------------------------------------------
Das Cmdlet „Invoke-DscResource“ gibt ausführliche, Warn- und Fehlermeldungen nicht in der Reihenfolge zurück, in der sie vom LCM oder der DSC-Ressource erstellt wurden.

**Lösung:** Keine.


Bei Verwendung mit „Invoke-DscResource“ ist das Debuggen von DSC-Ressourcen nicht einfach
-----------------------------------------------------------------------
Wenn der LCM im Debugmodus ausgeführt wird (unter [Debuggen von DSC-Ressourcenskripts](#dsc-resource-script-debugging) finden Sie weitere Details), bietet das Cmdlet „Invoke-DscResource“ keine Informationen zum Runspace, mit dem zum Debuggen eine Verbindung hergestellt werden soll.
**Lösung:** Zum Debuggen der DSC-Ressource müssen Sie zum Ermitteln des Runspaces und für ein Anfügen daran die Cmdlets **Get-PSHostProcessInfo**, **Enter-PSHostProcess**, **Get-Runspace** und **Debug-Runspace** verwenden.

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell 3932 DefaultAppDomain
powershell_ise 2304 DefaultAppDomain
WmiPrvSE 3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name ComputerName Type State Availability
-- ---- ------------ ---- ----- ------------
2 Runspace2 localhost Local Opened InBreakpoint
5 RemoteHost localhost Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```


Verschiedene Teilkonfigurationsdokumente für denselben Knoten dürfen keine identischen Ressourcennamen aufweisen
------------------------------------------------------------------------------------------

Wenn mehrere Teilkonfigurationen, die auf einem einzelnen Knoten bereitgestellt sind, identische Ressourcennamen aufweisen, kann ein Laufzeitfehler auftreten.

**Lösung:** Verwenden Sie unterschiedliche Namen für die dieselben Ressourcen in unterschiedlichen Teilkonfigurationen.


„Start-DscConfiguration –UseExisting“ funktioniert nicht mit „-Credential“
------------------------------------------------------------------

Bei Verwendung von „Start-DscConfiguration“ mit dem „–UseExisting“-Parameter wird der „–Credential“-Parameter ignoriert. DSC verwendet die Standardprozessidentität, um den Vorgang fortzusetzen. Dies bewirkt einen Fehler, wenn für das Fortsetzen auf einem Remoteknoten andere Anmeldeinformationen benötigt werden.

**Lösung:** Verwenden Sie für DSC-Remotevorgänge eine CIM-Sitzung:
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```


IPv6-Adressen als Knotennamen in DSC-Konfigurationen
--------------------------------------------------
IPv6-Adressen als Knotennamen in DSC-Konfigurationsskripts werden in dieser Version nicht unterstützt.

**Lösung:** Keine.


Debuggen klassenbasierter DSC-Ressourcen
--------------------------------------
Das Debuggen klassenbasierter DSC-Ressourcen wird in dieser Version nicht unterstützt.

**Lösung:** Keine.


Variablen und Funktionen, die im Bereich „$script“ in klassenbasierten DSC-Ressourcen definiert werden, bleiben bei mehreren Aufrufen einer DSC-Ressource nicht erhalten. 
-------------------------------------------------------------------------------------------------------------------------------------

Mehrere aufeinander folgende Aufrufe von „Start-DSCConfiguration“ misslingen, wenn die Konfiguration klassenbasierte Ressourcen mit im Bereich „$script“ definierten Variablen oder Funktionen verwendet.

**Lösung:** Definieren Sie alle Variablen und Funktionen in der DSC-Ressourcenklasse selbst. Keine Variablen/Funktionen aus dem Bereich „$script“.


Debuggen von DSC-Ressourcen, wenn eine Ressource „PSDscRunAsCredential“ verwendet
----------------------------------------------------------------------
Das Debuggen von DSC-Ressourcen, wenn eine Ressource *PSDscRunAsCredential* in der Konfiguration verwendet, wird in dieser Version nicht unterstützt.

**Lösung:** Keine.


„PsDscRunAsCredential“ wird für zusammengesetzte DSC-Ressourcen nicht unterstützt
----------------------------------------------------------------

**Lösung:** Verwenden Sie, falls verfügbar, die „Credential“-Eigenschaft. Beispiel für „ServiceSet“ und „WindowsFeatureSet“


*Get-DscResource -Syntax* spiegelt „PsDscRunAsCredential“ nicht ordnungsgemäß wider
-------------------------------------------------------------------------
„Get-DscResource -Syntax“ spiegelt „PsDscRunAsCredential“ nicht ordnungsgemäß wider, wenn eine Ressource das Element als erforderlich kennzeichnet oder es nicht unterstützt.

**Lösung:** Keine. Die Erstellungskonfiguration in ISE spiegelt jedoch ordnungsgemäße Metadaten zur „PsDscRunAsCredential“-Eigenschaft wider, wenn IntelliSense verwendet wird.


„WindowsOptionalFeature“ ist unter Windows 7 nicht verfügbar
-----------------------------------------------------

Die DSC-Ressource „WindowsOptionalFeature“ ist unter Windows 7 nicht verfügbar. Diese Ressource erfordert das DISM-Modul und DISM-Cmdlets, die ab Windows 8 und in neueren Versionen des Windows-Betriebssystems verfügbar sind.


Das Ausführen von „Set-DscLocalConfigurationManager“ zum Festlegen einer Metakonfiguration für WMF 4.0- oder WMF 5.0 Production Preview-Builds funktioniert nicht
---------------------------------------------------------------------------------------------------------------------------------------

Es liegt ein Abwärtskompatibilitätsproblem vor, wenn „Set-DscLocalConfiguration“ für vorherige WMFs ausgeführt wird. Sie sehen diese Fehlermeldung, die besagt, dass der neu hinzugefügte „-Force“-Parameter auf dem Zielcomputer nicht verfügbar ist.
```powershell
Set-DscLocalConfigurationManager -Path . -Verbose -ComputerName WIN-3B576EM3669
VERBOSE: Performing the operation "Start-DscConfiguration: SendMetaConfigurationApply" on target "MSFT_DSCLocalConfigurationManager".
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendMetaConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
The WinRM client cannot process the request. The object contains an unrecognized argument: "Force". Verify that the spelling of the argument name is correct.
+ CategoryInfo : MetadataError: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : HRESULT 0x803381e1
+ PSComputerName : WIN-3B576EM3669
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Set-DscLocalConfigurationManager finished in 0.121 seconds.
```
**Lösung:** Führen Sie diese Schritte aus, um mit „Invoke-CimMethod“ die zugrunde liegende CIM-Methode direkt aufzurufen, um die Metakonfiguration festzulegen.
```powershell
$computerName = "WIN-3B576EM3669"
$mofPath = "C:\$computerName.meta.mof"
$configurationData = [Byte[]][System.IO.File]::ReadAllBytes($mofPath)
$totalSize = [System.BitConverter]::GetBytes($configurationData.Length + 4 )
$configurationData = $totalSize + $configurationData
Invoke-CimMethod -Namespace root/microsoft/windows/desiredstateconfiguration -Class MSFT_DSCLocalConfigurationManager -Name SendMetaConfigurationApply -Arguments @{ConfigurationData = [Byte[]]$configurationData} -Verbose -ComputerName $computerName
VERBOSE: Performing the operation "Invoke-CimMethod: SendMetaConfigurationApply" on target "MSFT_DSCLocalConfigurationManager".
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendMetaConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/microsoft/windows/desiredstateconfiguration'.
VERBOSE: An LCM method call arrived from computer WIN-3B576EM3669 with user sid S-1-5-21-2127521184-1604012920-1887927527-5557045.
VERBOSE: [WIN-3B576EM3669]: LCM: [ Start Set ]
VERBOSE: [WIN-3B576EM3669]: LCM: [ Start Resource ] [MSFT_DSCMetaConfiguration]
VERBOSE: [WIN-3B576EM3669]: LCM: [ Start Set ] [MSFT_DSCMetaConfiguration]
VERBOSE: [WIN-3B576EM3669]: LCM: [ End Set ] [MSFT_DSCMetaConfiguration] in 0.4060 seconds.
VERBOSE: [WIN-3B576EM3669]: LCM: [ End Resource ] [MSFT_DSCMetaConfiguration]
VERBOSE: [WIN-3B576EM3669]: LCM: [ End Set ] in 0.4807 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

<!--HONumber=Mar16_HO2-->
