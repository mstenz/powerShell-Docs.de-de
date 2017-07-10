---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: f39328b240a36deb40d484c4aedb889cee91dc8d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="desired-state-configuration-dsc-known-issues-and-limitations" class="xliff"></a>
# Bekannte Probleme und Einschränkungen bei DSC (Desired State Configuration)

<a id="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm" class="xliff"></a>
Wichtige Änderung: Zertifikate zum Verschlüsseln und Entschlüsseln von Kennwörtern in DSC-Konfigurationen funktionieren nach der Installation von WMF 5.0 RTM ggf. nicht
--------------------------------------------------------------------------------------------------------------------------------

In den Versionen WMF 4.0 und WMF 5.0 Preview lässt DSC in der Konfiguration keine Kennwörter mit mehr als 121 Zeichen zu. DSC erzwang das Verwenden kurzer Kennwörter, auch wenn längere und sichere Kennwörter gewünscht waren. Dank dieser wichtigen Änderungen können Kennwörter in der DSC-Konfiguration nun eine beliebige Länge haben.

**Lösung:** Erstellen Sie das Zertifikat neu, indem Sie Data Encipherment oder Key Encipherment Key und Document Encryption Enhanced Key (1.3.6.1.4.1.311.80.1) verwenden. Im TechNet-Artikel <https://technet.microsoft.com/en-us/library/dn807171.aspx> finden Sie weitere Informationen.


<a id="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm" class="xliff"></a>
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


<a id="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview" class="xliff"></a>
DSC-Cmdlets funktionieren ggf. nicht, wenn die WMF 5.0 RTM-Version zusätzlich zur WMF 5.0 Production Preview-Version installiert wird
------------------------------------------------------
**Lösung:** Führen Sie den folgenden Befehl mit erhöhten Rechten in einer PowerShell-Sitzung aus (Als Administrator ausführen):
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```


<a id="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode" class="xliff"></a>
Der LCM kann bei Verwenden von „Get-DscConfiguration“ im Debugmodus instabil werden
-------------------------------------------------------------------------------

Wenn der LCM im Debugmodus ist, kann das Drücken von STRG+C zum Bearbeiten von „Get-DscConfiguration“ bewirken, dass der LCM so instabil wird, dass die Mehrheit der DSC-Cmdlets nicht funktioniert.

**Lösung:** Drücken Sie während des Debuggens des Cmdlets „Get-DscConfiguration“ nicht STRG+C.


<a id="stop-dscconfiguration-may-hang-in-debugmode" class="xliff"></a>
Stop-DscConfiguration bleibt ggf. im Debugmodus hängen
------------------------------------------------------------------------------------------------------------------------
Wenn der LCM im Debugmodus ist, kann „Stop-DscConfiguration“ möglicherweise beim Versuch hängenbleiben, einen Vorgang zu beenden, der mit „Get-DscConfiguration“ gestartet wurde.

**Lösung:** Beenden Sie das Debuggen des mit Get-DscConfiguration gestarteten Vorgangs gemäß den Angaben im Abschnitt [Debuggen von DSC-Ressourcen](https://msdn.microsoft.com/powershell/dsc/debugresource).


<a id="no-verbose-error-messages-are-shown-in-debugmode" class="xliff"></a>
Im Debugmodus werden keine ausführlichen Fehlermeldungen angezeigt
-----------------------------------------------------------------------------------
Wenn der LCM im Debugmodus ist, werden von DSC-Ressourcen keine ausführlichen Fehlermeldungen angezeigt.

**Lösung:** Deaktivieren Sie den *Debugmodus*, um ausführliche Meldungen der Ressource anzuzeigen.


<a id="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet" class="xliff"></a>
„Invoke-DscResource“-Vorgänge können vom Cmdlet „Get-DscConfigurationStatus“ nicht abgerufen werden
--------------------------------------------------------------------------------------
Nach Verwenden des Cmdlets „Invoke-DscResource“ zum direkten Aufrufen von Methoden einer Ressource können die Datensätze eines solchen Vorgangs später nicht mit „Get-DscConfigurationStatus“ abgerufen werden.

**Lösung:** Keine.


<a id="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency" class="xliff"></a>
„Get-DscConfigurationStatus“ gibt Pullzyklusvorgänge mit dem Typ *Consistency* zurück
---------------------------------------------------------------------------------
Wenn ein Knoten auf den PULL-Aktualisierungsmodus festgelegt ist, meldet das Cmdlet „Get-DscConfigurationStatus“ den Vorgangstyp als *Consistency* anstatt als *Initial*.

**Lösung:** Keine.

<a id="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced" class="xliff"></a>
Das Cmdlet „Invoke-DscResource“ gibt Meldungen nicht in der Reihenfolge ihrer Erstellung zurück
---------------------------------------------------------------------------------
Das Cmdlet „Invoke-DscResource“ gibt ausführliche, Warn- und Fehlermeldungen nicht in der Reihenfolge zurück, in der sie vom LCM oder der DSC-Ressource erstellt wurden.

**Lösung:** Keine.


<a id="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource" class="xliff"></a>
Bei Verwendung mit „Invoke-DscResource“ ist das Debuggen von DSC-Ressourcen nicht einfach
-----------------------------------------------------------------------
Wenn der LCM im Debugmodus ausgeführt wird (weitere Details finden Sie unter [Debuggen von DSC-Ressourcen](https://msdn.microsoft.com/powershell/dsc/debugresource)), bietet das Invoke-DscResource-Cmdlet keine Informationen zum Runspace, mit dem zum Debuggen eine Verbindung hergestellt werden soll.
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


<a id="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names" class="xliff"></a>
Verschiedene Teilkonfigurationsdokumente für denselben Knoten dürfen keine identischen Ressourcennamen aufweisen
------------------------------------------------------------------------------------------

Wenn mehrere Teilkonfigurationen, die auf einem einzelnen Knoten bereitgestellt sind, identische Ressourcennamen aufweisen, kann ein Laufzeitfehler auftreten.

**Lösung:** Verwenden Sie unterschiedliche Namen für die dieselben Ressourcen in unterschiedlichen Teilkonfigurationen.


<a id="start-dscconfiguration-useexisting-does-not-work-with--credential" class="xliff"></a>
„Start-DscConfiguration –UseExisting“ funktioniert nicht mit „-Credential“
------------------------------------------------------------------

Bei Verwendung von „Start-DscConfiguration“ mit dem „–UseExisting“-Parameter wird der „–Credential“-Parameter ignoriert. DSC verwendet die Standardprozessidentität, um den Vorgang fortzusetzen. Dies bewirkt einen Fehler, wenn für das Fortsetzen auf einem Remoteknoten andere Anmeldeinformationen benötigt werden.

**Lösung:** Verwenden Sie für DSC-Remotevorgänge eine CIM-Sitzung:
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```


<a id="ipv6-addresses-as-node-names-in-dsc-configurations" class="xliff"></a>
IPv6-Adressen als Knotennamen in DSC-Konfigurationen
--------------------------------------------------
IPv6-Adressen als Knotennamen in DSC-Konfigurationsskripts werden in dieser Version nicht unterstützt.

**Lösung:** Keine.


<a id="debugging-of-class-based-dsc-resources" class="xliff"></a>
Debuggen klassenbasierter DSC-Ressourcen
--------------------------------------
Das Debuggen klassenbasierter DSC-Ressourcen wird in dieser Version nicht unterstützt.

**Lösung:** Keine.


<a id="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource" class="xliff"></a>
Variablen und Funktionen, die im Bereich „$script“ in klassenbasierten DSC-Ressourcen definiert werden, bleiben bei mehreren Aufrufen einer DSC-Ressource nicht erhalten. 
-------------------------------------------------------------------------------------------------------------------------------------

Mehrere aufeinander folgende Aufrufe von „Start-DSCConfiguration“ misslingen, wenn die Konfiguration klassenbasierte Ressourcen mit im Bereich „$script“ definierten Variablen oder Funktionen verwendet.

**Lösung:** Definieren Sie alle Variablen und Funktionen in der DSC-Ressourcenklasse selbst. Keine Variablen/Funktionen aus dem Bereich „$script“.


<a id="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential" class="xliff"></a>
Debuggen von DSC-Ressourcen, wenn eine Ressource „PSDscRunAsCredential“ verwendet
----------------------------------------------------------------------
Das Debuggen von DSC-Ressourcen, wenn eine Ressource *PSDscRunAsCredential* in der Konfiguration verwendet, wird in dieser Version nicht unterstützt.

**Lösung:** Keine.


<a id="psdscrunascredential-is-not-supported-for-dsc-composite-resources" class="xliff"></a>
„PsDscRunAsCredential“ wird für zusammengesetzte DSC-Ressourcen nicht unterstützt
----------------------------------------------------------------

**Lösung:** Verwenden Sie, falls verfügbar, die „Credential“-Eigenschaft. Beispiel für „ServiceSet“ und „WindowsFeatureSet“


<a id="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly" class="xliff"></a>
*Get-DscResource -Syntax* spiegelt „PsDscRunAsCredential“ nicht ordnungsgemäß wider
-------------------------------------------------------------------------
„Get-DscResource -Syntax“ spiegelt „PsDscRunAsCredential“ nicht ordnungsgemäß wider, wenn eine Ressource das Element als erforderlich kennzeichnet oder es nicht unterstützt.

**Lösung:** Keine. Die Erstellungskonfiguration in ISE spiegelt jedoch ordnungsgemäße Metadaten zur „PsDscRunAsCredential“-Eigenschaft wider, wenn IntelliSense verwendet wird.


<a id="windowsoptionalfeature-is-not-available-in-windows-7" class="xliff"></a>
„WindowsOptionalFeature“ ist unter Windows 7 nicht verfügbar
-----------------------------------------------------

Die DSC-Ressource „WindowsOptionalFeature“ ist unter Windows 7 nicht verfügbar. Diese Ressource erfordert das DISM-Modul und DISM-Cmdlets, die ab Windows 8 und in neueren Versionen des Windows-Betriebssystems verfügbar sind.

<a id="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected" class="xliff"></a>
Bei klassenbasierten DSC-Ressourcen funktioniert „Import-DscResource-ModuleVersion“ möglicherweise nicht wie erwartet   
------------------------------------------------------------------------------------------
Falls der Kompilierungsknoten mehrere Versionen eines klassenbasierten DSC-Ressourcenmoduls aufweist, wählt `Import-DscResource -ModuleVersion` nicht die angegebene Version aus und folgender Kompilierungsfehler wird zurückgegeben.

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**Lösung:** Importieren Sie die erforderliche Version, indem Sie das *ModuleSpecification*-Objekt in `-ModuleName` mit dem `RequiredVersion`-Schlüssel wie folgt definieren:
``` PowerShell  
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}  
```  

<a id="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request" class="xliff"></a>
Bei einigen DSC-Ressourcen, wie z. B. der Registrierungsressource, kann das Starten der Verarbeitung der Anforderung lange dauern.
--------------------------------------------------------------------------------------------------------------------------------

**Lösung 1:** Erstellen Sie eine Zeitplanaufgabe zum regelmäßigen Bereinigen des folgenden Ordners.
``` PowerShell 
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis 
```

**Lösung 2:** Ändern Sie die DSC-Konfiguration so, dass der Ordner *CommandAnalysis* am Ende der Konfiguration bereinigt wird.
``` PowerShell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config 
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn="[Registry]SetRegisteredOwner"
        getscript="@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```

