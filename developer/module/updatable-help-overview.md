---
title: Übersicht über die aktualisierbare Hilfe | Microsoft-Dokumentation
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082091"
---
# <a name="updatable-help-overview"></a>Aktualisierbare Hilfeübersicht

Dieses Dokument enthält eine grundlegende Einführung in die Entwurfs- und den Betrieb von Windows PowerShell aktualisierbaren Hilfefunktion. Es dient modulautoren und andere, die Benutzer die Windows PowerShell-Hilfethemen für Benutzer bereitzustellen.

## <a name="introduction"></a>Einführung

Windows PowerShell-Hilfethemen sind ein wesentlicher Bestandteil der Windows PowerShell-Oberfläche. Wie Windows PowerShell-Module werden die Hilfethemen ständig aktualisiert und verbessert werden, durch die Autoren und die Beiträge der Community von Windows PowerShell-Benutzer.

Die *aktualisierbare Hilfe* , eingeführt in Windows PowerShell 3.0 wird sichergestellt, dass Benutzer an der Eingabeaufforderung ein, auch für die integrierte Windows PowerShell-Befehle, die neuesten Versionen der Hilfethemen haben, ohne neue Module herunterzuladen oder Ausführen von Windows Update. Aktualisierbare Hilfe wird aktualisiert einfach durch Bereitstellen von Cmdlets, die die neuesten Versionen der Hilfethemen aus dem Internet herunterladen und installieren Sie sie in der richtigen Unterverzeichnisse auf dem lokalen Computer des Benutzers. Selbst Benutzer, die sich hinter Firewalls befinden können die neuen Cmdlets aktualisierte Hilfe in einer internen Dateifreigabe verwenden.

Aktualisierbare Hilfe wird von allen Windows PowerShell-Modulen in Windows® 8 und Windows Server® 2012 vollständig unterstützt, und seine Funktionen sind für alle Autoren von Windows PowerShell-Modul verfügbar. Aktualisierbare Hilfe unterstützt nur die XML-basierte Hilfedateien. Kommentarbasierte Hilfe wird nicht unterstützt.

Aktualisierbare Hilfe umfasst die folgenden Funktionen.

- Die [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) -Cmdlet, das bestimmt, ob Benutzer über die neuesten Hilfedateien haben Dateien für ein Modul und, falls nicht, lädt die neuesten Hilfedateien aus dem Internet herunter, entpackt sie und installiert sie in den Unterverzeichnissen richtige Modul auf der Computer des Benutzers.
  Benutzer können die [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet, um die neu installierte Hilfethemen sofort anzuzeigen.
  Sie müssen kein PowerShell neu zu starten.

- Die [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) -Cmdlet, das die neuesten Hilfedateien lädt Dateien aus dem Internet und speichert sie in einem Dateisystemverzeichnis. Benutzer können die `Update-Help` -Cmdlet zum Abrufen von Hilfedateien aus dem Verzeichnis, und Entpacken und installieren Sie sie in den Unterverzeichnissen Modul auf dem Computer des Benutzers. Die `Save-Help` Cmdlet wurde entwickelt, für Benutzer mit eingeschränkter oder gar keinen Internetzugriff verfügen und für Unternehmen, die Zugriff auf das Internet einschränken möchten.

- **Die Hilfe für ein Modul**. Hilfedateien für ein Modul verwaltet und als Einheit bereitgestellt werden, damit Benutzer die Hilfedateien für Module Abrufen aller können, die sie verwenden. Aktualisierbare Hilfe ist nur für Module, die nicht für Windows PowerShell-Snap-ins unterstützt.

- **Versionsunterstützung**. Aktualisierbare Hilfedateien verwendet vier-Position (N1. N2. N3. Versionsnummern für N4). Aktualisierbare Hilfedateien Hilfedateien heruntergeladen, wenn die Versionsnummer der Hilfe-auf dem Computer des Benutzers Dateien (oder in der `Save-Help` Verzeichnis) ist niedriger als die Versionsnummer der Hilfedateien auf dem Speicherort im Internet.

- **Unterstützung mehrerer Sprachen**. Aktualisierbare Hilfe unterstützt Modul Hilfedateien in mehreren Benutzeroberflächenkulturen. Aktualisierbare Hilfedateien Dateinamen enthalten standard Sprachcodes, z. B. "En-US" und "ja-JP" und die `Update-Help` und `Save-Help` Cmdlets müssen Sie die Hilfedateien in sprachspezifischen Unterverzeichnissen des Modulverzeichnisses.

- **Automatisch generierte Hilfe**. Die [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet zeigt die grundlegende Hilfe für Befehle, die keine Hilfedateien vorhanden sind. Die automatisch generierte Hilfe umfasst die Befehlssyntax und Aliase, und Anweisungen für die Verwendung von online-Hilfe und die aktualisierbare Hilfe.

- **Verbesserte Onlinehilfe**. Einfacher Zugriff auf die Onlinehilfe ist die Hilfedateien mehr erforderlich. Die **Online** Parameter, der die `Get-Help` Cmdlet ruft nun die URL von einem Onlinehilfethema aus der Wert des der **HelpUri** Eigenschaft von Befehlen, wenn die online-Hilfe-URL in einer Hilfedatei gefunden werden kann. Sie füllen können die **HelpUri** Eigenschaft durch das Hinzufügen einer **HelpUri** -Attribut auf den Code des-Cmdlets, Funktionen und CIM-Befehle oder mithilfe der **. Link** kommentarbasierte Hilfe-Direktive in Workflows und Skripts.

  Um unsere Hilfedateien aktualisieren zu können, stammen nicht die Windows PowerShell-Module in Windows 8 und Windows Server vNext Hilfedateien. Benutzer können aktualisierbare Hilfe zum Installieren von Hilfedateien und diese zu aktualisieren. Autoren von anderen Modulen können Hilfedateien in Modulen enthalten, oder lassen sie. Unterstützung für aktualisierbare Hilfe ist optional, jedoch empfohlen.
