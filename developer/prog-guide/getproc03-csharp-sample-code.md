---
title: GetProc03 (C#)-Codebeispiele | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 4d921dd62999bc68b80838bafa2a3da8d4df3ebb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081517"
---
# <a name="getproc03-c-sample-code"></a>GetProc03-Codebeispiel (C#)

Der folgende Code zeigt die Implementierung einer `Get-Process` -Cmdlet, das annehmen kann Pipeline-Eingabe. Diese Implementierung definiert eine `Name` Parameter, die Pipeline-Eingaben akzeptiert Prozessinformationen aus dem lokalen Computer, die basierend auf den angegebenen Namen abgerufen und verwendet dann die [System.Management.Automation.Cmdlet.WriteObject% 28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) Methode als Ausgabemechanismus für die Objekte werden an die Pipeline gesendet.

> [!NOTE]
> Sie können die C# Quelldatei (getprov03.cs) für dieses Get-Proc-Cmdlet mit dem Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3.0-Laufzeitkomponenten. Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.

## <a name="code-sample"></a>Codebeispiel

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell Handbuch für Programmierer](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)