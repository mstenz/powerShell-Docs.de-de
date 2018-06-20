---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Erstellen einer PowerShell-Registerkarte in Windows PowerShell ISE
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 4d4388d889f2178b2cd24cb0f3350aee37327625
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950045"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="40d3f-103">Erstellen einer PowerShell-Registerkarte in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="40d3f-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>

<span data-ttu-id="40d3f-104">Registerkarten in Windows PowerShell Integrated Scripting Environment (ISE) ermöglichen Ihnen, mehrere Ausführungsumgebungen innerhalb derselben Anwendung gleichzeitig zu erstellen und zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="40d3f-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="40d3f-105">Jede PowerShell-Registerkarte entspricht einer separaten Ausführungsumgebung bzw. Sitzung.</span><span class="sxs-lookup"><span data-stu-id="40d3f-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> <span data-ttu-id="40d3f-106">**HINWEIS**:</span><span class="sxs-lookup"><span data-stu-id="40d3f-106">**NOTE**:</span></span>
>
> <span data-ttu-id="40d3f-107">Variablen, Funktionen und Aliase, die Sie auf einer Registerkarte erstellen, werden nicht auf andere übertragen.</span><span class="sxs-lookup"><span data-stu-id="40d3f-107">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="40d3f-108">Sie sind in verschiedenen Windows PowerShell-Sitzungen enthalten.</span><span class="sxs-lookup"><span data-stu-id="40d3f-108">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="40d3f-109">Gehen Sie folgendermaßen vor, um eine Registerkarte in Windows PowerShell zu öffnen oder zu schließen.</span><span class="sxs-lookup"><span data-stu-id="40d3f-109">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="40d3f-110">Legen Sie zum Umbenennen einer Registerkarte die Eigenschaft [DisplayName](The-PowerShellTab-Object.md#displayname) im Skriptobjekt für die Windows PowerShell-Registerkarte fest.</span><span class="sxs-lookup"><span data-stu-id="40d3f-110">To rename a tab, set the [DisplayName](The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="40d3f-111">So erstellen und verwenden Sie eine neue PowerShell-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="40d3f-111">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="40d3f-112">Klicken Sie im Menü **Datei** auf **Neue PowerShell-Registerkarte**. Die neue PowerShell-Registerkarte wird immer als aktives Fenster geöffnet.</span><span class="sxs-lookup"><span data-stu-id="40d3f-112">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="40d3f-113">PowerShell-Registerkarten sind in der Reihenfolge ihres Öffnens aufsteigend nummeriert.</span><span class="sxs-lookup"><span data-stu-id="40d3f-113">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="40d3f-114">Jede Registerkarte ist einem eigenen Windows PowerShell-Konsolenfenster zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="40d3f-114">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="40d3f-115">Sie können bis zu 32 PowerShell-Registerkarten mit jeweils eigener Sitzung gleichzeitig geöffnet haben (bei Windows PowerShell ISE 2.0 maximal 8.)</span><span class="sxs-lookup"><span data-stu-id="40d3f-115">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="40d3f-116">Beachten Sie, dass durch Klicken auf die Symbole **Neu** oder **Öffnen** auf der Symbolleiste keine neue Registerkarte mit einer separaten Sitzung erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="40d3f-116">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="40d3f-117">Über diese Schaltflächen wird stattdessen eine neue oder vorhandene Skriptdatei auf der derzeit in einer Sitzung aktiven Registerkarte geöffnet.</span><span class="sxs-lookup"><span data-stu-id="40d3f-117">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="40d3f-118">Auf jeder Registerkarte und in jeder Sitzung können mehrere Skriptdateien geöffnet sein.</span><span class="sxs-lookup"><span data-stu-id="40d3f-118">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="40d3f-119">Die Skriptregisterkarten für eine Sitzung werden nur unter den Sitzungsregisterkarten angezeigt, wenn die zugehörige Sitzung aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="40d3f-119">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="40d3f-120">Um eine PowerShell-Registerkarte zu aktivieren, klicken Sie auf die Registerkarte. Zum Auswählen aller PowerShell-Registerkarten, die im Menü **Ansicht** geöffnet sind, klicken Sie auf die PowerShell-Registerkarte, die Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="40d3f-120">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="40d3f-121">So erstellen und verwenden Sie eine Remote-PowerShell-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="40d3f-121">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="40d3f-122">Klicken Sie im Menü **Datei** auf **Neue Remote-PowerShell-Registerkarte**, um eine Sitzung auf einem Remotecomputer zu starten.</span><span class="sxs-lookup"><span data-stu-id="40d3f-122">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="40d3f-123">Ein Dialogfeld wird angezeigt und fordert Sie zur Eingabe von Details auf, die zum Herstellen der Remoteverbindung erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="40d3f-123">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="40d3f-124">Die Remoteregisterkarte funktioniert wie eine lokale PowerShell-Registerkarte, doch die Befehle und Skripts werden auf dem Remotecomputer ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="40d3f-124">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="40d3f-125">So schließen Sie eine PowerShell-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="40d3f-125">To close a PowerShell Tab</span></span>

<span data-ttu-id="40d3f-126">Zum Schließen einer Registerkarte können Sie eine der folgenden Methoden verwenden:</span><span class="sxs-lookup"><span data-stu-id="40d3f-126">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="40d3f-127">Klicken Sie auf die Registerkarte, die Sie schließen möchten.</span><span class="sxs-lookup"><span data-stu-id="40d3f-127">Click the tab that you want to close.</span></span>

- <span data-ttu-id="40d3f-128">Klicken Sie im Menü **Datei** auf **PowerShell-Registerkarte schließen**, oder klicken Sie auf einer aktiven Registerkarte auf die Schaltfläche „Schließen“ (**X**), um sie zu schließen.</span><span class="sxs-lookup"><span data-stu-id="40d3f-128">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="40d3f-129">Wenn Sie auf der PowerShell-Registerkarte nicht gespeicherte Dateien geöffnet sind, werden Sie aufgefordert, sie zu speichern oder zu verwerfen.</span><span class="sxs-lookup"><span data-stu-id="40d3f-129">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="40d3f-130">Weitere Informationen zum Speichern eines Skripts finden Sie unter [Speichern eines Skripts](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span><span class="sxs-lookup"><span data-stu-id="40d3f-130">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="40d3f-131">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="40d3f-131">See Also</span></span>

- [<span data-ttu-id="40d3f-132">Einführung in die Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="40d3f-132">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="40d3f-133">Verwenden des Konsolenbereichs in der Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="40d3f-133">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)