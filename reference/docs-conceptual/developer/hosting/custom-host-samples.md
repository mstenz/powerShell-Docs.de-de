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
# <a name="custom-host-samples"></a>Beispiele für benutzerdefinierte Hosts

Dieser Abschnitt enthält Beispielcode zum Schreiben eines benutzerdefinierten Hosts. Mit Microsoft Visual Studio können Sie eine Konsolenanwendung erstellen und dann den Code aus den Themen in diesem Abschnitt in die Host Anwendung kopieren.

## <a name="in-this-section"></a>In diesem Abschnitt

 [Host01-Beispiel](./host01-sample.md) Dieses Beispiel zeigt, wie eine Host Anwendung implementiert wird, die einen einfachen benutzerdefinierten Host verwendet.

 [Host02-Beispiel](./host02-sample.md) In diesem Beispiel wird gezeigt, wie eine Host Anwendung geschrieben wird, die die Windows PowerShell-Laufzeit zusammen mit einer benutzerdefinierten Host Implementierung verwendet. Die Host Anwendung legt die Host Kultur auf Deutsch fest, führt das [Get-Process-](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet aus und zeigt die Ergebnisse an, wie Sie Sie mit pwrsh. exe sehen würden, und gibt dann die aktuellen Daten und die aktuelle Zeit in Deutsch aus.

 [Host03-Beispiel](./host03-sample.md) Dieses Beispiel zeigt, wie eine interaktive konsolenbasierte Host Anwendung erstellt wird, die Befehle in der Befehlszeile liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt.

 [Host04-Beispiel](./host04-sample.md) Dieses Beispiel zeigt, wie eine interaktive konsolenbasierte Host Anwendung erstellt wird, die Befehle in der Befehlszeile liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt. Diese Hostanwendung unterstützt auch das Anzeigen von Eingabeaufforderungen, die es den Benutzern ermöglichen, mehrere Auswahlmöglichkeiten anzugeben.

 [Host05-Beispiel](./host05-sample.md) Dieses Beispiel zeigt, wie eine interaktive konsolenbasierte Host Anwendung erstellt wird, die Befehle in der Befehlszeile liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt. Diese Host Anwendung unterstützt auch Aufrufe von Remote Computern mithilfe der Cmdlets [Enter-PSSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) und [Exit-PSSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) .

 [Host06-Beispiel](./host06-sample.md) Dieses Beispiel zeigt, wie eine interaktive konsolenbasierte Host Anwendung erstellt wird, die Befehle in der Befehlszeile liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt. Darüber hinaus verwendet dieses Beispiel die Tokenizer-APIs, um die Farbe des vom Benutzer eingegebenen Texts anzugeben.

## <a name="see-also"></a>Weitere Informationen
