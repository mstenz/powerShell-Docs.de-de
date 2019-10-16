---
title: Leitfaden für Windows PowerShell-Programmierer&#39;| Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell Programmer's Guide
ms.assetid: f3aaf667-af84-4ea8-a5ad-d454d0d700b8
caps.latest.revision: 9
ms.openlocfilehash: 44a9c970d32dc6f98456227f8b02101280541dd9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360049"
---
# <a name="windows-powershell-programmer39s-guide"></a>Leitfaden für Windows PowerShell-Programmierer&#39;

Dieses Programmier Handbuch richtet sich an Entwickler, die an der Bereitstellung einer Befehlszeilen-Verwaltungs Umgebung für Systemadministratoren interessiert sind. Windows PowerShell bietet eine einfache Möglichkeit zum Erstellen von Verwaltungs Befehlen, die .NET-Objekte verfügbar machen, während Windows PowerShell den größten Teil der Arbeit für Sie ermöglicht.

Bei der herkömmlichen Befehls Entwicklung müssen Sie einen Parameter Parser, einen Parameter Binder, Filter und alle anderen Funktionen schreiben, die von jedem Befehl verfügbar gemacht werden. Windows PowerShell bietet Folgendes, um Ihnen das Schreiben von Befehlen zu erleichtern:

- Eine leistungsstarke Windows PowerShell-Laufzeit (Ausführungs-Engine) mit eigenem Parser und einem Mechanismus zum automatischen Binden von Befehlsparametern.

- Dienstprogramme zum Formatieren und Anzeigen von Befehls Ergebnissen mithilfe eines Befehlszeilen interpreters (CLI).

- Unterstützung für ein hohes Maß an Funktionalität (über Windows PowerShell-Anbieter), die den Zugriff auf gespeicherte Daten erleichtern.

  Mit geringem Kostenaufwand können Sie ein .NET-Objekt durch einen Rich-Befehl oder eine Reihe von Befehlen darstellen, die dem Administrator eine komplette Befehlszeilen Darstellung bieten.

  Der nächste Abschnitt behandelt die wichtigsten Konzepte und Begriffe von Windows PowerShell. Machen Sie sich vor Beginn der Entwicklung mit diesen Konzepten und Begriffen vertraut.

## <a name="about-windows-powershell"></a>Informationen zu Windows PowerShell

Windows PowerShell definiert mehrere Typen von Befehlen, die Sie bei der Entwicklung verwenden können. Diese Befehle umfassen: Funktionen, Filter, Skripts, Aliase und ausführbare Dateien (Anwendungen). Der in diesem Handbuch erörterte hauptbefehlstyp ist ein einfacher, kleiner Befehl, der als "Cmdlet" bezeichnet wird. Windows PowerShell stellt eine Reihe von Cmdlets zur Verfügung und unterstützt die Cmdlet-Anpassung vollständig für Ihre Umgebung. Die Windows PowerShell-Laufzeit verarbeitet alle Befehls Typen wie Cmdlets mithilfe von Pipelines.

Zusätzlich zu den Befehlen unterstützt Windows PowerShell verschiedene anpassbare Windows PowerShell-Anbieter, die bestimmte Sätze von Cmdlets zur Verfügung stellen. Die Shell wird in der von Windows PowerShell bereitgestellten Host Anwendung (Windows PowerShell. exe) betrieben, ist aber gleichermaßen über eine benutzerdefinierte Host Anwendung verfügbar, die Sie für bestimmte Anforderungen entwickeln können. Weitere Informationen finden Sie unter [Funktionsweise von Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

### <a name="windows-powershell-cmdlets"></a>Windows PowerShell-Cmdlets

Ein Cmdlet ist ein Lightweight-Befehl, der in der Windows PowerShell-Umgebung verwendet wird. Die Windows PowerShell-Laufzeit ruft diese Cmdlets im Kontext von Automatisierungs Skripts auf, die in der Befehlszeile bereitgestellt werden, und die Windows PowerShell-Laufzeit ruft Sie auch Programm gesteuert über Windows PowerShell-APIs auf.

Weitere Informationen zu Cmdlets finden Sie unter [Schreiben eines Windows PowerShell-Cmdlets](../cmdlet/writing-a-windows-powershell-cmdlet.md).

### <a name="windows-powershell-providers"></a>Windows PowerShell-Anbieter

Bei der Durchführung administrativer Aufgaben muss der Benutzer möglicherweise Daten untersuchen, die in einem Datenspeicher gespeichert sind (z. b. im Dateisystem, in der Windows-Registrierung oder in einem Zertifikat Speicher). Um diese Vorgänge zu vereinfachen, definiert Windows PowerShell ein Modul, das als Windows PowerShell-Anbieter bezeichnet wird und für den Zugriff auf einen bestimmten Datenspeicher, z. b. die Windows-Registrierung, verwendet werden kann. Jeder Anbieter unterstützt eine Reihe verwandter Cmdlets, um dem Benutzer eine symmetrische Ansicht der Daten im Speicher zu bieten.

Windows PowerShell bietet mehrere standardmäßige Windows PowerShell-Anbieter. Der Registrierungs Anbieter unterstützt z. b. die Navigation und Bearbeitung der Windows-Registrierung. Registrierungsschlüssel werden als Elemente dargestellt, und Registrierungs Werte werden als Eigenschaften behandelt.

Wenn Sie einen Datenspeicher verfügbar machen, auf den der Benutzer zugreifen muss, müssen Sie möglicherweise einen eigenen Windows PowerShell-Anbieter schreiben, wie unter [Erstellen von Windows PowerShell-Anbietern](./how-to-create-a-windows-powershell-provider.md)beschrieben. Weitere Informationen zu Windows PowerShell-Anbietern finden Sie unter [Funktionsweise von Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

### <a name="host-application"></a>Host Anwendung

Windows PowerShell umfasst die Standard Host Anwendung PowerShell. exe, eine Konsolenanwendung, die mit dem Benutzer interagiert und die Windows PowerShell-Laufzeit mithilfe eines Konsolenfensters hostet.

Nur selten müssen Sie eine eigene Host Anwendung für Windows PowerShell schreiben, auch wenn die Anpassung unterstützt wird. Ein Fall, in dem Sie möglicherweise Ihre eigene Anwendung benötigen, ist die Anforderung einer GUI-Schnittstelle, die umfangreicher als die von der Standard Host Anwendung bereitgestellte Schnittstelle ist. Möglicherweise möchten Sie auch eine benutzerdefinierte Anwendung, wenn Sie die GUI in der Befehlszeile haben. Weitere Informationen finden Sie unter [Erstellen einer Windows PowerShell-Host Anwendung](/powershell/developer/hosting/writing-a-windows-powershell-host-application).

### <a name="windows-powershell-runtime"></a>Windows PowerShell-Laufzeit

Die Windows PowerShell-Laufzeit ist die Ausführungs-Engine, die die Befehls Verarbeitung implementiert. Sie enthält die Klassen, die die Schnittstelle zwischen der Host Anwendung und Windows PowerShell-Befehlen und-Anbietern bereitstellen. Die Windows PowerShell-Laufzeit wird als Runspace-Objekt für die aktuelle Windows PowerShell-Sitzung implementiert, bei der es sich um die Betriebsumgebung handelt, in der die Shell und die Befehle ausgeführt werden. Ausführliche Informationen zu den Betriebs Details finden Sie unter [Funktionsweise von Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

### <a name="windows-powershell-language"></a>Windows PowerShell-Sprache

Die Windows PowerShell-Sprache stellt Skriptfunktionen und Mechanismen zum Aufrufen von Befehlen bereit. Ausführliche Informationen zur Skripterstellung finden Sie in der Windows PowerShell-Sprachreferenz in Windows PowerShell.

### <a name="extended-type-system-ets"></a>Erweitertes Typsystem (ETS)

Windows PowerShell ermöglicht den Zugriff auf eine Vielzahl von unterschiedlichen Objekten, z. b. auf .net-und XML-Objekte. Folglich verwendet die Shell das erweiterte Typsystem (ETS), um eine gemeinsame Abstraktion für alle Objekttypen darzustellen. Die meisten ETS-Funktionen sind für den Benutzer transparent, das Skript oder .NET-Entwickler verwendet Sie jedoch für folgende Zwecke:

- Anzeigen einer Teilmenge der Member bestimmter Objekte. Windows PowerShell bietet eine "angepasste" Ansicht mehrerer bestimmter Objekttypen.

- Hinzufügen von Membern zu vorhandenen Objekten.

- Zugriff auf serialisierte Objekte.

- Schreiben von angepassten Objekten.

  Mithilfe von ETS können Sie flexible neue "Typen" erstellen, die mit der Windows PowerShell-Sprache kompatibel sind. Wenn Sie .NET-Entwickler sind, können Sie mit Objekten arbeiten, die dieselbe Semantik wie die Windows PowerShell-Sprache für Skripts verwenden, um beispielsweise zu ermitteln, ob ein Objekt zu `true` ausgewertet wird.

  Weitere Informationen zu ETS und zur Verwendung von Objekten in Windows PowerShell finden Sie unter [Windows PowerShell-Objekt Konzepte](/powershell/scripting/learn/understanding-important-powershell-concepts?view=powershell-6).

## <a name="programming-for-windows-powershell"></a>Programmieren für Windows PowerShell

Windows PowerShell definiert den Code für Befehle, Anbieter und andere Programmmodule, die die .NET Framework verwenden. Sie sind nicht auf die Verwendung von Microsoft Visual Studio bei der Erstellung angepasster Module für Windows PowerShell beschränkt, obwohl die in diesem Handbuch bereitgestellten Beispiele bekanntermaßen in diesem Tool ausgeführt werden. Sie können jede .NET-Sprache verwenden, die die Klassen Vererbung und die Verwendung von Attributen unterstützt. In einigen Fällen erfordern Windows PowerShell-APIs, dass die Programmiersprache auf generische Typen zugreifen kann.

## <a name="programmers-reference"></a>Programmierer-Referenz

Informationen zur Referenz bei der Entwicklung für Windows PowerShell finden Sie unter [Windows PowerShell SDK](../windows-powershell-reference.md).

## <a name="getting-started-using-windows-powershell"></a>Einstieg in die Verwendung von Windows PowerShell

Weitere Informationen zum Einstieg in die Verwendung der Windows PowerShell-Shell finden Sie unter Erste Schritte [mit Windows](/powershell/scripting/getting-started/getting-started-with-windows-powershell) PowerShell in Windows PowerShell. Ein kurz Verweis-Trifold-Dokument wird auch als Einführung für die Cmdlet-Verwendung bereitgestellt.

## <a name="contents-of-this-guide"></a>Inhalt dieses Handbuchs

|Thema|Definition|
|-----------|----------------|
|[Erstellen eines Windows PowerShell-Anbieters](./how-to-create-a-windows-powershell-provider.md)|In diesem Abschnitt wird beschrieben, wie Sie einen Windows PowerShell-Anbieter für Windows PowerShell erstellen.|
|[Erstellen einer Windows PowerShell-Host Anwendung](/powershell/developer/hosting/writing-a-windows-powershell-host-application)|In diesem Abschnitt wird beschrieben, wie Sie eine Host Anwendung schreiben, die einen Runspace manipuliert und wie Sie eine Host Anwendung schreiben, die ihren eigenen benutzerdefinierten Host implementiert.|
|[Erstellen eines Windows PowerShell-Snap-Ins](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|In diesem Abschnitt wird beschrieben, wie Sie ein Snap-in erstellen, das zum Registrieren aller Cmdlets und Anbieter in einer Assembly verwendet wird, und wie Sie ein benutzerdefiniertes Snap-in erstellen.|
|[Erstellen einer Konsolen-Shell](./how-to-create-a-console-shell.md)|In diesem Abschnitt wird beschrieben, wie eine Konsolen Shell erstellt wird, die nicht erweiterbar ist.|
|[Windows PowerShell-Konzepte](./windows-powershell-concepts.md)|Dieser Abschnitt enthält konzeptionelle Informationen, die Ihnen helfen, Windows PowerShell vom Standpunkt eines Entwicklers zu verstehen.|

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell SDK](../windows-powershell-reference.md)
