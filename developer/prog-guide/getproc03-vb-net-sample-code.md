---
title: GetProc03 Beispielcode (VB.NET) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: da85155c43471150a7b35ac37c1dce0790277084
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854636"
---
# <a name="getproc03-vbnet-sample-code"></a>GetProc03-Codebeispiel (VB.NET)

Der folgende Code zeigt die Implementierung einer `Get-Process` -Cmdlet, das annehmen kann Pipeline-Eingabe. Diese Implementierung definiert eine `Name` Parameter, die Pipeline-Eingaben akzeptiert Prozessinformationen aus dem lokalen Computer, die basierend auf den angegebenen Namen abgerufen und verwendet dann die [System.Management.Automation.Cmdlet.Writeobject% 28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) Methode als Ausgabemechanismus für die Objekte werden an die Pipeline gesendet.

## <a name="code-sample"></a>Codebeispiel

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->