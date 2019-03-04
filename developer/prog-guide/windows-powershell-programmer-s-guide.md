---
title: Windows PowerShell-Programmierer&#39;Benutzerhandbuch | Microsoft-Dokumentation
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
ms.openlocfilehash: 1f7b5b60b202f4de0cf3d44b65057f5edd41f2b0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860046"
---
# <a name="windows-powershell-programmer39s-guide"></a>Windows PowerShell-Programmierer&#39;Benutzerhandbuch

Diese Handbuch für Programmierer ist auf Entwickler ausgerichtet, die eine Befehlszeile verwaltungsumgebung für Systemadministratoren, anbieten möchten. Windows PowerShell bietet eine einfache Möglichkeit für Sie Befehle zum Verwalten der erstellen, die .NET Objekte verfügbar zu machen, gleichzeitig werden Windows PowerShell die meiste Arbeit für Sie tun.

Bei der herkömmlichen Entwicklung müssen Sie einen Parameter-Parser, einen Binder für Parameter, Filter und alle anderen Funktionen, die verfügbar gemacht werden, indem Sie jeden Befehl zu schreiben. Windows PowerShell bietet Folgendes ein, um das Schreiben von Befehlen erleichtern:

- Eine leistungsstarke Windows PowerShell-Laufzeit (ausführungs-Engine) mit eigenen Parser und einen Mechanismus zum Binden von Parametern automatisch.

- Dienstprogramme für das Formatieren und Anzeigen der Ergebnisse von Befehlen mit einem Interpreter über die Befehlszeile (CLI).

- Unterstützung für hohes Maß an Funktionalität (über Windows PowerShell-Anbieter), die Zugriff auf gespeicherte Daten zu erleichtern.

  Mit geringen Kosten können Sie ein .NET Objekt durch einen umfassenden Befehl oder eine Gruppe von Befehlen, die eine vollständige Befehlszeile-Benutzeroberfläche an dem Administrator anbieten möchten darstellen.

  Im nächste Abschnitt behandelt die wichtigsten Windows PowerShell-Konzepten und Begriffen. Machen Sie sich diese Konzepte und Begriffe, die vor Beginn der Entwicklung.

## <a name="about-windows-powershell"></a>Informationen zu Windows PowerShell

Windows PowerShell definiert mehrere Typen von Befehlen, die Sie verwenden können, in der Entwicklung. Zu diesen Befehlen zählen: Funktionen, Filter, Skripts, Aliasen und ausführbare Dateien (Anwendungen). Der Hauptbefehl-Typ, der in diesem Handbuch beschriebene ist die einfache, kleine Befehl eine "Cmdlet". Windows PowerShell stellt bereit einen Satz von Cmdlets und Cmdlet-Anpassungen entsprechend Ihrer Umgebung vollständig unterstützt. Die Windows PowerShell-Laufzeit verarbeitet alle Befehlstypen, genau wie Cmdlets, die mithilfe von Pipelines.

Zusätzlich zu den Befehlen unterstützt Windows PowerShell die verschiedenen anpassbaren Windows PowerShell-Anbieter, die zur Verfügung bestimmte Gruppen von Cmdlets zu machen. Die Shell ausgeführt wird, in die bereitgestellte Windows PowerShell-hostanwendung (Windows PowerShell.exe), aber es ist genauso zugegriffen werden kann, in einer benutzerdefinierten hostanwendung, die Sie entwickeln können, um bestimmte Anforderungen zu erfüllen. Weitere Informationen finden Sie unter [Funktionsweise von Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="windows-powershell-cmdlets"></a>Windows PowerShell-Cmdlets

Ein Cmdlet ist ein einfacher Befehl, der in der Windows PowerShell-Umgebung verwendet wird. Die Windows PowerShell-Laufzeit ruft diese Cmdlets im Kontext des Automation-Skripts, die in der Befehlszeile bereitgestellt werden, und die Windows PowerShell-Laufzeit auch ruft diese programmgesteuert über Windows PowerShell-APIs.

Weitere Informationen zu den Cmdlets finden Sie unter [Schreiben eines Windows PowerShell-Cmdlets](../cmdlet/writing-a-windows-powershell-cmdlet.md).

### <a name="windows-powershell-providers"></a>Windows PowerShell-Anbieter

Bei der Ausführung von Verwaltungsaufgaben, kann der Benutzer müssen in einem Datenspeicher (z. B. das Dateisystem, die Windows-Registrierung oder einen Zertifikatspeicher) gespeicherte Daten zu untersuchen. Um diese Vorgänge zu vereinfachen, definiert die Windows PowerShell ein Modul namens einen Windows PowerShell-Anbieter, der auf einen bestimmten Datenspeicher, z. B. die Windows-Registrierung verwendet werden kann. Jeder Anbieter unterstützt eine Reihe von verwandten Cmdlets, die der Benutzer eine symmetrische Ansicht der Daten im Speicher zugewiesen.

Windows PowerShell stellt mehrere Windows PowerShell-Anbieter. Der Registrierungsanbieter unterstützt beispielsweise navigieren und Bearbeiten der Windows-Registrierung. Registrierungsschlüssel werden als Elemente dargestellt, und die Registrierungswerte werden als Eigenschaften behandelt.

Wenn Sie einen Datenspeicher verfügbar, die der Benutzer zugreifen muss machen, müssen möglicherweise schreiben Ihren eigenen Windows PowerShell-Anbieter, wie in beschrieben [Erstellen von Windows PowerShell-Anbieter](./how-to-create-a-windows-powershell-provider.md). Weitere Informationen AboutWindows PowerShell-Anbieter, finden Sie unter [Funktionsweise von Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="host-application"></a>Hostanwendung

Windows PowerShell umfasst die Standard-Host Anwendung powershell.exe, eine Konsolenanwendung, die mit der Benutzer interagiert, und hostet die Windows PowerShell-Laufzeit, die mit einem Konsolenfenster.

Nur selten müssen Sie zum Schreiben Ihrer eigenen hostanwendung für Windows PowerShell auch Anpassung unterstützt wird. Ein Fall, in dem Sie Ihre eigene Anwendung möglicherweise, ist bei einer Anforderung für eine Grafische Benutzeroberfläche, die umfangreicher als die Schnittstelle, von der hostanwendung standardmäßig bereitgestellt wird. Sie sollten auch eine benutzerdefinierte Anwendung, wenn die grafische Benutzeroberfläche, über die Befehlszeile basiert. Weitere Informationen finden Sie unter[Vorgehensweise: Erstellen einer Windows PowerShell-Hostanwendung](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07).

### <a name="windows-powershell-runtime"></a>Windows PowerShell-Laufzeit

Die Windows PowerShell-Laufzeit ist der ausführungs-Engine, die befehlsverarbeitung implementiert. Sie enthält die Klassen, die Schnittstelle zwischen der hostanwendung und Windows PowerShell-Befehle und Anbieter zu ermöglichen. Die Windows PowerShell-Laufzeit wird als ein Runspace-Objekt für die aktuelle Windows PowerShell-Sitzung implementiert, die die betriebsumgebung ist in der die Shell und die Befehle ausgeführt. Betriebsbezogenen Details, finden Sie unter [Funktionsweise von Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="windows-powershell-language"></a>Windows PowerShell-Sprache

Die Windows PowerShell-Sprache bietet scripting Funktionen und Mechanismen ein, um Befehle aufrufen. Vollständige Informationen zu Skripts finden Sie die Windows PowerShell-Sprachreferenz Lieferumfang von Windows PowerShell.

### <a name="extended-type-system-ets"></a>Extended Typensystem (ETS)

Windows PowerShell ermöglicht den Zugriff auf eine Vielzahl von verschiedenen Objekte, z. B. .NET und XML-Objekte. Um eine allgemeine Abstraktion für alle Objekttypen zu präsentieren verwendet daher die Shell die erweiterten Typ-System (ETS) an. Die meisten ETS-Funktionalität ist für den Benutzer transparent, aber das Skript bzw. die .NET Entwickler es für folgende Zwecke verwendet:

- Zeigen eine Untermenge der Mitglieder bestimmter Objekte an. Windows PowerShell bietet es sich um eine "angepasst" Ansicht von mehreren bestimmten Objekttypen.

- Hinzufügen von Mitgliedern zu vorhandenen Objekten ein.

- Serialisiert Objekte zugreifen.

- Schreiben benutzerdefinierter Objekte.

  Mit ETS, können Sie erstellen neue flexible "Typen", die mit der Windows PowerShell-Sprache kompatibel sind. Wenn Sie eine .NET Entwickler sind, Sie können zum Arbeiten mit Objekten, die mit der Semantik wie die Windows PowerShell-Sprache mit dem Skripting, z. B. angewendet wird, um zu bestimmen, ob ein Objekt ergibt `true`.

  Weitere Informationen zu ETS und wie Windows PowerShell Objekte verwendet, finden Sie unter [Konzepte von Windows PowerShell-Objekt](http://msdn.microsoft.com/en-us/12700631-be23-4e6b-9bf0-81ea0d166353).

## <a name="programming-for-windows-powershell"></a>Programmieren für Windows PowerShell

Windows PowerShell definiert den Code für Befehle, Anbieter und andere programmmodule mithilfe von .NET Framework. Sie sind nicht für die Verwendung von Microsoft Visual Studio beschränkt erstellen Sie angepasste Module für Windows PowerShell, auch wenn die Beispiele in diesem Handbuch bekannt ist, dass in diesem Tool ausführen. Sie können jeder verwenden, die klassenvererbung und die Verwendung von Attributen unterstützt. In einigen Fällen-Windows PowerShell-APIs erfordern die Programmiersprache, um generische Typen zugreifen zu können.

## <a name="programmers-reference"></a>Referenz für Programmierer

Bei der Entwicklung für Windows PowerShell finden Sie unter den [Windows PowerShell SDK](../windows-powershell-reference.md).

## <a name="getting-started-using-windows-powershell"></a>Erste Schritte mit Windows PowerShell

Weitere Informationen zum Starten der Windows PowerShell-Befehlsshell verwenden, finden Sie die [erste Schritte mit Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) im Lieferumfang von Windows PowerShell. Eine Kurzübersicht dreifach-Dokument wird auch als Einführung zur Verwendung von Cmdlets bereitgestellt.

## <a name="contents-of-this-guide"></a>Inhalt dieses Handbuchs

|Thema|Definition|
|-----------|----------------|
|[Vorgehensweise: Erstellen einer Windows PowerShell-Anbieter](./how-to-create-a-windows-powershell-provider.md)|Dieser Abschnitt beschreibt, wie Sie einen Windows PowerShell-Anbieter für Windows PowerShell zu erstellen.|
|[Vorgehensweise: erstellen eine Windows PowerShell-Hostanwendung](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07)|In diesem Abschnitt wird beschrieben, wie eine hostanwendung schreiben, die einen Runspace bearbeitet und wie Sie eine hostanwendung schreiben, die einen eigenen benutzerdefinierten Host implementiert.|
|[Vorgehensweise: Erstellen Sie ein Windows PowerShell-Snap-in](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|In diesem Abschnitt wird beschrieben, wie ein Snap-In zu erstellen, die verwendet wird, um alle Cmdlets und Anbieter in einer Assembly zu registrieren und wie Sie eine benutzerdefinierte-Snap-in erstellen.|
|[Vorgehensweise: Erstellen Sie eine Konsole-Shell](./how-to-create-a-console-shell.md)|Dieser Abschnitt beschreibt, wie Sie eine Konsole Shell erstellen, die nicht erweiterbar ist.|
|[Windows PowerShell-Konzepten](./windows-powershell-concepts.md)|Dieser Abschnitt enthält konzeptionelle Informationen, mit denen Sie die Windows PowerShell vom Standpunkt eines Entwicklers zu verstehen.|

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell SDK](../windows-powershell-reference.md)