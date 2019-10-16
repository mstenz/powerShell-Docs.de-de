---
title: GetProc03 (VB.net)-Beispiel Code | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: a0a88ca517347a94fc81534caace6efa0f13fdd7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360309"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="793c0-102">GetProc03-Codebeispiel (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="793c0-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="793c0-103">Der folgende Code zeigt die Implementierung eines `Get-Process`-Cmdlets, das Pipeline Eingaben akzeptieren kann.</span><span class="sxs-lookup"><span data-stu-id="793c0-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="793c0-104">Diese Implementierung definiert einen `Name`-Parameter, der Pipeline Eingaben annimmt, Prozessinformationen vom lokalen Computer auf der Grundlage der angegebenen Namen abruft und dann die Methode " [Write Object" (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) als Ausgabe verwendet. Mechanismus zum Senden von Objekten an die Pipeline.</span><span class="sxs-lookup"><span data-stu-id="793c0-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="793c0-105">Code Beispiel</span><span class="sxs-lookup"><span data-stu-id="793c0-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
