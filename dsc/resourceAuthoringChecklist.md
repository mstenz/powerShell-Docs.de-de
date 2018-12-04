---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Prüfliste für die Ressourcenerstellung
ms.openlocfilehash: 2b6e972776dba4ecc6fd1ab5c21361d653e1a469
ms.sourcegitcommit: e24525046dd37166b9d83eeecdc534726316f429
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2018
ms.locfileid: "52742838"
---
# <a name="resource-authoring-checklist"></a>Prüfliste für die Ressourcenerstellung

Diese Prüfliste ist eine Liste der bewährten Methoden beim Erstellen einer neuen DSC-Ressource.

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a>Das Ressourcenmodul enthält für jede Ressource Dateien des Typs „.psd1“ und „schema.mof“.

Stellen Sie sicher, dass Ihre Ressource eine ordnungsgemäße Struktur hat und alle erforderlichen Dateien enthält. Ein Ressourcenmodul muss eine PSD1-Datei enthalten, und für jede nicht zusammengesetzte Ressource muss die Datei „schema.mof“ vorhanden sein. Ressourcen ohne Schema werden nach Ausführen von `Get-DscResource` nicht aufgeführt. Zudem können Benutzer nicht mit IntelliSense arbeiten, wenn Code für diese Module in der ISE geschrieben wird.
Die Verzeichnisstruktur für die Ressource „xRemoteFile“, die Teil des [Ressourcenmoduls „xPSDesiredStateConfiguration“](https://github.com/PowerShell/xPSDesiredStateConfiguration) ist, sieht folgendermaßen aus:

```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a>Die Ressource und das Schema sind richtig

Überprüfen Sie die Ressourcenschemadatei („*.schema.mof“). Sie können den [DSC-Ressourcen-Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner) verwenden, um Ihr Schema zu entwickeln und zu testen.
Stellen Sie Folgendes sicher:

- Eigenschaftentypen sind ordnungsgemäß (z. B. STRING wird nicht für Eigenschaften für numerische Werte verwendet, wofür UInt32 oder andere numerische Typen gewählt werden müssen).
- Eigenschaftsattribute sind ordnungsgemäß angegeben als: ([key], [required], [write], [read]).
- Mindestens ein Parameter im Schema muss als [key] markiert sein.
- Die [read]-Eigenschaft darf nicht zusammen mit den folgenden Eigenschaften angegeben werden: [required], [key], [write]
- Wenn mehrere Qualifizierer außer [read] angegeben sind, hat [key] Vorrang.
- Wenn [write] und [required] angegeben sind, hat [required] Vorrang.
- ValueMap wird gegebenenfalls angegeben. Beispiel:

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- Der Anzeigename ist angegeben und entspricht den DSC-Benennungskonventionen.

  Beispiel: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`

- Jedes Feld hat eine aussagekräftige Beschreibung. Das PowerShell-GitHub-Repository enthält gute Beispiele, z.B. [die Datei „.schema.mof“ für „xRemoteFile“](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)

Sie sollten darüber hinaus die Cmdlets **Test-xDscResource** und **Test-xDscSchema** im [DSC-Ressourcen-Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner) verwenden, um die Ressource und das Schema automatisch zu überprüfen:

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

Beispiel:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a>Ressource wird ohne Fehler geladen.

Überprüfen Sie, ob das Ressourcenmodul erfolgreich geladen werden kann.
Dies kann manuell erfolgen, indem `Import-Module <resource_module> -force` ausgeführt und bestätigt wird, dass keine Fehler aufgetreten sind. Sie können auch einen automatisierten Test schreiben. Im letzteren Fall können Sie diese Struktur bei Ihrem Testfall befolgen:

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a>Die Ressource ist im positiven Sinn idempotent

Eine der grundlegenden Merkmale von DSC-Ressourcen ist die Idempotenz. Dies bedeutet, dass beim Anwenden einer DSC-Konfiguration, die diese Ressource mehrmals enthält, immer das gleiche Ergebnis erreicht wird. Angenommen, wir erstellen eine Konfiguration mit der folgenden „File“-Ressource:

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

Nach dem ersten Anwenden sollte die Datei „test.txt“ im Ordner `C:\test` enthalten sein. Bei nachfolgenden Ausführungen derselben Konfiguration sollte sich der Zustand des Computers nicht ändern (z.B. sollten keine Kopien der Datei `test.txt` erstellt werden).
Um sicherzustellen, dass eine Ressource idempotent ist, können Sie beim direkten Testen der Ressource `Set-TargetResource` wiederholt aufrufen. Bei End-to-End-Tests können Sie `Start-DscConfiguration` mehrmals aufrufen. Das Ergebnis sollte nach jeder Ausführung identisch sein.

## <a name="test-user-modification-scenario"></a>Testen des Benutzeränderungsszenarios

Sie können sicherstellen, dass `Set-TargetResource` und `Test-TargetResource` ordnungsgemäß funktionieren, indem Sie den Zustand des Computers ändern und DSC anschließend erneut ausführen. Führen Sie dazu die folgenden Schritte aus:

1. Beginnen Sie mit einer Ressource, die nicht im gewünschten Zustand ist.
2. Wenden Sie eine Konfiguration auf die Ressource an.
3. Stellen Sie sicher, dass `Test-DscConfiguration` „true“ zurückgibt.
4. Ändern Sie das konfigurierte Element dahingehend, dass es dem gewünschten Zustand nicht mehr entspricht.
5. Stellen Sie sicher, dass `Test-DscConfiguration` „false“ zurückgibt.

Hier ein konkreteres Beispiel der Ressource „Registry“:

1. Beginnen Sie mit einem Registrierungsschlüssel, der nicht im gewünschten Zustand ist.
2. Führen Sie `Start-DscConfiguration` mit einer Konfiguration aus, um sie in den gewünschten Zustand zu versetzen, in dem sie eine Überprüfung besteht.
3. Führen Sie `Test-DscConfiguration` aus, und stellen Sie sicher, dass sie „true“ zurückgibt.
4. Ändern Sie den Wert des Schlüssels so, dass er sich nicht im gewünschten Zustand befindet.
5. Führen Sie `Test-DscConfiguration` aus, und stellen Sie sicher, dass sie „false“ zurückgibt.
6. Die `Get-TargetResource`-Funktionalität wurde mit `Get-DscConfiguration` überprüft.

`Get-TargetResource` sollte Details zum aktuellen Zustand der Ressource zurückgeben. Testen Sie die Konfiguration durch Aufrufen von `Get-DscConfiguration`, nachdem Sie sie angewendet haben, und stellen Sie sicher, dass die Ausgabe den aktuellen Zustand des Computers ordnungsgemäß widerspiegelt. Es müssen unbedingt getrennte Tests erfolgen, da Probleme in diesem Bereich nicht auftauchen, wenn `Start-DscConfiguration` aufgerufen wird.

## <a name="call-getsettest-targetresource-functions-directly"></a>Direktes Aufrufen der **Get/Set/Test-TargetResource**-Funktionen

Stellen Sie sicher, dass Sie die **Get/Set/Test-TargetResource**-Funktionen testen, die in Ihrer Ressource implementiert sind, indem Sie sie direkt aufrufen und sicherstellen, dass sie erwartungsgemäß funktionieren.

## <a name="verify-end-to-end-using-start-dscconfiguration"></a>End-to-End-Überprüfen der Ressource mithilfe von **Start-DscConfiguration**

Das Testen von **Get/Set/Test-TargetResource**-Funktionen, indem sie direkt aufgerufen werden, ist wichtig, doch auf diese Weise werden nicht alle Probleme ermittelt. Konzentrieren Sie einen wesentlichen Teil Ihrer Tests auf die Verwendung von `Start-DscConfiguration` oder des Pullservers. Benutzer verwenden die Ressource genau so, weshalb Sie die Bedeutung dieser Art von Tests nicht unterschätzen sollten.
Mögliche Problemtypen:

- Das Verhalten von Anmeldeinformationen oder der Sitzung ist möglicherweise anders, da der DSC-Agent als Dienst ausgeführt wird.  Führen Sie in diesem Bereich auf jeden Fall End-to-End-Tests von Features durch.
- Von `Start-DscConfiguration` ausgegebene Fehler sind ggf. anders als die, die angezeigt werden, wenn die Funktion `Set-TargetResource` direkt aufgerufen wird.

## <a name="test-compatability-on-all-dsc-supported-platforms"></a>Testen der Kompatibilität auf allen DSC-unterstützten Plattformen

Die Ressource sollte auf allen von DSC unterstützten Plattformen funktionieren (Windows Server 2008 R2 und höher). Installieren Sie für Ihr Betriebssystem das neueste WMF (Windows Management Framework), um die neueste DSC-Version zu erhalten. Wenn Ihre Ressource einige dieser Plattformen entwurfsbedingt nicht unterstützt, sollte eine bestimmte Fehlermeldung zurückgegeben werden. Stellen Sie außerdem sicher, dass die Ressource überprüft, ob die Cmdlets, die Sie aufrufen, auf einem bestimmten Computer vorhanden sind. Windows Server 2012 wurde eine große Anzahl neuer Cmdlets hinzugefügt, die unter Windows Server 2008 R2, sogar mit installiertem WMF, nicht verfügbar sind.

## <a name="verify-on-windows-client-if-applicable"></a>Überprüfen auf Windows-Client (falls zutreffend)

Sehr häufig wird bei Tests die Ressource nur auf den Serverversionen von Windows zu überprüft. Viele Ressourcen sind aber auch für Client-SKUs konzipiert. Vergessen Sie daher nicht, wenn dies für Sie gilt, sie auf diesen Plattformen ebenfalls zu testen.

## <a name="get-dscresource-lists-the-resource"></a>Auflisten der Ressourcen mit „Get-DSCResource“

Nach der Bereitstellung des Moduls sollte ein Aufruf von `Get-DscResource` u.a. Ihre Ressource im Ergebnis auflisten. Wenn Sie die Ressource nicht finden können, stellen Sie sicher, dass die Datei „schema.mof“ für die Ressource vorhanden ist.

## <a name="resource-module-contains-examples"></a>Ressourcenmodul enthält Beispiele

Erstellen Sie anschauliche Beispiele, die anderen helfen, die Verwendung zu verstehen. Dies ist entscheidend, insbesondere seitdem viele Benutzer Beispielcode als Dokumentation behandeln.

- Zunächst sollten Sie die Beispiele bestimmen, die Sie dem Modul hinzufügen möchten. Zumindest sollten die wichtigsten Anwendungsfälle für Ihre Ressource abgedeckt werden:
- Wenn Ihr Modul mehrere Ressourcen enthält, die für ein End-to-End-Szenario zusammenarbeiten müssen, bietet sich idealerweise das grundlegende End-to-End-Beispiel als Erstes an.
- Die anfänglichen Beispiele sollten sehr einfach sein und die ersten Schritte mit Ihren Ressourcen in kurzen, übersichtlichen Abschnitten erläutern (z. B. das Erstellen einer neuen virtuellen Festplatte [VHD]).
- Nachfolgende Beispiele sollten auf diesen Beispielen aufbauen (z. b. Erstellen einer VM anhand einer VHD, Entfernen einer VM, Ändern einer VM) und erweiterte Funktionen veranschaulichen (z. B. das Erstellen einer VM mit dynamischem Arbeitsspeicher).
- Beispielkonfigurationen sollten parametrisiert sein (alle Werte sollten als Parameter an die Konfiguration übergeben werden, und es darf keine hartcodierten Werte geben):

  ```powershell
  configuration Sample_xRemoteFile_DownloadFile
  {
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
  }
  ```

- Es empfiehlt sich, am Ende des Beispielskripts ein (auskommentiertes) Beispiel hinzuzufügen, wie die Konfiguration mit den tatsächlichen Werte aufgerufen wird.
  Aus der obigen Konfiguration geht beispielsweise nicht unbedingt hervor, dass die beste Möglichkeit zum Angeben von „UserAgent“ wie folgt aussieht:

  `UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In diesem Fall kann ein Kommentar die beabsichtigte Ausführung der Konfiguration verdeutlichen:

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- Schreiben Sie für jedes Beispiel eine kurze Beschreibung mit einer Erläuterung der Funktionsweise und Bedeutung der Parameter.
- Vergewissern Sie sich, dass die Beispiele die meisten wichtigen Szenarien für Ihre Ressource abdecken. Wenn nichts fehlt, überprüfen Sie, dass sie alle ausgeführt werden und den Computer in den gewünschten Zustand versetzen.

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a>Leicht verständliche Fehlermeldungen helfen Benutzern bei der Problembehebung

Gute Fehlermeldungen zeichnen sich wie folgt aus:

- Ihr Vorhandensein: Das größte Problem bei Fehlermeldungen besteht darin, dass sie häufig nicht vorhanden sind. Achten Sie deshalb darauf, dass sie vorhanden sind.
- Einfach zu verstehende, von Menschen lesbare, nicht kryptische Fehlercodes.
- Genaue Beschreibung, was das Problem ist.
- Konstruktive Ratschläge zum Beheben des Problems.
- Höflicher Ton, in dem Benutzer nicht die Schuld gegeben wird oder ihm Vorwürfe gemacht werden.

Stellen Sie sicher, dass Sie Fehler in End-to-End-Szenarien (mit `Start-DscConfiguration`) überprüfen, da sie sich von denjenigen unterscheiden können, die zurückgegeben werden, wenn die Ressourcenfunktionen direkt ausgeführt werden.

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a>Protokollmeldungen sind leicht verständlich und informativ (z. B. „–verbose“, „–debug“ und ETW-Protokolle)

Stellen Sie sicher, dass Protokolle, die von der Ressource ausgegeben werden, leicht verständlich und für den Benutzer von Nutzen sind. Ressourcen sollten alle Informationen ausgeben, die für den Benutzer hilfreich sind, doch mehr Protokolle sind nicht unbedingt besser. Sie sollten das Ausgeben redundanter Daten ohne Mehrwert unbedingt vermeiden. Lassen Sie Benutzer nicht Hunderte von Protokolleinträgen durchlaufen, damit sie finden, was sie suchen. Keine Protokolle sind freilich keine akzeptable Lösung dieses Problems.

Beim Testen sollten Sie auch ausführliche und Debugprotokolle (durch Ausführen von `Start-DscConfiguration` mit den Switches `–Verbose` bzw. `–Debug`) sowie ETW-Protokolle analysieren. Um ETW-Protokolle für DSC anzuzeigen, wechseln Sie zur Ereignisanzeige, und öffnen Sie den folgenden Ordner: Anwendungen und Dienste -> Microsoft -> Windows -> Konfiguration für den gewünschten Zustand.  In der Standardeinstellung gibt es den Kanal „Betriebsbereit“. Aktivieren Sie vor dem Ausführen der Konfiguration jedoch auch die Kanäle „Analyse“ und „Debuggen“.
Zum Aktivieren der Kanäle „Analyse/Debuggen“ können Sie das folgende Skript ausführen:

```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a>Ressourcenimplementierung ohne hartcodierte Pfade

Vergewissern Sie sich, dass es in der Ressourcenimplementierung keine hartcodierten Pfade gibt, insbesondere wenn diese eine Sprache voraussetzen (z. B. en-us), oder wenn es Systemvariablen gibt, die verwendet werden können.
Wenn Ihre Ressource auf bestimmte Pfade zugreifen muss, verwenden Sie Umgebungsvariablen anstelle eines hartcodierten Pfads, da sich dieser je nach Computer unterscheiden kann.

Beispiel:

Anstelle von:

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

Können Sie Folgendes schreiben:

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a>Ressourcenimplementierung ohne Benutzerinformationen

Stellen Sie sicher, dass im Code keine E-Mail-Adressen, Kontoinformationen oder Namen von Personen vorhanden sind.

## <a name="resource-was-tested-with-validinvalid-credentials"></a>Ressourcentests mit gültigen/ungültigen Anmeldeinformationen

Wenn Ihre Ressource Anmeldeinformationen als Parameter verwendet:

- Überprüfen Sie, ob die Ressource funktioniert, wenn das lokale System (oder das Computerkonto für Remoteressourcen) keinen Zugriff hat.
- Überprüfen Sie, ob die Ressource mit für „Get“, „Set“ und „Test“ angegebenen Anmeldeinformationen funktioniert.
- Wenn die Ressource auf Freigaben zugreift, testen Sie alle Varianten, die Sie unterstützen müssen, wie z.B.:
  - Windows-Standardfreigaben.
  - DFS-Freigaben
  - SAMBA-Freigaben (wenn Sie Linux unterstützen möchten)

## <a name="resource-does-not-require-interactive-input"></a>Die Ressource benötigt keine interaktive Eingabe

**Get/Set/Test-TargetResource**-Funktionen sollen automatisch ausgeführt werden und in keiner Phase der Ausführung auf Benutzereingaben warten (platzieren Sie deshalb `Get-Credential` nicht innerhalb dieser Funktionen). Wenn Sie Benutzereingaben bereitstellen müssen, sollten Sie sie in der Kompilierungsphase als Parameter an die Konfiguration übergeben.

## <a name="resource-functionality-was-thoroughly-tested"></a>Gründliches Testen der Ressourcenfunktionalität

Diese Prüfliste enthält Elemente, die unbedingt getestet werden sollten und/oder oft übersehen werden. Es gibt eine Vielzahl von Tests, hauptsächlich Funktionstests, die spezifisch für die Ressource sind, die Sie testen, und hier nicht erwähnt werden. Vergessen Sie nicht die negativen Testfälle.

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a>Bewährte Methode: Ressourcenmodul enthält den Ordner „Tests“ mit dem Skript „ResourceDesignerTests.ps1“

Es empfiehlt sich, im Ressourcenmodul den Ordner „Tests“ anzulegen, die Datei `ResourceDesignerTests.ps1` zu erstellen und über **Test-xDscResource** und **Test-xDscSchema** Tests für alle Ressourcen in einem bestimmten Modul hinzuzufügen.
Auf diese Weise können Sie schnell die Schemas aller Ressourcen aus den angegebenen Modulen überprüfen und vor der Veröffentlichung eine Integritätsprüfung vornehmen.
Für „xRemoteFile“ kann `ResourceTests.ps1` einfach so aussehen:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a>Bewährte Methode: Ressourcenordner enthält Ressourcen-Designer-Skript zur Generierung des Schemas

Jede Ressource sollte ein Ressourcen-Designer-Skript enthalten, mit dem ein MOF-Schema der Ressource generiert wird. Diese Datei sollte unter `<ResourceName>\ResourceDesignerScripts` platziert und mit dem Namen `<ResourceName>Schema.ps1` versehen werden. Bei der Ressource „xRemoteFile“ würde diese Datei `GenerateXRemoteFileSchema.ps1` lauten und Folgendes enthalten:

```powershell
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.'
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile
```

## <a name="best-practice-resource-supports--whatif"></a>Bewährte Methode: Die Ressource unterstützt „-WhatIf“

Wenn mit der Ressource „gefährliche“ Vorgänge ausgeführt werden, empfiehlt es sich, `-WhatIf`-Funktionalität zu implementieren. Nachdem dies erfolgt ist, stellen Sie sicher, dass die `-WhatIf`-Ausgabe Vorgänge ordnungsgemäß beschreibt, die eintreten würden, wenn der Befehl ohne den Switch `-WhatIf` ausgeführt würde.
Vergewissern Sie sich auch, dass bei Vorhandensein des Switches `–WhatIf` keine Vorgänge ausgeführt werden (d.h. keine Änderungen am Zustand des Knotens erfolgen).
Angenommen, wir testen die Ressource „File“. Nachstehend finden Sie eine einfache Konfiguration, die die Datei `test.txt` mit dem Inhalt „test“ erstellt:

```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```

Wenn wir die Konfiguration kompilieren und dann mit dem Switch `-WhatIf` ausführen, gibt die Ausgabe genau an, was bei Ausführung der Konfiguration passieren würde. Die Konfiguration selbst wurde jedoch nicht ausgeführt (die Datei `test.txt` wurde nicht erstellt).

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```output
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

Diese Liste ist nicht vollständig. Sie deckt jedoch viele wichtige Aspekte ab, die beim Entwerfen, Entwickeln und Testen von DSC-Ressourcen auftreten können.
