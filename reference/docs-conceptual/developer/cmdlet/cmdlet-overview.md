---
title: Cmdlet-Übersicht | Microsoft-Dokumentation
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365889"
---
# <a name="cmdlet-overview"></a>Cmdlet-Übersicht

Ein Cmdlet ist ein Lightweight-Befehl, der in der Windows PowerShell-Umgebung verwendet wird. Die Windows PowerShell-Laufzeit ruft diese Cmdlets im Kontext von Automatisierungs Skripts auf, die in der Befehlszeile bereitgestellt werden. Windows PowerShell Runtime ruft diese auch Programm gesteuert über Windows PowerShell-APIs auf.

## <a name="cmdlets"></a>Cmdlets

-Cmdlets führen eine Aktion aus und geben in der Regel ein Microsoft .NET Framework-Objekt an den nächsten Befehl in der Pipeline zurück. Zum Schreiben eines Cmdlets müssen Sie eine Cmdlet-Klasse implementieren, die von einer von zwei spezialisierten Cmdlet-Basisklassen abgeleitet ist. Die abgeleitete Klasse muss Folgendes ausführen:

- Deklarieren Sie ein Attribut, das die abgeleitete Klasse als Cmdlet bezeichnet.

- Definieren Sie öffentliche Eigenschaften, die mit Attributen versehen sind, die die öffentlichen Eigenschaften als Cmdlet-Parameter identifizieren.

- Überschreiben Sie mindestens eine der Eingabe Verarbeitungsmethoden, um Datensätze zu verarbeiten.

Sie können die Assembly, die die Klasse enthält, direkt mithilfe des [Import-Module](/powershell/module/microsoft.powershell.core/import-module) -Cmdlets laden, oder Sie können eine Host Anwendung erstellen, die die Assembly mithilfe der [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -API lädt. Beide Methoden bieten programmgesteuerten und Befehlszeilen Zugriff auf die Funktionalität des Cmdlets.

## <a name="cmdlet-terms"></a>Cmdlet-Begriffe

Die folgenden Begriffe werden in der Windows PowerShell-Cmdlet-Dokumentation häufig verwendet:

### <a name="cmdlet-attribute"></a>Cmdlet-Attribut

Ein .NET Framework Attribut, das verwendet wird, um eine Cmdlet-Klasse als Cmdlet zu deklarieren.
Obwohl PowerShell mehrere andere Attribute verwendet, die optional sind, ist das Cmdlet-Attribut erforderlich.
Weitere Informationen zu diesem Attribut finden Sie unter [Cmdlet-Attribut Deklaration](cmdlet-attribute-declaration.md).

### <a name="cmdlet-parameter"></a>Cmdlet-Parameter

Die öffentlichen Eigenschaften, die die Parameter definieren, die für den Benutzer oder die Anwendung verfügbar sind, die das Cmdlet ausführen.
Cmdlets können über erforderliche, benannte, positionelle und *Switch* -Parameter verfügen.
Mit Switch-Parametern können Sie Parameter definieren, die nur ausgewertet werden, wenn die Parameter im-Befehl angegeben werden.
Weitere Informationen zu den verschiedenen Typen von Parametern finden [Sie unter Cmdlet-Parameter](cmdlet-parameters.md).

### <a name="parameter-set"></a>Parameter Satz

Gruppe von Parametern, die im selben Befehl verwendet werden kann, um eine bestimmte Aktion auszuführen.
Ein Cmdlet kann über mehrere Parametersätze verfügen, aber jeder Parametersatz muss mindestens einen eindeutigen Parameter aufweisen.
Ein guter Cmdlet-Entwurf deutet nachdrücklich darauf hin, dass der Unique-Parameter auch ein erforderlicher Parameter ist.
Weitere Informationen zu Parametersätzen finden Sie unter [Cmdlet-Parametersätze](cmdlet-parameter-sets.md).

### <a name="dynamic-parameter"></a>Dynamischer Parameter

Ein Parameter, der zur Laufzeit zum Cmdlet hinzugefügt wird.
Normalerweise werden die dynamischen Parameter zum Cmdlet hinzugefügt, wenn ein anderer Parameter auf einen bestimmten Wert festgelegt ist.
Weitere Informationen zu dynamischen Parametern finden [Sie unter Cmdlet Dynamic Parameters](cmdlet-dynamic-parameters.md).

### <a name="input-processing-method"></a>Eingabe Verarbeitungsmethode

Methode, die ein Cmdlet verwenden kann, um die Datensätze, die es empfängt, als Eingabe zu nutzen.
Die Eingabe Verarbeitungsmethoden umfassen die [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -Methode, die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode, die [ System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode und die [System. Management. Automation. Cmdlet. StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) -Methode. Wenn Sie ein Cmdlet implementieren, müssen Sie mindestens einen der [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)-, [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)-und [ System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methoden.
In der Regel ist die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode die Methode, die Sie überschreiben, da Sie für jeden Datensatz aufgerufen wird, den das Cmdlet verarbeitet.
Im Gegensatz dazu werden die [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -Methode und die [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode einmal aufgerufen, um die Datensätze vorab zu verarbeiten oder nachzuverarbeiten.
Weitere Informationen zu diesen Methoden finden Sie unter [Input processing Methods](cmdlet-input-processing-methods.md).

### <a name="shouldprocess-feature"></a>"Schuldprocess"-Funktion

PowerShell ermöglicht es Ihnen, Cmdlets zu erstellen, die den Benutzer zur Eingabe eines Feedbacks auffordern, bevor das Cmdlet eine Änderung am System vornimmt.
Um dieses Feature verwenden zu können, muss das Cmdlet deklarieren, dass es die "schuldprocess"-Funktion unterstützt, wenn Sie das Cmdlet-Attribut deklarieren, und das Cmdlet muss " [System. Management. Automation. Cmdlet. rudprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) " und [" System. Management. Automation. Cmdlet. dendcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Methoden aus einer Eingabe Verarbeitungsmethode.
Weitere Informationen zur Unterstützung der-Funktion zur Unterstützung der-Funktion finden Sie unter [Anfordern einer Bestätigung](requesting-confirmation-from-cmdlets.md).

### <a name="transaction"></a>Transaktion

Eine logische Gruppe von Befehlen, die als einzelne Aufgabe behandelt werden.
Der Task schlägt automatisch fehl, wenn ein Befehl in der Gruppe fehlschlägt, und der Benutzer hat die Möglichkeit, die in der Transaktion durchgeführten Aktionen anzunehmen oder abzulehnen.
Um an einer Transaktion teilnehmen zu können, muss das Cmdlet deklarieren, dass es Transaktionen unterstützt, wenn das Cmdlet-Attribut deklariert wird.
Unterstützung für Transaktionen wurde in Windows PowerShell 2,0 eingeführt.
Weitere Informationen zu Transaktionen finden [Sie unter How to Support Transactions](how-to-support-transactions.md).

## <a name="how-cmdlets-differ-from-commands"></a>Unterschiede zwischen Cmdlets und Befehlen

Cmdlets unterscheiden sich von Befehlen in anderen befehlsshellumgebungen auf folgende Weise:

- Cmdlets sind Instanzen von .NET Framework Klassen; Sie sind keine eigenständigen ausführbaren Dateien.

- Cmdlets können aus nur wenigen Codezeilen erstellt werden.

- Cmdlets führen in der Regel keine eigene Formatierung, Fehlerdarstellung oder Ausgabe Formatierung durch. Die Formatierung, die Fehlerdarstellung und die Ausgabe Formatierung werden von der Windows PowerShell-Laufzeit verarbeitet.

- -Cmdlets verarbeiten Eingabe Objekte aus der Pipeline und nicht aus Text strömen, und Cmdlets liefern in der Regel Objekte als Ausgabe an die Pipeline.

- Cmdlets sind Daten Satz orientiert, da Sie jeweils ein einzelnes Objekt verarbeiten.

## <a name="cmdlet-base-classes"></a>Cmdlet-Basisklassen

Windows PowerShell unterstützt Cmdlets, die von den folgenden zwei Basisklassen abgeleitet werden.

- Die meisten Cmdlets basieren auf .NET Framework Klassen, die von der [System. Management. Automation. Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) -Basisklasse abgeleitet werden. Durch Ableiten von dieser Klasse kann ein Cmdlet den minimalen Satz von Abhängigkeiten in der Windows PowerShell-Laufzeit verwenden. Dies hat zwei Vorteile: Der erste Vorteil besteht darin, dass die Cmdlet-Objekte kleiner sind, und Sie sind weniger wahrscheinlich von Änderungen an der Windows PowerShell-Laufzeit betroffen. Der zweite Vorteil besteht darin, dass Sie bei Bedarf direkt eine Instanz des Cmdlet-Objekts erstellen und dann direkt aufrufen können, anstatt Sie über die Windows PowerShell-Laufzeit aufzurufen.

- Die komplexeren Cmdlets basieren auf .NET Framework Klassen, die von der [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) -Basisklasse abgeleitet werden. Das Ableiten von dieser Klasse gewährt Ihnen viel mehr Zugriff auf die Windows PowerShell-Laufzeit. Dieser Zugriff ermöglicht es dem Cmdlet, Skripts aufzurufen, auf Anbieter zuzugreifen und auf den aktuellen Sitzungszustand zuzugreifen. (Um auf den aktuellen Sitzungszustand zuzugreifen, können Sie Sitzungsvariablen und-Einstellungen abrufen und festlegen.) Das Ableiten von dieser Klasse erhöht jedoch die Größe des Cmdlet-Objekts und bedeutet, dass Ihr Cmdlet enger an die aktuelle Version der Windows PowerShell-Laufzeit gekoppelt ist.

Wenn Sie den erweiterten Zugriff auf die Windows PowerShell-Runtime nicht benötigen, sollten Sie im Allgemeinen von der [System. Management. Automation. Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) -Klasse ableiten. Die Windows PowerShell-Laufzeit verfügt jedoch über umfangreiche Protokollierungsfunktionen für die Ausführung von Cmdlets. Wenn das Überwachungsmodell von dieser Protokollierung abhängt, können Sie die Ausführung Ihres Cmdlets in einem anderen Cmdlet verhindern, indem Sie von der [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) -Klasse ableiten.

## <a name="input-processing-methods"></a>Eingabe Verarbeitungsmethoden

Die [System. Management. Automation. Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) -Klasse stellt die folgenden virtuellen Methoden bereit, die zum Verarbeiten von Datensätzen verwendet werden. Alle abgeleiteten Cmdlet-Klassen müssen eine oder mehrere der ersten drei Methoden überschreiben:

- [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): wird verwendet, um optionale einmalige Vorverarbeitungs Funktionen für das Cmdlet bereitzustellen.

- [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): dient zum Bereitstellen von Daten Satz basierter Verarbeitungs Funktionalität für das Cmdlet. Die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode kann je nach Eingabe des Cmdlets beliebig oft oder gar nicht aufgerufen werden.

- [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): dient zur Bereitstellung optionaler, nachträglich verarbeitender Funktionen für das Cmdlet.

- [System. Management. Automation. Cmdlet. StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): wird verwendet, um die Verarbeitung zu beenden, wenn der Benutzer das Cmdlet asynchron beendet (z. b. durch Drücken von STRG + C).

Weitere Informationen zu diesen Methoden finden Sie unter [Cmdlet Input processing Methods](./cmdlet-input-processing-methods.md).

## <a name="cmdlet-attributes"></a>Cmdlet-Attribute

Windows PowerShell definiert mehrere .NET Framework Attribute, die zum Verwalten von Cmdlets verwendet werden, und um allgemeine Funktionen anzugeben, die von Windows PowerShell bereitgestellt werden und die möglicherweise vom Cmdlet benötigt werden. Attribute werden z. b. verwendet, um eine Klasse als Cmdlet festzulegen, um die Parameter des Cmdlets anzugeben und um die Validierung von Eingaben anzufordern, damit Cmdlet-Entwickler diese Funktionalität nicht in Ihrem Cmdlet-Code implementieren müssen. Weitere Informationen zu Attributen finden Sie unter [Windows PowerShell-Attribute](./cmdlet-attributes.md).

## <a name="cmdlet-names"></a>Cmdlet-Namen

Windows PowerShell verwendet ein Verb-und-Substantiv-namens Paar, um Cmdlets zu benennen. Das in Windows PowerShell enthaltene Cmdlet "`Get-Command`" wird beispielsweise verwendet, um alle Cmdlets zu erhalten, die in der Befehlsshell registriert sind. Das Verb gibt die Aktion an, die das Cmdlet ausführt, und das Substantiv identifiziert die Ressource, auf der das Cmdlet seine Aktion ausführt.

Diese Namen werden angegeben, wenn die .NET Framework-Klasse als Cmdlet deklariert wird. Weitere Informationen zum Deklarieren einer .NET Framework Klasse als Cmdlet finden [Sie unter Cmdlet-Attribut Deklaration](./cmdlet-class-declaration.md).

## <a name="writing-cmdlet-code"></a>Schreiben von Cmdlet-Code

Dieses Dokument bietet zwei Möglichkeiten, um zu ermitteln, wie der Cmdlet-Code geschrieben wird. Wenn Sie den Code ohne großen Erläuterung anzeigen möchten, finden Sie weitere Informationen unter [Beispiele für Cmdlet-Code](./examples-of-cmdlet-code.md). Weitere Erläuterungen zum Code finden Sie in den Themen zum [getproc-Tutorial](./getproc-tutorial.md), zum [stopproc-Tutorial](./stopproc-tutorial.md)oder zum [selectstr-Tutorial](./selectstr-tutorial.md) .

Weitere Informationen zu den Richtlinien zum Schreiben von Cmdlets finden [Sie unter Cmdlet-Entwicklungs Richtlinien](./cmdlet-development-guidelines.md).

## <a name="see-also"></a>Weitere Informationen

[Konzepte von Windows PowerShell-Cmdlets](./windows-powershell-cmdlet-concepts.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
