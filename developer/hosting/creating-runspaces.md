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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857906"
---
# <a name="creating-runspaces"></a><span data-ttu-id="cc96a-102">Erstellen von Runspaces</span><span class="sxs-lookup"><span data-stu-id="cc96a-102">Creating Runspaces</span></span>

<span data-ttu-id="cc96a-103">Ein Runspace ist die betriebsumgebung für die Befehle, die von einer hostanwendung aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="cc96a-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="cc96a-104">Diese Umgebung umfasst die Befehle und Daten, die derzeit vorhanden sind, und Language Einschränkungen, die derzeit gelten.</span><span class="sxs-lookup"><span data-stu-id="cc96a-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="cc96a-105">Hosten von Anwendungen mit dem standardmäßigen Runspace, der von Windows PowerShell, das alle verfügbaren Kern-Befehle enthält bereitgestellt wird, oder erstellen einen benutzerdefinierten Runspace, der nur eine Teilmenge der verfügbaren Befehle enthält.</span><span class="sxs-lookup"><span data-stu-id="cc96a-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="cc96a-106">Um einen benutzerdefinierten Runspace zu erstellen, erstellen Sie eine [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) Objekt aus, und weisen sie Sie Ihrem Runspace.</span><span class="sxs-lookup"><span data-stu-id="cc96a-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="cc96a-107">Runspace-Aufgaben</span><span class="sxs-lookup"><span data-stu-id="cc96a-107">Runspace tasks</span></span>

1. [<span data-ttu-id="cc96a-108">Erstellen eine InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="cc96a-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="cc96a-109">Erstellen einen eingeschränkten runspace</span><span class="sxs-lookup"><span data-stu-id="cc96a-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="cc96a-110">Erstellen von mehreren runspaces</span><span class="sxs-lookup"><span data-stu-id="cc96a-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="cc96a-111">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="cc96a-111">See Also</span></span>
