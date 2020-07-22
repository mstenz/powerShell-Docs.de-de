---
title: Aktualisierbare Hilfeübersicht
ms.date: 03/22/2012
ms.openlocfilehash: 142bac764c93728d302707504d6d3fb2d50a3a7b
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892318"
---
# <a name="updatable-help-overview"></a>Aktualisierbare Hilfeübersicht

Dieses Dokument enthält eine grundlegende Einführung in den Entwurf und den Betrieb der PowerShell-Funktion für aktualisierbare Hilfe. Es ist für Modul Autoren und andere konzipiert, die Windows PowerShell-Hilfe Themen für Benutzer bereitstellt.

## <a name="introduction"></a>Einführung

PowerShell-Hilfe Themen sind ein wesentlicher Bestandteil der PowerShell-Funktion. Ebenso wie PowerShell-Module werden Hilfe Themen ständig von den Autoren und den Beiträgen der Community von PowerShell-Benutzern aktualisiert und verbessert.

Das in Windows PowerShell 3,0 eingeführte Feature für *aktualisierbare Hilfe* stellt sicher, dass Benutzer über die neuesten Versionen der Hilfe Themen an der Eingabeaufforderung verfügen, auch für integrierte PowerShell-Befehle, ohne neue Module herunterzuladen oder Windows Update auszuführen. Aktualisierbare Hilfe vereinfacht das Aktualisieren durch Bereitstellen von Cmdlets, die die neuesten Versionen der Hilfe Themen aus dem Internet herunterladen und in den richtigen Unterverzeichnissen auf dem lokalen Computer des Benutzers installieren. Selbst Benutzer, die sich hinter Firewalls befinden, können die neuen Cmdlets verwenden, um aktualisierte Hilfe von einer internen Dateifreigabe zu erhalten.

Aktualisierbare Hilfe wird vollständig von allen Windows PowerShell-Modulen in Windows 8 und Windows Server 2012 unterstützt, und die zugehörigen Funktionen sind für alle Windows PowerShell-Modul Autoren verfügbar. Die aktualisierbare Hilfe unterstützt nur XML-basierte Hilfedateien. Die Kommentar basierte Hilfe wird nicht unterstützt.

Die aktualisierbare Hilfe umfasst die folgenden Funktionen:

- Das [Update-Help-](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlet, das bestimmt, ob Benutzer über die neuesten Hilfedateien für ein Modul verfügen, und wenn nicht, lädt die neuesten Hilfedateien aus dem Internet herunter, entpackt Sie und installiert Sie in den richtigen Modul Unterverzeichnissen auf dem Computer des Benutzers. Benutzer können das Cmdlet " [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) " verwenden, um die neu installierten Hilfe Themen sofort anzuzeigen. PowerShell muss nicht neu gestartet werden.

- Das [Save-Help-](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlet, das die neuesten Hilfedateien aus dem Internet herunterlädt und in einem Dateisystem Verzeichnis speichert. Benutzer können mit dem `Update-Help` Cmdlet Hilfedateien aus dem Dateisystem Verzeichnis erhalten und in den Modul Unterverzeichnissen auf dem Computer des Benutzers entpacken und installieren. Das `Save-Help` Cmdlet wurde für Benutzer konzipiert, die nur über eingeschränkten oder keinen Zugriff auf das Internet verfügen, und für Unternehmen, die bevorzugen, den Internet Zugriff einzuschränken.

- **Hilfe für ein Modul**. Hilfedateien für ein Modul werden verwaltet und als Einheit bereitgestellt, sodass Benutzer alle Hilfedateien für die Module erhalten können, die Sie verwenden. Aktualisierbare Hilfe wird nur für Module unterstützt, nicht für Windows PowerShell-Snap-Ins.

- **Versions Unterstützung**. Bei der aktualisierbaren Hilfe wird der Standardwert für vier Positionen (N1 N2. N3. N4) Versionsnummern.
  Aktualisierbare Hilfe lädt Hilfedateien herunter, wenn die Versionsnummer der Hilfedateien auf dem Computer des Benutzers (oder im `Save-Help` Verzeichnis) niedriger ist als die Versionsnummer der Hilfedateien am Internet Speicherort.

- **Unterstützung für mehrere Sprachen**. Aktualisierbare Hilfe unterstützt Modul Hilfedateien in mehreren Benutzeroberflächen Kulturen.
  Aktualisierbare Hilfe Dateinamen enthalten Standardsprachen Codes, wie z. b. "en-US" und "ja-JP", und die `Update-Help` -und- `Save-Help` Cmdlets platzieren die Hilfedateien in sprachspezifischen Unterverzeichnissen des Modul Verzeichnisses.

- **Automatisch generierte Hilfe**. Das Cmdlet " [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) " zeigt die grundlegende Hilfe für Befehle an, die keine Hilfedateien enthalten. Die automatisch generierte Hilfe umfasst die Befehlssyntax und Aliase sowie Anweisungen für die Verwendung der Online Hilfe und aktualisierbarer Hilfe.

- **Verbesserte Online Hilfe**. Der einfache Zugriff auf die Online Hilfe erfordert keine Hilfedateien mehr. Der **Online-** Parameter des `Get-Help` Cmdlets ruft nun die URL eines Online Hilfe Themas aus dem Wert der **HelpUri** -Eigenschaft eines beliebigen Befehls ab, wenn die Online Hilfe-URL nicht in einer Hilfedatei gefunden wird. Sie können die **HelpUri** -Eigenschaft auffüllen, indem Sie dem Code von Cmdlets, Funktionen und CIM-Befehlen ein **HelpUri** -Attribut hinzufügen oder indem Sie verwenden **. Link** Kommentar basierte Hilfe Direktive in Workflows und Skripts.

  Um unsere Hilfedateien aktualisierbar zu machen, werden die Windows PowerShell-Module in Windows 8 und Windows Server vNext nicht mit Hilfedateien geliefert. Benutzer können die aktualisierbare Hilfe verwenden, um Hilfedateien zu installieren und zu aktualisieren. Autoren anderer Module können Hilfedateien in Module einschließen oder Sie weglassen. Die Unterstützung für aktualisierbare Hilfe ist optional, wird jedoch empfohlen.
