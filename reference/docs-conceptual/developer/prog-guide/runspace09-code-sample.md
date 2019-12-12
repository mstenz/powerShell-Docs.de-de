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
ms.openlocfilehash: 122a40dea93d874a7c131774e3d1abb148bcd4fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360129"
---
# <a name="runspace09-code-sample"></a>RunSpace09-Codebeispiel

Im folgenden finden Sie den Quellcode für das Runspace09-Beispiel [, das unter Erstellen einer Konsolenanwendung beschrieben wird, die eine Pipeline asynchron](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47)aufruft. Diese Beispielanwendung erstellt und öffnet einen Runspace, erstellt eine Pipeline und ruft Sie asynchron auf und verwendet dann Pipeline Ereignisse, um das Skript asynchron zu verarbeiten. Das Skript, das von dieser Anwendung ausgeführt wird, erstellt die ganzen Zahlen 1 bis 10 in Intervallen von 0,5 Sekunden (500 ms).

## <a name="code-sample"></a>Codebeispiel

[!code-csharp[Runspace09.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell SDK](../windows-powershell-reference.md)
