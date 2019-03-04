---
title: Codebeispiel RunSpace06 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: 2874f9df3f5166fbe14deb5b128674540c0d6701
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854036"
---
# <a name="runspace06-code-sample"></a>RunSpace06-Codebeispiel

Hier ist der Quellcode, für das Beispiel Runspace06 in beschrieben [konfigurieren einen Runspace ein Windows PowerShell-Snap-in mit](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83). Diese beispielanwendung erstellt einen Runspace basierend auf einer Windows PowerShell-Snap-in, die dann zum Ausführen einer Pipeline mit einem einzigen Befehl verwendet wird. Zu diesem Zweck die Anwendung die Konfigurationsinformationen des Runspace erstellt, einen Runspace erstellt, erstellt eine Pipeline mit einem einzigen Befehl und führt dann die Pipeline.

> [!NOTE]
> Sie können die C# Quelldatei (runspace06.cs) mithilfe des Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3.0-Laufzeitkomponenten. Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).
> Sie können die C# Quelldatei (runspace06.cs) mithilfe des Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3.0-Laufzeitkomponenten. Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.

## <a name="code-sample"></a>Codebeispiel

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell Handbuch für Programmierer](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)