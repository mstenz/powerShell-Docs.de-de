---
ms.date: 12/12/2018
keywords: DSC, Powershell, Resource, Katalog, setup
title: Hinzufügen von Parametern zu einer Konfiguration
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401430"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="48437-103">Hinzufügen von Parametern zu einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="48437-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="48437-104">Ebenso wie Funktionen, [Konfigurationen](configurations.md) parametrisiert werden können, um mehr dynamische Konfigurationen, die auf Grundlage der Benutzereingabe zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="48437-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="48437-105">Die Schritte ähneln jenen in [Funktionen mit Parametern](/powershell/module/microsoft.powershell.core/about/about_functions).</span><span class="sxs-lookup"><span data-stu-id="48437-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="48437-106">Dieses Beispiel beginnt mit einer einfachen Konfiguration, die den "Spooler" Dienst "Ausgeführt wird" konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="48437-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="48437-107">Integrierte Konfiguration-Parameter</span><span class="sxs-lookup"><span data-stu-id="48437-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="48437-108">Im Gegensatz zu einer Funktion jedoch die [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) -Attribut fügt keine Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="48437-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="48437-109">Zusätzlich zu [allgemeine Parameter](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Konfigurationen können auch die folgenden integrierten in-Parameter, ohne dass Sie sie definieren.</span><span class="sxs-lookup"><span data-stu-id="48437-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="48437-110">Parameter</span><span class="sxs-lookup"><span data-stu-id="48437-110">Parameter</span></span>  |<span data-ttu-id="48437-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="48437-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="48437-112">Bei der Definition verwendet [zusammengesetzten Konfigurationen](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="48437-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="48437-113">Bei der Definition verwendet [zusammengesetzten Konfigurationen](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="48437-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="48437-114">Bei der Definition verwendet [zusammengesetzten Konfigurationen](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="48437-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="48437-115">Zum Übergeben von in strukturierten [Konfigurationsdaten](configData.md) für die Verwendung in der Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="48437-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="48437-116">Zum angeben, wo Ihre "\<Computername\>.mof" Datei kompiliert wird</span><span class="sxs-lookup"><span data-stu-id="48437-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="48437-117">Hinzufügen von Ihren eigenen Parametern an Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="48437-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="48437-118">Neben den integrierten-Standardparametern können Sie auch Ihren eigenen Parametern an, Ihre Konfigurationen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="48437-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="48437-119">Der Parameterblock wird direkt in der Deklaration der Konfiguration, wie eine Funktion.</span><span class="sxs-lookup"><span data-stu-id="48437-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="48437-120">Ein Konfigurationsblock-Parameter muss außerhalb einer **Knoten** Deklarationen und über allen *importieren* Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="48437-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="48437-121">Durch Hinzufügen von Parametern, können Sie Ihre Konfigurationen robuster und dynamisches vornehmen.</span><span class="sxs-lookup"><span data-stu-id="48437-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="48437-122">Fügen Sie einen "Computername"-Parameter hinzu.</span><span class="sxs-lookup"><span data-stu-id="48437-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="48437-123">Der erste Parameter, die Sie möglicherweise hinzufügen, ist eine `-Computername` an, damit Sie dynamisch eine "MOF"-Datei für eine beliebige kompilieren können, `-Computername` Sie Ihrer Konfiguration übergeben.</span><span class="sxs-lookup"><span data-stu-id="48437-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="48437-124">Wie Functions können Sie auch einen Standardwert definieren für den Fall, dass der Benutzer einen Wert für nicht erfüllt `-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="48437-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="48437-125">Anschließend können Sie angeben, in Ihrer Konfiguration können Ihre `-ComputerName` Parameter, wenn Sie Ihre "Node"-Block zu definieren.</span><span class="sxs-lookup"><span data-stu-id="48437-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="48437-126">Rufen Sie Ihre Konfiguration mit Parametern</span><span class="sxs-lookup"><span data-stu-id="48437-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="48437-127">Nachdem Sie die Konfiguration Parameter hinzugefügt haben, können Sie sie genau so wie Sie mit einem Cmdlet verwenden.</span><span class="sxs-lookup"><span data-stu-id="48437-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="48437-128">Kompilieren mehrere MOF-Dateien</span><span class="sxs-lookup"><span data-stu-id="48437-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="48437-129">Der "Node"-Block kann auch eine durch Trennzeichen getrennte Liste von Computernamen annehmen und "MOF"-Dateien für die einzelnen generiert.</span><span class="sxs-lookup"><span data-stu-id="48437-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="48437-130">Sie können das folgende Beispiel zum Generieren von "MOF"-Dateien für alle Computer, die an Ausführen der `-ComputerName` Parameter.</span><span class="sxs-lookup"><span data-stu-id="48437-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="48437-131">Erweiterte Parameter in Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="48437-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="48437-132">Zusätzlich zu einem `-ComputerName` Parameter, wir können die Parameter für den Dienstnamen und den Zustand hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="48437-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="48437-133">Das folgende Beispiel fügt einen Parameterblock mit einer `-ServiceName` Parameter und verwendet, um dynamisch zu definieren die **Service** Ressourcenblock.</span><span class="sxs-lookup"><span data-stu-id="48437-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="48437-134">Auch eine `-State` Parameter, um dynamisch zu definieren die **Zustand** in die **Service** Ressourcenblock.</span><span class="sxs-lookup"><span data-stu-id="48437-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="48437-135">In weitere Advacned Szenarien kann es sinnvoller, dynamische Daten in eine strukturierte verschieben, [Konfigurationsdaten](configData.md).</span><span class="sxs-lookup"><span data-stu-id="48437-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="48437-136">In diesem Beispiel Konfiguration jetzt wird eine dynamische `$ServiceName`, aber wenn nicht angegeben wurde, kompilieren führt zu einem Fehler.</span><span class="sxs-lookup"><span data-stu-id="48437-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="48437-137">Sie können einen Standardwert wie im folgenden Beispiel hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="48437-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="48437-138">In diesem Fall allerdings es ist sinnvoller, einfach erzwingen, dass die Benutzer geben Sie einen Wert für die `$ServiceName` Parameter.</span><span class="sxs-lookup"><span data-stu-id="48437-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="48437-139">Die `parameter` Attribut können Sie nun Unterstützung für weitere Überprüfung und die Pipeline an die Konfiguration der Parameter.</span><span class="sxs-lookup"><span data-stu-id="48437-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="48437-140">Fügen Sie vor jeder Parameterdeklaration der `parameter` Attributblock, wie im folgenden Beispiel.</span><span class="sxs-lookup"><span data-stu-id="48437-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="48437-141">Sie können angeben, dass Argumente für jede `parameter` -Attribut, um die Kontrolle einiger Aspekte der definierten Parameter.</span><span class="sxs-lookup"><span data-stu-id="48437-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="48437-142">Im folgenden Beispiel wird die `$ServiceName` eine **obligatorisch** Parameter.</span><span class="sxs-lookup"><span data-stu-id="48437-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="48437-143">Für die `$State` Parameter würden wir gerne, dass Benutzer von der Angabe von Werten außerhalb eines vordefinierten Satzes (z. B. wird ausgeführt, beendet) der `ValidationSet*`Attribut würde verhindern, dass den Benutzer angeben von Werten außerhalb eines vordefinierten Satzes (z. B. wird ausgeführt, Beendet).</span><span class="sxs-lookup"><span data-stu-id="48437-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="48437-144">Im folgenden Beispiel wird die `ValidationSet` -Attribut auf die `$State` Parameter.</span><span class="sxs-lookup"><span data-stu-id="48437-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="48437-145">Da wir nicht, stellen möchten die `$State` Parameter **obligatorisch**, wir müssen einen Standardwert für die sie hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="48437-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="48437-146">Sie müssen sich nicht an eine `parameter` -Attribut bei Verwendung einer `validation` Attribut.</span><span class="sxs-lookup"><span data-stu-id="48437-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="48437-147">Erfahren Sie mehr über die `parameter` und bei Validierungsattributen im [About_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="48437-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="48437-148">Vollständig parametrisierter Konfiguration</span><span class="sxs-lookup"><span data-stu-id="48437-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="48437-149">Wir verfügen jetzt über eine parametrisierte Konfiguration, die erzwingt, den Benutzer dass an eine `-InstanceName`, `-ServiceName`, und überprüft die `-State` Parameter.</span><span class="sxs-lookup"><span data-stu-id="48437-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="48437-150">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="48437-150">See also</span></span>

- [<span data-ttu-id="48437-151">Schreiben von Hilfe für DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="48437-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="48437-152">Dynamische Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="48437-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="48437-153">Verwenden von Konfigurationsdaten in Ihren Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="48437-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="48437-154">Separate Daten für Konfigurations- und Umgebungsdaten</span><span class="sxs-lookup"><span data-stu-id="48437-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
