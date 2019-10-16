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
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="c9941-102">Schreiben eines Navigationsanbieters</span><span class="sxs-lookup"><span data-stu-id="c9941-102">Writing a navigation provider</span></span>

<span data-ttu-id="c9941-103">In diesem Thema wird beschrieben, wie die Methoden eines Windows PowerShell-Anbieters implementiert werden, die die Unterstützung von schsted Containern (Datenspeicher mit mehreren Ebenen), das Verschieben von Elementen und relative Pfade unterstützen.</span><span class="sxs-lookup"><span data-stu-id="c9941-103">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="c9941-104">Ein Navigations Anbieter muss von der [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse abgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="c9941-104">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="c9941-105">Für den Anbieter in den Beispielen in diesem Thema wird eine Access-Datenbank als Datenspeicher verwendet.</span><span class="sxs-lookup"><span data-stu-id="c9941-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="c9941-106">Es gibt mehrere Hilfsmethoden und-Klassen, die für die Interaktion mit der Datenbank verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c9941-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="c9941-107">Das komplette Beispiel, das die-Hilfsmethoden enthält, finden Sie unter [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="c9941-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="c9941-108">Weitere Informationen zu Windows PowerShell-Anbietern finden Sie unter Übersicht über den [Windows PowerShell-Anbieter](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c9941-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="c9941-109">Implementieren von Navigationsmethoden</span><span class="sxs-lookup"><span data-stu-id="c9941-109">Implementing navigation methods</span></span>

<span data-ttu-id="c9941-110">Die [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse implementiert Methoden, die die Unterstützung von unterstützten Containern, relativen Pfaden und Verschiebungs Elementen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="c9941-110">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="c9941-111">Eine umfassende Liste dieser Methoden finden Sie unter [navigationcmdletprovider-Methoden](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).</span><span class="sxs-lookup"><span data-stu-id="c9941-111">For a complete list of these methods, see [NavigationCmdletProvider Methods](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).</span></span>

> [!NOTE]
> <span data-ttu-id="c9941-112">Dieses Thema baut auf den Informationen in der Schnellstartanleitung für den [Windows PowerShell-Anbieter](./windows-powershell-provider-quickstart.md)auf.</span><span class="sxs-lookup"><span data-stu-id="c9941-112">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="c9941-113">Dieses Thema behandelt nicht die Grundlagen der Einrichtung eines Anbieter Projekts oder die Implementierung der Methoden, die von der [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Klasse geerbt werden, die Laufwerke erstellt und entfernt.</span><span class="sxs-lookup"><span data-stu-id="c9941-113">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="c9941-114">Außerdem wird in diesem Thema nicht behandelt, wie Methoden implementiert werden, die von der [System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Klasse oder der [System. Management. Automation. Provider. containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) -Klasse verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="c9941-114">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="c9941-115">Ein Beispiel, das zeigt, wie Item-Cmdlets implementiert werden, finden Sie unter [Schreiben eines Element Anbieters](./writing-an-item-provider.md).</span><span class="sxs-lookup"><span data-stu-id="c9941-115">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="c9941-116">Ein Beispiel für das Implementieren von Container-Cmdlets finden Sie unter [Schreiben eines Container Anbieters](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="c9941-116">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="c9941-117">Deklarieren der Anbieter Klasse</span><span class="sxs-lookup"><span data-stu-id="c9941-117">Declaring the provider class</span></span>

<span data-ttu-id="c9941-118">Deklarieren Sie den Anbieter so, dass er von der [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse abgeleitet wird, und versehen Sie ihn mit dem [System. Management. Automation. Provider. cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="c9941-118">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="c9941-119">Implementieren von isitemcontainer</span><span class="sxs-lookup"><span data-stu-id="c9941-119">Implementing IsItemContainer</span></span>

<span data-ttu-id="c9941-120">Die [System. Management. Automation. Provider. navigationcmdletprovider. isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) -Methode überprüft, ob das Element im angegebenen Pfad ein Container ist.</span><span class="sxs-lookup"><span data-stu-id="c9941-120">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

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

### <a name="implementing-getchildname"></a><span data-ttu-id="c9941-121">Implementieren von "getchildname"</span><span class="sxs-lookup"><span data-stu-id="c9941-121">Implementing GetChildName</span></span>

<span data-ttu-id="c9941-122">Die [System. Management. Automation. Provider. navigationcmdletprovider. getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) -Methode ruft die Name-Eigenschaft des untergeordneten Elements im angegebenen Pfad ab.</span><span class="sxs-lookup"><span data-stu-id="c9941-122">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="c9941-123">Wenn das Element im angegebenen Pfad kein untergeordnetes Element eines Containers ist, sollte diese Methode den Pfad zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="c9941-123">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

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

### <a name="implementing-getparentpath"></a><span data-ttu-id="c9941-124">Implementieren von getcentpath</span><span class="sxs-lookup"><span data-stu-id="c9941-124">Implementing GetParentPath</span></span>

<span data-ttu-id="c9941-125">Mit der [System. Management. Automation. Provider. navigationcmdletprovider. getparameentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) -Methode wird der Pfad des übergeordneten Elements des Elements im angegebenen Pfad abgerufen.</span><span class="sxs-lookup"><span data-stu-id="c9941-125">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="c9941-126">Wenn das Element im angegebenen Pfad der Stamm des Datenspeicher ist (d. h., es ist kein übergeordnetes Element), sollte diese Methode den Stammpfad zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="c9941-126">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

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

### <a name="implementing-makepath"></a><span data-ttu-id="c9941-127">Implementieren von makepath</span><span class="sxs-lookup"><span data-stu-id="c9941-127">Implementing MakePath</span></span>

<span data-ttu-id="c9941-128">Die [System. Management. Automation. Provider. navigationcmdletprovider. makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) -Methode verbindet einen angegebenen übergeordneten Pfad und einen angegebenen untergeordneten Pfad, um einen Anbieter internen Pfad zu erstellen (Weitere Informationen zu Pfad Typen, die von Anbietern unterstützt werden können, finden Sie unter [Übersicht über den Windows PowerShell-Anbieter](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c9941-128">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="c9941-129">Die PowerShell-Engine ruft diese Methode auf, wenn ein Benutzer das [Microsoft. PowerShell. Commands. joinpathcommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) -Cmdlet aufruft.</span><span class="sxs-lookup"><span data-stu-id="c9941-129">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet.</span></span>

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

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="c9941-130">Implementieren von normalizerelativepath</span><span class="sxs-lookup"><span data-stu-id="c9941-130">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="c9941-131">Die [System. Management. Automation. Provider. navigationcmdletprovider. normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) -Methode übernimmt `path`-und `basepath`-Parameter und gibt einen normalisierten Pfad zurück, der dem `path`-Parameter und relativ zum `basepath` entspricht. Parame.</span><span class="sxs-lookup"><span data-stu-id="c9941-131">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

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

### <a name="implementing-moveitem"></a><span data-ttu-id="c9941-132">Implementieren von "muveitem"</span><span class="sxs-lookup"><span data-stu-id="c9941-132">Implementing MoveItem</span></span>

<span data-ttu-id="c9941-133">Die [System. Management. Automation. Provider. navigationcmdletprovider. muveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) -Methode verschiebt ein Element aus dem angegebenen Pfad in den angegebenen Zielpfad.</span><span class="sxs-lookup"><span data-stu-id="c9941-133">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="c9941-134">Die PowerShell-Engine ruft diese Methode auf, wenn ein Benutzer das Cmdlet " [Microsoft. PowerShell. Commands.](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) -Cmdlet" aufruft.</span><span class="sxs-lookup"><span data-stu-id="c9941-134">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c9941-135">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c9941-135">See Also</span></span>

[<span data-ttu-id="c9941-136">Schreiben eines Container Anbieters</span><span class="sxs-lookup"><span data-stu-id="c9941-136">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="c9941-137">Windows PowerShell-Anbieter (Übersicht)</span><span class="sxs-lookup"><span data-stu-id="c9941-137">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)