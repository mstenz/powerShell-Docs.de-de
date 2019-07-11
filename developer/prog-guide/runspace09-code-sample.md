---
title: Codebeispiel RunSpace09 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: 1a21af4b48a414d9c9fee57871eacb0a39c9ab11
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734900"
---
# <a name="runspace09-code-sample"></a>RunSpace09-Codebeispiel

Hier ist der Quellcode, für das Beispiel Runspace09 in beschrieben [erstellen eine Konsole, ruft Anwendung eine Pipeline asynchron](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47). Diese beispielanwendung erstellt und öffnet einen Runspace, erstellt und ruft Sie eine Pipeline asynchron auf, und klicken Sie dann pipeline verwendet Ereignisse, um das Skript asynchron zu verarbeiten. Das Skript, das von dieser Anwendung ausführen erstellt die ganzen Zahlen 1 bis 10 in 0,5-Sekunden-Intervallen (500 ms).

## <a name="code-sample"></a>Codebeispiel

[!code-csharp[Runspace09.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a>Siehe auch

[Windows PowerShell SDK](../windows-powershell-reference.md)