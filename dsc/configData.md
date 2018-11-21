---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Verwenden von Konfigurationsdaten
ms.openlocfilehash: f2d25b9ced805fb4c91378ebfe840104eb6ce52a
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619176"
---
# <a name="using-configuration-data-in-dsc"></a><span data-ttu-id="c4f60-103">Verwenden von Konfigurationsdaten in DSC</span><span class="sxs-lookup"><span data-stu-id="c4f60-103">Using configuration data in DSC</span></span>

> <span data-ttu-id="c4f60-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c4f60-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c4f60-105">Mithilfe des integrierten DSC-Parameters **ConfigurationData** können Sie Daten definieren, die innerhalb einer Konfiguration verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="c4f60-105">By using the built-in DSC **ConfigurationData** parameter, you can define data that can be used within a configuration.</span></span>
<span data-ttu-id="c4f60-106">Dadurch können Sie eine einzige Konfiguration erstellen, die für mehrere Knoten oder für unterschiedliche Umgebungen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="c4f60-106">This allows you to create a single configuration that can be used for multiple nodes or for different environments.</span></span>
<span data-ttu-id="c4f60-107">Wenn Sie z.B. eine Anwendung entwickeln, können Sie eine Konfiguration für die Entwicklungs-und die Produktionsumgebung verwenden und mithilfe von Konfigurationsdaten Daten für jede Umgebung angeben.</span><span class="sxs-lookup"><span data-stu-id="c4f60-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

<span data-ttu-id="c4f60-108">In diesem Thema wird die Struktur der Hashtabelle **ConfigurationData** beschrieben.</span><span class="sxs-lookup"><span data-stu-id="c4f60-108">This topic describes the structure of the **ConfigurationData** hashtable.</span></span>
<span data-ttu-id="c4f60-109">Beispiele zur Verwendung von Konfigurationsdaten finden Sie unter [Trennen von Konfigurations- und Umgebungsdaten](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="c4f60-109">For examples of how to use configuration data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="the-configurationdata-common-parameter"></a><span data-ttu-id="c4f60-110">Der allgemeine Parameter „ConfigurationData“</span><span class="sxs-lookup"><span data-stu-id="c4f60-110">The ConfigurationData common parameter</span></span>

<span data-ttu-id="c4f60-111">Eine DSC-Konfiguration umfasst einen allgemeinen Parameter namens **ConfigurationData**, den Sie beim Kompilieren der Konfiguration angeben.</span><span class="sxs-lookup"><span data-stu-id="c4f60-111">A DSC configuration takes a common parameter, **ConfigurationData**, that you specify when you compile the configuration.</span></span>
<span data-ttu-id="c4f60-112">Informationen zum Kompilieren von Konfigurationen finden Sie unter [DSC-Konfigurationen](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="c4f60-112">For information about compiling configurations, see [DSC configurations](configurations.md).</span></span>

<span data-ttu-id="c4f60-113">Der Parameter **ConfigurationData** ist eine Hashtabelle, die mindestens einen Schlüssel namens **AllNodes** benötigt.</span><span class="sxs-lookup"><span data-stu-id="c4f60-113">The **ConfigurationData** parameter is a hashtable that must have at least one key named **AllNodes**.</span></span>
<span data-ttu-id="c4f60-114">Die Hashtabelle kann außerdem noch weitere Schlüssel umfassen.</span><span class="sxs-lookup"><span data-stu-id="c4f60-114">It can also have one or more other keys.</span></span>

> [!NOTE]
> <span data-ttu-id="c4f60-115">In den Beispielen in diesem Artikel wird (neben dem Schlüssel **AllNodes**) nur ein einziger zusätzlicher Schlüssel verwendet. Dieser trägt den Namen `NonNodeData`. Sie können jedoch eine beliebige Anzahl zusätzlicher Schlüssel verwenden und diese nach Wunsch benennen.</span><span class="sxs-lookup"><span data-stu-id="c4f60-115">The examples in this topic use a single additional key (other than the named **AllNodes** key) named `NonNodeData`, but you can include any number of additional keys, and name them whatever you want.</span></span>

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

<span data-ttu-id="c4f60-116">Der Wert des **AllNodes**-Schlüssels ist ein Array.</span><span class="sxs-lookup"><span data-stu-id="c4f60-116">The value of the **AllNodes** key is an array.</span></span> <span data-ttu-id="c4f60-117">Jedes Element dieses Arrays ist ebenfalls eine Hashtabelle, die mindestens einen Schlüssel namens **NodeName** benötigt:</span><span class="sxs-lookup"><span data-stu-id="c4f60-117">Each element of this array is also a hash table that must have at least one key named **NodeName**:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="c4f60-118">Sie können jeder Hashtabelle auch andere Schlüssel hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="c4f60-118">You can add other keys to each hash table as well:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="c4f60-119">Um allen Knoten eine Eigenschaft zuzuweisen, können Sie ein Member des **AllNodes**-Arrays erstellen, dessen **NodeName** gleich `*` ist.</span><span class="sxs-lookup"><span data-stu-id="c4f60-119">To apply a property to all nodes, you can create a member of the **AllNodes** array that has a **NodeName** of `*`.</span></span>
<span data-ttu-id="c4f60-120">Verwenden Sie z.B. folgenden Code, um allen Knoten die Eigenschaft `LogPath` zuzuweisen:</span><span class="sxs-lookup"><span data-stu-id="c4f60-120">For example, to give every node a `LogPath` property, you could do this:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

<span data-ttu-id="c4f60-121">Dies entspricht dem Hinzufügen einer Eigenschaft namens `LogPath` mit einem Wert `"C:\Logs"` zu jedem der anderen Blöcke (`VM-1`, `VM-2` und `VM-3`).</span><span class="sxs-lookup"><span data-stu-id="c4f60-121">This is the equivalent of adding a property with a name of `LogPath` with a value of `"C:\Logs"` to each of the other blocks (`VM-1`, `VM-2`, and `VM-3`).</span></span>

## <a name="defining-the-configurationdata-hashtable"></a><span data-ttu-id="c4f60-122">Definieren der ConfigurationData-Hashtabelle</span><span class="sxs-lookup"><span data-stu-id="c4f60-122">Defining the ConfigurationData hashtable</span></span>

<span data-ttu-id="c4f60-123">Sie können **ConfigurationData** entweder als eine Variable innerhalb derselben Skriptdatei als Konfiguration (wie in unseren bisherigen Beispielen) oder in einer separaten `.psd1`-Datei definieren.</span><span class="sxs-lookup"><span data-stu-id="c4f60-123">You can define **ConfigurationData** either as a variable within the same script file as a configuration (as in our previous examples) or in a separate `.psd1` file.</span></span>
<span data-ttu-id="c4f60-124">Erstellen Sie zum Definieren von **ConfigurationData** in einer `.psd1`-Datei eine Datei, die nur die Hashtabelle enthält, die die Konfigurationsdaten darstellt.</span><span class="sxs-lookup"><span data-stu-id="c4f60-124">To define **ConfigurationData** in a `.psd1` file, create a file that contains only the hashtable that represents the configuration data.</span></span>

<span data-ttu-id="c4f60-125">Sie könnten z.B. eine Datei namens `MyData.psd1` mit folgendem Inhalt erstellen:</span><span class="sxs-lookup"><span data-stu-id="c4f60-125">For example, you could create a file named `MyData.psd1` with the following contents:</span></span>

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a><span data-ttu-id="c4f60-126">Kompilieren einer Konfiguration mit Konfigurationsdaten</span><span class="sxs-lookup"><span data-stu-id="c4f60-126">Compiling a configuration with configuration data</span></span>

<span data-ttu-id="c4f60-127">Um eine Konfiguration zu kompilieren, für die Sie Konfigurationsdaten definiert haben, übergeben Sie die Konfigurationsdaten als Wert des Parameters **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="c4f60-127">To compile a configuration for which you have defined configuration data, you pass the configuration data as the value of the **ConfigurationData** parameter.</span></span>

<span data-ttu-id="c4f60-128">Auf diese Weise wird für jeden Eintrag im **AllNodes**-Array eine MOF-Datei erstellt.</span><span class="sxs-lookup"><span data-stu-id="c4f60-128">This will create a MOF file for each entry in the **AllNodes** array.</span></span>
<span data-ttu-id="c4f60-129">Jede MOF-Datei wird nach der `NodeName`-Eigenschaft des zugehörigen Arrayeintrags benannt.</span><span class="sxs-lookup"><span data-stu-id="c4f60-129">Each MOF file will be named with the `NodeName` property of the corresponding array entry.</span></span>

<span data-ttu-id="c4f60-130">Wenn Sie beispielsweise Konfigurationsdaten wie in der vorstehenden `MyData.psd1`-Datei definieren, werden beim Kompilieren einer Konfiguration sowohl `VM-1.mof`- als auch `VM-2.mof`-Dateien erstellt.</span><span class="sxs-lookup"><span data-stu-id="c4f60-130">For example, if you define configuration data as in the `MyData.psd1` file above, compiling a configuration would create both `VM-1.mof` and `VM-2.mof` files.</span></span>

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a><span data-ttu-id="c4f60-131">Kompilieren einer Konfiguration mit Konfigurationsdaten unter Verwendung einer Variablen</span><span class="sxs-lookup"><span data-stu-id="c4f60-131">Compiling a configuration with configuration data using a variable</span></span>

<span data-ttu-id="c4f60-132">Um Konfigurationsdaten zu verwenden, die in derselben `.ps1`-Datei wie die Konfiguration als Variable definiert sind, übergeben Sie den Variablennamen beim Kompilieren der Konfiguration als Wert des Parameters **ConfigurationData**:</span><span class="sxs-lookup"><span data-stu-id="c4f60-132">To use configuration data that is defined as a variable in the same `.ps1` file as the configuration, you pass the variable name as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a><span data-ttu-id="c4f60-133">Kompilieren einer Konfiguration mit Konfigurationsdaten unter Verwendung einer Datendatei</span><span class="sxs-lookup"><span data-stu-id="c4f60-133">Compiling a configuration with configuration data using a data file</span></span>

<span data-ttu-id="c4f60-134">Um Konfigurationsdaten zu verwenden, die in einer PSD1-Datei definiert sind, übergeben Sie Pfad und Namen der Datei bei der Kompilierung der Konfiguration als Wert des Parameters **ConfigurationData**:</span><span class="sxs-lookup"><span data-stu-id="c4f60-134">To use configuration data that is defined in a .psd1 file, you pass the path and name of that file as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a><span data-ttu-id="c4f60-135">Verwenden von ConfigurationData-Variablen in einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="c4f60-135">Using ConfigurationData variables in a configuration</span></span>

<span data-ttu-id="c4f60-136">DSC bietet die folgenden besonderen Variablen, die in einem Konfigurationsskript verwendet werden können:</span><span class="sxs-lookup"><span data-stu-id="c4f60-136">DSC provides the following special variables that can be used in a configuration script:</span></span>

- <span data-ttu-id="c4f60-137">**$AllNodes** bezieht sich auf die gesamte, in **ConfigurationData** definierte Knotensammlung.</span><span class="sxs-lookup"><span data-stu-id="c4f60-137">**$AllNodes** refers to the entire collection of nodes defined in **ConfigurationData**.</span></span> <span data-ttu-id="c4f60-138">Sie können die **AllNodes**-Sammlung mit **.Where()** und **.ForEach()** filtern.</span><span class="sxs-lookup"><span data-stu-id="c4f60-138">You can filter the **AllNodes** collection by using **.Where()** and **.ForEach()**.</span></span>
- <span data-ttu-id="c4f60-139">**ConfigurationData** bezieht sich auf die gesamte Hashtabelle, die beim Kompilieren einer Konfiguration als Parameter übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="c4f60-139">**ConfigurationData** refers to the entire hash table that is passed as the parameter when compiling a configuration.</span></span>
- <span data-ttu-id="c4f60-140">**MyTypeName** enthält die [Konfiguration](configurations.md) die Variable, im verwendet wird Namen.</span><span class="sxs-lookup"><span data-stu-id="c4f60-140">**MyTypeName** contains the [configuration](configurations.md) name the variable is used in.</span></span> <span data-ttu-id="c4f60-141">Z. B. in der Konfiguration `MyDscConfiguration`, `$MyTypeName` Wert der `MyDscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="c4f60-141">For example, in the configuration `MyDscConfiguration`, the `$MyTypeName` will have a value of `MyDscConfiguration`.</span></span>
- <span data-ttu-id="c4f60-142">**Nodes** bezieht sich auf einen bestimmten Eintrag in der **AllNodes**-Sammlung, nachdem sie mithilfe von **.Where()** oder **.ForEach()** gefiltert wurde.</span><span class="sxs-lookup"><span data-stu-id="c4f60-142">**Node** refers to a particular entry in the **AllNodes** collection after it is filtered by using **.Where()** or **.ForEach()**.</span></span>
  - <span data-ttu-id="c4f60-143">Weitere Informationen zu diesen Methoden finden Sie unter [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md).</span><span class="sxs-lookup"><span data-stu-id="c4f60-143">You can read more about these methods in [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span></span>

## <a name="using-non-node-data"></a><span data-ttu-id="c4f60-144">Verwenden von Daten ohne Knoten</span><span class="sxs-lookup"><span data-stu-id="c4f60-144">Using non-node data</span></span>

<span data-ttu-id="c4f60-145">Wie wir in den vorherigen Beispielen gesehen haben, kann die Hashtabelle **ConfigurationData** neben dem erforderlichen Schlüssel **AllNodes** weitere Schlüssel aufweisen.</span><span class="sxs-lookup"><span data-stu-id="c4f60-145">As we've seen in previous examples, the **ConfigurationData** hashtable can have one or more keys in addition to the required **AllNodes** key.</span></span>
<span data-ttu-id="c4f60-146">In den Beispielen in diesem Thema wurde nur ein einziger zusätzlicher Knoten namens `NonNodeData` verwendet.</span><span class="sxs-lookup"><span data-stu-id="c4f60-146">In the examples in this topic, we have used only a single additional node, and named it `NonNodeData`.</span></span>
<span data-ttu-id="c4f60-147">Sie können jedoch eine beliebige Anzahl von zusätzlichen Schlüsseln definieren und diese nach Wunsch benennen.</span><span class="sxs-lookup"><span data-stu-id="c4f60-147">However, you can define any number of additional keys, and name them anything you want.</span></span>

<span data-ttu-id="c4f60-148">Ein Beispiel für die Verwendung von Nicht-Knotendaten finden Sie unter [Trennen von Konfigurations- und Umgebungsdaten](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="c4f60-148">For an example of using non-node data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c4f60-149">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c4f60-149">See Also</span></span>

- [<span data-ttu-id="c4f60-150">Optionen für Anmeldeinformationen in den Konfigurationsdaten</span><span class="sxs-lookup"><span data-stu-id="c4f60-150">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="c4f60-151">DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="c4f60-151">DSC Configurations</span></span>](configurations.md)