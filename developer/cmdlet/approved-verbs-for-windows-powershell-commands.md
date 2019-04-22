---
title: Genehmigte Verben für PowerShell-Befehle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/07/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- action names [PowerShell SDK]
- verb names [PowerShell SDK]
- cmdlets [PowerShell SDK], verb names
ms.assetid: 2d4e58a9-05bc-437c-86b9-d8d55cba7d48
caps.latest.revision: 36
ms.openlocfilehash: 4475b3f5e15826efbe8bab867011985cd7e2e1ae
ms.sourcegitcommit: 17ce42f97e13e8b3286779dc3f583474b0357023
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "59293349"
---
# <a name="approved-verbs-for-powershell-commands"></a>Genehmigten Verben für PowerShell-Befehle

PowerShell verwendet ein Verb-Substantiv-Paar, für den Namen von Cmdlets und ihrer abgeleiteten Klassen von Microsoft .NET Framework.
Z. B. die `Get-Command` Cmdlet von PowerShell wird verwendet, um alle Befehle abzurufen, die in PowerShell registriert sind.
Der Verb-Teil des Namens identifiziert, die Aktion, die das-Cmdlet führt.
Der Nomenteil des Namens identifiziert die Entität, auf der die Aktion ausgeführt wird.

> [!NOTE]
> PowerShell verwendet den Begriff *Verb* um ein Wort zu beschreiben, die eine Aktion impliziert, selbst wenn das Wort nicht um ein standard-Verb in der englischen Sprache ist.
> Beispielsweise den Begriff *neu* ein gültiger Namen der PowerShell-Verb ist, da es sich um eine Aktion impliziert, obwohl es sich nicht um ein Verb in der englischen Sprache ist.

## <a name="verb-naming-rules"></a>Verb-Benennungskonventionen

Die folgende Liste enthält Richtlinien, die bei der Auswahl des Verbs für einen Cmdlet-Namen:

* Wenn Sie das Verb angeben, es wird empfohlen, dass Sie eine der vordefinierten Verbnamen bereitgestellt werden, indem Sie PowerShell verwenden (Aliase für diese vordefinierten Verben in den folgenden Tabellen enthalten sind).
  Wenn Sie eine vordefinierte Verb verwenden, stellen Sie sicher Sie Konsistenz zwischen den Cmdlets, die Sie erstellen die Cmdlets, die von PowerShell bereitgestellt werden und die Cmdlets, die von anderen Benutzern entwickelt wurden.

* Verwenden Sie die vordefinierten Verben zum Bereich "Allgemeinen" der Aktion beschreiben, und verwenden Sie Parameter, um die Aktion des-Cmdlets zu optimieren.

* Um die Konsistenz über Cmdlets zu erzwingen, verwenden Sie kein Synonym für ein genehmigtes Verb.

* Verwenden Sie nur die Form jedes Verb, das in diesem Thema aufgeführt ist.
  Verwenden Sie z. B. "Get", aber verwenden Sie "Abrufen" oder "Ruft auf" nicht.

* Pascal-Schreibweise Groß-/Kleinschreibung für Verben.
  In Pascal-Schreibweise wird Groß-/Kleinschreibung die ersten Buchstaben jedes Worts, z. B. "ForEach" groß geschrieben.

* Verwenden Sie nicht die folgenden reservierten Verben oder Aliase.
  Diese Verben werden durch die PowerShell-Sprache oder durch spezielle Groß-/Kleinschreibung, von PowerShell bereitgestellten Cmdlets verwendet werden.
  - ForEach (Foreach)
  - Format (f)
  - Gruppe (Gp)
  - Sort (sr)
  - Tee (Te)
  - Wo (was)

## <a name="similar-verbs-for-different-actions"></a>Ähnlich wie Verben für verschiedene Aktionen

Die folgenden ähnlichen Verben stellen unterschiedliche Aktionen dar.

### <a name="new-vs-set"></a>Preisvergleich: neuabonnement Festlegen
Die `New` Verb wird verwendet, um eine neue Ressource erstellen.
Die `Set` Verb wird verwendet, um eine vorhandene Ressource optional Erstellen der Ressource, wenn er nicht, z. B. vorhanden ist Ändern der `Set-Variable` Cmdlet.

### <a name="find-vs-search"></a>Im Vergleich zu finden. Suchen
Die `Find` Verb wird verwendet, um für ein Objekt zu suchen.
Die `Search` Verb wird verwendet, um einen Verweis auf eine Ressource in einem Container zu erstellen.

### <a name="get-vs-read"></a>Visual Studio zu erhalten. Lesen
Die `Get` Verb verwendet, um eine Ressource, z. B. eine Datei abzurufen.
Die `Read` Verb zum Abrufen von Informationen aus einer Quelle, z. B. eine Datei verwendet wird.

### <a name="invoke-vs-start"></a>Rufen Sie Visual Studio. Start
Die `Invoke` Verb wird verwendet, um einen Vorgang auszuführen, die in der Regel ein synchroner Vorgang, z. B. das Ausführen eines Befehls ist.
Die `Start` Verb dient zum Starten eines Vorgangs, der einen asynchronen Vorgang, wie z. B. das Starten eines Prozesses in der Regel ist.

### <a name="ping-vs-test"></a>Ping im Vergleich zu Test
Verwenden der `Test` Verb.

## <a name="common-verbs"></a>Allgemeine Verben

PowerShell verwendet die [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) Enumerationsklasse allgemeine Aktionen zu definieren, die für nahezu alle Cmdlets anwenden können.
Die folgende Tabelle enthält die meisten der definierten Verben.

|Verb (Alias)|Aktion|Kommentare|
|--------------------|------------|--------------|
|[Hinzufügen](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|Fügt eine Ressource in einem Container oder fügt ein Element in ein anderes Element. Z. B. die `Add-Content` Cmdlet fügt den Inhalt in eine Datei. Dieses Verb ist gekoppelt mit `Remove`.|Für diese Aktion nicht verwenden Sie Verben wie z. B. Append, Anfügen und verketten oder einfügen.|
|[Klare](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (cl)|Entfernt alle Ressourcen aus einem Container, jedoch wird den Container nicht gelöscht. Z. B. die `Clear-Content` Cmdlet entfernt den Inhalt einer Datei, aber die Datei wird nicht gelöscht.|Verwenden Sie für diese Aktion nicht Verben wie leeren, löschen, Version, Markierung, löschen oder aufheben.|
|[Schließen](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (Cs)|Ändert den Zustand einer Ressource zu erleichtern kann nicht zugegriffen werden, nicht verfügbar oder kann nicht verwendet werden. Dieses Verb zugeordnet ist `Open.`||
|[Kopie](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (cp)|Kopiert eine Ressource an, um einen anderen Namen oder einen anderen Container. Z. B. die `Copy-Item` -Cmdlet, das verwendet wird, den Zugriff auf gespeicherte Daten kopiert ein Element von einem Speicherort im Datenspeicher in einen anderen.|Verwenden Sie für diese Aktion nicht die Verben wie doppelte, Klonen, Replikation oder synchronisieren.|
|[Geben Sie](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (Eastern Time)|Gibt eine Aktion, die dem Benutzer ermöglicht, die in einer Ressource zu verschieben. Z. B. die `Enter-PSSession` Cmdlet platziert der Benutzer in einer interaktiven Sitzung. Dieses Verb ist gekoppelt mit `Exit`.|Verwenden Sie für diese Aktion nicht Verben wie z. B. Pushbenachrichtigungen und in.|
|[Exit](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (Beispiel)|Legt die aktuelle Umgebung oder das Kontextmenü für den zuletzt verwendeten Kontext fest. Z. B. die `Exit-PSSession` Cmdlet platziert der Benutzer in der Sitzung, die verwendet wurde, um die interaktive Sitzung zu starten. Dieses Verb ist gekoppelt mit `Enter`.|Verwenden Sie für diese Aktion Verben wie Pop oder sich nicht.|
|[Suchen](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (fd)|Sucht nach der ein Objekt in einem Container, der unbekannt, impliziten, optional oder angegeben ist.||
|[Format](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)|Ordnet die Objekte in einer bestimmten Form oder das Layout.||
|[Erste](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|Gibt eine Aktion, die eine Ressource abruft. Dieses Verb ist gekoppelt mit `Set`.|Verwenden Sie für diese Aktion nicht Verben wie lesen, Open, Cat, Typ, Dir, abrufen, Dump, abrufen, überprüfen, suchen oder durchsuchen.|
|[Ausblenden](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|Stellt eine Ressource nicht erkennbare. Ein Cmdlet, dessen Name das Verb ausblenden enthält, möglicherweise einen Dienst z. B. von einem Benutzer verborgen werden. Dieses Verb ist gekoppelt mit `Show`.|Verwenden Sie für diese Aktion kein Verb, z.B. das blockieren.|
|[Join](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|Kombiniert Ressourcen in eine Ressource an. Z. B. die `Join-Path` Cmdlet kombiniert einen Pfad mit einem der untergeordneten Pfade um einen einzelnen Pfad zu erstellen. Dieses Verb ist gekoppelt mit `Split`.|Verwenden Sie für diese Aktion nicht Verben wie kombinieren, Unite, verbinden oder zuordnen.|
|[Sperre](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (lk)|Sichert eine Ressource an. Dieses Verb ist gekoppelt mit `Unlock`.|Verwenden Sie für diese Aktion nicht Verben wie einschränken oder Secure.|
|[Verschieben Sie](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|Verschiebt eine Ressource von einem Speicherort. Z. B. die `Move-Item` Cmdlet verschiebt ein Element von einem Speicherort im Datenspeicher an einen anderen Speicherort.|Verwenden Sie für diese Aktion nicht Verben wie übertragen, den Namen oder migrieren.|
|[Neue](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|Erstellt eine Ressource. (Die `Set` Verb kann auch verwendet werden, wenn eine Ressource zu erstellen, die Daten, wie beispielsweise enthält die `Set-Variable` Cmdlet.)|Verwenden Sie für diese Aktion nicht Verben wie erstellen, generieren, erstellen, stellen oder zuweisen.|
|[Open](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (Opening, Op)|Ändert den Zustand einer Ressource auf sie zugegriffen werden kann, verfügbar oder verwendbar zu machen. Dieses Verb ist gekoppelt mit `Close`.||
|[Optimieren der](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (Om)|Erhöht die Effektivität einer Ressource an.||
|[POP](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|Entfernt ein Element aus der oben im Stapel. Z. B. die `Pop-Location` Cmdlet ändert die aktuelle Position in der Speicherort, der die zuletzt auf dem Stapel abgelegt wurde.||
|[Mithilfe von Push übertragen](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (Pu)|Fügt ein Element am Anfang eines Stapels. Z. B. die `Push-Location` Cmdlet legt die aktuelle Position im Stapel.||
|[Wiederholen](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (neu)|Eine Ressource zurückgesetzt auf den Zustand, der nicht rückgängig gemacht wurde.||
|[Entfernen Sie](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (R)|Löscht eine Ressource aus einem Container an. Z. B. die `Remove-Variable` -Cmdlet Löscht eine Variable und ihren Wert. Dieses Verb ist gekoppelt mit `Add`.|Verwenden Sie für diese Aktion Verben, die solche wie löschen, Ausschneiden, Dispose, verwerfen, oder nicht löschen.|
|[Benennen Sie](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (Rn)|Ändert den Namen einer Ressource. Z. B. die `Rename-Item` -Cmdlet, das zum Zugriff auf gespeicherte Daten verwendet wird, ändert den Namen eines Elements im Datenspeicher.|Verwenden Sie für diese Aktion kein Verb, z. B. ändern.|
|[Zurücksetzen](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (Rs)|Legt eine Ressource wieder in den ursprünglichen Zustand fest.||
|[Suche](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (sr)|Erstellt einen Verweis auf eine Ressource in einem Container an.|Verwenden Sie für diese Aktion nicht Verben wie suchen, oder suchen.|
|[Wählen Sie](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (sc)|Sucht eine Ressource in einem Container an. Z. B. die `Select-String` Cmdlet sucht nach Text in Dateien und Zeichenfolgen.|Verwenden Sie für diese Aktion nicht Verben wie suchen, oder suchen.|
|[Legen Sie](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|Daten für eine vorhandene Ressource ersetzt, oder erstellt eine Ressource, die Daten enthält. Z. B. die `Set-Date` -Cmdlet ändert die Systemzeit auf dem lokalen Computer. (Die `New` Verb kann auch zum Erstellen einer Ressource verwendet werden.) Dieses Verb ist gekoppelt mit `Get`.|Verwenden Sie für diese Aktion nicht Verben wie schreiben "," Reset "," zuweisen "oder" konfigurieren.|
|[Anzeigen](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (sh)|Stellt eine Ressource für den Benutzer sichtbar. Dieses Verb ist gekoppelt mit `Hide`.|Verwenden Sie für diese Aktion nicht Verben wie z. B. anzeigen oder erstellen.|
|[Skip](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (sk)|Umgeht eine oder mehrere Ressourcen oder Punkte in einer Sequenz an.|Verwenden Sie für diese Aktion kein Verb, z. B. umgehen oder springen.|
|[Split](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (sl)|Trennt die Teile einer Ressource. Z. B. die `Split-Path` -Cmdlet gibt die verschiedene Teilen eines Pfads zurück. Dieses Verb ist gekoppelt mit `Join`.|Verwenden Sie für diese Aktion kein Verb diese separaten.|
|[Schritt](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (St)|Wechselt zum nächsten Punkt oder Ressource in einer Sequenz.||
|[Switch](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (sw)|Gibt eine Aktion, die zwischen zwei Ressourcen, z. B. wechselt, um zwischen zwei Standorten, Aufgaben oder Status zu ändern.||
|[Rückgängig:](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (un)|Legt eine Ressource auf den vorherigen Zustand fest.||
|[Nicht entsperren](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (uk)|Eine Ressource, die gesperrt wird, wurde freigegeben. Dieses Verb ist gekoppelt mit `Lock`.|Verwenden Sie für diese Aktion nicht Verben wie Version, Unrestrict oder unsicher.|
|[Sehen Sie sich](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (wc)|Fortlaufend überprüft, oder eine Ressource auf Änderungen überwacht.||

## <a name="communications-verbs"></a>Kommunikation-Verben

PowerShell verwendet die [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) Klasse, um Aktionen zu definieren, die für die Kommunikation gelten.
Die folgende Tabelle enthält die meisten der definierten Verben.

|Verb (Alias)|Aktion|Kommentare|
|--------------------|------------|--------------|
|[Herstellen einer mit](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (cc)|Erstellt eine Verknüpfung zwischen einer Quelle und Ziel. Dieses Verb ist gekoppelt mit `Disconnect`.|Verwenden Sie für diese Aktion nicht Verben wie z. B. Join oder Telnet.|
|[Trennen Sie](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (dc)|Hebt die Verknüpfung zwischen einer Quelle und Ziel. Dieses Verb ist gekoppelt mit `Connect`.|Verwenden Sie für diese Aktion nicht Verben wie Break oder abmelden.|
|[Lesen](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (rd)|Ruft Informationen aus einer Quelle ab. Dieses Verb ist gekoppelt mit `Write`.|Für diese Aktion Verben wie abrufen, Eingabeaufforderung verwenden, oder nicht abrufen.|
|[Empfangen von](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (rc)|Akzeptiert die Informationen, die von einer Quelle gesendet. Dieses Verb ist gekoppelt mit `Send`.|Für diese Aktion Verben, z. B. lesen, akzeptieren, verwenden oder nicht einsehen.|
|[Senden von](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (sd)|Bietet Informationen zu einem Ziel. Dieses Verb ist gekoppelt mit `Receive`.|Verwenden Sie für diese Aktion nicht Verben wie Put, Übertragung, E-Mail oder Fax.|
|[Schreiben von](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (Wr)|Fügt Informationen an ein Ziel an. Dieses Verb ist gekoppelt mit `Read`.|Verwenden Sie für diese Aktion nicht Verben wie Put oder drucken.|

## <a name="data-verbs"></a>Daten-Verben

PowerShell verwendet die [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData) Klasse, um Aktionen zu definieren, die für die Behandlung von Daten gelten.
Die folgende Tabelle enthält die meisten der definierten Verben.

|Verbnamen (Alias)|Aktion|Kommentare|
|-------------------------|------------|--------------|
|[Sicherung](/dotnet/api/System.Management.Automation.VerbsData.Backup) (BA);|Speichert Daten replizieren.|Verwenden Sie für diese Aktion nicht Verben wie z. B. speichern "," Burn, Replikation oder Sync.|
|[Checkpoint](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (ch)|Erstellt eine Momentaufnahme des aktuellen Zustands der Daten oder der Konfiguration.|Verwenden Sie für diese Aktion kein Verb, z. B. Diff.|
|[Vergleichen Sie](/dotnet/api/System.Management.Automation.VerbsData.Compare) (Cr)|Wertet die Daten aus einer Ressource für die Daten aus einer anderen Ressource an.|Verwenden Sie für diese Aktion kein Verb, z. B. Diff.|
|[Komprimieren](/dotnet/api/System.Management.Automation.VerbsData.Compress) (zertifikatsverwaltung)|Komprimiert die Daten einer Ressource an. -Paaren mit `Expand`.|Verwenden Sie für diese Aktion kein Verb wie z. B. Compact.|
|[Konvertieren von](/dotnet/api/System.Management.Automation.VerbsData.Convert) (KA)|Ändert die Daten aus einer Darstellung in ein anderes ein, wenn das Cmdlet bidirektionale Konvertierung unterstützt oder das Cmdlet die Konvertierung zwischen mehreren Datentypen unterstützt.|Verwenden Sie für diese Aktion Verben wie z. B. Ändern der Größe, ändern oder nicht erneut einlesen.|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (Cf)|Konvertiert einen primären Typ der Eingabe (das Cmdlet-Nomen gibt die Eingabe) in eine oder mehrere der unterstützten Ausgabetypen.|Verwenden Sie für diese Aktion nicht Verben wie Export, Ausgabe oder Out.|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (ct)|Konvertiert eine oder mehrere Arten von Eingaben für einen primären Ausgabetyp (das Cmdlet-Nomen gibt den Ausgabetyp an).|Für diese Aktion, verwenden Sie keine Verben wie importieren, Eingabe, oder im.|
|[Aufheben der Bereitstellung](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (dm)|Trennt eine benannte Entität von einem Speicherort an. Dieses Verb ist gekoppelt mit `Mount`.|Verwenden Sie für diese Aktion nicht Verben wie aufheben oder Verknüpfung aufheben.|
|[Bearbeiten Sie](/dotnet/api/System.Management.Automation.VerbsData.Edit) (Ed)|Ändert vorhandene Daten durch Hinzufügen oder Entfernen von Inhalt an.|Verwenden Sie für diese Aktion nicht Verben wie ändern, aktualisieren oder ändern.|
|[Erweitern Sie](/dotnet/api/System.Management.Automation.VerbsData.Expand) (En)|Stellt die Daten einer Ressource, die komprimiert wurden den ursprünglichen Zustand wieder her. Dieses Verb ist gekoppelt mit `Compress`.|Verwenden Sie für diese Aktion nicht die Verben wie z. B. Explode oder dekomprimieren.|
|[Exportieren Sie](/dotnet/api/System.Management.Automation.VerbsData.Export) (Ep)|Kapselt die primäre Eingabe in einem persistenten Datenspeicher, z. B. eine Datei oder in ein Austauschformat. Dieses Verb ist gekoppelt mit `Import`.|Verwenden Sie für diese Aktion nicht Verben wie extrahieren oder eine Sicherung.|
|[Gruppe](/dotnet/api/System.Management.Automation.VerbsData.Group) (Gp)|Ordnet oder ordnet eine oder mehrere Ressourcen.|Verwenden Sie für diese Aktion Verben wie Aggregat, Arrange, verknüpfen, oder nicht korrelieren.|
|[Import](/dotnet/api/System.Management.Automation.VerbsData.Import) (Ip)|Erstellt eine Ressource aus Daten, die in einem persistenten Datenspeicher (z. B. eine Datei) oder in einem Austauschformat gespeichert werden. Z. B. die `Import-CSV` Cmdlet importiert Daten aus einer durch Trennzeichen getrennten Werten (CSV)-Datei auf Objekte, die von anderen Cmdlets verwendet werden können. Dieses Verb ist gekoppelt mit `Export`.|Verwenden Sie für diese Aktion nicht Verben wie Bulkload- oder laden.|
|[Initialisieren Sie](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (in)|Bereitet eine Ressource für die Verwendung und wird zu einem Standardzustand.|Verwenden Sie für diese Aktion nicht Verben wie löschen, Init, Erneuerung, neu erstellen, initialisieren oder Setup.|
|[Limit](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|Wendet Einschränkungen auf eine Ressource an.|Verwenden Sie für diese Aktion kein Verb, z. B. Kontingent.|
|[Merge](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|Erstellt eine einzelne Ressource aus mehreren Ressourcen.|Verwenden Sie für diese Aktion nicht Verben wie kombinieren oder Join.|
|[Einbinden](/dotnet/api/System.Management.Automation.VerbsData.Mount) (Mt)|Fügt eine benannte Entität an einen Speicherort an. Dieses Verb ist gekoppelt mit `Dismount`.|Verwenden Sie für diese Aktion nicht das Verb verbinden.|
|[Out](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|Sendet Daten aus der Umgebung. Z. B. die `Out-Printer` Cmdlet sendet Daten an einen Drucker.||
|[Veröffentlichen von](/dotnet/api/System.Management.Automation.VerbsData.Publish) (pb)|Stellt eine Ressource für andere Personen verfügbar. Dieses Verb ist gekoppelt mit `Unpublish`.|Verwenden Sie für diese Aktion Verben wie bereitstellen, wird oder nicht installieren.|
|[Wiederherstellen](/dotnet/api/System.Management.Automation.VerbsData.Restore) (rr)|Versetzt Sie in den vordefinierten Status, z. B. festlegen, indem eine Ressource `Checkpoint`. Z. B. die `Restore-Computer` Cmdlet startet eine Systemwiederherstellung auf dem lokalen Computer.|Verwenden Sie für diese Aktion nicht Verben wie reparieren, Return, Rückgängigmachen oder beheben.|
|[Speichern Sie](/dotnet/api/System.Management.Automation.VerbsData.Save) (Sv)|Behält Daten, um Datenverlust zu vermeiden.||
|[Synchronisierung](/dotnet/api/System.Management.Automation.VerbsData.Sync) (Sy)|Stellt sicher, dass zwei oder mehr Ressourcen in den gleichen Zustand befinden.|Verwenden Sie für diese Aktion Verben wie Replikation, zum umwandeln, oder nicht übereinstimmen.|
|[Aufheben der Veröffentlichung](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (Ub)|Stellt eine Ressource für andere Benutzer nicht verfügbar sind. Dieses Verb ist gekoppelt mit `Publish`.|Verwenden Sie für diese Aktion Verben wie deinstallieren, wiederherstellen, oder ausblenden.|
|[Update](/dotnet/api/System.Management.Automation.VerbsData.Update) (Ud)|Stellt eine Ressource, die auf dem neuesten Stand, um dessen Status, Genauigkeit, Konformität oder Compliance zu verwalten. Z. B. die `Update-FormatData` Cmdlet aktualisiert und die aktuelle PowerShell-Konsole Formatierungsdateien hinzugefügt.|Für diese Aktion nicht verwenden Sie Verben wie die Neuberechnung der erneuern, aktualisieren oder neu zu indizieren.|

## <a name="diagnostic-verbs"></a>Diagnose-Verben

PowerShell verwendet die [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) Klasse, um Aktionen zu definieren, die für die Diagnose gelten.
Die folgende Tabelle enthält die meisten der definierten Verben.

|Verb (Alias)|Aktion|Kommentare|
|--------------------|------------|--------------|
|[Debuggen von](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (Db)|Überprüft eine Ressource, um operative Probleme zu diagnostizieren.|Verwenden Sie für diese Aktion kein Verb, z. B. diagnostizieren.|
|[Measure](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (ms)|Bezeichnet die Ressourcen, die durch einen angegebenen Vorgang verbraucht werden, oder ruft die Statistiken zu einer Ressource ab.|Verwenden Sie für diese Aktion nicht Verben wie berechnen, ermitteln und analysieren.|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (Pi)|Verwenden der `Test` Verb.||
|[Reparatur](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (Rp)|Stellt eine Ressource einen nutzbaren Zustand wieder her|Verwenden Sie für diese Aktion nicht Verben wie Fehlerbehebung oder Wiederherstellung.|
|[Beheben](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (rv)|Ordnet eine Kurzform-Darstellung einer Ressource in eine vollständige Darstellung.|Verwenden Sie für diese Aktion nicht die Verben wie Erweiterungs- oder stellen Sie fest.|
|[Test](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|Überprüft, ob der Vorgang oder Konsistenz einer Ressource.|Verwenden Sie für diese Aktion nicht die Verben wie Diagnose "," analysieren "," Restwert "oder" überprüfen.|
|[Ablaufverfolgung](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (tr)|Überwacht die Aktivitäten von einer Ressource an.|Für diese Aktion nicht verwenden Sie Verben wie z. B. nachverfolgen, gehen Sie folgendermaßen vor, überprüfen oder Produkt noch besser kennenzulernen.|

## <a name="lifecycle-verbs"></a>Lebenszyklus-Verben

PowerShell verwendet die [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) Klasse, um Aktionen zu definieren, die für den Lebenszyklus einer Ressource gelten.
Die folgende Tabelle enthält die meisten der definierten Verben.

|Verb (Alias)|Aktion|Kommentare|
|--------------------|------------|--------------|
|[Genehmigen Sie](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (ap)|Bestätigt oder stimmt der Status einer Ressource oder einen Prozess.||
|[Assert-](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (wie)|Bestätigen den Status einer Ressource an.|Verwenden Sie für diese Aktion kein Verb, z. B. Certify.|
|[Erstellen Sie](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (bd)|Erstellt ein Artefakt (in der Regel eine Binärdatei oder Dokumentschema) aus eine Gruppe von Eingabedateien (in der Regel von Quellcode oder deklarativen Dokumente)|Dieses Verb wurde in PowerShell IPv6 hinzugefügt.|
|[Vollständige](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (cp)|Ist einen Vorgang abgeschlossen.||
|[Vergewissern Sie sich](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (Cn)|Bestätigt, überprüft oder überprüft den Status einer Ressource oder einen Prozess.|Verwenden Sie für diese Aktion nicht Verben wie Acknowledge, ich stimme zu, Certify, überprüfen oder überprüfen.|
|[Verweigern](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (dn)|Weist, Objekte, blockiert oder wendet den Status einer Ressource oder einen Prozess.|Für diese Aktion nicht verwenden Sie Verben wie z. B. die Block-Objekt, ablehnen oder ablehnen.|
|[Bereitstellen von](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (dp)|Sendet eine Anwendung, eine Website oder eine Projektmappe mit einem Remoteziel [s] so, dass ein Consumer dieser Lösung darauf zugreifen kann, nachdem die Bereitstellung abgeschlossen ist|Dieses Verb wurde in PowerShell IPv6 hinzugefügt.|
|[Deaktivieren Sie](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|Konfiguriert eine Ressource, um einen nicht verfügbar oder inaktiven Status. Z. B. die `Disable-PSBreakpoint` -Cmdlet führt einen Haltepunkt inaktiv. Dieses Verb ist gekoppelt mit `Enable`.|Verwenden Sie für diese Aktion nicht Verben wie Halt ein- oder ausblenden.|
|[Aktivieren Sie](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|Konfiguriert eine Ressource auf einem verfügbaren oder "aktiv". Z. B. die `Enable-PSBreakpoint` Cmdlet aktiviert einen Haltepunkt. Dieses Verb ist gekoppelt mit `Disable`.|Verwenden Sie für diese Aktion nicht Verben wie z. B. starten oder Begin.|
|[Installieren Sie](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (ist)|Fügt eine Ressource an einem Speicherort, und optional initialisiert wird. Dieses Verb ist gekoppelt mit `Uninstall`.|Führen Sie für diese Aktion keine aus einer Verb wie z.B. das Setup aus.|
|[Rufen Sie](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|Führt eine Aktion, z. B. das Ausführen eines Befehls oder einer Methode.|Verwenden Sie für diese Aktion nicht Verben wie ausführen "oder" starten.|
|[Registrieren Sie](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (Rg)|Erstellt einen Eintrag für eine Ressource in einem Repository, z. B. eine Datenbank an. Dieses Verb ist gekoppelt mit `Unregister`.||
|[Anforderung](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (Rq)|Fordert eine Ressource oder die Berechtigungen anfordert.||
|[Starten Sie neu](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (rt)|Beendet einen Vorgang aus, und dann erneut gestartet. Z. B. die `Restart-Service` Cmdlet beendet und startet dann einen Dienst.|Verwenden Sie für diese Aktion kein Verb, z. B. Wiederverwendung.|
|[Fortsetzen](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (ru)|Startet einen Vorgang, der angehalten wurde. Z. B. die `Resume-Service` -Cmdlet wird einen Dienst, der angehalten wurde gestartet. Dieses Verb ist gekoppelt mit `Suspend`.||
|[Starten Sie](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (sa)|Initiiert einen Vorgang. Z. B. die `Start-Service` Cmdlet startet einen Dienst. Dieses Verb ist gekoppelt mit `Stop`.|Verwenden Sie für diese Aktion nicht Verben wie z. B. starten, initiieren oder Start.|
|[Beenden Sie](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (sp)|Beendet eine Aktivität an. Dieses Verb ist gekoppelt mit `Start`.|Für diese Aktion nicht verwenden Sie Verben wie End Kill, beenden oder Abbrechen.|
|[Übermitteln von](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (Sb)|Stellt eine Ressource zur Genehmigung an.|Verwenden Sie für diese Aktion keinem Verb, z. B. Post.|
|[Anhalten](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (ss)|Hält eine Aktivität an. Z. B. die `Suspend-Service` Cmdlet hält einen Dienst. Dieses Verb ist gekoppelt mit `Resume`.|Verwenden Sie für diese Aktion kein Verb, z. B. anhalten.|
|[Deinstallieren Sie](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (USA)|Entfernt eine Ressource von einem angegebenen Speicherort. Dieses Verb ist gekoppelt mit `Install`.||
|[Aufheben der Registrierung](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (Ihre)|Entfernt den Eintrag für eine Ressource aus einem Repository. Dieses Verb ist gekoppelt mit `Register`.|Verwenden Sie für diese Aktion kein Verb, z. B. entfernen.|
|[Warten Sie](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|Hält einen Vorgang, bis ein bestimmtes Ereignis auftritt. Z. B. die `Wait-Job` Cmdlet Vorgänge angehalten, bis eine oder mehrere der Hintergrundaufträge abgeschlossen sind.|Verwenden Sie für diese Aktion nicht Verben wie Standby- oder anhalten.|

## <a name="security-verbs"></a>Security-Verben

PowerShell verwendet die [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) Klasse, um Aktionen zu definieren, die auf die Sicherheit anzuwenden.
Die folgende Tabelle enthält die meisten der definierten Verben.

|Verb (Alias)|Aktion|Kommentare|
|--------------------|------------|--------------|
|[Block](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (Bl)|Schränkt den Zugriff auf eine Ressource an. Dieses Verb ist gekoppelt mit `Unblock`.|Verwenden Sie für diese Aktion nicht die Verben wie z. B. verhindern, Grenzwert oder verweigern.|
|[GRANT](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (Gr)|Ermöglicht den Zugriff auf eine Ressource. Dieses Verb ist gekoppelt mit `Revoke`.|Verwenden Sie für diese Aktion nicht Verben wie zulassen "oder" aktivieren.|
|[Schützen von](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (pt)|Schützt eine Ressource vor Angriffen oder Verlust. Dieses Verb ist gekoppelt mit `Unprotect`.|Verwenden Sie für diese Aktion nicht Verben wie verschlüsseln, schützen oder versiegeln.|
|[Widerrufen](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (ZS)|Gibt eine Aktion, die Zugriff auf eine Ressource nicht möglich ist. Dieses Verb ist gekoppelt mit `Grant`.|Verwenden Sie für diese Aktion nicht Verben wie entfernen oder deaktivieren.|
|[Entsperren](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (Ul)|Einschränkungen auf eine Ressource wird entfernt. Dieses Verb ist gekoppelt mit `Block`.|Verwenden Sie für diese Aktion nicht Verben wie z. B. deaktivieren oder zulassen.|
|[Aufheben des Schutzes](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (bis)|Entfernt aus einer Ressource, die hinzugefügt wurden, um sie vor Angriffen oder Datenverluste zu verhindern, dass Sicherheitsmaßnahmen. Dieses Verb ist gekoppelt mit `Protect`.|Verwenden Sie für diese Aktion nicht Verben wie z. B. entschlüsseln oder Unseal.|

## <a name="other-verbs"></a>Andere Verben

PowerShell verwendet die [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) Klasse definieren kanonische Verbnamen, die nicht in ein bestimmtes Verb Kategoriename, z. B. die allgemeinen, die Kommunikation, die Daten, die Lebenszyklus passen oder Sicherheit Verbnamen Verben.

|Verb (Alias)|Aktion|Kommentare|
|--------------------|------------|--------------|
|[Verwendung](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|Enthält eine Ressource, um etwas zu tun, oder verwendet.||

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

[System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

[Cmdlet-Deklaration](./cmdlet-class-declaration.md)

[Windows PowerShell Handbuch für Programmierer](../prog-guide/windows-powershell-programmer-s-guide.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
