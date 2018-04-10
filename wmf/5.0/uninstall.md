---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 78ae7ecd40b4d8ad0a6750f43002986483ab18a7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="b2534-102">Deinstallationsanweisungen</span><span class="sxs-lookup"><span data-stu-id="b2534-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="b2534-103">Verwenden der Eingabeaufforderung</span><span class="sxs-lookup"><span data-stu-id="b2534-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="b2534-104">Öffnen Sie die **Eingabeaufforderung**.</span><span class="sxs-lookup"><span data-stu-id="b2534-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="b2534-105">Führen Sie das [eigenständige Windows Update-Startprogramm](https://support.microsoft.com/en-us/kb/934307) wie unten dargestellt aus:</span><span class="sxs-lookup"><span data-stu-id="b2534-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="b2534-106">Unter Windows Server 2012 R2 und Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="b2534-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="b2534-107">Unter Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="b2534-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="b2534-108">Unter Windows Server 2008 R2 SP1 und Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="b2534-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="b2534-109">Über die Systemsteuerung</span><span class="sxs-lookup"><span data-stu-id="b2534-109">Using Control Panel</span></span>
1.  <span data-ttu-id="b2534-110">Öffnen Sie die **Systemsteuerung**.</span><span class="sxs-lookup"><span data-stu-id="b2534-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="b2534-111">Öffnen Sie **Programme** und dann **Programm deinstallieren**.</span><span class="sxs-lookup"><span data-stu-id="b2534-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="b2534-112">Klicken Sie auf **Installierte Updates anzeigen**.</span><span class="sxs-lookup"><span data-stu-id="b2534-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="b2534-113">Wählen Sie in der Liste der installierten Updates **Windows Management Framework 5.0** aus.</span><span class="sxs-lookup"><span data-stu-id="b2534-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="b2534-114">Dies entspricht *KB3134758*, *KB3134759* oder *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="b2534-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="b2534-115">Klicken Sie auf **Deinstallieren**.</span><span class="sxs-lookup"><span data-stu-id="b2534-115">Click **Uninstall.**</span></span>