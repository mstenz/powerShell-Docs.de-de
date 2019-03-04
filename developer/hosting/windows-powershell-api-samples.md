---
title: Windows PowerShell-API-Beispiele | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860776"
---
# <a name="windows-powershell-api-samples"></a><span data-ttu-id="5c809-102">Beispiele für Windows PowerShell-APIs</span><span class="sxs-lookup"><span data-stu-id="5c809-102">Windows PowerShell API Samples</span></span>

<span data-ttu-id="5c809-103">Dieser Abschnitt enthält Beispielcode, der zeigt, wie zum Erstellen von Runspaces, die Funktionalität einschränken und asynchron ausführen der Befehle mit, dass ein runspacepool der Runspaces angeben.</span><span class="sxs-lookup"><span data-stu-id="5c809-103">This section includes sample code that shows how to create runspaces that restrict functionality, and how to asynchronously run commands by using a runspace pool to supply the runspaces.</span></span> <span data-ttu-id="5c809-104">Sie können Microsoft Visual Studio verwenden, erstellen eine Konsolenanwendung, und kopieren Sie den Code in den Themen in diesem Abschnitt, in der hostanwendung.</span><span class="sxs-lookup"><span data-stu-id="5c809-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="5c809-105">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="5c809-105">In This Section</span></span>

<span data-ttu-id="5c809-106">[PowerShell01 Beispiel](./windows-powershell01-sample.md) diesem Beispiel wird gezeigt, wie Sie mit einem [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) Objekt, das die Funktionalität von einem Runspace zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="5c809-106">[PowerShell01 Sample](./windows-powershell01-sample.md) This sample shows how to use an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to limit the functionality of a runspace.</span></span> <span data-ttu-id="5c809-107">Die Ausgabe dieses Beispiels wird veranschaulicht, wie beschränken Sie den Sprachmodus, der den Runspace, wie ein Cmdlet als privat markiert, hinzufügen und entfernen-Cmdlets und Anbieter, wie Sie einen Proxybefehl und vieles mehr hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5c809-107">The output of this sample demonstrates how to restrict the language mode of the runspace, how to mark a cmdlet as private, how to add and remove cmdlets and providers, how to add a proxy command, and more.</span></span>

<span data-ttu-id="5c809-108">[Beispiel für PowerShell02](./windows-powershell02-sample.md) diesem Beispiel wird gezeigt, wie Befehle asynchron ausgeführt wird, wird der Runspaces, der einen runspacepool verwenden.</span><span class="sxs-lookup"><span data-stu-id="5c809-108">[PowerShell02 Sample](./windows-powershell02-sample.md) This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="5c809-109">Im Beispiel generiert eine Liste der Befehle, und klicken Sie dann diese Befehle ausgeführt werden, während des Windows PowerShell-Moduls aus dem Pool einen Runspace öffnet, wenn er benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="5c809-109">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>