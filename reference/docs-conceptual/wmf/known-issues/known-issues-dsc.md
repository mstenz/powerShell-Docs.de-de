---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Bekannte Probleme und Einschränkungen bei DSC (Desired State Configuration)
ms.openlocfilehash: 6faf24795d14a93f265943029d9f6f1388f32263
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147720"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a>Bekannte Probleme und Einschränkungen bei DSC (Desired State Configuration)

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a>Breaking Change: Zertifikate zum Verschlüsseln und Entschlüsseln von Kennwörtern in DSC-Konfigurationen funktionieren nach der Installation von WMF 5.0 RTM ggf. nicht

In den Versionen WMF 4.0 und WMF 5.0 Preview lässt DSC in der Konfiguration keine Kennwörter mit mehr als 121 Zeichen zu. DSC erzwang das Verwenden kurzer Kennwörter, auch wenn längere und sichere Kennwörter gewünscht waren. Dank dieser wichtigen Änderungen können Kennwörter in der DSC-Konfiguration nun eine beliebige Länge haben.

**Lösung:** Erstellen Sie das Zertifikat mit der Schlüsselverwendung für die Daten- oder Schlüsselchiffrierung und der erweiterten Schlüsselverwendung für die Dokumentverschlüsselung (1.3.6.1.4.1.311.80.1). Weitere Informationen finden Sie unter [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a>DSC-Cmdlets funktionieren nach Installation von WMF 5.0 RTM ggf. nicht mehr

`Start-DscConfiguration` und andere DSC-Cmdlets funktionieren ggf. nach der Installation von WMF 5.0 RTM nicht mehr, und der folgende Fehler wird angezeigt:

```Output
LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
+ CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : MI RESULT 6
+ PSComputerName : localhost
```

**Lösung:** Löschen Sie „DSCEngineCache.mof“, indem Sie den folgenden Befehl mit erhöhten Rechten in einer PowerShell-Sitzung ausführen (Als Administrator ausführen):

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a>DSC-Cmdlets funktionieren ggf. nicht, wenn die WMF 5.0 RTM-Version zusätzlich zur WMF 5.0 Production Preview-Version installiert wird

**Lösung:** Führen Sie den folgenden Befehl mit erhöhten Rechten in einer PowerShell-Sitzung aus (Als Administrator ausführen):

```powershell
mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a>Der LCM kann bei Verwenden von „Get-DscConfiguration“ im Debugmodus instabil werden

Wenn der LCM im Debugmodus ist, kann das Drücken von STRG+C zum Bearbeiten von `Get-DscConfiguration` bewirken, dass der LCM so instabil wird, dass die Mehrheit der DSC-Cmdlets nicht funktioniert.

**Lösung:** Drücken Sie während des Debuggens des Cmdlets `Get-DscConfiguration` nicht STRG+C.

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a>Das Cmdlet „Stop-DscConfiguration“ reagiert im Debugmodus möglicherweise nicht.

Wenn der lokale Konfigurations-Manager im Debugmodus ist, reagiert `Stop-DscConfiguration` möglicherweise nicht beim Versuch, einen Vorgang zu beenden, der mit `Get-DscConfiguration` gestartet wurde.

**Lösung:** Beenden Sie das Debuggen des mit `Get-DscConfiguration` gestarteten Vorgangs gemäß der Anweisungen unter [Debuggen von DSC-Ressourcen](/powershell/dsc/troubleshooting/debugResource).

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a>Im Debugmodus werden keine ausführlichen Fehlermeldungen angezeigt

Wenn der LCM im **DebugMode** (Debugmodus) ist, werden von DSC-Ressourcen keine ausführlichen Fehlermeldungen angezeigt.

**Lösung:** Deaktivieren Sie den **Debugmodus**, um ausführliche Meldungen der Ressource anzuzeigen.

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a>„Invoke-DscResource“-Vorgänge können vom Cmdlet „Get-DscConfigurationStatus“ nicht abgerufen werden

Nach Verwenden des Cmdlets `Invoke-DscResource` zum direkten Aufrufen von Methoden einer Ressource können die Datensätze eines solchen Vorgangs später nicht mit `Get-DscConfigurationStatus` abgerufen werden.

**Lösung:** Keine.

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a>„Get-DscConfigurationStatus“ gibt Pullzyklusvorgänge mit dem Typ **Consistency** zurück

Wenn ein Knoten auf den PULL-Aktualisierungsmodus festgelegt ist, meldet das Cmdlet `Get-DscConfigurationStatus` den Vorgangstyp als **Consistency** anstatt als *Initial*.

**Lösung:** Keine.

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a>Das Cmdlet „Invoke-DscResource“ gibt Meldungen nicht in der Reihenfolge ihrer Erstellung zurück

Das Cmdlet `Invoke-DscResource` gibt ausführliche, Warn- und Fehlermeldungen nicht in der Reihenfolge zurück, in der sie vom LCM oder der DSC-Ressource erstellt wurden.

**Lösung:** Keine.

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a>Bei Verwendung mit „Invoke-DscResource“ ist das Debuggen von DSC-Ressourcen nicht einfach

Wenn der LCM im Debugmodus ausgeführt wird, bietet das Cmdlet `Invoke-DscResource` keine Informationen zum Runspace, mit dem zum Debuggen eine Verbindung hergestellt werden soll. Weitere Informationen finden Sie unter [Debuggen von DSC-Ressourcen](/powershell/dsc/troubleshooting/debugResource).

**Lösung:** Ermitteln und Anfügen an den Runspace mithilfe der Cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess`, `Get-Runspace` und `Debug-Runspace` zum Debuggen der DSC-Ressource.

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName    ProcessId AppDomainName
-----------    --------- -------------
powershell          3932 DefaultAppDomain
powershell_ise      2304 DefaultAppDomain
WmiPrvSE            3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name       ComputerName Type  State  Availability
-- ----       ------------ ----  -----  ------------
 2 Runspace2  localhost    Local Opened InBreakpoint
 5 RemoteHost localhost    Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a>Verschiedene Teilkonfigurationsdokumente für denselben Knoten dürfen keine identischen Ressourcennamen aufweisen

Wenn mehrere Teilkonfigurationen, die auf einem einzelnen Knoten bereitgestellt sind, identische Ressourcennamen aufweisen, kann ein Laufzeitfehler auftreten.

**Lösung:** Verwenden Sie auch für die gleichen Ressourcen in verschiedenen Teilkonfigurationen verschiedene Namen.

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a>„Start-DscConfiguration –UseExisting“ funktioniert nicht mit „-Credential“

Bei Verwendung von `Start-DscConfiguration` mit dem **UseExisting** wird der Parameter **Credential** ignoriert. DSC verwendet die Standardprozessidentität, um den Vorgang fortzusetzen. Dies bewirkt einen Fehler, wenn für das Fortsetzen auf einem Remoteknoten andere Anmeldeinformationen benötigt werden.

**Lösung:** Verwenden Sie eine CIM-Sitzung für DSC-Remotevorgänge:

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a>IPv6-Adressen als Knotennamen in DSC-Konfigurationen

IPv6-Adressen als Knotennamen in DSC-Konfigurationsskripts werden in dieser Version nicht unterstützt.

**Lösung:** Keine.

## <a name="debugging-of-class-based-dsc-resources"></a>Debuggen von `Class-Based` DSC-Ressourcen

Das Debuggen klassenbasierter DSC-Ressourcen wird in dieser Version nicht unterstützt.

**Lösung:** Keine.

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a>Variablen und Funktionen, die im Bereich „$script“ in klassenbasierten DSC-Ressourcen definiert werden, bleiben bei mehreren Aufrufen einer DSC-Ressource nicht erhalten.

Mehrere aufeinander folgende Aufrufe von `Start-DSCConfiguration` misslingen, wenn die Konfiguration klassenbasierte Ressourcen mit im Bereich `$script` definierten Variablen oder Funktionen verwendet.

**Lösung:** Definieren Sie alle Variablen und Funktionen in der DSC-Ressourcenklasse selbst. Keine Variablen/Funktionen aus dem Bereich `$script`.

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a>Debuggen von DSC-Ressourcen, wenn eine Ressource „PSDscRunAsCredential“ verwendet

Das Debuggen von DSC-Ressourcen, wenn eine Ressource **PSDscRunAsCredential** in der Konfiguration verwendet, wird in dieser Version nicht unterstützt.

**Lösung:** Keine.

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a>„PsDscRunAsCredential“ wird für zusammengesetzte DSC-Ressourcen nicht unterstützt

**Lösung:** Verwenden Sie, falls verfügbar, die Eigenschaft „Credential“. Beispiel für „ServiceSet“ und „WindowsFeatureSet“

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a>„-Syntax“ von „Get-DscResource“ spiegelt „PsDscRunAsCredential“ nicht ordnungsgemäß wider

Der Parameter **Syntax** spiegelt **PsDscRunAsCredential** nicht ordnungsgemäß wider, wenn ihn eine Ressource als erforderlich kennzeichnet oder nicht unterstützt.

**Lösung:** Keine. Die Erstellungskonfiguration in ISE spiegelt jedoch ordnungsgemäße Metadaten zur **PsDscRunAsCredential**-Eigenschaft wider, wenn IntelliSense verwendet wird.

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a>„WindowsOptionalFeature“ ist unter Windows 7 nicht verfügbar

Die DSC-Ressource **WindowsOptionalFeature** ist unter Windows 7 nicht verfügbar. Diese Ressource erfordert das DISM-Modul und DISM-Cmdlets, die ab Windows 8 und in neueren Versionen des Windows-Betriebssystems verfügbar sind.

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a>Bei klassenbasierten DSC-Ressourcen funktioniert „Import-DscResource-ModuleVersion“ möglicherweise nicht wie erwartet

Falls der Kompilierungsknoten mehrere Versionen eines klassenbasierten DSC-Ressourcenmoduls aufweist, wählt `Import-DscResource -ModuleVersion` nicht die angegebene Version aus und folgender Kompilierungsfehler wird zurückgegeben.

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**Lösung:** Importieren Sie die erforderliche Version, indem Sie das **ModuleSpecification**-Objekt auf den **ModuleName**-Parameter definieren, mit dem Schlüssel **RequiredVersion** festgelegt wie folgt :

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a>Bei einigen DSC-Ressourcen, wie z. B. der Registrierungsressource, kann das Starten der Verarbeitung der Anforderung lange dauern.

**Lösung 1:** Erstellen Sie eine geplante Aufgabe zum regelmäßigen Bereinigen des folgenden Ordners.

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

**Lösung 2:** Ändern Sie die DSC-Konfiguration so, dass der Ordner *CommandAnalysis* am Ende der Konfiguration bereinigt wird.

```powershell
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
        DependsOn = "[Registry]SetRegisteredOwner"
        getscript = "@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
