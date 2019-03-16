---
title: Schreiben eines Datenanbieters Artikel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: 9285a2f0e673de8b86084157423512bdeeda109d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058187"
---
# <a name="writing-an-item-provider"></a>Schreiben eines Elementanbieters

In diesem Thema wird beschrieben, wie die Methoden von einem Windows PowerShell-Anbieter implementiert, die Zugriff auf, und ändern die Elemente im Datenspeicher. Um auf Elemente zugreifen können, muss ein Anbieter von abgeleitet werden die [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse.

Der Anbieter in den Beispielen in diesem Thema verwendet eine Access-Datenbank als Datenspeicher. Es gibt mehrere Hilfsmethoden und Klassen, die verwendet werden, um die Interaktion mit der Datenbank. Das vollständige Beispiel, das die Hilfsmethoden enthält, finden Sie unter [AccessDBProviderSample03](./accessdbprovidersample03.md)

Weitere Informationen zu Windows PowerShell-Anbietern finden Sie unter [Übersicht über Windows PowerShell-Anbieter](./windows-powershell-provider-overview.md).

## <a name="implementing-item-methods"></a>Implementierungsmethoden-Element

Die [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse stellt mehrere Methoden, die zum zugreifen und diese bearbeiten die Elemente in einem Datenspeicher verwendet werden können. Eine vollständige Liste der folgenden Methoden, finden Sie unter [ItemCmdletProvider Methoden](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx). In diesem Beispiel werden wir vier der folgenden Methoden implementieren. [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) Ruft ein Element in einem angegebenen Pfad ab. [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) legt den Wert des angegebenen Elements fest. [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) überprüft, ob ein Element am angegebenen Pfad vorhanden ist. [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) überprüft einen Pfad, um festzustellen, ob es an einem Speicherort im Datenspeicher zugeordnet.

> [!NOTE]
> Dieses Thema baut auf den Informationen in [Schnellstartanleitung zu Windows PowerShell-Anbieter](./windows-powershell-provider-quickstart.md). Dieses Thema deckt sich nicht auf die Grundlagen zum Einrichten eines Anbieter-Projekts und Gewusst wie: Implementieren der Methoden geerbt von der [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Klasse, die erstellen und Entfernen von Laufwerken.

### <a name="declaring-the-provider-class"></a>Die Anbieterklasse deklarieren

Deklarieren Sie den Anbieter für die Ableitung der [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse, und versehen Sie sie mit der [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>GetItem implementieren

Die [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) wird von der PowerShell-Engine aufgerufen, wenn ein Benutzer aufruft der [Microsoft.PowerShell.Commands.Get-Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) -Cmdlet für Ihre Anbieter. Die Methode gibt das Element am angegebenen Pfad zurück. In der Access-Datenbank beispielsweise überprüft die Methode an, ob das Element dem Laufwerk selbst, eine Tabelle in der Datenbank oder eine Zeile in der Datenbank. Die-Methode sendet das Element an der PowerShell-Engine, durch Aufrufen der [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) Methode.

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

### <a name="implementing-setitem"></a>Implementieren von SetItem

Die [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) Methode wird von der PowerShell-Engine ruft aufgerufen, wenn ein Benutzer ruft die [Microsoft.PowerShell.Commands.Set-Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) Cmdlet . Es wird der Wert des Elements an, unter dem angegebenen Pfad.

In der Access-Datenbank beispielsweise ist es sinnvoll, Sie legen Sie den Wert eines Elements aus, nur dann, wenn das Element eine Zeile ist, sodass die Methode löst [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) Wenn das Element ist keine Zeile.

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

### <a name="implementing-itemexists"></a>Implementieren von ItemExists

Die [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) Methode wird von der PowerShell-Engine aufgerufen, wenn ein Benutzer ruft die [Microsoft.PowerShell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) Cmdlet. Die Methode bestimmt, ob ein Element am angegebenen Pfad vorhanden ist. Wenn das Element vorhanden ist, die Methode übergibt sie an der PowerShell-Engine durch Aufrufen von [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).

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

Die [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) Methode überprüft, ob der angegebene Pfad für den aktuellen Anbieter syntaktisch gültig ist. Es wird nicht überprüft, ob ein Element im Pfad vorhanden ist.

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

Ein typische realen-Anbieter ist für die Unterstützung von Elementen, die anderen Elemente enthalten, und Verschieben von Elementen aus einem Pfad zu einem anderen in das Laufwerk kann. Ein Beispiel für einen Anbieter, Container unterstützt, finden Sie unter [Schreiben eines Anbieters Container](./writing-a-container-provider.md). Ein Beispiel für einen Anbieter, Verschieben von Elementen unterstützt, finden Sie unter [Schreiben eines Anbieters für die Navigation](./writing-a-navigation-provider.md).

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Anbieters für container](./writing-a-container-provider.md)

[Schreiben eines Anbieters für die navigation](./writing-a-navigation-provider.md)

[Windows PowerShell-Anbieter (Übersicht)](./windows-powershell-provider-overview.md)