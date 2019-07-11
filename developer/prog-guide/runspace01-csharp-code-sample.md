---
title: Runspace01 (C#) Codebeispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: ab067485d70523a16493eb57170615ab300eaa98
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735052"
---
# <a name="runspace01-c-code-sample"></a>Runspace01-Codebeispiel (C#)

Hier sind die Codebeispiele, für der Runspace beschrieben [erstellen eine Konsole Einzelanwendung eines angegebenen Befehls](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program). Zu diesem Zweck die Anwendung einen Runspace aufruft, und ruft dann einen Befehl auf. (Beachten Sie, dass diese Anwendung gibt keinen Runspace-Konfigurationsinformationen oder wird explizit eine Pipeline erstellt.) Der Befehl, der aufgerufen wird, wird die `Get-Process` Cmdlet.

> [!NOTE]
> Sie können die C# Quelldatei (runspace01.cs) für diesen Runspace, mit dem Microsoft Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3.0-Laufzeitkomponenten. Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.

## <a name="code-sample"></a>Codebeispiel

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell Handbuch für Programmierer](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)