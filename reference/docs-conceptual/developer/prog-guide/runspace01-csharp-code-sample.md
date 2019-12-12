---
title: Runspace01 (C#)-Code Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 607113ed566fc1e08e5b1d7092c83da2a22366ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74418023"
---
# <a name="runspace01-c-code-sample"></a>Runspace01-Codebeispiel (C#)

Im folgenden finden Sie die Codebeispiele für den Runspace [, der unter Erstellen einer Konsolenanwendung beschrieben wird, die einen angegebenen Befehl ausführt](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program). Hierzu ruft die Anwendung einen Runspace auf und ruft dann einen Befehl auf. (Beachten Sie, dass diese Anwendung keine Informationen zur Runspace-Konfiguration angibt und keine Pipeline explizit erstellt). Der Befehl, der aufgerufen wird, ist das Cmdlet "`Get-Process`".

> [!NOTE]
> Sie können die C# Quelldatei (runspace01.cs) für diesen Runspace mithilfe der Laufzeitkomponenten Microsoft Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3,0 herunterladen. Anweisungen zum Herunterladen finden Sie unter [Installieren von Windows PowerShell und Herunterladen des Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> Die heruntergeladenen Quelldateien stehen im **\<PowerShell-Beispiele >** Verzeichnis zur Verfügung.

## <a name="code-sample"></a>Codebeispiel

[!code-csharp[Runspace01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell-Programmier Handbuch](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
