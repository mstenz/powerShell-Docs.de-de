---
title: Erstellen eine Windows PowerShell-Navigationsanbieter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- navigation providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], navigation provider
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
caps.latest.revision: 5
ms.openlocfilehash: 5f7a61e261399d3d2abe62fe4523e8c9895d5ad4
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855171"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>Erstellen eines Windows PowerShell-Navigationsanbieters

Dieses Thema beschreibt, wie Sie eine Windows PowerShell-Navigationsanbieter zu erstellen, die den Datenspeicher navigieren kann. Dieser Anbieter unterstützt rekursive Befehle, geschachtelte Container und relative Pfade.

> [!NOTE]
> Sie können die C# Quelldatei (AccessDBSampleProvider05.cs) für diesen Anbieter, die mit dem Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3.0-Laufzeitkomponenten. Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.
>
> Weitere Informationen zu anderen Implementierungen der Windows PowerShell-Anbieter, finden Sie unter [Entwerfen Ihrer Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md).

Der Anbieter, die hier beschriebenen ermöglicht der Benutzerhandle einer Access-Datenbank als Laufwerk, sodass der Benutzer, um die Datentabellen in der Datenbank navigieren können. Wenn Sie Ihren eigenen Navigationsanbieter zu erstellen, können Sie Methoden implementieren, die laufwerkbezogenen Pfade, die für die Navigation erforderlich machen, relative Pfade zu normalisieren, Verschieben von Elementen, die Data-Speicher als auch Methoden, die untergeordnete Namen zu erhalten, rufen Sie den übergeordneten Pfad eines Elements und testen können um zu identifizieren, wenn ein Element ein Container ist.

> [!CAUTION]
> Denken Sie daran, dass dieser Entwurf einer Datenbank geht davon aus, die ein Feld mit der namens-ID und der Typ des Felds LongInteger ist.

## <a name="define-the-windows-powershell-provider"></a>Definieren Sie den Windows PowerShell-Anbieter

Ein Windows PowerShell-Navigationsanbieter muss eine abgeleitete Klasse .NET erstellen, die [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) Basisklasse. Hier ist die Definition der Klasse für den Navigationsbereich-Anbieter, die in diesem Abschnitt beschrieben.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

Beachten Sie, dass in diesem Anbieter die [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) Attribut enthält zwei Parameter. Der erste Parameter gibt einen benutzerfreundlichen Namen für den Anbieter, der von Windows PowerShell verwendet wird. Der zweite Parameter gibt die spezifischen Windows PowerShell-Funktionen, die der Anbieter für die Windows PowerShell-Laufzeit während der befehlsverarbeitung verfügbar macht. Für diesen Anbieter sind keine bestimmten Windows PowerShell-Funktionen, die hinzugefügt werden.

## <a name="defining-base-functionality"></a>Definiert die grundlegenden Funktionen

Siehe [Ihr Design-PS-Anbieter](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) Basisklasse abgeleitet wird, von anderen Klassen, die anderen Anbieter bereitgestellt die Funktionalität. Ein Windows PowerShell-Navigationsanbieter, muss daher alle die Funktionalität von diesen Klassen definieren.

Zum Implementieren der Funktionalität, die sitzungsspezifischen Initialisierungsinformationen hinzufügen und Freigeben von Ressourcen, die vom Anbieter verwendet werden, finden Sie unter [Erstellen eines grundlegenden PS-Anbieters](./creating-a-basic-windows-powershell-provider.md). Die meisten Anbieter (einschließlich des Anbieters, die hier beschriebene) können jedoch die standardmäßige Implementierung dieser Funktionalität von Windows PowerShell verwenden.

Um Zugriff auf den Datenspeicher über ein Windows PowerShell-Laufwerk zu erhalten, müssen Sie die Methoden der implementieren die [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Basisklasse. Weitere Informationen zu diesen Methoden implementiert werden, finden Sie unter [erstellen ein Windows PowerShell-Laufwerk-Anbieter](./creating-a-windows-powershell-drive-provider.md).

Der Anbieter muss zum Bearbeiten der Elemente von einem Datenspeicher, z. B. abrufen, festlegen und Löschen von Elementen, die vom bereitgestellten Methoden implementieren die [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Basisklasse. Weitere Informationen zu diesen Methoden implementiert werden, finden Sie unter [erstellen eine Windows PowerShell-Elementanbieter](./creating-a-windows-powershell-item-provider.md).

Rufen Sie die untergeordneten Elemente oder ihren Namen, der die Data-Speicher als auch Methoden, die zu erstellen, kopieren, umbenennen und Entfernen von Elementen, müssen Sie die vom bereitgestellten Methoden implementieren die [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)Basisklasse. Weitere Informationen zu diesen Methoden implementiert werden, finden Sie unter [erstellen eine Windows PowerShell-Containeranbieter](./creating-a-windows-powershell-container-provider.md).

## <a name="creating-a-windows-powershell-path"></a>Beim Erstellen eines Windows PowerShell-Pfads

Windows PowerShell-Navigationsanbieter verwenden einen internen Anbieter-Windows PowerShell-Pfad, um die Elemente des Datenspeichers zu navigieren. Zum Erstellen von eines Anbieter-internen Pfads des Anbieters müssen implementieren die [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) Methodenaufrufe für die Unterstützung des kombinieren-Path-Cmdlets. Diese Methode kombiniert einen übergeordneten und untergeordneten Pfad zu einer internen Anbieter-Pfad mit einem anbieterspezifischen Pfadtrennzeichen zwischen übergeordneten und untergeordneten Pfade an.

Die Standardimplementierung akzeptiert Pfade mit "/" oder "\\"als Pfadtrennzeichen, normalisiert auf Pfadtrennzeichen"\\", die Teile mit übergeordneten und untergeordneten Pfad kombiniert, mit dem Trennzeichen zwischen ihnen und gibt dann eine Zeichenfolge, enthält die kombinierten Pfade.

Dieser Navigationsanbieter implementiert diese Methode nicht. Der folgende Code ist jedoch die standardmäßige Implementierung der [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>Punkte zu beachten, die zum Implementieren von MakePath

Die folgenden Bedingungen für Ihre Implementierung der gelten möglicherweise [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):

- Die Implementierung von der [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) Methode den Pfad als rechtliche den vollqualifizierten Pfad für den Namespace des Anbieters sollte nicht überprüft werden. Denken Sie daran, dass jeder Parameter kann nur einen Teil eines Pfads darstellen, und die kombinierten Teile kann möglicherweise einen vollständig qualifizierten Pfad nicht generiert. Z. B. die [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) -Methode für der Filesystem-Anbieter wird möglicherweise "windows\system32" in der `parent` Parameter und "abc.dll" in der `child` Parameter. Die Methode verbindet diese Werte mit der "\\" als Trennzeichen und gibt "windows\system32\abc.dll", die nicht vollqualifiziert Dateisystempfad ist.

  > [!IMPORTANT]
  > Die pfadanteile, die im Aufruf angegeben [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) enthalten möglicherweise Zeichen, die in den Namespace des Anbieters nicht zulässig. Diese Zeichen in den meisten Fällen für die platzhaltererweiterung verwendet werden, und die Implementierung dieser Methode sollte nicht entfernt.

## <a name="retrieving-the-parent-path"></a>Den übergeordnete Pfad abrufen

Windows PowerShell-Navigationsanbieter implementieren die [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) Methode zum Abrufen des übergeordneten Teils des angezeigten vollständig oder teilweise Anbieter-spezifischen Pfad. Die Methode entfernt die untergeordneten Teil des Pfads und gibt das übergeordnete Pfad aber unverändert zurück. Die `root` Parameter gibt an, die den vollqualifizierten Pfad zum Stamm eines Laufwerks. Dieser Parameter kann null oder leer, wenn ein bereitgestelltes Laufwerk nicht für den Abrufvorgang wird sein. Wenn ein Stamm angegeben wird, muss die Methode einen Pfad zu einem Container in der gleichen Struktur als Stamm zurückgeben.

Die Beispiel-Navigationsanbieter überschreibt diese Methode nicht, aber es verwendet die Standardimplementierung. Akzeptiert Pfade, die sowohl "/" und "\\" als Pfadtrennzeichen. Es zuerst normalisiert den Pfad zur nur "\\" Trennzeichen, teilt dann des letzten deaktivieren den übergeordnete Pfad "\\" und gibt den übergeordneten Pfad zurück.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>Zum Implementieren von GetParentPath merken

Die Implementierung von der [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) Methode sollte den Pfad auf dem die Trennzeichen im Pfad für den Namespace des Anbieters lexikalisch aufgeteilt wird. Beispielsweise verwendet der Filesystem-Anbieter diese Methode nach der letzten gesucht werden soll "\\" und gibt alle Elemente auf der linken Seite des Trennzeichens.

## <a name="retrieve-the-child-path-name"></a>Der Name der untergeordneten Pfad abrufen

Die Navigation-Anbieter implementiert die [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) Methode zum Abrufen des Namens (Leaf-Element) des untergeordneten Elements des Elements befindet sich in den angegebenen vollständigen oder anbieterspezifische Teilpfad.

Navigation Beispielanbieter überschreibt diese Methode nicht. Die Standardimplementierung ist unten dargestellt. Akzeptiert Pfade, die sowohl "/" und "\\" als Pfadtrennzeichen. Es zuerst normalisiert den Pfad zur nur "\\" Trennzeichen, klicken Sie dann den übergeordneten Pfad Deaktivieren des letzten teilt "\\" und der Name des untergeordneten Pfad aber unverändert zurückgegeben.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>Punkte zu beachten, die zum Implementieren von GetChildName

Die Implementierung von der [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) Methode sollte den Pfad für das Pfadtrennzeichen lexikalisch aufgeteilt wird. Wenn der angegebene Pfad keine Trennzeichen im Pfad enthält, sollte die Methode der Pfad, der unverändert zurückgegeben.

> [!IMPORTANT]
> Der Pfad, in dem Aufruf dieser Methode bereitgestellte kann Zeichen enthalten, die in den Namespace des Anbieters nicht zulässig sind. Diese Zeichen befinden sich wahrscheinlich für die platzhaltererweiterung oder Suche mit regulären Ausdrücken verwendet, und die Implementierung dieser Methode sollte nicht entfernt.

## <a name="determining-if-an-item-is-a-container"></a>Bestimmen, ob ein Element ein Container ist.

Der Navigationsbereich-Anbieter implementieren kann die [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) Methode, um zu bestimmen, ob es sich bei der angegebene Pfad einen Container angibt. True, wenn der Pfad einen Container, und klicken Sie auf "false", andernfalls darstellt gibt es zurück. Der Benutzer benötigt diese Methode verwenden, können die `Test-Path` Cmdlet für den angegebenen Pfad.

Der folgende code zeigt die [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) -Implementierung in unserem Beispiel Navigation-Anbieter. Die Methode überprüft, ob der angegebene Pfad richtig ist und wenn die Tabelle vorhanden ist, und "true" gibt, wenn der Pfad ein Containers gibt.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>Punkte zu beachten, die zum Implementieren von IsItemContainer

Ihre Navigationsanbieter .NET-Klasse kann die Funktionen des Anbieters der ExpandWildcards, Filter, einschließen oder ausschließen, deklarieren, aus der [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) Enumeration. In diesem Fall ist die Implementierung der [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) muss sicherstellen, dass der übergebene Pfad Anforderungen erfüllt. Zu diesem Zweck die Methode sollte Zugriff auf die entsprechende Eigenschaft, z. B. die [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) Eigenschaft.

## <a name="moving-an-item"></a>Verschieben eines Elements

Unterstützung des der `Move-Item` -Cmdlet, um den Navigationsbereich-Anbieter implementiert die [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) Methode. Diese Methode verschiebt das Element, die gemäß der `path` Parameter, um den Container unter dem im angegebenen Pfad die `destination` Parameter.

Navigation Beispielanbieter überschreibt nicht die [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) Methode. Im folgenden wird die standardmäßige Implementierung.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>Punkte zu beachten, die zum Implementieren von MoveItem

Ihre Navigationsanbieter .NET-Klasse kann die Funktionen des Anbieters der ExpandWildcards, Filter, einschließen oder ausschließen, deklarieren, aus der [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) Enumeration. In diesem Fall ist die Implementierung der [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) müssen sicherstellen, dass der übergebene Pfad Anforderungen erfüllt. Zu diesem Zweck die Methode sollte Zugriff auf die entsprechende Eigenschaft, z. B. die **CmdletProvider.Exclude** Eigenschaft.

Standardmäßig überschreibt diese Methode sollte nicht Objekte verschieben über vorhandene Objekte, sofern die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaftensatz auf `true`. Z. B. der Filesystem-Anbieter werden nicht kopiert c:\temp\abc.txt über eine vorhandene c:\bar.txt-Datei, wenn die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaftensatz auf `true`. Wenn der Pfad, in angegeben der `destination` Parameter vorhanden ist und einen Container, der [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) Eigenschaft ist nicht erforderlich. In diesem Fall [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) verschoben werden soll das Element, angegeben durch die `path` Parameter, um den Container angegeben wird, durch die `destination` Parameter als ein untergeordnetes Element.

Die Implementierung von der [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) Methodenaufruf sollten [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) , und überprüfen Sie den Rückgabewert, bevor Änderungen an den Datenspeicher. Diese Methode wird verwendet, um die Ausführung eines Vorgangs zu bestätigen, wenn eine Änderung z. B. um den Systemstatus erfolgt Dateien werden gelöscht. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sendet den Namen der Ressource, die für den Benutzer geändert werden, mit der Windows PowerShell-Laufzeit berücksichtigt alle über die befehlszeileneinstellungen oder der Preference-Variablen in bestimmen, was dem Benutzer angezeigt werden soll.

Nach dem Aufruf von [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) gibt `true`, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) Methodenaufruf sollte die [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) Methode. Diese Methode sendet eine Nachricht an den Benutzer können Sie Feedback zu sagen, wenn der Vorgang fortgesetzt werden soll. Ihr Anbieter sollte Aufrufen [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) als eine zusätzliche Überprüfung auf potenziell gefährliche systemmodifizierungen.

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>Das Cmdlet "Move-Item" Anfügen dynamische Parameter

In einigen Fällen die `Move-Item` Cmdlet erfordert zusätzliche Parameter, die zur Laufzeit dynamisch bereitgestellt werden. Um diese dynamischen Parameter zu gewährleisten, muss der Navigationsanbieter implementieren die [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) Methode, um die erforderlichen Parameterwerte abzurufen. ein Objekt mit Eigenschaften und Felder mit der Analyse Attribute aus dem Element am angegebenen Pfad, und Rückgabe ähnlich einer Cmdlet-Klasse oder ein [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt.

Dieser Navigationsanbieter implementiert diese Methode nicht. Der folgende Code ist jedoch die standardmäßige Implementierung des [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>Das Normalisieren eines relativen Pfads

Die Navigation-Anbieter implementiert die [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) Methode, um den vollqualifizierten Pfad zu normalisieren angegeben wird, der `path` Parameter als relativ zum angegebenen Pfad die `basePath` Parameter. Die Methode gibt eine Zeichenfolgendarstellung der normalisierte Pfad zurück. Er schreibt einen Fehler, wenn die `path` Parameter gibt den Pfad nicht vorhanden.

Navigation Beispielanbieter überschreibt diese Methode nicht. Im folgenden wird die standardmäßige Implementierung.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>Punkte zu beachten, die zum Implementieren von NormalizeRelativePath

Die Implementierung von [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) analysieren soll, die `path` -Parameter, aber es muss keine rein syntaktischen Analyse verwenden. Sie werden aufgefordert, entwerfen, dass diese Methode verwenden Sie den Pfad für die Suche der Pfadangaben in den Datenspeicher aus, und erstellen Sie einen Pfad, der die Groß-/Kleinschreibung übereinstimmt und standardisierten Syntax für elementpfade.

## <a name="code-sample"></a>Codebeispiel

Vollständigen Beispielcode finden Sie unter [AccessDbProviderSample05 Codebeispiel](./accessdbprovidersample05-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

Es ist möglich, für einen Anbieter zum Hinzufügen von Mitgliedern zu vorhandenen Objekten oder neue Objekte zu definieren. Weitere Informationen finden Sie unter[Objekttypen erweitern und Formatierung](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Erstellen den Windows PowerShell-Anbieter

Weitere Informationen finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Testen des Windows PowerShell-Anbieters

Wenn Ihre Windows PowerShell-Anbieter mit Windows PowerShell registriert wurde, können Sie es testen, durch Ausführen der unterstützten Cmdlets in der Befehlszeile, einschließlich Cmdlets, die durch Ableitung zur Verfügung gestellt. In diesem Beispiel wird die Navigation Beispielanbieter testen.

1. Führen Sie Ihre neue Shell, und Verwenden der `Set-Location` Cmdlet, um den Pfad zu die Access-Datenbank anzugeben.

   ```powershell
   Set-Location mydb:
   ```

2. Führen Sie nun die `Get-Childitem` -Cmdlet zum Abrufen einer Liste von der Datenbank-Elemente, die den Tabellen der verfügbar sind. Für jede Tabelle ruft dieses Cmdlet auch die Anzahl der Zeilen der Tabelle ab.

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```output
   RowCount   Name
   --------   ----
        180   MSysAccessObjects
          0   MSysACEs
          1   MSysCmdbars
          0   MSysIMEXColumns
          0   MSysIMEXSpecs
          0   MSysObjects
          0   MSysQueries
          7   MSysRelationships
          8   Categories
         91   Customers
          9   Employees
       2155   Order Details
        830   Orders
         77   Products
          3   Shippers
         29   Suppliers
   ```

3. Verwenden der `Set-Location` Cmdlet erneut aus, um den Speicherort der Mitarbeiter Datentabelle festgelegt.

   ```powershell
   Set-Location Employees
   ```

4. Wir stellen jetzt mit der `Get-Location` Cmdlet, um den Pfad zu der Employees-Tabelle abrufen.

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. Verwenden Sie jetzt die `Get-Childitem` Cmdlet über die Pipeline an das `Format-Table` Cmdlet. Dieser Satz von Cmdlets Ruft die Elemente für die Mitarbeiter-Datentabelle, die Zeilen der Tabelle ab. Sie werden formatiert entsprechend der Angabe durch die `Format-Table` Cmdlet.

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```output
   RowNumber   PSIsContainer   Data
   ---------   --------------   ----
   0           False            System.Data.DataRow
   1           False            System.Data.DataRow
   2           False            System.Data.DataRow
   3           False            System.Data.DataRow
   4           False            System.Data.DataRow
   5           False            System.Data.DataRow
   6           False            System.Data.DataRow
   7           False            System.Data.DataRow
   8           False            System.Data.DataRow
   ```

6. Sie können jetzt ausführen der `Get-Item` Cmdlet, um die Elemente für die Zeile "0" der Tabelle Employees Daten abgerufen werden sollen.

   ```powershell
   Get-Item 0
   ```

   ```output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. Verwenden der `Get-Item` Cmdlet erneut aus, um die Mitarbeiterdaten für die Elemente in Zeile 0 abzurufen.

   ```powershell
   (Get-Item 0).data
   ```

   ```output
   EmployeeID      : 1
   LastName        : Davis
   FirstName       : Sara
   Title           : Sales Representative
   TitleOfCourtesy : Ms.
   BirthDate       : 12/8/1968 12:00:00 AM
   HireDate        : 5/1/1992 12:00:00 AM
   Address         : 4567 Main Street
                     Apt. 2A
   City            : Buffalo
   Region          : NY
   PostalCode      : 98052
   Country         : USA
   HomePhone       : (206) 555-9857
   Extension       : 5467
   Photo           : EmpID1.bmp
   Notes           : Education includes a BA in psychology from
                     Colorado State University. She also completed "The
                     Art of the Cold Call."  Nancy is a member of
                     Toastmasters International.
   ReportsTo       : 2
   ```

## <a name="see-also"></a>Weitere Informationen

[Erstellen von Windows PowerShell-Anbieter](./how-to-create-a-windows-powershell-provider.md)

[Entwurf der Windows-PowerShell-Anbieter](./designing-your-windows-powershell-provider.md)

[Erweitern die Objekttypen und Formatierung](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implementieren eines Containers Windows PowerShell-Anbieters](./creating-a-windows-powershell-container-provider.md)

[So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Handbuch für Programmierer](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)