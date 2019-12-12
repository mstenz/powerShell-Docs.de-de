---
title: Beispiele für die Windows PowerShell-API | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360839"
---
# <a name="windows-powershell-api-samples"></a>Beispiele für Windows PowerShell-APIs

Dieser Abschnitt enthält Beispielcode, der zeigt, wie Sie Runspaces erstellen, die die Funktionalität einschränken, und wie Sie Befehle asynchron ausführen, indem Sie einen Runspace-Pool verwenden, um die Runspaces bereitzustellen. Mit Microsoft Visual Studio können Sie eine Konsolenanwendung erstellen und dann den Code aus den Themen in diesem Abschnitt in die Host Anwendung kopieren.

## <a name="in-this-section"></a>In diesem Abschnitt

[PowerShell01-Beispiel](./windows-powershell01-sample.md) In diesem Beispiel wird gezeigt, wie ein [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt verwendet wird, um die Funktionalität eines Runspace einzuschränken. In der Ausgabe dieses Beispiels wird veranschaulicht, wie der Sprachmodus des Runspace eingeschränkt wird, wie ein Cmdlet als privat markiert wird, wie Cmdlets und Anbieter hinzugefügt und entfernt werden, wie ein Proxy Befehl hinzugefügt wird und vieles mehr.

[PowerShell02-Beispiel](./windows-powershell02-sample.md) In diesem Beispiel wird gezeigt, wie Befehle asynchron mit den Runspaces eines Runspace-Pools ausgeführt werden. Das Beispiel generiert eine Liste mit Befehlen und führt diese Befehle aus, während die Windows PowerShell-Engine einen Runspace aus dem Pool öffnet, wenn Sie benötigt wird.