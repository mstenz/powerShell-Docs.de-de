---
ms.date: 2017-06-05T00:00:00.000Z
keywords: powershell,cmdlet
title: Verwaltung mit Windows PowerShell
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: fa87745b9be04d14de37a308d870b73c5a98cf83
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2017
---
# <a name="using-windows-powershell-for-administration"></a>Verwaltung mit Windows PowerShell
Das grundlegende Ziel von Windows PowerShell ist das Ermöglichen einer besseren und einfacheren administrativen Kontrolle über Systeme, entweder interaktiv oder per Skript. In diesem Kapitel werden Lösungen für viele spezifische Probleme bei der Verwaltung von Windows-Systemen mit Windows PowerShell erläutert. Obwohl wir im Windows PowerShell-Benutzerhandbuch nicht die Rede von Skripts oder Funktionen ist, können die Lösungen später in Skripts oder als Funktionen verwendet werden. Wir zeigen Beispiele, die Funktionen als Teil der Lösung zum Beheben von Problemen enthalten.

In sämtlichen Lösungsbeschreibungen finden Sie eine Mischung aus Lösungen bestehend aus bestimmten Cmdlets, dem allgemeinen Cmdlet „Get-WmiObject“ und sogar externen Tools, die Teil der Windows- und .NET Framework-Infrastruktur sind. Die Verwendung externer Tools ist Teil des langfristigen Entwurfsziels von Windows PowerShell. Sobald die Systeme wachsen, werden Benutzer immer wieder auf Situationen treffen, in denen die verfügbaren Toolsets nicht alles leisten, was benötigt wird. Anstatt die Abhängigkeit allein von Cmdlet-Implementierungen zu fördern, versucht Windows PowerShell, die Integration von Lösungen aus allen möglichen alternativen Szenarien zu unterstützen.

