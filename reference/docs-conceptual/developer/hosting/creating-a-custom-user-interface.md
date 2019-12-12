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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367629"
---
# <a name="creating-a-custom-user-interface"></a><span data-ttu-id="54520-102">Erstellen einer benutzerdefinierten Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="54520-102">Creating a custom user interface</span></span>

<span data-ttu-id="54520-103">Windows PowerShell bietet abstrakte Klassen und Schnittstellen, mit denen Sie eine benutzerdefinierte interaktive Benutzeroberfläche erstellen können, auf der die Windows PowerShell-Engine gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="54520-103">Windows PowerShell provides abstract classes and interfaces that allow you to create a custom interactive UI that hosts the Windows PowerShell engine.</span></span> <span data-ttu-id="54520-104">Um eine benutzerdefinierte Benutzeroberfläche zu erstellen, müssen Sie die [System. Management. Automation. Host. pshost](/dotnet/api/System.Management.Automation.Host.PSHost) -Klasse implementieren.</span><span class="sxs-lookup"><span data-stu-id="54520-104">To create a custom UI, you must implement the [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) class.</span></span> <span data-ttu-id="54520-105">Optional: Sie können auch die Klassen " [System. Management. Automation. Host. pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)" und " [System. Management. Automation. Host. pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) " sowie die Schnittstellen " [System. Management. Automation. Host. ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) " und " [System. Management. Automation. Host](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection)</span><span class="sxs-lookup"><span data-stu-id="54520-105">Optionally, you can also implement the [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)and [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) classes, and the [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) and [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) interfaces.</span></span>
