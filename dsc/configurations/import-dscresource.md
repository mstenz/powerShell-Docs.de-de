---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Verwenden von Import-DscResource
ms.openlocfilehash: 6bc3c1aa1d34a05e3188666da825322235c0672e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401592"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="c5fd6-103">Verwenden von Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="c5fd6-103">Using Import-DSCResource</span></span>

<span data-ttu-id="c5fd6-104">`Import-DScResource` ist ein Schlüsselwort "dynamic", die nur innerhalb eines Skriptblocks Konfiguration verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="c5fd6-105">Die `Import-DSCResource` Schlüsselwort, um alle Ressourcen in Ihrer Konfiguration erforderlich sind, zu importieren.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="c5fd6-106">Ressourcen, die unter `$phsome` werden automatisch importiert, aber es dennoch als bewährte Methode, die alle verwendete Ressourcen explizit Importieren Ihrer [Konfiguration](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="c5fd6-106">Resources under `$phsome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="c5fd6-107">Die Syntax für `Import-DSCResource` ist unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-107">The syntax for `Import-DSCResource` is shown below.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>]
```

|<span data-ttu-id="c5fd6-108">Parameter</span><span class="sxs-lookup"><span data-stu-id="c5fd6-108">Parameter</span></span>  |<span data-ttu-id="c5fd6-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c5fd6-109">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="c5fd6-110">Den Namen der DSC-Ressource, die Sie importieren müssen.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-110">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="c5fd6-111">Wenn Sie der Namen des Moduls angegeben wird, durchsucht der Befehl, um diese DSC-Ressourcen innerhalb dieses Moduls; Andernfalls sucht der Befehl die DSC-Ressourcen in allen Pfaden der DSC-Ressource.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-111">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="c5fd6-112">Platzhalter werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-112">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="c5fd6-113">Der Container-Module-Namen oder Modul Spezifikation(en).</span><span class="sxs-lookup"><span data-stu-id="c5fd6-113">The container module name(s), or module specification(s).</span></span>  <span data-ttu-id="c5fd6-114">Bei Angabe von Ressourcen, die von einem Modul zu importieren. versucht der Befehl, nur die Ressourcen zu importieren.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-114">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="c5fd6-115">Wenn Sie das Modul nur angeben, importiert der Befehl alle DSC-Ressourcen im Modul an.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-115">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

<span data-ttu-id="c5fd6-116">Sie können Platzhalterzeichen mit dem `-Name` Parameter bei Verwendung `Import-DSCResource`.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-116">You can use wildcards with the `-Name` parameter when using `Import-DSCResource`.</span></span>

```powershell
Import-DscResource -Name * -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="c5fd6-117">Beispiel: Verwenden Sie Import-DSCResource in einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="c5fd6-117">Example: Use Import-DSCResource within a configuration</span></span>

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName MS_DSC1 -name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    Import-DSCResource -Name File, TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
...
```

> [!NOTE]
> <span data-ttu-id="c5fd6-118">Mehrere Werte für Namen von Ressourcen und Module im selben Befehl angeben, werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="c5fd6-119">Sie haben nicht deterministische Verhalten in Bezug auf die Ressource, von welchem Modul geladen wird, für den Fall, dass dieselbe Ressource in mehrere Module vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="c5fd6-120">Folgenden Befehl aus, führt zu Fehler während der Kompilierung.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="c5fd6-121">Folgendes in Betracht, wenn Sie nur den Name-Parameter verwenden:</span><span class="sxs-lookup"><span data-stu-id="c5fd6-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="c5fd6-122">Es ist ein ressourcenintensiver Vorgang abhängig von der Anzahl der Module, die auf dem Computer installiert.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="c5fd6-123">Es lädt die erste Ressource mit dem angegebenen Namen gefunden.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="c5fd6-124">Bei mehr als eine Ressource mit demselben Namen, die installiert wird, konnte es falsche Ressource geladen.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="c5fd6-125">Die empfohlene Verwendung ist an `–ModuleName` mit der `-Name` Parameter, wie unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="c5fd6-126">Diese Verwendung hat die folgenden Vorteile:</span><span class="sxs-lookup"><span data-stu-id="c5fd6-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="c5fd6-127">Es verringert die Auswirkungen auf die Leistung begrenzen den Suchbereich für die angegebene Ressource.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="c5fd6-128">Das Modul definieren die Ressource, um sicherzustellen, dass die richtige Ressource geladen wird definiert explizit.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="c5fd6-129">In PowerShell 5.0 können DSC-Ressourcen mehrere Versionen haben, und verschiedene Versionen können parallel auf einem Computer installiert sein.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="c5fd6-130">Dies wird dadurch implementiert, dass mehrere Versionen eines Ressourcenmoduls vorhanden sind, die sich im selben Modulordner befinden.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="c5fd6-131">Weitere Informationen finden Sie unter [Verwenden von Ressourcen mit mehreren Versionen](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="c5fd6-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="c5fd6-132">IntelliSense mit Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="c5fd6-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="c5fd6-133">Beim Erstellen der DSC-Konfigurations in der ISE bietet PowerShell IntelliSense für Ressourcen und Ressourceneigenschaften.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="c5fd6-134">Ressourcendefinitionen unter der `$pshome` Modulpfad automatisch geladen werden.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="c5fd6-135">Beim Importieren von Ressourcen mithilfe der `Import-DSCResource` -Schlüsselwort, die Definitionen für die angegebene Ressource hinzugefügt werden und Intellisense wird erweitert, um die importierte Ressource Schema enthalten.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![Intellisense für Ressourcen](/media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="c5fd6-137">PowerShell 5.0 ab, wurde Tab-Vervollständigung der ISE für DSC-Ressourcen und deren Eigenschaften hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="c5fd6-138">Weitere Informationen finden Sie unter [Ressourcen](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="c5fd6-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="c5fd6-139">Beim Kompilieren der Konfiguration, verwendet PowerShell die Definitionen für importierte Ressource, um alle ressourcenblöcken in der Konfiguration zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="c5fd6-140">Jedem Ressourcenblock wird überprüft, mit der Schemadefinition der Ressource, für die folgenden Regeln.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="c5fd6-141">Nur Eigenschaften, die im Schema definiert wird.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="c5fd6-142">Die Datentypen für jede Eigenschaft sind korrekt.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="c5fd6-143">Eigenschaften von Schlüsseln werden angegeben.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-143">Keys properties are specified.</span></span>
- <span data-ttu-id="c5fd6-144">Keine nur-Lese Eigenschaft wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-144">No read-only property is used.</span></span>
- <span data-ttu-id="c5fd6-145">Überprüfung auf dem Wert werden die Datentypen zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-145">Validation on value maps types.</span></span>

<span data-ttu-id="c5fd6-146">Beachten Sie die folgende Konfiguration ein:</span><span class="sxs-lookup"><span data-stu-id="c5fd6-146">Consider the following configuration:</span></span>

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

<span data-ttu-id="c5fd6-147">Kompilieren diese Konfiguration führt zu einem Fehler.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="c5fd6-148">IntelliSense und der schemaüberprüfung können Sie weitere Fehler während der Analyse und Kompilierung, Abfangen Komplikationen zur Laufzeit vermieden.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="c5fd6-149">Jede DSC-Ressource kann einen Namen haben, und ein **FriendlyName** durch die der Ressource Schema definiert wird.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="c5fd6-150">Im folgenden sind die ersten beiden Zeilen von "MSFT_ServiceResource.shema.mof".</span><span class="sxs-lookup"><span data-stu-id="c5fd6-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="c5fd6-151">Wenn Sie diese Ressource in einer Konfiguration verwenden, können Sie angeben **MSFT_ServiceResource** oder **Service**.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="c5fd6-152">PowerShell-v4- und v5-Unterschiede</span><span class="sxs-lookup"><span data-stu-id="c5fd6-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="c5fd6-153">Es gibt mehrere Unterschiede, die Sie sehen, wenn Konfigurationen in PowerShell 4.0 im Vergleich zu erstellen. PowerShell 5.0 und höher.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="c5fd6-154">In diesem Abschnitt werden die Unterschiede hervorgehoben, dass für diesen Artikel relevant angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="c5fd6-155">Mehrere Versionen der Ressource</span><span class="sxs-lookup"><span data-stu-id="c5fd6-155">Multiple Resource Versions</span></span>

<span data-ttu-id="c5fd6-156">Installieren und verwenden mehrere Versionen der Ressourcen-Seite-an-Seite wurde in PowerShell 4.0 nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="c5fd6-157">Wenn Sie das Importieren von Ressourcen in Ihrer Konfiguration Probleme feststellen, stellen Sie sicher, dass Sie nur eine Version der Ressource installiert haben.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="c5fd6-158">In der Abbildung unten, zwei Versionen der **"xpsdesiredstateconfiguration"** -Modul installiert werden.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Mehrere Ressourcen Versionen behoben](/media/multiple-resource-versions-broken.md)

<span data-ttu-id="c5fd6-160">Kopieren Sie den Inhalt Ihrer gewünschten Module-Version, auf der obersten Ebene des Modulverzeichnisses.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Mehrere Ressourcen Versionen behoben](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a><span data-ttu-id="c5fd6-162">Ressourcenspeicherort</span><span class="sxs-lookup"><span data-stu-id="c5fd6-162">Resource location</span></span>

<span data-ttu-id="c5fd6-163">Beim Erstellen und Kompilieren von Konfigurationen, können Ihre Ressourcen gespeichert werden, in einem Verzeichnis, die gemäß Ihrer [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="c5fd6-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="c5fd6-164">In PowerShell 4.0 erfordert der LCM alle DSC-ressourcenmodulen unter "Programm Files\WindowsPowerShell\Modules" gespeichert werden oder `$pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="c5fd6-165">Ab in PowerShell 5.0 ist diese Anforderung wurde entfernt und Ressourcenmodule können gespeichert werden, in einem Verzeichnis anhand des `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="c5fd6-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5fd6-166">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c5fd6-166">See also</span></span>

- [<span data-ttu-id="c5fd6-167">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="c5fd6-167">Resources</span></span>](../resources/resources.md)
