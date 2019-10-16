---
title: Erstellen eines Windows PowerShell-Container Anbieters | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], container provider
- container providers [PowerShell Programmer's Guide]
ms.assetid: a7926647-0d18-45b2-967e-b31f92004bc4
caps.latest.revision: 5
ms.openlocfilehash: 0822e01d1191b019318fd0ea06dadea1a87a299e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366849"
---
# <a name="creating-a-windows-powershell-container-provider"></a>Erstellen eines Windows PowerShell-Containeranbieters

In diesem Thema wird beschrieben, wie Sie einen Windows PowerShell-Anbieter erstellen, der in Daten speichern mit mehreren Ebenen verwendet werden kann. Bei dieser Art von Datenspeicher enthält die oberste Ebene des Stores die Stamm Elemente, und jede nachfolgende Ebene wird als Knoten untergeordneter Elemente bezeichnet. Da der Benutzer an diesen untergeordneten Knoten arbeiten kann, kann er hierarchisch über den Datenspeicher interagieren.

Anbieter, die an Daten speichern mit mehreren Ebenen arbeiten können, werden als Windows PowerShell-Container Anbieter bezeichnet. Beachten Sie jedoch, dass ein Windows PowerShell-Container Anbieter nur verwendet werden kann, wenn es einen Container (keine unter-Container) mit Elementen gibt. Wenn es sich um Container handelt, müssen Sie einen Windows PowerShell-Navigations Anbieter implementieren. Weitere Informationen zum Implementieren des Windows PowerShell-navigationsanbieters finden Sie unter [Erstellen eines Windows PowerShell-navigationsanbieters](./creating-a-windows-powershell-navigation-provider.md).

> [!NOTE]
> Sie können die C# Quelldatei (AccessDBSampleProvider04.cs) für diesen Anbieter mithilfe des Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3,0-Laufzeitkomponenten herunterladen. Anweisungen zum Herunterladen finden Sie unter [Installieren von Windows PowerShell und Herunterladen des Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Die heruntergeladenen Quelldateien sind in den **\<powershell-Beispielen >** Verzeichnis verfügbar.
>
> Weitere Informationen zu anderen Windows PowerShell-Anbieter Implementierungen finden [Sie unter Entwerfen des Windows PowerShell-Anbieters](./designing-your-windows-powershell-provider.md).

Mit dem hier beschriebenen Windows PowerShell-Container Anbieter wird die Datenbank als einzelner Container definiert, wobei die Tabellen und Zeilen der Datenbank als Container Elemente definiert sind.

> [!CAUTION]
> Beachten Sie, dass bei diesem Entwurf eine Datenbank mit einem Feld mit der namens-ID und der Typ des Felds longinteger ist.

## <a name="defining-a-windows-powershell-container-provider-class"></a>Definieren einer Windows PowerShell-Container Anbieter Klasse

Ein Windows PowerShell-Container Anbieter muss eine .NET-Klasse definieren, die von der [System. Management. Automation. Provider. containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) -Basisklasse abgeleitet wird. Hier ist die Klassendefinition für den Windows PowerShell-Container Anbieter, der in diesem Abschnitt beschrieben wird.

```csharp
   [CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

Beachten Sie, dass in dieser Klassendefinition das [System. Management. Automation. Provider. cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) -Attribut zwei Parameter enthält. Der erste Parameter gibt einen benutzerfreundlichen Namen für den Anbieter an, der von Windows PowerShell verwendet wird. Der zweite Parameter gibt die Windows PowerShell-spezifischen Funktionen an, die der Anbieter während der Befehls Verarbeitung für die Windows PowerShell-Laufzeit verfügbar macht. Für diesen Anbieter gibt es keine Windows PowerShell-spezifischen Funktionen, die hinzugefügt werden.

## <a name="defining-base-functionality"></a>Definieren der Basisfunktionalität

Wie unter [Entwerfen des Windows PowerShell-Anbieters](./designing-your-windows-powershell-provider.md)beschrieben, wird die [System. Management. Automation. Provider. containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) -Klasse von mehreren anderen Klassen abgeleitet, die unterschiedliche Anbieter Funktionen bereitgestellt haben. Ein Windows PowerShell-Container Anbieter muss daher alle Funktionen definieren, die von diesen Klassen bereitgestellt werden.

Informationen zum Implementieren von Funktionen zum Hinzufügen von Sitzungs spezifischen Initialisierungs Informationen und zum Freigeben von Ressourcen, die vom Anbieter verwendet werden, finden Sie unter [Erstellen eines einfachen Windows PowerShell-Anbieters](./creating-a-basic-windows-powershell-provider.md). Die meisten Anbieter (einschließlich des hier beschriebenen Anbieters) können jedoch die Standard Implementierung dieser Funktionalität verwenden, die von Windows PowerShell bereitgestellt wird.

Um Zugriff auf den Datenspeicher zu erhalten, muss der Anbieter die Methoden der [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Basisklasse implementieren. Weitere Informationen zum Implementieren dieser Methoden finden Sie unter [Erstellen eines Windows PowerShell-Laufwerks Anbieters](./creating-a-windows-powershell-drive-provider.md).

Zum Bearbeiten der Elemente eines Datenspeicher, z. b. zum erhalten, festlegen und Löschen von Elementen, muss der Anbieter die von der [System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Basisklasse bereitgestellten Methoden implementieren. Weitere Informationen zum Implementieren dieser Methoden finden Sie unter [Erstellen eines Windows PowerShell-Element Anbieters](./creating-a-windows-powershell-item-provider.md).

## <a name="retrieving-child-items"></a>Abrufen von untergeordneten Elementen

Zum Abrufen eines untergeordneten Elements muss der Windows PowerShell-Container Anbieter die [System. Management. Automation. Provider. containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) -Methode überschreiben, um Aufrufe aus dem Cmdlet "`Get-ChildItem`" zu unterstützen. Diese Methode ruft untergeordnete Elemente aus dem Datenspeicher ab und schreibt Sie als-Objekte in die Pipeline. Wenn der `recurse`-Parameter des Cmdlets angegeben ist, ruft die-Methode alle untergeordneten Elemente unabhängig von der Ebene ab, auf der Sie sich befinden. Wenn der `recurse`-Parameter nicht angegeben ist, ruft die-Methode nur eine einzelne Ebene von untergeordneten Elementen ab.

Hier ist die Implementierung der [System. Management. Automation. Provider. containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) -Methode für diesen Anbieter. Beachten Sie, dass diese Methode die untergeordneten Elemente in allen Datenbanktabellen abruft, wenn der Pfad die Access-Datenbank angibt, und die untergeordneten Elemente aus den Zeilen dieser Tabelle abruft, wenn der Pfad eine Datentabelle angibt.

```csharp
protected override void GetChildItems(string path, bool recurse)
{
    // If path represented is a drive then the children in the path are
    // tables. Hence all tables in the drive represented will have to be
    // returned
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table, path, true);

            // if the specified item exists and recurse has been set then
            // all child items within it have to be obtained as well
            if (ItemExists(path) && recurse)
            {
                GetChildItems(path + pathSeparator + table.Name, recurse);
            }
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get the table name, row number and type of path from the
        // path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Obtain all the rows within the table
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);
            WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
        }
        else
        {
            // In this case, the path specified is not valid
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L311-L362 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchilditems"></a>Dinge, die Sie beim Implementieren von getchilditems beachten sollten

Die folgenden Bedingungen können für Ihre Implementierung von [System. Management. Automation. Provider. containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)gelten:

- Wenn Sie die Anbieter Klasse definieren, kann ein Windows PowerShell-Container Anbieter die Anbieter Funktionen von expandwildcards, Filtern, einschließen oder Ausschließen von der [System. Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration deklarieren. In diesen Fällen muss die Implementierung der [System. Management. Automation. Provider. containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) -Methode sicherstellen, dass der Pfad, der an die-Methode übergeben wird, die Anforderungen der angegebenen Funktionen erfüllt. Zu diesem Zweck sollte die-Methode auf die entsprechende Eigenschaft zugreifen, z. b. die [System. Management. Automation. Provider. cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) -und [System. Management. Automation. Provider. cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) -Eigenschaften.

- Die Implementierung dieser Methode muss jede Art von Zugriff auf das Element berücksichtigen, das das Element für den Benutzer sichtbar machen könnte. Wenn ein Benutzer beispielsweise über den File System-Anbieter Schreibzugriff auf eine Datei hat (von Windows PowerShell bereitgestellt), aber nicht über Lesezugriff verfügt, ist die Datei noch vorhanden, und [System. Management. Automation. Provider. itemcmdletprovider. itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) gibt @no__ t-1. Ihre Implementierung erfordert möglicherweise das Überprüfen eines übergeordneten Elements, um festzustellen, ob das untergeordnete Element aufgelistet werden kann.

- Wenn Sie mehrere Elemente schreiben, kann die [System. Management. Automation. Provider. containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) -Methode einige Zeit in Anspruch nehmen. Sie können Ihren Anbieter so entwerfen, dass die Elemente mithilfe der [System. Management. Automation. Provider. cmdletprovider. Write-temuject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) -Methode nacheinander geschrieben werden. Mit dieser Technik werden die Elemente für den Benutzer in einem Stream angezeigt.

- Ihre Implementierung von [System. Management. Automation. Provider. containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ist dafür verantwortlich, eine unendliche Rekursion zu verhindern, wenn zirkuläre Verknüpfungen vorhanden sind, und wie. Eine entsprechende Beendigungs Ausnahme sollte ausgelöst werden, um eine solche Bedingung widerzuspiegeln.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>Anfügen dynamischer Parameter an das Cmdlet "Get-ChildItem"

Manchmal erfordert das `Get-ChildItem`-Cmdlet, das [System. Management. Automation. Provider. containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) aufruft, zusätzliche Parameter, die zur Laufzeit dynamisch angegeben werden. Um diese dynamischen Parameter bereitzustellen, muss der Windows PowerShell-Container Anbieter die [System. Management. Automation. Provider. containercmdletprovider. getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) -Methode implementieren. Diese Methode ruft dynamische Parameter für das Element an dem angezeigten Pfad ab und gibt ein Objekt zurück, das über Eigenschaften und Felder mit ähnlichen Attributen wie eine Cmdlet-Klasse oder ein [System. Management. Automation. runtimedefinedparameterdictionary verfügt.](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene-Objekt, um die Parameter dem `Get-ChildItem`-Cmdlet hinzuzufügen.

Diese Methode wird von diesem Windows PowerShell-Container Anbieter nicht implementiert. Der folgende Code ist jedoch die Standard Implementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>Abrufen von untergeordneten Elementnamen

Zum Abrufen der Namen von untergeordneten Elementen muss der Windows PowerShell-Container Anbieter die [System. Management. Automation. Provider. containercmdletprovider. getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) -Methode überschreiben, um Aufrufe des Cmdlets "`Get-ChildItem`" zu unterstützen, wenn dessen `Name` der-Parameter wird angegeben. Diese Methode ruft die Namen der untergeordneten Elemente für den angegebenen Pfad oder die untergeordneten Elementnamen für alle Container ab, wenn der `returnAllContainers`-Parameter des Cmdlets angegeben wird. Ein untergeordneter Name ist der Blatt Teil eines Pfads. Der untergeordnete Name für den Pfad c:\windows\system32\abc.dll lautet z. b. "ABC. dll". Der untergeordnete Name für das Verzeichnis c:\Windows\System32 lautet "System32".

Hier ist die Implementierung der [System. Management. Automation. Provider. containercmdletprovider. getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) -Methode für diesen Anbieter. Beachten Sie, dass die-Methode Tabellennamen abruft, wenn der angegebene Pfad die Zugriffs Datenbank (das Laufwerk) und die Zeilennummern angibt, wenn der Pfad eine Tabelle angibt.

```csharp
protected override void GetChildNames(string path,
                            ReturnContainers returnContainers)
{
    // If the path represented is a drive, then the child items are
    // tables. get the names of all the tables in the drive.
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table.Name, path, true);
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get type, table name and row number from path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Get all the rows in the table and then write out the
            // row numbers.
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row.RowNumber, path, false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);

            WriteItemObject(row.RowNumber, path, false);
        }
        else
        {
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildNames
```

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L369-L411 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchildnames"></a>Dinge, die Sie beim Implementieren von getchildnames beachten sollten

Die folgenden Bedingungen können für Ihre Implementierung von [System. Management. Automation. Provider. containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)gelten:

- Wenn Sie die Anbieter Klasse definieren, kann ein Windows PowerShell-Container Anbieter die Anbieter Funktionen von expandwildcards, Filtern, einschließen oder Ausschließen von der [System. Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration deklarieren. In diesen Fällen muss die Implementierung der [System. Management. Automation. Provider. containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) -Methode sicherstellen, dass der Pfad, der an die-Methode übergeben wird, die Anforderungen der angegebenen Funktionen erfüllt. Zu diesem Zweck sollte die-Methode auf die entsprechende Eigenschaft zugreifen, z. b. die [System. Management. Automation. Provider. cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) -und [System. Management. Automation. Provider. cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) -Eigenschaften.

  > [!NOTE]
  > Eine Ausnahme zu dieser Regel tritt auf, wenn der `returnAllContainers`-Parameter des Cmdlets angegeben wird. In diesem Fall sollte die-Methode jeden untergeordneten Namen für einen Container abrufen, auch wenn Sie nicht den Werten von [System. Management. Automation. Provider. cmdletprovider. Filter *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter) [entspricht. System. Management. Automation. Provider. cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)-oder [System. Management. Automation. Provider. cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) -Eigenschaften.

- Standardmäßig sollten über schreibungen dieser Methode keine Namen von Objekten abrufen, die im Allgemeinen für den Benutzer ausgeblendet sind, es sei denn, die [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft ist angegeben. Wenn der angegebene Pfad einen Container angibt, ist die [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft nicht erforderlich.

- Ihre Implementierung von [System. Management. Automation. Provider. containercmdletprovider. getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) ist dafür verantwortlich, eine unendliche Rekursion zu verhindern, wenn zirkuläre Verknüpfungen vorhanden sind, und wie. Eine entsprechende Beendigungs Ausnahme sollte ausgelöst werden, um eine solche Bedingung widerzuspiegeln.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>Anfügen dynamischer Parameter an das Cmdlet "Get-ChildItem" (Name)

Manchmal erfordert das Cmdlet "`Get-ChildItem`" (mit dem Parameter "`Name`") zusätzliche Parameter, die zur Laufzeit dynamisch angegeben werden. Um diese dynamischen Parameter bereitzustellen, muss der Windows PowerShell-Container Anbieter die [System. Management. Automation. Provider. containercmdletprovider. getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) -Methode implementieren. Diese Methode ruft die dynamischen Parameter für das Element am angezeigten Pfad ab und gibt ein Objekt zurück, das über Eigenschaften und Felder mit Attribut Attributen verfügt, die einer Cmdlet-Klasse oder einem [System. Management. Automation. runtimedefinedparameterdictionary ähneln. ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)-Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene-Objekt, um die Parameter dem `Get-ChildItem`-Cmdlet hinzuzufügen.

Diese Methode wird von diesem Anbieter nicht implementiert. Der folgende Code ist jedoch die Standard Implementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>Umbenennen von Elementen

Zum Umbenennen eines Elements muss ein Windows PowerShell-Container Anbieter die [System. Management. Automation. Provider. containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) -Methode überschreiben, um Aufrufe vom `Rename-Item`-Cmdlet zu unterstützen. Diese Methode ändert den Namen des Elements im angegebenen Pfad in den angegebenen neuen Namen. Der neue Name muss immer relativ zum übergeordneten Element (Container) sein.

Dieser Anbieter überschreibt nicht die [System. Management. Automation. Provider. containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) -Methode. Im folgenden finden Sie jedoch die Standard Implementierung.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>Dinge, die Sie beim Implementieren von RenameItem beachten sollten

Die folgenden Bedingungen können für Ihre Implementierung von [System. Management. Automation. Provider. containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)gelten:

- Wenn Sie die Anbieter Klasse definieren, kann ein Windows PowerShell-Container Anbieter die Anbieter Funktionen von expandwildcards, Filtern, einschließen oder Ausschließen von der [System. Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration deklarieren. In diesen Fällen muss die Implementierung der [System. Management. Automation. Provider. containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) -Methode sicherstellen, dass der Pfad, der an die-Methode übergeben wird, die Anforderungen der angegebenen Funktionen erfüllt. Zu diesem Zweck sollte die-Methode auf die entsprechende Eigenschaft zugreifen, z. b. die [System. Management. Automation. Provider. cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) -und [System. Management. Automation. Provider. cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) -Eigenschaften.

- Die [System. Management. Automation. Provider. containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) -Methode ist nur für die Änderung des Namens eines Elements und nicht für Verschiebe Vorgänge vorgesehen. Die Implementierung der-Methode sollte einen Fehler schreiben, wenn der Parameter "`newName`" Pfad Trennzeichen enthält oder andernfalls bewirkt, dass das Element seinen übergeordneten Speicherort ändert.

- Standardmäßig sollten über schreibungen dieser Methode Objekte nicht umbenennen, es sei denn, die [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft ist angegeben. Wenn der angegebene Pfad einen Container angibt, ist die [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft nicht erforderlich.

- Ihre Implementierung der [System. Management. Automation. Provider. containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) -Methode sollte [System. Management. Automation. Provider. cmdletprovider. rechtdprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) und den zugehörigen Rückgabewert vor vornehmen von Änderungen am Datenspeicher. Diese Methode wird verwendet, um die Ausführung eines Vorgangs zu bestätigen, wenn eine Änderung am Systemstatus vorgenommen wird, z. b. beim Umbenennen von Dateien. [System. Management. Automation. Provider. cmdletprovider. schuldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sendet den Namen der Ressource, die an den Benutzer geändert werden soll, wobei die Windows PowerShell-Laufzeit alle Befehlszeilen Einstellungen oder Einstellungs Variablen beim Bestimmen von Was angezeigt werden soll.

  Nachdem der [System. Management. Automation. Provider. cmdletprovider. tiondprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) -Befehl `true` zurückgegeben hat, sollte die [System. Management. Automation. Provider. containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) -Methode die [ System. Management. Automation. Provider. cmdletprovider. schuldcontinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) -Methode. Diese Methode sendet eine Meldung eine Bestätigungsmeldung an den Benutzer, um zusätzliche Feedback zu geben, um zu bestätigen, dass der Vorgang fortgesetzt werden soll. Ein Anbieter sollte [System. Management. Automation. Provider. cmdletprovider. undcontinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) als zusätzliche Überprüfung auf potenziell gefährliche System Änderungen abrufen.

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>Anfügen dynamischer Parameter an das Cmdlet Rename-Item

Manchmal erfordert das `Rename-Item`-Cmdlet zusätzliche Parameter, die zur Laufzeit dynamisch angegeben werden. Um diese dynamischen Parameter bereitzustellen, muss der Windows PowerShell-Container Anbieter die [System. Management. Automation. Provider. containercmdletprovider. renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) -Methode implementieren. Diese Methode ruft die Parameter für das Element an dem angezeigten Pfad ab und gibt ein Objekt zurück, das über Eigenschaften und Felder mit ähnlichen Attributen wie eine Cmdlet-Klasse oder ein [System. Management. Automation. runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) verfügt. Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene-Objekt, um die Parameter dem `Rename-Item`-Cmdlet hinzuzufügen.

Dieser Container Anbieter implementiert diese Methode nicht. Der folgende Code ist jedoch die Standard Implementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>Erstellen neuer Elemente

Um neue Elemente zu erstellen, muss ein Container Anbieter die [System. Management. Automation. Provider. containercmdletprovider. netwitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) -Methode implementieren, um Aufrufe vom `New-Item`-Cmdlet zu unterstützen. Diese Methode erstellt ein Datenelement, das sich unter dem angegebenen Pfad befindet. Der `type`-Parameter des Cmdlets enthält den Anbieter definierten Typ für das neue Element. Beispielsweise verwendet der File System-Anbieter einen `type`-Parameter mit dem Wert "file" oder "Directory". Der `newItemValue`-Parameter des Cmdlets gibt einen anbieterspezifischen Wert für das neue Element an.

Hier ist die Implementierung der [System. Management. Automation. Provider. containercmdletprovider. netwitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) -Methode für diesen Anbieter.

```csharp
protected override void NewItem( string path, string type,
                                 object newItemValue )
{
    // Create the new item here after
    // performing necessary validations
    //
    // WriteItemObject(newItemValue, path, false);

    // Example
    //
    // if (ShouldProcess(path, "new item"))
    // {
    //      // Create a new item and then call WriteObject
    //      WriteObject(newItemValue, path, false);
    // }

} // NewItem
```

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L939-L955 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-newitem"></a>Dinge, die Sie beim Implementieren von "netwitem

Die folgenden Bedingungen können für Ihre Implementierung von [System. Management. Automation. Provider. containercmdletprovider. netwitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)gelten:

- Die [System. Management. Automation. Provider. containercmdletprovider. netwitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) -Methode sollte einen Vergleich der im `type`-Parameter übergebenen Zeichenfolge ohne Beachtung der Groß-/Kleinschreibung durchführen. Außerdem sollten Sie mindestens mehrdeutige Übereinstimmungen zulassen. Beispielsweise ist für die Typen "file" und "Directory" nur der erste Buchstabe erforderlich, um die Eindeutigkeit zu unterscheiden. Wenn der `type`-Parameter einen Typ angibt, der vom Anbieter nicht erstellt werden kann, sollte die [System. Management. Automation. Provider. containercmdletprovider. netwitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) -Methode eine ArgumentException mit einer Meldung schreiben, die die Typen angibt, die der Anbieter Stelle.

- Für den Parameter "`newItemValue`" wird die Implementierung der [System. Management. Automation. Provider. containercmdletprovider. netwitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) -Methode empfohlen, um mindestens Zeichen folgen zu akzeptieren. Außerdem sollte Sie den Typ des Objekts akzeptieren, das von der [System. Management. Automation. Provider. itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) -Methode für denselben Pfad abgerufen wird. Die [System. Management. Automation. Provider. containercmdletprovider. netwitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) -Methode kann die [System. Management. Automation. LanguagePrimitives. ConvertTo *](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) -Methode verwenden, um Typen in den gewünschten Typ zu konvertieren.

- Ihre Implementierung der [System. Management. Automation. Provider. containercmdletprovider. netwitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) -Methode sollte [System. Management. Automation. Provider. cmdletprovider. rechtdprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) und den zugehörigen Rückgabewert vor vornehmen von Änderungen am Datenspeicher. Nachdem der [System. Management. Automation. Provider. cmdletprovider. schuldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) -Befehl true zurückgegeben hat, sollte die [System. Management. Automation. Provider. containercmdletprovider. netwitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) -Methode die [ System. Management. Automation. Provider. cmdletprovider. rechtdcontinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) -Methode als zusätzliche Überprüfung auf potenziell gefährliche Systemänderungen.

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>Anfügen dynamischer Parameter an das Cmdlet "New-Item"

Manchmal erfordert das `New-Item`-Cmdlet zusätzliche Parameter, die zur Laufzeit dynamisch angegeben werden. Um diese dynamischen Parameter bereitzustellen, muss der Container Anbieter die [System. Management. Automation. Provider. containercmdletprovider. netwitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) -Methode implementieren. Diese Methode ruft die Parameter für das Element an dem angezeigten Pfad ab und gibt ein Objekt zurück, das über Eigenschaften und Felder mit ähnlichen Attributen wie eine Cmdlet-Klasse oder ein [System. Management. Automation. runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) verfügt. Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene-Objekt, um die Parameter dem `New-Item`-Cmdlet hinzuzufügen.

Diese Methode wird von diesem Anbieter nicht implementiert. Der folgende Code ist jedoch die Standard Implementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>Entfernen von Elementen

Zum Entfernen von Elementen muss der Windows PowerShell-Anbieter die [System. Management. Automation. Provider. containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) -Methode überschreiben, um Aufrufe vom `Remove-Item`-Cmdlet zu unterstützen. Diese Methode löscht ein Element im angegebenen Pfad aus dem Datenspeicher. Wenn der `recurse`-Parameter des `Remove-Item`-Cmdlets auf `true` festgelegt ist, entfernt die Methode alle untergeordneten Elemente unabhängig von ihrer Ebene. Wenn der-Parameter auf `false` festgelegt ist, entfernt die-Methode nur ein einzelnes Element im angegebenen Pfad.

Dieser Anbieter unterstützt das Entfernen von Elementen nicht. Der folgende Code ist jedoch die Standard Implementierung von [System. Management. Automation. Provider. containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>Dinge, die Sie beim Implementieren von RemoveItem beachten sollten

Die folgenden Bedingungen können für Ihre Implementierung von [System. Management. Automation. Provider. containercmdletprovider. netwitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)gelten:

- Wenn Sie die Anbieter Klasse definieren, kann ein Windows PowerShell-Container Anbieter die Anbieter Funktionen von expandwildcards, Filtern, einschließen oder Ausschließen von der [System. Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration deklarieren. In diesen Fällen muss die Implementierung der [System. Management. Automation. Provider. containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) -Methode sicherstellen, dass der Pfad, der an die-Methode übergeben wird, die Anforderungen der angegebenen Funktionen erfüllt. Zu diesem Zweck sollte die-Methode auf die entsprechende Eigenschaft zugreifen, z. b. die [System. Management. Automation. Provider. cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) -und [System. Management. Automation. Provider. cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) -Eigenschaften.

- Standardmäßig sollten über schreibungen dieser Methode Objekte nicht entfernen, es sei denn, die [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft ist auf true festgelegt. Wenn der angegebene Pfad einen Container angibt, ist die [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft nicht erforderlich.

- Ihre Implementierung von [System. Management. Automation. Provider. containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) ist dafür verantwortlich, eine unendliche Rekursion zu verhindern, wenn zirkuläre Verknüpfungen vorhanden sind, und wie. Eine entsprechende Beendigungs Ausnahme sollte ausgelöst werden, um eine solche Bedingung widerzuspiegeln.

- Ihre Implementierung der [System. Management. Automation. Provider. containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) -Methode sollte [System. Management. Automation. Provider. cmdletprovider. rechtdprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) und den zugehörigen Rückgabewert vor vornehmen von Änderungen am Datenspeicher. Nachdem der [System. Management. Automation. Provider. cmdletprovider. tiondprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) -Befehl `true` zurückgegeben hat, sollte die [System. Management. Automation. Provider. containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) -Methode das [ System. Management. Automation. Provider. cmdletprovider. rechtdcontinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) -Methode als zusätzliche Überprüfung auf potenziell gefährliche Systemänderungen.

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>Anfügen dynamischer Parameter an das Cmdlet "Remove-Item"

Manchmal erfordert das `Remove-Item`-Cmdlet zusätzliche Parameter, die zur Laufzeit dynamisch angegeben werden. Um diese dynamischen Parameter bereitzustellen, muss der Container Anbieter die [System. Management. Automation. Provider. containercmdletprovider. removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) -Methode implementieren, um diese Parameter zu verarbeiten. Diese Methode ruft die dynamischen Parameter für das Element am angezeigten Pfad ab und gibt ein Objekt zurück, das über Eigenschaften und Felder mit Attribut Attributen verfügt, die einer Cmdlet-Klasse oder einem [System. Management. Automation. runtimedefinedparameterdictionary ähneln. ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)-Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene-Objekt, um die Parameter dem `Remove-Item`-Cmdlet hinzuzufügen.

Dieser Container Anbieter implementiert diese Methode nicht. Der folgende Code ist jedoch die Standard Implementierung von [System. Management. Automation. Provider. containercmdletprovider. removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>Abfragen von untergeordneten Elementen

Um festzustellen, ob untergeordnete Elemente im angegebenen Pfad vorhanden sind, muss der Windows PowerShell-Container Anbieter die [System. Management. Automation. Provider. containercmdletprovider. haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) -Methode überschreiben. Diese Methode gibt `true` zurück, wenn das Element über untergeordnete Elemente verfügt, und `false` andernfalls. Bei einem NULL-oder leeren Pfad betrachtet die Methode alle Elemente im Datenspeicher als untergeordnete Elemente und gibt `true` zurück.

Dies ist die außer Kraft setzung der [System. Management. Automation. Provider. containercmdletprovider. haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) -Methode. Wenn mehr als zwei Pfad Teile von der Hilfsmethode "chunkpath" erstellt werden, gibt die Methode `false` zurück, da nur ein Daten Bank Container und ein Tabellen Container definiert werden. Weitere Informationen zu dieser Hilfsmethode finden Sie unter [Erstellen eines Windows PowerShell-Element Anbieters](./creating-a-windows-powershell-item-provider.md)mithilfe der Methode "chunkpath".

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a>Dinge, die Sie beim Implementieren von haschilditems beachten sollten

Die folgenden Bedingungen können für Ihre Implementierung von [System. Management. Automation. Provider. containercmdletprovider. haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)gelten:

- Wenn der Container Anbieter einen Stamm verfügbar macht, der interessante Bereitstellungs Punkte enthält, sollte die Implementierung der [System. Management. Automation. Provider. containercmdletprovider. haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) -Methode `true` zurückgeben, wenn ein NULL-Wert oder ein leerer Wert die Zeichenfolge wird für den Pfad übermittelt.

## <a name="copying-items"></a>Kopieren von Elementen

Zum Kopieren von Elementen muss der Container Anbieter die [System. Management. Automation. Provider. containercmdletprovider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) -Methode implementieren, um Aufrufe vom `Copy-Item`-Cmdlet zu unterstützen. Diese Methode kopiert ein Datenelement von dem Speicherort, der durch den `path`-Parameter des Cmdlets angegeben wird, an den Speicherort, der durch den `copyPath`-Parameter angegeben wird. Wenn der `recurse`-Parameter angegeben wird, kopiert die-Methode alle unter Container. Wenn der-Parameter nicht angegeben wird, kopiert die-Methode nur eine einzelne Element Ebene.

Diese Methode wird von diesem Anbieter nicht implementiert. Der folgende Code ist jedoch die Standard Implementierung von [System. Management. Automation. Provider. containercmdletprovider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>Dinge, die Sie bei der Implementierung von CopyItem beachten sollten

Die folgenden Bedingungen können für Ihre Implementierung von [System. Management. Automation. Provider. containercmdletprovider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)gelten:

- Wenn Sie die Anbieter Klasse definieren, kann ein Windows PowerShell-Container Anbieter die Anbieter Funktionen von expandwildcards, Filtern, einschließen oder Ausschließen von der [System. Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration deklarieren. In diesen Fällen muss die Implementierung der [System. Management. Automation. Provider. containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) -Methode sicherstellen, dass der Pfad, der an die-Methode übergeben wird, die Anforderungen der angegebenen Funktionen erfüllt. Zu diesem Zweck sollte die-Methode auf die entsprechende Eigenschaft zugreifen, z. b. die [System. Management. Automation. Provider. cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) -und [System. Management. Automation. Provider. cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) -Eigenschaften.

- Standardmäßig sollten über schreibungen dieser Methode Objekte nicht über vorhandene Objekte kopieren, es sei denn, die [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft ist auf `true` festgelegt. Beispielsweise kopiert der File System-Anbieter nicht "c:\temp\abc.txt" über eine vorhandene c:\abc.txt-Datei, es sei denn, die [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft ist auf "`true`" festgelegt. Wenn der im Parameter "`copyPath`" angegebene Pfad vorhanden ist und einen Container angibt, ist die Eigenschaft " [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) " nicht erforderlich. In diesem Fall sollte [System. Management. Automation. Provider. containercmdletprovider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) das vom `path`-Parameter festgeschriebene Element in den Container kopieren, der durch den `copyPath`-Parameter als untergeordnetes Element angegeben wird.

- Ihre Implementierung von [System. Management. Automation. Provider. containercmdletprovider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) ist dafür verantwortlich, eine unendliche Rekursion zu verhindern, wenn zirkuläre Verknüpfungen vorhanden sind, und wie. Eine entsprechende Beendigungs Ausnahme sollte ausgelöst werden, um eine solche Bedingung widerzuspiegeln.

- Ihre Implementierung der [System. Management. Automation. Provider. containercmdletprovider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) -Methode sollte [System. Management. Automation. Provider. cmdletprovider. rechtdprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) und den zugehörigen Rückgabewert vor vornehmen von Änderungen am Datenspeicher. Nachdem der [System. Management. Automation. Provider. cmdletprovider. rudprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) -Befehl "true" zurückgegeben hat, sollte die [System. Management. Automation. Provider. containercmdletprovider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) -Methode das [ System. Management. Automation. Provider. cmdletprovider. rechtdcontinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) -Methode als zusätzliche Überprüfung auf potenziell gefährliche Systemänderungen. Weitere Informationen zum Aufrufen dieser Methoden finden Sie unter [Umbenennen von Elementen](#renaming-items).

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>Anfügen dynamischer Parameter an das Cmdlet "Copy-Item"

Manchmal erfordert das `Copy-Item`-Cmdlet zusätzliche Parameter, die zur Laufzeit dynamisch angegeben werden. Um diese dynamischen Parameter bereitzustellen, muss der Windows PowerShell-Container Anbieter die [System. Management. Automation. Provider. containercmdletprovider. copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) -Methode implementieren, um diese Parameter zu verarbeiten. Diese Methode ruft die Parameter für das Element an dem angezeigten Pfad ab und gibt ein Objekt zurück, das über Eigenschaften und Felder mit ähnlichen Attributen wie eine Cmdlet-Klasse oder ein [System. Management. Automation. runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) verfügt. Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene-Objekt, um die Parameter dem `Copy-Item`-Cmdlet hinzuzufügen.

Diese Methode wird von diesem Anbieter nicht implementiert. Der folgende Code ist jedoch die Standard Implementierung von [System. Management. Automation. Provider. containercmdletprovider. copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>Code Beispiel

Einen umfassenden Beispielcode finden Sie unter [AccessDbProviderSample04-Codebeispiel](./accessdbprovidersample04-code-sample.md).

## <a name="building-the-windows-powershell-provider"></a>Entwickeln des Windows PowerShell-Anbieters

Weitere Informationen finden [Sie unter Registrieren von Cmdlets, Anbietern und Host Anwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Testen des Windows PowerShell-Anbieters

Wenn Ihr Windows PowerShell-Anbieter bei Windows PowerShell registriert wurde, können Sie ihn testen, indem Sie die unterstützten Cmdlets in der Befehlszeile ausführen. Beachten Sie, dass die folgende Beispielausgabe eine fiktive Access-Datenbank verwendet.

1. Führen Sie das `Get-ChildItem`-Cmdlet aus, um die Liste der untergeordneten Elemente aus einer Customers-Tabelle in der Access-Datenbank abzurufen.

   ```powershell
   Get-ChildItem mydb:customers
   ```

   Die folgende Ausgabe wird angezeigt.

   ```output
   PSPath        : AccessDB::customers
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : True
   Data          : System.Data.DataRow
   Name          : Customers
   RowCount      : 91
   Columns       :
   ```

2. Führen Sie das Cmdlet "`Get-ChildItem`" erneut aus, um die Daten einer Tabelle abzurufen.

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   Die folgende Ausgabe wird angezeigt.

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. Verwenden Sie nun das Cmdlet "`Get-Item`", um die Elemente in Zeile 0 in der Datentabelle abzurufen.

   ```powershell
   Get-Item mydb:\customers\0
   ```

   Die folgende Ausgabe wird angezeigt.

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. Verwenden Sie `Get-Item`, um die Daten für die Elemente in Zeile 0 abzurufen.

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   Die folgende Ausgabe wird angezeigt.

   ```output
   CustomerID   : 1234
   CompanyName  : Fabrikam
   ContactName  : Eric Gruber
   ContactTitle : President
   Address      : 4567 Main Street
   City         : Buffalo
   Region       : NY
   PostalCode   : 98052
   Country      : USA
   Phone        : (425) 555-0100
   Fax          : (425) 555-0101
   ```

5. Verwenden Sie nun das Cmdlet "`New-Item`", um einer vorhandenen Tabelle eine Zeile hinzuzufügen. Der `Path`-Parameter gibt den vollständigen Pfad zur Zeile an und muss eine Zeilennummer angeben, die größer ist als die vorhandene Anzahl von Zeilen in der Tabelle. Der `Type`-Parameter gibt "Row" an, um den Typ des hinzu zufügenden Elements anzugeben. Schließlich gibt der Parameter "`Value`" eine durch Trennzeichen getrennte Liste von Spaltenwerten für die Zeile an.

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. Überprüfen Sie die Richtigkeit des Vorgangs des neuen Elements wie folgt.

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   Die folgende Ausgabe wird angezeigt.

   ```output
   ID        : 3
   FirstName : Eric
   LastName  : Gruber
   Email     : ericgruber@fabrikam.com
   Title     : President
   Company   : Fabrikam
   WorkPhone : (425) 555-0100
   Address   : 4567 Main Street
   City      : Buffalo
   State     : NY
   Zip       : 98052
   Country   : USA
   ```

## <a name="see-also"></a>Weitere Informationen

[Erstellen von Windows PowerShell-Anbietern](./how-to-create-a-windows-powershell-provider.md)

[Entwerfen Ihres Windows PowerShell-Anbieters](./designing-your-windows-powershell-provider.md)

[Implementieren eines Windows PowerShell-Anbieters für Elemente](./creating-a-windows-powershell-item-provider.md)

[Implementieren eines Windows PowerShell-navigationsanbieters](./creating-a-windows-powershell-navigation-provider.md)

[Registrieren von Cmdlets, Anbietern und Host Anwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell-Programmier Handbuch](./windows-powershell-programmer-s-guide.md)
