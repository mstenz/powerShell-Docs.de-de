---
title: Übersicht über Cmdlets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK]
- cmdlets [PowerShell SDK], described
ms.assetid: 0aa32589-4447-4ead-a5dd-a3be99113140
caps.latest.revision: 21
ms.openlocfilehash: 14200aed2fb94c37c8b8af29650f602945e7ac1c
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229367"
---
# <a name="cmdlet-overview"></a>Cmdlet-Übersicht

Ein Cmdlet ist ein einfacher Befehl, der in der Windows PowerShell-Umgebung verwendet wird. Die Windows PowerShell-Laufzeit ruft diese Cmdlets im Kontext des Automation-Skripts, die in der Befehlszeile bereitgestellt werden. Die Windows PowerShell-Laufzeit ruft auch diese programmgesteuert über Windows PowerShell-APIs.

## <a name="cmdlets"></a>Cmdlets

-Cmdlets eine Aktion ausführen und in der Regel ein Microsoft .NET Framework-Objekt an den nächsten Befehl in der Pipeline zurückgeben. Um ein Cmdlet zu schreiben, müssen Sie eine Cmdlet-Klasse implementieren, die von einem der zwei spezielle Cmdlet Basisklassen abgeleitet wird. Die abgeleitete Klasse muss:

- Deklarieren Sie ein Attribut, das die abgeleitete Klasse als Cmdlet identifiziert.

- Definieren Sie öffentliche Eigenschaften, die mit Attributen versehen sind, die die öffentlichen Eigenschaften als Cmdlet-Parameter zu identifizieren.

- Überschreiben Sie mindestens eine der eingabeverarbeitungsmethoden zum Verarbeiten von Datensätzen.

Sie können die Assembly mit der Klasse direkt mithilfe der laden die [Import-Module](/powershell/module/microsoft.powershell.core/import-module) -Cmdlet, oder Sie können eine hostanwendung, die die Assembly mit lädt erstellen die [ System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API. Beide Methoden bieten programmgesteuerten und Befehlszeilentools Zugriff auf die Funktionalität des Cmdlets.

## <a name="cmdlet-terms"></a>Cmdlet-Begriffe

Die folgenden Begriffe werden häufig in der Dokumentation zu Windows PowerShell-Cmdlet verwendet:

### <a name="cmdlet-attribute"></a>Cmdlet-Attribut

Ein .NET Framework-Attribut, das verwendet wird, um eine Cmdlet-Klasse als ein Cmdlet zu deklarieren.
Obwohl es sich bei PowerShell mehreren anderen Attributen verwendet, die optional sind, ist die Cmdlet-Attribut erforderlich.
Weitere Informationen zu diesem Attribut finden Sie unter [Cmdlet Attributdeklaration](cmdlet-attribute-declaration.md).

### <a name="cmdlet-parameter"></a>Cmdlet-Parameter

Die öffentlichen Eigenschaften, die die Parameter definieren, die für den Benutzer oder die Anwendung zur Verfügung stehen, mit dem-Cmdlet ausgeführt wird.
Cmdlets können über die erforderlichen, benannte, mit Feldern fester Breite, und *wechseln* Parameter.
Switch-Parameter können Sie Parameter definieren, die ausgewertet werden, nur dann, wenn der Parameter im Aufruf angegeben werden.
Weitere Informationen zu den verschiedenen Typen von Parametern finden Sie unter [Cmdletparameter](cmdlet-parameters.md).

### <a name="parameter-set"></a>Parametersatz

Gruppe von Parametern, die im selben Befehl verwendet werden kann, um eine bestimmte Aktion auszuführen.
Ein Cmdlet kann über mehrere Parametersätze verfügen, aber jeder Parametersatz müssen mindestens einen Parameter, der eindeutig ist.
Gute Cmdlet-Entwurf empfiehlt nachdrücklich, dass die unique-Parameter auch ein erforderlicher Parameter.
Weitere Informationen zu Parametersätze, finden Sie unter [Cmdlet Parametersätze](cmdlet-parameter-sets.md).

### <a name="dynamic-parameter"></a>Dynamischer parameter

Ein Parameter, der an das Cmdlet zur Laufzeit hinzugefügt wird.
In der Regel werden die dynamischen Parameter an das Cmdlet hinzugefügt, wenn ein anderer Parameter auf einen bestimmten Wert festgelegt ist.
Weitere Informationen zu dynamischen Parametern finden Sie unter [dynamische Cmdletparameter](cmdlet-dynamic-parameters.md).

### <a name="input-processing-method"></a>Eingabeverarbeitungsmethode

Methode, die ein Cmdlet verwenden kann, um die Datensätze, die es empfängt, als Eingabe zu nutzen.
Die eingabeverarbeitungsmethoden sind die [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -Methode, die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode, die [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode, und die [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) Methode. Wenn Sie ein Cmdlet implementieren, müssen Sie mindestens eine der überschreiben die [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), und [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Methoden.
In der Regel die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode ist die Methode, die Sie überschreiben, da sie für jeden Datensatz aufgerufen wird, die mit dem-Cmdlet verarbeitet.
Im Gegensatz dazu die [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) Methode und die [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Methode einmal aufgerufen werden, ausführen vorverarbeitung oder nach der Verarbeitung der Datensätze.
Weitere Informationen zu diesen Methoden finden Sie unter [Eingabe verarbeiten Methoden](cmdlet-input-processing-methods.md).

### <a name="shouldprocess-feature"></a>ShouldProcess-Funktion

PowerShell ermöglicht Ihnen die Erstellung von Cmdlets, die der Benutzer Feedback aufgefordert werden, bevor das Cmdlet eine Änderung an das System ausführt.
Um dieses Feature verwenden zu können, muss das-Cmdlet, dass sie die ShouldProcess-Funktion unterstützt, wenn Sie das Cmdlet-Attribut deklarieren, und mit dem-Cmdlet aufrufen muss, deklariert die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) und [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methoden eine Eingabe, die Verarbeitungsmethode aus.
Weitere Informationen dazu, wie Sie die ShouldProcess-Funktionen unterstützen, finden Sie unter [Bestätigung anfordern](requesting-confirmation-from-cmdlets.md).

### <a name="transaction"></a>Transaction

Eine logische Gruppe von Befehlen, die als eine einzelne Aufgabe behandelt werden.
Die Aufgabe schlägt automatisch einen beliebigen Befehl in der Gruppe ein Fehler auftritt, und der Benutzer hat die Möglichkeit, annehmen oder ablehnen von Aktionen innerhalb der Transaktion ausgeführt.
In einer Transaktion beteiligt sein soll, muss das-Cmdlet deklariert werden, dass sie Transaktionen unterstützt, wenn das Cmdlet-Attribut deklariert wird.
Unterstützung für Transaktionen wurde in Windows PowerShell 2.0 eingeführt.
Weitere Informationen über Transaktionen finden Sie unter [wie unterstützen Transaktionen](how-to-support-transactions.md).

## <a name="how-cmdlets-differ-from-commands"></a>Wie unterscheiden sich Cmdlets von Befehlen

Cmdlets unterscheiden sich von Befehlen in anderen Umgebungen Befehl-Shell die folgenden Möglichkeiten:

- Cmdlets sind Instanzen von .NET Framework-Klassen. Es sind keine eigenständigen ausführbaren Dateien.

- Cmdlets können von weniger als ein Dutzend Zeilen von Code erstellt werden.

- Cmdlets sind im Allgemeinen keine eigene Analyse, Präsentation für Fehler, oder die Formatierung der Ausgabe. Analyse, Präsentation für Fehler und Formatierung der Ausgabe werden von der Windows PowerShell-Laufzeit behandelt.

- Vorgang von Cmdlets geben Objekte aus der Pipeline, anstatt von Streams von Text, und übermitteln Cmdlets die Objekte in der Regel als Ausgabe an die Pipeline.

- -Cmdlets sind datensatzorientierten, da sie ein einzelnes Objekt gleichzeitig verarbeiten.

## <a name="cmdlet-base-classes"></a>Basisklassen-Cmdlet

Windows PowerShell unterstützt Cmdlets, die von den folgenden zwei Basisklassen abgeleitet werden.

- Die meisten Cmdlets basieren auf .NET Framework-Klassen, die Ableiten der [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) Basisklasse. Ableiten von dieser Klasse können ein Cmdlet aus, um den minimalen Satz von Abhängigkeiten für die Windows PowerShell-Laufzeit verwenden. Dies hat zwei Vorteile. Der erste Vorteil ist, dass die Cmdlet-Objekte kleiner sind, und Sie werden mit geringerer Wahrscheinlichkeit von Änderungen an der Windows PowerShell-Laufzeit betroffen sind. Der zweite Vorteil ist, wenn Sie zu verwenden, können Sie direkt zu eine Instanz des Objekts Cmdlet erstellen und dann so aufrufen, direkt aufrufen, anstatt ihn über die Windows PowerShell-Laufzeit.

- Die komplexere Cmdlets basieren auf .NET Framework-Klassen, die von abgeleitet der [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) Basisklasse. Ableiten von dieser Klasse erhalten Sie wesentlich mehr Zugriff auf die Windows PowerShell-Laufzeit. Dieser Zugriff ermöglicht es, Ihre Cmdlets aufrufen, Skripts, die zum Zugreifen auf Anbieter, und klicken Sie auf dem aktuellen Sitzungsstatus. (Der aktuelle Sitzungszustand für den Zugriff auf Sie Get- und set Sitzungsvariablen und die Einstellungen.) Allerdings von dieser Klasse ableiten, erhöht die Größe des Cmdlet-Objekts, und dies bedeutet, dass Ihr Cmdlet enger an die aktuelle Version der Windows PowerShell-Laufzeit gekoppelt ist.

Im Allgemeinen, es sei denn, Sie den erweiterten Zugriff auf die Windows PowerShell-Laufzeit benötigen, sollten Sie die Ableitung von der [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) Klasse. Allerdings muss die Windows PowerShell-Laufzeit umfassende Protokollierungsfunktionen für die Ausführung des Cmdlets. Wenn Ihr Modell Überwachung diese Protokollierung abhängig ist, können Sie die Ausführung Ihres Cmdlets aus, in ein anderes Cmdlet verhindern, durch Ableiten von der [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) Klasse.

## <a name="input-processing-methods"></a>Eingabeverarbeitungsmethoden

Die [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) -Klasse bietet die folgenden virtuellen Methoden, die verwendet werden, um Datensätze zu verarbeiten. Alle abgeleiteten Cmdlet-Klassen müssen mindestens eine der ersten drei Methoden überschreiben:

- [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): Verwendet das Cmdlet optionale Funktionen für einmalige, vorverarbeitung bereit.

- [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): Zum Bereitstellen von Datensätzen Verarbeitungsfunktion für das Cmdlet verwendet. Die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode kann beliebig oft oder überhaupt nicht abhängig von der Eingabe des-Cmdlets aufgerufen werden.

- [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): Verwendet das Cmdlet optionale Nachbearbeitung einmalige Funktionen bereit.

- [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): Zum Beenden der Verarbeitung, wenn der Benutzer das Cmdlet asynchron beendet wird (z. B. durch Drücken von STRG + C) verwendet.

Weitere Informationen zu diesen Methoden finden Sie unter [Cmdlet Eingabe verarbeiten Methoden](./cmdlet-input-processing-methods.md).

## <a name="cmdlet-attributes"></a>Cmdlet-Attribute

Windows PowerShell definiert mehrere .NET Framework-Attribute, die verwendet werden, um Cmdlets zu verwalten und allgemeine Funktionen, die von Windows PowerShell bereitgestellt wird, und, vorgeschrieben werden vom Cmdlet, angeben. Beispielsweise werden Attribute zum Definieren einer Klasse als ein Cmdlet, das zum Angeben der Parameter des Cmdlets und die Überprüfung der Eingabe anfordern, so dass die Cmdlet-Entwickler nicht verfügen, um diese Funktionalität in ihrem Cmdlet-Code zu implementieren. Weitere Informationen zu Attributen finden Sie unter [Windows PowerShell-Attribute](./cmdlet-attributes.md).

## <a name="cmdlet-names"></a>Cmdlet-Namen

Windows PowerShell verwendet ein Verb-Nomen-Name-Paar für Name-Cmdlets. Z. B. die `Get-Command` in Windows PowerShell enthaltenen Cmdlets verwendet, um alle Cmdlets abzurufen, die in der Befehlsshell registriert sind. Das Verb identifiziert, die Aktion, die das-Cmdlet führt, und das Nomen identifiziert die Ressource, die auf der das Cmdlet die zugehörige Aktion ausführt.

Diese Namen angegeben sind, wenn .NET Framework-Klasse als ein Cmdlet deklariert wird. Weitere Informationen dazu, wie Sie eine .NET Framework-Klasse als Cmdlet zu deklarieren, finden Sie unter [Cmdlet Attributdeklaration](./cmdlet-class-declaration.md).

## <a name="writing-cmdlet-code"></a>Schreiben von Cmdlet-Code

Dieses Dokument bietet zwei Möglichkeiten, um zu ermitteln, wie die Cmdlet-Code geschrieben wird. Wenn Sie den Code nicht weiter erläutert anzeigen möchten, finden Sie unter [Beispiele der Cmdlet-Code](./examples-of-cmdlet-code.md). Wenn Sie weitere erläuterungen zum Code bevorzugen, finden Sie unter den [GetProc Tutorial](./getproc-tutorial.md), [StopProc Tutorial](./stopproc-tutorial.md), oder [SelectStr Tutorial](./selectstr-tutorial.md) Themen.

Weitere Informationen zu den Richtlinien für das Schreiben von Cmdlets, finden Sie unter [Cmdlet-Entwicklungsrichtlinien](./cmdlet-development-guidelines.md).

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell-Cmdlet-Konzepte](./windows-powershell-cmdlet-concepts.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
