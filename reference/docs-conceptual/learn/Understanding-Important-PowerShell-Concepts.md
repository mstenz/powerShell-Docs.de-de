---
ms.date: 08/23/2018
keywords: powershell,cmdlet
title: Grundlegendes zu wichtigen PowerShell-Konzepten
ms.assetid: 3e601e38-4520-4578-a48d-b6779f1d35ee
ms.openlocfilehash: fad64563d1a7a6abd4f0e430331f81f91f43d312
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401145"
---
# <a name="understanding-important-powershell-concepts"></a>Grundlegendes zu wichtigen PowerShell-Konzepten

PowerShell integriert Konzepte aus vielen verschiedenen Umgebungen. Einige der Konzepte werden Benutzern vertraut sein, die Erfahrung im Umgang mit Shell- oder Programmierumgebungen besitzen. Allerdings werden nur wenige Benutzer sämtliche dieser Konzepte kennen. Ein Blick auf einige dieser Konzepte ermöglicht eine nützliche Übersicht über die Shell.

## <a name="output-is-object-based"></a>Die Ausgabe ist objektbasiert

Im Gegensatz zu herkömmlichen Befehlszeilenschnittstellen sind PowerShell-Cmdlets für den Umgang mit Objekten entworfen.
Ein Objekt setzt sich aus strukturierten Informationen zusammen und ist mehr als nur die Zeichenfolge, die auf dem Bildschirm erscheint. Die Befehlsausgabe umfasst immer zusätzliche Informationen, die Sie bei Bedarf nutzen können.

Wenn Sie in schon mal ein Textverarbeitungsprogramm zum Verarbeiten von Daten verwendet haben, werden Sie das abweichende Verhalten der Daten in PowerShell bemerken. In den meisten Fällen benötigen Sie kein Textverarbeitungsprogramm, um bestimmte Informationen zu extrahieren. Sie greifen mit der standardmäßigen PowerShell-Objektsyntax direkt auf Teile der Daten zu.

## <a name="the-command-family-is-extensible"></a>Die Befehlsfamilie ist erweiterbar

Schnittstellen wie **cmd.exe** bieten keine Möglichkeit zur direkten Erweiterung des integrierten Befehlssatzes. Sie können externe Befehlszeilentools erstellen, die in **cmd.exe** ausgeführt werden. Aber diese externen Tools umfassen keine Dienste wie z.B. eine integrierte Hilfe. **cmd.exe** weiß nicht automatisch, dass es sich bei diesen externen Tools um gültige Befehle handelt.

Die nativen Befehle in PowerShell werden als *Cmdlets* bezeichnet (ausgesprochen: Command-Lets). Mithilfe von kompiliertem Code oder Skripts können Sie eigene Cmdlet-Module und -Funktionen erstellen. Mit Modulen können der Shell Cmdlets und Anbieter hinzugefügt werden. PowerShell bietet außerdem Unterstützung für Skripts, analog zu UNIX-Shellskripts und **cmd.exe**-Batchdateien.

## <a name="powershell-handles-console-input-and-display"></a>PowerShell verarbeitet Konsoleneingabe und Anzeige

Wenn Sie einen Befehl eingeben, verarbeitet PowerShell die Befehlszeileneingabe immer sofort. PowerShell formatiert darüber hinaus die Ausgabe, die auf dem Bildschirm angezeigt wird. Dieser Unterschied ist wesentlich, weil dadurch die Arbeit für jedes Cmdlet verringert wird. Es wird sichergestellt, dass Sie Aufgaben mit beliebigen Cmdlets immer gleich ausführen können. Cmdlet-Entwickler müssen keinen Code schreiben, mit dem die Befehlszeilenargumente analysiert oder die Ausgabe formatiert wird.

Herkömmliche Befehlszeilentools haben eigene Schemas zum Anfordern und Anzeigen von Hilfe. Bei einigen Befehlszeilentools muss **/?** eingegeben werden, um die Anzeige von Hilfe auszulösen. Bei anderen muss **-?**, **/H** oder gar **//** eingegeben werden. Bei einigen wird Hilfe in einem Fenster auf der grafischen Benutzeroberfläche und nicht in der Konsole angezeigt. Wenn Sie den falschen Parameter verwenden, ignoriert das Tool möglicherweise Ihre Eingabe und beginnt damit, automatisch einen Task auszuführen.
Da PowerShell die Befehlszeile automatisch analysiert und verarbeitet, wird der Parameter **-?** immer als „Hilfe für diesen Befehl anzeigen“ interpretiert.

> [!NOTE]
> Wenn Sie eine grafische Anwendung in PowerShell ausführen, wird das Fenster für die Anwendung geöffnet.
> PowerShell greift nur beim Verarbeiten der angegebenen Befehlszeileneingabe oder zur Ausgabe der Anwendungsergebnisse im Konsolenfenster ein. PowerShell hat keinen Einfluss darauf, wie die Anwendung intern arbeitet.

## <a name="powershell-uses-some-c-syntax"></a>PowerShell verwendet Teile der C#-Syntax

PowerShell basiert auf dem .NET Framework. Es verwendet einige Syntaxfeatures und Schlüsselwörter der Programmiersprache C#. Das Erlernen von PowerShell kann daher den Einstieg in C# vereinfachen. Wenn Sie bereits mit C# vertraut sind, kann Ihnen dies das Erlernen von PowerShell erleichtern.
