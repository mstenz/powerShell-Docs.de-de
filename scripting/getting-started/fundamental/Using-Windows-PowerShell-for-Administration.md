---
title:  Verwaltung mit Windows PowerShell
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  db6334ec-ace6-436d-ab88-77aefc817511
---

# Verwaltung mit Windows PowerShell
Das grundlegende Ziel von Windows PowerShell ist das Ermöglichen einer besseren und einfacheren administrativen Kontrolle über Systeme, entweder interaktiv oder per Skript. In diesem Kapitel werden Lösungen für viele spezifische Probleme bei der Verwaltung von Windows-Systemen mit Windows PowerShell erläutert. Obwohl wir im Windows PowerShell-Benutzerhandbuch nicht die Rede von Skripts oder Funktionen ist, können die Lösungen später in Skripts oder als Funktionen verwendet werden. Wir zeigen Beispiele, die Funktionen als Teil der Lösung zum Beheben von Problemen enthalten.

In sämtlichen Lösungsbeschreibungen finden Sie eine Mischung aus Lösungen bestehend aus bestimmten Cmdlets, dem allgemeinen Cmdlet „Get-WmiObject“ und sogar externen Tools, die Teil der Windows- und .NET Framework-Infrastruktur sind. Die Verwendung externer Tools ist Teil des langfristigen Entwurfsziels von Windows PowerShell. Sobald die Systeme wachsen, werden Benutzer immer wieder auf Situationen treffen, in denen die verfügbaren Toolsets nicht alles leisten, was benötigt wird. Anstatt die Abhängigkeit allein von Cmdlet-Implementierungen zu fördern, versucht Windows PowerShell, die Integration von Lösungen aus allen möglichen alternativen Szenarien zu unterstützen.



<!--HONumber=May16_HO2-->


