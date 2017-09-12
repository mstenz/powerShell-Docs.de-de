---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Starten der 32-Bit-Version von Windows PowerShell
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: d682ce45ebc92cda3a9008ab608bacf9ef8eba57
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2017
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="f6d35-103">Starten der 32-Bit-Version von Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6d35-103">Starting the 32-Bit Version of Windows PowerShell</span></span>
<span data-ttu-id="f6d35-104">Bei der Installation von Windows PowerShell auf einem 64-Bit-Computer wird **Windows PowerShell (x86)**, eine 32-Bit-Version von Windows PowerShell, zusätzlich zur 64-Bit-Version installiert.</span><span class="sxs-lookup"><span data-stu-id="f6d35-104">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="f6d35-105">Wenn Sie Windows PowerShell ausführen, wird standardmäßig die 64-Bit-Version ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="f6d35-105">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="f6d35-106">Es kann jedoch möglicherweise erforderlich sein, **Windows PowerShell (x86)** auszuführen, z.B. wenn Sie ein Modul verwenden, das die 32-Bit-Version verlangt, oder Sie eine Remoteverbindung mit einem 32-Bit-Computer herstellen.</span><span class="sxs-lookup"><span data-stu-id="f6d35-106">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="f6d35-107">Wählen Sie eines der folgenden Verfahren, um eine 32-Bit-Version von Windows PowerShell zu starten.</span><span class="sxs-lookup"><span data-stu-id="f6d35-107">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="f6d35-108">In Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f6d35-108">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="f6d35-109">Geben Sie im**** Startbildschirm **Windows PowerShell (x86)** ein.</span><span class="sxs-lookup"><span data-stu-id="f6d35-109">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="f6d35-110">Klicken Sie auf die Kachel **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="f6d35-110">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="f6d35-111">Wählen Sie im **Server-Manager** im Menü **Extras** den Eintrag **Windows PowerShell (x86)** aus.</span><span class="sxs-lookup"><span data-stu-id="f6d35-111">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="f6d35-112">Bewegen Sie auf dem Desktop den Cursor in die rechte obere Ecke, klicken Sie auf **Suchen**, geben Sie **PowerShell x86** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="f6d35-112">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="f6d35-113">Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="f6d35-113">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="f6d35-114">In Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="f6d35-114">In Windows Server® 2012</span></span>

- <span data-ttu-id="f6d35-115">Klicken Sie auf **Start**, geben Sie **PowerShell** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="f6d35-115">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="f6d35-116">Wählen Sie im **Server-Manager** im Menü **Extras** den Eintrag **Windows PowerShell (x86)** aus.</span><span class="sxs-lookup"><span data-stu-id="f6d35-116">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="f6d35-117">Bewegen Sie auf dem Desktop den Cursor in die rechte obere Ecke, klicken Sie auf **Suchen**, geben Sie **PowerShell** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="f6d35-117">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="f6d35-118">Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="f6d35-118">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="f6d35-119">In Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="f6d35-119">In Windows® 8.1</span></span>

- <span data-ttu-id="f6d35-120">Geben Sie im**** Startbildschirm **Windows PowerShell (x86)** ein.</span><span class="sxs-lookup"><span data-stu-id="f6d35-120">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="f6d35-121">Klicken Sie auf die Kachel **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="f6d35-121">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="f6d35-122">Falls Sie die [Remoteserver-Verwaltungstools](http://go.microsoft.com/fwlink/?LinkID=304145) für Windows 8.1 ausführen, können Sie Windows PowerShell x86 auch im Server-Manager-Menü **Extras** öffnen.</span><span class="sxs-lookup"><span data-stu-id="f6d35-122">If you are running [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="f6d35-123">Wählen Sie **Windows PowerShell (x86)** aus.</span><span class="sxs-lookup"><span data-stu-id="f6d35-123">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="f6d35-124">Bewegen Sie auf dem Desktop den Cursor in die rechte obere Ecke, klicken Sie auf **Suchen**, geben Sie **PowerShell x86** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="f6d35-124">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
   
- <span data-ttu-id="f6d35-125">Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="f6d35-125">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="f6d35-126">In Windows® 8</span><span class="sxs-lookup"><span data-stu-id="f6d35-126">In Windows® 8</span></span>

- <span data-ttu-id="f6d35-127">Bewegen Sie auf dem Bildschirm **Start** den Cursor in die rechte obere Ecke, klicken Sie auf **Einstellungen**, dann auf **Kacheln**, und bewegen Sie den Schieberegler **Verwaltungstools anzeigen** auf „Ja“.</span><span class="sxs-lookup"><span data-stu-id="f6d35-127">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="f6d35-128">Geben Sie dann **PowerShell** ein, und klicken Sie auf **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="f6d35-128">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="f6d35-129">Falls Sie die [Remoteserver-Verwaltungstools](http://www.microsoft.com/download/details.aspx?id=28972) für Windows 8 ausführen, können Sie Windows PowerShell x86 auch im Server-Manager-Menü **Extras** öffnen.</span><span class="sxs-lookup"><span data-stu-id="f6d35-129">If you are running [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="f6d35-130">Wählen Sie **Windows PowerShell (x86)** aus.</span><span class="sxs-lookup"><span data-stu-id="f6d35-130">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="f6d35-131">Geben Sie auf dem Bildschirm **Start** oder dem Desktop **PowerShell (x86)** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="f6d35-131">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="f6d35-132">Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="f6d35-132">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

