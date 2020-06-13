---
title: Cmdlet-Übersicht
ms.date: 06/11/2020
ms.topic: article
ms.openlocfilehash: e179bf371c26781cf1c8db641c46c0329036c8ea
ms.sourcegitcommit: 56463fb628a7d83dec4364e89417d83316c3e53b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2020
ms.locfileid: "84722829"
---
# <a name="cmdlet-overview"></a>Cmdlet-Übersicht

Ein Cmdlet ist ein Lightweight-Befehl, der in der PowerShell-Umgebung verwendet wird. Die PowerShell-Laufzeit ruft diese Cmdlets im Kontext von Automatisierungs Skripts auf, die in der Befehlszeile bereitgestellt werden. Die PowerShell-Laufzeit ruft Sie auch Programm gesteuert über PowerShell-APIs auf.

## <a name="cmdlets"></a>Cmdlets

-Cmdlets führen eine Aktion aus und geben in der Regel ein Microsoft .NET Objekt an den nächsten Befehl in der Pipeline zurück. Ein Cmdlet ist ein einzelner Befehl, der an der Pipeline Semantik von PowerShell beteiligt ist.
Dies schließt binäre Cmdlets (c#), erweiterte Skriptfunktionen, cdxml und Workflows ein.

In dieser SDK-Dokumentation wird beschrieben, wie in c# geschriebene binäre Cmdlets erstellt werden. Informationen zu skriptbasierten Cmdlets finden Sie unter:

- [about_Functions_Advanced](/powershell/module/microsoft.powershell.core/about/about_functions_advanced)
- [about_Functions_CmdletBindingAttribute](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute)
- [about_Functions_Advanced_Methods](/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods)

Um ein binäres Cmdlet zu erstellen, müssen Sie eine Cmdlet-Klasse implementieren, die von einer von zwei spezialisierten Cmdlet-Basisklassen abgeleitet ist. Die abgeleitete Klasse muss Folgendes ausführen:

- Deklarieren Sie ein Attribut, das die abgeleitete Klasse als Cmdlet bezeichnet.
- Definieren Sie öffentliche Eigenschaften, die mit Attributen versehen sind, die die öffentlichen Eigenschaften als Cmdlet-Parameter identifizieren.
- Überschreiben Sie mindestens eine der Eingabe Verarbeitungsmethoden, um Datensätze zu verarbeiten.

Sie können die Assembly, die die Klasse enthält, direkt mithilfe des [Import-Module](/powershell/module/microsoft.powershell.core/import-module) -Cmdlets laden, oder Sie können eine Host Anwendung erstellen, die die Assembly mithilfe der [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -API lädt. Beide Methoden bieten programmgesteuerten und Befehlszeilen Zugriff auf die Funktionalität des Cmdlets.

## <a name="cmdlet-terms"></a>Cmdlet-Begriffe

Die folgenden Begriffe werden in der PowerShell-Cmdlet-Dokumentation häufig verwendet:

### <a name="cmdlet-attribute"></a>Cmdlet-Attribut

Ein .NET-Attribut, das verwendet wird, um eine Cmdlet-Klasse als Cmdlet zu deklarieren. Obwohl PowerShell mehrere andere Attribute verwendet, die optional sind, ist das Cmdlet-Attribut erforderlich. Weitere Informationen zu diesem Attribut finden Sie unter [Cmdlet-Attribut Deklaration](cmdlet-attribute-declaration.md).

### <a name="cmdlet-parameter"></a>Cmdlet-Parameter

Die öffentlichen Eigenschaften, die die Parameter definieren, die für den Benutzer oder die Anwendung verfügbar sind, die das Cmdlet ausführen. Cmdlets können über erforderliche, benannte, positionelle und *Switch* -Parameter verfügen. Mit Switch-Parametern können Sie Parameter definieren, die nur ausgewertet werden, wenn die Parameter im-Befehl angegeben werden. Weitere Informationen zu den verschiedenen Typen von Parametern finden [Sie unter Cmdlet-Parameter](cmdlet-parameters.md).

### <a name="parameter-set"></a>Parametersatz

Gruppe von Parametern, die im selben Befehl verwendet werden kann, um eine bestimmte Aktion auszuführen. Ein Cmdlet kann über mehrere Parametersätze verfügen, aber jeder Parametersatz muss mindestens einen eindeutigen Parameter aufweisen. Ein guter Cmdlet-Entwurf deutet nachdrücklich darauf hin, dass der Unique-Parameter auch ein erforderlicher Parameter ist.
Weitere Informationen zu Parametersätzen finden Sie unter [Cmdlet-Parametersätze](cmdlet-parameter-sets.md).

### <a name="dynamic-parameter"></a>Dynamischer Parameter

Ein Parameter, der zur Laufzeit zum Cmdlet hinzugefügt wird. Normalerweise werden die dynamischen Parameter zum Cmdlet hinzugefügt, wenn ein anderer Parameter auf einen bestimmten Wert festgelegt ist. Weitere Informationen zu dynamischen Parametern finden [Sie unter Cmdlet Dynamic Parameters](cmdlet-dynamic-parameters.md).

### <a name="input-processing-methods"></a>Eingabe Verarbeitungsmethoden

Die [System. Management. Automation. Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) -Klasse stellt die folgenden virtuellen Methoden bereit, die zum Verarbeiten von Datensätzen verwendet werden. Alle abgeleiteten Cmdlet-Klassen müssen eine oder mehrere der ersten drei Methoden überschreiben:

- [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): wird verwendet, um optionale einmalige Vorverarbeitungs Funktionen für das Cmdlet bereitzustellen.
- [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): dient zum Bereitstellen von Daten Satz basierter Verarbeitungs Funktionalität für das Cmdlet. Die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode kann je nach Eingabe des Cmdlets beliebig oft oder gar nicht aufgerufen werden.
- [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): dient zur Bereitstellung optionaler, nachträglich verarbeitender Funktionen für das Cmdlet.
- [System. Management. Automation. Cmdlet. StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): wird verwendet, um die Verarbeitung zu beenden, wenn der Benutzer das Cmdlet asynchron beendet (z. b. durch Drücken von <kbd>STRG</kbd> + <kbd>C</kbd>).

Weitere Informationen zu diesen Methoden finden Sie unter [Cmdlet Input processing Methods](./cmdlet-input-processing-methods.md).

Wenn Sie ein Cmdlet implementieren, müssen Sie mindestens eine dieser Eingabe Verarbeitungsmethoden überschreiben.
In der Regel ist **ProcessRecord ()** die Methode, die Sie überschreiben, da Sie für jeden Datensatz aufgerufen wird, den das Cmdlet verarbeitet. Im Gegensatz dazu werden die **BeginProcessing ()** -Methode und die **EndProcessing ()** -Methode einmal aufgerufen, um die Datensätze vor oder nach der Verarbeitung auszuführen. Weitere Informationen zu diesen Methoden finden Sie unter [Input processing Methods](cmdlet-input-processing-methods.md).

### <a name="shouldprocess-feature"></a>"Schuldprocess"-Funktion

PowerShell ermöglicht es Ihnen, Cmdlets zu erstellen, die den Benutzer zur Eingabe eines Feedbacks auffordern, bevor das Cmdlet eine Änderung am System vornimmt. Um dieses Feature verwenden zu können, muss das Cmdlet deklarieren, dass es das Feature unterstützt `ShouldProcess` , wenn Sie das Cmdlet-Attribut deklarieren, und das Cmdlet muss die Methoden " [System. Management. Automation. Cmdlet. Schulter dprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) " und " [System. Management. Automation. Cmdlet. undcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) " aus einer Eingabe Verarbeitungsmethode abrufen. Weitere Informationen zur Unterstützung der `ShouldProcess` Funktionalität finden Sie unter [Anfordern einer Bestätigung](requesting-confirmation-from-cmdlets.md).

### <a name="transaction"></a>Transaktion

Eine logische Gruppe von Befehlen, die als einzelne Aufgabe behandelt werden. Der Task schlägt automatisch fehl, wenn ein Befehl in der Gruppe fehlschlägt, und der Benutzer hat die Möglichkeit, die in der Transaktion durchgeführten Aktionen anzunehmen oder abzulehnen. Um an einer Transaktion teilnehmen zu können, muss das Cmdlet deklarieren, dass es Transaktionen unterstützt, wenn das Cmdlet-Attribut deklariert wird. Unterstützung für Transaktionen wurde in Windows PowerShell 2,0 eingeführt. Weitere Informationen zu Transaktionen finden [Sie unter How to Support Transactions](how-to-support-transactions.md).

## <a name="how-cmdlets-differ-from-commands"></a>Unterschiede zwischen Cmdlets und Befehlen

Cmdlets unterscheiden sich von Befehlen in anderen befehlsshellumgebungen auf folgende Weise:

- Cmdlets sind Instanzen von .NET-Klassen. Sie sind keine eigenständigen ausführbaren Dateien.
- Cmdlets können aus nur wenigen Codezeilen erstellt werden.
- Cmdlets führen in der Regel keine eigene Formatierung, Fehlerdarstellung oder Ausgabe Formatierung durch. Die Formatierung, die Fehlerdarstellung und die Ausgabe Formatierung werden von der PowerShell-Laufzeit behandelt.
- -Cmdlets verarbeiten Eingabe Objekte aus der Pipeline und nicht aus Text strömen, und Cmdlets liefern in der Regel Objekte als Ausgabe an die Pipeline.
- Cmdlets sind Daten Satz orientiert, da Sie jeweils ein einzelnes Objekt verarbeiten.

## <a name="cmdlet-base-classes"></a>Cmdlet-Basisklassen

Windows PowerShell unterstützt Cmdlets, die von den folgenden zwei Basisklassen abgeleitet werden.

- Die meisten Cmdlets basieren auf .NET-Klassen, die von der [System. Management. Automation. Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) -Basisklasse abgeleitet werden.
  Durch Ableiten von dieser Klasse kann ein Cmdlet den minimalen Satz von Abhängigkeiten in der Windows PowerShell-Laufzeit verwenden. Dies hat zwei Vorteile. Der erste Vorteil besteht darin, dass die Cmdlet-Objekte kleiner sind, und Sie sind weniger wahrscheinlich von Änderungen an der PowerShell-Laufzeit betroffen. Der zweite Vorteil besteht darin, dass Sie bei Bedarf direkt eine Instanz des Cmdlet-Objekts erstellen und dann direkt aufrufen können, anstatt Sie über die PowerShell-Laufzeit aufzurufen.

- Die komplexeren Cmdlets basieren auf .NET-Klassen, die von der [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) -Basisklasse abgeleitet werden. Das Ableiten von dieser Klasse gewährt Ihnen viel mehr Zugriff auf die PowerShell-Laufzeit. Dieser Zugriff ermöglicht es dem Cmdlet, Skripts aufzurufen, auf Anbieter zuzugreifen und auf den aktuellen Sitzungszustand zuzugreifen.
  (Um auf den aktuellen Sitzungszustand zuzugreifen, können Sie Sitzungsvariablen und-Einstellungen abrufen und festlegen.) Das Ableiten von dieser Klasse erhöht jedoch die Größe des Cmdlet-Objekts und bedeutet, dass Ihr Cmdlet enger an die aktuelle Version der PowerShell-Laufzeit gekoppelt ist.

Wenn Sie den erweiterten Zugriff auf die PowerShell-Runtime nicht benötigen, sollten Sie im Allgemeinen von der [System. Management. Automation. Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) -Klasse ableiten.
Die PowerShell-Laufzeit verfügt jedoch über umfangreiche Protokollierungsfunktionen für die Ausführung von Cmdlets. Wenn das Überwachungsmodell von dieser Protokollierung abhängt, können Sie die Ausführung Ihres Cmdlets in einem anderen Cmdlet verhindern, indem Sie von der [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) -Klasse ableiten.

## <a name="cmdlet-attributes"></a>Cmdlet-Attribute

PowerShell definiert mehrere .NET-Attribute, die zum Verwalten von Cmdlets und zum Angeben allgemeiner Funktionen verwendet werden, die von PowerShell bereitgestellt werden und die möglicherweise vom Cmdlet benötigt werden. Attribute werden z. b. verwendet, um eine Klasse als Cmdlet festzulegen, um die Parameter des Cmdlets anzugeben und um die Validierung von Eingaben anzufordern, damit Cmdlet-Entwickler diese Funktionalität nicht in Ihrem Cmdlet-Code implementieren müssen. Weitere Informationen zu Attributen finden Sie unter [PowerShell-Attribute](./cmdlet-attributes.md).

## <a name="cmdlet-names"></a>Cmdlet-Namen

PowerShell verwendet ein Verb-und-Substantiv-namens Paar, um Cmdlets zu benennen. Beispielsweise wird das `Get-Command` in PowerShell enthaltene Cmdlet verwendet, um alle Cmdlets zu erhalten, die in der Befehlsshell registriert sind. Das Verb gibt die Aktion an, die das Cmdlet ausführt, und das Substantiv identifiziert die Ressource, auf der das Cmdlet seine Aktion ausführt.

Diese Namen werden angegeben, wenn die .NET-Klasse als Cmdlet deklariert wird. Weitere Informationen zum Deklarieren einer .NET-Klasse als Cmdlet finden Sie unter [Cmdlet-Attribut Deklaration](./cmdlet-class-declaration.md).

## <a name="writing-cmdlet-code"></a>Schreiben von Cmdlet-Code

Dieses Dokument bietet zwei Möglichkeiten, um zu ermitteln, wie der Cmdlet-Code geschrieben wird. Wenn Sie den Code ohne großen Erläuterung anzeigen möchten, finden Sie weitere Informationen unter [Beispiele für Cmdlet-Code](./examples-of-cmdlet-code.md). Weitere Erläuterungen zum Code finden Sie in den Themen zum [getproc-Tutorial](./getproc-tutorial.md), zum [stopproc-Tutorial](./stopproc-tutorial.md)oder zum [selectstr-Tutorial](./selectstr-tutorial.md) .

Weitere Informationen zu den Richtlinien zum Schreiben von Cmdlets finden [Sie unter Cmdlet-Entwicklungs Richtlinien](./cmdlet-development-guidelines.md).

## <a name="see-also"></a>Weitere Informationen

[Konzepte von PowerShell-Cmdlets](./windows-powershell-cmdlet-concepts.md)

[Schreiben eines PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[PowerShell SDK](../windows-powershell-reference.md)
