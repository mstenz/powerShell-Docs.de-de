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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367579"
---
# <a name="creating-runspaces"></a>Erstellen von Runspaces

Ein Runspace ist die Betriebsumgebung für die Befehle, die von einer Host Anwendung aufgerufen werden. Diese Umgebung umfasst die derzeit vorhandenen Befehle und Daten sowie alle derzeit geltenden Spracheinschränkungen.

 Host Anwendungen können den von Windows PowerShell bereitgestellten standardrunspace verwenden, der alle verfügbaren Kern Befehle enthält, oder einen benutzerdefinierten Runspace erstellen, der nur eine Teilmenge der verfügbaren Befehle enthält. Um einen benutzerdefinierten Runspace zu erstellen, erstellen Sie ein [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt, und weisen Sie es Ihrem Runspace zu.

## <a name="runspace-tasks"></a>Runspace-Tasks

1. [Erstellen eines initialsessionstate](./creating-an-initialsessionstate.md)

2. [Erstellen eines eingeschränkten Runspace](./creating-a-constrained-runspace.md)

3. [Erstellen mehrerer Runspaces](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Weitere Informationen
