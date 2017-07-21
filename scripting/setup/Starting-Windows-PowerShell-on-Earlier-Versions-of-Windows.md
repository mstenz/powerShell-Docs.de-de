---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Starten von Windows PowerShell unter früheren Versionen von Windows"
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: cb56fded1e67a4f4219d210dd95078314e855b1a
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="941ff-103">Starten von Windows PowerShell unter früheren Versionen von Windows</span><span class="sxs-lookup"><span data-stu-id="941ff-103">Starting Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="941ff-104">In diesem Abschnitt wird das Starten von Windows PowerShell und Windows PowerShell Integrated Scripting Environment (ISE) unter Windows® 7, Windows Server® 2008 R2 und Windows Server® 2008 erläutert.</span><span class="sxs-lookup"><span data-stu-id="941ff-104">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="941ff-105">Außerdem wird beschrieben, wie das optionale Feature für Windows PowerShell ISE in Windows PowerShell 2.0 in Windows Server® 2008 R2 und Windows Server® 2008 aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="941ff-105">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="941ff-106">Zum Installieren von Windows PowerShell 4.0 in unterstützten Systemen müssen Sie [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) herunterladen und installieren.</span><span class="sxs-lookup"><span data-stu-id="941ff-106">To install Windows PowerShell 4.0 on supported systems, download and install [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span></span> <span data-ttu-id="941ff-107">Weitere Informationen finden Sie unter [Installieren von Windows PowerShell](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="941ff-107">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

<span data-ttu-id="941ff-108">Zum Installieren von Windows PowerShell 3.0 in unterstützten Systemen müssen Sie [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290) herunterladen und installieren.</span><span class="sxs-lookup"><span data-stu-id="941ff-108">To install Windows PowerShell 3.0 on supported systems, download and install [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span> <span data-ttu-id="941ff-109">Weitere Informationen finden Sie unter [Installieren von Windows PowerShell](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="941ff-109">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="941ff-110">Starten von Windows PowerShell unter früheren Versionen von Windows</span><span class="sxs-lookup"><span data-stu-id="941ff-110">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="941ff-111">Mit den folgenden Methoden können Sie die installierte Version von Windows PowerShell 3.0 oder Windows PowerShell 4.0 installieren, sofern zutreffend.</span><span class="sxs-lookup"><span data-stu-id="941ff-111">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="941ff-112">Über das Startmenü</span><span class="sxs-lookup"><span data-stu-id="941ff-112">From the Start Menu</span></span>

-   <span data-ttu-id="941ff-113">Klicken Sie auf **Start**, geben Sie **PowerShell** ein, und klicken Sie dann auf **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="941ff-113">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>

-   <span data-ttu-id="941ff-114">Klicken Sie im Menü **** **Start** auf **Alle Programme**, danach auf **Zubehör**, anschließend auf den Ordner **Windows PowerShell** und schließlich auf **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="941ff-114">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="941ff-115">An der Eingabeaufforderung</span><span class="sxs-lookup"><span data-stu-id="941ff-115">At the Command Prompt</span></span>

-   <span data-ttu-id="941ff-116">Geben Sie zum Starten von Windows PowerShell in Cmd.exe, Windows PowerShell oder Windows PowerShell ISE Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="941ff-116">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell
    ```

    <span data-ttu-id="941ff-117">Sie können auch die Parameter des Programms „PowerShell.exe“ verwenden, um die Sitzung anzupassen.</span><span class="sxs-lookup"><span data-stu-id="941ff-117">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="941ff-118">Weitere Informationen finden Sie unter [PowerShell.exe – Befehlszeilenhilfe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="941ff-118">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="941ff-119">Mit administrativen Berechtigungen (Als Administrator ausführen)</span><span class="sxs-lookup"><span data-stu-id="941ff-119">With Administrative privileges ("Run as administrator")</span></span>

1.  <span data-ttu-id="941ff-120">Klicken Sie auf **Start**, geben Sie **PowerShell** ein, klicken Sie mit der rechten Maustaste auf **Windows PowerShell**, und klicken Sie dann auf **Als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="941ff-120">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="941ff-121">Starten von Windows PowerShell ISE unter früheren Versionen von Windows</span><span class="sxs-lookup"><span data-stu-id="941ff-121">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="941ff-122">Verwenden Sie eine der folgenden Methoden, um Windows PowerShell ISE zu starten:</span><span class="sxs-lookup"><span data-stu-id="941ff-122">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="941ff-123">Über das Startmenü</span><span class="sxs-lookup"><span data-stu-id="941ff-123">From the Start Menu</span></span>

-   <span data-ttu-id="941ff-124">Klicken Sie auf **Start**, geben Sie **ISE** ein, und klicken Sie dann auf **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="941ff-124">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>

-   <span data-ttu-id="941ff-125">Klicken Sie im Menü **** **Start** auf **Alle Programme**, danach auf **Zubehör**, anschließend auf den Ordner **Windows PowerShell** und schließlich auf **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="941ff-125">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="941ff-126">An der Eingabeaufforderung</span><span class="sxs-lookup"><span data-stu-id="941ff-126">At the Command Prompt</span></span>

-   <span data-ttu-id="941ff-127">Geben Sie zum Starten von Windows PowerShell in Cmd.exe, Windows PowerShell oder Windows PowerShell ISE Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="941ff-127">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell_ISE
    ```

    <span data-ttu-id="941ff-128">oder</span><span class="sxs-lookup"><span data-stu-id="941ff-128">or</span></span>

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="941ff-129">Mit administrativen Berechtigungen (Als Administrator ausführen)</span><span class="sxs-lookup"><span data-stu-id="941ff-129">With Administrative privileges ("Run as administrator")</span></span>

1.  <span data-ttu-id="941ff-130">Klicken Sie auf **Start**, geben Sie **ISE** ein, klicken Sie mit der rechten Maustaste auf **Windows PowerShell ISE**, und klicken Sie dann auf **Als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="941ff-130">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="941ff-131">Aktivieren von Windows PowerShell ISE unter früheren Versionen von Windows</span><span class="sxs-lookup"><span data-stu-id="941ff-131">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="941ff-132">In Windows PowerShell 4.0 und Windows PowerShell 3.0 ist Windows PowerShell ISE standardmäßig für alle Versionen von Windows aktiviert.</span><span class="sxs-lookup"><span data-stu-id="941ff-132">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="941ff-133">Falls es nicht bereits aktiviert ist, erfolgt die Aktivierung mithilfe von Windows Management Framework 4.0 oder Windows Management Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="941ff-133">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="941ff-134">In Windows PowerShell 2.0 ist Windows PowerShell ISE standardmäßig für Windows 7 aktiviert.</span><span class="sxs-lookup"><span data-stu-id="941ff-134">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="941ff-135">Allerdings ist es in Windows Server 2008 R2 und Windows Server 2008 ein optionales Feature.</span><span class="sxs-lookup"><span data-stu-id="941ff-135">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="941ff-136">Gehen Sie wie folgt vor, um Windows PowerShell ISE in Windows PowerShell 2.0 unter Windows Server 2008 R2 oder Windows Server 2008 zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="941ff-136">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="941ff-137">So aktivieren Sie Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="941ff-137">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1.  <span data-ttu-id="941ff-138">Starten Sie den Server-Manager.</span><span class="sxs-lookup"><span data-stu-id="941ff-138">Start Server Manager.</span></span>

2.  <span data-ttu-id="941ff-139">Klicken Sie auf **Features** und dann auf **Features hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="941ff-139">Click **Features** and then click **Add Features**.</span></span>

3.  <span data-ttu-id="941ff-140">Klicken Sie unter „Features auswählen“ auf „Windows PowerShell Integrated Scripting Environment (ISE)“.</span><span class="sxs-lookup"><span data-stu-id="941ff-140">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

