---
ms.date: 12/12/2018
keywords: DSC,PowerShell,Ressource,Katalog,Setup
title: Hinzufügen von Parametern zu einer Konfiguration
ms.openlocfilehash: 9dd9f2be58c13840be2b24e7e21a0d4af79b67cc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80263151"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="6b486-103">Hinzufügen von Parametern zu einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="6b486-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="6b486-104">Ebenso wie Funktionen können [Konfigurationen](configurations.md) parametrisiert werden können, sodass dynamischere Konfigurationen auf Grundlage der Benutzereingabe möglich sind.</span><span class="sxs-lookup"><span data-stu-id="6b486-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="6b486-105">Die Schritte ähneln den in [Funktionen mit Parametern](/powershell/module/microsoft.powershell.core/about/about_functions) beschriebenen.</span><span class="sxs-lookup"><span data-stu-id="6b486-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="6b486-106">Dieses Beispiel beginnt mit einer einfachen Konfiguration, die den „Spooler“-Dienst als „Wird ausgeführt“ konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="6b486-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to explicitly import any required resources or modules.
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

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="6b486-107">Integrierte Konfigurationsparameter</span><span class="sxs-lookup"><span data-stu-id="6b486-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="6b486-108">Im Gegensatz zu einer Funktion fügt das [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute)-Attribut jedoch keine Funktionalität hinzu.</span><span class="sxs-lookup"><span data-stu-id="6b486-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="6b486-109">Zusätzlich zu [allgemeinen Parametern](/powershell/module/microsoft.powershell.core/about/about_commonparameters) können Konfigurationen auch die folgenden integrierten Parameter verwenden, ohne dass Sie sie definieren müssen.</span><span class="sxs-lookup"><span data-stu-id="6b486-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|        <span data-ttu-id="6b486-110">Parameter</span><span class="sxs-lookup"><span data-stu-id="6b486-110">Parameter</span></span>        |                                         <span data-ttu-id="6b486-111">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="6b486-111">Description</span></span>                                          |
| ----------------------- | -------------------------------------------------------------------------------------------- |
| `-InstanceName`         | <span data-ttu-id="6b486-112">Zur Definition [zusammengesetzter Konfigurationen](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="6b486-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>                             |
| `-DependsOn`            | <span data-ttu-id="6b486-113">Zur Definition [zusammengesetzter Konfigurationen](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="6b486-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>                             |
| `-PSDSCRunAsCredential` | <span data-ttu-id="6b486-114">Zur Definition [zusammengesetzter Konfigurationen](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="6b486-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>                             |
| `-ConfigurationData`    | <span data-ttu-id="6b486-115">Zur Übergabe strukturierter [Konfigurationsdaten](configData.md) für die Verwendung in der Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6b486-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span> |
| `-OutputPath`           | <span data-ttu-id="6b486-116">Um anzugeben, wo Ihre „\<Computername\>.mof“-Datei kompiliert wird</span><span class="sxs-lookup"><span data-stu-id="6b486-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>                      |

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="6b486-117">Hinzufügen Ihrer eigenen Parameter zu Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="6b486-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="6b486-118">Neben den integrierten Parametern können Sie auch Ihre eigenen Parameter Ihren Konfigurationen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6b486-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span>
<span data-ttu-id="6b486-119">Der Parameterblock wird wie eine Funktion direkt in die Deklaration der Konfiguration eingefügt.</span><span class="sxs-lookup"><span data-stu-id="6b486-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="6b486-120">Ein Konfigurationsparameterblock muss außerhalb von **Node**-Deklarationen und vor jeglichen *import*-Anweisungen platziert werden.</span><span class="sxs-lookup"><span data-stu-id="6b486-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="6b486-121">Durch Hinzufügen von Parametern können Sie Ihre Konfigurationen robuster und dynamischer machen.</span><span class="sxs-lookup"><span data-stu-id="6b486-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="6b486-122">Hinzufügen eines ComputerName-Parameters</span><span class="sxs-lookup"><span data-stu-id="6b486-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="6b486-123">Als ersten Parameter könnten Sie einen `-Computername`-Parameter hinzufügen, sodass Sie dynamisch eine MOF-Datei für einen beliebigen `-Computername` kompilieren können, den Sie Ihrer Konfiguration übergeben.</span><span class="sxs-lookup"><span data-stu-id="6b486-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="6b486-124">Wie bei Funktionen können Sie auch einen Standardwert definieren für den Fall, dass der Benutzer keinen Wert für `-ComputerName` übergibt.</span><span class="sxs-lookup"><span data-stu-id="6b486-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="6b486-125">Anschließend können Sie in Ihrer Konfiguration Ihren `-ComputerName`-Parameter angeben, wenn Sie Ihren Node-Block definieren.</span><span class="sxs-lookup"><span data-stu-id="6b486-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="6b486-126">Aufrufen Ihrer Konfiguration mit Parametern</span><span class="sxs-lookup"><span data-stu-id="6b486-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="6b486-127">Nachdem Sie Ihrer Konfiguration Parameter hinzugefügt haben, können Sie sie genau so wie ein Cmdlet verwenden.</span><span class="sxs-lookup"><span data-stu-id="6b486-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="6b486-128">Kompilieren mehrerer MOF-Dateien</span><span class="sxs-lookup"><span data-stu-id="6b486-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="6b486-129">Der Node-Block kann auch eine durch Trennzeichen getrennte Liste von Computernamen annehmen und generiert für jeden eine MOF-Datei.</span><span class="sxs-lookup"><span data-stu-id="6b486-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="6b486-130">Sie können das folgende Beispiel ausführen, um MOF-Dateien für alle an den `-ComputerName`-Parameter übergebenen Computer zu generieren.</span><span class="sxs-lookup"><span data-stu-id="6b486-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
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

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="6b486-131">Erweiterte Parameter in Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="6b486-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="6b486-132">Zusätzlich zu einem `-ComputerName`-Parameter können wir Parameter für den Dienstnamen und Zustand hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6b486-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span>
<span data-ttu-id="6b486-133">Im folgenden Beispiel wird ein Parameterblock mit einem `-ServiceName`-Parameter hinzugefügt und verwendet, um den **Service**-Ressourcenblock dynamisch zu definieren.</span><span class="sxs-lookup"><span data-stu-id="6b486-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="6b486-134">Es wird auch ein `-State`-Parameter hinzugefügt, um den **State** (Zustand) im **Service**-Ressourcenblock dynamisch zu definieren.</span><span class="sxs-lookup"><span data-stu-id="6b486-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

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

    # It is best practice to explicitly import any required resources or modules.
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
> <span data-ttu-id="6b486-135">In fortgeschritteneren Szenarien könnte es sinnvoller sein, dynamische Daten in strukturierte [Konfigurationsdaten](configData.md) zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="6b486-135">In more advanced scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="6b486-136">Die Beispielkonfiguration nimmt einen dynamischen `$ServiceName` an, aber wenn er nicht angegeben wird, tritt beim Kompilieren ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="6b486-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="6b486-137">Sie können einen Standardwert wie im folgenden Beispiel hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6b486-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="6b486-138">In diesem Fall ist es allerdings sinnvoller, vom Benutzer einfach die Eingabe eines Werts für den `$ServiceName`-Parameter zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="6b486-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="6b486-139">Mit dem `parameter`-Attribut können Sie die Überprüfungs- und Pipelineunterstützung durch die Parameter Ihrer Konfiguration erweitern.</span><span class="sxs-lookup"><span data-stu-id="6b486-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="6b486-140">Fügen Sie vor jeder Parameterdeklaration wie im folgenden Beispiel den `parameter`-Attributblock ein.</span><span class="sxs-lookup"><span data-stu-id="6b486-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="6b486-141">Sie können für jedes `parameter`-Attribut Argumente angeben, um die Aspekte der definierten Parameter zu steuern.</span><span class="sxs-lookup"><span data-stu-id="6b486-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="6b486-142">Im folgenden Beispiel wird `$ServiceName` zu einem **Mandatory**-Parameter.</span><span class="sxs-lookup"><span data-stu-id="6b486-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="6b486-143">Wir möchten verhindern, dass der Benutzer für den `$State`-Parameter außerhalb eines vordefinierten Satzes (z.B. „Running“, „Stopped“) liegende Werte angibt, und verwenden hierzu das `ValidationSet*`-Attribut.</span><span class="sxs-lookup"><span data-stu-id="6b486-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="6b486-144">Im folgenden Beispiel wird das `ValidationSet`-Attribut dem `$State`-Parameter hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="6b486-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="6b486-145">Da wir den `$State`-Parameter nicht zu einem **Mandatory**-Parameter machen möchten, müssen wir für ihn einen Standardwert hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6b486-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="6b486-146">Sie müssen kein `parameter`-Attribut angeben, wenn Sie ein `validation`-Attribut verwenden.</span><span class="sxs-lookup"><span data-stu-id="6b486-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="6b486-147">Weitere Informationen über `parameter` und Validierungsattribute finden Sie unter [Informationen zu Parametern erweiterter Funktionen](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span><span class="sxs-lookup"><span data-stu-id="6b486-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="6b486-148">Vollständig parametrisierte Konfiguration</span><span class="sxs-lookup"><span data-stu-id="6b486-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="6b486-149">Wir verfügen jetzt über eine parametrisierte Konfiguration, die vom Benutzer die Eingabe von `-InstanceName` und `-ServiceName` erzwingt und den `-State`-Parameter überprüft.</span><span class="sxs-lookup"><span data-stu-id="6b486-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

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

    # It is best practice to explicitly import any required resources or modules.
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

## <a name="see-also"></a><span data-ttu-id="6b486-150">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6b486-150">See also</span></span>

- [<span data-ttu-id="6b486-151">Schreiben von Hilfe für DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="6b486-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="6b486-152">Bedingte Anweisungen und Schleifen in Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="6b486-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="6b486-153">Verwenden von Konfigurationsdaten in DSC</span><span class="sxs-lookup"><span data-stu-id="6b486-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="6b486-154">Trennen von Konfiguration und Umgebungsdaten</span><span class="sxs-lookup"><span data-stu-id="6b486-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
