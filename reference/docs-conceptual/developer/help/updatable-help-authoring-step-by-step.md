---
title: 'Aktualisierbare Hilfe Erstellung: Schritt für Schritt | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: a5290265f3d729504983b95195c793b88c4a2613
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811379"
---
# <a name="updatable-help-authoring-step-by-step"></a>Aktualisierbare Hilfeerstellung: Ausführliche Anleitung

In diesem Dokument sind die Schritte zum Erstellen der aktualisierbaren Hilfe aufgeführt.

## <a name="authoring-updatable-help-step-by-step"></a>Erstellen aktualisierbarer Hilfe: Schritt für Schritt

Aktualisierbare Hilfe ist für Endbenutzer konzipiert, bietet aber auch bedeutende Vorteile für Modul Autoren und Unterstützung von Writern, einschließlich der Möglichkeit, Inhalte hinzuzufügen, Fehler zu beheben, in mehreren Benutzeroberflächen Kulturen zu übermitteln und auf Benutzerkommentare und-Anforderungen zu reagieren, solange das Modul ausgeliefert wurde. In diesem Thema wird erläutert, wie Sie Hilfedateien Verpacken und hochladen, damit Benutzer diese mithilfe der Cmdlets [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) und [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) herunterladen und installieren können.

Die folgenden Schritte bieten einen Überblick über den Prozess der Unterstützung der aktualisierbaren Hilfe.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>Schritt 1: Suchen einer Internet Website für Ihre Hilfedateien

Der erste Schritt bei der Erstellung der aktualisierbaren Hilfe ist die Suche nach einem Internet Speicherort für die Hilfedateien Ihres Moduls. Tatsächlich können Sie zwei verschiedene Speicherorte verwenden. Sie können die Hilfe Informationsdatei Ihres Moduls (helpinfo XML-beschrieben unten) an einem Internet Speicherort und den Hilfe Inhalts-CAB-Dateien an einem anderen Internet Speicherort aufbewahren. Alle Hilfe Inhalts-CAB-Dateien für ein Modul müssen sich am gleichen Speicherort befinden. Sie können Hilfe Inhalts-CAB-Dateien für verschiedene Module am gleichen Speicherort platzieren.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>Schritt 2: Hinzufügen eines helpinfouri-Schlüssels zum Modul Manifest

Fügen Sie dem Modul Manifest einen **helpinfouri** -Schlüssel hinzu. Der Wert des Schlüssels ist die Uniform Resource Identifier (URI) des Speicher Orts der helpinfo-XML-Informationsdatei für das Modul. Aus Sicherheitsgründen muss die Adresse mit "http" oder "https" beginnen. Der URI sollte einen Internet Speicherort angeben, darf jedoch nicht den Namen der helpinfo-XML-Datei enthalten.

Beispiel:

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'https://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>Schritt 3: Erstellen einer helpinfo-XML-Datei

Die helpinfo-XML-Informationsdatei enthält den URI des Internet Speicherorts ihrer Hilfedateien und die Versionsnummern der neuesten Hilfedateien für das Modul in jeder unterstützten Benutzeroberflächen Kultur. Jedes Windows PowerShell-Modul verfügt über eine helpinfo-XML-Datei. Wenn Sie die Hilfedateien aktualisieren, müssen Sie die helpinfo-XML-Datei bearbeiten oder ersetzen. Sie fügen keinen weiteren hinzu. Weitere Informationen finden Sie unter [Erstellen einer helpinfo-XML-Datei](./how-to-create-a-helpinfo-xml-file.md).

### <a name="step-4-sign-your-help-files"></a>Schritt 4: Signieren der Hilfedateien

Digitale Signaturen sind nicht erforderlich, aber Sie sind eine bewährte Empfehlung, wenn Sie Dateien freigeben.

### <a name="step-5-create-cab-files"></a>Schritt 5: Erstellen von CAB-Dateien

Verwenden Sie ein Tool, mit dem CAB-Dateien (z. b. makecab. exe) erstellt werden, um eine zu erstellen. Die CAB-Datei, die die Hilfedateien für das Modul enthält. Erstellen Sie eine separate CAB-Datei für die Hilfedateien in jeder unterstützten Benutzeroberflächen Kultur. Weitere Informationen finden Sie unter [Vorbereiten der CAB-Dateien der aktualisierbaren Hilfe](./how-to-prepare-updatable-help-cab-files.md).

### <a name="step-6-upload-your-files"></a>Schritt 6: Hochladen der Dateien

Zum Veröffentlichen neuer oder aktualisierter Hilfedateien laden Sie die CAB-Dateien an den Internet Speicherort hoch, der durch das **helpcontenturi** -Element in der helpinfo-XML-Datei angegeben wird. Laden Sie dann die helpinfo-XML-Datei an den Internet Speicherort hoch, der durch den Wert des **helpinfouri** -Schlüssels im Modul Manifest angegeben wird.
