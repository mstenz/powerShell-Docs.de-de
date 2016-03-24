# Prüfliste für die Ressourcenerstellung

## Das Ressourcenmodul enthält für jede Ressource Dateien des Typs „.psd1“ und „schema.mof“. 
Als Erstes müssen Sie prüfen, ob Ihre Ressource eine ordnungsgemäße Struktur hat und alle erforderlichen Dateien enthält. Ein Ressourcenmodul muss eine PSD1-Datei enthalten, und für jede nicht zusammengesetzte Ressource muss die Datei „schema.mof“ vorhanden sein. Ressourcen ohne Schema werden nach Ausführen von **Get-DscResource** nicht aufgeführt. Zudem können Benutzer nicht mit IntelliSense arbeiten, wenn Code für diese Module in der ISE geschrieben wird. 
Die Beispielverzeichnisstruktur für die Ressource „xRemoteFile“, die Teil des Ressourcenmoduls „xPSDesiredStateConfiguration“ ist, kann so aussehen:


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

## Ressourcen und das Schema sind korrekt und wurden mit Cmdlets des Typs „DscResourceDesigner“ überprüft. ##
Ein weiterer wichtiger Aspekt ist das Überprüfen der Ressourcenschemadatei (*.schema.mof). 
Stellen Sie Folgendes sicher:
-   Eigenschaftentypen sind ordnungsgemäß (z. B. STRING wird nicht für Eigenschaften für numerische Werte verwendet, wofür UInt32 oder andere numerische Typen gewählt werden müssen).
-   Eigenschaftenattribute sind ordnungsgemäß angegeben ([key], [required], [write], [read]).


- Mindestens ein Parameter im Schema muss als [key] markiert sein.


- Die [read]-Eigenschaft darf nicht zusammen mit den folgenden Eigenschaften angegeben werden: [required], [key], [write]


- Wenn mehrere Qualifizierer außer [read] angegeben sind, hat [key] Vorrang.
Wenn [write] und [required] angegeben sind, hat [required] Vorrang.
-   „ValueMap“ wird gegebenenfalls angegeben.

Beispiel:
```
[Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
```

-   Der Anzeigename ist angegeben und entspricht den DSC-Benennungskonventionen.

Beispiel: 
```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```

-   Jedes Feld hat eine aussagekräftige Beschreibung.

Es folgt ein anschauliches Beispiel der Ressourcenschemadatei (dies ist das tatsächliche Schema der Ressource „xRemoteFile“ im DSC Resource Kit).
```
[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]
class MSFT_xRemoteFile : OMI_BaseResource
{
    [Key, Description("Path under which downloaded or copied file should be accessible after operation.")] String DestinationPath;
    [Required, Description("Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.")] String Uri;
    [Write, Description("User agent for the web request.")] String UserAgent;
    [Write, EmbeddedInstance("MSFT_KeyValuePair"), Description("Headers of the web request.")] String Headers[];
    [Write, EmbeddedInstance("MSFT_Credential"), Description("Specifies a user account that has permission to send the request.")] String Credential;
    [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
}; 
```
Sie sollten darüber hinaus die Cmdlets **Test-xDscResource** und **Test-xDscSchema** im DSC-Ressourcen-Designer verwenden, um die Ressource und das Schema automatisch zu überprüfen:
```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```
Beispiel:
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## Ressource wird ohne Fehler geladen. ##
Nachdem Sie bestätigt haben, dass die Ressource alle erforderlichen Dateien enthält und der DSC-Ressourcen-Designer sie überprüft hat, muss geprüft werden, ob das Ressourcenmodul geladen werden kann.
Dies kann manuell erfolgen, indem `Import-Module <resource_module> -force ` ausgeführt und bestätigt wird, dass keine Fehler aufgetreten sind. Sie können auch einen automatisierten Test schreiben. Im letzteren Fall können Sie diese Struktur bei Ihrem Testfall befolgen:
```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```
4   Ressource ist in positivem Sinn idempotent. 
Eines der grundlegenden Merkmale aller DSC-Ressourcen muss Idempotenz sein. Dies bedeutet, dass wir eine DSC-Konfiguration mit dieser Ressource mehrmals anwenden können, ohne das Ergebnis nach der erstmaligen Anwendung zu ändern. Angenommen, wir erstellen eine Konfiguration mit der folgenden „File“-Ressource:
```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
} 
```
Nach dem ersten Anwenden sollte die Datei „Test.txt“ im Ordner „C:\test“ enthalten sein. Bei nachfolgenden Ausführungen derselben Konfiguration sollte sich der Zustand des Computers nicht ändern (d. h. keine Kopien der Datei „Test.txt“ sollten erstellt werden).
Um sicherzustellen, dass unsere Ressource idempotent ist, können wir beim direkten Testen der Ressource **Set-TargetResource** wiederholt aufrufen. Bei End-to-End-Tests können wir **Start-DscConfiguration** mehrmals aufrufen. Das Ergebnis sollte nach jeder Ausführung identisch sein. 


## Benutzeränderungsszenario getestet ##
Das Ändern des Benutzers ist ein weiteres gängiges Szenario, das zu testen lohnt. Es dient zum Überprüfen, ob **Set-TargetResource** und **Test-TargetResource** richtig funktionieren. Es folgen die für einen Test auszuführenden Schritte:
1.  Beginnen Sie mit einer Ressource, die nicht im gewünschten Zustand ist.
2.  Wenden Sie eine Konfiguration auf die Ressource an.
3.  Überprüfen Sie, ob **Test-DscConfiguration** „True“ zurückgibt.
4.  Ändern Sie den gewünschten Zustand der Ressource.
5.  Überprüfen Sie, ob **Test-DscConfiguration** „False“ zurückgibt.
Hier ein konkreteres Beispiel der Ressource „Registry“:
1.  Beginnen Sie mit einem Registrierungsschlüssel, der nicht im gewünschten Zustand ist.
2.  Führen Sie **Start-DscConfiguration** mit einer Konfiguration aus, um sie in den gewünschten Zustand zu versetzen, der eine Überprüfung besteht.
3.  Führen Sie **Test-DscConfiguration** aus, und prüfen Sie, ob „True“ zurückgegeben wird.
4.  Ändern Sie den Wert des Schlüssels so, dass er sich nicht im gewünschten Zustand befindet.
5.  Führen Sie **Test-DscConfiguration** aus, und prüfen Sie, ob „False“ zurückgegeben wird.
6.  Überprüfen von „Get-TargetResource“-Funktionalität mit „Get-DscConfiguration“

„Get-TargetResource“ sollte Details zum aktuellen Zustand der Ressource zurückgeben. Testen Sie sie durch Aufrufen von „Get-DscConfiguration“ nach Anwenden der Konfiguration, und überprüfen Sie, ob die Ausgabe den aktuellen Zustand des Computers ordnungsgemäß widerspiegelt. Es müssen unbedingt getrennte Tests erfolgen, da Probleme in diesem Bereich nicht auftauchen, wenn „Start-DscConfiguration“ aufgerufen wird.

## Überprüfen der Ressource durch direktes Aufrufen von **Get/Set/Test-TargetResource**-Funktionen ##

Stellen Sie sicher, dass Sie die **Get/Set/Test-TargetResource**-Funktionen testen, die in Ihrer Ressource implementiert sind, indem Sie sie direkt aufrufen und sicherstellen, dass sie erwartungsgemäß funktionieren.

## End-to-End-Überprüfung der Ressource mit **Start-DscConfiguration** ##

Das Testen von **Get/Set/Test-TargetResource**-Funktionen, indem sie direkt aufgerufen werden, ist wichtig, doch auf diese Weise werden nicht alle Probleme ermittelt. Konzentrieren Sie einen wesentlichen Teil Ihrer Tests auf das Verwenden von **Start-DscConfiguration** oder des Pullservers. Benutzer verwenden die Ressource genau so, weshalb Sie die Bedeutung dieser Art von Tests nicht unterschätzen sollten. 
Mögliche Problemtypen:
-   Das Verhalten von Anmeldeinformationen oder der Sitzung ist möglicherweise anders, da der DSC-Agent als Dienst ausgeführt wird.  Führen Sie in diesem Bereich auf jeden Fall End-to-End-Tests von Features durch.
-   Überprüfen Sie, ob von der Ressource angezeigte Fehlermeldungen sinnvoll sind. Von **Start-DscConfiguration** ausgegebene Fehler sind ggf. anders als die, die angezeigt werden, wenn die **Set-TargetResource**-Funktion direkt aufgerufen wird.

## Die Ressource verhält sich auf allen von DSC unterstützten Plattformen ordnungsgemäß (oder gibt andernfalls einen Fehler zurück) ##
Die Ressource sollte auf allen von DSC unterstützten Plattformen funktionieren (Windows Server 2008 R2 und höher). Stellen Sie sicher, dass Sie für Ihr Betriebssystem das neueste WMF (Windows Management Framework) installieren, um mit der neuesten DSC-Version zu arbeiten. Wenn eine Ressource auf einigen dieser Plattformen standardmäßig nicht funktioniert, sollte eine entsprechende Fehlermeldung zurückgegeben werden. Stellen Sie außerdem sicher, dass die Ressource überprüft, ob die Cmdlets, die Sie aufrufen, auf einem bestimmten Computer vorhanden sind. Windows Server 2012 wurde eine große Anzahl neuer Cmdlets hinzugefügt, die unter Windows Server 2008 R2, sogar mit installiertem WMF, nicht verfügbar sind. 

## Überprüfen der Ressourcenfunktionalität auf Windows-Client (falls zutreffend) ##
Sehr häufig wird bei Tests die Ressource nur auf den Serverversionen von Windows zu überprüft. Viele Ressourcen sind aber auch für Client-SKUs konzipiert. Vergessen Sie daher nicht, wenn dies für Sie gilt, sie auf diesen Plattformen ebenfalls zu testen. 
## Auflisten der Ressourcen mit „Get-DSCResource“ ##
Nach der Bereitstellung des Moduls auf dem Computer sollte nach Aufrufen von „Get-DscResource“ Ihre Ressource im Ergebnis enthalten sein. Wenn Sie die Ressource nicht finden können, stellen Sie sicher, dass die Datei „schema.mof“ für die Ressource vorhanden ist. 
## Ressourcenmodul enthält Beispiele ##
Wenn Sie beabsichtigen, die Ressource freizugeben (was Sie hoffentlich tun), erstellen Sie anschauliche Beispiele, die anderen ihre Nutzung erleichtern. Dies ist entscheidend, insbesondere seitdem viele Benutzer Beispielcode als Dokumentation behandeln. 
-   Zunächst sollten Sie die Beispiele bestimmen, die Sie dem Modul hinzufügen möchten. Zumindest sollten die wichtigsten Anwendungsfälle für Ihre Ressource abgedeckt werden:
-   Wenn Ihr Modul mehrere Ressourcen enthält, die für ein End-to-End-Szenario zusammenarbeiten müssen, bietet sich idealerweise das grundlegende End-to-End-Beispiel als Erstes an.
-   Die anfänglichen Beispiele sollten sehr einfach sein und die ersten Schritte mit Ihren Ressourcen in kurzen, übersichtlichen Abschnitten erläutern (z. B. das Erstellen einer neuen virtuellen Festplatte [VHD]).
-   Nachfolgende Beispiele sollten auf diesen Beispielen aufbauen (z. b. Erstellen einer VM anhand einer VHD, Entfernen einer VM, Ändern einer VM) und erweiterte Funktionen veranschaulichen (z. B. das Erstellen einer VM mit dynamischem Arbeitsspeicher).
-   Beispielkonfigurationen sollten parametrisiert sein (alle Werte sollten als Parameter an die Konfiguration übergeben werden, und es darf keine hartcodierten Werte geben):
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
-   Es empfiehlt sich, am Ende des Beispielskripts ein (auskommentiertes) Beispiel hinzuzufügen, wie die Konfiguration mit den tatsächlichen Werte aufgerufen wird. 
Aus der obigen Konfiguration geht beispielsweise nicht unbedingt hervor, dass die beste Möglichkeit zum Angeben von „UserAgent“ so aussieht:

`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer`  
Daher sollten wir die Beispielausführung der Konfiguration mit Kommentaren versehen:
```
<# 
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>  
```
-   Schreiben Sie für jedes Beispiel eine kurze Beschreibung mit einer Erläuterung der Funktionsweise und Bedeutung der Parameter. 
-   Vergewissern Sie sich, dass die Beispiele die meisten wichtigen Szenarien für Ihre Ressource abdecken. Wenn nichts fehlt, überprüfen Sie, dass sie alle ausgeführt werden und den Computer in den gewünschten Zustand versetzen.  

## Leicht verständliche Fehlermeldungen helfen Benutzern bei der Problembehebung ##
Gute Fehlermeldungen zeichnen sich wie folgt aus:
-   Ihr Vorhandensein: Das größte Problem bei Fehlermeldungen besteht darin, dass sie häufig nicht vorhanden sind. Achten Sie deshalb darauf, dass sie vorhanden sind. 
-   Einfach zu verstehende, von Menschen lesbare, nicht kryptische Fehlercodes.
-   Genaue Beschreibung, was das Problem ist.
-   Konstruktive Ratschläge zum Beheben des Problems.
-   Höfliche Informationen, die dem Benutzer nicht die Schuld geben oder ihn dumm aussehen lassen.
Stellen Sie sicher, dass Sie Fehler in End-to-End-Szenarien (mit **Start-DscConfiguration**) überprüfen, da sie sich von denjenigen unterscheiden können, die zurückgegeben werden, wenn die Ressourcenfunktionen direkt ausgeführt werden. 

## Protokollmeldungen sind leicht verständlich und informativ (z. B. „–verbose“, „–debug“ und ETW-Protokolle) ##
Stellen Sie sicher, dass Protokolle, die von der Ressource ausgegeben werden, leicht verständlich und für den Benutzer von Nutzen sind. Ressourcen sollten alle Informationen ausgeben, die für den Benutzer hilfreich sind, doch mehr Protokolle sind nicht unbedingt besser. Sie sollten das Ausgeben redundanter Daten ohne Mehrwert unbedingt vermeiden. Lassen Sie Benutzer nicht Hunderte von Protokolleinträgen durchlaufen, damit sie finden, was sie suchen. Keine Protokolle sind freilich keine akzeptable Lösung dieses Problems. 

Beim Testen sollten Sie auch ausführliche und Debugprotokolle (durch Ausführen von **Start-DscConfiguration** mit den Schaltern „–verbose“ und „–debug“) sowie ETW-Protokolle analysieren. Um ETW-Protokolle für DSC anzuzeigen, wechseln Sie zur Ereignisanzeige, und öffnen Sie den folgenden Ordner: Anwendungen und Dienste -> Microsoft -> Windows -> Konfiguration für den gewünschten Zustand.  In der Standardeinstellung gibt es den Kanal „Betriebsbereit“, doch aktivieren Sie auch die Kanäle „Analyse“ und „Debuggen“ (was vor dem Ausführen der Konfiguration erfolgen muss). 
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
## Ressourcenimplementierung ohne hartcodierte Pfade ##
Vergewissern Sie sich, dass es in der Ressourcenimplementierung keine hartcodierten Pfade gibt, insbesondere wenn diese eine Sprache voraussetzen (z. B. en-us), oder wenn es Systemvariablen gibt, die verwendet werden können.
Wenn Ihre Ressource auf bestimmte Pfade zugreifen muss, verwenden Sie Umgebungsvariablen anstelle eines hartcodierten Pfads, da sich dieser je nach Computer unterscheiden kann.

Beispiel:

Anstelle von:
```
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
 ```
Können Sie Folgendes schreiben:
```
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)} 
```
## Ressourcenimplementierung ohne Benutzerinformationen ##
Stellen Sie sicher, dass im Code keine E-Mail-Adressen, Kontoinformationen oder Namen von Personen vorhanden sind.
## Ressourcentests mit gültigen/ungültigen Anmeldeinformationen ##
Wenn Ihre Ressource Anmeldeinformationen als Parameter verwendet:
-   Überprüfen Sie, ob die Ressource funktioniert, wenn das lokale System (oder das Computerkonto für Remoteressourcen) keinen Zugriff hat.
-   Überprüfen Sie, ob die Ressource mit für „Get“, „Set“ und „Test“ angegebenen Anmeldeinformationen funktioniert. 
-   Wenn die Ressource auf Freigaben zugreift, testen Sie alle Varianten, die Sie unterstützen müssen.  
Beispiel:
- Windows-Standardfreigaben.
- DFS-Freigaben
- SAMBA-Freigaben (wenn Sie Linux unterstützen möchten)

## Ressource ohne Cmdlets mit erforderlicher interaktiver Eingabe ##
**Get/Set/Test-TargetResource**-Funktionen sollen automatisch ausgeführt werden und in keiner Phase der Ausführung auf Benutzereingaben warten (platzieren Sie deshalb **Get-Credential** nicht innerhalb dieser Funktionen). Wenn Sie Benutzereingaben bereitstellen müssen, sollten Sie sie in der Kompilierungsphase als Parameter an die Konfiguration übergeben. 
## Gründliches Testen der Ressourcenfunktionalität ##
Sie sind verantwortlich, dass sich die Ressource ordnungsgemäß verhält. Deshalb müssen Sie ihre Funktionalität manuell oder besser noch automatisiert testen. Diese Prüfliste enthält Elemente, die unbedingt getestet werden sollten und/oder oft übersehen werden. Es gibt eine Vielzahl von Tests, hauptsächlich Funktionstests, die spezifisch für die Ressource sind, die Sie testen, und hier nicht erwähnt werden. Vergessen Sie nicht die negativen Testfälle. Diese stellen wahrscheinlich den aufwendigsten Teil der Ressourcentests dar. 
## Bewährte Methode: Ressourcenmodul enthält den Ordner „Tests“ mit dem Skript „ResourceDesignerTests.ps1“ ##
Es empfiehlt sich, im Ressourcenmodul den Ordner „Tests“ anzulegen, die Datei „ResourceDesignerTests.ps1“ zu erstellen und über **Test-xDscResource** und **Test-xDscSchema** Tests für alle Ressourcen in einem bestimmten Modul hinzuzufügen. 
Auf diese Weise können wir schnell die Schemas aller Ressourcen aus bestimmten Modulen überprüfen und vor der Veröffentlichung eine Integritätsprüfung vornehmen.
Für „xRemoteFile“ kann „ResourceTests.ps1“ einfach so aussehen:
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof 
```
**Bewährte Methode: Ressourcenordner enthält Ressourcen-Designer-Skript zur Generierung des Schemas**
Jede Ressource sollte ein Ressourcen-Designer-Skript enthalten, mit dem ein MOF-Schema der Ressource generiert wird. Diese Datei sollte in <ResourceName>„\ResourceDesignerScripts“ gespeichert und „Generate<ResourceName>Schema.ps1“ genannt werden.
Für die Ressource „xRemoteFile“ wird diese Datei „GenerateXRemoteFileSchema.ps1“ genannt und enthält Folgendes:
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
22  Bewährte Methode: Die Ressource unterstützt „-whatif“
Wenn mit der Ressource „gefährliche“ Vorgänge ausgeführt werden, empfiehlt es sich, „-whatif“-Funktionalität zu implementieren. Nachdem dies erfolgt ist, stellen Sie sicher, dass die „whatif“-Ausgabe Vorgänge ordnungsgemäß beschreibt, die eintreten würden, wenn der Befehl ohne den Schalter „whatif“ ausgeführt würde.
Vergewissern Sie sich auch, dass wenn der Schalter „-whatif“ vorhanden ist, keine Vorgänge ausgeführt werden (d. h. keine Änderungen am Zustand des Knotens erfolgen). 
Angenommen, wir testen die Ressource „File“. Nachstehend finden Sie einfache Konfiguration, die die Datei „test.txt“ mit dem Inhalt „test“ erstellt:
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
Wenn wir die Konfiguration kompilieren und dann mit dem Schalter „-whatif“ ausführen, gibt die Ausgabe genau an, was bei Ausführung der Konfiguration passieren würde. Die Konfiguration selbst wurde jedoch nicht ausgeführt (die Datei „test.txt“ wurde nicht erstellt).
```powershell 
Start-DscConfiguration -path .\config -ComputerName localhost -wait -verbose -whatif
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

Hiermit endet unsere Prüfliste. Beachten Sie, dass diese Liste nicht vollständig ist. Doch sie spricht viele wichtige Aspekte an, auf die wir beim Entwerfen, Entwickeln und Testen von DSC-Ressourcen gestoßen sind. Eine Prüfliste hilft sicherstellen, dass wir keinen dieser Aspekte vergessen. Zudem nutzen wir sie bei Microsoft selbst bei der Entwicklung von DSC-Ressourcen. 
Wenn Sie Leitlinien und bewährte Methoden formuliert haben, die Sie beim Schreiben und Testen von DSC-Ressourcen befolgen, teilen Sie sie bitte mit uns!
<!--HONumber=Mar16_HO1-->
