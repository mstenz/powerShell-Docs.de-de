# <a name="item-manifest-values-that-impact-the-powershell-gallery-ui"></a>Elementmanifestwerte, die die Benutzeroberfläche des PowerShell-Katalogs betreffen

Dieses Thema enthält zusammenfassende Informationen darüber, wie Herausgeber das Manifest für ihre PowerShell-Katalogveröffentlichungen im Hinblick auf Features von PowerShellGet-Cmdlets und die Benutzeroberfläche des PowerShell-Katalogs ändern können. Der Inhalt des vorliegenden Artikels ist entsprechend der Darstellung der Änderungen organisiert – und zwar beginnend mit dem mittleren Abschnitt bis zum Navigationsbereich auf der linken Seite. Der Artikel enthält einen Detailabschnitt, in dem wichtige Tags sowie einige der häufiger verwendeten Tags erläutert werden. In zwei Themen werden Beispiele für Manifeste vorgestellt: 

* Informationen zu Modulen finden Sie unter [Update-ModuleManifest](https://docs.microsoft.com/powershell/gallery/psget/module/psget_update-modulemanifest).
* Informationen zu Skripts finden Sie unter [New-ScriptFileInfo](https://docs.microsoft.com/powershell/gallery/psget/script/psget_new-scriptfileinfo).

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>Vom Manifest gesteuerte Elemente der PowerShell-Katalogfeatures

Die folgende Tabelle enthält die Benutzeroberflächenelemente der PowerShell-Katalogelementseiten, die vom Herausgeber gesteuert werden.
Die einzelnen Elemente geben an, ob sie vom Modul- oder Skriptmanifest gesteuert werden können.

| Benutzeroberflächenelement | Beschreibung | Modul | Skript | 
| --- | --- | --- | --- |
| **Titel** | Dies ist der Name des Elements, das im Katalog veröffentlicht wird.  | Nein | Nein |
| **Version** | Die angezeigte Version besteht aus der Versionszeichenfolge in den Metadaten und falls angegeben eines Vorabrelease. Der erste Teil der Version in einem Modulmanifest ist ModuleVersion. Bei einem Skript lautet dieser „.VERSION“. Wenn die Versionszeichenfolge eines Vorabrelease angegeben wird, wird diese bei Modulen an ModuleVersion angefügt oder bei Skripts im Rahmen von „.VERSION“ angegeben. Für die Angabe von Vorabreleasezeichenfolgen steht entsprechende Dokumentation zu [Modulen](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/prereleasemodule) und [Skripts](https://docs.microsoft.com/en-us/powershell/gallery/psget/script/prereleasescript) zur Verfügung. | Ja | Ja |
| **Beschreibung** | Dieses Element wird im Modulmanifest durch „Description“ und in einer Skriptmanifestdatei durch „.DESCRIPTION“ angegeben. | Ja | Ja |
| **Erforderliche Zustimmung zur Lizenz** | Ein Modul kann erfordern, dass der Benutzer eine Lizenz akzeptieren muss, indem er das Modulmanifest mit RequireLicenseAcceptance = $true ändert, ein LicenseURI angibt und eine Datei namens „license.txt“ im Stammverzeichnis des Modulordners bereitstellt. Weitere Informationen finden Sie im Thema [Erforderliche Zustimmung zur Lizenz](https://docs.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_requires_license_acceptance). | Ja | Nein |
| **Anmerkungen zu dieser Version** | Bei Modulen werden diese Informationen aus dem Abschnitt „ReleaseNotes“ unter „PSData\PrivateData“ abgerufen. Bei Skriptmanifesten ist es das Element „.RELEASENOTES“. | Ja | Ja |
| **Besitzer** | Unter „Besitzer“ befindet sich die Liste der Benutzer im PowerShell-Katalog, die ein Element aktualisieren können. Die Liste der Besitzer ist nicht im Elementmanifest enthalten. Die zusätzliche Dokumentation enthält Informationen zur [Verwaltung von Elementbesitzern](https://docs.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners). | Nein | Nein |
| **Autor** | Dieses Element lautet im Modulmanifest „Author“ und in einem Skriptmanifest „.AUTHOR“. Das Feld „Autor“ wird häufig verwendet, um ein Unternehmen oder eine Organisation anzugeben, das einem Element zugeordnet ist. | Ja | Ja |
| **Copyright** | Dieses Element ist in einem Modulmanifest das Feld „Copyright“ und lautet in einem Skriptmanifest „.COPYRIGHT“. | Ja | Ja |
| **FileList** | Die Dateiliste wird aus dem Paket abgerufen, wenn sie im PowerShell-Katalog veröffentlicht wird. Sie kann nicht durch die Manifestinformationen gesteuert werden. Hinweis: Bei jedem Element im PowerShell-Katalog, das nach der Installation des Elements in einem System nicht vorhanden ist, wird eine zusätzliche NUSPEC-Datei aufgeführt. Dies ist das NuGet-Paketmanifest für das Element und kann ignoriert werden. | Nein | Nein |
| **Tags** | Bei Modulen befinden sich Tags unter „PSData\PrivateData“. Bei Skripts wird der Abschnitt als „.TAGS“ bezeichnet. Hinweis: Tags dürfen keine Leerzeichen enthalten, selbst wenn sie in Anführungszeichen gesetzt sind. Für Tags gelten zusätzliche Anforderungen und Bedeutungen, die weiter unten in diesem Thema im Abschnitt „Tagdetails“ erläutert werden. | Ja | Ja |
| **Cmdlets** | Dieses Element wird im Modulmanifest mithilfe von CmdletsToExport angegeben. Hinweis: Es wird empfohlen, anstelle des Platzhalterzeichens „*“ die Elemente explizit aufzulisten, da hierdurch der Vorgang zum Laden des Moduls für Benutzer verbessert wird. | Ja | Nein |
| **Funktionen** | Dieses Element wird im Modulmanifest mithilfe von FunctionsToExport angegeben. Hinweis: Es wird empfohlen, anstelle des Platzhalterzeichens „*“ die Elemente explizit aufzulisten, da hierdurch der Vorgang zum Laden des Moduls für Benutzer verbessert wird. | Ja | Nein |
| **DSC-Ressourcen** | Bei Modulen, die in PowerShell Version 5.0 und höher verwendet werden, wird dieses Element im Manifest mithilfe von DscResourcesToExport angegeben. Wenn das Modul in PowerShell 4 verwendet werden soll, sollte nicht DSCResourcesToExport verwendet werden, da keine Unterstützung für diesen Manifestschlüssel besteht. (DSC war vor PowerShell 4 nicht vorhanden.) | Ja | Nein |
| **Workflows** | Workflows werden als Skripts im PowerShell-Katalog veröffentlicht und im Code als Workflows identifiziert (ein Beispiel finden Sie unter [Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1)). Dieses Element wird nicht vom Manifest gesteuert. | Nein | Nein |
| **Rollenfunktionen** | Dieses Element wird aufgeführt, wenn das im PowerShell-Katalog veröffentlichte Modul eine oder mehrere Rollenfunktionsdateien (PSRC) enthält, die von JEA verwendet werden. Weitere Informationen zu [Rollenfunktionen](https://docs.microsoft.com/en-us/powershell/jea/role-capabilities) finden Sie in der JEA-Dokumentation. | Ja | Nein |
| **PowerShell-Editionen** | Dieses Element wird in einem Skript- oder Modulmanifest angegeben. Bei Modulen, die für die Verwendung von PowerShell 5.0 oder niedriger konzipiert sind, wird dieses Element mithilfe von Tags gesteuert. Bei Desktop wird das Tag „PSEdition_Desktop“ und bei Core das „Tag PSEdition_Core“ verwendet. Bei Modulen, die nur in PowerShell 5.1 oder höher verwendet werden, ist ein CompatiblePSEditions-Schlüssel im Hauptmanifest enthalten. Weitere Informationen zum PS-Editionsfeature finden Sie in der [PowerShellGet-Dokumentation](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/modulewithpseditionsupport). | Ja | Ja |
| **Abhängigkeiten** | Abhängigkeiten sind die Module im PowerShell-Katalog, die entweder im Modul als RequiredModules oder im Skriptmanifest als „#Requires – Module (Name)“ deklariert werden. | Ja | Ja |
| **PowerShell-Mindestversion** | Dieses Element kann in einem Modulmanifest als PowerShellVersion angegeben werden. | Ja | Nein |
| **Versionsverlauf** | Der Versionsverlauf stellt die Updates dar, die an einem Modul im PowerShell-Katalog vorgenommen wurden. Wenn eine Elementversion mit der Löschfunktion ausgeblendet wird, wird diese nur Elementbesitzern im Versionsverlauf angezeigt. | Nein | Nein |
| **Projektwebsite** | Die Projektwebsite wird bei Modulen im Abschnitt „Privatedata\PSData“ des Modulmanifests durch Angabe von ProjectURI bereitgestellt. Im Skriptmanifest wird dieses Element durch Angabe von „.PROJECTURI“ gesteuert. | Ja | Ja |
| **Lizenz** | Ein Lizenzlink wird bei Modulen im Abschnitt „Privatedata\PSData“ des Modulmanifests durch Angabe von LicenseURI bereitgestellt. Im Skriptmanifest wird dieses Element durch Angabe von „.LICENSEURI“ gesteuert. Hinweis: Es ist wichtig zu erwähnen, dass die Nutzungsbedingungen für den PowerShell-Katalog die Nutzungsbedingungen für das Element angeben, wenn eine Lizenz nicht anhand von LicenseURI oder innerhalb eines Moduls angegeben wird. Weitere Informationen finden Sie in den Nutzungsbedingungen. | Ja | Ja |

## <a name="editing-item-details"></a>Bearbeiten von Elementdetails

Auf der Seite zur Elementbearbeitung im PowerShell-Katalog können Herausgeber einige der für ein Element angezeigten Felder ändern. Dies gilt insbesondere für Folgende:

* Anrede
* Beschreibung
* Zusammenfassung
* Symbol-URL
* URL der Projektstartseite
* Autoren
* Copyright
* Tags
* Anmerkungen zu dieser Version
* Lizenz erforderlich

Von diesem Ansatz wird in der Regel abgeraten, ausgenommen die angezeigten Element müssen für eine ältere Version eines Moduls korrigiert werden. Benutzer, die das Modul abrufen, werden sehen, dass die Metadaten nicht mit den im PowerShell-Katalog angezeigten Metadaten übereinstimmen. Daher wird von der Verwendung des Elements abgeraten. Dies führt dazu, dass zur Bestätigung der Änderung häufig Anfragen an Elementbesitzer gesendet werden. Es wird dringend empfohlen, bei dieser Vorgehensweise stets eine neue Version des Elements mit den gleichen Änderungen zu veröffentlichen. 

## <a name="tag-details"></a>Tagdetails

Tags sind einfache Zeichenfolgen, mit denen Consumer Elemente suchen. Tags sind besonders nützlich, wenn sie über viele Elemente zu dem gleichen Thema hinweg einheitlich verwendet werden. Die Verwendung verschiedener Varianten des gleichen Worts (z.B. „Datenbank“ und „Datenbanken“ oder „Test“ und „Tests“) bietet in der Regel keinen großen Nutzen. Bei Tags handelt es sich um Zeichenfolgen aus einzelnen Wörtern, bei denen die Groß-/Kleinschreibung nicht berücksichtigt wird und die keine Leerzeichen enthalten dürfen. Ausdrücke, die möglicherweise von Benutzern gesucht werden, können zur Elementbeschreibung hinzugefügt werden. Sie werden in den Suchergebnissen aufgeführt. Verwenden Sie die Pascal-Schreibweise, Bindestriche, Unterstriche oder Punkte, wenn Sie die Lesbarkeit verbessern möchten. Erstellen Sie keine langen, komplizierten oder ungewöhnlichen Tags, da diese häufig falsch geschrieben werden. 

Einige Tags müssen gesondert erläutert werden, da sie im PowerShell-Katalog und in den PowerShellGet-Cmdlets unterschiedlich verarbeitet werden. Dies betrifft z.B. speziell „PSEdition_Desktop“ und „PSEdition_Core“, die oben beschrieben werden. 

Wie bereits erwähnt, bieten Tags den größten Nutzen, wenn sie speziell ausgedrückt und konsistent in zahlreichen Elementen verwendet werden. Um herauszufinden, welche Tags am besten geeignet sind, sollten Herausgeber im PowerShell-Katalog nach den von Ihnen in Betracht gezogenen Tags suchen. Im Idealfall sollten viele Elemente zurückgegeben werden, und die Elementbeschreibungen sollten der Verwendung des jeweiligen Schlüsselworts entsprechen. 

Als Referenz werden im Folgenden einige der am häufigsten verwendeten Tags seit dem 14.12.2017 aufgeführt. In einigen Fällen werden ähnliche, jedoch möglicherweise weniger geeignete Optionen neben dem Tag aufgeführt.
Es wird empfohlen, das bevorzugte Tag zu verwenden, da dies die Anzahl falscher Ergebnisse reduziert und zu besseren Suchergebnisse für Consumer führt. 


| **Bevorzugtes Tag** | **Alternativen und Hinweise** |
| --- | --- |
| **Azure** |  |
| **DSC** | DesiredStateConfiguration ist nicht das bevorzugte Tag, da es zu lang ist. |
| **ResourceManager** | ARM wird zur Beschreibung von Prozessorgruppen verwendet und sollte nicht im Zusammenhang mit dem Azure Resource Manager verwendet werden. | **DSCResourceKit** |  |
| **SQL** |  |
| **AWS** |  |
| **DSCResource** |  |
| **Automation** |  |
| **REST** |  |
| **ActiveDirectory** | AD wird gegenwärtig nicht als eigenständiges Wort verwendet.  |
| **SQLServer** |  |
| **DBA** |  |
| **Sicherheit** | „Defense“ ist nicht präzise genug. |
| **Database** | „Databases“ (Plural) ist nicht das bevorzugte Tag. |
| **DevOps** |  |
| **Windows** |  |
| **Build** |  |
| **Deployment** | „Deploy“ wird etwas seltener verwendet. |
| **Cloud** |  |
| **GIT** |  |
| **Test** | „Tests“ ist nicht das bevorzugte Tag. |
| **VersionControl** | „Version“ ist nicht präzise genug, obwohl es häufiger verwendet wird.  |
| **Logging** | Dies ist die bevorzugte Verwendung von Protokollierung als Aktion. |
| **Log** | Dies ist die bevorzugte Verwendung eines Protokolls als Objekt. |
| **Backup** |  |
| **IaaS** |  |
| **Linux** |  |
| **IIS** |  |
| **AzureAutomation** |  |
| **Storage** |  |
| **GitHub** |  |
| **Json** |  |
| **Exchange** |  |
| **Network** | „Networking“ weist Ähnlichkeiten auf, wird jedoch seltener verwendet. |
| **SharePoint** |  |
| **Reporting** | „Reporting“ bezieht sich auf eine Aktion, während „Report“ ein Objekt bezeichnet. |
| **Report** | „Report“ bezeichnet ein Objekt. |
| **WinRM** |  |
| **Monitoring** |  |
| **VSTS** |  |
| **Excel** |  |
| **Google** |  |
| **Color** |  |
| **DNS** |  |
| **Office365** | „Office“ sollte vorzugsweise ausgeschrieben werden. „O365“ ist zwar kürzer, wird jedoch seltener verwendet. | **Gitlab** |  |
| **Pester** |  |
| **AzureAD** |  |
| **HTML** |  |
| **Hyper-V** | „HyperV“ wird seltener als Tag verwendet. |
| **Configuration** |  |
| **ChatOps** |  |
| **PackageManagement** |  |
| **WMI** |  |
| **Firewall** |  |
| **Docker** |  |
| **Appveyor** |  |
| **AzureRm** | Dieses Element wird in erster Linie bei AzureRM-Modulen verwendet. |
| **Zip** |  |
| **MSI** |  |
| **Mac** |  |
| **PoshBot** |  |


