---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, Cmdlet, Katalog
ms.date: 2016-10-14
contributor: manikb
title: "Häufig gestellte Fragen | MSDN"
ms.technology: powershell
ms.openlocfilehash: c352fe48c5833e9bbb2c86e6b23037a4a8f84596
ms.sourcegitcommit: 6d27d6db5ab0e2d5b6c7229e2e2d2e57915ea22d
translationtype: HT
---
# <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

## <a name="what-is-a-powershell-module"></a>Was ist ein PowerShell-Modul?

Ein PowerShell-Modul ist ein wiederverwendbares Paket, das einige PowerShell-Funktionen enthält. In PowerShell kann alles (Funktionen, Variablen, DSC-Ressourcen usw.) in Module verpackt werden. Üblicherweise sind Module Ordner, die bestimmte Dateitypen in einem bestimmten Pfad enthalten. Es gibt verschiedene Typen von PowerShell-Modulen.

## <a name="what-is-a-powershell-script"></a>Was ist ein PowerShell-Skript?

Ein PowerShell-Skript ist eine Reihe von Befehlen, die in einer PS1-Datei gespeichert sind, um die Wiederverwendung und Freigabe zu ermöglichen. PowerShell-Workflows sind auch PowerShell-Skripts, die eine Reihe von Aufgaben zeigen und Sequenzierungen für diese Aufgaben bereitstellen. Weitere Informationen finden Sie unter [Einführung in Windows PowerShell Workflow](https://technet.microsoft.com/en-us/library/jj134242.aspx).

## <a name="how-are-powershell-scripts-different-from-powershell-modules"></a>Worin unterscheiden sich PowerShell-Skripts von PowerShell-Modulen?

In der Regel sind Module besser für das Teilen, aber wir ermöglichen die Skriptfreigabe, damit Sie Workflows und Skripts leichter zur Community beitragen können. Weitere Informationen finden Sie auf den folgenden Blogs:

- [Don't Write Scripts, Write PowerShell Modules](https://blogs.technet.microsoft.com/heyscriptingguy/2011/06/27/dont-write-scripts-write-powershell-modules/)
- [Understanding PowerShell Modules](https://blogs.technet.microsoft.com/heyscriptingguy/2015/07/10/understanding-powershell-modules/)

## <a name="how-can-i-publish-to-the-powershell-gallery"></a>Wie kann ich etwas im PowerShell-Katalog veröffentlichen?

Sie müssen zuerst ein Konto im PowerShell-Katalog erstellen, bevor Sie Elemente im Katalog veröffentlichen können. Das liegt daran, dass das Veröffentlichen von Elementen einen NuGet API-Schlüssel erfordert, der bei der Registrierung bereitgestellt wird. Verwenden Sie zum Registrieren und Anmelden im PowerShell-Katalog Ihr persönliches, Geschäfts- oder Schulkonto. Ein einmaliger Registrierungsprozess ist erforderlich, wenn Sie sich zum ersten Mal anmelden. Danach ist der NuGet API-Schlüssel auf Ihrer Profilseite verfügbar.

Verwenden Sie, sobald Sie sich beim Katalog registriert haben, die Cmdlets [Publish-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) oder [Publish-Script](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), um Ihr Angebot im Katalog zu veröffentlichen. Weitere Informationen zum Ausführen dieser Cmdlets finden Sie auf der Registerkarte „Veröffentlichen“, oder lesen Sie die Dokumentation zu [Publish-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) und [Publish-Script](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

**Sie müssen sich zum Installieren oder Speichern der Elemente nicht im Katalog registrieren oder anmelden.**

## <a name="i-received-failed-to-process-request-the-specified-api-key-is-invalid-or-does-not-have-permission-to-access-the-specified-package-the-remote-server-returned-an-error-403-forbidden-error-when-i-tried-to-publish-an-item-to-the-powershell-gallery-what-does-that-mean"></a>Ich habe die Fehlermeldung „Fehler beim Verarbeiten der Anforderung. 'Der angegebene API-Schlüssel ist ungültig oder verfügt nicht über die Zugriffsberechtigung auf das angegebene Paket.' Der Remoteserver hat einen Fehler zurückgegeben: (403) Forbidden.“ erhalten, als ich ein Element im PowerShell-Katalog veröffentlichen wollte. Was bedeutet das?

Dieser Fehler kann aus folgenden Gründen auftreten:

- **Der angegebene API-Schlüssel ist ungültig.**
     Stellen Sie sicher, dass Sie den gültigen API-Schlüssel Ihres Konto angegeben haben. Den API-Schlüssel finden Sie auf Ihrer Profilseite.
- **Der angegebene Elementname gehört Ihnen nicht.**
     Wenn Sie sich vergewissert haben, dass Ihr API-Schlüssel richtig ist, existiert möglicherweise bereits ein Element mit demselben Namen wie der, den Sie verwenden möchten. Die Auflistung für das Element wurde möglicherweise durch den Besitzer aufgehoben. In diesem Fall wird es in keinen Suchergebnissen angezeigt. Öffnen Sie einen Browser, und navigieren Sie zur Seite „Elementdetails“, um festzustellen, ob bereits ein Element mit dem gleichen Namen vorhanden ist: `https://www.powershellgallery.com/packages/<itemName>`. Navigieren Sie z.B. direkt zu `https://www.powershellgallery.com/packages/pester`, gelangen Sie zur Detailseite des Pester-Moduls, unabhängig davon, ob es aufgeführt ist oder nicht. Wenn bereits ein Element mit einem einen Konflikt verursachenden Namen vorhanden ist und nicht aufgelistet ist, können Sie Folgendes tun:
    - Einen anderen Namen für das Element auswählen
    - Die Besitzer des vorhandenen Elements kontaktieren

## <a name="why-cant-i-sign-in-with-my-personal-account-but-i-could-sign-in-yesterday"></a>Warum konnte ich mich gestern mit meinem persönlichen Konto anmelden, heute aber nicht mehr?

Bitte bedenken Sie, dass Ihr Katalog-Konto keine Änderungen an Ihrem primären E-Mail-Alias übernimmt. Weitere Informationen finden Sie im Microsoft [Verwalten von Aliasen für Ihr Microsoft-Konto](https://windows.microsoft.com/en-us/windows/outlook/add-alias-account).

## <a name="why-dont-i-see-all-the-gallery-items-when-i-select-all-the-category-checkboxes-on-the-items-tab"></a>Warum werden mir nicht alle Katalogelemente angezeigt, wenn ich auf der Registerkarte „Elemente“ alle „Category“-Kontrollkästchen aktiviere?

Wenn Sie ein „Kategorie“-Kontrollkästchen aktivieren, geben Sie damit an, dass Sie alle Elemente in dieser Kategorie anzeigen möchten. Nur die Elemente in den ausgewählten Kategorien werden angezeigt. Wenn Sie alle „Kategorie“-Kontrollkästchen aktivieren, geben Sie damit entsprechend an, dass Sie alle Elemente in jeder beliebigen Kategorie anzeigen möchten. Allerdings gehören einige der Elemente im Katalog nicht zu den aufgeführten Kategorien, weshalb sie nicht in den Ergebnissen angezeigt werden. Deaktivieren Sie zum Anzeigen aller Elemente im Katalog alle „Kategorien“, oder wählen Sie die Registerkarte „Elemente“ erneut aus.

## <a name="what-are-the-requirements-to-publish-a-module-to-the-powershell-gallery"></a>Welche sind die Voraussetzungen, um ein Modul im PowerShell-Katalog veröffentlichen zu können?

Jede Art von PowerShell-Modul (Skriptmodule, binäre Module oder Manifestmodule) können im Katalog veröffentlicht werden. PowerShellGet benötigt zum Veröffentlichen einige Informationen über das Modul, wie z.B. Version, Beschreibung, Autor und Lizenzierung. Diese Informationen werden im Rahmen des Veröffentlichungsprozesses in der *Modulmanifest*-Datei (psd1) oder aus dem Wert des **LicenseUri** Parameter des Cmdlets [**Publish-Module**](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). Alle im Katalog veröffentlichten Module müssen über Modulmanifeste verfügen. Jedes Modul, das die folgenden Informationen in seinem Manifest enthält, kann im Katalog veröffentlicht werden:

- Version
- Beschreibung
- Autor
- Ein URI zu den Lizenzbedingungen des Moduls, entweder als Teil des **PrivateData**-Abschnitt des Manifests oder im **LicenseUri**-Parameter des Cmdlets [**Publish-Module**](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

## <a name="how-do-i-create-a-correctly-formatted-module-manifest"></a>Wie erstelle ich ein korrekt formatiertes Modulmanifest?

Die einfachste Möglichkeit, ein Modulmanifest zu erstellen, ist die Ausführung des Cmdlets [**New-ModuleManifest**](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). In PowerShell 5.0 oder höher, generiert New-ModuleManifest eine korrekt formatiertes Modulmanifest mit leeren Feldern für nützliche Metadaten wie **ProjectUri**, **LicenseUri** und **Tags**. Tragen Sie einfach etwas in die leeren Felder ein, oder verwenden Sie das generierte Manifest als Beispiel für die richtige Formatierung.

Verwenden Sie das Cmdlet [**Test-ModuleManifest**](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), um zu überprüfen, ob alle erforderlichen Metadatenfelder ordnungsgemäß ausgefüllt wurden.

Verwenden Sie das Cmdlet [**Update-ModuleManifest**](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), um die Felder der Modulmanifestdatei zu aktualisieren.

## <a name="what-are-the-requirements-to-publish-a-script-to-the-gallery"></a>Welche Voraussetzungen müssen erfüllt sein, damit ich ein Modul im Katalog veröffentlichen kann?

Jede Art von PowerShell-Skript (Skripts oder Workflows) kann im Katalog veröffentlicht werden. PowerShellGet benötigt zum Veröffentlichen einige Informationen über das Skript, wie z.B. Version, Beschreibung, Autor und Lizenzierung. Diese Informationen werden im Rahmen des Veröffentlichungsprozesses aus dem Abschnitt *PSScriptInfo* der Skriptdatei oder aus dem Wert des **LicenseUri**-Parameters des Cmdlets [**Publish-Script**](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) gelesen. Alle im Katalog veröffentlichten Skripts müssen Metadateninformationen besitzen. Jedes Skript, das die folgenden Informationen im Abschnitt „PSScriptInfo“ enthält, kann im Katalog veröffentlicht werden:

- Version
- Beschreibung
- Autor
- Ein URI zu den Lizenzbedingungen des Skripts, entweder als Teil des Abschnitts **PSScriptInfo** des Skripts oder im **LicenseUri**-Parameter des Cmdlets [**Publish-Script**](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

## <a name="how-do-i-search"></a>Wie führe ich eine Suche aus?

Geben Sie das gesuchte Thema in das Textfeld ein. Wenn Sie z.B. Module im Zusammenhang mit Azure SQL suchen, geben Sie einfach „Azure SQL“ ein. Die Suchmaschine sucht dann in allen veröffentlichten Elementen nach diesen Schlüsselwörtern, einschließlich Titel, Beschreibungen und metadatenübergreifend. Anschließend werden auf Grundlage einer gewichteten Qualitätsbewertung die besten Ergebnisse angezeigt. Sie können auch nach bestimmten Feldern der folgenden Feldtypen suchen, indem Sie die Syntax „Feld:"Wert"“ in der Suchabfrage verwenden:

- Tags
- Funktionen
- Cmdlets
- DscResources
- PowerShellVersion

Wenn Sie beispielsweise nach „PowerShellVersion:"2.0"“ suchen, werden die Ergebnisse angezeigt, die (basierend auf dem Modul-/Skriptmanifest) mit PowerShell Version 2.0 kompatibel sind.

## <a name="how-do-i-create-a-correctly-formatted-script-file"></a>Wie erstelle ich eine korrekt formatierte Skriptdatei?

Am einfachste Weg, eine korrekt formatierte Skriptdatei zu erstellen, ist das Cmdlet [**New-ScriptFileInfo**](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) auszuführen. In PowerShell 5.0 generiert New-ScriptFileInfo eine korrekt formatierte Skriptdatei mit leeren Feldern für nützliche Metadaten wie **ProjectUri**, **LicenseUri** und **Tags**. Tragen Sie einfach etwas in die leeren Felder ein, oder verwenden Sie das generierte Skript als Beispiel für die richtige Formatierung.

Verwenden Sie das Cmdlet [**Test-ScriptFileInfo**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), um zu überprüfen, ob alle erforderlichen Metadatenfelder ordnungsgemäß ausgefüllt wurden.

Verwenden Sie das Cmdlet [**Update-ScriptFileInfo**](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), um die Metadatenfelder des Skripts zu aktualisieren.

## <a name="what-other-types-of-powershell-modules-exist"></a>Welche anderen Typen von PowerShell-Modulen gibt es?

Der Begriff „PowerShell-Modul“ bezieht sich auch auf die Dateien, die die eigentliche Funktionalität implementieren. Skriptmoduldateien (.psm1) enthalten PowerShell-Code. Binäre Moduldateien (.dll) enthalten kompilierten Code.

Sie können sich dies wie folgt vorstellen: Der Ordner, der das Modul kapselt, ist der Modulordner. Die Modulordner kann ein Modulmanifest (.psd1) enthalten, das den Inhalt des Ordners beschreibt. Die Dateien, die die eigentliche Arbeit ausführen, sind die Skriptmoduldateien (.psm1) und die binären Moduldateien (.dll). Die DSC-Ressourcen befinden sich in einem bestimmten Unterordner und werden als Skriptmoduldateien oder binäre Moduldateien implementiert.

Alle Module im Katalog enthalten Modulmanifeste, und die meisten dieser Module enthalten Skriptmoduldateien oder binäre Moduldateien. Der Begriff „Modul“ kann aufgrund dieser verschiedenen Bedeutungen verwirren. Alle Verwendungen des Worts „Modul“ auf dieser Seite beziehen sich auf den Modulordner mit diesen Dateien, es sei denn, es wird explizit eine andere Bedeutung angegeben.

## <a name="how-does-packagemanagement-relate-to-powershellget-high-level-answer"></a>Was hat PackageManagement mit PowerShellGet zu tun? (Allgemeine Antwort)

PackageManagement ist eine allgemeine Schnittstelle für die Arbeit mit einem beliebigen Paket-Manager. Unabhängig davon, ob Sie mit PowerShell-Modulen, MSIs, RubyGems, NuGet-Paketen oder Perl-Modulen arbeiten, sollten Sie PackageManagement-Befehle (Find-Package und Install-Package) verwenden können, um sie suchen und installieren zu können. PackageManagement regelt dies mithilfe eines eigenen Paketanbieters für jeden Paket-Manager, der an PackageManagement eingebunden ist. Anbieter verrichten die eigentliche Arbeit: Sie rufen Inhalte aus Repositorys ab und installieren die Inhalte lokal. Häufig umschließen Paketanbieter einfach die vorhandenen Paket-Manager-Tools für einen gegebenen Paket.

PowerShellGet ist der Paket-Manager für PowerShell-Elemente. Es gibt einen Anbieter von PSModule-Paketen, der die PowerShellGet-Funktionalität über PackageManagement verfügbar macht. Sie können daher entweder [Install-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) oder „Install-Package -Provider PSModule“ ausführen, um ein Modul aus dem PowerShell-Katalog zu installieren. Auf bestimmte PowerShellGet-Funktionen, einschließlich [Update-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) und [Publish-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), kann nicht über PackageManagement-Befehle zugegriffen werden.

Alles in allem bietet PowerShellGet eine erstklassige Schnittstelle zur Paketverwaltung für PowerShell-Inhalte. PackageManagement dient der Bereitstellung aller Schnittstellungen zur Paketverwaltung mithilfe einiger allgemeiner Tools. Wenn Ihnen diese Antwort nicht geholfen hat, finden Sie eine ausführlichere Hilfestellung am Ende dieses Texts im Abschnitt **Wie beziehen sich PackageManagement und PowerShellGet tatsächlich aufeinander?**.

Weitere Informationen finden Sie auf der Projektseite zu [PackageManagement](https://oneget.org/).

## <a name="how-does-nuget-relate-to-powershellget"></a>Was hat NuGet mit PowerShellGet zu tun?

Der PowerShell-Katalog ist eine geänderte Version des [NuGet-Katalogs](https://www.nuget.org/). PowerShellGet verwendet den NuGet-Anbieter, um mit NuGet-basierten Repositorys wie dem PowerShell-Katalog zu arbeiten.

Sie können PowerShellGet für jedes gültige NuGet-Repository oder jede gültige NuGet-Dateifreigabe verwenden. Hierzu müssen Sie das Repository einfach mithilfe des Cmdlets [**Register-PSRepository**](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) hinzufügen.

## <a name="does-that-mean-i-can-use-nugetexe-to-work-with-the-gallery"></a>Bedeutet dies, dass ich NuGet.exe verwenden kann, um mit dem Katalog zu arbeiten?

Ja.

## <a name="how-does-packagemanagement-actually-relate-to-powershellget-technical-details"></a>Wie beziehen sich PackageManagement und PowerShellGet tatsächlich aufeinander? (Technische Details)

PowerShellGet nutzt im Hintergrund stark die PackageManagement-Infrastruktur.

Auf der Ebene der PowerShell-Cmdlets ist [Install-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) ein einfacher Wrapper um Install-Package -Provider PSModule.

Auf der Ebene des PackageManagement-Paketanbieters ruft der PSModule-Paketanbieter andere PackageManagement-Paketanbieter auf. Wenn Sie beispielsweise mit NuGet-basierten Katalogen arbeiten(z.B. dem PowerShell-Katalog), verwendet der PSModule-Paketanbieter den NuGet-Paketanbieter, um mit dem Repository zu arbeiten.

![PowerShellGet-Architektur](Images/powershellgetArchitecture.png)

Abbildung 1: PowerShellGet-Architektur

## <a name="what-is-required-to-run-powershellget"></a>Was ist für die Ausführung von PowerShellGet erforderlich?

Im Allgemeinen wird empfohlen, die neueste Version des PowerShellGet-Moduls auszuwählen (beachten Sie, dass .NET Version 4.5 notwendig ist).

Für das **PowerShellGet**-Modul ist **PowerShell 3.0 oder neuer** erforderlich.

Aus diesem Grund erfordert **PowerShellGet** eines der folgenden Betriebssysteme:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

Für **PowerShellGet** ist außerdem .NET Framework 4.5 oder höher erforderlich. Von [hier](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx) können Sie .NET Framework 4.5 oder höher installieren.

## <a name="is-it-possible-to-reserve-names-for-items-that-will-be-published-in-future"></a>Ist es möglich, Namen für Elemente zu reservieren, die in Zukunft veröffentlicht werden?

Es ist nicht möglich, Elementnamen zu reservieren. Wenn Sie glauben, dass ein vorhandenes Element einen Namen trägt, der besser zu Ihrem Element passt, [wenden Sie sich an den Besitzer des Elements](psgallery_contacting_item_owners.md). Wenn Sie innerhalb einiger Wochen keine Antwort erhalten, können Sie den Support kontaktieren und das Team für den PowerShell-Katalog prüft die Angelegenheit.

## <a name="how-do-i-claim-ownership-for-items-"></a>Wie mache ich Besitzansprüche für Elemente geltend?

Details hierzu finden Sie unter [Verwalten von Elementbesitzern](Managing-Item-Owners.md).

## <a name="how-do-i-deal-with-an-item-owner-who-is-violating-my-item-license"></a>Wie gehe ich mit einem Elementbesitzer um, der meine Elementlizenz verletzt?

Wir möchten die Zusammenarbeit in der PowerShell-Community fördern, um mögliche Rechtsstreitigkeiten zu beheben, die zwischen dem Elementbesitzern auftreten können.  Wir haben einen [Prozess zur Beilegung von Streitigkeiten](psgallery_dispute_resolution.md) entworfen, und bitten Sie, diesen zu befolgen, bevor die Administratoren von PowerShellGallery.com eingeschaltet werden.
