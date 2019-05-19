---
title: Erstellen eine Windows PowerShell-Containeranbieter | Microsoft-Dokumentation
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
ms.openlocfilehash: 9e7da13ff559e802d52df475f2a555baeeeef983
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855192"
---
# <a name="creating-a-windows-powershell-container-provider"></a>Erstellen eines Windows PowerShell-Containeranbieters

Dieses Thema beschreibt, wie Sie einen Windows PowerShell-Anbieter erstellen, der in Datenspeichern mit mehreren Ebenen arbeiten können. Für diesen Typ des Datenspeichers die oberste Ebene des Speichers die Stamm-Elemente enthält, und jeder nachfolgenden Ebene wird als Knoten der untergeordneten Elemente bezeichnet. Dadurch, dass des Benutzers auf diesen untergeordneten Knoten arbeiten, kann Benutzer über den Data Store hierarchisch interagieren.

Anbieter, die auf Datenspeicher mit mehreren Ebenen können werden als Windows PowerShell-Container-Anbieter bezeichnet. Bedenken Sie jedoch, dass eine Windows PowerShell-Containeranbieter nur, wenn ein Container (keine geschachtelten Container) mit der Elemente verwendet werden kann. Wenn geschachtelte Container sind, müssen Sie eine Windows PowerShell-Navigationsanbieter implementieren. Weitere Informationen zum Implementieren von Windows PowerShell-Navigationsanbieter finden Sie unter [erstellen eine Windows PowerShell-Navigationsanbieter](./creating-a-windows-powershell-navigation-provider.md).

> [!NOTE]
> Sie können die C# Quelldatei (AccessDBSampleProvider04.cs) für diesen Anbieter, die mit dem Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3.0-Laufzeitkomponenten. Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.
>
> Weitere Informationen zu anderen Implementierungen der Windows PowerShell-Anbieter, finden Sie unter [Entwerfen Ihrer Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md).

Die hier beschriebenen Windows PowerShell-Containeranbieter definiert die Datenbank als die einzelnen Container mit den Tabellen und Zeilen der Datenbank, definiert als Elemente des Containers.

> [!CAUTION]
> Denken Sie daran, dass dieser Entwurf einer Datenbank geht davon aus, die ein Feld mit der namens-ID und der Typ des Felds LongInteger ist.

## <a name="defining-a-windows-powershell-container-provider-class"></a>Definieren einer Windows PowerShell-Container-Klasse

Ein Windows PowerShell-Containeranbieter muss eine abgeleitete Klasse .NET definieren die [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) Basisklasse. Hier ist die Klassendefinition für die Windows PowerShell-Containeranbieter, die in diesem Abschnitt beschrieben.

```csharp
   [CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

Beachten Sie, die in dieser Klasse die Definition der [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) Attribut enthält zwei Parameter. Der erste Parameter gibt einen benutzerfreundlichen Namen für den Anbieter, der von Windows PowerShell verwendet wird. Der zweite Parameter gibt die spezifischen Windows PowerShell-Funktionen, die der Anbieter für die Windows PowerShell-Laufzeit während der befehlsverarbeitung verfügbar macht. Für diesen Anbieter sind keine bestimmten Windows PowerShell-Funktionen, die hinzugefügt werden.

## <a name="defining-base-functionality"></a>Definiert die grundlegenden Funktionen

Siehe [Entwerfen Ihrer Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) Klasse leitet sich von anderen Klassen, die bereitgestellt Funktionalität der anderen Anbieter. Aus diesem Grund muss ein Windows PowerShell-Containeranbieter, alle die Funktionalität von diesen Klassen definieren.

Zum Implementieren der Funktionalität, die sitzungsspezifischen Initialisierungsinformationen hinzufügen und Freigeben von Ressourcen, die vom Anbieter verwendet werden, finden Sie unter [erstellen einen einfachen Windows PowerShell-Anbieter](./creating-a-basic-windows-powershell-provider.md). Allerdings können die meisten Anbieter (einschließlich des hier beschriebenen Anbieters) die standardmäßige Implementierung dieser Funktionalität, die von Windows PowerShell bereitgestellt wird.

Um Zugriff auf den Datenspeicher zu erhalten, muss der Anbieter implementiert die Methoden der [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Basisklasse. Weitere Informationen zu diesen Methoden implementiert werden, finden Sie unter [erstellen eine Windows PowerShell-Laufwerk-Anbieter](./creating-a-windows-powershell-drive-provider.md).

Der Anbieter muss zum Bearbeiten der Elemente von einem Datenspeicher, z. B. abrufen, festlegen und Löschen von Elementen, die vom bereitgestellten Methoden implementieren die [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Basisklasse. Weitere Informationen zu diesen Methoden implementiert werden, finden Sie unter [erstellen eine Windows PowerShell-Elementanbieter](./creating-a-windows-powershell-item-provider.md).

## <a name="retrieving-child-items"></a>Abrufen von untergeordneten Elementen

Um ein untergeordnetes Element abzurufen, muss die Windows PowerShell-Containeranbieter überschreiben die [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) -Methode zur Unterstützung der Aufrufe von der `Get-ChildItem` Cmdlet. Diese Methode ruft die untergeordneten Elemente ab, aus dem Datenspeicher und schreibt sie in der Pipeline als Objekte. Wenn die `recurse` -Parameter des Cmdlets wird angegeben, wird die Methode ruft alle untergeordneten Objekte unabhängig davon, welche Zugriffsebene sie auf dem sind ab. Wenn die `recurse` Parameter nicht angegeben wird, die Methode ruft nur eine einzelne Ebene der untergeordneten Elemente ab.

Dies ist die Implementierung von der [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) Methode für diesen Anbieter. Beachten Sie, dass diese Methode ruft die untergeordneten Elemente in allen Datenbanktabellen ab, wenn der Pfad Gibt an, die Access-Datenbank, und ruft die untergeordneten Elemente aus den Zeilen der Tabelle ab, wenn der Pfad eine Datentabelle angibt.

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

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L311-L362 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchilditems"></a>Punkte zu beachten, die zum Implementieren von GetChildItems

Die folgenden Bedingungen für Ihre Implementierung der gelten möglicherweise [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Wenn die Provider-Klasse zu definieren, kann ein Windows PowerShell-Containeranbieter von Funktionen des Anbieters der ExpandWildcards, Filter, einschließen oder ausschließen, deklarieren die [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) Enumeration. In diesen Fällen die Implementierung der [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) Methode muss sicherstellen, dass der Pfad, an die Methode übergeben, die Anforderungen des angegebenen entspricht Funktionen. Zu diesem Zweck die Methode sollte Zugriff auf die entsprechende Eigenschaft, z. B. die [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) und [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) Eigenschaften.

- Die Implementierung dieser Methode sollte keinerlei Zugriff auf das Element berücksichtigt, die das Element für den Benutzer sichtbar machen können. Z. B. wenn ein Benutzer Schreibzugriff in eine Datei über der FileSystem-Anbieter (bereitgestellt durch Windows PowerShell), aber keinen Lesezugriff verfügt, die Datei noch vorhanden ist und [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) gibt `true`. Ihre Implementierung möglicherweise die Überprüfung eines übergeordneten Elements, um festzustellen, ob das untergeordnete Element aufgelistet werden kann.

- Wenn Sie mehrere Elemente schreiben die [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) Methode kann einige Zeit dauern. Sie können Ihren Anbieter, um die Elemente, die mithilfe von schreiben Entwerfen der [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) eine Methode zu einem Zeitpunkt. Mit diesem Verfahren werden die Elemente in einen Datenstrom an dem Benutzer angezeigt.

- Die Implementierung von [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ist verantwortlich für die Endlosschleife verhindern, wenn zirkuläre Links und ähnliches vorliegen. Eine entsprechende abschließende Ausnahme sollte ausgelöst werden, um eine solche Bedingung widerzuspiegeln.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>Das Cmdlet "Get-ChildItem" Anfügen dynamische Parameter

In einigen Fällen die `Get-ChildItem` -Cmdlet, das Aufrufe [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) erfordert zusätzliche Parameter, die dynamisch zur Laufzeit angegeben werden. Um diese dynamischen Parameter zu gewährleisten, muss die Windows PowerShell-Containeranbieter implementieren die [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) Methode. Diese Methode ruft die dynamischen Parameter für das Element am angegebenen Pfad ab und gibt ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene Objekt, um die Parameter zum Hinzufügen der `Get-ChildItem` Cmdlet.

Diese Windows-PowerShell-Containeranbieter implementiert diese Methode nicht. Der folgende Code ist jedoch die Standardimplementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>Abrufen von untergeordneten Elementnamen

Um die Namen der untergeordneten Elemente abzurufen, muss die Windows PowerShell-Containeranbieter überschreiben die [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) -Methode zur Unterstützung der Aufrufe von der `Get-ChildItem`Cmdlet bei der `Name` Parameter angegeben ist. Diese Methode ruft die Namen der untergeordneten Elemente für den angegebenen Pfad oder ein untergeordnetes Element-Namen, für alle Container ab, wenn die `returnAllContainers` -Parameter des Cmdlets angegeben ist. Der Name einer untergeordneten ist der Blattebene Teil eines Pfads. Beispielsweise ist der Name der untergeordneten für den Pfad c:\windows\system32\abc.dll "abc.dll". Der Name der untergeordneten für das Verzeichnis c:\windows\system32 ist "system32".

Dies ist die Implementierung von der [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) Methode für diesen Anbieter. Beachten Sie, dass die Methode ruft Tabellennamen ab, wenn der angegebene Pfad Gibt die Access-Datenbank (Laufwerk) und die Zeilennummern an, ob der Pfad eine Tabelle gibt.

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

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L369-L411 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchildnames"></a>Punkte zu beachten, die zum Implementieren von GetChildNames

Die folgenden Bedingungen für Ihre Implementierung der gelten möglicherweise [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Wenn die Provider-Klasse zu definieren, kann ein Windows PowerShell-Containeranbieter von Funktionen des Anbieters der ExpandWildcards, Filter, einschließen oder ausschließen, deklarieren die [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) Enumeration. In diesen Fällen die Implementierung der [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) Methode muss sicherstellen, dass der Pfad, an die Methode übergeben, die Anforderungen des angegebenen entspricht Funktionen. Zu diesem Zweck die Methode sollte Zugriff auf die entsprechende Eigenschaft, z. B. die [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) und [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) Eigenschaften.

  > [!NOTE]
  > Eine Ausnahme von dieser Regel tritt auf, wenn die `returnAllContainers` -Parameter des Cmdlets angegeben ist. In diesem Fall sollten die Methode einen beliebigen untergeordneten Namen für einen Container abrufen, selbst wenn er nicht, die Werte von übereinstimmt der [System.Management.Automation.Provider.Cmdletprovider.Filter*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include), oder [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) Eigenschaften.

- Standardmäßig überschreibt diese Methode sollte nicht abgerufen werden Namen von Objekten, die in der Regel vom Benutzer es sei denn, ausgeblendet sind die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft angegeben wird. Wenn der angegebene Pfad einen-Container angibt, dass die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) Eigenschaft ist nicht erforderlich.

- Die Implementierung von [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) ist verantwortlich für die Endlosschleife verhindern, wenn zirkuläre Links und ähnliches vorliegen. Eine entsprechende abschließende Ausnahme sollte ausgelöst werden, um eine solche Bedingung widerzuspiegeln.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>Anfügen von dynamischen Parametern an das Cmdlet "Get-ChildItem" (Name)

In einigen Fällen die `Get-ChildItem` Cmdlet (mit der `Name` Parameter) erfordert zusätzliche Parameter, die dynamisch zur Laufzeit angegeben werden. Um diese dynamischen Parameter zu gewährleisten, muss die Windows PowerShell-Containeranbieter implementieren die [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) Methode. Diese Methode ruft die dynamischen Parameter für das Element am angegebenen Pfad ab und gibt ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene Objekt, um die Parameter zum Hinzufügen der `Get-ChildItem` Cmdlet.

Dieser Anbieter wird diese Methode nicht implementiert. Der folgende Code ist jedoch die Standardimplementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>Umbenennen von Elementen

Um ein Element umzubenennen, muss eine Windows PowerShell-Containeranbieter überschreiben die [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) -Methode zur Unterstützung der Aufrufe von der `Rename-Item` Cmdlet. Diese Methode ändert den Namen des Elements am angegebenen Pfad auf den neuen Namen bereitgestellt. Der neue Name muss immer relativ zum übergeordneten Element (Container) sein.

Dieser Anbieter wird nicht überschrieben werden. die [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) Methode. Folgendes ist jedoch die Standardimplementierung.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>Punkte zu beachten, die zum Implementieren von RenameItem

Die folgenden Bedingungen für Ihre Implementierung der gelten möglicherweise [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):

- Wenn die Provider-Klasse zu definieren, kann ein Windows PowerShell-Containeranbieter von Funktionen des Anbieters der ExpandWildcards, Filter, einschließen oder ausschließen, deklarieren die [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) Enumeration. In diesen Fällen die Implementierung der [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) Methode muss sicherstellen, dass der Pfad, an die Methode übergeben, die Anforderungen des angegebenen entspricht Funktionen. Zu diesem Zweck die Methode sollte Zugriff auf die entsprechende Eigenschaft, z. B. die [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) und [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) Eigenschaften.

- Die [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) Methode ist für die Änderung des Namens der nur ein Element, und nicht für Move-Vorgänge vorgesehen. Ihre Implementierung der Methode einen Fehler schreiben sollten, wenn die `newName` Parameter Trennzeichen im Pfad enthält, oder möglicherweise andernfalls das Element, dessen übergeordneten Standort zu ändern.

- Standardmäßig überschreibt diese Methode sollte nicht umbenennen von Objekten, wenn die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft angegeben wird. Wenn der angegebene Pfad einen-Container angibt, dass die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) Eigenschaft ist nicht erforderlich.

- Die Implementierung von der [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) Methodenaufruf sollten [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) , und überprüfen Sie den Rückgabewert, bevor Änderungen an den Datenspeicher. Diese Methode wird verwendet, um die Ausführung eines Vorgangs zu bestätigen, wenn ein Systemstatus, z. B. Änderung Umbenennen von Dateien. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sendet den Namen der Ressource, die für den Benutzer geändert werden, mit der Windows PowerShell-Laufzeit berücksichtigt alle über die befehlszeileneinstellungen oder der Preference-Variablen in bestimmen, was angezeigt werden soll.

  Nach dem Aufruf von [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) gibt `true`, [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) Methodenaufruf sollte die [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) Methode. Diese Methode sendet einer Nachricht eine bestätigungsmeldung an den Benutzer können Sie zusätzliches Feedback zu sagen, wenn der Vorgang fortgesetzt werden soll. Ein Anbieter sollte [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) als eine zusätzliche Überprüfung auf potenziell gefährliche systemmodifizierungen.

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>Anfügen von dynamischen Parametern an das Cmdlet Rename-Item

In einigen Fällen die `Rename-Item` Cmdlet erfordert zusätzliche Parameter, die dynamisch zur Laufzeit angegeben werden. Um diese dynamischen Parameter zu gewährleisten, muss Windows PowerShell-Containeranbieter implementieren die [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) Methode. Diese Methode ruft die Parameter für das Element am angegebenen Pfad ab und gibt ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene Objekt, um die Parameter zum Hinzufügen der `Rename-Item` Cmdlet.

Dieser Containeranbieter implementiert diese Methode nicht. Der folgende Code ist jedoch die Standardimplementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>Erstellen von neuen Elementen

Um neue Elemente erstellen zu können, muss ein Containeranbieter implementieren die [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) -Methode zur Unterstützung der Aufrufe von der `New-Item` Cmdlet. Diese Methode erstellt ein Datenelement im angegebenen Pfad. Die `type` -Parameter des Cmdlets enthält, den Anbieter definierte Typ für das neue Element. Der FileSystem-Anbieter verwendet z. B. eine `type` Parameter mit dem Wert "File" oder "Directory". Die `newItemValue` -Parameter des Cmdlets gibt einen anbieterspezifischen Wert für das neue Element an.

Dies ist die Implementierung von der [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) Methode für diesen Anbieter.

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

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L939-L955 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-newitem"></a>Punkte zu beachten, die zum Implementieren von NewItem

Die folgenden Bedingungen für Ihre Implementierung der gelten möglicherweise [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- Die [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) Methode führen Sie einen Vergleich der übergebenen Zeichenfolge Groß-/Kleinschreibung sollte die `type` Parameter. Es sollte auch für mindestens mehrdeutig Übereinstimmungen zulassen. Beispielsweise ist für die Typen "File" und "Directory", nur der erste Buchstaben erforderlich, um zu unterscheiden. Wenn die `type` Parameter gibt an, einen Typ, der Ihrem Anbieter kann nicht erstellt werden, die [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) Methode sollte eine ArgumentException mit einer Nachricht schreiben der angibt, der Types kann der Anbieter erstellen.

- Für die `newItemValue` -Parameter, die Implementierung der [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) Methode wird empfohlen, um Zeichenfolgen, die auf ein Minimum zu akzeptieren. Sie sollten auch den Typ des Objekts, die von abgerufen akzeptieren die [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) -Methode für den gleichen Pfad. Die [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) Methode können die [System.Management.Automation.Languageprimitives.Convertto*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) Methode zum Konvertieren von Typen, für die der gewünschte Typ.

- Die Implementierung von der [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) Methodenaufruf sollten [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) , und überprüfen Sie den Rückgabewert, bevor Änderungen an den Datenspeicher. Nach dem Aufruf von [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) gibt true zurück, die [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) -Methode aufrufen, sollte die [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) Methode als eine zusätzliche Überprüfung auf potenziell gefährliche System Änderungen.

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>Das Cmdlet "New-Item" Anfügen dynamische Parameter

In einigen Fällen die `New-Item` Cmdlet erfordert zusätzliche Parameter, die dynamisch zur Laufzeit angegeben werden. Um diese dynamischen Parameter zu gewährleisten, muss der Containeranbieter implementieren die [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) Methode. Diese Methode ruft die Parameter für das Element am angegebenen Pfad ab und gibt ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene Objekt, um die Parameter zum Hinzufügen der `New-Item` Cmdlet.

Dieser Anbieter wird diese Methode nicht implementiert. Der folgende Code ist jedoch die Standardimplementierung dieser Methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>Entfernen von Elementen

Zum Entfernen von Elementen der Windows PowerShell-Anbieter außer Kraft setzen muss die [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) -Methode zur Unterstützung der Aufrufe von der `Remove-Item` Cmdlet. Diese Methode löscht ein Element aus dem Datenspeicher im angegebenen Pfad. Wenn die `recurse` Parameter, der die `Remove-Item` Cmdlet nastaven NA hodnotu `true`, die-Methode entfernt alle untergeordneten Elemente unabhängig von der Ebene. Wenn der Parameter, um festgelegt ist `false`, die Methode wird nur ein einziges Element am angegebenen Pfad entfernt.

Dieser Anbieter unterstützt nicht das Entfernen eines Elements. Der folgende Code ist jedoch die standardmäßige Implementierung des [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>Punkte zu beachten, die zum Implementieren von RemoveItem

Die folgenden Bedingungen für Ihre Implementierung der gelten möglicherweise [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- Wenn die Provider-Klasse zu definieren, kann ein Windows PowerShell-Containeranbieter von Funktionen des Anbieters der ExpandWildcards, Filter, einschließen oder ausschließen, deklarieren die [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) Enumeration. In diesen Fällen die Implementierung der [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) Methode muss sicherstellen, dass der Pfad, an die Methode übergeben, die Anforderungen des angegebenen entspricht Funktionen. Zu diesem Zweck die Methode sollte Zugriff auf die entsprechende Eigenschaft, z. B. die [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) und [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) Eigenschaften.

- Standardmäßig überschreibt diese Methode sollte nicht entfernen, Objekte, sofern die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaftensatz auf "true". Wenn der angegebene Pfad einen-Container angibt, dass die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) Eigenschaft ist nicht erforderlich.

- Die Implementierung von [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) ist verantwortlich für die Endlosschleife verhindern, wenn zirkuläre Links und ähnliches vorliegen. Eine entsprechende abschließende Ausnahme sollte ausgelöst werden, um eine solche Bedingung widerzuspiegeln.

- Die Implementierung von der [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) Methodenaufruf sollten [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) , und überprüfen Sie den Rückgabewert, bevor Änderungen an den Datenspeicher. Nach dem Aufruf von [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) gibt `true`, [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) Methodenaufruf sollte die [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) Methode als eine zusätzliche Überprüfung auf potenziell gefährliche System Änderungen.

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>Das Cmdlet "Remove-Item" Anfügen dynamische Parameter

In einigen Fällen die `Remove-Item` Cmdlet erfordert zusätzliche Parameter, die dynamisch zur Laufzeit angegeben werden. Um diese dynamischen Parameter zu gewährleisten, muss der Containeranbieter implementieren die [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) Methode, um diese Parameter zu verarbeiten. Diese Methode ruft die dynamischen Parameter für das Element am angegebenen Pfad ab und gibt ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene Objekt, um die Parameter zum Hinzufügen der `Remove-Item` Cmdlet.

Dieser Containeranbieter implementiert diese Methode nicht. Der folgende Code ist jedoch die standardmäßige Implementierung des [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>Abfragen von untergeordneten Elementen

Um zu überprüfen, um festzustellen, ob die untergeordneten Elemente im angegebenen Pfad vorhanden sind, muss die Windows PowerShell-Containeranbieter überschreiben die [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) Methode. Diese Methode gibt `true` verfügt das Element untergeordnete Elemente und `false` andernfalls. Für einen Pfad null oder leer sein, die Methode alle Elemente im Datenspeicher als untergeordnete Elemente berücksichtigt, und gibt `true`.

Hier ist die Außerkraftsetzung für die [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) Methode. Wenn mehr als zwei Pfad teilen, die mit der Hilfsmethode ChunkPath erstellt sind, gibt die Methode `false`, da nur ein Datenbankcontainer und einen Tabellencontainer definiert sind. Weitere Informationen über diese Hilfsmethode finden Sie unter die Methode ChunkPath ausführlicher [erstellen eine Windows PowerShell-Elementanbieter](./creating-a-windows-powershell-item-provider.md).

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a>Punkte zu beachten, die zum Implementieren von HasChildItems

Die folgenden Bedingungen für Ihre Implementierung der gelten möglicherweise [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):

- Wenn der Containeranbieter einen Stamm verfügbar macht, die interessant, die Implementierung von Bereitstellungspunkten der [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) Methode sollte zurückgeben`true`Wenn ein NULL-Wert oder eine leere Zeichenfolge übergeben wird den Pfad.

## <a name="copying-items"></a>Kopieren von Elementen

Zum Kopieren von Elementen der Containeranbieter implementieren muss die [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) -Methode zur Unterstützung der Aufrufe von der `Copy-Item` Cmdlet. Diese Methode kopiert ein Datenelement aus dessen Speicherort vom die `path` Parameter des Cmdlets, um dessen Speicherort vom die `copyPath` Parameter. Wenn die `recurse` -Parameter angegeben wird, die Methode werden alle untergeordneten Container kopiert. Wenn der Parameter nicht angegeben wird, kopiert die Methode nur eine einzelne Ebene von Elementen an.

Dieser Anbieter wird diese Methode nicht implementiert. Der folgende Code ist jedoch die standardmäßige Implementierung des [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>Punkte zu beachten, die zur Implementierung von CopyItem

Die folgenden Bedingungen für Ihre Implementierung der gelten möglicherweise [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):

- Wenn die Provider-Klasse zu definieren, kann ein Windows PowerShell-Containeranbieter von Funktionen des Anbieters der ExpandWildcards, Filter, einschließen oder ausschließen, deklarieren die [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) Enumeration. In diesen Fällen die Implementierung der [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) Methode muss sicherstellen, dass der Pfad, an die Methode übergeben, die Anforderungen des angegebenen entspricht Funktionen. Zu diesem Zweck die Methode sollte Zugriff auf die entsprechende Eigenschaft, z. B. die [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) und [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) Eigenschaften.

- Standardmäßig überschreibt diese Methode sollte nicht kopieren Objekte über vorhandene Objekte, wenn die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaftensatz auf `true`. Z. B. der FileSystem-Anbieter werden nicht kopiert c:\temp\abc.txt über eine vorhandene c:\abc.txt-Datei, wenn die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaftensatz auf `true`. Wenn der Pfad, in angegeben der `copyPath` Parameter vorhanden ist, und gibt einen Container, der [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) Eigenschaft ist nicht erforderlich. In diesem Fall [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) sollten das Element, angegeben durch Kopieren der `path` Parameter, um den Container angegeben wird, durch die `copyPath` Parameter als ein untergeordnetes Element.

- Die Implementierung von [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) ist verantwortlich für die Endlosschleife verhindern, wenn zirkuläre Links und ähnliches vorliegen. Eine entsprechende abschließende Ausnahme sollte ausgelöst werden, um eine solche Bedingung widerzuspiegeln.

- Die Implementierung von der [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) Methodenaufruf sollten [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) , und überprüfen Sie den Rückgabewert, bevor Änderungen an den Datenspeicher. Nach dem Aufruf von [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) gibt true zurück, die [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) -Methode aufrufen, sollte die [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) Methode als eine zusätzliche Überprüfung auf potenziell gefährliche System Änderungen. Weitere Informationen zum Aufrufen dieser Methoden finden Sie unter [Elemente umbenennen](#renaming-items).

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>Anfügen von dynamischen Parametern an die Copy-Item-Cmdlet

In einigen Fällen die `Copy-Item` Cmdlet erfordert zusätzliche Parameter, die dynamisch zur Laufzeit angegeben werden. Um diese dynamischen Parameter zu gewährleisten, muss die Windows PowerShell-Containeranbieter implementieren die [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) Methode, um diese zu verarbeiten Parameter. Diese Methode ruft die Parameter für das Element am angegebenen Pfad ab und gibt ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene Objekt, um die Parameter zum Hinzufügen der `Copy-Item` Cmdlet.

Dieser Anbieter wird diese Methode nicht implementiert. Der folgende Code ist jedoch die standardmäßige Implementierung des [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>Codebeispiel

Vollständigen Beispielcode finden Sie unter [AccessDbProviderSample04 Codebeispiel](./accessdbprovidersample04-code-sample.md).

## <a name="building-the-windows-powershell-provider"></a>Erstellen den Windows PowerShell-Anbieter

Finden Sie unter [so registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Testen der Windows PowerShell-Anbieter

Bei Ihrem Windows PowerShell-Anbieter mit Windows PowerShell registriert wurde, können Sie es testen, indem die unterstützten Cmdlets in der Befehlszeile ausgeführt. Denken Sie daran, dass die Ausgabe des folgenden Beispiels eine fiktive Access-Datenbank verwendet.

1. Führen Sie die `Get-ChildItem` -Cmdlet zum Abrufen der Liste der untergeordneten Elemente aus einer Customers-Tabelle in der Access-Datenbank.

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

2. Führen Sie die `Get-ChildItem` Cmdlet erneut aus, um die Daten einer Tabelle abzurufen.

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

3. Verwenden Sie jetzt die `Get-Item` Cmdlet, um die Elemente in Zeile 0 in der Datentabelle abgerufen werden sollen.

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

4. Wiederverwenden `Get-Item` zum Abrufen der Daten für die Elemente in Zeile 0.

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

5. Verwenden Sie jetzt die `New-Item` Cmdlet, um einer vorhandenen Tabelle eine Zeile hinzuzufügen. Die `Path` Parameter gibt den vollständigen Pfad zu der Zeile, und muss eine Zeilennummer angeben, die größer als die vorhandene Anzahl der Zeilen in der Tabelle ist. Die `Type` Parameter gibt an, "Zeile", um die den Typ des hinzuzufügenden Elements angeben. Zum Schluss die `Value` Parameter gibt eine durch Trennzeichen getrennte Liste der Spaltenwerte für die Zeile an.

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. Überprüfen Sie die Richtigkeit des neuen Elements Vorgangs wie folgt aus.

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

[Erstellen von Windows PowerShell-Anbieter](./how-to-create-a-windows-powershell-provider.md)

[Entwerfen Ihre Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md)

[Implementieren eine Windows PowerShell-Elementanbieter](./creating-a-windows-powershell-item-provider.md)

[Implementieren eine Windows PowerShell-Navigationsanbieter](./creating-a-windows-powershell-navigation-provider.md)

[So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell Handbuch für Programmierer](./windows-powershell-programmer-s-guide.md)