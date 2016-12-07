---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "Häufige Fehler bei Rollenfunktionen"
ms.technology: powershell
ms.openlocfilehash: 8e928ec07ef98b2ec8186a27d3aefa1450a3a424
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
### <a name="common-role-capability-pitfalls"></a>Häufige Fehler bei Rollenfunktionen
Wenn Sie diesen Prozess alleine absolvieren, könnten Ihnen einige häufig auftretende Fehler unterlaufen.
Hier finden Sie einige wichtige Informationen dazu, wie Sie solche Fehler identifizieren und beheben, wenn Sie einen neuen Endpunkt erstellen oder ändern:

#### <a name="functions-vs-cmdlets"></a>Funktionen im Vergleich zu Cmdlets
In PowerShell geschriebene PowerShell-Befehle sind PowerShell-Funktionen.
Als spezielle .NET-Klassen geschriebene PowerShell-Befehle sind PowerShell-Cmdlets.
Sie können den Befehlstyp prüfen, indem Sie `Get-Command` ausführen.

#### <a name="visibleproviders"></a>VisibleProviders
Sie müssen alle Anbieter verfügbar machen, die von Ihren Befehlen benötigt werden.
Am häufigsten wird der Dateisystemanbieter verwendet, Sie werden jedoch möglicherweise auch weitere Anbieter verfügbar machen müssen, beispielsweise den Registrierungsanbieter.
Eine Einführung in das Thema Anbieter finden Sie in diesem Blogbeitrag von [Hey, Scripting Guy!](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).
Gehen Sie vorsichtig vor, wenn Sie Anbieter verfügbar machen – häufig ist es besser, selbst eine Funktion zu definieren, die mit den zugrunde liegenden Anbietern arbeitet, als den Anbieter in einer JEA-Sitzung direkt verfügbar zu machen.
Auf diese Weise können Sie Benutzern weiterhin ermöglichen, mit Dateien, Registrierungsschlüsseln usw. zu arbeiten, behalten aber dank einer benutzerdefinierten Validierungslogik die Kontrolle darüber, mit **welchen** Dateien und Registrierungsschlüsseln die Benutzer arbeiten.

