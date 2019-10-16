---
title: Schreiben eines navigationsanbieters | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98bcfda0-6ee2-46f5-bbc7-5fab8b780d6a
caps.latest.revision: 5
ms.openlocfilehash: edb4d9944a527391983e068ddf07f4fac415c3f9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359869"
---
# <a name="writing-a-navigation-provider"></a>Schreiben eines Navigationsanbieters

In diesem Thema wird beschrieben, wie die Methoden eines Windows PowerShell-Anbieters implementiert werden, die die Unterstützung von schsted Containern (Datenspeicher mit mehreren Ebenen), das Verschieben von Elementen und relative Pfade unterstützen. Ein Navigations Anbieter muss von der [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse abgeleitet werden.

Für den Anbieter in den Beispielen in diesem Thema wird eine Access-Datenbank als Datenspeicher verwendet. Es gibt mehrere Hilfsmethoden und-Klassen, die für die Interaktion mit der Datenbank verwendet werden. Das komplette Beispiel, das die-Hilfsmethoden enthält, finden Sie unter [AccessDBProviderSample05](./accessdbprovidersample05.md).

Weitere Informationen zu Windows PowerShell-Anbietern finden Sie unter Übersicht über den [Windows PowerShell-Anbieter](./windows-powershell-provider-overview.md).

## <a name="implementing-navigation-methods"></a>Implementieren von Navigationsmethoden

Die [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse implementiert Methoden, die die Unterstützung von unterstützten Containern, relativen Pfaden und Verschiebungs Elementen unterstützen. Eine umfassende Liste dieser Methoden finden Sie unter [navigationcmdletprovider-Methoden](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).

> [!NOTE]
> Dieses Thema baut auf den Informationen in der Schnellstartanleitung für den [Windows PowerShell-Anbieter](./windows-powershell-provider-quickstart.md)auf. Dieses Thema behandelt nicht die Grundlagen der Einrichtung eines Anbieter Projekts oder die Implementierung der Methoden, die von der [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Klasse geerbt werden, die Laufwerke erstellt und entfernt. Außerdem wird in diesem Thema nicht behandelt, wie Methoden implementiert werden, die von der [System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Klasse oder der [System. Management. Automation. Provider. containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) -Klasse verfügbar gemacht werden. Ein Beispiel, das zeigt, wie Item-Cmdlets implementiert werden, finden Sie unter [Schreiben eines Element Anbieters](./writing-an-item-provider.md). Ein Beispiel für das Implementieren von Container-Cmdlets finden Sie unter [Schreiben eines Container Anbieters](./writing-a-container-provider.md).

### <a name="declaring-the-provider-class"></a>Deklarieren der Anbieter Klasse

Deklarieren Sie den Anbieter so, dass er von der [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse abgeleitet wird, und versehen Sie ihn mit dem [System. Management. Automation. Provider. cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a>Implementieren von isitemcontainer

Die [System. Management. Automation. Provider. navigationcmdletprovider. isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) -Methode überprüft, ob das Element im angegebenen Pfad ein Container ist.

```csharp
protected override bool IsItemContainer(string path)
      {
         if (PathIsDrive(path))
         {
             return true;
         }

         string[] pathChunks = ChunkPath(path);
         string tableName;
         int rowNumber;

         PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

         if (type == PathType.Table)
         {
            foreach (DatabaseTableInfo ti in GetTables())
            {
                if (string.Equals(ti.Name, tableName, StringComparison.OrdinalIgnoreCase))
                {
                    return true;
                }
            } // foreach (DatabaseTableInfo...
         } // if (pathChunks...

         return false;
      }
```

### <a name="implementing-getchildname"></a>Implementieren von "getchildname"

Die [System. Management. Automation. Provider. navigationcmdletprovider. getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) -Methode ruft die Name-Eigenschaft des untergeordneten Elements im angegebenen Pfad ab. Wenn das Element im angegebenen Pfad kein untergeordnetes Element eines Containers ist, sollte diese Methode den Pfad zurückgeben.

```csharp
protected override string GetChildName(string path)
       {
           if (PathIsDrive(path))
           {
               return path;
           }

           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               return tableName;
           }
           else if (type == PathType.Row)
           {
               return rowNumber.ToString(CultureInfo.CurrentCulture);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

           return null;
       }
```

### <a name="implementing-getparentpath"></a>Implementieren von getcentpath

Mit der [System. Management. Automation. Provider. navigationcmdletprovider. getparameentpath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) -Methode wird der Pfad des übergeordneten Elements des Elements im angegebenen Pfad abgerufen. Wenn das Element im angegebenen Pfad der Stamm des Datenspeicher ist (d. h., es ist kein übergeordnetes Element), sollte diese Methode den Stammpfad zurückgeben.

```csharp
protected override string GetParentPath(string path, string root)
       {
           // If root is specified then the path has to contain
           // the root. If not nothing should be returned
           if (!String.IsNullOrEmpty(root))
           {
               if (!path.Contains(root))
               {
                   return null;
               }
           }

           return path.Substring(0, path.LastIndexOf(pathSeparator, StringComparison.OrdinalIgnoreCase));
       }
```

### <a name="implementing-makepath"></a>Implementieren von makepath

Die [System. Management. Automation. Provider. navigationcmdletprovider. makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) -Methode verbindet einen angegebenen übergeordneten Pfad und einen angegebenen untergeordneten Pfad, um einen Anbieter internen Pfad zu erstellen (Weitere Informationen zu Pfad Typen, die von Anbietern unterstützt werden können, finden Sie unter [Übersicht über den Windows PowerShell-Anbieter](./windows-powershell-provider-overview.md). Die PowerShell-Engine ruft diese Methode auf, wenn ein Benutzer das [Microsoft. PowerShell. Commands. joinpathcommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) -Cmdlet aufruft.

```csharp
protected override string MakePath(string parent, string child)
       {
           string result;

           string normalParent = NormalizePath(parent);
           normalParent = RemoveDriveFromPath(normalParent);
           string normalChild = NormalizePath(child);
           normalChild = RemoveDriveFromPath(normalChild);

           if (String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               result = String.Empty;
           }
           else if (String.IsNullOrEmpty(normalParent) && !String.IsNullOrEmpty(normalChild))
           {
               result = normalChild;
           }
           else if (!String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               if (normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent;
               }
               else
               {
                   result = normalParent + pathSeparator;
               }
           } // else if (!String...
           else
           {
               if (!normalParent.Equals(String.Empty) &&
                   !normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent + pathSeparator;
               }
               else
               {
                   result = normalParent;
               }

               if (normalChild.StartsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result += normalChild.Substring(1);
               }
               else
               {
                   result += normalChild;
               }
           } // else

           return result;
       }
```

### <a name="implementing-normalizerelativepath"></a>Implementieren von normalizerelativepath

Die [System. Management. Automation. Provider. navigationcmdletprovider. normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) -Methode übernimmt `path`-und `basepath`-Parameter und gibt einen normalisierten Pfad zurück, der dem `path`-Parameter und relativ zum `basepath` entspricht. Parame.

```csharp
protected override string NormalizeRelativePath(string path,
                                                            string basepath)
       {
           // Normalize the paths first
           string normalPath = NormalizePath(path);
           normalPath = RemoveDriveFromPath(normalPath);
           string normalBasePath = NormalizePath(basepath);
           normalBasePath = RemoveDriveFromPath(normalBasePath);

           if (String.IsNullOrEmpty(normalBasePath))
           {
               return normalPath;
           }
           else
           {
               if (!normalPath.Contains(normalBasePath))
               {
                   return null;
               }

               return normalPath.Substring(normalBasePath.Length + pathSeparator.Length);
           }
       }
```

### <a name="implementing-moveitem"></a>Implementieren von "muveitem"

Die [System. Management. Automation. Provider. navigationcmdletprovider. muveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) -Methode verschiebt ein Element aus dem angegebenen Pfad in den angegebenen Zielpfad. Die PowerShell-Engine ruft diese Methode auf, wenn ein Benutzer das Cmdlet " [Microsoft. PowerShell. Commands.](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) -Cmdlet" aufruft.

```csharp
protected override void MoveItem(string path, string destination)
       {
           // Get type, table name and rowNumber from the path
           string tableName, destTableName;
           int rowNumber, destRowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           PathType destType = GetNamesFromPath(destination, out destTableName,
                                    out destRowNumber);

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           if (destType == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(destination);
           }

           if (type == PathType.Table)
           {
               ArgumentException e = new ArgumentException("Move not supported for tables");

               WriteError(new ErrorRecord(e, "MoveNotSupported",
                   ErrorCategory.InvalidArgument, path));

               throw e;
           }
           else
           {
               OdbcDataAdapter da = GetAdapterForTable(tableName);
               if (da == null)
               {
                   return;
               }

               DataSet ds = GetDataSetForTable(da, tableName);
               DataTable table = GetDataTable(ds, tableName);

               OdbcDataAdapter dda = GetAdapterForTable(destTableName);
               if (dda == null)
               {
                   return;
               }

               DataSet dds = GetDataSetForTable(dda, destTableName);
               DataTable destTable = GetDataTable(dds, destTableName);
               DataRow row = table.Rows[rowNumber];

               if (destType == PathType.Table)
               {
                   DataRow destRow = destTable.NewRow();

                   destRow.ItemArray = row.ItemArray;
               }
               else
               {
                   DataRow destRow = destTable.Rows[destRowNumber];

                   destRow.ItemArray = row.ItemArray;
               }

               // Update the changes
               if (ShouldProcess(path, "MoveItem"))
               {
                   WriteItemObject(row, path, false);
                   dda.Update(dds, destTableName);
               }
           }
       }
```

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Container Anbieters](./writing-a-container-provider.md)

[Windows PowerShell-Anbieter (Übersicht)](./windows-powershell-provider-overview.md)