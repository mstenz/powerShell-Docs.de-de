---
title: Erstellen eines Windows PowerShell-Element Anbieters | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- item providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], item provider
ms.assetid: a5a304ce-fc99-4a5b-a779-de7d85e031fe
caps.latest.revision: 6
ms.openlocfilehash: a64e49894ce5195cc177e97a7049740389b09456
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870709"
---
# <a name="creating-a-windows-powershell-item-provider"></a>Erstellen eines Windows PowerShell-Elementanbieters

In diesem Thema wird beschrieben, wie Sie einen Windows PowerShell-Anbieter erstellen, der die Daten in einem Datenspeicher bearbeiten kann. In diesem Thema werden die Elemente der Daten im Speicher als "Elemente" des Datenspeicher bezeichnet. Folglich wird ein Anbieter, der die Daten im Speicher bearbeiten kann, als Windows PowerShell-Element Anbieter bezeichnet.

> [!NOTE]
> Sie können die C# Quelldatei (AccessDBSampleProvider03.cs) für diesen Anbieter mithilfe des Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3,0-Laufzeitkomponenten herunterladen. Anweisungen zum Herunterladen finden Sie unter [Installieren von Windows PowerShell und Herunterladen des Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> Die heruntergeladenen Quelldateien stehen im **\<PowerShell-Beispiele >** Verzeichnis zur Verfügung. Weitere Informationen zu anderen Windows PowerShell-Anbieter Implementierungen finden [Sie unter Entwerfen des Windows PowerShell-Anbieters](./designing-your-windows-powershell-provider.md).

Der in diesem Thema beschriebene Windows PowerShell-Element Anbieter ruft Datenelemente aus einer Access-Datenbank ab. In diesem Fall ist ein "Item" entweder eine Tabelle in der Access-Datenbank oder eine Zeile in einer Tabelle.

## <a name="defining-the-windows-powershell-item-provider-class"></a>Definieren der Windows PowerShell-Element Anbieter Klasse

Ein Windows PowerShell-Element Anbieter muss eine .NET-Klasse definieren, die von der [System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Basisklasse abgeleitet wird. Im folgenden finden Sie die Klassendefinition für den in diesem Abschnitt beschriebenen Element Anbieter.

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

Beachten Sie, dass das [System. Management. Automation. Provider. cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) -Attribut in dieser Klassendefinition zwei Parameter enthält. Der erste Parameter gibt einen benutzerfreundlichen Namen für den Anbieter an, der von Windows PowerShell verwendet wird. Der zweite Parameter gibt die Windows PowerShell-spezifischen Funktionen an, die der Anbieter während der Befehls Verarbeitung für die Windows PowerShell-Laufzeit verfügbar macht. Für diesen Anbieter gibt es keine zusätzlichen Windows PowerShell-spezifischen Funktionen.

## <a name="defining-base-functionality"></a>Definieren der Basisfunktionalität

Wie unter [Entwerfen des Windows PowerShell-Anbieters](./designing-your-windows-powershell-provider.md)beschrieben, wird die [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Klasse von mehreren anderen Klassen abgeleitet, die unterschiedliche Anbieter Funktionen bereitgestellt haben. Ein Windows PowerShell-Element Anbieter muss daher alle Funktionen definieren, die von diesen Klassen bereitgestellt werden.

Weitere Informationen zum Implementieren von Funktionen zum Hinzufügen von Sitzungs spezifischen Initialisierungs Informationen und zum Freigeben von Ressourcen, die vom Anbieter verwendet werden, finden Sie unter [Erstellen eines einfachen Windows PowerShell-Anbieters](./creating-a-basic-windows-powershell-provider.md).
Die meisten Anbieter, einschließlich des hier beschriebenen Anbieters, können jedoch die Standard Implementierung dieser Funktionalität verwenden, die von Windows PowerShell bereitgestellt wird.

Bevor der Windows PowerShell-Element Anbieter die Elemente im Speicher bearbeiten kann, muss er die Methoden der Basisklasse [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) implementieren, um auf den Datenspeicher zuzugreifen. Weitere Informationen zur Implementierung dieser Klasse finden Sie unter [Erstellen eines Windows PowerShell-Laufwerks Anbieters](./creating-a-windows-powershell-drive-provider.md).

## <a name="checking-for-path-validity"></a>Überprüfen der Pfad Gültigkeit

Bei der Suche nach einem Datenelement stellt die Windows PowerShell-Runtime einen Windows PowerShell-Pfad zum Anbieter zur Seite, wie im Abschnitt "pspath-Konzepte" der [Funktionsweise von Windows PowerShell](/previous-versions/ms714658(v=vs.85))definiert.
Ein Windows PowerShell-Element Anbieter muss die syntaktische und semantische Gültigkeit jedes von ihm übergebenen Pfades überprüfen, indem er die [System. Management. Automation. Provider. itemcmdletprovider. IsValidPath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) -Methode implementiert. Diese Methode gibt `true` zurück, wenn der Pfad gültig ist, und `false` andernfalls. Beachten Sie, dass die Implementierung dieser Methode nicht das vorhanden sein des Elements im Pfad überprüfen sollte, sondern nur, dass der Pfad syntaktisch und semantisch korrekt ist.

Hier ist die Implementierung der [System. Management. Automation. Provider. itemcmdletprovider. IsValidPath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) -Methode für diesen Anbieter. Beachten Sie, dass diese Implementierung eine normalizepath-Hilfsmethode aufruft, um alle Trennzeichen im Pfad in eine einheitliche zu konvertieren.

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>Ermitteln, ob ein Element vorhanden ist

Nachdem Sie den Pfad überprüft haben, muss die Windows PowerShell-Laufzeit bestimmen, ob ein Element der Daten an diesem Pfad vorhanden ist. Zur Unterstützung dieser Art von Abfrage implementiert der Windows PowerShell-Element Anbieter die [System. Management. Automation. Provider. itemcmdletprovider. itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) -Methode. Diese Methode gibt zurück, `true` ein Element im angegebenen Pfad gefunden wurde, und `false` (Standard) andernfalls.

Hier ist die Implementierung der [System. Management. Automation. Provider. itemcmdletprovider. itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) -Methode für diesen Anbieter. Beachten Sie, dass diese Methode die Hilfsmethoden pathisdrive, chunkpath und Getting aufruft und ein vom Anbieter definiertes databasetableinfo-Objekt verwendet.

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>Dinge, die Sie beim Implementieren von itemexists beachten sollten

Die folgenden Bedingungen können für Ihre Implementierung von [System. Management. Automation. Provider. itemcmdletprovider. itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)gelten:

- Beim Definieren der Anbieter Klasse kann ein Windows PowerShell-Element Anbieter die Anbieter Funktionen von expandwildcards, Filtern, einschließen oder Ausschließen von der [System. Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration deklarieren. In diesen Fällen muss die Implementierung der [System. Management. Automation. Provider. itemcmdletprovider. itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) -Methode sicherstellen, dass der Pfad, der an die-Methode übergeben wird, die Anforderungen der angegebenen Funktionen erfüllt. Zu diesem Zweck sollte die-Methode auf die entsprechende Eigenschaft zugreifen, z. b. die [System. Management. Automation. Provider. cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) -und [System. Management. Automation. Provider. cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) -Eigenschaften.

- Die Implementierung dieser Methode sollte jede Art von Zugriff auf das Element verarbeiten, das das Element für den Benutzer sichtbar machen kann. Wenn ein Benutzer beispielsweise über den File System-Anbieter Schreibzugriff auf eine Datei hat (von Windows PowerShell bereitgestellt), aber nicht über Lesezugriff verfügt, ist die Datei weiterhin vorhanden, und [System. Management. Automation. Provider. itemcmdletprovider. itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) gibt `true`zurück. Ihre Implementierung erfordert möglicherweise das Überprüfen eines übergeordneten Elements, um festzustellen, ob das untergeordnete Element aufgelistet werden kann.

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>Anfügen dynamischer Parameter an das Cmdlet "Test-Path"

Manchmal erfordert das `Test-Path`-Cmdlet, das [System. Management. Automation. Provider. itemcmdletprovider. itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) aufruft, zusätzliche Parameter, die zur Laufzeit dynamisch angegeben werden. Um diese dynamischen Parameter bereitzustellen, muss der Windows PowerShell-Element Anbieter die [System. Management. Automation. Provider. itemcmdletprovider. itemexistsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) -Methode implementieren. Diese Methode ruft die dynamischen Parameter für das Element im angezeigten Pfad ab und gibt ein Objekt zurück, das über Eigenschaften und Felder mit Attribut Attributen verfügt, die einer Cmdlet-Klasse oder einem [System. Management. Automation. runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -Objekt ähneln. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene-Objekt, um die Parameter dem `Test-Path`-Cmdlet hinzuzufügen.

Diese Methode wird von diesem Windows PowerShell-Element Anbieter nicht implementiert. Der folgende Code ist jedoch die Standard Implementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>Abrufen eines Elements

Zum Abrufen eines Elements muss der Windows PowerShell-Element Anbieter die [System. Management. Automation. Provider. itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) -Methode überschreiben, um Aufrufe aus dem `Get-Item`-Cmdlet zu unterstützen. Diese Methode schreibt das Element mithilfe der [System. Management. Automation. Provider. cmdletprovider. Write teitemabject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) -Methode.

Hier ist die Implementierung der [System. Management. Automation. Provider. itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) -Methode für diesen Anbieter. Beachten Sie, dass diese Methode die Hilfsmethoden geable und GetRow verwendet, um Elemente abzurufen, bei denen es sich entweder um Tabellen in der Access-Datenbank oder um Zeilen in einer Datentabelle handelt.

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>Dinge, die Sie beim Implementieren von GetItem beachten sollten

Die folgenden Bedingungen können auf eine Implementierung von [System. Management. Automation. Provider. itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)zutreffen:

- Beim Definieren der Anbieter Klasse kann ein Windows PowerShell-Element Anbieter die Anbieter Funktionen von expandwildcards, Filtern, einschließen oder Ausschließen von der [System. Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration deklarieren. In diesen Fällen muss die Implementierung von [System. Management. Automation. Provider. itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) sicherstellen, dass der an die Methode weiter gegebene Pfad diese Anforderungen erfüllt. Zu diesem Zweck sollte die-Methode auf die entsprechende Eigenschaft zugreifen, z. b. die [System. Management. Automation. Provider. cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) -und [System. Management. Automation. Provider. cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) -Eigenschaften.

- Standardmäßig sollten über schreibungen dieser Methode keine Objekte abrufen, die im Allgemeinen für den Benutzer ausgeblendet sind, es sei denn, die [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft ist auf `true`festgelegt. Beispielsweise überprüft die [System. Management. Automation. Provider. itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) -Methode für den File System-Anbieter die [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft, bevor versucht wird, [System. Management. Automation. Provider. cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>Anfügen dynamischer Parameter an das Cmdlet "Get-Item"

Manchmal erfordert das `Get-Item`-Cmdlet zusätzliche Parameter, die zur Laufzeit dynamisch angegeben werden. Um diese dynamischen Parameter bereitzustellen, muss der Windows PowerShell-Element Anbieter die [System. Management. Automation. Provider. itemcmdletprovider. getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) -Methode implementieren. Diese Methode ruft die dynamischen Parameter für das Element im angezeigten Pfad ab und gibt ein Objekt zurück, das über Eigenschaften und Felder mit Attribut Attributen verfügt, die einer Cmdlet-Klasse oder einem [System. Management. Automation. runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -Objekt ähneln. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene-Objekt, um die Parameter dem `Get-Item`-Cmdlet hinzuzufügen.

Diese Methode wird von diesem Anbieter nicht implementiert. Der folgende Code ist jedoch die Standard Implementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>Festlegen eines Elements

Um ein Element festzulegen, muss der Windows PowerShell-Element Anbieter die [System. Management. Automation. Provider. itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) -Methode überschreiben, um Aufrufe aus dem `Set-Item`-Cmdlet zu unterstützen. Diese Methode legt den Wert des Elements im angegebenen Pfad fest.

Dieser Anbieter stellt keine außer Kraft setzung für die [System. Management. Automation. Provider. itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) -Methode bereit. Im folgenden finden Sie jedoch die Standard Implementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>Dinge, die Sie bei der Implementierung von "" implementieren müssen

Die folgenden Bedingungen können für Ihre Implementierung von [System. Management. Automation. Provider. itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)gelten:

- Beim Definieren der Anbieter Klasse kann ein Windows PowerShell-Element Anbieter die Anbieter Funktionen von expandwildcards, Filtern, einschließen oder Ausschließen von der [System. Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration deklarieren. In diesen Fällen muss die Implementierung von [System. Management. Automation. Provider. itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) sicherstellen, dass der an die Methode weiter gegebene Pfad diese Anforderungen erfüllt. Zu diesem Zweck sollte die-Methode auf die entsprechende Eigenschaft zugreifen, z. b. die [System. Management. Automation. Provider. cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) -und [System. Management. Automation. Provider. cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) -Eigenschaften.

- Standardmäßig sollten über schreibungen dieser Methode keine Objekte festlegen oder schreiben, die für den Benutzer ausgeblendet sind, es sei denn, die [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft ist auf `true`festgelegt. An die [System. Management. Automation. Provider. cmdletprovider. Write-error](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) -Methode sollte ein Fehler gesendet werden, wenn der Pfad ein ausgeblendetes Element darstellt und [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) auf `false`festgelegt ist.

- Ihre Implementierung der [System. Management. Automation. Provider. itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) -Methode sollte [System. Management. Automation. Provider. cmdletprovider. dendprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) aufrufen und seinen Rückgabewert überprüfen, bevor Änderungen am Datenspeicher vorgenommen werden. Diese Methode wird verwendet, um die Ausführung eines Vorgangs zu bestätigen, wenn eine Änderung am Datenspeicher vorgenommen wird, z. b. das Löschen von Dateien. Die [System. Management. Automation. Provider. cmdletprovider. tiondprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) -Methode sendet den Namen der Ressource, die an den Benutzer geändert werden soll, wobei die Windows PowerShell-Laufzeit alle Befehlszeilen Einstellungen oder Einstellungs Variablen unternimmt, um zu bestimmen, was angezeigt werden soll.

  Nach dem Aufrufen von [System. Management. Automation. Provider. cmdletprovider. schuldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) wird `true`zurückgegeben. die [System. Management. Automation. Provider. itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) -Methode sollte die [System. Management. Automation. Provider. cmdletprovider. dendcontinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) -Methode aufrufen. Diese Methode sendet eine Meldung an den Benutzer, damit das Feedback überprüft werden kann, ob der Vorgang fortgesetzt werden soll. Der [System. Management. Automation. Provider. cmdletprovider. rudcontinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) -Befehl ermöglicht eine zusätzliche Überprüfung auf potenziell gefährliche System Änderungen.

## <a name="retrieving-dynamic-parameters-for-setitem"></a>Abrufen von dynamischen Parametern für "System Item"

Manchmal erfordert das `Set-Item`-Cmdlet zusätzliche Parameter, die zur Laufzeit dynamisch angegeben werden. Um diese dynamischen Parameter bereitzustellen, muss der Windows PowerShell-Element Anbieter die [System. Management. Automation. Provider. itemcmdletprovider. setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) -Methode implementieren. Diese Methode ruft die dynamischen Parameter für das Element im angezeigten Pfad ab und gibt ein Objekt zurück, das über Eigenschaften und Felder mit Attribut Attributen verfügt, die einer Cmdlet-Klasse oder einem [System. Management. Automation. runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -Objekt ähneln. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene-Objekt, um die Parameter dem `Set-Item`-Cmdlet hinzuzufügen.

Diese Methode wird von diesem Anbieter nicht implementiert. Der folgende Code ist jedoch die Standard Implementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>Löschen eines Elements

Zum Löschen eines Elements implementiert der Windows PowerShell-Element Anbieter die [System. Management. Automation. Provider. itemcmdletprovider. ClearItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) -Methode, um Aufrufe aus dem `Clear-Item`-Cmdlet zu unterstützen. Diese Methode löscht das Datenelement im angegebenen Pfad.

Diese Methode wird von diesem Anbieter nicht implementiert. Der folgende Code ist jedoch die Standard Implementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>Dinge, die Sie beim Implementieren von ClearItem beachten sollten

Die folgenden Bedingungen können auf eine Implementierung von [System. Management. Automation. Provider. itemcmdletprovider. ClearItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)zutreffen:

- Beim Definieren der Anbieter Klasse kann ein Windows PowerShell-Element Anbieter die Anbieter Funktionen von expandwildcards, Filtern, einschließen oder Ausschließen von der [System. Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration deklarieren. In diesen Fällen muss die Implementierung von [System. Management. Automation. Provider. itemcmdletprovider. ClearItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) sicherstellen, dass der an die Methode weiter gegebene Pfad diese Anforderungen erfüllt. Zu diesem Zweck sollte die-Methode auf die entsprechende Eigenschaft zugreifen, z. b. die [System. Management. Automation. Provider. cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) -und [System. Management. Automation. Provider. cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) -Eigenschaften.

- Standardmäßig sollten über schreibungen dieser Methode keine Objekte festlegen oder schreiben, die für den Benutzer ausgeblendet sind, es sei denn, die [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft ist auf `true`festgelegt. Es sollte ein Fehler an die [System. Management. Automation. Provider. cmdletprovider. Write-error](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) -Methode gesendet werden, wenn der Pfad ein Element darstellt, das für den Benutzer ausgeblendet ist, und [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ist auf `false`festgelegt.

- Ihre Implementierung der [System. Management. Automation. Provider. itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) -Methode sollte [System. Management. Automation. Provider. cmdletprovider. dendprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) aufrufen und seinen Rückgabewert überprüfen, bevor Änderungen am Datenspeicher vorgenommen werden. Diese Methode wird verwendet, um die Ausführung eines Vorgangs zu bestätigen, wenn eine Änderung am Datenspeicher vorgenommen wird, z. b. das Löschen von Dateien. Die [System. Management. Automation. Provider. cmdletprovider. tiondprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) -Methode sendet den Namen der Ressource, die mit der Windows PowerShell-Laufzeit an den Benutzer geändert werden soll, und verarbeitet alle Befehlszeilen Einstellungen oder Einstellungs Variablen, um zu bestimmen, was angezeigt werden soll.

  Nach dem Aufrufen von [System. Management. Automation. Provider. cmdletprovider. schuldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) wird `true`zurückgegeben. die [System. Management. Automation. Provider. itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) -Methode sollte die [System. Management. Automation. Provider. cmdletprovider. dendcontinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) -Methode aufrufen. Diese Methode sendet eine Meldung an den Benutzer, damit das Feedback überprüft werden kann, ob der Vorgang fortgesetzt werden soll. Der [System. Management. Automation. Provider. cmdletprovider. rudcontinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) -Befehl ermöglicht eine zusätzliche Überprüfung auf potenziell gefährliche System Änderungen.

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>Dynamische Parameter für ClearItem abrufen

Manchmal erfordert das `Clear-Item`-Cmdlet zusätzliche Parameter, die zur Laufzeit dynamisch angegeben werden. Um diese dynamischen Parameter bereitzustellen, muss der Windows PowerShell-Element Anbieter die [System. Management. Automation. Provider. itemcmdletprovider. clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) -Methode implementieren. Diese Methode ruft die dynamischen Parameter für das Element im angezeigten Pfad ab und gibt ein Objekt zurück, das über Eigenschaften und Felder mit Attribut Attributen verfügt, die einer Cmdlet-Klasse oder einem [System. Management. Automation. runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -Objekt ähneln. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene-Objekt, um die Parameter dem `Clear-Item`-Cmdlet hinzuzufügen.

Dieser Element Anbieter implementiert diese Methode nicht. Der folgende Code ist jedoch die Standard Implementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>Ausführen einer Standardaktion für ein Element

Ein Windows PowerShell-Element Anbieter kann die [System. Management. Automation. Provider. itemcmdletprovider. invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) -Methode implementieren, um Aufrufe aus dem `Invoke-Item`-Cmdlet zu unterstützen, die es dem Anbieter ermöglichen, eine Standardaktion für das Element im angegebenen Pfad auszuführen. Der File System-Anbieter könnte diese Methode z. b. verwenden, um ShellExecute für ein bestimmtes Element aufzurufen.

Diese Methode wird von diesem Anbieter nicht implementiert. Der folgende Code ist jedoch die Standard Implementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>Dinge, die Sie beim Implementieren von invokedefaultaction beachten sollten

Die folgenden Bedingungen können auf eine Implementierung von [System. Management. Automation. Provider. itemcmdletprovider. invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)zutreffen:

- Beim Definieren der Anbieter Klasse kann ein Windows PowerShell-Element Anbieter die Anbieter Funktionen von expandwildcards, Filtern, einschließen oder Ausschließen von der [System. Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration deklarieren. In diesen Fällen muss die Implementierung von [System. Management. Automation. Provider. itemcmdletprovider. invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) sicherstellen, dass der an die Methode übergebenen Pfad diese Anforderungen erfüllt. Zu diesem Zweck sollte die-Methode auf die entsprechende Eigenschaft zugreifen, z. b. die [System. Management. Automation. Provider. cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) -und [System. Management. Automation. Provider. cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) -Eigenschaften.

- Standardmäßig sollten über schreibungen dieser Methode keine Objekte festlegen oder schreiben, die für den Benutzer ausgeblendet sind, es sei denn, die [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft ist auf `true`festgelegt. Es sollte ein Fehler an die [System. Management. Automation. Provider. cmdletprovider. Write-error](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) -Methode gesendet werden, wenn der Pfad ein Element darstellt, das für den Benutzer ausgeblendet ist, und [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ist auf `false`festgelegt.

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>Dynamische Parameter für invokedefaultaction abrufen

Manchmal erfordert das `Invoke-Item`-Cmdlet zusätzliche Parameter, die zur Laufzeit dynamisch angegeben werden. Um diese dynamischen Parameter bereitzustellen, muss der Windows PowerShell-Element Anbieter die [System. Management. Automation. Provider. itemcmdletprovider. invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) -Methode implementieren. Diese Methode ruft die dynamischen Parameter für das Element im angezeigten Pfad ab und gibt ein Objekt zurück, das über Eigenschaften und Felder mit Attribut Attributen verfügt, die einer Cmdlet-Klasse oder einem [System. Management. Automation. runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -Objekt ähneln. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene-Objekt, um dem `Invoke-Item`-Cmdlet die dynamischen Parameter hinzuzufügen.

Dieser Element Anbieter implementiert diese Methode nicht. Der folgende Code ist jedoch die Standard Implementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>Implementieren von Hilfsmethoden und-Klassen

Dieser Element Anbieter implementiert mehrere Hilfsmethoden und-Klassen, die von den öffentlichen Überschreibungs Methoden verwendet werden, die von Windows PowerShell definiert werden. Der Code für diese Hilfsmethoden und-Klassen wird im [Codebeispiel](#code-sample) Abschnitt angezeigt.

### <a name="normalizepath-method"></a>Normalizepath-Methode

Dieser Element Anbieter implementiert eine normalizepath-Hilfsmethode, um sicherzustellen, dass der Pfad ein konsistentes Format aufweist. Das angegebene Format verwendet einen umgekehrten Schrägstrich (\\) als Trennzeichen.

### <a name="pathisdrive-method"></a>Pathisdrive-Methode

Dieser Element Anbieter implementiert eine pathisdrive-Hilfsmethode, um zu bestimmen, ob der angegebene Pfad tatsächlich der Laufwerks Name ist.

### <a name="chunkpath-method"></a>Chunkpath-Methode

Dieser Element Anbieter implementiert eine chunkpath-Hilfsmethode, die den angegebenen Pfad aufteilt, sodass der Anbieter seine einzelnen Elemente identifizieren kann. Es wird ein Array zurückgegeben, das aus den Pfad Elementen besteht.

### <a name="gettable-method"></a>GetTables-Methode

Dieser Element Anbieter implementiert die getTables-Hilfsmethode, die ein databasetableinfo-Objekt zurückgibt, das Informationen zu der im-Befehl angegebenen Tabelle darstellt.

### <a name="getrow-method"></a>GetRow-Methode

Die [System. Management. Automation. Provider. itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) -Methode dieses Element Anbieters Ruft die GetRows-Hilfsmethode auf. Diese Hilfsmethode Ruft ein databaserowinfo-Objekt ab, das Informationen über die angegebene Zeile in der Tabelle darstellt.

### <a name="databasetableinfo-class"></a>Databasetableinfo-Klasse

Dieser Element Anbieter definiert eine databasetableinfo-Klasse, die eine Sammlung von Informationen in einer Datentabelle in der Datenbank darstellt. Diese Klasse ähnelt der [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) -Klasse.

Der Beispiel Element Anbieter definiert eine databasetableinfo. getTables-Methode, die eine Auflistung von Tabellen Informationsobjekten zurückgibt, die die Tabellen in der Datenbank definieren. Diese Methode schließt einen try/catch-Block ein, um sicherzustellen, dass alle Datenbankfehler als Zeile mit 0 (null) Einträgen angezeigt werden.

### <a name="databaserowinfo-class"></a>Databaserowinfo-Klasse

Dieser Element Anbieter definiert die databaserowinfo-Hilfsklasse, die eine Zeile in einer Tabelle der Datenbank darstellt. Diese Klasse ähnelt der [System. IO. filinput Info](/dotnet/api/System.IO.FileInfo) -Klasse.

Der Beispiel Anbieter definiert eine databaserowinfo. GetRows-Methode, um eine Auflistung von Zeilen Informationsobjekten für die angegebene Tabelle zurückzugeben. Diese Methode enthält einen try/catch-Block zum Abfangen von Ausnahmen. Alle Fehler führen zu keinen Zeilen Informationen.

## <a name="code-sample"></a>Codebeispiel

Einen umfassenden Beispielcode finden Sie unter [AccessDbProviderSample03-Codebeispiel](./accessdbprovidersample03-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

Beim Schreiben eines Anbieters müssen möglicherweise Elemente zu vorhandenen Objekten hinzugefügt oder neue Objekte definiert werden. Wenn Sie fertig sind, erstellen Sie eine Typdatei, mit der Windows PowerShell die Member des Objekts und eine Format Datei identifizieren kann, die definiert, wie das Objekt angezeigt wird. Weitere Informationen zu finden Sie unter [Erweitern von Objekttypen und Formatierung](/previous-versions/ms714665(v=vs.85)).

## <a name="building-the-windows-powershell-provider"></a>Entwickeln des Windows PowerShell-Anbieters

Weitere Informationen finden [Sie unter Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions/ms714644(v=vs.85)).

## <a name="testing-the-windows-powershell-provider"></a>Testen des Windows PowerShell-Anbieters

Wenn dieser Windows PowerShell-Element Anbieter bei Windows PowerShell registriert ist, können Sie nur die grundlegenden und Laufwerk Funktionen des Anbieters testen. Zum Testen der Bearbeitung von Elementen müssen Sie auch die Container Funktionalität implementieren, die unter [Implementieren eines Windows PowerShell-Anbieters für Container](./creating-a-windows-powershell-container-provider.md)beschrieben wird.

## <a name="see-also"></a>Siehe auch

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell-Programmier Handbuch](./windows-powershell-programmer-s-guide.md)

[Erstellen von Windows PowerShell-Anbietern](./how-to-create-a-windows-powershell-provider.md)

[Entwerfen Ihres Windows PowerShell-Anbieters](./designing-your-windows-powershell-provider.md)

[Erweitern von Objekttypen und Formatierung](/previous-versions/ms714665(v=vs.85))

[Funktionsweise von Windows PowerShell](/previous-versions/ms714658(v=vs.85))

[Erstellen eines Windows PowerShell-Anbieters für Container](./creating-a-windows-powershell-container-provider.md)

[Erstellen eines Windows PowerShell-Anbieters für Laufwerke](./creating-a-windows-powershell-drive-provider.md)

[Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions/ms714644(v=vs.85))
