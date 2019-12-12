---
title: Aktualisierbare Hilfe Übersicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: 3f7388a9-9fa8-42bc-b294-538c9a01e30a
caps.latest.revision: 12
ms.openlocfilehash: f2dfb9642ba2dde38124142b659b425bbbb00f37
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366959"
---
# <a name="updatable-help-overview"></a>Aktualisierbare Hilfeübersicht

Dieses Dokument bietet eine grundlegende Einführung in den Entwurf und den Betrieb der aktualisierbaren Hilfe Funktion von Windows PowerShell. Es ist für Modul Autoren und andere konzipiert, die Windows PowerShell-Hilfe Themen für Benutzer bereitstellt.

## <a name="introduction"></a>Einführung

Windows PowerShell-Hilfe Themen sind ein wesentlicher Bestandteil der Windows PowerShell-Funktion. Ebenso wie Windows PowerShell-Module werden Hilfe Themen ständig von den Autoren und den Beiträgen der Community von Windows PowerShell-Benutzern aktualisiert und verbessert.

Das *aktualisierbare Hilfe* Feature, das in Windows PowerShell 3,0 eingeführt wurde, stellt sicher, dass die Benutzer über die neuesten Versionen der Hilfe Themen an der Eingabeaufforderung verfügen, auch für integrierte Windows PowerShell-Befehle, ohne neue Module herunterzuladen oder Windows Update auszuführen. Aktualisierbare Hilfe vereinfacht das Aktualisieren durch Bereitstellen von Cmdlets, die die neuesten Versionen der Hilfe Themen aus dem Internet herunterladen und in den richtigen Unterverzeichnissen auf dem lokalen Computer des Benutzers installieren. Selbst Benutzer, die sich hinter Firewalls befinden, können die neuen Cmdlets verwenden, um aktualisierte Hilfe von einer internen Dateifreigabe zu erhalten.

Aktualisierbare Hilfe wird vollständig von allen Windows PowerShell-Modulen in Windows® 8 und Windows Server® 2012 unterstützt, und die zugehörigen Funktionen sind für alle Windows PowerShell-Modul Autoren verfügbar. Die aktualisierbare Hilfe unterstützt nur XML-basierte Hilfedateien. Die Kommentar basierte Hilfe wird nicht unterstützt.

Die aktualisierbare Hilfe umfasst die folgenden Funktionen:

- Das [Update-Help-](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlet, das bestimmt, ob Benutzer über die neuesten Hilfedateien für ein Modul verfügen, und wenn nicht, lädt die neuesten Hilfedateien aus dem Internet herunter, entpackt Sie und installiert Sie in den richtigen Modul Unterverzeichnissen auf dem Computer des Benutzers.
  Benutzer können das Cmdlet " [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) " verwenden, um die neu installierten Hilfe Themen sofort anzuzeigen.
  PowerShell muss nicht neu gestartet werden.

- Das [Save-Help-](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlet, das die neuesten Hilfedateien aus dem Internet herunterlädt und in einem Dateisystem Verzeichnis speichert. Benutzer können das Cmdlet "`Update-Help`" verwenden, um Hilfedateien aus dem Dateisystem Verzeichnis abzurufen und Sie in den Modul Unterverzeichnissen auf dem Computer des Benutzers zu entpacken und zu installieren. Das Cmdlet "`Save-Help`" wurde für Benutzer konzipiert, die nur über eingeschränkten oder keinen Zugriff auf das Internet verfügen, und für Unternehmen, die den Zugriff auf den Internet

- **Hilfe für ein Modul**. Hilfedateien für ein Modul werden verwaltet und als Einheit bereitgestellt, sodass Benutzer alle Hilfedateien für die Module erhalten können, die Sie verwenden. Aktualisierbare Hilfe wird nur für Module unterstützt, nicht für Windows PowerShell-Snap-Ins.

- **Versions Unterstützung**. Bei der aktualisierbaren Hilfe wird der Standardwert für vier Positionen (N1 N2. N3. N4) Versionsnummern. Aktualisierbare Hilfe lädt Hilfedateien herunter, wenn die Versionsnummer der Hilfedateien auf dem Computer des Benutzers (oder im `Save-Help` Verzeichnis) niedriger ist als die Versionsnummer der Hilfedateien am Internet Speicherort.

- **Unterstützung für mehrere Sprachen**. Aktualisierbare Hilfe unterstützt Modul Hilfedateien in mehreren Benutzeroberflächen Kulturen. Zu den aktualisierbaren Hilfe Dateinamen zählen Standardsprachen Codes, wie z. b. "en-US" und "ja-JP", und die Cmdlets "`Update-Help`" und "`Save-Help`" platzieren die Hilfedateien in sprachspezifischen Unterverzeichnissen des Modul Verzeichnisses.

- **Automatisch generierte Hilfe**. Das Cmdlet " [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) " zeigt die grundlegende Hilfe für Befehle an, die keine Hilfedateien enthalten. Die automatisch generierte Hilfe umfasst die Befehlssyntax und Aliase sowie Anweisungen für die Verwendung der Online Hilfe und aktualisierbarer Hilfe.

- **Verbesserte Online Hilfe**. Der einfache Zugriff auf die Online Hilfe erfordert keine Hilfedateien mehr. Der **Online-** Parameter des Cmdlets "`Get-Help`" ruft nun die URL eines Online Hilfe Themas aus dem Wert der **HelpUri** -Eigenschaft eines beliebigen Befehls ab, wenn die Online Hilfe-URL nicht in einer Hilfedatei gefunden wird. Sie können die **HelpUri** -Eigenschaft auffüllen, indem Sie dem Code von Cmdlets, Funktionen und CIM-Befehlen ein **HelpUri** -Attribut hinzufügen oder indem Sie verwenden **. Link** Kommentar basierte Hilfe Direktive in Workflows und Skripts.

  Um unsere Hilfedateien aktualisierbar zu machen, werden die Windows PowerShell-Module in Windows 8 und Windows Server vNext nicht mit Hilfedateien geliefert. Benutzer können die aktualisierbare Hilfe verwenden, um Hilfedateien zu installieren und zu aktualisieren. Autoren anderer Module können Hilfedateien in Module einschließen oder Sie weglassen. Die Unterstützung für aktualisierbare Hilfe ist optional, wird jedoch empfohlen.
