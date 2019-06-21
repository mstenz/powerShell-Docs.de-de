---
title: GetProc02 (C#)-Codebeispiele | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: c4e7c13ffc26980e533530965187df8563003470
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301552"
---
# <a name="getproc02-c-sample-code"></a>GetProc02-Codebeispiel (C#)

Der folgende Code zeigt die Implementierung einer `Get-Process` -Cmdlet, das Befehlszeilen-Eingaben akzeptiert. Beachten Sie, die diese Implementierung definiert eine `Name` verwendet Parameter, um die Befehlszeile, und sie können die [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) Objekte Methode als Ausgabemechanismus zum Senden der Ausgabe der Pipeline.

## <a name="code-sample"></a>Codebeispiel

[!code-csharp[GetProcessSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell SDK](../windows-powershell-reference.md)
