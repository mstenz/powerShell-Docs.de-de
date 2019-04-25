---
title: Ändern den Installationspfad PSModulePath | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082208"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="ffc1f-102">Ändern des Installationspfads PSModulePath</span><span class="sxs-lookup"><span data-stu-id="ffc1f-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="ffc1f-103">Die `PSModulePath` Umgebungsvariable speichert die Pfade zu den Speicherorten der Module, die auf dem Datenträger installiert sind.</span><span class="sxs-lookup"><span data-stu-id="ffc1f-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="ffc1f-104">Windows PowerShell verwendet diese Variable, um Module zu suchen, wenn der Benutzer nicht den vollständigen Pfad zu einem Modul angibt.</span><span class="sxs-lookup"><span data-stu-id="ffc1f-104">Windows PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="ffc1f-105">Die Pfade in dieser Variablen werden in der Reihenfolge durchsucht, in denen sie angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ffc1f-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="ffc1f-106">Wenn Windows PowerShell gestartet wird, `PSModulePath` wird als eine Systemumgebungsvariable mit dem folgenden Standardwert erstellt: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="ffc1f-106">When Windows PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="ffc1f-107">Anzeigen der PSModulePath-variable</span><span class="sxs-lookup"><span data-stu-id="ffc1f-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="ffc1f-108">Die Pfade anzeigen, die im angegebenen die `PSModulePath` Variable Geben Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="ffc1f-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="ffc1f-109">Speicherorte der PSModulePath-Variable hinzufügen</span><span class="sxs-lookup"><span data-stu-id="ffc1f-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="ffc1f-110">Um diese Variable Pfade hinzuzufügen, verwenden Sie eine der folgenden Methoden:</span><span class="sxs-lookup"><span data-stu-id="ffc1f-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="ffc1f-111">Um einen temporären Wert hinzufügen, der nur für die aktuelle Sitzung verfügbar ist, führen Sie den folgenden Befehl an der Befehlszeile aus:</span><span class="sxs-lookup"><span data-stu-id="ffc1f-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- <span data-ttu-id="ffc1f-112">Um einen persistenten Wert hinzuzufügen, der verfügbar ist, wenn eine Sitzung geöffnet ist, fügen Sie den folgenden Befehl, um ein Windows PowerShell-Profil:</span><span class="sxs-lookup"><span data-stu-id="ffc1f-112">To add a persistent value that is available whenever a session is opened, add the following command to a Windows PowerShell profile:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  <span data-ttu-id="ffc1f-113">Weitere Informationen zu Profilen finden Sie unter ["about_profiles"](/powershell/module/microsoft.powershell.core/about/about_profiles) in der Microsoft TechNet-Bibliothek.</span><span class="sxs-lookup"><span data-stu-id="ffc1f-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in the Microsoft TechNet library.</span></span>

- <span data-ttu-id="ffc1f-114">Um die Registrierung eine permanente Variablen hinzugefügt haben, erstellen Sie eine neue Benutzerumgebungsvariable aufgerufen `PSModulePath` mit dem Umgebung Variablen-Editor in die **Systemeigenschaften** Dialogfeld.</span><span class="sxs-lookup"><span data-stu-id="ffc1f-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="ffc1f-115">Verwenden Sie zum Hinzufügen einer permanenten Variablen mithilfe eines Skripts die **SetEnvironmentVariable** Methode für die Umgebung-Klasse.</span><span class="sxs-lookup"><span data-stu-id="ffc1f-115">To add a persistent variable by using a script, use the **SetEnvironmentVariable** method on the Environment class.</span></span> <span data-ttu-id="ffc1f-116">Das folgende Skript fügt beispielsweise den "c:\Programme\Microsoft Files\Fabrikam\Module Pfad auf den Wert der PSModulePath-Umgebungsvariablen für den Computer.</span><span class="sxs-lookup"><span data-stu-id="ffc1f-116">For example, the following script adds the "C:\Program Files\Fabrikam\Module path to the value of the PSModulePath environment variable for the computer.</span></span> <span data-ttu-id="ffc1f-117">Um den Pfad die Umgebungsvariable PSModulePath hinzuzufügen, legen Sie das Ziel auf "Benutzer" ein.</span><span class="sxs-lookup"><span data-stu-id="ffc1f-117">To add the path to the user PSModulePath environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="ffc1f-118">So entfernen Sie die Standorte aus der PSModulePath</span><span class="sxs-lookup"><span data-stu-id="ffc1f-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="ffc1f-119">Sie können Pfade aus der Variablen mit ähnlichen Methoden entfernen: z. B. `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` entfernt die **c:\ModulePath** Pfad aus der aktuellen Sitzung.</span><span class="sxs-lookup"><span data-stu-id="ffc1f-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="ffc1f-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ffc1f-120">See Also</span></span>

[<span data-ttu-id="ffc1f-121">Schreiben eines Windows PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="ffc1f-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
