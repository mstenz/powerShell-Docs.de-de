---
title: Erstellen von Runspaces | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367579"
---
# <a name="creating-runspaces"></a><span data-ttu-id="160b9-102">Erstellen von Runspaces</span><span class="sxs-lookup"><span data-stu-id="160b9-102">Creating Runspaces</span></span>

<span data-ttu-id="160b9-103">Ein Runspace ist die Betriebsumgebung für die Befehle, die von einer Host Anwendung aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="160b9-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="160b9-104">Diese Umgebung umfasst die derzeit vorhandenen Befehle und Daten sowie alle derzeit geltenden Spracheinschränkungen.</span><span class="sxs-lookup"><span data-stu-id="160b9-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="160b9-105">Host Anwendungen können den von Windows PowerShell bereitgestellten standardrunspace verwenden, der alle verfügbaren Kern Befehle enthält, oder einen benutzerdefinierten Runspace erstellen, der nur eine Teilmenge der verfügbaren Befehle enthält.</span><span class="sxs-lookup"><span data-stu-id="160b9-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="160b9-106">Um einen benutzerdefinierten Runspace zu erstellen, erstellen Sie ein [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt, und weisen Sie es Ihrem Runspace zu.</span><span class="sxs-lookup"><span data-stu-id="160b9-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="160b9-107">Runspace-Tasks</span><span class="sxs-lookup"><span data-stu-id="160b9-107">Runspace tasks</span></span>

1. [<span data-ttu-id="160b9-108">Erstellen eines initialsessionstate</span><span class="sxs-lookup"><span data-stu-id="160b9-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="160b9-109">Erstellen eines eingeschränkten Runspace</span><span class="sxs-lookup"><span data-stu-id="160b9-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="160b9-110">Erstellen mehrerer Runspaces</span><span class="sxs-lookup"><span data-stu-id="160b9-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="160b9-111">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="160b9-111">See Also</span></span>
