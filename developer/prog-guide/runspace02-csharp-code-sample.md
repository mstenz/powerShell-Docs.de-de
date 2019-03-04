---
title: Runspace02 (C#) Codebeispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59a7b8b9-f72e-43fd-9a10-77404441a3f2
caps.latest.revision: 6
ms.openlocfilehash: 0a8fc05db74529e2bfb88820b9cfd988245e0aeb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854616"
---
# <a name="runspace02-c-code-sample"></a>Runspace02-Codebeispiel (C#)

Hier ist die C# Quellcode für das Beispiel Runspace02. Dieses Beispiel verwendet die [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) Klasse zum Ausführen der `Get-Process` Cmdlet synchron. Windows Forms und Datenbindung werden dann zum Anzeigen der Ergebnisse in einem DataGridView-Steuerelement

## <a name="code-sample"></a>Codebeispiel

[!code-csharp[Runspace02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs#L11-L82 "Runspace02.cs")]

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell SDK](../windows-powershell-reference.md)