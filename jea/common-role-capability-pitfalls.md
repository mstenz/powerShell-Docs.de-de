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
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 0e221c840f083ce0b8ecbcbb34c184bcdbc0c73e

---

### Häufige Fehler bei Rollenfunktionen
Wenn Sie diesen Prozess alleine absolvieren, könnten Ihnen einige häufig auftretende Fehler unterlaufen.
Hier finden Sie einige wichtige Informationen dazu, wie Sie solche Fehler identifizieren und beheben, wenn Sie einen neuen Endpunkt erstellen oder ändern:

#### Funktionen im Vergleich zu Cmdlets
In PowerShell geschriebene PowerShell-Befehle sind PowerShell-Funktionen.
Als spezielle .NET-Klassen geschriebene PowerShell-Befehle sind PowerShell-Cmdlets.
Sie können den Befehlstyp prüfen, indem Sie `Get-Command` ausführen.

#### VisibleProviders
Sie müssen alle Anbieter verfügbar machen, die von Ihren Befehlen benötigt werden.
Am häufigsten wird der Dateisystemanbieter verwendet, Sie werden jedoch möglicherweise auch weitere Anbieter verfügbar machen müssen, beispielsweise den Registrierungsanbieter.
Eine Einführung in das Thema Anbieter finden Sie in diesem Blogbeitrag von [Hey, Scripting Guy!](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).
Gehen Sie vorsichtig vor, wenn Sie Anbieter verfügbar machen – häufig ist es besser, selbst eine Funktion zu definieren, die mit den zugrunde liegenden Anbietern arbeitet, als den Anbieter in einer JEA-Sitzung direkt verfügbar zu machen.
Auf diese Weise können Sie Benutzern weiterhin ermöglichen, mit Dateien, Registrierungsschlüsseln usw. zu arbeiten, behalten aber dank einer benutzerdefinierten Validierungslogik die Kontrolle darüber, mit **welchen** Dateien und Registrierungsschlüsseln die Benutzer arbeiten.




<!--HONumber=Jun16_HO4-->


