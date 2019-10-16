---
title: Ändern des psmodulepath-Installations Pfads | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360669"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="bde66-102">Ändern des Installationspfads PSModulePath</span><span class="sxs-lookup"><span data-stu-id="bde66-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="bde66-103">Die Umgebungsvariable `PSModulePath` speichert die Pfade zu den Speicherorten der Module, die auf dem Datenträger installiert sind.</span><span class="sxs-lookup"><span data-stu-id="bde66-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="bde66-104">Windows PowerShell verwendet diese Variable, um Module zu suchen, wenn der Benutzer nicht den vollständigen Pfad zu einem Modul angibt.</span><span class="sxs-lookup"><span data-stu-id="bde66-104">Windows PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="bde66-105">Die Pfade in dieser Variablen werden in der Reihenfolge durchsucht, in der Sie angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bde66-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="bde66-106">Beim Starten von Windows PowerShell wird `PSModulePath` als System Umgebungsvariable mit dem folgenden Standardwert erstellt: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="bde66-106">When Windows PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="bde66-107">So zeigen Sie die psmodulepath-Variable an</span><span class="sxs-lookup"><span data-stu-id="bde66-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="bde66-108">Geben Sie den folgenden Befehl ein, um die in der `PSModulePath`-Variablen angegebenen Pfade anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="bde66-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="bde66-109">So fügen Sie der psmodulepath-Variablen Speicherorte hinzu</span><span class="sxs-lookup"><span data-stu-id="bde66-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="bde66-110">Um dieser Variablen Pfade hinzuzufügen, verwenden Sie eine der folgenden Methoden:</span><span class="sxs-lookup"><span data-stu-id="bde66-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="bde66-111">Wenn Sie einen temporären Wert hinzufügen möchten, der nur für die aktuelle Sitzung verfügbar ist, führen Sie den folgenden Befehl in der Befehlszeile aus:</span><span class="sxs-lookup"><span data-stu-id="bde66-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- <span data-ttu-id="bde66-112">Fügen Sie den folgenden Befehl in ein Windows PowerShell-Profil ein, um einen persistenten Wert hinzuzufügen, der immer verfügbar ist, wenn eine Sitzung geöffnet wird:</span><span class="sxs-lookup"><span data-stu-id="bde66-112">To add a persistent value that is available whenever a session is opened, add the following command to a Windows PowerShell profile:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  <span data-ttu-id="bde66-113">Weitere Informationen zu Profilen finden Sie unter [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in der Microsoft TechNet-Bibliothek.</span><span class="sxs-lookup"><span data-stu-id="bde66-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in the Microsoft TechNet library.</span></span>

- <span data-ttu-id="bde66-114">Um der Registrierung eine permanente Variable hinzuzufügen, erstellen Sie eine neue Benutzer Umgebungsvariable mit dem Namen "`PSModulePath`", indem Sie im Dialogfeld " **System Eigenschaften** " den Umgebungsvariablen-Editor verwenden.</span><span class="sxs-lookup"><span data-stu-id="bde66-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="bde66-115">Um eine persistente Variable mithilfe eines Skripts hinzuzufügen, verwenden Sie die Methode "\*" **in der Umgebungs** Klasse.</span><span class="sxs-lookup"><span data-stu-id="bde66-115">To add a persistent variable by using a script, use the **SetEnvironmentVariable** method on the Environment class.</span></span> <span data-ttu-id="bde66-116">Mit dem folgenden Skript wird z. b. der Pfad "c:\programme\fabrikam\module" dem Wert der Umgebungsvariablen "psmodulepath" für den Computer hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="bde66-116">For example, the following script adds the "C:\Program Files\Fabrikam\Module path to the value of the PSModulePath environment variable for the computer.</span></span> <span data-ttu-id="bde66-117">Zum Hinzufügen des Pfads zur Benutzer-psmodulepath-Umgebungsvariablen legen Sie für das Ziel den Wert "User" fest.</span><span class="sxs-lookup"><span data-stu-id="bde66-117">To add the path to the user PSModulePath environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="bde66-118">So entfernen Sie Speicherorte aus dem psmodulepath</span><span class="sxs-lookup"><span data-stu-id="bde66-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="bde66-119">Sie können Pfade aus der Variablen entfernen, indem Sie ähnliche Methoden verwenden: beispielsweise entfernt `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` den Pfad " **c:\modulepath** " aus der aktuellen Sitzung.</span><span class="sxs-lookup"><span data-stu-id="bde66-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="bde66-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="bde66-120">See Also</span></span>

[<span data-ttu-id="bde66-121">Schreiben eines Windows PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="bde66-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
