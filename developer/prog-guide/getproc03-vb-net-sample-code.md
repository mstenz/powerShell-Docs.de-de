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
ms.openlocfilehash: a0a88ca517347a94fc81534caace6efa0f13fdd7
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301571"
---
# <a name="getproc03-vbnet-sample-code"></a>GetProc03-Codebeispiel (VB.NET)

Der folgende Code zeigt die Implementierung einer `Get-Process` -Cmdlet, das annehmen kann Pipeline-Eingabe. Diese Implementierung definiert eine `Name` Parameter, die Pipeline-Eingaben akzeptiert Prozessinformationen aus dem lokalen Computer, die basierend auf den angegebenen Namen abgerufen und verwendet dann die [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)Methode als Ausgabemechanismus für die Objekte werden an die Pipeline gesendet.

## <a name="code-sample"></a>Codebeispiel

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
