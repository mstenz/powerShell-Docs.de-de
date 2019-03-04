---
title: Windows PowerShell-API-Beispiele | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860776"
---
# <a name="windows-powershell-api-samples"></a>Beispiele für Windows PowerShell-APIs

Dieser Abschnitt enthält Beispielcode, der zeigt, wie zum Erstellen von Runspaces, die Funktionalität einschränken und asynchron ausführen der Befehle mit, dass ein runspacepool der Runspaces angeben. Sie können Microsoft Visual Studio verwenden, erstellen eine Konsolenanwendung, und kopieren Sie den Code in den Themen in diesem Abschnitt, in der hostanwendung.

## <a name="in-this-section"></a>In diesem Abschnitt

[PowerShell01 Beispiel](./windows-powershell01-sample.md) diesem Beispiel wird gezeigt, wie Sie mit einem [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) Objekt, das die Funktionalität von einem Runspace zu beschränken. Die Ausgabe dieses Beispiels wird veranschaulicht, wie beschränken Sie den Sprachmodus, der den Runspace, wie ein Cmdlet als privat markiert, hinzufügen und entfernen-Cmdlets und Anbieter, wie Sie einen Proxybefehl und vieles mehr hinzufügen.

[Beispiel für PowerShell02](./windows-powershell02-sample.md) diesem Beispiel wird gezeigt, wie Befehle asynchron ausgeführt wird, wird der Runspaces, der einen runspacepool verwenden. Im Beispiel generiert eine Liste der Befehle, und klicken Sie dann diese Befehle ausgeführt werden, während des Windows PowerShell-Moduls aus dem Pool einen Runspace öffnet, wenn er benötigt wird.