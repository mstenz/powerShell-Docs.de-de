---
title: Schreiben von Hilfe für PowerShell-Module
ms.date: 04/10/2020
ms.openlocfilehash: 115ea3f3c5941e74ed6ddbc8480d4a21576bc5c6
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893066"
---
# <a name="writing-help-for-powershell-modules"></a><span data-ttu-id="2abc0-102">Schreiben von Hilfe für PowerShell-Module</span><span class="sxs-lookup"><span data-stu-id="2abc0-102">Writing Help for PowerShell Modules</span></span>

<span data-ttu-id="2abc0-103">PowerShell-Module können Hilfe Themen über das Modul und über die Modulmember enthalten, wie z. b. Cmdlets, Anbieter, Funktionen und Skripts.</span><span class="sxs-lookup"><span data-stu-id="2abc0-103">PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="2abc0-104">Das `Get-Help` -Cmdlet zeigt die Modul Hilfe Themen im gleichen Format an, in dem die Hilfe für andere PowerShell-Elemente angezeigt wird, und Benutzer verwenden Standard `Get-Help` Befehle, um die Hilfe Themen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="2abc0-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="2abc0-105">In diesem Dokument werden das Format und die richtige Platzierung der Hilfe Themen für Module erläutert, und es werden Richtlinien für den Inhalt der Modul Hilfe vorgeschlagen.</span><span class="sxs-lookup"><span data-stu-id="2abc0-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="2abc0-106">Arten der Modul Hilfe</span><span class="sxs-lookup"><span data-stu-id="2abc0-106">Types of Module Help</span></span>

<span data-ttu-id="2abc0-107">Ein Modul kann die folgenden Arten von Hilfe enthalten.</span><span class="sxs-lookup"><span data-stu-id="2abc0-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="2abc0-108">**Hilfe zu Cmdlets**.</span><span class="sxs-lookup"><span data-stu-id="2abc0-108">**Cmdlet Help**.</span></span> <span data-ttu-id="2abc0-109">Die Hilfe Themen, in denen Cmdlets in einem Modul beschrieben werden, sind XML-Dateien, die das Befehls Hilfe Schema verwenden.</span><span class="sxs-lookup"><span data-stu-id="2abc0-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="2abc0-110">**Anbieter Hilfe**.</span><span class="sxs-lookup"><span data-stu-id="2abc0-110">**Provider Help**.</span></span> <span data-ttu-id="2abc0-111">Die Hilfe Themen, in denen Anbieter in einem Modul beschrieben werden, sind XML-Dateien, die das Anbieter Hilfe Schema verwenden.</span><span class="sxs-lookup"><span data-stu-id="2abc0-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="2abc0-112">**Hilfe zu Funktionen**.</span><span class="sxs-lookup"><span data-stu-id="2abc0-112">**Function Help**.</span></span> <span data-ttu-id="2abc0-113">In den Hilfe Themen, in denen Funktionen in einem Modul beschrieben werden, kann es sich um XML-Dateien handeln, die das Befehls Hilfe Schema oder Kommentar basierte Hilfe Themen innerhalb der Funktion oder des Skripts oder Skript Moduls verwenden.</span><span class="sxs-lookup"><span data-stu-id="2abc0-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="2abc0-114">**Skript-Hilfe**.</span><span class="sxs-lookup"><span data-stu-id="2abc0-114">**Script Help**.</span></span> <span data-ttu-id="2abc0-115">In den Hilfe Themen, in denen Skripts in einem Modul beschrieben werden, kann es sich um XML-Dateien handeln, die das Befehls Hilfe Schema oder Kommentar basierte Hilfe Themen im Skript-oder Skript Modul verwenden.</span><span class="sxs-lookup"><span data-stu-id="2abc0-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="2abc0-116">**Konzeptionelle Hilfe ("about")**.</span><span class="sxs-lookup"><span data-stu-id="2abc0-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="2abc0-117">Sie können ein konzeptionelles ("about") Hilfethema verwenden, um das Modul und seine Member zu beschreiben und zu erläutern, wie die Member zum Ausführen von Aufgaben verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="2abc0-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span>
  <span data-ttu-id="2abc0-118">Konzeptionelle Hilfe Themen sind Textdateien mit Unicode-Codierung (UTF-8).</span><span class="sxs-lookup"><span data-stu-id="2abc0-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="2abc0-119">Der Dateiname muss das `about_<name>.help.txt` Format verwenden, z `about_MyModule.help.txt` . b..</span><span class="sxs-lookup"><span data-stu-id="2abc0-119">The filename must use the `about_<name>.help.txt` format, such as `about_MyModule.help.txt`.</span></span> <span data-ttu-id="2abc0-120">Standardmäßig umfasst PowerShell mehr als 100 dieser konzeptionellen Informationen zu Hilfe Themen, die wie im folgenden Beispiel formatiert sind.</span><span class="sxs-lookup"><span data-stu-id="2abc0-120">By default, PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

  ```Output
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the PowerShell console.

  ```

<span data-ttu-id="2abc0-121">Alle Schema Dateien befinden sich im `$PSHOME\Schemas\PSMaml` Ordner.</span><span class="sxs-lookup"><span data-stu-id="2abc0-121">All of the schema files can be found in the `$PSHOME\Schemas\PSMaml` folder.</span></span>

## <a name="placement-of-module-help"></a><span data-ttu-id="2abc0-122">Platzierung der Modul Hilfe</span><span class="sxs-lookup"><span data-stu-id="2abc0-122">Placement of Module Help</span></span>

<span data-ttu-id="2abc0-123">Das- `Get-Help` Cmdlet sucht nach Modul Hilfe Themendateien in sprachspezifischen Unterverzeichnissen des Modul Verzeichnisses.</span><span class="sxs-lookup"><span data-stu-id="2abc0-123">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="2abc0-124">Das folgende Verzeichnisstruktur Diagramm zeigt beispielsweise den Speicherort der Hilfe Themen für das SampleModule-Modul.</span><span class="sxs-lookup"><span data-stu-id="2abc0-124">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> <span data-ttu-id="2abc0-125">Im Beispiel `<ModulePath>` stellt der Platzhalter einen der Pfade in der `PSModulePath` Umgebungsvariablen dar, z. b. `$HOME\Documents\Modules` , `$PSHOME\Modules` oder einen benutzerdefinierten Pfad, den der Benutzer angibt.</span><span class="sxs-lookup"><span data-stu-id="2abc0-125">In the example, the `<ModulePath>` placeholder represents one of the paths in the `PSModulePath` environment variable, such as `$HOME\Documents\Modules`, `$PSHOME\Modules`, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="2abc0-126">Hilfe zum Modul</span><span class="sxs-lookup"><span data-stu-id="2abc0-126">Getting Module Help</span></span>

<span data-ttu-id="2abc0-127">Wenn ein Benutzer ein Modul in eine Sitzung importiert, werden die Hilfe Themen für dieses Modul zusammen mit dem Modul in die Sitzung importiert.</span><span class="sxs-lookup"><span data-stu-id="2abc0-127">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="2abc0-128">Sie können die Hilfe Themendateien im Wert des FileList-Schlüssels im Modul Manifest auflisten, aber die Hilfe Themen sind vom `Export-ModuleMember` Cmdlet nicht betroffen.</span><span class="sxs-lookup"><span data-stu-id="2abc0-128">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="2abc0-129">Sie können Modul Hilfe Themen in verschiedenen Sprachen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="2abc0-129">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="2abc0-130">Das `Get-Help` -Cmdlet zeigt automatisch Modul Hilfe Themen in der Sprache an, die für den aktuellen Benutzer in der Systemsteuerung unter Regions-und Sprachoptionen angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="2abc0-130">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="2abc0-131">In Windows Vista und höheren Versionen von Windows `Get-Help` sucht nach den Hilfe Themen in sprachspezifischen Unterverzeichnissen des Modul Verzeichnisses in Übereinstimmung mit den für Windows eingerichteten sprach Fall Back Standards.</span><span class="sxs-lookup"><span data-stu-id="2abc0-131">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="2abc0-132">Ab PowerShell 3,0 löst das Ausführen eines `Get-Help` Befehls für ein Cmdlet oder eine Funktion das automatische Importieren des Moduls aus.</span><span class="sxs-lookup"><span data-stu-id="2abc0-132">Beginning in PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="2abc0-133">Mit dem- `Get-Help` Cmdlet wird sofort der Inhalt der Hilfe Themen im-Modul angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2abc0-133">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="2abc0-134">Wenn das Modul keine Hilfe Themen enthält und keine Hilfe Themen für die Befehle im Modul auf dem Computer des Benutzers vorhanden sind, zeigt die `Get-Help` automatisch generierte Hilfe an.</span><span class="sxs-lookup"><span data-stu-id="2abc0-134">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="2abc0-135">Die automatisch generierte Hilfe umfasst die Befehlssyntax, Parameter und Eingabe-und Ausgabetypen, enthält jedoch keine Beschreibungen.</span><span class="sxs-lookup"><span data-stu-id="2abc0-135">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="2abc0-136">Die automatisch generierte Hilfe enthält Text, der den Benutzer zum Versuch auffordert, das `Update-Help` Cmdlet zum Herunterladen der Hilfe für den Befehl aus dem Internet oder einer Dateifreigabe zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="2abc0-136">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the internet or a file share.</span></span> <span data-ttu-id="2abc0-137">Außerdem empfiehlt es sich, den **Online-** Parameter des `Get-Help` Cmdlets zu verwenden, um die Online Version des Hilfe Themas zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="2abc0-137">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="2abc0-138">Unterstützung einer aktualisierbaren Hilfe</span><span class="sxs-lookup"><span data-stu-id="2abc0-138">Supporting Updatable Help</span></span>

<span data-ttu-id="2abc0-139">Benutzer von PowerShell 3,0 und höheren Versionen von PowerShell können aktualisierte Hilfedateien für ein Modul aus dem Internet oder aus einer lokalen Dateifreigabe herunterladen und installieren.</span><span class="sxs-lookup"><span data-stu-id="2abc0-139">Users of PowerShell 3.0 and later versions of PowerShell can download and install updated help files for a module from the internet or from a local file share.</span></span> <span data-ttu-id="2abc0-140">Das `Update-Help` - `Save-Help` Cmdlet und das-Cmdlet blenden die Verwaltungs Details des Benutzers aus.</span><span class="sxs-lookup"><span data-stu-id="2abc0-140">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="2abc0-141">Benutzer führen das `Update-Help` Cmdlet aus und verwenden dann das `Get-Help` Cmdlet, um die neuesten Hilfedateien für das Modul an der PowerShell-Eingabeaufforderung zu lesen.</span><span class="sxs-lookup"><span data-stu-id="2abc0-141">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the PowerShell command prompt.</span></span>
<span data-ttu-id="2abc0-142">Benutzer müssen Windows oder PowerShell nicht neu starten.</span><span class="sxs-lookup"><span data-stu-id="2abc0-142">Users do not need to restart Windows or PowerShell.</span></span>

<span data-ttu-id="2abc0-143">Benutzer hinter Firewalls und denjenigen ohne Internet Zugriff können auch aktualisierbare Hilfe verwenden.</span><span class="sxs-lookup"><span data-stu-id="2abc0-143">Users behind firewalls and those without internet access can use Updatable Help, as well.</span></span>
<span data-ttu-id="2abc0-144">Administratoren mit Internet Zugriff verwenden das `Save-Help` Cmdlet zum herunterladen und Installieren der neuesten Hilfedateien auf einer Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="2abc0-144">Administrators with internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="2abc0-145">Anschließend verwenden die Benutzer den **path** -Parameter des `Update-Help` Cmdlets, um die neuesten Hilfedateien aus der Dateifreigabe zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="2abc0-145">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="2abc0-146">Modul Autoren können Hilfedateien in das Modul einschließen und die aktualisierbare Hilfe verwenden, um die Hilfedateien zu aktualisieren, oder Hilfedateien aus dem Modul weglassen und die aktualisierbare Hilfe verwenden, um Sie zu installieren und zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="2abc0-146">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="2abc0-147">Weitere Informationen zur aktualisierbaren Hilfe finden Sie [unter unterstützen der aktualisierbaren Hilfe](./supporting-updatable-help.md).</span><span class="sxs-lookup"><span data-stu-id="2abc0-147">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="2abc0-148">Unterstützung einer Onlinehilfe</span><span class="sxs-lookup"><span data-stu-id="2abc0-148">Supporting Online Help</span></span>

<span data-ttu-id="2abc0-149">Benutzer, die aktualisierte Hilfedateien auf ihren Computern nicht installieren können oder nicht installieren, basieren häufig auf der Online Version der Modul Hilfe Themen.</span><span class="sxs-lookup"><span data-stu-id="2abc0-149">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="2abc0-150">Der **Online-** Parameter des `Get-Help` Cmdlets öffnet die Online Version eines Cmdlets oder Hilfe Themas für erweiterte Funktionen für den Benutzer in seinem standardmäßigen Internetbrowser.</span><span class="sxs-lookup"><span data-stu-id="2abc0-150">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default internet browser.</span></span>

<span data-ttu-id="2abc0-151">Das `Get-Help` Cmdlet verwendet den Wert der **HelpUri** -Eigenschaft des Cmdlets oder der Funktion, um die Online Version des Hilfe Themas zu suchen.</span><span class="sxs-lookup"><span data-stu-id="2abc0-151">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="2abc0-152">Ab PowerShell 3,0 können Sie Benutzer bei der Suche nach der Online Version der Hilfe Themen zu Cmdlets und Funktionen unterstützen, indem Sie das HelpUri-Attribut in der Cmdlet-Klasse oder die **HelpUri** -Eigenschaft des **cmdletbinding** -Attributs definieren.</span><span class="sxs-lookup"><span data-stu-id="2abc0-152">Beginning in PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="2abc0-153">Der Wert des-Attributs ist der Wert der **HelpUri** -Eigenschaft des Cmdlets oder der Funktion.</span><span class="sxs-lookup"><span data-stu-id="2abc0-153">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="2abc0-154">Weitere Informationen finden Sie [unter unterstützen der Online Hilfe](./supporting-online-help.md).</span><span class="sxs-lookup"><span data-stu-id="2abc0-154">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2abc0-155">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2abc0-155">See Also</span></span>

[<span data-ttu-id="2abc0-156">Schreiben eines PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="2abc0-156">Writing a PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="2abc0-157">Unterstützung einer aktualisierbaren Hilfe</span><span class="sxs-lookup"><span data-stu-id="2abc0-157">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="2abc0-158">Unterstützung einer Onlinehilfe</span><span class="sxs-lookup"><span data-stu-id="2abc0-158">Supporting Online Help</span></span>](./supporting-online-help.md)
