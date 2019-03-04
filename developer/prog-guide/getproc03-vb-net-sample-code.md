---
title: GetProc03 Beispielcode (VB.NET) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: da85155c43471150a7b35ac37c1dce0790277084
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854636"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="6aa95-102">GetProc03-Codebeispiel (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="6aa95-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="6aa95-103">Der folgende Code zeigt die Implementierung einer `Get-Process` -Cmdlet, das annehmen kann Pipeline-Eingabe.</span><span class="sxs-lookup"><span data-stu-id="6aa95-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="6aa95-104">Diese Implementierung definiert eine `Name` Parameter, die Pipeline-Eingaben akzeptiert Prozessinformationen aus dem lokalen Computer, die basierend auf den angegebenen Namen abgerufen und verwendet dann die [System.Management.Automation.Cmdlet.Writeobject% 28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) Methode als Ausgabemechanismus für die Objekte werden an die Pipeline gesendet.</span><span class="sxs-lookup"><span data-stu-id="6aa95-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6aa95-105">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="6aa95-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->