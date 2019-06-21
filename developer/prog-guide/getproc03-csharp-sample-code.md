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
ms.openlocfilehash: 116a116a5ba5b81a77b4432a81f001cc999fe46d
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301354"
---
# <a name="getproc03-c-sample-code"></a>GetProc03-Codebeispiel (C#)

Der folgende Code zeigt die Implementierung einer `Get-Process` -Cmdlet, das annehmen kann Pipeline-Eingabe. Diese Implementierung definiert eine `Name` Parameter, die Pipeline-Eingaben akzeptiert Prozessinformationen aus dem lokalen Computer, die basierend auf den angegebenen Namen abgerufen und verwendet dann die [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)Methode als Ausgabemechanismus für die Objekte werden an die Pipeline gesendet.

> [!NOTE]
> Sie können die C# Quelldatei (getprov03.cs) für dieses Get-Proc-Cmdlet mit dem Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3.0-Laufzeitkomponenten. Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.

## <a name="code-sample"></a>Codebeispiel

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell Handbuch für Programmierer](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
