---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Erstellen einer PowerShell-Registerkarte in Windows PowerShell ISE
ms.openlocfilehash: 7baf9a4051a196045d53eebf8ce5260bdc1bc55a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030588"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="99364-103">Erstellen einer PowerShell-Registerkarte in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="99364-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>

<span data-ttu-id="99364-104">Registerkarten in Windows PowerShell Integrated Scripting Environment (ISE) ermöglichen Ihnen, mehrere Ausführungsumgebungen innerhalb derselben Anwendung gleichzeitig zu erstellen und zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="99364-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="99364-105">Jede PowerShell-Registerkarte entspricht einer separaten Ausführungsumgebung bzw. Sitzung.</span><span class="sxs-lookup"><span data-stu-id="99364-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> [!NOTE]
> <span data-ttu-id="99364-106">Variablen, Funktionen und Aliase, die Sie auf einer Registerkarte erstellen, werden nicht auf andere übertragen.</span><span class="sxs-lookup"><span data-stu-id="99364-106">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="99364-107">Sie sind in verschiedenen Windows PowerShell-Sitzungen enthalten.</span><span class="sxs-lookup"><span data-stu-id="99364-107">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="99364-108">Gehen Sie folgendermaßen vor, um eine Registerkarte in Windows PowerShell zu öffnen oder zu schließen.</span><span class="sxs-lookup"><span data-stu-id="99364-108">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="99364-109">Legen Sie zum Umbenennen einer Registerkarte die Eigenschaft [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) im Skriptobjekt für die Windows PowerShell-Registerkarte fest.</span><span class="sxs-lookup"><span data-stu-id="99364-109">To rename a tab, set the [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="99364-110">So erstellen und verwenden Sie eine neue PowerShell-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="99364-110">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="99364-111">Klicken Sie im Menü **Datei** auf **Neue PowerShell-Registerkarte**. Die neue PowerShell-Registerkarte wird immer als aktives Fenster geöffnet.</span><span class="sxs-lookup"><span data-stu-id="99364-111">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="99364-112">PowerShell-Registerkarten sind in der Reihenfolge ihres Öffnens aufsteigend nummeriert.</span><span class="sxs-lookup"><span data-stu-id="99364-112">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="99364-113">Jede Registerkarte ist einem eigenen Windows PowerShell-Konsolenfenster zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="99364-113">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="99364-114">Sie können bis zu 32 PowerShell-Registerkarten mit jeweils eigener Sitzung gleichzeitig geöffnet haben (bei Windows PowerShell ISE 2.0 maximal 8.)</span><span class="sxs-lookup"><span data-stu-id="99364-114">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="99364-115">Beachten Sie, dass durch Klicken auf die Symbole **Neu** oder **Öffnen** auf der Symbolleiste keine neue Registerkarte mit einer separaten Sitzung erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="99364-115">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="99364-116">Über diese Schaltflächen wird stattdessen eine neue oder vorhandene Skriptdatei auf der derzeit in einer Sitzung aktiven Registerkarte geöffnet.</span><span class="sxs-lookup"><span data-stu-id="99364-116">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="99364-117">Auf jeder Registerkarte und in jeder Sitzung können mehrere Skriptdateien geöffnet sein.</span><span class="sxs-lookup"><span data-stu-id="99364-117">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="99364-118">Die Skriptregisterkarten für eine Sitzung werden nur unter den Sitzungsregisterkarten angezeigt, wenn die zugehörige Sitzung aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="99364-118">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="99364-119">Um eine PowerShell-Registerkarte zu aktivieren, klicken Sie auf die Registerkarte. Zum Auswählen aller PowerShell-Registerkarten, die im Menü **Ansicht** geöffnet sind, klicken Sie auf die PowerShell-Registerkarte, die Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="99364-119">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="99364-120">So erstellen und verwenden Sie eine Remote-PowerShell-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="99364-120">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="99364-121">Klicken Sie im Menü **Datei** auf **Neue Remote-PowerShell-Registerkarte**, um eine Sitzung auf einem Remotecomputer zu starten.</span><span class="sxs-lookup"><span data-stu-id="99364-121">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="99364-122">Ein Dialogfeld wird angezeigt und fordert Sie zur Eingabe von Details auf, die zum Herstellen der Remoteverbindung erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="99364-122">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="99364-123">Die Remoteregisterkarte funktioniert wie eine lokale PowerShell-Registerkarte, doch die Befehle und Skripts werden auf dem Remotecomputer ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="99364-123">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="99364-124">So schließen Sie eine PowerShell-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="99364-124">To close a PowerShell Tab</span></span>

<span data-ttu-id="99364-125">Zum Schließen einer Registerkarte können Sie eine der folgenden Methoden verwenden:</span><span class="sxs-lookup"><span data-stu-id="99364-125">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="99364-126">Klicken Sie auf die Registerkarte, die Sie schließen möchten.</span><span class="sxs-lookup"><span data-stu-id="99364-126">Click the tab that you want to close.</span></span>

- <span data-ttu-id="99364-127">Klicken Sie im Menü **Datei** auf **PowerShell-Registerkarte schließen**, oder klicken Sie auf einer aktiven Registerkarte auf die Schaltfläche „Schließen“ (**X**), um sie zu schließen.</span><span class="sxs-lookup"><span data-stu-id="99364-127">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="99364-128">Wenn Sie auf der PowerShell-Registerkarte nicht gespeicherte Dateien geöffnet sind, werden Sie aufgefordert, sie zu speichern oder zu verwerfen.</span><span class="sxs-lookup"><span data-stu-id="99364-128">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="99364-129">Weitere Informationen zum Speichern eines Skripts finden Sie unter [Speichern eines Skripts](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span><span class="sxs-lookup"><span data-stu-id="99364-129">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="99364-130">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="99364-130">See Also</span></span>

- [<span data-ttu-id="99364-131">Einführung in die Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="99364-131">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="99364-132">Verwenden des Konsolenbereichs in der Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="99364-132">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)
