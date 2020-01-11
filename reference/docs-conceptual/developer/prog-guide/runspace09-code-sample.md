---
title: RunSpace09-Code Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: 2f447fd0ce21c5bca8abe1fddb4e3c7025b70ef1
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870579"
---
# <a name="runspace09-code-sample"></a>RunSpace09-Codebeispiel

Im folgenden finden Sie den Quellcode für das Runspace09-Beispiel [, das unter Erstellen einer Konsolenanwendung beschrieben wird, die eine Pipeline asynchron](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47)aufruft.
Diese Beispielanwendung erstellt und öffnet einen Runspace, erstellt eine Pipeline und ruft Sie asynchron auf und verwendet dann Pipeline Ereignisse, um das Skript asynchron zu verarbeiten. Das Skript, das von dieser Anwendung ausgeführt wird, erstellt die ganzen Zahlen 1 bis 10 in Intervallen von 0,5 Sekunden (500 ms).

## <a name="code-sample"></a>Codebeispiel

[!code-csharp[Runspace09.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a>Siehe auch

[Windows PowerShell SDK](../windows-powershell-reference.md)
