---
title: Schreiben eines Element Anbieters | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: 12d2cb8c40c9fd6278bb964a6259d03167536195
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359879"
---
# <a name="writing-an-item-provider"></a>Schreiben eines Elementanbieters

In diesem Thema wird beschrieben, wie die Methoden eines Windows PowerShell-Anbieters implementiert werden, die auf Elemente im Datenspeicher zugreifen und diese bearbeiten. Um auf Elemente zugreifen zu können, muss ein Anbieter von der [System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Klasse abgeleitet werden.

Für den Anbieter in den Beispielen in diesem Thema wird eine Access-Datenbank als Datenspeicher verwendet. Es gibt mehrere Hilfsmethoden und-Klassen, die für die Interaktion mit der Datenbank verwendet werden. Das komplette Beispiel, das die Hilfsmethoden enthält, finden Sie unter [AccessDBProviderSample03](./accessdbprovidersample03.md)

Weitere Informationen zu Windows PowerShell-Anbietern finden Sie unter Übersicht über den [Windows PowerShell-Anbieter](./windows-powershell-provider-overview.md).

## <a name="implementing-item-methods"></a>Implementieren von Element Methoden

Die [System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Klasse stellt mehrere Methoden bereit, die verwendet werden können, um auf die Elemente in einem Datenspeicher zuzugreifen und diese zu bearbeiten. Eine umfassende Liste dieser Methoden finden Sie unter [itemcmdletprovider-Methoden](/dotnet/api/system.management.automation.provider.itemcmdletprovider?view=pscore-6.2.0#methods). In diesem Beispiel werden vier dieser Methoden implementiert. [System. Management. Automation. Provider. itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) Ruft ein Element an einem angegebenen Pfad ab. [System. Management. Automation. Provider. itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) legt den Wert des angegebenen Elements fest. [System. Management. Automation. Provider. itemcmdletprovider. itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) überprüft, ob ein Element im angegebenen Pfad vorhanden ist. [System. Management. Automation. Provider. itemcmdletprovider. IsValidPath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) überprüft einen Pfad, um festzustellen, ob er einem Speicherort im Datenspeicher zugeordnet ist.

> [!NOTE]
> Dieses Thema baut auf den Informationen in der Schnellstartanleitung für den [Windows PowerShell-Anbieter](./windows-powershell-provider-quickstart.md)auf. Dieses Thema behandelt nicht die Grundlagen der Einrichtung eines Anbieter Projekts oder die Implementierung der Methoden, die von der [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Klasse geerbt werden, die Laufwerke erstellt und entfernt.

### <a name="declaring-the-provider-class"></a>Deklarieren der Anbieter Klasse

Deklarieren Sie den Anbieter so, dass er von der [System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Klasse abgeleitet wird, und versehen Sie ihn mit dem [System. Management. Automation. Provider. cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>Implementieren von GetItem

Das [System. Management. Automation. Provider. itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) wird von der PowerShell-Engine aufgerufen, wenn ein Benutzer das [Microsoft. PowerShell. Commands. getitemcommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) -Cmdlet für Ihren Anbieter aufruft. Die-Methode gibt das Element am angegebenen Pfad zurück. Im Beispiel Access Database überprüft die-Methode, ob es sich bei dem Element um das Laufwerk selbst, eine Tabelle in der Datenbank oder eine Zeile in der Datenbank handelt. Die-Methode sendet das Element an das PowerShell-Modul, indem Sie die [System. Management. Automation. Provider. cmdletprovider. Write teitemabject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) -Methode aufrufen.

```csharp
protected override void GetItem(string path)
      {
          // check if the path represented is a drive
          if (PathIsDrive(path))
          {
              WriteItemObject(this.PSDriveInfo, path, true);
              return;
          }// if (PathIsDrive...

           // Get table name and row information from the path and do
           // necessary actions
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               DatabaseTableInfo table = GetTable(tableName);
               WriteItemObject(table, path, true);
           }
           else if (type == PathType.Row)
           {
               DatabaseRowInfo row = GetRow(tableName, rowNumber);
               WriteItemObject(row, path, false);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

### <a name="implementing-setitem"></a>Implementieren von "System Item"

Die [System. Management. Automation. Provider. itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) -Methode wird von den PowerShell-Engine-aufrufen aufgerufen, wenn ein Benutzer das [Microsoft. PowerShell. Commands. setitemcommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) -Cmdlet aufruft. Er legt den Wert des Elements im angegebenen Pfad fest.

Im Beispiel der Access-Datenbank ist es sinnvoll, den Wert eines Elements nur dann festzulegen, wenn das Element eine Zeile ist. Daher löst die Methode [NotSupportedException](/dotnet/api/system.notsupportedexception?view=netframework-4.8) aus, wenn das Element keine Zeile ist.

```csharp
protected override void SetItem(string path, object values)
       {
           // Get type, table name and row number from the path specified
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type != PathType.Row)
           {
               WriteError(new ErrorRecord(new NotSupportedException(
                     "SetNotSupported"), "",
                  ErrorCategory.InvalidOperation, path));

               return;
           }

           // Get in-memory representation of table
           OdbcDataAdapter da = GetAdapterForTable(tableName);

           if (da == null)
           {
               return;
           }
           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           if (rowNumber >= table.Rows.Count)
           {
               // The specified row number has to be available. If not
               // NewItem has to be used to add a new row
               throw new ArgumentException("Row specified is not available");
           } // if (rowNum...

           string[] colValues = (values as string).Split(',');

           // set the specified row
           DataRow row = table.Rows[rowNumber];

           for (int i = 0; i < colValues.Length; i++)
           {
               row[i] = colValues[i];
           }

           // Update the table
           if (ShouldProcess(path, "SetItem"))
           {
               da.Update(ds, tableName);
           }

       }
```

### <a name="implementing-itemexists"></a>Implementieren von itemexists

Die [System. Management. Automation. Provider. itemcmdletprovider. itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) -Methode wird von der PowerShell-Engine aufgerufen, wenn ein Benutzer das [Microsoft. PowerShell. Commands. testpathcommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) -Cmdlet aufruft. Die-Methode bestimmt, ob ein Element am angegebenen Pfad vorhanden ist. Wenn das Element vorhanden ist, übergibt die Methode es durch Aufrufen von [System. Management. Automation. Provider. cmdletprovider. Write](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)Element Item * an das PowerShell-Modul.

```csharp
protected override bool ItemExists(string path)
       {
           // check if the path represented is a drive
           if (PathIsDrive(path))
           {
               return true;
           }

           // Obtain type, table name and row number from path
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           DatabaseTableInfo table = GetTable(tableName);

           if (type == PathType.Table)
           {
               // if specified path represents a table then DatabaseTableInfo
               // object for the same should exist
               if (table != null)
               {
                   return true;
               }
           }
           else if (type == PathType.Row)
           {
               // if specified path represents a row then DatabaseTableInfo should
               // exist for the table and then specified row number must be within
               // the maximum row count in the table
               if (table != null && rowNumber < table.RowCount)
               {
                   return true;
               }
           }

           return false;

       }
```

### <a name="implementing-isvalidpath"></a>Implementieren von IsValidPath

Die [System. Management. Automation. Provider. itemcmdletprovider. IsValidPath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) -Methode überprüft, ob der angegebene Pfad für den aktuellen Anbieter syntaktisch gültig ist. Es wird nicht überprüft, ob ein Element im Pfad vorhanden ist.

```csharp
protected override bool IsValidPath(string path)
       {
           bool result = true;

           // check if the path is null or empty
           if (String.IsNullOrEmpty(path))
           {
               result = false;
           }

           // convert all separators in the path to a uniform one
           path = NormalizePath(path);

           // split the path into individual chunks
           string[] pathChunks = path.Split(pathSeparator.ToCharArray());

           foreach (string pathChunk in pathChunks)
           {
               if (pathChunk.Length == 0)
               {
                   result = false;
               }
           }
           return result;
       }
```

## <a name="next-steps"></a>Nächste Schritte

Ein typischer Real-World-Anbieter ist in der Lage, Elemente zu unterstützen, die andere Elemente enthalten, und Elemente innerhalb des Laufwerks von einem Pfad zu einem anderen zu verschieben. Ein Beispiel für einen Anbieter, der Container unterstützt, finden Sie unter [Schreiben eines Container Anbieters](./writing-a-container-provider.md). Ein Beispiel für einen Anbieter, der das Verschieben von Elementen unterstützt, finden Sie unter [Schreiben eines navigationsanbieters](./writing-a-navigation-provider.md).

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Container Anbieters](./writing-a-container-provider.md)

[Schreiben eines navigationsanbieters](./writing-a-navigation-provider.md)

[Windows PowerShell-Anbieter (Übersicht)](./windows-powershell-provider-overview.md)
