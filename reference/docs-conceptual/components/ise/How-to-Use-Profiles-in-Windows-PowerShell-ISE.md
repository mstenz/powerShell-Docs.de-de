---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: "So wird's gemacht: Verwenden von Profilen in Windows PowerShell ISE"
ms.openlocfilehash: 28354f39aaaa577cec69c1b3f62cfe16ef091218
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030606"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="c050f-103">So wird's gemacht: Verwenden von Profilen in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c050f-103">How to Use Profiles in Windows PowerShell ISE</span></span>

<span data-ttu-id="c050f-104">In diesem Thema wird erklärt, wie Profile in Windows PowerShell® Integrated Scripting Environment (ISE) verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="c050f-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="c050f-105">Es empfiehlt sich, die Aufgaben in diesem Abschnitt erst auszuführen, nachdem Sie [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) gelesen oder im Konsolenbereich `Get-Help about_Profiles` eingegeben und die **EINGABETASTE** gedrückt haben.</span><span class="sxs-lookup"><span data-stu-id="c050f-105">We recommend that before performing the tasks in this section, you review [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), or in the Console Pane, type, `Get-Help about_Profiles` and press **ENTER**.</span></span>

<span data-ttu-id="c050f-106">Ein Profil ist ein Windows PowerShell ISE-Skript, das automatisch ausgeführt wird, wenn Sie eine neue Sitzung starten.</span><span class="sxs-lookup"><span data-stu-id="c050f-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>  <span data-ttu-id="c050f-107">Sie können ein oder mehrere Windows PowerShell-Profile für Windows PowerShell ISE erstellen und diese dazu verwenden, die Umgebung von Windows PowerShell oder Windows PowerShell ISE zu konfigurieren, um sie mit den Variablen, Aliasen, Funktionen sowie Farb- und Schriftartvoreinstellungen vorzubereiten, die Sie zur Verfügung haben möchten.</span><span class="sxs-lookup"><span data-stu-id="c050f-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="c050f-108">Ein Profil wirkt sich auf jede Windows PowerShell ISE-Sitzung aus, die Sie starten.</span><span class="sxs-lookup"><span data-stu-id="c050f-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="c050f-109">Die Windows PowerShell-Ausführungsrichtlinie bestimmt, ob Sie Skripts ausführen und ein Profil laden dürfen.</span><span class="sxs-lookup"><span data-stu-id="c050f-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span> <span data-ttu-id="c050f-110">Die Standardausführungsrichtlinie, „Restricted“, verhindert das Ausführen jeglicher Skripts, einschließlich Profile.</span><span class="sxs-lookup"><span data-stu-id="c050f-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span> <span data-ttu-id="c050f-111">Wenn Sie die Richtlinie „Restricted“ verwenden, kann das Profil nicht geladen werden.</span><span class="sxs-lookup"><span data-stu-id="c050f-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="c050f-112">Weitere Informationen zu Ausführungsrichtlinien finden Sie unter [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="c050f-112">For more information about execution policy, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="c050f-113">Auswählen eines Profils, das in Windows PowerShell ISE verwendet werden soll</span><span class="sxs-lookup"><span data-stu-id="c050f-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>

<span data-ttu-id="c050f-114">Windows PowerShell ISE unterstützt Profile für den aktuellen Benutzer sowie für alle Benutzer.</span><span class="sxs-lookup"><span data-stu-id="c050f-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="c050f-115">Außerdem werden die Windows PowerShell-Profile unterstützt, die für alle Hosts gelten.</span><span class="sxs-lookup"><span data-stu-id="c050f-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="c050f-116">Das Profil, das Sie verwenden, wird durch die Verwendung der Windows PowerShell und Windows PowerShell ISE bestimmt.</span><span class="sxs-lookup"><span data-stu-id="c050f-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="c050f-117">Wenn Sie nur Windows PowerShell ISE verwenden, um Windows PowerShell auszuführen, speichern Sie alle ihre Elemente in einem ISE-spezifischen Profil, z.B. dem Profil „CurrentUserCurrentHost“ für Windows PowerShell ISE oder „AllUsersCurrentHost“ für Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c050f-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the CurrentUserCurrentHost profile for Windows PowerShell ISE or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="c050f-118">Wenn Sie mehrere Hostprogramme verwenden, um Windows PowerShell auszuführen, speichern Sie Ihre Funktionen, Aliase, Variablen und Befehle in einem Profil, das alle Hostprogramme betrifft, z.B. dem Profil „CurrentUserAllHosts“ oder „AllUsersAllHosts“. Speichern Sie ISE-spezifische Merkmale wie Anpassungen von Farbe und Schriftart im Profil „CurrentUserCurrentHost“ für Windows PowerShell ISE oder „AllUsersCurrentHost“ für Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c050f-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the AllUsersAllHosts profile, and save ISE-specific features, like color and font customization in the CurrentUserCurrentHost profile for Windows PowerShell ISE profile or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="c050f-119">Die folgenden Profile sind Profile, die in Windows PowerShell ISE erstellt und verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="c050f-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="c050f-120">Jedes Profil wird in seinem eigenen speziellen Pfad gespeichert.</span><span class="sxs-lookup"><span data-stu-id="c050f-120">Each profile is saved to its own specific path.</span></span>

| <span data-ttu-id="c050f-121">Profiltyp</span><span class="sxs-lookup"><span data-stu-id="c050f-121">Profile Type</span></span> | <span data-ttu-id="c050f-122">Profilpfad</span><span class="sxs-lookup"><span data-stu-id="c050f-122">Profile Path</span></span> |
| --- | --- |
| <span data-ttu-id="c050f-123">**Aktueller Benutzer, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="c050f-123">**Current user, PowerShell ISE**</span></span>| <span data-ttu-id="c050f-124">`$PROFILE.CurrentUserCurrentHost` oder `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="c050f-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="c050f-125">**Alle Benutzer, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="c050f-125">**All users, PowerShell ISE**</span></span>| `$PROFILE.AllUsersCurrentHost` |
| <span data-ttu-id="c050f-126">**Aktueller Benutzer, alle Hosts**</span><span class="sxs-lookup"><span data-stu-id="c050f-126">**Current user, All hosts**</span></span>| `$PROFILE.CurrentUserAllHosts` |
| <span data-ttu-id="c050f-127">**Alle Benutzer, alle Hosts**</span><span class="sxs-lookup"><span data-stu-id="c050f-127">**All users, All hosts**</span></span> | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="c050f-128">So erstellen Sie ein neues Profil</span><span class="sxs-lookup"><span data-stu-id="c050f-128">To create a new profile</span></span>

<span data-ttu-id="c050f-129">Um ein neues „Aktueller Benutzer, PowerShell ISE“-Profil zu erstellen, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="c050f-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="c050f-130">Um ein neues „Alle Benutzer, PowerShell ISE“-Profil zu erstellen, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="c050f-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="c050f-131">Um ein neues „Aktueller Benutzer, alle Hosts“-Profil zu erstellen, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="c050f-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="c050f-132">Um ein neues „Alle Benutzer, alle Hosts“-Profil zu erstellen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="c050f-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="c050f-133">So bearbeiten Sie ein Profil</span><span class="sxs-lookup"><span data-stu-id="c050f-133">To edit a profile</span></span>

1. <span data-ttu-id="c050f-134">Um das Profil zu öffnen, führen Sie den Befehl „psedit“ mit der Variablen aus, die das Profil angibt, das Sie bearbeiten möchten.</span><span class="sxs-lookup"><span data-stu-id="c050f-134">To open the profile, run the command psedit with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="c050f-135">Wenn Sie beispielsweise das „Aktueller Benutzer, PowerShell ISE“-Profil öffnen möchten, geben Sie Folgendes ein: `psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="c050f-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="c050f-136">Fügen Sie dem Profil einige Elemente hinzu.</span><span class="sxs-lookup"><span data-stu-id="c050f-136">Add some items to your profile.</span></span> <span data-ttu-id="c050f-137">Es folgen einige Beispiele, die Ihnen den Einstieg erleichtern sollen:</span><span class="sxs-lookup"><span data-stu-id="c050f-137">The following are a few examples to get you started:</span></span>

   - <span data-ttu-id="c050f-138">Um die Standardhintergrundfarbe des Konsolenbereichs in Blau zu ändern, geben Sie Folgendes in die Profildatei ein: `$psISE.Options.OutputPaneBackground = 'blue'`.</span><span class="sxs-lookup"><span data-stu-id="c050f-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="c050f-139">Weitere Informationen zu der Variablen „$psISE“ finden Sie unter [Referenz zum Windows PowerShell ISE-Objektmodell](object-model/The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="c050f-139">For more information about the $psISE variable, see [Windows PowerShell ISE Object Model Reference](object-model/The-ISE-Object-Model-Hierarchy.md).</span></span>

   - <span data-ttu-id="c050f-140">Um den Schriftgrad in 20 zu ändern, geben Sie Folgendes in die Profildatei ein: `$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="c050f-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="c050f-141">Um Ihre Profildatei zu speichern, klicken Sie im Menü **Datei** auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="c050f-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="c050f-142">Wenn Sie Windows PowerShell ISE das nächste Mal öffnen, werden Ihre Anpassungen angewendet.</span><span class="sxs-lookup"><span data-stu-id="c050f-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="c050f-143">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c050f-143">See Also</span></span>

- [<span data-ttu-id="c050f-144">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="c050f-144">about_Profiles</span></span>](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [<span data-ttu-id="c050f-145">Einführung in die Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c050f-145">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
