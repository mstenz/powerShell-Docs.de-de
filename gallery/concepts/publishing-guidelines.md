---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
description: Richtlinien für Herausgeber
title: Veröffentlichungsrichtlinien und Best Practices für den PowerShell-Katalog
ms.openlocfilehash: 1cd0140cc208949e13d23331b23a58ffc374430b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084656"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>Veröffentlichungsrichtlinien und Best Practices für den PowerShell-Katalog

In diesem Thema erfahren Sie, welche Schritte die Microsoft-Teams empfehlen, damit Ihre im PowerShell-Katalog veröffentlichten Pakete von möglichst vielen Benutzern verwendet werden und diesen einen hohen Mehrwert bieten. Diese Empfehlungen basieren auf der Verarbeitung von Manifestdaten durch den PowerShell-Katalog sowie auf dem Feedback zahlreicher PowerShell-Katalogbenutzer.
Pakete, die gemäß den hier beschriebenen Richtlinien veröffentlicht werden, werden eher installiert, als vertrauenswürdig eingestuft und erzielen ein größeres Benutzerinteresse.

Die nachfolgenden Richtlinien definieren, wodurch sich ein gutes PowerShell-Katalogpaket auszeichnet, welche optionalen Manifesteinstellungen besonders wichtig sind, wie Sie Ihren Code mithilfe von Benutzerfeedback und [PowerShell Script Analyzer](https://aka.ms/psscriptanalyzer) verbessern und wie Sie die Versionsverwaltung Ihres Moduls, der zugehörigen Dokumentation sowie von Tests und Anwendungsbeispielen durchführen.
Ein Großteil dieser Dokumentation folgt den Richtlinien für das Veröffentlichen von [hochwertigen DSC-Ressourcenmodulen](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).

Informationen zu den Mechanismen für das Veröffentlichen eines Pakets im PowerShell-Katalog finden Sie unter [Erstellen und Veröffentlichen eines Pakets](/powershell/gallery/how-to/publishing-packages/publishing-a-package).

Wir freuen uns auf Ihr Feedback zu diesen Richtlinien. Wenn Sie Anmerkungen haben, öffnen Sie ein Problem in unserem [GitHub-Dokumentationsrepository](https://github.com/powershell/powershell-docs/issues).

## <a name="best-practices-for-publishing-packages"></a>Bewährte Methoden zum Veröffentlichen von Paketen

Die folgenden Best Practices für PowerShell-Katalogelemente definieren die Punkte, die von Katalogbenutzern als wichtig eingestuft werden, aufgeführt nach der genannten Priorität.
Pakete, die diesen Richtlinien entsprechen, werden eher heruntergeladen und von den Benutzern angenommen.

- Verwenden Sie PSScriptAnalyzer
- Stellen Sie eine Dokumentation und Beispiele bereit
- Antworten Sie auf Feedback
- Stellen Sie anstelle von Skripts Module bereit
- Stellen Sie einen Link zu einer Projektwebsite bereit
- Versehen Sie Ihr Paket mit Tags der kompatiblen PowerShell-Edition(en) und Plattformen
- Schließen Sie Tests in Ihre Module ein
- Schließen Sie Lizenzbedingungen (bzw. einen Link auf diese) ein
- Signieren Sie Ihren Code
- Folgen Sie bei der Versionsverwaltung den [SemVer](http://semver.org/)-Richtlinien
- Verwenden Sie allgemeine Tags, wie in „Common PowerShell Gallery Tags“ dokumentiert.
- Testen der Veröffentlichung mit einem lokalen Repository
- Verwenden von PowerShell für die Veröffentlichung

Jede dieser Richtlinien wird in den nachfolgenden Abschnitten kurz erläutert.

## <a name="use-psscriptanalyzer"></a>Verwenden Sie PSScriptAnalyzer

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) ist ein kostenloses Analysetool für statischen Code, das für PowerShell-Code eingesetzt werden kann.
PSScriptAnalyzer identifiziert die häufigsten Probleme in PowerShell-Code und stellt in vielen Fällen eine Empfehlung zur Lösung des Problems bereit.
Das Tool ist einfach bedienbar und unterteilt die Probleme in Fehler (schwerwiegend, müssen behoben werden), Warnungen (müssen überprüft und sollten behoben werden) und Informationsmeldungen (sollten im Rahmen der Best Practices überprüft werden).
Alle der im PowerShell-Katalog veröffentlichten Pakete werden mithilfe von PSScriptAnalyzer überprüft. Gefundene Fehler werden dem Besitzer gemeldet und müssen beseitigt werden.

Als Best Practice wird `Invoke-ScriptAnalyzer` mit `-Recurse` und `-Severity` mit der Einstellung „Warning“ ausgeführt. 

Überprüfen Sie die Ergebnisse, und stellen Sie Folgendes sicher:

- Alle Fehler wurden behoben oder in Ihrer Dokumentation behandelt.
- Alle Warnungen wurden überprüft und nach Möglichkeit behoben.

Benutzern, die Pakete aus dem PowerShell-Katalog abrufen, wird dringend empfohlen, PSScriptAnalyzer auszuführen und alle Fehler und Warnungen auszuwerten.
Benutzer setzen sich sehr wahrscheinlich mit den Paketbesitzern in Verbindung, wenn PSScriptAnalyzer einen Fehler meldet.
Wenn ein triftiger Grund dafür spricht, als fehlerhaft markierten Code für Ihr Paket beizubehalten, fügen Sie diese Information in Ihre Dokumentation ein. So müssen Sie nicht wiederholt dieselbe Frage beantworten.

## <a name="include-documentation-and-examples"></a>Stellen Sie eine Dokumentation und Beispiele bereit

Benutzer können freigegebenen Code optimal nutzen, wenn eine Dokumentation und Beispiele bereitgestellt werden.

Die Dokumentation ist die nützlichste Informationsquelle, die für ein im PowerShell-Katalog veröffentlichtes Paket bereitgestellt werden kann.
Benutzer meiden im Allgemeinen Pakete ohne Dokumentation, da die Alternative darin besteht, den Code lesen zu müssen, um das Paket und seine Verwendung zu verstehen.
In MSDN finden Sie verschiedene Artikel zur Bereitstellung von Dokumentation für PowerShell-Pakete, darunter diese:

- Richtlinien zum Bereitstellen von Hilfe finden Sie im Artikel [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) (Schreiben von Hilfe zu Cmdlets).
- Das Erstellen von Hilfetexten zu Cmdlets ist der beste Ansatz für beliebige PowerShell-Skripts, -Funktionen oder -Cmdlets.
  Informationen dazu, wie Sie eine Cmdlet-Hilfe schreiben, finden Sie unter [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) (Schreiben von Hilfe zu Cmdlets).
  Informationen dazu, wie Sie innerhalb eines Skripts Hilfe hinzufügen, finden Sie unter [Informationen zur kommentarbasierten Hilfe](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).
- Viele Module enthalten Dokumentation in Textformat, z.B. als MarkDown-Dateien.
  Dies kann besonders nützlich sein, wenn eine Projektwebsite in GitHub vorhanden ist, wo Markdown-Dateien ein häufig verwendetes Format sind.
  Als Best Practice sollte [GitHub Flavored Markdown (GFM)](https://help.github.com/categories/writing-on-github/) verwendet werden.

Beispiele zeigen dem Benutzer, wie das Paket verwendet werden sollte.
Viele Entwickler sehen sich die Beispiele noch vor der Dokumentation an, um die Verwendungsweise eines Elements zu verstehen.
Die besten Beispiele zeigen die grundlegende Verwendung sowie einige simulierte Anwendungsfälle, und der Code ist gut kommentiert.
Beispiele für im PowerShell-Katalog veröffentlichte Module sollten in einem Ordner „Examples“ im Modulstamm enthalten sein.

Ein gutes Muster für Beispiele finden Sie im [PSDscResource-Modul](https://www.powershellgallery.com/packages/PSDscResources) im Ordner „Examples\RegistryResource“.
Dort sind vier Beispielanwendungsfälle mit einer kurzen Beschreibung zu Beginn jeder Datei enthalten, die das Gezeigte dokumentieren.

## <a name="respond-to-feedback"></a>Antworten Sie auf Feedback

Paketbesitzer, die angemessen auf Feedback reagieren, werden in der Community sehr geschätzt.
Es ist wichtig, Benutzern zu antworten, die konstruktives Feedback geben, da diese Benutzer Sie dabei unterstützen können, das Paket zu verbessern.

Im PowerShell-Katalog sind zwei Feedbackmethoden verfügbar:

- Besitzer kontaktieren: Über diese Option kann ein Benutzer eine E-Mail an den oder die Paketbesitzer senden. Als Paketbesitzer müssen Sie dafür Sorge tragen, dass die für PowerShell-Katalogpakete verwendete E-Mail-Adresse regelmäßig überwacht wird und gemeldete Probleme gelöst werden. Ein Nachteil dieser Methode besteht darin, dass die Kommunikation nur zwischen Benutzer und Besitzer erfolgt, sodass der Besitzer dieselbe Frage möglicherweise wiederholt beantworten muss.
- Kommentare: Im unteren Bereich der Paketseite befindet sich ein Kommentarfeld.
  Der Vorteil dieses Systems liegt darin, dass andere Benutzer die Kommentare und Antworten sehen können. Auf diese Weise muss eine einzelne Frage nicht wiederholt beantwortet werden.
  Paketbesitzern wird dringend empfohlen, die Kommentare für jedes Paket zu verfolgen.
Ausführliche Informationen hierzu finden Sie unter [Bereitstellen von Feedback über soziale Netzwerke oder Kommentare](../how-to/working-with-packages/social-media-feedback.md).

Besitzer, die konstruktiv auf Feedback reagieren, werden von der Community sehr geschätzt.
Nutzen Sie die Gelegenheit, im Bericht bei Bedarf weitere Informationen anzufordern, eine Problemumgehung bereitzustellen oder darauf hinzuweisen, dass ein Problem durch ein Update behoben werden kann.

Falls über einen dieser Kommunikationskanäle ein unangemessenes Verhalten beobachtet wird, verwenden Sie das Feature „Missbrauch melden“ im PowerShell-Katalog, um sich an die PowerShell-Katalogadministratoren zu wenden.

## <a name="modules-versus-scripts"></a>Module und Skripts im Vergleich

Das Freigeben eines Skripts für andere Benutzer ist grundsätzlich eine gute Sache und ermöglicht es, Beispiele für die Beseitigung möglicher Probleme bereitzustellen.
Der Nachteil von Skripts im PowerShell-Katalog liegt darin, dass es sich um einzelne Dateien ohne separate Dokumentation, Beispiele und Tests handelt.

PowerShell-Module bieten eine Ordnerstruktur, die es erlaubt, mehrere Ordner und Dateien in das Paket einzuschließen.
Die Modulstruktur ermöglicht das Bereitstellen weiterer Pakete, die wir als Best Practices auflisten: Cmdlet-Hilfe, Dokumentation, Beispiele und Tests.
Der größte Nachteil besteht darin, dass ein Skript innerhalb eines Moduls als Funktion verfügbar gemacht und verwendet werden muss.
Informationen zum Erstellen eines Moduls finden Sie unter [Writing a Windows PowerShell Module](http://go.microsoft.com/fwlink/?LinkId=144916) (Schreiben eines Windows PowerShell-Moduls).

Es gibt Situationen, in denen ein Skript benutzerfreundlicher ist, dies gilt insbesondere bei DSC-Konfigurationen.
Die bewährte Methode für DSC-Konfigurationen besteht darin, die Konfiguration als Skript zu veröffentlichen, gemeinsam mit einem Begleitmodul, das die Dokumentation, Beispiele und Tests enthält.
Im Skript wird das Begleitmodul unter Verwendung von „RequiredModules = @(Name des Moduls)“ aufgeführt.
Dieser Ansatz kann für jedes Skript verwendet werden.

Eigenständige Skripts, die den weiteren Best Practices entsprechen, bieten anderen Benutzern einen echten Nutzen.
Beim Veröffentlichen eines Skripts im PowerShell-Katalog wird dringend empfohlen, eine kommentarbasierte Dokumentation und einen Link zu einer Projektwebsite bereitzustellen.

## <a name="provide-a-link-to-a-project-site"></a>Stellen Sie einen Link zu einer Projektwebsite bereit

Auf einer Projektwebsite kann der Herausgeber direkt mit den Benutzern seiner PowerShell-Katalogpakete interagieren.
Benutzer bevorzugen Pakete mit einer Projektwebsite, weil es einfacher ist, Informationen zum Paket zu erhalten.
Viele Pakete im PowerShell-Katalog werden in GitHub entwickelt, andere werden von Organisationen mit einer dedizierten Webpräsenz bereitgestellt.
Beides kann als eine Projektwebsite betrachtet werden.

Ein Link kann durch Einschließen eines ProjectURI-Werts im PSData-Abschnitt des Manifests hinzugefügt werden:

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

Wenn Sie einen ProjectURI angeben, wird im PowerShell-Katalog links auf der Paketseite ein Link zur Projektwebsite angezeigt.

## <a name="tag-your-package-with-the-compatible-pseditions-and-platforms"></a>Versehen Sie Ihr Paket mit Tags der kompatiblen PowerShell-Edition(en) und Plattformen

Verwenden Sie die folgenden Tags, um Benutzern anzuzeigen, welche Pakete sich für deren Umgebung gut eignen:

- PSEdition_Desktop : Pakete, die mit Windows PowerShell kompatibel sind.
- PSEdition_Core : Pakete, die mit PowerShell Core kompatibel sind.
- Windows : Pakete, die mit dem Windows-Betriebssystem kompatibel sind.
- Linux : Pakete, die mit dem Linux-Betriebssystem kompatibel sind.
- MacOS : Pakete, die mit MacOS kompatibel sind.

Wenn Sie das Paket mit den kompatiblen Plattformen markieren, wird es in die Katalogsuchfilter im linken Bereich der Suchergebnisse einbezogen. Wenn Sie das Paket auf GitHub hosten, wenn Sie es markieren, profitieren Sie außerdem von unserem [PowerShell-Katalog-Kompatibilitätsschutz](https://img.shields.io/powershellgallery/p/:packageName.svg) 
![Kompatibilitätsschutz](https://img.shields.io/powershellgallery/p/CosmosDB.svg).  

## <a name="include-tests"></a>Schließen Sie Tests ein

Das Einschließen von Tests mit Open Source-Code ist wichtig für die Benutzer, weil diese so sicher sein können, dass Ihr Code überprüft wurde. Zudem können Sie Informationen zur Funktionsweise des Codes bereitstellen. Darüber hinaus können die Benutzer sich darauf verlassen, dass die ursprüngliche Funktionalität durch eine Anpassung Ihres Codes an die Benutzerumgebung nicht beeinträchtigt wird.

Es wird dringend empfohlen, Tests zu schreiben, um von den Vorteilen des Pester-Testframeworks zu profitieren, das speziell für PowerShell entworfen wurde.
Pester ist in [GitHub](https://github.com/Pester/Pester) und dem [PowerShell-Katalog](https://www.powershellgallery.com/packages/Pester/) verfügbar und gehört zum Lieferumfang von Windows 10, Windows Server 2016, WMF 5.0 und WMF 5.1.

Die [Pester-Projektwebsite in GitHub](https://github.com/Pester/Pester) umfasst eine gute Dokumentation zum Schreiben von Pester-Tests – von den ersten Schritten bis hin zu den Best Practices.

Die Ziele für die Testabdeckung werden in der [Dokumentation zu hochwertigen Ressourcenmodulen](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md) benannt, hierbei wird für Komponententests eine Codeabdeckung von 70 % empfohlen.

## <a name="include-andor-link-to-license-terms"></a>Schließen Sie Lizenzbedingungen (bzw. einen Link auf diese) ein

Alle Pakete, die im PowerShell-Katalog veröffentlicht werden, müssen Lizenzbedingungen angeben oder der Lizenz unterliegen, die in den [Nutzungsbedingungen](https://www.powershellgallery.com/policies/Terms) unter „Anhang A“ enthalten sind.
Der beste Ansatz für das Angeben einer anderen Lizenz besteht darin, mithilfe von LicenseURI im PSData-Abschnitt einen Link zur Lizenz bereitzustellen.
Ein Beispiel finden Sie im Thema zu den empfohlenen Manifestfeldern.

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>Signieren Sie Ihren Code

Durch Signieren des Codes bieten Sie Benutzern höchstmögliche Sicherheit in Bezug auf den Paketherausgeber – die Benutzer können darauf vertrauen, dass die erworbene Kopie des Codes exakt dem Code entspricht, den der Herausgeber veröffentlicht hat.
Allgemeine Informationen zum Signieren von Code finden Sie in der [Einführung in das Codesignieren](http://go.microsoft.com/fwlink/?LinkId=106296).
PowerShell unterstützt in Bezug auf das Signieren von Code zwei primäre Ansätze:

- Signieren von Skriptdateien
- Katalogsignierung von Modulen

Das Signieren von PowerShell-Dateien ist ein bewährter Ansatz, mit dem sichergestellt wird, dass der ausgeführte Code aus einer zuverlässigen Quelle stammt und nicht verändert wurde.
Details zum Signieren von PowerShell-Skriptdateien werden im Thema [Informationen zu Signaturen](/powershell/module/microsoft.powershell.core/about/about_signing) behandelt.
Allgemein ausgedrückt, kann eine Signatur jeder PS1-Datei hinzugefügt werden, die PowerShell beim Laden des Skripts überprüft.
Mithilfe der Cmdlets für [Ausführungsrichtlinien](/powershell/module/microsoft.powershell.core/about/about_execution_policies) kann PowerShell auf die Verwendung von signierten Skripts beschränkt werden.

Die Katalogsignierung von Modulen ist ein Feature, das PowerShell in Version 5.1 hinzugefügt wurde.
Das Signieren eines Moduls wird im Thema [Katalog-Cmdlets](/powershell/wmf/5.1/catalog-cmdlets) abgedeckt.
Allgemein ausgedrückt wird bei der Katalogsignierung eine Katalogdatei erstellt, die einen Hashwert für jede Datei im Modul enthält, und anschließend wird diese Datei signiert.
Die PowerShell-Cmdlets „publish-module“, „install-module“, „save-module“ und „update-module“ überprüfen die Signatur auf ihre Gültigkeit und bestätigen dann, dass der Hashwert für jedes Paket den Daten im Katalog entspricht.
Wenn eine vorherige Version des Moduls auf dem System installiert ist, wird mithilfe von „install-module“ bestätigt, dass die Signaturstelle für die neue Version derjenigen der vorherigen Installation entspricht.
Die Katalogsignierung kann zusammen mit dem Signieren von Skriptdateien verwendet werden, ersetzt diese Methode aber nicht. PowerShell führt beim Laden von Modulen keine Überprüfung von Katalogsignaturen durch.

## <a name="follow-semver-guidelines-for-versioning"></a>Folgen Sie bei der Versionsverwaltung den SemVer-Richtlinien

[SemVer](http://semver.org/) ist eine öffentliche Konvention, die beschreibt, wie eine Version strukturiert und geändert wird, um eine einfache Interpretation von Änderungen zu ermöglichen.
Die Version für Ihr Paket muss in den Manifestdaten enthalten sein.

- Die Version sollte aus 3 numerischen Blöcken bestehen, die durch Punkte getrennt sind. Beispiele: 0.1.1 oder 4.11.192
- Mit 0 beginnende Versionsnummern deuten darauf hin, dass das Paket noch nicht bereit für die Produktion ist, und die erste Nummer darf nur mit 0 beginnen, wenn dies die einzige verwendete Nummer ist.
- Änderungen an der ersten Nummer (1.9.9999 bis 2.0.0) weisen auf wichtige Änderungen und Änderungen mit Auswirkung auf die Lauffähigkeit der Versionen hin.
- Änderungen an der zweiten Nummer (1.1 bis 1.2) weisen auf Änderungen auf Featureebene hin, z.B. auf neue Cmdlets, die dem Modul hinzugefügt wurden.
- Änderungen an der dritten Nummer weisen auf Änderungen ohne Auswirkung auf die Lauffähigkeit hin, z.B. neue Parameter, aktualisierte Beispiele oder neue Tests.
- Beim Auflisten von Versionen sortiert PowerShell die Versionen als Zeichenfolgen, deshalb wird 1.01.0 als größer als 1.001.0 eingestuft.

PowerShell wurde vor Herausgabe der SemVer-Richtlinien entwickelt und bietet daher Unterstützung für die meisten, aber nicht alle Elemente von SemVer. Hierbei gilt insbesondere Folgendes:

- In Versionsnummern werden keine Zeichenfolgen für Vorabreleases unterstützt. Dies ist nützlich, wenn ein Herausgeber eine Vorschauversion einer neuen Hauptversion bereitstellen möchte, nachdem eine Version 1.0.0 veröffentlicht wurde. Diese Option wird in einer zukünftigen Version des PowerShell-Katalogs und der PowerShell-Cmdlets unterstützt.
- PowerShell und der PowerShell-Katalog lassen Versionszeichenfolgen mit 1, 2 und 4 Segmenten zu. Viele frühere Module entsprachen nicht den Richtlinien, und Produktversionen von Microsoft umfassen Buildinformationen als 4. Nummernblock (z.B. 5.1.14393.1066). Vom Standpunkt der Versionsverwaltung aus werden diese Unterschiede ignoriert.

## <a name="test-using-a-local-repository"></a>Testen mit einem lokalen Repository

Der PowerShell-Katalog ist nicht als Ziel zum Testen des Veröffentlichungsprozesses konzipiert.
Die beste Methode, um den End-to-End-Prozess der Veröffentlichung im PowerShell-Katalog zu testen, ist das Einrichten und Verwenden Ihres eigenen lokalen Repositorys.
Dies kann auf verschiedene Arten erfolgen, einschließlich folgender:

- Richten Sie mithilfe des [PS Private Gallery project (PS Private Gallery-Projekts)](https://github.com/PowerShell/PSPrivateGallery) in GitHub eine lokale Instanz des PowerShell-Katalogs ein. Dieses Vorschauprojekt wird Sie beim Einrichten einer Instanz des PowerShell-Katalogs unterstützen, die Sie steuern und für Ihre Tests benutzen können.
- Richten Sie ein [internes NuGet-Repository](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/) ein. Dieses einzurichten erfordert mehr Arbeit. Es hat jedoch den Vorteil, dass einige zusätzliche Anforderungen damit überprüft werden können. Dazu zählt insbesondere die Überprüfung der Verwendung eines API-Schlüssels und ob beim Veröffentlichen Abhängigkeiten im Ziel vorhanden sind.
- Richten Sie eine Dateifreigabe als „Test-Repository“ ein. Diese einzurichten ist einfach, aber da es sich dabei um eine Dateifreigabe handelt, werden die oben aufgeführten Überprüfungen nicht ausgeführt. Ein möglicher Vorteil in diesem Fall ist, dass die Dateifreigabe den (benötigten) API-Schlüssel nicht überprüft, sodass Sie denselben Schlüssel verwenden können, den Sie auch bei der Veröffentlichung in den PowerShell-Katalog verwenden würden.

Verwenden Sie für jede dieser Lösungen Register-PSRepository, um ein neues „Repository“ zu definieren, das Sie im Modul „Repositoryeigenschaft zum Veröffentlichen“ verwenden.

Ein weiterer Punkt zum Testen von Veröffentlichungen: Ein Paket, das Sie im PowerShell-Katalog veröffentlichen, kann nicht ohne die Hilfe des Betriebsteams wieder gelöscht werden, da von diesem bestätigt werden muss, dass kein anderes Element von dem Paket abhängig ist, das Sie veröffentlichen möchten.
Aus diesem Grund unterstützen wir den PowerShell-Katalog nicht als Testziel und werden jeden Herausgeber kontaktieren, der dies tut.

## <a name="use-powershellget-to-publish"></a>Verwenden von PowerShell für die Veröffentlichung

Es wird dringend empfohlen, dass Verleger die Cmdlets „Publish-Module“ und „Publish-Script“ verwenden, wenn Sie mit dem PowerShell-Katalog arbeiten.
PowerShellGet wurde entwickelt, damit Sie sich nicht alle wichtigen Informationen zur Installation aus dem und Veröffentlichung im PowerShell-Katalog merken müssen.
Gelegentlich überspringen Verleger PowerShellGet und verwenden den NuGet-Client oder auch PackageManagement-Cmdlets anstelle des Publish-Module-Cmdlets.
Es gibt viele Informationen, die leicht übersehen werden, wodurch eine Vielzahl von Supportanfragen aufkommt.

Wenn es einen Grund gibt, warum Sie Publish-Module oder Publish-Script nicht verwenden können, teilen Sie uns dies mit.
Stellen Sie ein Ticket im GitHub-Repository für PowerShellGet aus, und nennen Sie uns die Details, warum Sie sich für NuGet oder PackageManagement entschieden haben.

## <a name="recommended-workflow"></a>Empfohlener Workflow

Als erfolgreichster Ansatz für das Veröffentlichen von Paketen im PowerShell-Katalog hat sich der folgende bewährt:

- Führen Sie die anfängliche Entwicklung auf einer Open Source-Projektwebsite durch. Das PowerShell-Team verwendet GitHub.
- Nutzen Sie das Feedback von Benutzern und Testern sowie [Powershell Script Analyzer](https://aka.ms/psscriptanalyzer), um den Code in einen stabilen Zustand zu überführen.
- Schließen Sie eine Dokumentation ein, damit andere Benutzer wissen, wie Ihr Code verwendet wird.
- Testen Sie die Veröffentlichung, indem Sie ein lokales Repository verwenden.
- Veröffentlichen Sie eine stabile oder Alphaversion im PowerShell-Katalog. Schließen Sie in diese Version die Dokumentation und einen Link zu Ihrer Projektwebsite ein.
- Sammeln Sie Feedback, und durchlaufen Sie Ihren Code auf der Projektwebsite. Veröffentlichen Sie anschließend stabile Updates im PowerShell-Katalog.
- Fügen Sie Ihrem Projekt und Ihrem Modul Beispiele und Pester-Tests hinzu.
- Entscheiden Sie, ob Sie Ihrem Paket eine Codesignatur hinzufügen möchten.
- Wenn Sie der Meinung sind, dass das Projekt bereit zur Verwendung in einer Produktionsumgebung ist, veröffentlichen Sie eine Version 1.0.0 im PowerShell-Katalog.
- Sammeln Sie weiterhin Feedback, und durchlaufen Sie Ihren Code basierend auf Hinweisen und Kommentaren von Benutzern.
