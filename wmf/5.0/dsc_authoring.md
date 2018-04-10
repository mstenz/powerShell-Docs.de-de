---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 3b2c268cd10d7c421b3d1fc73a7bbeaa4714f5fc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="authoring-improvements-using-powershell-ise"></a><span data-ttu-id="51adf-102">Erstellungsverbesserungen mithilfe von PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="51adf-102">Authoring Improvements using PowerShell ISE</span></span>

<span data-ttu-id="51adf-103">Das Erstellen von DSC-Konfigurationen in Windows PowerShell ISE ist nun dank der folgenden Verbesserungen viel einfacher:</span><span class="sxs-lookup"><span data-stu-id="51adf-103">Authoring DSC configurations in Windows PowerShell ISE is much easier, thanks to the following improvements:</span></span>

- <span data-ttu-id="51adf-104">Auflisten aller DSC-Ressourcen in einem **Configuration**-Block oder **node**-Block durch Drücken von **STRG+LEERTASTE** in einer leeren Zeile.</span><span class="sxs-lookup"><span data-stu-id="51adf-104">List all DSC resources within a **configuration** block or **node** block by entering **Ctrl+Space** on a blank line within it.</span></span>
- <span data-ttu-id="51adf-105">Automatische Vervollständigung für Ressourceneigenschaften mit dem **enumeration**-Typ.</span><span class="sxs-lookup"><span data-stu-id="51adf-105">Automatic completion on resource properties that are of the **enumeration** type.</span></span>
- <span data-ttu-id="51adf-106">Automatische Vervollständigung für die **DependsOn**-Eigenschaft von DSC-Ressourcen basierend auf anderen Ressourceninstanzen in der Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="51adf-106">Automatic completion on the **DependsOn** property of DSC resources, based on other resource instances in the configuration.</span></span>
- <span data-ttu-id="51adf-107">Bessere automatische Ergänzung von Eigenschaftswerten von Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="51adf-107">Better tab completion of resource property values.</span></span>

<span data-ttu-id="51adf-108">**Hinweis:** Sie benötigen eine leere Zeichenfolge für Werte von Ressourceneigenschaften, bevor Sie STRG+LEERTASTE zum Auflisten von Optionen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="51adf-108">**Note:** You must have an empty string for resource property values before you can use Ctrl+Space to list the options.</span></span> <span data-ttu-id="51adf-109">Bei Drücken der **TAB**-Taste werden Optionen durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="51adf-109">Pressing **Tab** cycles through options.</span></span>