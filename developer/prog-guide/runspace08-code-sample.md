---
title: Codebeispiel RunSpace08 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: ec6aae544eafea1dedc1379dab00beeed2c7c436
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734913"
---
# <a name="runspace08-code-sample"></a>RunSpace08-Codebeispiel

Hier ist der Quellcode, für das Beispiel Runspace08 in beschrieben [erstellen eine Anwendung, fügt Konsolenparameter zu einem Befehl](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba). Diese beispielanwendung einen Runspace erstellt, wird eine Pipeline erstellt, die Pipeline zwei Befehle hinzugefügt, mit dem zweiten Befehl werden zwei Parameter hinzugefügt und führt dann die Pipeline. Die Befehle, die der Pipeline hinzugefügt werden, sind die `Get-Process` und `Sort-Object` Cmdlets.

## <a name="code-sample"></a>Codebeispiel

[!code-csharp[Runspace08.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a>Siehe auch

[Windows PowerShell SDK](../windows-powershell-reference.md)