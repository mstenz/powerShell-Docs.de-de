---
title: Schreiben einer Windows PowerShell-Host Anwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81aeafad-dbc3-4712-8bb9-e6a417be260f
caps.latest.revision: 15
ms.openlocfilehash: b44708b3bbcb974a6178323dff2302b7da121af6
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323492"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="eecf1-102">Schreiben einer Windows PowerShell-Hostanwendung</span><span class="sxs-lookup"><span data-stu-id="eecf1-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="eecf1-103">Sie können Windows PowerShell in Ihrer Anwendung hosten.</span><span class="sxs-lookup"><span data-stu-id="eecf1-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="eecf1-104">Die Host Anwendung kann den Runspace definieren, in dem Befehle ausgeführt werden, Sitzungen auf einem lokalen Computer oder einem Remote Computer öffnen und die Befehle entweder synchron oder asynchron basierend auf den Anforderungen der Anwendung aufrufen.</span><span class="sxs-lookup"><span data-stu-id="eecf1-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="eecf1-105">In den folgenden Themen wird erläutert, wie Sie eine Anwendung erstellen, die Windows PowerShell hostet.</span><span class="sxs-lookup"><span data-stu-id="eecf1-105">The following topics explain how to create an application that hosts Windows PowerShell.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="eecf1-106">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="eecf1-106">In This Section</span></span>

<span data-ttu-id="eecf1-107">[Schnellstart für Windows PowerShell-Host](./windows-powershell-host-quickstart.md) Enthält Anweisungen und Codebeispiele, die Ihnen den Einstieg in die Erstellung von Host Anwendungen erleichtern.</span><span class="sxs-lookup"><span data-stu-id="eecf1-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="eecf1-108">[Erstellen von Runspaces](./creating-runspaces.md) Eine Reihe von Themen, in denen erläutert wird, wie Runspaces zum Ausführen des Windows PowerShell-Befehls in einer Host Anwendung erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="eecf1-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="eecf1-109">[Hinzufügen und Aufrufen von Befehlen](./adding-and-invoking-commands.md) Erläutert, wie eine Befehls Pipeline in der Host Anwendung erstellt und ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="eecf1-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="eecf1-110">[Erstellen von Remoterunspaces](./creating-remote-runspaces.md) Erläutert, wie ein Runspace mit einem Remote Computer verbunden wird.</span><span class="sxs-lookup"><span data-stu-id="eecf1-110">[Creating remote runspaces](./creating-remote-runspaces.md) Explains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="eecf1-111">[Erstellen einer benutzerdefinierten Benutzeroberfläche](./creating-a-custom-user-interface.md) Stellt benutzerdefinierte Benutzeroberflächen vor und stellt Links zu Beispielen bereit.</span><span class="sxs-lookup"><span data-stu-id="eecf1-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="eecf1-112">[Beispiele für Host Anwendungen](./host-application-samples.md) Dieser Abschnitt enthält Beispiele für komplette Host Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="eecf1-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="eecf1-113">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="eecf1-113">See Also</span></span>

[<span data-ttu-id="eecf1-114">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eecf1-114">Windows PowerShell</span></span>](https://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)
