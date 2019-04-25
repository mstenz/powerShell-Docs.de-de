---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 385bb7223b19c8ace8088ba469e543721a527b99
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057519"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="8f912-102">Deinstallationsanweisungen</span><span class="sxs-lookup"><span data-stu-id="8f912-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="8f912-103">Verwenden der Eingabeaufforderung</span><span class="sxs-lookup"><span data-stu-id="8f912-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="8f912-104">Öffnen Sie die **Eingabeaufforderung**.</span><span class="sxs-lookup"><span data-stu-id="8f912-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="8f912-105">Führen Sie das [eigenständige Windows Update-Startprogramm](https://support.microsoft.com/en-us/kb/934307) wie unten dargestellt aus:</span><span class="sxs-lookup"><span data-stu-id="8f912-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="8f912-106">Unter Windows Server 2012 R2 und Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="8f912-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="8f912-107">Unter Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="8f912-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="8f912-108">Unter Windows Server 2008 R2 SP1 und Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="8f912-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="8f912-109">Über die Systemsteuerung</span><span class="sxs-lookup"><span data-stu-id="8f912-109">Using Control Panel</span></span>
1.  <span data-ttu-id="8f912-110">Öffnen Sie die **Systemsteuerung**.</span><span class="sxs-lookup"><span data-stu-id="8f912-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="8f912-111">Öffnen Sie **Programme** und dann **Programm deinstallieren**.</span><span class="sxs-lookup"><span data-stu-id="8f912-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="8f912-112">Klicken Sie auf **Installierte Updates anzeigen**.</span><span class="sxs-lookup"><span data-stu-id="8f912-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="8f912-113">Wählen Sie in der Liste der installierten Updates **Windows Management Framework 5.0** aus.</span><span class="sxs-lookup"><span data-stu-id="8f912-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="8f912-114">Dies entspricht *KB3134758*, *KB3134759* oder *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="8f912-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="8f912-115">Klicken Sie auf **Deinstallieren**.</span><span class="sxs-lookup"><span data-stu-id="8f912-115">Click **Uninstall.**</span></span>
