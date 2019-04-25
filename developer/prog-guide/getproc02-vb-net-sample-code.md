---
title: GetProc02 Beispielcode (VB.NET) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3497546-5b3a-4e29-84ba-cd9747be64b3
caps.latest.revision: 6
ms.openlocfilehash: 821d0dd327529614322e446bfb30d128d1b6a7f3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081593"
---
# <a name="getproc02-vbnet-sample-code"></a>GetProc02-Codebeispiel (VB.NET)

Der folgende Code zeigt die Implementierung einer `Get-Process` -Cmdlet, das Befehlszeilen-Eingaben akzeptiert. Beachten Sie, die diese Implementierung definiert eine `Name` verwendet Parameter, um die Befehlszeile, und sie können die [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) Methode als Ausgabe Mechanismus zum Senden der Ausgabe Objekte in der Pipeline.

## <a name="code-sample"></a>Codebeispiel

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell SDK](../windows-powershell-reference.md)