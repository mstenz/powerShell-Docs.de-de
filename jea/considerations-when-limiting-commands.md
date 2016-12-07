---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "Überlegungen zum Einschränken von Befehlen"
ms.technology: powershell
ms.openlocfilehash: 0b4396ee130d99c42f613c1b79193c236ad472e7
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
### <a name="considerations-when-limiting-commands"></a>Überlegungen zum Einschränken von Befehlen
Ein wichtiger Hinweis zu diesem Schritt:
Es ist von entscheidender Bedeutung, dass alle über JEA verfügbar gemachten Funktionen sich in Bereichen befinden, auf die nur Administratoren zugreifen können.
Benutzer ohne Administratorrechte dürfen nicht die Möglichkeit haben, die verwendeten Skripts über JEA-Endpunkte zu ändern.

In diesem Zusammenhang ist es ebenso wichtig, dass Sie JEA-Benutzern nicht die Möglichkeit bieten, JEA-Konfigurationen und Skripts auf der Whitelist in ihren JEA-Sitzungen zu überschreiben.
Gehen Sie mit größter Umsicht vor, wenn Sie Befehle wie `Copy-Item` verfügbar machen!

