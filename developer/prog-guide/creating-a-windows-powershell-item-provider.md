---
title: Erstellen eine Windows PowerShell-Elementanbieter | Microsoft-Dokumentation
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
ms.openlocfilehash: be1446dbd2b244f4752e55c8137433edee8427b0
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429991"
---
# <a name="creating-a-windows-powershell-item-provider"></a>Erstellen eines Windows PowerShell-Elementanbieters

Dieses Thema beschreibt, wie Sie einen Windows PowerShell-Anbieter erstellen, der die Daten in einem Datenspeicher bearbeiten können. In diesem Thema werden die Elemente der Daten im Speicher zum Speichern von als "Elemente" der Daten bezeichnet. Daher ist ein Anbieter, der die Daten im Speicher zu bearbeiten, kann als eine Windows PowerShell-elementanbieter bezeichnet.

> [!NOTE]
> Sie können die C# Quelldatei (AccessDBSampleProvider03.cs) für diesen Anbieter, die mit dem Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3.0-Laufzeitkomponenten. Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.
>
> Weitere Informationen zu anderen Implementierungen der Windows PowerShell-Anbieter, finden Sie unter [Entwerfen Ihrer Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md).

Die in diesem Thema beschriebenen Windows PowerShell-elementanbieter ruft Datenelemente aus einer Access-Datenbank ab. In diesem Fall wird eine "Item", entweder eine Tabelle in der Access-Datenbank oder eine Zeile in einer Tabelle.

Die folgende Liste enthält die Abschnitte in diesem Thema. Wenn Sie mit dem Schreiben von einer Windows PowerShell-elementanbieter nicht vertraut sind, lesen Sie diese Abschnitte in der angezeigten Reihenfolge. Allerdings Sie mit dem Schreiben von einer Windows PowerShell-elementanbieter vertraut sind, fahren Sie direkt auf die Informationen, die Sie benötigen:

- [Definieren die Windows PowerShell-Item-Provider-Klasse](#Defining-the-Windows-PowerShell-Item-Provider-Class)

- [Definiert die grundlegenden Funktionen](#Defining-Base-Functionality)

- [Für die Gültigkeit überprüfen](#Checking-for-Path-Validity)

- [Bestimmen, ob ein Element vorhanden ist.](#Determining-if-an-Item-Exists)

- [Anfügen von dynamische Parametern zu der `Test-Path` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Test-Path-Cmdlet)

- [Abrufen eines Elements](#Retrieving-an-Item)

- [Anfügen von dynamische Parametern zu der `Get-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Item-Cmdlet)

- [Ein Element festlegen](#Setting-an-Item)

- [Anfügen von dynamische Parametern zu der `Set-Item` Cmdlet](#Retrieving-Dynamic-Parameters-for-SetItem)

- [Löschen eines Elements](#Clearing-an-Item)

- [Dynamische Parameter Anfügen an das Cmdlet Get-Item Cler](#Retrieve-Dynamic-Parameters-for-ClearItem)

- [Eine Standardaktion ausführen für ein Element](#Performing-a-Default-Action-for-an-Item)

- [Abrufen von dynamischen Parametern für InvokeDefaultAction](#Retrieve-Dynamic-Parameters-for-InvokeDefaultAction)

- [Implementieren von Hilfsmethoden und-Klassen](#Implementing-Helper-Methods-and-Classes)

- [Codebeispiel](#Code-Sample)

- [Definieren von Objekttypen und Formatierung](#Defining-Object-Types-and-Formatting)

- [Erstellen den Windows PowerShell-Anbieter](#Building-the-Windows-PowerShell-provider)

- [Testen der Windows PowerShell-Anbieter](#Testing-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-item-provider-class"></a>Definieren die Windows PowerShell-Item-Provider-Klasse

Ein Windows PowerShell-elementanbieter muss eine abgeleitete Klasse .NET definieren die [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Basisklasse. Folgendes ist die Definition der Klasse für den elementanbieter, die in diesem Abschnitt beschrieben.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

Beachten Sie, dass diese Klasse die Definition der [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) Attribut enthält zwei Parameter. Der erste Parameter gibt einen benutzerfreundlichen Namen für den Anbieter, der von Windows PowerShell verwendet wird. Der zweite Parameter gibt die spezifischen Windows PowerShell-Funktionen, die der Anbieter für die Windows PowerShell-Laufzeit während der befehlsverarbeitung verfügbar macht. Für diesen Anbieter sind keine hinzugefügten bestimmten Funktionen von Windows PowerShell.

## <a name="defining-base-functionality"></a>Definiert die grundlegenden Funktionen

Siehe [Entwurf der Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Klasse abgeleitet wird, von anderen Klassen, die verschiedene bereitgestellt Anbieterfunktionen. Ein Windows PowerShell-elementanbieter, muss daher alle die Funktionalität von diesen Klassen definieren.

Weitere Informationen zum Implementieren von Funktionen, die sitzungsspezifischen Initialisierungsinformationen hinzufügen und Freigeben von Ressourcen, die vom Anbieter verwendete, finden Sie unter [erstellen einen einfachen Windows PowerShell-Anbieter](./creating-a-basic-windows-powershell-provider.md). Allerdings können die meisten Anbieter, einschließlich des hier beschriebenen Anbieters die standardmäßige Implementierung dieser Funktionalität, die von Windows PowerShell bereitgestellt wird.

Vor der Windows PowerShell-elementanbieter die Elemente im Speicher ändern kann, müssen sie die Methoden der implementieren die [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Basisklasse, um den Zugriff auf den Datenspeicher. Weitere Informationen zur Implementierung dieser Klasse finden Sie unter [erstellen ein Windows PowerShell-Laufwerk-Anbieter](./creating-a-windows-powershell-drive-provider.md).

## <a name="checking-for-path-validity"></a>Für die Gültigkeit überprüfen

Bei der Suche für ein Datenelement, stellt die Windows PowerShell-Laufzeit die bereit eines Windows PowerShell-Pfads auf den Anbieter, wie im Abschnitt "Konzepte PSPath" definiert [Funktionsweise von Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58). Ein Windows PowerShell-elementanbieter muss überprüfen, ob die syntaktische und semantische Gültigkeit jeder Pfad, der an es übergeben wird, durch die Implementierung der [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) Methode. Diese Methode gibt `true` Wenn der Pfad gültig ist und `false` andernfalls. Beachten Sie, dass die Implementierung dieser Methode nicht das Vorhandensein des Elements unter dem Pfad, aber nur überprüft werden soll, die der Pfad syntaktisch und semantisch richtige sein.

Dies ist die Implementierung von der [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) Methode für diesen Anbieter. Beachten Sie, dass diese Implementierung eine NormalizePath-Hilfsmethode zum Konvertieren alle Trennzeichen im Pfad zu einer einheitlichen aufruft.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>Bestimmen, ob ein Element vorhanden ist.

Nachdem Sie überprüft haben, den Pfad, muss die Windows PowerShell-Laufzeit bestimmen, ob es sich bei ein Datenelements unter diesem Pfad vorhanden ist. Um diese Art von Abfrage zu unterstützen, die Windows PowerShell-elementanbieter implementiert die [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) Methode. Diese Methode gibt `true` ist ein Element am angegebenen Pfad gefunden und `false` (Standard) werden, andernfalls.

Dies ist die Implementierung von der [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) Methode für diesen Anbieter. Beachten Sie, dass diese Methode die Hilfsmethoden PathIsDrive ChunkPath und GetTable ruft und einen Anbieter verwendet definiert DatabaseTableInfo-Objekt.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>Punkte zu beachten, die zum Implementieren von ItemExists

Die folgenden Bedingungen für Ihre Implementierung der gelten möglicherweise [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists):

- Wenn die Provider-Klasse zu definieren, kann ein Windows PowerShell-elementanbieter von Funktionen des Anbieters der ExpandWildcards, Filter, einschließen oder ausschließen, deklarieren die [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)Enumeration. In diesen Fällen die Implementierung der [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) Methode muss sicherstellen, dass der Pfad, an die Methode übergeben die die angegebenen Funktionen erfüllt. Zu diesem Zweck die Methode sollte Zugriff auf die entsprechende Eigenschaft, z. B. die [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) und [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) Eigenschaften.

- Die Implementierung dieser Methode sollte keinerlei Zugriff auf das Element verarbeiten, die das Element für den Benutzer sichtbar machen können. Z. B. wenn ein Benutzer Schreibzugriff in eine Datei über der FileSystem-Anbieter (bereitgestellt durch Windows PowerShell), aber keinen Lesezugriff verfügt, die Datei noch vorhanden ist und [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) gibt `true`. Ihre Implementierung möglicherweise Überprüfen eines übergeordneten Elements, um festzustellen, ob das untergeordnete Element aufgelistet werden kann.

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>Das Cmdlet "Test-Path" Anfügen dynamische Parameter

In einigen Fällen die `Test-Path` -Cmdlet, das Aufrufe [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) erfordert zusätzliche Parameter, die dynamisch zur Laufzeit angegeben werden. Diese dynamische Parameter der Windows PowerShell bereitstellen muss vom elementanbieter implementiert die [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) Methode. Diese Methode ruft die dynamischen Parameter für das Element am angegebenen Pfad ab und gibt ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene Objekt, um die Parameter zum Hinzufügen der `Test-Path` Cmdlet.

Dieses Windows PowerShell-elementanbieter implementiert diese Methode nicht. Der folgende Code ist jedoch die Standardimplementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>Abrufen eines Elements

Um ein Element abgerufen werden, muss die Windows PowerShell-elementanbieter überschreiben [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) -Methode zur Unterstützung der Aufrufe von der `Get-Item` Cmdlet. Das Element mit der diese Methode schreibt die [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) Methode.

Dies ist die Implementierung von der [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) Methode für diesen Anbieter. Beachten Sie, dass diese Methode die Hilfsmethoden GetTable und die GetRow verwendet, um die Elemente abgerufen werden sollen, die Tabellen in der Access-Datenbank oder Zeilen in einer Tabelle darstellen.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>Punkte zu beachten, die zum Implementieren von GetItem

Möglicherweise gelten die folgenden Bedingungen zu einer Implementierung von [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem):

- Wenn die Provider-Klasse zu definieren, kann ein Windows PowerShell-elementanbieter von Funktionen des Anbieters der ExpandWildcards, Filter, einschließen oder ausschließen, deklarieren die [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)Enumeration. In diesen Fällen die Implementierung der [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) müssen sicherstellen, dass der Pfad, an die Methode übergeben, diese Anforderungen erfüllt. Zu diesem Zweck die Methode sollte Zugriff auf die entsprechende Eigenschaft, z. B. die [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) und [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) Eigenschaften.

- Standardmäßig überschreibt diese Methode sollte nicht abgerufen werden Objekte, die in der Regel in der der Benutzer es sei denn, ausgeblendet sind die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaftensatz auf `true`. Z. B. die [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) -Methode für der FileSystem-Anbieter überprüft die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) Eigenschaft, bevor versucht wird, rufen Sie [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) nach ausgeblendeten oder Systemdateien.

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>Das Cmdlet "Get-Item" Anfügen dynamische Parameter

In einigen Fällen die `Get-Item` Cmdlet erfordert zusätzliche Parameter, die dynamisch zur Laufzeit angegeben werden. Diese dynamische Parameter der Windows PowerShell bereitstellen muss vom elementanbieter implementiert die [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) Methode. Diese Methode ruft die dynamischen Parameter für das Element am angegebenen Pfad ab und gibt ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene Objekt, um die Parameter zum Hinzufügen der `Get-Item` Cmdlet.

Dieser Anbieter wird diese Methode nicht implementiert. Der folgende Code ist jedoch die Standardimplementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>Ein Element festlegen

Um ein Element festzulegen, muss die Windows PowerShell-elementanbieter überschreiben die [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) -Methode zur Unterstützung der Aufrufe von der `Set-Item` Cmdlet. Diese Methode wird der Wert des Elements am angegebenen Pfad.

Dieser Anbieter stellt keine Außerkraftsetzung für die [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) Methode. Folgendes ist jedoch die Standardimplementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>Punkte zu beachten, die zum Implementieren von SetItem

Die folgenden Bedingungen für Ihre Implementierung der gelten möglicherweise [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem):

- Wenn die Provider-Klasse zu definieren, kann ein Windows PowerShell-elementanbieter von Funktionen des Anbieters der ExpandWildcards, Filter, einschließen oder ausschließen, deklarieren die [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)Enumeration. In diesen Fällen die Implementierung der [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) müssen sicherstellen, dass der Pfad, an die Methode übergeben, diese Anforderungen erfüllt. Zu diesem Zweck die Methode sollte Zugriff auf die entsprechende Eigenschaft, z. B. die [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) und [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) Eigenschaften.

- Standardmäßig überschreibt diese Methode sollte nicht festgelegt oder Schreiben von Objekten, die vom Benutzer ausgeblendet sind, es sei denn, die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaftensatz auf `true`. Ein Fehler gesendet werden soll, um die [System.Management.Automation.Provider.Cmdletprovider.Writeerror*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) Methode, wenn Sie den Pfad ein ausgeblendetes Element darstellt und [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) nastaven NA hodnotu `false`.

- Die Implementierung von der [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) Methodenaufruf sollten [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)und den Rückgabewert zu überprüfen, bevor Sie Änderungen an den Datenspeicher. Diese Methode wird verwendet, um die Ausführung eines Vorgangs zu bestätigen, wenn eine Änderung vorgenommen wird, mit dem Datenspeicher, z. B. Dateien werden gelöscht. Die [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) Methode sendet den Namen der Ressource, die für den Benutzer geändert werden, mit der Windows PowerShell-Laufzeit berücksichtigt alle befehlszeileneinstellungen oder Preference-Variablen, bei der Bestimmung, was angezeigt werden soll.

  Nach dem Aufruf von [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) gibt `true`, [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)Methodenaufruf sollte die [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) Methode. Diese Methode sendet eine Nachricht an den Benutzer können Sie Feedback zu überprüfen, ob der Vorgang fortgesetzt werden soll. Der Aufruf von [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) ermöglicht eine zusätzliche Überprüfung auf potenziell gefährliche systemmodifizierungen.

## <a name="retrieving-dynamic-parameters-for-setitem"></a>Abrufen von dynamischen Parametern für SetItem

In einigen Fällen die `Set-Item` Cmdlet erfordert zusätzliche Parameter, die dynamisch zur Laufzeit angegeben werden. Diese dynamische Parameter der Windows PowerShell bereitstellen muss vom elementanbieter implementiert die [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) Methode. Diese Methode ruft die dynamischen Parameter für das Element am angegebenen Pfad ab und gibt ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene Objekt, um die Parameter zum Hinzufügen der `Set-Item` Cmdlet.

Dieser Anbieter wird diese Methode nicht implementiert. Der folgende Code ist jedoch die Standardimplementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>Löschen eines Elements

Um ein Element zu löschen, die Windows PowerShell-elementanbieter implementiert die [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) -Methode zur Unterstützung der Aufrufe von der `Clear-Item` Cmdlet. Diese Methode löscht das Datenelement am angegebenen Pfad.

Dieser Anbieter wird diese Methode nicht implementiert. Der folgende Code ist jedoch die Standardimplementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>Punkte zu beachten, die zum Implementieren von ClearItem

Möglicherweise gelten die folgenden Bedingungen zu einer Implementierung von [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem):

- Wenn die Provider-Klasse zu definieren, kann ein Windows PowerShell-elementanbieter von Funktionen des Anbieters der ExpandWildcards, Filter, einschließen oder ausschließen, deklarieren die [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)Enumeration. In diesen Fällen die Implementierung der [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) müssen sicherstellen, dass der Pfad, an die Methode übergeben, diese Anforderungen erfüllt. Zu diesem Zweck die Methode sollte Zugriff auf die entsprechende Eigenschaft, z. B. die [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) und [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) Eigenschaften.

- Standardmäßig überschreibt diese Methode sollte nicht festgelegt oder Schreiben von Objekten, die vom Benutzer ausgeblendet sind, es sei denn, die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaftensatz auf `true`. Ein Fehler gesendet werden soll, um die [System.Management.Automation.Provider.Cmdletprovider.Writeerror*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) Methode, wenn Sie den Pfad ein Elements darstellt, die vom Benutzer ausgeblendet ist und [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) nastaven NA hodnotu `false`.

- Die Implementierung von der [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) Methodenaufruf sollten [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)und den Rückgabewert zu überprüfen, bevor Sie Änderungen an den Datenspeicher. Diese Methode wird verwendet, um die Ausführung eines Vorgangs zu bestätigen, wenn eine Änderung vorgenommen wird, mit dem Datenspeicher, z. B. Dateien werden gelöscht. Die [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) Methode sendet den Namen der Ressource, die in den Benutzer mit der Windows PowerShell-Laufzeit geändert werden, und alle befehlszeileneinstellungen oder Einstellung Variablen, bei der Bestimmung, was angezeigt werden soll.

  Nach dem Aufruf von [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) gibt `true`, [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)Methodenaufruf sollte die [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) Methode. Diese Methode sendet eine Nachricht an den Benutzer können Sie Feedback zu überprüfen, ob der Vorgang fortgesetzt werden soll. Der Aufruf von [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) ermöglicht eine zusätzliche Überprüfung auf potenziell gefährliche systemmodifizierungen.

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>Dynamische Parameter für ClearItem abrufen

In einigen Fällen die `Clear-Item` Cmdlet erfordert zusätzliche Parameter, die dynamisch zur Laufzeit angegeben werden. Diese dynamische Parameter der Windows PowerShell bereitstellen muss vom elementanbieter implementiert die [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) Methode. Diese Methode ruft die dynamischen Parameter für das Element am angegebenen Pfad ab und gibt ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene Objekt, um die Parameter zum Hinzufügen der `Clear-Item` Cmdlet.

Dieses elementanbieter implementiert diese Methode nicht. Der folgende Code ist jedoch die Standardimplementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>Eine Standardaktion ausführen für ein Element

Ein Windows PowerShell-elementanbieter kann implementieren, die [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) -Methode zur Unterstützung der Aufrufe von der `Invoke-Item` -Cmdlet, das der Anbieter ermöglicht, Führen Sie eine Standardaktion für das Element am angegebenen Pfad. Beispielsweise kann der FileSystem-Anbieter diese Methode verwenden, ShellExecute für ein bestimmtes Element aufrufen.

Dieser Anbieter wird diese Methode nicht implementiert. Der folgende Code ist jedoch die Standardimplementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>Punkte zu beachten, die zum Implementieren von InvokeDefaultAction

Möglicherweise gelten die folgenden Bedingungen zu einer Implementierung von [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction):

- Wenn die Provider-Klasse zu definieren, kann ein Windows PowerShell-elementanbieter von Funktionen des Anbieters der ExpandWildcards, Filter, einschließen oder ausschließen, deklarieren die [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)Enumeration. In diesen Fällen die Implementierung der [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) müssen sicherstellen, dass der Pfad, an die Methode übergeben, diese Anforderungen erfüllt. Zu diesem Zweck die Methode sollte Zugriff auf die entsprechende Eigenschaft, z. B. die [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) und [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) Eigenschaften.

- Standardmäßig überschreibt diese Methode sollte nicht festgelegt oder Schreiben von Objekten, die vom Benutzer ausgeblendet werden, es sei denn, die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaftensatz auf `true`. Ein Fehler gesendet werden soll, um die [System.Management.Automation.Provider.Cmdletprovider.Writeerror*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) Methode, wenn Sie den Pfad ein Elements darstellt, die vom Benutzer ausgeblendet ist und [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) nastaven NA hodnotu `false`.

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>Dynamische Parameter für InvokeDefaultAction abrufen

In einigen Fällen die `Invoke-Item` Cmdlet erfordert zusätzliche Parameter, die dynamisch zur Laufzeit angegeben werden. Diese dynamische Parameter der Windows PowerShell bereitstellen muss vom elementanbieter implementiert die [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) Methode. Diese Methode ruft die dynamischen Parameter für das Element am angegebenen Pfad ab und gibt ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene Objekt, um die dynamischen Parameter zum Hinzufügen der `Invoke-Item` Cmdlet.

Dieses elementanbieter implementiert diese Methode nicht. Der folgende Code ist jedoch die Standardimplementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>Implementieren von Hilfsmethoden und-Klassen

Dieses elementanbieter implementiert mehrere Hilfsmethoden und Klassen, die von der öffentlichen verwendet werden Überschreiben von Windows PowerShell definiert. Der Code für diese Hilfsmethoden und Klassen werden angezeigt, der [Codebeispiel](#Code-Sample) Abschnitt.

### <a name="normalizepath-method"></a>NormalizePath-Methode

Dieses elementanbieter implementiert eine NormalizePath-Hilfsmethode, um sicherzustellen, dass der Pfad ein konsistentes Format enthält. Das angegebene Format wird der umgekehrte Schrägstrich (\\) als Trennzeichen.

### <a name="pathisdrive-method"></a>PathIsDrive-Methode

Dieses elementanbieter implementiert eine PathIsDrive-Hilfsmethode, um festzustellen, ob der angegebene Pfad tatsächlich den Namen des Laufwerks ist.

### <a name="chunkpath-method"></a>ChunkPath-Methode

Dieses elementanbieter implementiert eine ChunkPath-Hilfsmethode, die den angegebenen Pfad unterbrochen wird, damit der Anbieter die einzelnen Elemente identifizieren kann. Es gibt zurück, dass ein Array, das die Pfad-Elemente aus.

### <a name="gettable-method"></a>GetTable-Methode

Dieses elementanbieter implementiert die GetTables-Hilfsmethode, die eine DatabaseTableInfo-Objekt zurückgibt, das Informationen über die Tabelle, die im Aufruf angegeben darstellt.

### <a name="getrow-method"></a>GetRow-Methode

Die [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) Methodenaufrufe für diesen elementanbieter die GetRows-Hilfsmethode. Diese Hilfsmethode Ruft ein DatabaseRowInfo-Objekt, das Informationen über die angegebene Zeile in der Tabelle darstellt.

### <a name="databasetableinfo-class"></a>DatabaseTableInfo-Klasse

Dieser elementanbieter definiert eine DatabaseTableInfo-Klasse, die eine Auflistung von Informationen in einer Datentabelle in der Datenbank darstellt. Diese Klasse ist vergleichbar mit der [System.IO.Directoryinfo](/dotnet/api/System.IO.DirectoryInfo) Klasse.

Der Beispielanbieter-Element definiert eine DatabaseTableInfo.GetTables-Methode, die eine Auflistung von Tabellenobjekten Informationen definieren die Tabellen in der Datenbank zurückgibt. Diese Methode enthält einen Try/Catch-Block, um sicherzustellen, dass alle Datenbank-Fehler als eine Zeile mit NULL-Einträge werden angezeigt.

### <a name="databaserowinfo-class"></a>DatabaseRowInfo-Klasse

Dieser elementanbieter definiert die DatabaseRowInfo-Hilfsklasse, die eine Zeile in einer Tabelle der Datenbank darstellt. Diese Klasse ist vergleichbar mit der [System.IO.Fileinfo](/dotnet/api/System.IO.FileInfo) Klasse.

Der Beispielanbieter definiert eine DatabaseRowInfo.GetRows-Methode, um eine Auflistung von Objekten von Zeile Informationen für die angegebene Tabelle zurück. Diese Methode enthält einen Try/Catch-Block zum Abfangen von Ausnahmen. Jeder Fehler führt keine Zeileninformationen.

## <a name="code-sample"></a>Codebeispiel

Vollständigen Beispielcode finden Sie unter [AccessDbProviderSample03 Codebeispiel](./accessdbprovidersample03-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

Wenn Sie einen Anbieter schreiben, ist es möglicherweise notwendig, vorhandene Objekte hinzufügen oder neue Objekte zu definieren. Abschließend erstellen Sie eine Typendatei, die Windows PowerShell verwenden können, um der Member des Objekts zu identifizieren und einer Formatdatei, die definiert, wie das Objekt angezeigt wird. Weitere Informationen finden Sie unter [Objekttypen erweitern und Formatierung](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Erstellen den Windows PowerShell-Anbieter

Finden Sie unter [so registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Testen des Windows PowerShell-Anbieters

Wenn dieser Windows PowerShell-elementanbieter mit Windows PowerShell registriert ist, können Sie nur die grundlegenden testen und fördern die Funktionalität des Anbieters. Um die Bearbeitung von Elementen zu testen, müssen Sie auch Container-Funktionen, die in beschriebenen implementieren [implementieren eine Windows PowerShell-Containeranbieter](./creating-a-windows-powershell-container-provider.md).

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell Handbuch für Programmierer](./windows-powershell-programmer-s-guide.md)

[Erstellen von Windows PowerShell-Anbieter](./how-to-create-a-windows-powershell-provider.md)

[Entwerfen Ihre Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md)

[Erweitern die Objekttypen und Formatierung](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Funktionsweise von Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Erstellen eines Containers Windows PowerShell-Anbieters](./creating-a-windows-powershell-container-provider.md)

[Erstellen einen Laufwerk Windows PowerShell-Anbieter](./creating-a-windows-powershell-drive-provider.md)

[So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)