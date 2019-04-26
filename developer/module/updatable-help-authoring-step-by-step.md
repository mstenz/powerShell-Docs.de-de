---
title: 'Aktualisierbare Hilfeerstellung: Schrittweise | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082123"
---
# <a name="updatable-help-authoring-step-by-step"></a>Aktualisierbare Hilfeerstellung: Ausführliche Anleitung

Diese Dokumente sind die Schritte im Erstellen von aktualisierbaren Hilfe aufgeführt.

## <a name="authoring-updatable-help-step-by-step"></a>Erstellen aktualisierbare Hilfe: Ausführliche Anleitung

Aktualisierbare Hilfe ist für Endbenutzer ausgelegt, aber bietet auch bedeutende Vorteile, modulautoren und Hilfe Schreibern stammen, einschließlich der Möglichkeit zum Hinzufügen von Inhalt, Beheben von Fehlern, Bereitstellen in mehreren Benutzeroberflächenkulturen und reagieren auf Kommentare von Benutzern und Anforderungen, lange dauert es nach der Modul wurde versandt. In diesem Thema wird erläutert, wie Sie verpacken und Hochladen-Hilfedateien, damit Benutzer herunterladen und installieren Sie sie mithilfe von können die [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) und [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlets.

Die folgenden Schritte bieten einen Überblick über den Prozess der Unterstützung der aktualisierbaren Hilfe.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>Schritt 1: Suchen einer Internetsite für Ihre Hilfedateien

Der erste Schritt beim Erstellen von aktualisierbaren Hilfe ist finden Sie einen Speicherort im Internet nach Hilfedateien des Moduls. Tatsächlich können Sie zwei verschiedene Speicherorten. Sie können an einem Speicherort im Internet und die Hilfe Content-CAB-Dateien auf einem anderen Speicherort im Internet des Moduls hilfeinformationsdatei (HelpInfo XML - unten beschrieben) beibehalten. Alle Inhalte CAB Hilfedateien für ein Modul müssen sich am gleichen Standort sein. Sie können Hilfe Inhalte CAB-Dateien für unterschiedliche Module am gleichen Speicherort platzieren.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>Schritt 2: Fügen Sie einen HelpInfoURI-Schlüssel zu Ihrem modulmanifest

Hinzufügen einer **HelpInfoURI** Schlüssel zu Ihrem modulmanifest. Der Wert des Schlüssels ist der Uniform Resource Identifier (URI) des Speicherorts der HelpInfo XML-Informationsdatei für Ihr Modul. Aus Sicherheitsgründen muss die Adresse mit "http" oder "Https" beginnen. Der URI sollte einen Speicherort im Internet angeben, aber Sie dürfen keine der HelpInfo XML-Dateiname.

Beispiel:

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>Schritt 3: Erstellen Sie eine HelpInfo XML-Datei

Die HelpInfo XML-Informationsdatei enthält den URI, von dem Speicherort im Internet die Hilfedateien und die Versionsnummern der neuesten Hilfedateien für das Modul in jede unterstützte Benutzeroberflächenkultur an. Alle Windows PowerShell-Modul verfügt über eine HelpInfo XML-Datei. Wenn Sie die Hilfedateien aktualisieren, wird Sie bearbeiten oder Ersetzen Sie die HelpInfo XML-Datei; Fügen Sie eine andere nicht. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer HelpInfo-XML-Datei](./how-to-create-a-helpinfo-xml-file.md).

### <a name="step-4-sign-your-help-files"></a>Schritt 4: Signieren Sie die Hilfedateien

Digitale Signaturen sind nicht erforderlich, aber sie sind eine optimale Empfehlung, wenn Sie Dateien gemeinsam nutzen.

### <a name="step-5-create-cab-files"></a>Schritt 5: Erstellen der CAB-Dateien

Verwenden Sie ein Tool, erstellt der CAB-Dateien wie MakeCab.exe, zum Erstellen, einer. CAB-Datei, die die Hilfedateien für das Modul enthält. Erstellen Sie eine separate CAB-Datei für die Hilfedateien in jede unterstützte Benutzeroberflächenkultur an. Weitere Informationen finden Sie unter [vorbereiten aktualisierbare Hilfe CAB-Dateien wie](./how-to-prepare-updatable-help-cab-files.md).

### <a name="step-6-upload-your-files"></a>Schritt 6: Hochladen von Dateien

Um neue oder aktualisierte Hilfedateien zu veröffentlichen, Hochladen von CAB-Dateien auf dem Speicherort im Internet, die angegeben wird die **HelpContentUri** Element in der HelpInfo XML-Datei. Klicken Sie dann die HelpInfo XML-Datei hochladen, zu dem Speicherort im Internet, die durch den Wert der angegebenen die **HelpInfoUri** -Schlüssels im modulmanifest.
