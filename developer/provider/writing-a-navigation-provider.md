---
title: Schreiben eines Anbieters für die Navigation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98bcfda0-6ee2-46f5-bbc7-5fab8b780d6a
caps.latest.revision: 5
ms.openlocfilehash: edb4d9944a527391983e068ddf07f4fac415c3f9
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734729"
---
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="f731d-102">Schreiben eines Navigationsanbieters</span><span class="sxs-lookup"><span data-stu-id="f731d-102">Writing a navigation provider</span></span>

<span data-ttu-id="f731d-103">In diesem Thema wird beschrieben, wie Sie die Methoden von einem Windows PowerShell-Anbieter implementieren, die die geschachtelten Container (mit mehreren Ebenen Datenspeicher), verschieben Elemente und relative Pfade zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="f731d-103">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="f731d-104">Muss ein Navigationsanbieter von abgeleitet werden die [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="f731d-104">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="f731d-105">Der Anbieter in den Beispielen in diesem Thema verwendet eine Access-Datenbank als Datenspeicher.</span><span class="sxs-lookup"><span data-stu-id="f731d-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="f731d-106">Es gibt mehrere Hilfsmethoden und Klassen, die verwendet werden, um die Interaktion mit der Datenbank.</span><span class="sxs-lookup"><span data-stu-id="f731d-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="f731d-107">Das vollständige Beispiel, das die Hilfsmethoden enthält, finden Sie unter [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="f731d-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="f731d-108">Weitere Informationen zu Windows PowerShell-Anbietern finden Sie unter [Übersicht über Windows PowerShell-Anbieter](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f731d-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="f731d-109">Navigationsmethoden implementiert werden</span><span class="sxs-lookup"><span data-stu-id="f731d-109">Implementing navigation methods</span></span>

<span data-ttu-id="f731d-110">Die [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse implementiert Methoden, die die geschachtelten Container, relative Pfade und Verschieben von Elementen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="f731d-110">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="f731d-111">Eine vollständige Liste der folgenden Methoden, finden Sie unter [NavigationCmdletProvider Methoden](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).</span><span class="sxs-lookup"><span data-stu-id="f731d-111">For a complete list of these methods, see [NavigationCmdletProvider Methods](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).</span></span>

> [!NOTE]
> <span data-ttu-id="f731d-112">Dieses Thema baut auf den Informationen in [Schnellstartanleitung zu Windows PowerShell-Anbieter](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="f731d-112">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="f731d-113">Dieses Thema deckt sich nicht auf die Grundlagen zum Einrichten eines Anbieter-Projekts und Gewusst wie: Implementieren der Methoden geerbt von der [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Klasse, die erstellen und Entfernen von Laufwerken.</span><span class="sxs-lookup"><span data-stu-id="f731d-113">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="f731d-114">In diesem Thema behandelt auch nicht vom verfügbar gemachten Methoden implementieren die [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) oder [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) Klassen.</span><span class="sxs-lookup"><span data-stu-id="f731d-114">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="f731d-115">Ein Beispiel zum Implementieren der Item-Cmdlets finden Sie unter [Schreiben eines Datenanbieters Element](./writing-an-item-provider.md).</span><span class="sxs-lookup"><span data-stu-id="f731d-115">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="f731d-116">Ein Beispiel, wie Container Cmdlets implementiert, finden Sie unter [Schreiben eines Anbieters Container](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="f731d-116">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="f731d-117">Die Anbieterklasse deklarieren</span><span class="sxs-lookup"><span data-stu-id="f731d-117">Declaring the provider class</span></span>

<span data-ttu-id="f731d-118">Deklarieren Sie den Anbieter für die Ableitung der [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) Klasse, und versehen Sie sie mit der [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="f731d-118">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="f731d-119">Implementieren von IsItemContainer</span><span class="sxs-lookup"><span data-stu-id="f731d-119">Implementing IsItemContainer</span></span>

<span data-ttu-id="f731d-120">Die [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) Methode überprüft, ob das Element am angegebenen Pfad einem Container ist.</span><span class="sxs-lookup"><span data-stu-id="f731d-120">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

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

### <a name="implementing-getchildname"></a><span data-ttu-id="f731d-121">Implementieren von GetChildName</span><span class="sxs-lookup"><span data-stu-id="f731d-121">Implementing GetChildName</span></span>

<span data-ttu-id="f731d-122">Die [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) Methode ruft die Name-Eigenschaft des untergeordneten Elements am angegebenen Pfad ab.</span><span class="sxs-lookup"><span data-stu-id="f731d-122">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="f731d-123">Wenn das Element am angegebenen Pfad nicht um ein untergeordnetes Element eines Containers ist, sollte diese Methode den Pfad zurück.</span><span class="sxs-lookup"><span data-stu-id="f731d-123">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

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

### <a name="implementing-getparentpath"></a><span data-ttu-id="f731d-124">Implementieren von GetParentPath</span><span class="sxs-lookup"><span data-stu-id="f731d-124">Implementing GetParentPath</span></span>

<span data-ttu-id="f731d-125">Die [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) Methode ruft den Pfad des übergeordneten Elements des Elements am angegebenen Pfad ab.</span><span class="sxs-lookup"><span data-stu-id="f731d-125">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="f731d-126">Wenn das Element am angegebenen Pfad ist der Stamm des Datenspeichers (damit es kein übergeordnetes Element besitzt), sollte diese Methode den Stammpfad zurück.</span><span class="sxs-lookup"><span data-stu-id="f731d-126">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

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

### <a name="implementing-makepath"></a><span data-ttu-id="f731d-127">MakePath implementieren</span><span class="sxs-lookup"><span data-stu-id="f731d-127">Implementing MakePath</span></span>

<span data-ttu-id="f731d-128">Die [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) -Methode verknüpft einen angegebenen übergeordneten Pfad und einen angegebenen untergeordneten Pfad einen Anbieter-internen Pfad erstellen (für Informationen zu Path Datentypen Anbieter können zu unterstützen, finden Sie unter [Übersicht über Windows PowerShell-Anbieter](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f731d-128">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="f731d-129">Die PowerShell-Engine ruft diese Methode auf, wenn ein Benutzer ruft die [Microsoft.PowerShell.Commands.JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f731d-129">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet.</span></span>

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

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="f731d-130">Implementieren von NormalizeRelativePath</span><span class="sxs-lookup"><span data-stu-id="f731d-130">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="f731d-131">Die [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) -Methode übernimmt `path` und `basepath` Parameter und gibt einen normalisierten Pfad, der die entspricht`path`Parameter und relativ zu den `basepath` Parameter.</span><span class="sxs-lookup"><span data-stu-id="f731d-131">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

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

### <a name="implementing-moveitem"></a><span data-ttu-id="f731d-132">Implementieren von MoveItem</span><span class="sxs-lookup"><span data-stu-id="f731d-132">Implementing MoveItem</span></span>

<span data-ttu-id="f731d-133">Die [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) Methode verschiebt ein Element aus dem angegebenen Pfad, in den angegebenen Zielpfad.</span><span class="sxs-lookup"><span data-stu-id="f731d-133">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="f731d-134">Die PowerShell-Engine ruft diese Methode auf, wenn ein Benutzer ruft die [Microsoft.PowerShell.Commands.MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f731d-134">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f731d-135">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f731d-135">See Also</span></span>

[<span data-ttu-id="f731d-136">Schreiben eines Anbieters für container</span><span class="sxs-lookup"><span data-stu-id="f731d-136">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="f731d-137">Windows PowerShell-Anbieter (Übersicht)</span><span class="sxs-lookup"><span data-stu-id="f731d-137">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)