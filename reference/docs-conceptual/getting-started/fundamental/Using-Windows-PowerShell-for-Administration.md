---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Verwaltung mit Windows PowerShell
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: 69790ddd6bae26dd18e30af860bad4c749cd86a5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="using-windows-powershell-for-administration"></a>Verwaltung mit Windows PowerShell
Das grundlegende Ziel von Windows PowerShell ist das Ermöglichen einer besseren und einfacheren administrativen Kontrolle über Systeme, entweder interaktiv oder per Skript. In diesem Kapitel werden Lösungen für viele spezifische Probleme bei der Verwaltung von Windows-Systemen mit Windows PowerShell erläutert. Obwohl wir im Windows PowerShell-Benutzerhandbuch nicht die Rede von Skripts oder Funktionen ist, können die Lösungen später in Skripts oder als Funktionen verwendet werden. Wir zeigen Beispiele, die Funktionen als Teil der Lösung zum Beheben von Problemen enthalten.

In sämtlichen Lösungsbeschreibungen finden Sie eine Mischung aus Lösungen bestehend aus bestimmten Cmdlets, dem allgemeinen Cmdlet „Get-WmiObject“ und sogar externen Tools, die Teil der Windows- und .NET Framework-Infrastruktur sind. Die Verwendung externer Tools ist Teil des langfristigen Entwurfsziels von Windows PowerShell. Sobald die Systeme wachsen, werden Benutzer immer wieder auf Situationen treffen, in denen die verfügbaren Toolsets nicht alles leisten, was benötigt wird. Anstatt die Abhängigkeit allein von Cmdlet-Implementierungen zu fördern, versucht Windows PowerShell, die Integration von Lösungen aus allen möglichen alternativen Szenarien zu unterstützen.