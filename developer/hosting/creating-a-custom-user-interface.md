---
title: Erstellen einer benutzerdefinierten Benutzeroberfläche | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7286443-eed4-43d5-b809-50cdcdcba088
caps.latest.revision: 4
ms.openlocfilehash: 23518c625fe1138e1bd2bcc895274cb21d7daf8a
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2019
ms.locfileid: "56863716"
---
# <a name="creating-a-custom-user-interface"></a><span data-ttu-id="4e829-102">Erstellen einer benutzerdefinierten Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="4e829-102">Creating a custom user interface</span></span>

<span data-ttu-id="4e829-103">Windows PowerShell bietet abstrakter Klassen und Schnittstellen, mit denen Sie eine benutzerdefinierte interaktive Benutzeroberfläche zu erstellen, die Windows PowerShell-Engine hostet.</span><span class="sxs-lookup"><span data-stu-id="4e829-103">Windows PowerShell provides abstract classes and interfaces that allow you to create a custom interactive UI that hosts the Windows PowerShell engine.</span></span> <span data-ttu-id="4e829-104">Um eine benutzerdefinierte Benutzeroberfläche erstellen möchten, müssen Sie implementieren die [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) Klasse.</span><span class="sxs-lookup"><span data-stu-id="4e829-104">To create a custom UI, you must implement the [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) class.</span></span> <span data-ttu-id="4e829-105">Optional können Sie auch implementieren die [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)und [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) Klassen und die [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) und [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) Schnittstellen.</span><span class="sxs-lookup"><span data-stu-id="4e829-105">Optionally, you can also implement the [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)and [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) classes, and the [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) and [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) interfaces.</span></span>
