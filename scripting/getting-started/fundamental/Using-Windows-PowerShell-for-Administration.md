---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Verwaltung mit Windows PowerShell
ms.technology: powershell
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: c0a15bc813e6fdb850fe2d957711f1ad005d853d
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="using-windows-powershell-for-administration"></a>Verwaltung mit Windows PowerShell
Das grundlegende Ziel von Windows PowerShell ist das Ermöglichen einer besseren und einfacheren administrativen Kontrolle über Systeme, entweder interaktiv oder per Skript. In diesem Kapitel werden Lösungen für viele spezifische Probleme bei der Verwaltung von Windows-Systemen mit Windows PowerShell erläutert. Obwohl wir im Windows PowerShell-Benutzerhandbuch nicht die Rede von Skripts oder Funktionen ist, können die Lösungen später in Skripts oder als Funktionen verwendet werden. Wir zeigen Beispiele, die Funktionen als Teil der Lösung zum Beheben von Problemen enthalten.

In sämtlichen Lösungsbeschreibungen finden Sie eine Mischung aus Lösungen bestehend aus bestimmten Cmdlets, dem allgemeinen Cmdlet „Get-WmiObject“ und sogar externen Tools, die Teil der Windows- und .NET Framework-Infrastruktur sind. Die Verwendung externer Tools ist Teil des langfristigen Entwurfsziels von Windows PowerShell. Sobald die Systeme wachsen, werden Benutzer immer wieder auf Situationen treffen, in denen die verfügbaren Toolsets nicht alles leisten, was benötigt wird. Anstatt die Abhängigkeit allein von Cmdlet-Implementierungen zu fördern, versucht Windows PowerShell, die Integration von Lösungen aus allen möglichen alternativen Szenarien zu unterstützen.

