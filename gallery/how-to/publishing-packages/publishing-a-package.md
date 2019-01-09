---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Erstellen und Veröffentlichen eines Elements
ms.openlocfilehash: 70696535a3bf540ff75a2dc43bca80cb1adf8f45
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012533"
---
# <a name="creating-and-publishing-an-item"></a>Erstellen und Veröffentlichen eines Elements

Der PowerShell-Katalog ist der Ort, an dem stabile PowerShell-Module, -Skripts und DSC-Ressourcen veröffentlicht und mit der großen PowerShell-Benutzercommunity geteilt werden.

In diesem Artikel werden die Mechanismen und wichtigen Schritte zum Vorbereiten eines Skripts oder Moduls sowie deren Veröffentlichung im PowerShell-Katalog erläutert. Es wird dringend empfohlen, die [Veröffentlichungsrichtlinien](../../concepts/publishing-guidelines.md) zu lesen, um zu verstehen, wie Sie sicherstellen, dass veröffentlichte Elemente größere Akzeptanz durch die PowerShell-Katalogbenutzer erfahren.

Für das Veröffentlichen eines Elements im PowerShell-Katalog gelten diese Mindestvoraussetzungen:

- Sie benötigen ein PowerShell-Katalogkonto und den zugeordneten API-Schlüssel.
- Sie müssen gewährleisten, dass Ihr Element die erforderlichen Metadaten umfasst.
- Sie müssen mithilfe der Tools zur Vorabprüfung sicherstellen, dass Ihr Element bereit für die Veröffentlichung ist.
- Sie müssen das Element mithilfe der Befehle „Publish-Module“ und „Publish-Script“ im PowerShell-Katalog veröffentlichen.
- Antworten auf Fragen oder Bedenken zu Ihrem Element

Im PowerShell-Katalog können PowerShell-Module und PowerShell-Skripts veröffentlicht werden. Bei der Bezugnahme auf Skripts sind aus einer einzigen Datei bestehende PowerShell-Skripts gemeint – nicht hingegen Skripts, die Bestandteil eines größeren Moduls sind.

## <a name="powershell-gallery-account-and-api-key"></a>PowerShell-Katalogkonto und API-Schlüssel

Informationen zum Einrichten Ihres PowerShell-Katalogkontos finden Sie unter [Erstellen eines PowerShell-Katalogkontos](/powershell/gallery/how-to/publishing-packages/creating-an-account).

Nachdem Sie ein Konto erstellt haben, können Sie den benötigten API-Schlüssel zum Veröffentlichen eines Elements abrufen. Nachdem Sie sich mit dem Konto angemeldet haben, wird oben auf den PowerShell-Katalogseiten anstelle von „Register“ (Registrieren) Ihr Benutzername angezeigt. Durch Klicken auf Ihren Benutzernamen werden Sie zur Seite „My Account“ (Mein Konto) geleitet, auf der Sie den API-Schlüssel finden.

Hinweis: Der API-Schlüssel müssen so sicher wie Benutzernamen und Kennwort behandelt werden.
Mit diesem Schlüssel können Sie – oder jede andere Person – ein beliebiges Element im PowerShell-Katalog aktualisieren, dessen Besitzer Sie sind.
Es wird empfohlen, den Schlüssel regelmäßig zu aktualisieren. Die Aktualisierung kann über den Befehl „Reset Key“ (Schlüssel zurücksetzen) auf der Seite „My Account“ (Mein Konto) durchgeführt werden.

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>Erforderliche Metadaten für im PowerShell-Katalog veröffentlichte Elemente

Der PowerShell-Katalog stellt den Katalogbenutzern Informationen bereit, die aus Metadatenfeldern extrahiert werden, die im Skript oder Modulmanifest enthalten sind. Beim Erstellen oder Ändern von Elementen für die Veröffentlichung im PowerShell-Katalog gelten einige wenige Anforderungen für Informationen, die im Elementmanifest angegeben werden.
Es wird dringend empfohlen, den Abschnitt „Elementmetadaten“ in den [Veröffentlichungsrichtlinien](../../concepts/publishing-guidelines.md) zu lesen, um zu erfahren, wie Sie optimale Elementinformationen für die Benutzer bereitstellen.

Mit den Cmdlets [New-ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest) und [New-ScriptFileInfo](/powershell/module/PowerShellGet/New-ScriptFileInfo) wird die Manifestvorlage für Sie erstellt, mit Platzhaltern für alle Manifestelemente.

Beide Manifeste verfügen über zwei Abschnitte, die für die Veröffentlichung, die Primary Key-Daten und "psdata" Bereich "privatedata" am wichtigsten sind. Die Primärschlüsseldaten in einem PowerShell-modulmanifest ist alles außerhalb des PrivateData-Abschnitts. Der Satz an primären Schlüsseln ist an die verwendete PowerShell-Version gebunden, das Auslassen der Schlüsseldefinition wird nicht unterstützt. „PrivateData“ unterstützt das Hinzufügen neuer Schlüssel, deshalb befinden sich PowerShell-Katalog-spezifische Elemente in „PSData“.


Die wichtigsten Manifestelemente, die für im PowerShell-Katalog veröffentlichte Elemente ausgefüllt werden müssen, sind diese:

- Script or Module Name: Diese Informationen werden aus dem Namen der PS1-Datei für ein Skript oder der PSD1-Datei für ein Modul abgerufen.
- Version: Dies ist ein erforderlicher primärer Schlüssel, das Format sollte den SemVer-Richtlinien folgen. Details finden Sie bewährte Methoden.
- Autor: Dies ist ein erforderlicher primärer Schlüssel, und enthält den Namen des Elements zugeordnet werden soll.
Finden Sie unter Autoren und Besitzer unten.
- Description: Dies ist ein erforderlicher Schlüssel, mit dem kurz erläutert wird, wobei es sich bei dem Element handelt und welche Anforderungen für dessen Verwendung gelten.
- ProjectURI: Dies ist ein dringend empfohlenes URI-Feld in „PSData“, das einen Link zu einem GitHub-Repository oder einem ähnlichen Standort bereitstellt, an dem Sie das Element entwickeln.
- RFID-Transponder - ist es empfohlen, Ihr Paket basierend auf seine Kompatibilität mit PowerShell-Editionen und Plattformen zu kennzeichnen. Weitere Informationen finden Sie unter den [Veröffentlichungsrichtlinien](../../concepts/publishing-guidelines.md#tag-your-package-with-the-compatible-pseditions-and-platforms).

„Authors“ und „Owners“ in PowerShell-Katalogelementen sind verwandte Konzepte, stimmen aber nicht immer überein. Elementbesitzer (Owners) sind Benutzer mit PowerShell-Katalogkonten, die über die Berechtigung zum Verwalten des Elements verfügen. Es kann mehrere Besitzer geben, die ein beliebiges Element aktualisieren können. Die Owner-Daten sind nur im PowerShell-Katalog verfügbar und gehen verloren, wenn das Element von einem System in ein anderes kopiert wird. „Author“ ist eine Zeichenfolge, die in die Manifestdaten integriert ist, sodass sie immer Teil des Elements bleibt. Für Elemente von Microsoft-Produkten gelten diese Empfehlungen:

- Legen Sie mehrere Besitzer fest, von denen mindestens einer den Namen des Teams angibt, von dem das Element entwickelt wird.
- Geben Sie als „Author“ den Namen eines bekannten Teams (z.B. Azure SDK Team) oder Microsoft Corporation an.


## <a name="pre-validate-your-item"></a>Vorabüberprüfung Ihres Elements

Es gibt einige Tools, die Sie für Ihren Code ausführen müssen, bevor Sie Ihr Element im PowerShell-Katalog veröffentlichen:

- [PowerShell Script Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/), dieses Tool ist im PowerShell-Katalog enthalten.
- Für Module „Test-ModuleManifest“, das Bestandteil von PowerShell ist.
- Für Skripts „Test-ScriptFileInfo“, enthalten im PowerShell Get-Modul.

[PowerShell Script Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) ist ein Analysetool für statischen Code, mit dem überprüft wird, ob Ihr Code den grundlegenden Richtlinien für die PowerShell-Codierung entspricht. Dieses Tool identifiziert häufige und kritische Probleme in Ihrem Code und sollte während der Entwicklung regelmäßig ausgeführt werden, damit Sie wissen, wann Ihr Element bereit für die Veröffentlichung ist. PowerShell Script Analyzer liefert eine Liste der ermittelten Probleme kategorisiert nach Fehler, Warnung und Information. Sie müssen alle Fehler beseitigen, bevor Sie eine Veröffentlichung im PowerShell-Katalog durchführen können. Warnungen müssen überprüft und sollten behoben werden. PowerShell Script Analyzer wird bei jeder Veröffentlichung oder Aktualisierung eines Elements im PowerShell-Katalog ausgeführt. Das für den Katalogbetrieb verantwortliche Team kontaktiert die Elementbesitzer, um gefundene Fehler zu beheben.

Wenn die Manifestinformationen in Ihrem Element nicht von der PowerShell-Kataloginfrastruktur gelesen werden können, ist eine Veröffentlichung nicht möglich.
[Test-ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest) findet häufige Probleme, durch die das Modul nach der Installation unbrauchbar wäre. Dieses Tool muss für jedes Modul ausgeführt werden, bevor dieses im PowerShell-Katalog veröffentlicht wird.

In gleicher Weise überprüft [Test-ScriptFileInfo](/powershell/module/PowerShellGet/test-scriptfileinfo) die Metadaten in einem Skript und muss für jedes (separat von einem Modul veröffentlichte) Skript ausgeführt werden, bevor es im PowerShell-Katalog veröffentlicht wird.


## <a name="publishing-items"></a>Veröffentlichen von Elementen

Sie müssen [Publish-Script](/powershell/module/PowerShellGet/publish-script) oder [Publish-Module](/powershell/module/PowerShellGet/publish-module) verwenden, um Elemente im PowerShell-Katalog zu veröffentlichen. Für diese Befehle sind folgende Informationen erforderlich:

- Der Pfad zu dem Element, das Sie veröffentlichen. Verwenden Sie den für Ihr Modul benannten Ordner. Wenn Sie einen Ordner angeben, der mehrere Versionen desselben Moduls enthält, müssen Sie „RequiredVersion“ angeben.
- Einen NuGet-API-Schlüssel. Dies ist der API-Schlüssel, der auf der Seite „My Account“ (Mein Konto) im PowerShell-Katalog enthalten ist.

Die meisten der weiteren Optionen in der Befehlszeile sollten in den Manifestdaten für das Element enthalten sein, das Sie veröffentlichen. Deshalb sollte die Angabe im Befehl nicht erforderlich sein.

Um Fehler zu vermeiden, wird dringend empfohlen, die Befehle mit „-Whatif -Verbose“ zu testen, bevor Sie die Veröffentlichung durchführen. Hierdurch sparen Sie eine Menge Zeit, weil Sie bei jeder Veröffentlichung im PowerShell-Katalog die Versionsnummer im Manifestabschnitt des Elements aktualisieren müssen.

Beispiele für würde folgendermaßen lauten:

* `Publish-Module -Path ".\MyModule" -NugetAPIKey "GUID" -Whatif -Verbose`
* `Publish-Script -Path ".\MyScriptFile.PS1" -NugetAPIKey "GUID" -Whatif -Verbose`

Lesen Sie die Ausgabe sorgfältig, und wiederholen Sie den Befehl ohne „-Whatif“, wenn keine Fehler oder Warnungen angezeigt werden.

Alle im PowerShell-Katalog veröffentlichten Elemente werden auf Viren überprüft und mit PowerShell Script Analyzer analysiert. Alle Probleme, die bei dieser Überprüfung ermittelt werden, werden zur Lösung an den Herausgeber gesendet.

Nachdem Sie ein Element im PowerShell-Katalog veröffentlicht haben, müssen Sie das Feedback für Ihr Element verfolgen.

- Stellen Sie sicher, dass die E-Mail-Adresse überwacht wird, die dem für die Veröffentlichung verwendeten Konto zugeordnet ist. Benutzer und das operative Team für den PowerShell-Katalog senden Feedback über dieses Konto, Probleme aus PSSA oder Antivirenprüfungen eingeschlossen. Wenn das E-Mail-Konto ungültig ist oder schwerwiegende Probleme gemeldet und über einen längeren Zeitraum ungelöst bleiben, können Elemente als aufgegeben betrachtet und aus dem PowerShell-Katalog entfernt werden, wie in den [Nutzungsbedingungen](https://www.powershellgallery.com/policies/Terms) beschrieben.
- Es wird empfohlen, die Kommentare für jedes PowerShell-Katalogelement zu abonnieren, das Sie veröffentlichen. Auf diese Weise werden Sie immer dann benachrichtigt, wenn ein Kommentar zu Ihren Elementen im PowerShell-Katalog hinterlassen wird. Diese Vorgehensweise ist optional, da hierzu ein Konto bei LiveFyre erstellt werden muss.
