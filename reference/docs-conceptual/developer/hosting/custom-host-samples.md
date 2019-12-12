---
title: Beispiele für benutzerdefinierte Hosts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367509"
---
# <a name="custom-host-samples"></a><span data-ttu-id="4fb21-102">Beispiele für benutzerdefinierte Hosts</span><span class="sxs-lookup"><span data-stu-id="4fb21-102">Custom Host Samples</span></span>

<span data-ttu-id="4fb21-103">Dieser Abschnitt enthält Beispielcode zum Schreiben eines benutzerdefinierten Hosts.</span><span class="sxs-lookup"><span data-stu-id="4fb21-103">This section includes sample code for writing a custom host.</span></span> <span data-ttu-id="4fb21-104">Mit Microsoft Visual Studio können Sie eine Konsolenanwendung erstellen und dann den Code aus den Themen in diesem Abschnitt in die Host Anwendung kopieren.</span><span class="sxs-lookup"><span data-stu-id="4fb21-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4fb21-105">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="4fb21-105">In This Section</span></span>

 <span data-ttu-id="4fb21-106">[Host01-Beispiel](./host01-sample.md) Dieses Beispiel zeigt, wie eine Host Anwendung implementiert wird, die einen einfachen benutzerdefinierten Host verwendet.</span><span class="sxs-lookup"><span data-stu-id="4fb21-106">[Host01 Sample](./host01-sample.md) This sample shows how to implement a host application that uses a basic custom host.</span></span>

 <span data-ttu-id="4fb21-107">[Host02-Beispiel](./host02-sample.md) In diesem Beispiel wird gezeigt, wie eine Host Anwendung geschrieben wird, die die Windows PowerShell-Laufzeit zusammen mit einer benutzerdefinierten Host Implementierung verwendet.</span><span class="sxs-lookup"><span data-stu-id="4fb21-107">[Host02 Sample](./host02-sample.md) This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="4fb21-108">Die Host Anwendung legt die Host Kultur auf Deutsch fest, führt das [Get-Process-](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet aus und zeigt die Ergebnisse an, wie Sie Sie mit pwrsh. exe sehen würden, und gibt dann die aktuellen Daten und die aktuelle Zeit in Deutsch aus.</span><span class="sxs-lookup"><span data-stu-id="4fb21-108">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>

 <span data-ttu-id="4fb21-109">[Host03-Beispiel](./host03-sample.md) Dieses Beispiel zeigt, wie eine interaktive konsolenbasierte Host Anwendung erstellt wird, die Befehle in der Befehlszeile liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt.</span><span class="sxs-lookup"><span data-stu-id="4fb21-109">[Host03 Sample](./host03-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

 <span data-ttu-id="4fb21-110">[Host04-Beispiel](./host04-sample.md) Dieses Beispiel zeigt, wie eine interaktive konsolenbasierte Host Anwendung erstellt wird, die Befehle in der Befehlszeile liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt.</span><span class="sxs-lookup"><span data-stu-id="4fb21-110">[Host04 Sample](./host04-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="4fb21-111">Diese Hostanwendung unterstützt auch das Anzeigen von Eingabeaufforderungen, die es den Benutzern ermöglichen, mehrere Auswahlmöglichkeiten anzugeben.</span><span class="sxs-lookup"><span data-stu-id="4fb21-111">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

 <span data-ttu-id="4fb21-112">[Host05-Beispiel](./host05-sample.md) Dieses Beispiel zeigt, wie eine interaktive konsolenbasierte Host Anwendung erstellt wird, die Befehle in der Befehlszeile liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt.</span><span class="sxs-lookup"><span data-stu-id="4fb21-112">[Host05 Sample](./host05-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="4fb21-113">Diese Host Anwendung unterstützt auch Aufrufe von Remote Computern mithilfe der Cmdlets [Enter-PSSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) und [Exit-PSSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) .</span><span class="sxs-lookup"><span data-stu-id="4fb21-113">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span></span>

 <span data-ttu-id="4fb21-114">[Host06-Beispiel](./host06-sample.md) Dieses Beispiel zeigt, wie eine interaktive konsolenbasierte Host Anwendung erstellt wird, die Befehle in der Befehlszeile liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt.</span><span class="sxs-lookup"><span data-stu-id="4fb21-114">[Host06 Sample](./host06-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="4fb21-115">Darüber hinaus verwendet dieses Beispiel die Tokenizer-APIs, um die Farbe des vom Benutzer eingegebenen Texts anzugeben.</span><span class="sxs-lookup"><span data-stu-id="4fb21-115">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="4fb21-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4fb21-116">See Also</span></span>
