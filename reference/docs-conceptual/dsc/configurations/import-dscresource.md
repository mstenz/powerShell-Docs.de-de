---
ms.date: 12/12/2018
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: Verwenden von Import-DscResource
ms.openlocfilehash: a041169ad557becf7ca87641d9ce5222ee8f6beb
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402447"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="d3891-103">Verwenden von Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="d3891-103">Using Import-DSCResource</span></span>

<span data-ttu-id="d3891-104">`Import-DScResource` ist ein dynamisches Schlüsselwort, das nur innerhalb eines Configuration-Skriptblocks verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="d3891-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="d3891-105">Das `Import-DSCResource`-Schlüsselwort dient zum Importieren aller Ressourcen, die in Ihrer Konfiguration erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="d3891-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="d3891-106">Ressourcen unter `$pshome` werden automatisch importiert, aber es gilt immer noch als bewährte Methode, alle in Ihrer [Konfiguration](Configurations.md) verwendeten Ressourcen explizit zu importieren.</span><span class="sxs-lookup"><span data-stu-id="d3891-106">Resources under `$pshome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="d3891-107">Die Syntax für `Import-DSCResource` ist unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="d3891-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="d3891-108">Wenn Sie Module mit Namen angeben, müssen Sie jedes in einer neuen Zeile aufführen.</span><span class="sxs-lookup"><span data-stu-id="d3891-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>] [-ModuleVersion <ModuleVersion>]
```

|<span data-ttu-id="d3891-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="d3891-109">Parameter</span></span>  |<span data-ttu-id="d3891-110">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="d3891-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="d3891-111">Die Namen der DSC-Ressourcen, die Sie importieren müssen.</span><span class="sxs-lookup"><span data-stu-id="d3891-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="d3891-112">Wenn der Name des Moduls angegeben wird, durchsucht der Befehl dieses Modul nach diesen DSC-Ressourcen; andernfalls durchsucht der Befehl die DSC-Ressourcen in allen DSC-Ressourcenpfaden.</span><span class="sxs-lookup"><span data-stu-id="d3891-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="d3891-113">Platzhalter werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d3891-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="d3891-114">Modulname oder Modulspezifikation.</span><span class="sxs-lookup"><span data-stu-id="d3891-114">The module name, or module specification.</span></span>  <span data-ttu-id="d3891-115">Bei Angabe von Ressourcen, die aus einem Modul importiert werden sollen, versucht der Befehl, nur diese Ressourcen zu importieren.</span><span class="sxs-lookup"><span data-stu-id="d3891-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="d3891-116">Wenn Sie nur das Modul angeben, importiert der Befehl alle DSC-Ressourcen im Modul.</span><span class="sxs-lookup"><span data-stu-id="d3891-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|
|`-ModuleVersion`|<span data-ttu-id="d3891-117">Ab PowerShell 5.0 können Sie angeben, welche Version eines Moduls von einer Konfiguration verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="d3891-117">Beginning in PowerShell 5.0, you can specify which version of a module a configuration should use.</span></span> <span data-ttu-id="d3891-118">Weitere Informationen finden Sie unter [Importieren einer spezifischen Version einer installierten Ressource](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="d3891-118">For more information, see [Import a specific version of an installed resource](sxsresource.md).</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="d3891-119">Beispiel: Verwenden von Import-DSCResource in einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="d3891-119">Example: Use Import-DSCResource within a configuration</span></span>

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    # In PowerShell 5.0 and later, you can specify a ModuleVersion parameter
    Import-DSCResource -ModuleName ComputerManagementDsc -ModuleVersion 6.0.0.0
...
```

> [!NOTE]
> <span data-ttu-id="d3891-120">Die Angabe mehrerer Werte für Ressourcen- und Modulnamen im selben Befehl wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d3891-120">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="d3891-121">Falls dieselbe Ressource in mehreren Modulen vorhanden ist, kann dies in Bezug darauf, welche Ressource aus welchem Modul geladen wird, zu einem nicht deterministischen Verhalten führen.</span><span class="sxs-lookup"><span data-stu-id="d3891-121">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="d3891-122">Der folgende Befehl führt zu einem Fehler während der Kompilierung.</span><span class="sxs-lookup"><span data-stu-id="d3891-122">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="d3891-123">Wenn Sie nur den Name-Parameter verwenden, müssen Sie Folgendes beachten:</span><span class="sxs-lookup"><span data-stu-id="d3891-123">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="d3891-124">Abhängig von der Anzahl der auf dem Computer installierten Module ist es ein ressourcenintensiver Vorgang.</span><span class="sxs-lookup"><span data-stu-id="d3891-124">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="d3891-125">Es wird die zuerst gefundene Ressource des angegebenen Namens geladen.</span><span class="sxs-lookup"><span data-stu-id="d3891-125">It will load the first resource found with the given name.</span></span> <span data-ttu-id="d3891-126">Falls mehrere Ressourcen mit demselben Namen installiert sind, könnte die falsche Ressource geladen werden.</span><span class="sxs-lookup"><span data-stu-id="d3891-126">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="d3891-127">Wie unten beschrieben sollte `–ModuleName` mit dem `-Name`-Parameter angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="d3891-127">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="d3891-128">Dies bietet folgende Vorteile:</span><span class="sxs-lookup"><span data-stu-id="d3891-128">This usage has the following benefits:</span></span>

- <span data-ttu-id="d3891-129">Durch Begrenzen des Suchbereichs für die angegebene Ressource sind die Auswirkungen auf die Leistung geringer.</span><span class="sxs-lookup"><span data-stu-id="d3891-129">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="d3891-130">Durch Definieren der Ressource wird das Modul explizit definiert und sichergestellt, dass die richtige Ressource geladen wird.</span><span class="sxs-lookup"><span data-stu-id="d3891-130">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="d3891-131">In PowerShell 5.0 können DSC-Ressourcen mehrere Versionen haben, und verschiedene Versionen können parallel auf einem Computer installiert sein.</span><span class="sxs-lookup"><span data-stu-id="d3891-131">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="d3891-132">Dies wird dadurch implementiert, dass mehrere Versionen eines Ressourcenmoduls vorhanden sind, die sich im selben Modulordner befinden.</span><span class="sxs-lookup"><span data-stu-id="d3891-132">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="d3891-133">Weitere Informationen finden Sie unter [Verwenden von Ressourcen mit mehreren Versionen](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="d3891-133">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="d3891-134">IntelliSense mit Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="d3891-134">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="d3891-135">Beim Erstellen der DSC-Konfiguration in ISE stellt PowerShell IntelliSense für Ressourcen und Ressourceneigenschaften zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="d3891-135">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="d3891-136">Ressourcendefinitionen unter dem `$pshome`-Modulpfad werden automatisch geladen.</span><span class="sxs-lookup"><span data-stu-id="d3891-136">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="d3891-137">Beim Importieren von Ressourcen mithilfe des `Import-DSCResource`-Schlüsselworts werden die angegebenen Ressourcendefinitionen hinzugefügt, und IntelliSense wird erweitert, um das Schema der importierten Ressource einzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="d3891-137">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![IntelliSense für Ressourcen](media/import-dscresource/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="d3891-139">In PowerShell 5.0 wurde der ISE für DSC-Ressourcen und deren Eigenschaften die Vervollständigung mit der TAB-TASTE hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d3891-139">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="d3891-140">Weitere Informationen finden Sie unter [Ressourcen](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="d3891-140">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="d3891-141">Beim Kompilieren der Konfiguration verwendet PowerShell die importierten Ressourcendefinitionen, um alle Ressourcenblöcke in der Konfiguration zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="d3891-141">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="d3891-142">Jeder Ressourcenblock wird mit der Schemadefinition der Ressource auf Einhaltung der folgenden Regeln überprüft.</span><span class="sxs-lookup"><span data-stu-id="d3891-142">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="d3891-143">Nur im Schema definierte Eigenschaften werden verwendet.</span><span class="sxs-lookup"><span data-stu-id="d3891-143">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="d3891-144">Die Datentypen für jede Eigenschaft sind korrekt.</span><span class="sxs-lookup"><span data-stu-id="d3891-144">The data types for each property are correct.</span></span>
- <span data-ttu-id="d3891-145">Schlüsseleigenschaften werden angegeben.</span><span class="sxs-lookup"><span data-stu-id="d3891-145">Keys properties are specified.</span></span>
- <span data-ttu-id="d3891-146">Es wird keine schreibgeschützte Eigenschaft verwendet.</span><span class="sxs-lookup"><span data-stu-id="d3891-146">No read-only property is used.</span></span>
- <span data-ttu-id="d3891-147">Überprüfung von Wertzuordnungstypen.</span><span class="sxs-lookup"><span data-stu-id="d3891-147">Validation on value maps types.</span></span>

<span data-ttu-id="d3891-148">Beachten Sie die folgende Konfiguration:</span><span class="sxs-lookup"><span data-stu-id="d3891-148">Consider the following configuration:</span></span>

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = "Telnet-Client"
            Ensure = "Invalid"
        }
    }
}
```

<span data-ttu-id="d3891-149">Die Kompilierung dieser Konfiguration führt zu einem Fehler.</span><span class="sxs-lookup"><span data-stu-id="d3891-149">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values 'Invalid' is not supported or valid for property 'Ensure' on class 'WindowsFeature'. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="d3891-150">Mit IntelliSense und Schemaüberprüfung können Sie mehr Fehler während Analyse und Kompilierung abfangen und damit Komplikationen während der Runtime vermieden.</span><span class="sxs-lookup"><span data-stu-id="d3891-150">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="d3891-151">Jede DSC-Ressource kann einen Namen haben und einen durch das Schema der Ressource definierten **FriendlyName** (Anzeigenamen).</span><span class="sxs-lookup"><span data-stu-id="d3891-151">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="d3891-152">Im Folgenden sehen Sie ersten beiden Zeilen von „MSFT_ServiceResource.shema.mof“.</span><span class="sxs-lookup"><span data-stu-id="d3891-152">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="d3891-153">Wenn Sie diese Ressource in einer Konfiguration verwenden, können Sie **MSFT_ServiceResource** oder **Service** angeben.</span><span class="sxs-lookup"><span data-stu-id="d3891-153">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="d3891-154">Unterschiede zwischen PowerShell v4 und v5</span><span class="sxs-lookup"><span data-stu-id="d3891-154">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="d3891-155">Wenn Sie Konfigurationen in PowerShell 4.0 und PowerShell 5.0 und höher erstellen, werden Ihnen mehrere Unterschiede auffallen.</span><span class="sxs-lookup"><span data-stu-id="d3891-155">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="d3891-156">In diesem Abschnitt werden die Unterschiede hervorgehoben, die für diesen Artikel relevant sind.</span><span class="sxs-lookup"><span data-stu-id="d3891-156">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="d3891-157">Mehrere Versionen der Ressource</span><span class="sxs-lookup"><span data-stu-id="d3891-157">Multiple Resource Versions</span></span>

<span data-ttu-id="d3891-158">Das parallele Installieren und Verwenden mehrerer Versionen von Ressourcen wurde in PowerShell 4.0 nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d3891-158">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="d3891-159">Wenn beim Importieren von Ressourcen in Ihre Konfiguration Probleme auftreten, stellen Sie sicher, dass Sie nur eine Version der Ressource installiert haben.</span><span class="sxs-lookup"><span data-stu-id="d3891-159">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="d3891-160">In der folgenden Abbildung sind zwei Versionen des **xPSDesiredStateConfiguration**-Moduls installiert.</span><span class="sxs-lookup"><span data-stu-id="d3891-160">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Problembehebung bei mehreren Versionen einer Ressource](media/import-dscresource/multiple-resource-versions-broken.png)

<span data-ttu-id="d3891-162">Kopieren Sie den Inhalt Ihrer gewünschten Modulversion in die oberste Ebene des Modulverzeichnisses.</span><span class="sxs-lookup"><span data-stu-id="d3891-162">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Problembehebung bei mehreren Versionen einer Ressource](media/import-dscresource/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a><span data-ttu-id="d3891-164">Ressourcenspeicherort</span><span class="sxs-lookup"><span data-stu-id="d3891-164">Resource location</span></span>

<span data-ttu-id="d3891-165">Beim Erstellen und Kompilieren von Konfigurationen können Ihre Ressourcen in einem beliebigen, durch Ihren [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path) angegebenen Verzeichnis gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="d3891-165">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="d3891-166">In PowerShell 4.0 erfordert der LCM, dass alle DSC-Ressourcenmodule unter „Programme\WindowsPowerShell\Modules“ oder `$pshome\Modules` gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="d3891-166">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="d3891-167">Seit PowerShell 5.0 besteht diese Anforderung nicht mehr, und Ressourcenmodule können in einem beliebigen durch `PSModulePath` angegebenen Verzeichnis gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="d3891-167">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

### <a name="moduleversion-added"></a><span data-ttu-id="d3891-168">ModuleVersion hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="d3891-168">ModuleVersion added</span></span>

<span data-ttu-id="d3891-169">Ab PowerShell 5.0 können Sie mit dem `-ModuleVersion`-Parameter angeben, welche Version eines Moduls in der Konfiguration verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="d3891-169">Beginning in PowerShell 5.0, the `-ModuleVersion` parameter allows you to specify which version of a module to use within your configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3891-170">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d3891-170">See also</span></span>

- [<span data-ttu-id="d3891-171">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="d3891-171">Resources</span></span>](../resources/resources.md)
