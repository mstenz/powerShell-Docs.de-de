---
title: Beispiele für benutzerdefinierten Host | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082922"
---
# <a name="custom-host-samples"></a><span data-ttu-id="647e5-102">Beispiele für benutzerdefinierte Hosts</span><span class="sxs-lookup"><span data-stu-id="647e5-102">Custom Host Samples</span></span>

<span data-ttu-id="647e5-103">Dieser Abschnitt enthält Beispielcode für einen benutzerdefinierten Host schreiben.</span><span class="sxs-lookup"><span data-stu-id="647e5-103">This section includes sample code for writing a custom host.</span></span> <span data-ttu-id="647e5-104">Sie können Microsoft Visual Studio verwenden, erstellen eine Konsolenanwendung, und kopieren Sie den Code in den Themen in diesem Abschnitt, in der hostanwendung.</span><span class="sxs-lookup"><span data-stu-id="647e5-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="647e5-105">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="647e5-105">In This Section</span></span>

 <span data-ttu-id="647e5-106">[Beispiel für Host01](./host01-sample.md) in diesem Beispiel wird gezeigt, wie eine hostanwendung implementiert wird, die einen einfachen benutzerdefinierten Host verwendet.</span><span class="sxs-lookup"><span data-stu-id="647e5-106">[Host01 Sample](./host01-sample.md) This sample shows how to implement a host application that uses a basic custom host.</span></span>

 <span data-ttu-id="647e5-107">[Beispiel für Host02](./host02-sample.md) dieses Beispiel zeigt, wie eine hostanwendung zu schreiben, die Windows PowerShell-Laufzeit, zusammen mit einer benutzerdefinierten hostimplementierung verwendet.</span><span class="sxs-lookup"><span data-stu-id="647e5-107">[Host02 Sample](./host02-sample.md) This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="647e5-108">Die hostanwendung legt die auf Deutsch fest, führt die [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) -Cmdlet und zeigt die Ergebnisse, wie Sie sehen sie mithilfe von pwrsh.exe, und klicken Sie dann druckt das aktuelle Datum und Uhrzeit auf Deutsch.</span><span class="sxs-lookup"><span data-stu-id="647e5-108">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>

 <span data-ttu-id="647e5-109">[Beispiel für Host03](./host03-sample.md) diesem Beispiel wird gezeigt, wie Sie eine interaktive, konsolenbasierte hostanwendung zu erstellen, die Befehle von der Befehlszeile aus liest, führt die Befehle und die Ergebnisse anschließend in der Konsole anzeigt.</span><span class="sxs-lookup"><span data-stu-id="647e5-109">[Host03 Sample](./host03-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

 <span data-ttu-id="647e5-110">[Beispiel für Host04](./host04-sample.md) diesem Beispiel wird gezeigt, wie Sie eine interaktive, konsolenbasierte hostanwendung zu erstellen, die Befehle von der Befehlszeile aus liest, führt die Befehle und die Ergebnisse anschließend in der Konsole anzeigt.</span><span class="sxs-lookup"><span data-stu-id="647e5-110">[Host04 Sample](./host04-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="647e5-111">Diese Hostanwendung unterstützt auch das Anzeigen von Eingabeaufforderungen, die es den Benutzern ermöglichen, mehrere Auswahlmöglichkeiten anzugeben.</span><span class="sxs-lookup"><span data-stu-id="647e5-111">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

 <span data-ttu-id="647e5-112">[Beispiel für Host05](./host05-sample.md) diesem Beispiel wird gezeigt, wie Sie eine interaktive, konsolenbasierte hostanwendung zu erstellen, die Befehle von der Befehlszeile aus liest, führt die Befehle und die Ergebnisse anschließend in der Konsole anzeigt.</span><span class="sxs-lookup"><span data-stu-id="647e5-112">[Host05 Sample](./host05-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="647e5-113">Diese hostanwendung unterstützt auch Aufrufe an Remotecomputern mithilfe der [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) und [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) Cmdlets</span><span class="sxs-lookup"><span data-stu-id="647e5-113">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span></span>

 <span data-ttu-id="647e5-114">[Beispiel für Host06](./host06-sample.md) diesem Beispiel wird gezeigt, wie Sie eine interaktive, konsolenbasierte hostanwendung zu erstellen, die Befehle von der Befehlszeile aus liest, führt die Befehle und die Ergebnisse anschließend in der Konsole anzeigt.</span><span class="sxs-lookup"><span data-stu-id="647e5-114">[Host06 Sample](./host06-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="647e5-115">Darüber hinaus verwendet dieses Beispiel die Tokenizer-APIs, um die Farbe des vom Benutzer eingegebenen Texts anzugeben.</span><span class="sxs-lookup"><span data-stu-id="647e5-115">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="647e5-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="647e5-116">See Also</span></span>
