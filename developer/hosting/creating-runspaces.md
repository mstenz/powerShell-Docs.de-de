---
title: Erstellen von Runspaces | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857906"
---
# <a name="creating-runspaces"></a>Erstellen von Runspaces

Ein Runspace ist die betriebsumgebung für die Befehle, die von einer hostanwendung aufgerufen werden. Diese Umgebung umfasst die Befehle und Daten, die derzeit vorhanden sind, und Language Einschränkungen, die derzeit gelten.

 Hosten von Anwendungen mit dem standardmäßigen Runspace, der von Windows PowerShell, das alle verfügbaren Kern-Befehle enthält bereitgestellt wird, oder erstellen einen benutzerdefinierten Runspace, der nur eine Teilmenge der verfügbaren Befehle enthält. Um einen benutzerdefinierten Runspace zu erstellen, erstellen Sie eine [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) Objekt aus, und weisen sie Sie Ihrem Runspace.

## <a name="runspace-tasks"></a>Runspace-Aufgaben

1. [Erstellen eine InitialSessionState](./creating-an-initialsessionstate.md)

2. [Erstellen einen eingeschränkten runspace](./creating-a-constrained-runspace.md)

3. [Erstellen von mehreren runspaces](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Weitere Informationen
