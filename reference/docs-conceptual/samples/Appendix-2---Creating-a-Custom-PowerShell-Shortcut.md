---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Anhang 2 – Erstellen einer benutzerdefinierten PowerShell-Verknüpfung
ms.assetid: 5d4fd421-5d43-4ec7-86fd-acfe887b066e
ms.openlocfilehash: e8081b7a64d313c8ef4bbccf95f250445dd68ad9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402017"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a><span data-ttu-id="e68d8-103">Anhang 2: Erstellen einer benutzerdefinierten PowerShell-Verknüpfung</span><span class="sxs-lookup"><span data-stu-id="e68d8-103">Appendix 2 - Creating a Custom PowerShell Shortcut</span></span>

<span data-ttu-id="e68d8-104">In der folgenden Vorgehensweise wird beschrieben, wie Sie eine Verknüpfung zu Windows PowerShell erstellen, in der mehrere praktische Optionen angepasst sind.</span><span class="sxs-lookup"><span data-stu-id="e68d8-104">The following procedure describes how to create a shortcut to Windows PowerShell that has several convenient options customized.</span></span>

1. <span data-ttu-id="e68d8-105">Erstellen Sie eine Verknüpfung, die auf „Powershell.exe“ verweist.</span><span class="sxs-lookup"><span data-stu-id="e68d8-105">Create a shortcut that points to Powershell.exe.</span></span>

2. <span data-ttu-id="e68d8-106">Klicken Sie mit der rechten Maustaste auf die Verknüpfung, und klicken Sie dann auf **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="e68d8-106">Right-click the shortcut, and then click **Properties**.</span></span>

3. <span data-ttu-id="e68d8-107">Klicken Sie auf die Registerkarte **Optionen**.</span><span class="sxs-lookup"><span data-stu-id="e68d8-107">Click the **Options** tab.</span></span>

4. <span data-ttu-id="e68d8-108">Aktivieren Sie im Abschnitt **Bearbeitungsoptionen** das Kontrollkästchen **QuickEdit**.</span><span class="sxs-lookup"><span data-stu-id="e68d8-108">In the **Edit Options** section, select the **QuickEdit** check box.</span></span>

    <span data-ttu-id="e68d8-109">Diese Einstellung ermöglicht es Ihnen, Text im Windows PowerShell-Konsolenfenster durch Ziehen bei gedrückter linker Maustaste zu markieren sowie Text in die Zwischenablage zu kopieren, indem Sie die EINGABETASTE drücken oder mit der rechten Maustaste klicken.</span><span class="sxs-lookup"><span data-stu-id="e68d8-109">This setting lets you select text in the Windows PowerShell console window by dragging the left mouse button, and it lets you copy text to the clipboard by pressing ENTER or by right-clicking the mouse.</span></span>

5. <span data-ttu-id="e68d8-110">Aktivieren Sie im Abschnitt **Bearbeitungsoptionen** das Kontrollkästchen **Einfügemodus**.</span><span class="sxs-lookup"><span data-stu-id="e68d8-110">In the **Edit Options** section, select the **Insert Mode** check box.</span></span> <span data-ttu-id="e68d8-111">Diese Einstellung ermöglicht es Ihnen, Text aus der Zwischenablage automatisch durch Klicken mit der rechten Maustaste im Konsolenfenster einzufügen.</span><span class="sxs-lookup"><span data-stu-id="e68d8-111">This setting lets you right-click in the console window to automatically paste text from the clipboard.</span></span>

6. <span data-ttu-id="e68d8-112">Geben Sie im Abschnitt **Befehlsspeicher** direkt oder durch Auswählen eine Zahl zwischen 1 und 999 in das Feld **Puffergröße** ein.</span><span class="sxs-lookup"><span data-stu-id="e68d8-112">In the **Command History** section, type or select a number between 1 and 999 in the **Buffer Size** box.</span></span> <span data-ttu-id="e68d8-113">Hiermit wird die Anzahl von eingegebenen Befehlen festgelegt, die im Konsolenpuffer aufbewahrt werden.</span><span class="sxs-lookup"><span data-stu-id="e68d8-113">This sets the number of typed commands that will be kept in the console buffer.</span></span>

7. <span data-ttu-id="e68d8-114">Aktivieren Sie im Abschnitt **Befehlsspeicher** das Kontrollkästchen **Alte Duplikate löschen**, damit wiederholte Befehle aus dem Konsolenpuffer entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="e68d8-114">In the **Command History** section, select the **Discard Old Duplicates** check box to eliminate repeated commands from the console buffer.</span></span>

8. <span data-ttu-id="e68d8-115">Klicken Sie auf die Registerkarte **Layout**.</span><span class="sxs-lookup"><span data-stu-id="e68d8-115">Click the **Layout** tab.</span></span>

9. <span data-ttu-id="e68d8-116">Geben Sie im Abschnitt **Fensterpuffergröße** eine Zahl zwischen 1 und 9999 in das Feld **Höhe** ein.</span><span class="sxs-lookup"><span data-stu-id="e68d8-116">In the **Screen Buffer** section, type a number between 1 and 9999 in the **Height** box.</span></span> <span data-ttu-id="e68d8-117">Diese Höhe entspricht der Anzahl von Ausgabezeilen, die gepuffert werden.</span><span class="sxs-lookup"><span data-stu-id="e68d8-117">The height represents the number of lines of output that are buffered.</span></span> <span data-ttu-id="e68d8-118">Dies ist die maximale Anzahl von Zeilen, die für die Anzeige beibehalten werden, wenn Sie durch das Konsolenfenster scrollen.</span><span class="sxs-lookup"><span data-stu-id="e68d8-118">This is the maximum number of lines retained for viewing when you scroll through the console window.</span></span> <span data-ttu-id="e68d8-119">Ist diese Anzahl kleiner als der Wert für die Höhenangabe im Abschnitt **Fenstergröße**, wird die Fensterhöhe automatisch auf denselben Wert verringert.</span><span class="sxs-lookup"><span data-stu-id="e68d8-119">If this number is lower than the height shown in the **Window size** section, the window size height will automatically be reduced to the same value.</span></span>

10. <span data-ttu-id="e68d8-120">Geben Sie im Abschnitt **Fenstergröße** eine Zahl zwischen 1 und 9999 für die Breite ein.</span><span class="sxs-lookup"><span data-stu-id="e68d8-120">In the **Window Size** section, type a number between 1 and 9999 for the width.</span></span> <span data-ttu-id="e68d8-121">Diese Zahl entspricht der Anzahl von Zeichen, die horizontal im Konsolenfenster angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e68d8-121">This represents the number of characters that are displayed across the console window.</span></span> <span data-ttu-id="e68d8-122">Die Standardbreite beträgt 80, und die Ausgabeformatierung von Windows PowerShell ist für diese Breite konzipiert.</span><span class="sxs-lookup"><span data-stu-id="e68d8-122">The default width is 80, and Windows PowerShell's output formatting is designed for this width.</span></span>

11. <span data-ttu-id="e68d8-123">Wenn Sie die Konsole beim Öffnen an einer bestimmten Stelle auf dem Desktop platzieren möchten, deaktivieren Sie im Abschnitt **Fensterposition** das Kontrollkästchen **Automatisch positionieren**, und ändern Sie die Werte in den Feldern **Links** und **Oben** im Abschnitt **Fensterposition**.</span><span class="sxs-lookup"><span data-stu-id="e68d8-123">If you want to place the console at a particular point on the desktop when it is opened, clear the **Let system position window** check box in the **Window position** section, and then change the values in the **Left** and **Top** boxes in the **Window position** section.</span></span>

12. <span data-ttu-id="e68d8-124">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="e68d8-124">Click **OK**.</span></span>