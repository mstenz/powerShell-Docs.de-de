---
title: RunSpace03 (C#)-Code Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 9afdb97b8ae2919f091ca5bacccedbe37c2e1584
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848027"
---
# <a name="runspace03-c-code-sample"></a>Runspace03-Codebeispiel (C#)

Im folgenden finden C# Sie den Quellcode für die Konsolenanwendung, die unter "Erstellen einer Konsolenanwendung, die ein bestimmtes Skript ausführt" beschrieben wird. In diesem Beispiel wird die [System. Management. Automation. runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) -Klasse verwendet, um ein Skript auszuführen, das Prozessinformationen mithilfe der Liste der Prozessnamen abruft, die an das Skript übermittelt werden. Es zeigt, wie Eingabe Objekte an ein Skript übergeben werden und wie Fehler Objekte sowie die Ausgabe Objekte abgerufen werden.

> [!NOTE]
> Sie können die C# Quelldatei (runspace03.cs) für dieses Beispiel mithilfe der Laufzeitkomponenten Microsoft Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3,0 herunterladen. Anweisungen zum Herunterladen finden Sie unter [Installieren von Windows PowerShell und Herunterladen des Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
> Die heruntergeladenen Quelldateien sind im > Verzeichnis für  **\<PowerShell-Beispiele** verfügbar.

## <a name="code-sample"></a>Code Beispiel

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell-Programmier Handbuch](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)