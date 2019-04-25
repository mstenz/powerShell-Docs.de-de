---
title: Schreiben von Hilfe für Windows PowerShell-Module | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082029"
---
# <a name="writing-help-for-windows-powershell-modules"></a><span data-ttu-id="8b0ea-102">Schreiben einer Hilfe für Windows PowerShell-Module</span><span class="sxs-lookup"><span data-stu-id="8b0ea-102">Writing Help for Windows PowerShell Modules</span></span>

<span data-ttu-id="8b0ea-103">Windows PowerShell-Module können Hilfethemen, die über das Modul und die Member des Moduls, wie z. B. Cmdlets, Anbieter, Funktionen und Skripts enthalten.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-103">Windows PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="8b0ea-104">Die `Get-Help` Cmdlet zeigt die Modul-Hilfethemen im selben Format, wie es zeigt die Hilfe für andere Windows PowerShell-Elemente, und Benutzer können `Get-Help` Befehle aus, um die Hilfethemen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other Windows PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="8b0ea-105">In diesem Dokument wird erläutert, das Format und die korrekte Platzierung des Moduls Hilfethemen, und Richtlinien für das Modul Hilfeinhalt schlägt vor.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="8b0ea-106">Typen von Hilfe zu Integrationsmodulen</span><span class="sxs-lookup"><span data-stu-id="8b0ea-106">Types of Module Help</span></span>

<span data-ttu-id="8b0ea-107">Ein Modul kann die folgenden Typen von Hilfe enthalten.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="8b0ea-108">**Cmdlet-Hilfe**.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-108">**Cmdlet Help**.</span></span> <span data-ttu-id="8b0ea-109">Die Hilfethemen zu Cmdlets in einem Modul sind, dass die XML-Dateien, die dem Befehl Schema unterstützen</span><span class="sxs-lookup"><span data-stu-id="8b0ea-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="8b0ea-110">**Hilfe durch Anbieter**.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-110">**Provider Help**.</span></span> <span data-ttu-id="8b0ea-111">Hilfe zu Themen, die Anbieter in einem Modul zu beschreiben sind, dass die XML-Dateien, die den Anbieter verwenden, Schema unterstützen.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="8b0ea-112">**Funktionen**.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-112">**Function Help**.</span></span> <span data-ttu-id="8b0ea-113">Die Hilfethemen zu Funktionen in einem Modul kann sein, dass die XML-Dateien, die den Befehl verwenden, Schema oder die Kommentar-Hilfethemen innerhalb der Funktion oder des Skripts oder das Skriptmodul helfen</span><span class="sxs-lookup"><span data-stu-id="8b0ea-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="8b0ea-114">**Skripts**.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-114">**Script Help**.</span></span> <span data-ttu-id="8b0ea-115">Die Hilfethemen zu Skripts in einem Modul möglich, dass die XML-Dateien, die den Befehl verwenden, Schema oder die Kommentar-Hilfethemen in das Skript oder das Modul "Script" können.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="8b0ea-116">**("Info") Hilfe konzeptionellen**.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="8b0ea-117">Sie können eines konzeptionellen ("Info") Hilfethema verwenden, um das Modul und ihre Member beschreiben und erläutern, wie die Elemente zusammen verwendet werden können für Aufgaben.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span> <span data-ttu-id="8b0ea-118">Konzeptionelle Hilfethemen sind Textdateien mit der Codierung von Unicode (UTF-8).</span><span class="sxs-lookup"><span data-stu-id="8b0ea-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="8b0ea-119">Verwenden Sie der Dateinamen muss die `about_<name>.help.txt` Format, z. B. about_MyModule.help.txt.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-119">The file name must use the `about_<name>.help.txt` format, such as about_MyModule.help.txt.</span></span> <span data-ttu-id="8b0ea-120">Standardmäßig Windows PowerShell umfasst mehr als 100 konzeptionelle Themen zu unterstützen, und sie wie im folgenden Beispiel formatiert sind.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-120">By default, Windows PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

  ```
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
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a><span data-ttu-id="8b0ea-121">Platzierung der Hilfe zu Integrationsmodulen</span><span class="sxs-lookup"><span data-stu-id="8b0ea-121">Placement of Module Help</span></span>

<span data-ttu-id="8b0ea-122">Die `Get-Help` Cmdlet sucht Modul Hilfedateien in sprachspezifischen Unterverzeichnissen des Modulverzeichnisses.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-122">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="8b0ea-123">Das folgende Diagramm der Directory-Struktur zeigt beispielsweise den Speicherort für die Hilfethemen für das Modul SampleModule.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-123">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

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
> <span data-ttu-id="8b0ea-124">Im Beispiel die  *\<ModulePath >* steht für einen der Pfade in der `PSModulePath` Umgebungsvariablen wie z. B. $Home\Documents\Modules, $Pshome\Modules oder einen benutzerdefinierten Pfad, der den Benutzer angibt.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-124">In the example, the *\<ModulePath>* placeholder represents one of the paths in the `PSModulePath` environment variable, such as $home\Documents\Modules, $pshome\Modules, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="8b0ea-125">Abrufen von Hilfe zu Integrationsmodulen</span><span class="sxs-lookup"><span data-stu-id="8b0ea-125">Getting Module Help</span></span>

<span data-ttu-id="8b0ea-126">Wenn ein Benutzer ein Modul in eine Sitzung importiert, werden die Hilfethemen für das Modul in der Sitzung zusammen mit dem Modul importiert.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-126">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="8b0ea-127">Sie können die Hilfedateien im Wert des Schlüssels im modulmanifest FileList auflisten, aber Hilfethemen sind nicht betroffen von dem `Export-ModuleMember` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-127">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="8b0ea-128">Sie können die Modul-Hilfethemen in verschiedenen Sprachen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-128">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="8b0ea-129">Die `Get-Help` Cmdlet zeigt automatisch die Modul-Hilfethemen in der Sprache, die für den aktuellen Benutzer in den Regions- und Sprachoptionen Element in der Systemsteuerung angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-129">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="8b0ea-130">In Windows Vista und höheren Versionen von Windows `Get-Help` sucht nach den Hilfethemen in sprachspezifischen Unterverzeichnissen des Modulverzeichnisses in Übereinstimmung mit der Sprache fallback Standards, die für Windows.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-130">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="8b0ea-131">Ab Windows PowerShell 3.0, mit einem `Get-Help` -Befehl für ein Cmdlet oder eine Funktion löst automatischen Importieren des Moduls.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-131">Beginning in Windows PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="8b0ea-132">Die `Get-Help` Cmdlet zeigt sofort den Inhalt der Hilfethemen im Modul.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-132">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="8b0ea-133">Wenn das Modul enthält keine Hilfethemen, und es keine Hilfethemen für die Befehle im Modul auf dem Computer des Benutzers sind, `Get-Help` zeigt die automatisch generierte Hilfe an.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-133">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="8b0ea-134">Die automatisch generierte Hilfe umfasst die Befehlssyntax, Parameter und Eingabe-und Ausgabetypen, jedoch keine Beschreibungen.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-134">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="8b0ea-135">Die automatisch generierte Hilfe umfasst Text, der leitet den Benutzer mit der `Update-Help` -Cmdlet zum Herunterladen von Hilfe für den Befehl aus dem Internet oder eine Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-135">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="8b0ea-136">Außerdem empfiehlt die **Online** Parameter der `Get-Help` Cmdlet, um die Onlineversion des Hilfethemas abzurufen.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-136">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="8b0ea-137">Unterstützung für aktualisierbare Hilfe</span><span class="sxs-lookup"><span data-stu-id="8b0ea-137">Supporting Updatable Help</span></span>

<span data-ttu-id="8b0ea-138">Benutzer von Windows PowerShell 3.0 und höheren Versionen von Windows PowerShell können herunterladen und Installieren der aktualisierten Hilfedateien für ein Modul aus dem Internet oder aus einer lokalen Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-138">Users of Windows PowerShell 3.0 and later versions of Windows PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="8b0ea-139">Die `Update-Help` und `Save-Help` Cmdlets ausblenden, die verwaltungsdetails des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-139">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="8b0ea-140">Benutzer führen die `Update-Help` Cmdlet und verwenden Sie dann die `Get-Help` Cmdlet, um die neuesten Hilfedateien für das Modul an der Windows PowerShell-Eingabeaufforderung zu lesen.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-140">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the Windows PowerShell command prompt.</span></span> <span data-ttu-id="8b0ea-141">Benutzer müssen sich nicht auf Windows oder Windows PowerShell neu zu starten.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-141">Users do not need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="8b0ea-142">Benutzer hinter Firewalls und ohne Internetzugriff können aktualisierbare Hilfe, ebenfalls verwenden.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-142">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span> <span data-ttu-id="8b0ea-143">Administratoren mit Internet zugreifen, verwenden die `Save-Help` -Cmdlet zum Herunterladen und installieren die neuesten Hilfedateien auf einer Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-143">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="8b0ea-144">Klicken Sie dann die Benutzer verwenden die **Pfad** Parameter der `Update-Help` Cmdlet, um die neuesten Hilfedateien aus der Dateifreigabe abzurufen.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-144">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="8b0ea-145">Modulautoren können Hilfedateien in das Modul einschließen und aktualisierbare Hilfe verwenden, aktualisieren die Hilfedateien vorhanden sind, oder lassen Sie die Hilfedateien aus dem Modul und aktualisierbare Hilfe verwenden, installieren und diese aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-145">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="8b0ea-146">Weitere Informationen zur aktualisierbaren Hilfe finden Sie unter [unterstützen aktualisierbarer Hilfe](./supporting-updatable-help.md).</span><span class="sxs-lookup"><span data-stu-id="8b0ea-146">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="8b0ea-147">Unterstützung für Onlinehilfe</span><span class="sxs-lookup"><span data-stu-id="8b0ea-147">Supporting Online Help</span></span>

<span data-ttu-id="8b0ea-148">Benutzer, die nicht möglich, oder installieren Sie nicht aktualisiert, Hilfe, die Dateien auf ihren Computern häufig die Onlineversion des Hilfethemen Modul abhängig.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-148">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="8b0ea-149">Die **Online** Parameter, der die `Get-Help` Cmdlet öffnet die Onlineversion eines Cmdlets oder die erweiterte Funktion-Hilfethema für den Benutzer in ihren Standard-Internetbrowser.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-149">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="8b0ea-150">Die `Get-Help` Cmdlet verwendet den Wert der **HelpUri** Eigenschaft der Cmdlets oder einer Funktion, um die Onlineversion des Hilfethemas zu finden.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-150">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="8b0ea-151">Ab Windows PowerShell 3.0, Sie können Benutzern helfen, die Onlineversion des Cmdlet- und Hilfethemen suchen, indem das HelpUri-Attribut in der Cmdlet-Klasse oder die **HelpUri** Eigenschaft der **CmdletBinding** Attribut.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-151">Beginning in Windows PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="8b0ea-152">Der Wert des Attributs ist der Wert des der **HelpUri** Eigenschaft der Cmdlets oder der Funktion.</span><span class="sxs-lookup"><span data-stu-id="8b0ea-152">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="8b0ea-153">Weitere Informationen finden Sie unter [Supporting Online Help](./supporting-online-help.md).</span><span class="sxs-lookup"><span data-stu-id="8b0ea-153">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8b0ea-154">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8b0ea-154">See Also</span></span>

[<span data-ttu-id="8b0ea-155">Schreiben eines Windows PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="8b0ea-155">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="8b0ea-156">Unterstützung für aktualisierbare Hilfe</span><span class="sxs-lookup"><span data-stu-id="8b0ea-156">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="8b0ea-157">Unterstützung von Onlinehilfe</span><span class="sxs-lookup"><span data-stu-id="8b0ea-157">Supporting Online Help</span></span>](./supporting-online-help.md)