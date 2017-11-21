---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Erstellen einer Pipeline für Continuous Integration und Continuous Deplyoment mit DSC"
ms.openlocfilehash: baa56088d83fba56d3a19cff7954d3081f341f9a
ms.sourcegitcommit: 60c6f9d8cf316e6d5b285854e6e5641ac7648f3f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2017
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a>Erstellen einer Pipeline für Continuous Integration und Continuous Deplyoment mit DSC

Dieses Beispiel zeigt, wie Sie unter Verwendung von PowerShell, DSC, Pester und Visual Studio Team Foundation Server (TFS) eine CI/CD-Pipeline (Continuous Integration/Continuous Deployment) erstellen.

Nachdem die Pipeline erstellt und konfiguriert wurde, können Sie sie für das vollständige Bereitstellen, Konfigurieren und Testen eines DNS-Servers sowie der zugeordneten Hosteinträge verwenden. Dieser Prozess simuliert den ersten Teil einer Pipeline, die in einer Entwicklungsumgebung verwendet werden würde.

Eine automatisierte CI/CD-Pipeline unterstützt Sie bei einer schnelleren und zuverlässigeren Aktualisierung Ihrer Software. Außerdem wird sichergestellt, dass der gesamte Code getestet wird und dass immer ein aktueller Build Ihres Codes verfügbar ist.

## <a name="prerequisites"></a>Voraussetzungen

Um dieses Beispiel zu verwenden, sollten Sie mit folgenden Konzepten und Modellen vertraut sein:

- CI-CD-Konzepte, eine gute Referenz bietet [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf) (Das Releasepipeline-Modell)
- [Git](https://git-scm.com/)-Quellcodeverwaltung
- Das [Pester](https://github.com/pester/Pester)-Testframework
- [Team Foundation Server](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a>Benötigte Komponenten

Um dieses Beispiel zu erstellen und auszuführen, benötigen Sie eine Umgebung mit verschiedenen physischen und/oder virtuellen Computern.

### <a name="client"></a>Client

Dies ist der Computer, auf dem Sie die gesamte Arbeitseinrichtung vornehmen und das Beispiel ausführen.

Der Clientcomputer muss ein Windows-Computer sein, auf dem folgende Komponenten installiert sind:
- [Git](https://git-scm.com/)
- Ein lokales Git-Repository, geklont aus https://github.com/PowerShell/Demo_CI
- Ein Text-Editor, z.B. [Visual Studio Code](https://code.visualstudio.com/)

### <a name="tfssrv1"></a>TFSSrv1

Der Computer, der den TFS-Server hostet, auf dem Sie Build und Release definieren.
Auf diesem Computer muss [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installiert sein.

### <a name="buildagent"></a>BuildAgent

Der Computer, auf dem der Windows-Build-Agent ausgeführt wird, mit dem das Projekt erstellt wird.
Auf diesem Computer muss ein Windows-Build-Agent installiert sein und ausgeführt werden.
Anweisungen zum Installieren und Ausführen eines Windows-Build-Agents finden Sie unter [Bereitstellen eines Agents unter Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows).

Sie müssen außerdem die DSC-Module `xDnsServer` und `xNetworking` auf diesem Computer installieren.

### <a name="testagent1"></a>TestAgent1

Dies ist der Computer, der anhand der DSC-Konfiguration in diesem Beispiel als DNS-Server konfiguriert wird.
Auf dem Computer muss [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016) ausgeführt werden.

### <a name="testagent2"></a>TestAgent2

Dies ist der Computer, der die in diesem Beispiel konfigurierte Website hostet.
Auf dem Computer muss [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016) ausgeführt werden. 

## <a name="add-the-code-to-tfs"></a>Hinzufügen des Codes zu TFS

Im ersten Schritt erstellen wir ein Git-Repository in TFS und importieren den Code aus Ihrem lokalen Repository auf den Clientcomputer.
Wenn Sie das Demo_CI-Repository noch nicht auf Ihren Clientcomputer geklont haben, holen Sie dies jetzt nach, indem Sie den folgenden Git-Befehl ausführen:

`git clone https://github.com/PowerShell/Demo_CI`

1. Navigieren Sie auf Ihrem Clientcomputer in einem Webbrowser zu Ihrem TFS-Server.
1. [Erstellen Sie in TFS ein neues Teamprojekt](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) mit dem Namen „Demo_CI“.

    Stellen Sie sicher, dass **Versionskontrolle** auf **Git** festgelegt ist.
1. Fügen Sie dem soeben auf Ihrem Clientcomputer in TFS erstellten Repository mit dem folgenden Befehl ein Remoterepository hinzu:

    `git remote add tfs <YourTFSRepoURL>`

    Hierbei steht `<YourTFSRepoURL>` für die URL zum Klonen des TFS-Repositorys, das Sie im vorherigen Schritt erstellt haben.

    Wenn Sie nicht wissen, wo Sie diese URL finden, lesen Sie den Artikel [Klonen eines vorhandenen Git-Repositorys](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).
1. Pushen Sie mit dem folgenden Befehl den Code aus Ihrem lokalen Repository in Ihr TFS-Repository:

    `git push tfs --all`
1. Das TFS-Repository wird mit dem Demo_CI-Code aufgefüllt.

>**Hinweis**: Dieses Beispiel verwendet den Code im `ci-cd-example`-Branch des Git-Repositorys.
>Achten Sie darauf, diesen Branch in Ihrem TFS-Projekt sowie für die erstellten CI/CD-Trigger als Standardbranch anzugeben.

## <a name="understanding-the-code"></a>Grundlegendes zum Code

Sehen wir uns vor dem Erstellen der Build- und Bereitstellungspipelines einige Codeabschnitt an, um deren Bedeutung zu verstehen.
Öffnen Sie auf dem Clientcomputer Ihren bevorzugten Text-Editor, und navigieren Sie zum Stamm Ihres Git-Repositorys „Demo_CI“.

### <a name="the-dsc-configuration"></a>Die DSC-Konfiguration

Öffnen Sie die Datei `DNSServer.ps1` (ausgehend vom Stamm des lokalen Demo_CI-Repositorys, `./InfraDNS/Configs/DNSServer.ps1`).

Diese Datei enthält die DSC-Konfiguration zum Einrichten des DNS-Servers. Dies ist der vollständige Code:

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

Beachten Sie die `Node`-Anweisung:

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

Hiermit werden alle Knoten gesucht, die in den vom `DevEnv.ps1`-Skript erstellten [Konfigurationsdaten](configData.md) mit der Rolle `DNSServer` definiert wurden.

Die Verwendung von Konfigurationsdaten zum Definieren von Knoten ist im Rahmen der Continuous Integration wichtig, weil sich Knoteninformationen je nach Umgebung wahrscheinlich ändern. Mithilfe von Konfigurationsdaten können Sie problemlos Änderungen an Knoteninformationen durchführen, ohne den Konfigurationscode ändern zu müssen.

Im ersten Ressourcenblock ruft die Konfiguration [WindowsFeature](windowsFeatureResource.md) auf, um sicherzustellen, dass das DNS-Feature aktiviert ist. Die folgenden Ressourcenblöcke rufen Ressourcen aus dem [xDnsServer](https://github.com/PowerShell/xDnsServer)-Modul auf, um die primäre Zone und DNS-Einträge zu konfigurieren.

Beachten Sie, dass die zwei `xDnsRecord`-Blöcke von `foreach`-Schleifen umschlossen sind, mit denen die Arrays in den Konfigurationsdaten durchlaufen werden.
Auch hier werden die Konfigurationsdaten durch das `DevEnv.ps1`-Skript erstellt, das wir nachfolgend betrachten.

### <a name="configuration-data"></a>Konfigurationsdaten

Die `DevEnv.ps1`-Datei (ausgehend vom Stamm des lokalen Demo_CI-Repositorys, `./InfraDNS/DevEnv.ps1`), gibt die umgebungsspezifischen Konfigurationsdaten in einer Hashtabelle an und übergibt diese Hashtabelle an einen Aufruf der `New-DscConfigurationDataDocument`-Funktion, die in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`) definiert ist.

Die Datei `DevEnv.ps1` enthält Folgendes:

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

Die `New-DscConfigurationDataDocument`-Funktion (definiert in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) erstellt programmgesteuert ein Dokument mit Konfigurationsdaten aus der Hashtabelle (Knotendaten) und dem Array (Nicht-Knotendaten), die als Parameter `RawEnvData` und `OtherEnvData` übergeben werden.

Im vorliegenden Fall wird nur der Parameter `RawEnvData` verwendet.

### <a name="the-psake-build-script"></a>Das psake-Buildskript

Das in `Build.ps1` (ausgehend vom Stamm des Demo_CI-Repositorys, `./InfraDNS/Build.ps1`) definierte [psake](https://github.com/psake/psake)-Buildskript definiert Tasks, die Bestandteil des Builds sind.
Darüber hinaus wird definiert, von welchen weiteren Tasks jeder Task abhängt. Beim Aufruf des psake-Skripts wird sichergestellt, dass der angegebene Task (oder der Task `Default`, sofern kein Task angegeben wird) ausgeführt wird, ebenso wie alle abhängigen Komponenten (dieser Vorgang ist rekursiv, d.h. abhängige Komponenten von abhängigen Komponenten werden ausgeführt usw.).

In diesem Beispiel ist der `Default`-Task so definiert:

```powershell
Task Default -depends UnitTests
```

Der `Default`-Task weist selbst keine Implementierung auf, sondern hängt vom `CompileConfigs`-Task ab.
Die Ergebniskette aus Taskabhängigkeiten stellt sicher, dass alle Tasks im Buildskript ausgeführt werden.

In diesem Beispiel wird das psake-Skript durch einen Aufruf von `Invoke-PSake` in der `Initiate.ps1`-Datei aufgerufen (diese befindet sich im Stamm des Demo_CI-Repositorys):

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

Wenn wir die Builddefinition für unser Beispiel in TFS erstellen, geben wir unsere pskake-Skriptdatei als `fileName`-Parameter für dieses Skript an.

Das Buildskript definiert die folgenden Tasks:

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

Führt `DevEnv.ps1` aus, mit der die Konfigurationsdatendatei generiert wird.

#### <a name="installmodules"></a>InstallModules

Installiert die von der Konfiguration `DNSServer.ps1` benötigten Module.

#### <a name="scriptanalysis"></a>ScriptAnalysis

Ruft [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) auf.

#### <a name="unittests"></a>UnitTests

Führt die [Pester](https://github.com/pester/Pester/wiki)-Komponententests aus.

#### <a name="compileconfigs"></a>CompileConfigs

Kompiliert die Konfiguration (`DNSServer.ps1`) unter Verwendung der über den `GenerateEnvironmentFiles`-Task generierten Konfigurationsdaten in eine MOF-Datei.

#### <a name="clean"></a>Clean

Erstellt die für das Beispiel verwendeten Ordner und entfernt alle Testergebnisse, Konfigurationsdatendateien und Module aus vorherigen Ausführungen.

### <a name="the-psake-deploy-script"></a>Das psake-Bereitstellungsskript

Das in `Deploy.ps1` (ausgehend vom Stamm des Demo_CI-Repositorys, `./InfraDNS/Deploy.ps1`) definierte [psake](https://github.com/psake/psake)-Bereitstellungsskript definiert Tasks zum Bereitstellen und Ausführen der Konfiguration.

`Deploy.ps1` definiert die folgenden Tasks:

#### <a name="deploymodules"></a>DeployModules

Startet eine PowerShell-Sitzung auf `TestAgent1` und installiert die Module mit den DSC-Ressourcen, die für die Konfiguration erforderlich sind.

#### <a name="deployconfigs"></a>DeployConfigs

Ruft das Cmdlet [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) auf, um die Konfiguration auf `TestAgent1` auszuführen.

#### <a name="integrationtests"></a>IntegrationTests

Führt die [Pester](https://github.com/pester/Pester/wiki)-Integrationstests aus.

#### <a name="acceptancetests"></a>AcceptanceTests

Führt die [Pester](https://github.com/pester/Pester/wiki)-Akzeptanztests aus.

#### <a name="clean"></a>Clean

Entfernt alle in vorherigen Ausführungen installierten Module und stellt sicher, dass die Testergebnisordner vorhanden sind.

### <a name="test-scripts"></a>Testskripts

Die Akzeptanz-, Integrations- und Komponententests werden in Skripts im Ordner `Tests` (ausgehend vom Stamm des Demo_CI-Repositorys, `./InfraDNS/Tests`) definiert, in Dateien namens `DNSServer.tests.ps1` in den jeweiligen Ordnern.

Die Testskripts verwenden die [Pester](https://github.com/pester/Pester/wiki)- und [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction)-Syntax.

#### <a name="unit-tests"></a>Komponententests

Mit den Komponententests werden die DSC-Konfigurationen selbst getestet. So wird sichergestellt, dass die Konfigurationen bei ihrer Ausführung wie erwartet funktionieren.
Das Skript für den Komponententest verwendet [Pester](https://github.com/pester/Pester/wiki).

#### <a name="integration-tests"></a>Integrationstests

Mit den Integrationstests wird die Konfiguration des Systems getestet. So wird gewährleistet, dass das System bei der Integration in andere Komponenten wie erwartet konfiguriert wird. Diese Tests werden nach der Konfiguration mit DSC auf dem Zielknoten ausgeführt.
Das Skript für die Integrationstests verwendet eine Kombination aus der [Pester](https://github.com/pester/Pester/wiki)- und [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction)-Syntax.

#### <a name="acceptance-tests"></a>Akzeptanztests

Über die Akzeptanztests wird getestet, ob sich das System wie erwartet verhält.
Beispielsweise wird getestet, ob eine Webseite bei der Abfrage die richtigen Informationen zurückgibt.
Diese Tests werden remote vom Zielknoten aus ausgeführt, um ein realistisches Szenario für den Test zu schaffen.
Das Skript für die Integrationstests verwendet eine Kombination aus der [Pester](https://github.com/pester/Pester/wiki)- und [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction)-Syntax.

## <a name="define-the-build"></a>Definieren des Builds

Fahren wir jetzt, nachdem wir unseren Code in TFS hochgeladen und uns seine Funktionsweise angesehen haben, mit dem Definieren unseres Builds fort.

Nachfolgend werden nur die Buildschritte abgedeckt, die Sie dem Build hinzufügen. Anweisungen zum Erstellen einer Builddefinition in TFS finden Sie unter [Erstellen einer Builddefinition und Einreihen in die Warteschlange](https://www.visualstudio.com/en-us/docs/build/define/create).

Erstellen Sie eine neue Builddefinition namens „InfraDNS“ (wählen Sie die Vorlage **Leer** aus).
Fügen Sie Ihrer Builddefinition die folgenden Schritte hinzu:

- PowerShell-Skript
- Testergebnisse veröffentlichen
- Dateien kopieren
- Artefakt veröffentlichen

Nachdem Sie diese Buildschritte hinzugefügt haben, bearbeiten Sie die Eigenschaften jedes Schritts folgendermaßen:

### <a name="powershell-script"></a>PowerShell-Skript

1. Legen Sie die Eigenschaft **Typ** auf `File Path` fest.
1. Legen Sie die Eigenschaft **Skriptpfad** auf `initiate.ps1` fest.
1. Fügen Sie `-fileName build` zur Eigenschaft **Argumente** hinzu.

Mit diesem Buildschritt wird die Datei `initiate.ps1` ausgeführt, mit der das psake-Buildskript aufgerufen wird.

### <a name="publish-test-results"></a>Testergebnisse veröffentlichen

1. Legen Sie **Testergebnisformat** auf `NUnit` fest.
1. Legen Sie **Testergebnisdateien** auf `InfraDNS/Tests/Results/*.xml` fest.
1. Legen Sie **Testlauftitel** auf `Unit` fest.
1. Stellen Sie sicher, dass sowohl **Steuerungsoptionen** **Aktiviert** als auch **Immer ausführen** ausgewählt sind.

Mit diesem Buildschritt werden die Komponententests im Pester-Skript ausgeführt, das wir uns weiter oben angesehen haben. Die Ergebnisse werden im Ordner `InfraDNS/Tests/Results/*.xml` gespeichert.

### <a name="copy-files"></a>Dateien kopieren

1. Fügen Sie **Inhalte** jede der folgenden Zeilen hinzu:

    ```
    initiate.ps1
    **\deploy.ps1
    **\Acceptance\**
    **\Integration\**
    ```

1. Legen Sie **TargetFolder** auf `$(Build.ArtifactStagingDirectory)\` fest.

Mit diesem Schritt werden der Build und die Testskripts in das Stagingverzeichnis kopiert, sodass im nächsten Schritt eine Veröffentlichung als Buildartefakte erfolgen kann.

### <a name="publish-artifact"></a>Artefakt veröffentlichen

1. Legen Sie **Zu veröffentlichender Pfad** auf `$(Build.ArtifactStagingDirectory)\` fest.
1. Legen Sie **Artefaktname** auf `Deploy` fest.
1. Legen Sie **Artefaktyp** auf `Server` fest.
1. Wählen Sie in den **Steuerungsoptionen** die Einstellung `Enabled` aus.

## <a name="enable-continuous-integration"></a>Aktivieren der Continuous Integration

Jetzt richten wir einen Trigger ein, mit dem das Projekt immer dann erstellt wird, wenn eine Änderung in den `ci-cd-example`-Branch des Git-Repositorys eingecheckt wird.

1. Klicken Sie in TFS auf die Registerkarte **Build und Release**.
1. Wählen Sie die Builddefinition `DNS Infra` aus, und klicken Sie auf **Bearbeiten**.
1. Klicken Sie auf die Registerkarte **Trigger**.
1. Wählen Sie **Continuous Integration (CI)** aus, und wählen Sie in der Dropdownliste für den Branch `refs/heads/ci-cd-example` aus.
1. Klicken Sie auf **Speichern** und anschließend auf **OK**.

Jetzt löst jede Änderung im TFS-Git-Repository eine automatisierte Builderstellung aus.

## <a name="create-the-release-definition"></a>Erstellen der Releasedefinition

Erstellen wir jetzt eine Releasedefinition, damit das Projekt immer dann in der Entwicklungsumgebung bereitgestellt wird, wenn der Code eingecheckt wird.

Fügen Sie hierzu eine neue Releasedefinition hinzu, die der zuvor erstellten Builddefinition `InfraDNS` zugeordnet ist.
Stellen Sie sicher, dass **Continuous Deployment** ausgewählt ist, damit immer dann eine neue Release ausgelöst wird, wenn ein neuer Build erstellt wurde.
([Gewusst wie: Arbeiten mit Releasedefinitionen](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) und anschließende Konfiguration:

Fügen Sie der Releasedefinition die folgenden Schritte hinzu:

- PowerShell-Skript
- Testergebnisse veröffentlichen
- Testergebnisse veröffentlichen

Bearbeiten Sie die Schritte wie folgt:

### <a name="powershell-script"></a>PowerShell-Skript

1. Legen Sie das Feld **Skriptpfad** auf `$(Build.DefinitionName)\Deploy\initiate.ps1"` fest.
1. Legen Sie das Feld **Argumente** auf `-fileName Deploy` fest.

### <a name="first-publish-test-results"></a>Erstes Veröffentlichen der Testergebnisse

1. Wählen Sie für das Feld **Testergebnisformat** die Einstellung `NUnit` aus.
1. Legen Sie das Feld **Testergebnisdateien** auf `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml` fest.
1. Legen Sie **Testlauftitel** auf `Integration` fest.
1. Aktivieren Sie unter **Steuerungsoptionen** die Option **Immer ausführen**.

### <a name="second-publish-test-results"></a>Zweites Veröffentlichen der Testergebnisse

1. Wählen Sie für das Feld **Testergebnisformat** die Einstellung `NUnit` aus.
1. Legen Sie das Feld **Testergebnisdateien** auf `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml` fest.
1. Legen Sie **Testlauftitel** auf `Acceptance` fest.
1. Aktivieren Sie unter **Steuerungsoptionen** die Option **Immer ausführen**.

## <a name="verify-your-results"></a>Überprüfen Ihrer Ergebnisse

Jetzt wird jedes Mal, wenn Sie Änderungen in den `ci-cd-example`-Branch in TFS pushen, ein neuer Build gestartet.
Bei einem erfolgreichen Abschluss des Builds wird eine neue Bereitstellung ausgelöst.

Sie können die Ergebnisse der Bereitstellung überprüfen, indem Sie einen Browser auf dem Clientcomputer öffnen und zu `www.contoso.com` navigieren.

## <a name="next-steps"></a>Nächste Schritte

In diesem Beispiel wird der DNS-Server `TestAgent1` konfiguriert, damit die URL `www.contoso.com` in `TestAgent2` aufgelöst wird. Es erfolgt jedoch keine tatsächliche Bereitstellung einer Website.
Das Skeleton hierfür wird im Repository unterhalb des Ordners `WebApp` bereitgestellt.
Sie können die bereitgestellten Stubs zum Erstellen von psake-Skripts, Pester-Tests und DSC-Konfigurationen verwenden, um Ihre eigene Website bereitzustellen.







