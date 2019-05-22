---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Deinstallieren von WMF 5.0
ms.openlocfilehash: f562a4a4506bfdede6b23bd186b80f40cc9e45ca
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855465"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="c2813-103">Deinstallationsanweisungen</span><span class="sxs-lookup"><span data-stu-id="c2813-103">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="c2813-104">Verwenden der Eingabeaufforderung</span><span class="sxs-lookup"><span data-stu-id="c2813-104">Using Command Prompt</span></span>

1. <span data-ttu-id="c2813-105">Öffnen Sie die **Eingabeaufforderung**.</span><span class="sxs-lookup"><span data-stu-id="c2813-105">Open **Command Prompt.**</span></span>
2. <span data-ttu-id="c2813-106">Führen Sie das [eigenständige Windows Update-Startprogramm](https://support.microsoft.com/en-us/kb/934307) wie unten dargestellt aus:</span><span class="sxs-lookup"><span data-stu-id="c2813-106">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="c2813-107">Unter Windows Server 2012 R2 und Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="c2813-107">On Windows Server 2012 R2 and Windows 8.1:</span></span>

```powershell
wusa /uninstall /kb:3134758
```

<span data-ttu-id="c2813-108">Unter Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="c2813-108">On Windows Server 2012:</span></span>

```powershell
wusa /uninstall /kb:3134759
```

<span data-ttu-id="c2813-109">Unter Windows Server 2008 R2 SP1 und Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="c2813-109">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>

```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="c2813-110">Über die Systemsteuerung</span><span class="sxs-lookup"><span data-stu-id="c2813-110">Using Control Panel</span></span>

1. <span data-ttu-id="c2813-111">Öffnen Sie die **Systemsteuerung**.</span><span class="sxs-lookup"><span data-stu-id="c2813-111">Open **Control Panel.**</span></span>
2. <span data-ttu-id="c2813-112">Öffnen Sie **Programme** und dann **Programm deinstallieren**.</span><span class="sxs-lookup"><span data-stu-id="c2813-112">Open **Programs**, then open **Uninstall a program.**</span></span>
3. <span data-ttu-id="c2813-113">Klicken Sie auf **Installierte Updates anzeigen**.</span><span class="sxs-lookup"><span data-stu-id="c2813-113">Click **View installed updates.**</span></span>
4. <span data-ttu-id="c2813-114">Wählen Sie in der Liste der installierten Updates **Windows Management Framework 5.0** aus.</span><span class="sxs-lookup"><span data-stu-id="c2813-114">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="c2813-115">Dies entspricht *KB3134758*, *KB3134759* oder *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="c2813-115">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="c2813-116">Klicken Sie auf **Deinstallieren**.</span><span class="sxs-lookup"><span data-stu-id="c2813-116">Click **Uninstall.**</span></span>
