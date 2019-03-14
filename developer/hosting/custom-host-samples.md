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
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794143"
---
# <a name="custom-host-samples"></a>Beispiele für benutzerdefinierte Hosts

Dieser Abschnitt enthält Beispielcode für einen benutzerdefinierten Host schreiben. Sie können Microsoft Visual Studio verwenden, erstellen eine Konsolenanwendung, und kopieren Sie den Code in den Themen in diesem Abschnitt, in der hostanwendung.

## <a name="in-this-section"></a>In diesem Abschnitt

 [Beispiel für Host01](./host01-sample.md) in diesem Beispiel wird gezeigt, wie eine hostanwendung implementiert wird, die einen einfachen benutzerdefinierten Host verwendet.

 [Beispiel für Host02](./host02-sample.md) dieses Beispiel zeigt, wie eine hostanwendung zu schreiben, die Windows PowerShell-Laufzeit, zusammen mit einer benutzerdefinierten hostimplementierung verwendet. Die hostanwendung legt die auf Deutsch fest, führt die [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) -Cmdlet und zeigt die Ergebnisse, wie Sie sehen sie mithilfe von pwrsh.exe, und klicken Sie dann druckt das aktuelle Datum und Uhrzeit auf Deutsch.

 [Beispiel für Host03](./host03-sample.md) diesem Beispiel wird gezeigt, wie Sie eine interaktive, konsolenbasierte hostanwendung zu erstellen, die Befehle von der Befehlszeile aus liest, führt die Befehle und die Ergebnisse anschließend in der Konsole anzeigt.

 [Beispiel für Host04](./host04-sample.md) diesem Beispiel wird gezeigt, wie Sie eine interaktive, konsolenbasierte hostanwendung zu erstellen, die Befehle von der Befehlszeile aus liest, führt die Befehle und die Ergebnisse anschließend in der Konsole anzeigt. Diese Hostanwendung unterstützt auch das Anzeigen von Eingabeaufforderungen, die es den Benutzern ermöglichen, mehrere Auswahlmöglichkeiten anzugeben.

 [Beispiel für Host05](./host05-sample.md) diesem Beispiel wird gezeigt, wie Sie eine interaktive, konsolenbasierte hostanwendung zu erstellen, die Befehle von der Befehlszeile aus liest, führt die Befehle und die Ergebnisse anschließend in der Konsole anzeigt. Diese hostanwendung unterstützt auch Aufrufe an Remotecomputern mithilfe der [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) und [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) Cmdlets

 [Beispiel für Host06](./host06-sample.md) diesem Beispiel wird gezeigt, wie Sie eine interaktive, konsolenbasierte hostanwendung zu erstellen, die Befehle von der Befehlszeile aus liest, führt die Befehle und die Ergebnisse anschließend in der Konsole anzeigt. Darüber hinaus verwendet dieses Beispiel die Tokenizer-APIs, um die Farbe des vom Benutzer eingegebenen Texts anzugeben.

## <a name="see-also"></a>Weitere Informationen
