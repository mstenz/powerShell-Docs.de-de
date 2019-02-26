---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Verwenden von Import-DscResource
ms.openlocfilehash: ee0b2f0469c6507c8f0148138198597a9e57cdd7
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803411"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="aab4a-103">Verwenden von Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="aab4a-103">Using Import-DSCResource</span></span>

<span data-ttu-id="aab4a-104">`Import-DScResource` ist ein Schlüsselwort "dynamic", die nur innerhalb eines Skriptblocks Konfiguration verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="aab4a-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="aab4a-105">Die `Import-DSCResource` Schlüsselwort, um alle Ressourcen in Ihrer Konfiguration erforderlich sind, zu importieren.</span><span class="sxs-lookup"><span data-stu-id="aab4a-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="aab4a-106">Ressourcen, die unter `$pshome` werden automatisch importiert, aber es dennoch als bewährte Methode, die alle verwendete Ressourcen explizit Importieren Ihrer [Konfiguration](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="aab4a-106">Resources under `$pshome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="aab4a-107">Die Syntax für `Import-DSCResource` ist unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="aab4a-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="aab4a-108">Wenn Sie Module mit Namen angeben, ist es eine Anforderung, um die einzelnen in einer neuen Zeile aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="aab4a-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|<span data-ttu-id="aab4a-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="aab4a-109">Parameter</span></span>  |<span data-ttu-id="aab4a-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="aab4a-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="aab4a-111">Den Namen der DSC-Ressource, die Sie importieren müssen.</span><span class="sxs-lookup"><span data-stu-id="aab4a-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="aab4a-112">Wenn Sie der Namen des Moduls angegeben wird, durchsucht der Befehl, um diese DSC-Ressourcen innerhalb dieses Moduls; Andernfalls sucht der Befehl die DSC-Ressourcen in allen Pfaden der DSC-Ressource.</span><span class="sxs-lookup"><span data-stu-id="aab4a-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="aab4a-113">Platzhalter werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="aab4a-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="aab4a-114">Der Modulname oder Modul-Spezifikation.</span><span class="sxs-lookup"><span data-stu-id="aab4a-114">The module name, or module specification.</span></span>  <span data-ttu-id="aab4a-115">Bei Angabe von Ressourcen, die von einem Modul zu importieren. versucht der Befehl, nur die Ressourcen zu importieren.</span><span class="sxs-lookup"><span data-stu-id="aab4a-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="aab4a-116">Wenn Sie das Modul nur angeben, importiert der Befehl alle DSC-Ressourcen im Modul an.</span><span class="sxs-lookup"><span data-stu-id="aab4a-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="aab4a-117">Beispiel: Mit Import-DSCResource in einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="aab4a-117">Example: Use Import-DSCResource within a configuration</span></span>

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
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> <span data-ttu-id="aab4a-118">Mehrere Werte für Namen von Ressourcen und Module im selben Befehl angeben, werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="aab4a-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="aab4a-119">Sie haben nicht deterministische Verhalten in Bezug auf die Ressource, von welchem Modul geladen wird, für den Fall, dass dieselbe Ressource in mehrere Module vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="aab4a-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="aab4a-120">Folgenden Befehl aus, führt zu Fehler während der Kompilierung.</span><span class="sxs-lookup"><span data-stu-id="aab4a-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="aab4a-121">Folgendes in Betracht, wenn Sie nur den Name-Parameter verwenden:</span><span class="sxs-lookup"><span data-stu-id="aab4a-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="aab4a-122">Es ist ein ressourcenintensiver Vorgang abhängig von der Anzahl der Module, die auf dem Computer installiert.</span><span class="sxs-lookup"><span data-stu-id="aab4a-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="aab4a-123">Es lädt die erste Ressource mit dem angegebenen Namen gefunden.</span><span class="sxs-lookup"><span data-stu-id="aab4a-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="aab4a-124">Bei mehr als eine Ressource mit demselben Namen, die installiert wird, konnte es falsche Ressource geladen.</span><span class="sxs-lookup"><span data-stu-id="aab4a-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="aab4a-125">Die empfohlene Verwendung ist an `–ModuleName` mit der `-Name` Parameter, wie unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="aab4a-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="aab4a-126">Diese Verwendung hat die folgenden Vorteile:</span><span class="sxs-lookup"><span data-stu-id="aab4a-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="aab4a-127">Es verringert die Auswirkungen auf die Leistung begrenzen den Suchbereich für die angegebene Ressource.</span><span class="sxs-lookup"><span data-stu-id="aab4a-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="aab4a-128">Das Modul definieren die Ressource, um sicherzustellen, dass die richtige Ressource geladen wird definiert explizit.</span><span class="sxs-lookup"><span data-stu-id="aab4a-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="aab4a-129">In PowerShell 5.0 können DSC-Ressourcen mehrere Versionen haben, und verschiedene Versionen können parallel auf einem Computer installiert sein.</span><span class="sxs-lookup"><span data-stu-id="aab4a-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="aab4a-130">Dies wird dadurch implementiert, dass mehrere Versionen eines Ressourcenmoduls vorhanden sind, die sich im selben Modulordner befinden.</span><span class="sxs-lookup"><span data-stu-id="aab4a-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="aab4a-131">Weitere Informationen finden Sie unter [Verwenden von Ressourcen mit mehreren Versionen](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="aab4a-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="aab4a-132">IntelliSense mit Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="aab4a-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="aab4a-133">Beim Erstellen der DSC-Konfigurations in der ISE bietet PowerShell IntelliSense für Ressourcen und Ressourceneigenschaften.</span><span class="sxs-lookup"><span data-stu-id="aab4a-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="aab4a-134">Ressourcendefinitionen unter der `$pshome` Modulpfad automatisch geladen werden.</span><span class="sxs-lookup"><span data-stu-id="aab4a-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="aab4a-135">Beim Importieren von Ressourcen mithilfe der `Import-DSCResource` -Schlüsselwort, die Definitionen für die angegebene Ressource hinzugefügt werden und Intellisense wird erweitert, um die importierte Ressource Schema enthalten.</span><span class="sxs-lookup"><span data-stu-id="aab4a-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![Intellisense für Ressourcen](/media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="aab4a-137">PowerShell 5.0 ab, wurde Tab-Vervollständigung der ISE für DSC-Ressourcen und deren Eigenschaften hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="aab4a-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="aab4a-138">Weitere Informationen finden Sie unter [Ressourcen](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="aab4a-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="aab4a-139">Beim Kompilieren der Konfiguration, verwendet PowerShell die Definitionen für importierte Ressource, um alle ressourcenblöcken in der Konfiguration zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="aab4a-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="aab4a-140">Jedem Ressourcenblock wird überprüft, mit der Schemadefinition der Ressource, für die folgenden Regeln.</span><span class="sxs-lookup"><span data-stu-id="aab4a-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="aab4a-141">Nur Eigenschaften, die im Schema definiert wird.</span><span class="sxs-lookup"><span data-stu-id="aab4a-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="aab4a-142">Die Datentypen für jede Eigenschaft sind korrekt.</span><span class="sxs-lookup"><span data-stu-id="aab4a-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="aab4a-143">Eigenschaften von Schlüsseln werden angegeben.</span><span class="sxs-lookup"><span data-stu-id="aab4a-143">Keys properties are specified.</span></span>
- <span data-ttu-id="aab4a-144">Keine nur-Lese Eigenschaft wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="aab4a-144">No read-only property is used.</span></span>
- <span data-ttu-id="aab4a-145">Überprüfung auf dem Wert werden die Datentypen zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="aab4a-145">Validation on value maps types.</span></span>

<span data-ttu-id="aab4a-146">Beachten Sie die folgende Konfiguration ein:</span><span class="sxs-lookup"><span data-stu-id="aab4a-146">Consider the following configuration:</span></span>

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
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

<span data-ttu-id="aab4a-147">Kompilieren diese Konfiguration führt zu einem Fehler.</span><span class="sxs-lookup"><span data-stu-id="aab4a-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="aab4a-148">IntelliSense und der schemaüberprüfung können Sie weitere Fehler während der Analyse und Kompilierung, Abfangen Komplikationen zur Laufzeit vermieden.</span><span class="sxs-lookup"><span data-stu-id="aab4a-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="aab4a-149">Jede DSC-Ressource kann einen Namen haben, und ein **FriendlyName** durch die der Ressource Schema definiert wird.</span><span class="sxs-lookup"><span data-stu-id="aab4a-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="aab4a-150">Im folgenden sind die ersten beiden Zeilen von "MSFT_ServiceResource.shema.mof".</span><span class="sxs-lookup"><span data-stu-id="aab4a-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="aab4a-151">Wenn Sie diese Ressource in einer Konfiguration verwenden, können Sie angeben **MSFT_ServiceResource** oder **Service**.</span><span class="sxs-lookup"><span data-stu-id="aab4a-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="aab4a-152">PowerShell-v4- und v5-Unterschiede</span><span class="sxs-lookup"><span data-stu-id="aab4a-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="aab4a-153">Es gibt mehrere Unterschiede, die Sie sehen, wenn Konfigurationen in PowerShell 4.0 im Vergleich zu erstellen. PowerShell 5.0 und höher.</span><span class="sxs-lookup"><span data-stu-id="aab4a-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="aab4a-154">In diesem Abschnitt werden die Unterschiede hervorgehoben, dass für diesen Artikel relevant angezeigt.</span><span class="sxs-lookup"><span data-stu-id="aab4a-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="aab4a-155">Mehrere Versionen der Ressource</span><span class="sxs-lookup"><span data-stu-id="aab4a-155">Multiple Resource Versions</span></span>

<span data-ttu-id="aab4a-156">Installieren und verwenden mehrere Versionen der Ressourcen-Seite-an-Seite wurde in PowerShell 4.0 nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="aab4a-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="aab4a-157">Wenn Sie das Importieren von Ressourcen in Ihrer Konfiguration Probleme feststellen, stellen Sie sicher, dass Sie nur eine Version der Ressource installiert haben.</span><span class="sxs-lookup"><span data-stu-id="aab4a-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="aab4a-158">In der Abbildung unten, zwei Versionen der **"xpsdesiredstateconfiguration"** -Modul installiert werden.</span><span class="sxs-lookup"><span data-stu-id="aab4a-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Mehrere Ressourcen Versionen behoben](/media/multiple-resource-versions-broken.md)

<span data-ttu-id="aab4a-160">Kopieren Sie den Inhalt Ihrer gewünschten Module-Version, auf der obersten Ebene des Modulverzeichnisses.</span><span class="sxs-lookup"><span data-stu-id="aab4a-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Mehrere Ressourcen Versionen behoben](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a><span data-ttu-id="aab4a-162">Ressourcenspeicherort</span><span class="sxs-lookup"><span data-stu-id="aab4a-162">Resource location</span></span>

<span data-ttu-id="aab4a-163">Beim Erstellen und Kompilieren von Konfigurationen, können Ihre Ressourcen gespeichert werden, in einem Verzeichnis, die gemäß Ihrer [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="aab4a-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="aab4a-164">In PowerShell 4.0 erfordert der LCM alle DSC-ressourcenmodulen unter "Programm Files\WindowsPowerShell\Modules" gespeichert werden oder `$pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="aab4a-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="aab4a-165">Ab in PowerShell 5.0 ist diese Anforderung wurde entfernt und Ressourcenmodule können gespeichert werden, in einem Verzeichnis anhand des `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="aab4a-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="aab4a-166">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="aab4a-166">See also</span></span>

- [<span data-ttu-id="aab4a-167">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="aab4a-167">Resources</span></span>](../resources/resources.md)
