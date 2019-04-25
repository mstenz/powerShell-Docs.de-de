---
title: Funktionsweise von aktualisierbaren Hilfe Works | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: 5b6ae54ee6c843996c875189b6ee553be5e4f614
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082259"
---
# <a name="how-updatable-help-works"></a>Funktionsweise der aktualisierbaren Hilfe

In diesem Thema wird erläutert, wie der aktualisierbaren Hilfe Prozesse die HelpInfo XML-Datei und die CAB-Dateien für jedes Modul, und installiert die Hilfe für Benutzer aktualisiert.

## <a name="the-update-help-process"></a>Der Update-Help-Prozess

Die folgende Liste beschreibt die Aktionen der [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlet aus, wenn ein Benutzer einen Befehl zum Aktualisieren der Hilfedateien für ein Modul in einer bestimmten UI-Kultur ausgeführt wird.

1. `Update-Help` Ruft die HelpInfo XML-Remotedatei an der durch den Wert der angegebenen Position der **HelpInfoURI** im modulmanifest Schlüssel und die Datei anhand des Schemas überprüft. (Um das Schema anzuzeigen, finden Sie unter [HelpInfo-XML-Schema](./helpinfo-xml-schema.md).) Klicken Sie dann `Update-Help` sucht nach einer lokalen HelpInfo XML-Datei für das Modul in das Modulverzeichnis auf dem Computer des Benutzers.

2. `Update-Help` Vergleicht die Versionsnummer der Hilfedateien für die angegebene Benutzeroberflächenkultur in den lokalen und remote HelpInfo XML-Dateien für das Modul an. Wenn die Versionsnummer für die remote-Datei größer als die Versionsnummer für die lokale Datei ist oder wenn es keine lokale HelpInfo XML-Datei für das Modul gibt `Update-Help` bereitet, neue Hilfedateien herunterzuladen.

3. `Update-Help` Wählt die CAB-Datei für das Modul aus dem Speicherort, die gemäß der **HelpContentUri** Element in der remote HelpInfo-XML-Datendatei. Es verwendet die Modulnamen, die Modul-GUID und die UI-Kultur, um die CAB-Datei zu identifizieren.

4. `Update-Help` Lädt die CAB-Datei herunter, entpackt sie, überprüft die Hilfe Inhaltsdateien und speichert die Hilfe Inhaltsdateien in die sprachspezifischen Unterverzeichnis des Modulverzeichnisses auf dem Computer des Benutzers.

5. `Update-Help` erstellt eine lokale HelpInfo XML-Datei durch Kopieren der remote HelpInfo XML-Datei an. Die lokale HelpInfo XML-Datei bearbeitet, damit sie Elemente nur für die CAB-Datei enthält, die es installiert. Anschließend speichert die lokale HelpInfo XML-Datei im Modulverzeichnis gespeichert und wird abgeschlossen, das Update.

## <a name="the-save-help-process"></a>Der Save-Help-Prozess

Die folgende Liste beschreibt die Aktionen der [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) und [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlets, wenn ein Benutzer führt die Befehle zum Aktualisieren der Hilfedateien in einer Dateifreigabe, und klicken Sie dann diese Dateien beim Aktualisieren der Hilfedateien auf den Computer des Benutzers.

Die `Save-Help` -Cmdlet führt die folgenden Aktionen als Reaktion auf einen Befehl aus, um die Hilfedateien für ein Modul in eine Dateifreigabe zu speichern, die angegeben wird die **DestinationPath** Parameter.

1. `Save-Help` Ruft die HelpInfo XML-Remotedatei an der durch den Wert der angegebenen Position der **HelpInfoURI** im modulmanifest Schlüssel und die Datei anhand des Schemas überprüft. (Um das Schema anzuzeigen, finden Sie unter [HelpInfo-XML-Schema](./helpinfo-xml-schema.md).) Klicken Sie dann `Save-Help` sucht nach einer lokalen HelpInfo XML-Datei im Verzeichnis, das angegeben wird die **DestinationPath** Parameter in der `Save-Help` Befehl.

2. `Save-Help` Vergleicht die Versionsnummer der Hilfedateien für die angegebene Benutzeroberflächenkultur in den lokalen und remote HelpInfo XML-Dateien für das Modul an. Wenn die Versionsnummer für die remote-Datei größer als die Versionsnummer für die lokale Datei ist oder wenn es keine lokale HelpInfo XML-Datei für das Modul gibt der **DestinationPath** Verzeichnis `Save-Help` bereitet, neue Hilfedateien herunterzuladen.

3. `Save-Help` Wählt die CAB-Datei für das Modul aus dem Speicherort, die gemäß der **HelpContentUri** Element in der remote HelpInfo-XML-Datendatei. Es verwendet die Modulnamen, die Modul-GUID und die UI-Kultur, um die CAB-Datei zu identifizieren.

4. `Save-Help` die CAB-Datei lädt und speichert sie in der **DestinationPath** Verzeichnis. (Es wird keine sprachspezifischen Unterverzeichnisse erstellt.)

5. `Save-Help` erstellt eine lokale HelpInfo XML-Datei durch Kopieren der remote HelpInfo XML-Datei an. Die lokale HelpInfo XML-Datei bearbeitet, damit sie Elemente nur für die CAB-Datei enthält, die sie gespeichert haben. Dann die lokale HelpInfo XML-Datei in speichert die **DestinationPath** Verzeichnis und schließt das Update.

   Die `Update-Help` -Cmdlet führt die folgenden Aktionen als Reaktion auf einen Befehl aus, um die Hilfedateien auf dem Computer eines Benutzers aus den Dateien in einer Dateifreigabe aktualisieren, die angegeben wird die **SourcePath** Parameter.

1. `Update-Help` Ruft ab, der remote HelpInfo XML-Datei aus dem **SourcePath** Verzeichnis. Klicken Sie dann nach einer lokalen HelpInfo XML-Datei im Modulverzeichnis auf dem Computer des Benutzers gesucht.

2. `Update-Help` Vergleicht die Versionsnummer der Hilfedateien für die angegebene Benutzeroberflächenkultur in den lokalen und remote HelpInfo XML-Dateien für das Modul an. Wenn die Versionsnummer für die remote-Datei größer als die Versionsnummer für die lokale Datei ist oder wenn es keine lokale HelpInfo XML-Datei gibt `Update-Help` bereitet, neue Hilfedateien zu installieren.

3. `Update-Help` Wählt die CAB-Datei für das Modul aus **SourcePath** Verzeichnis. Es verwendet die Modulnamen, die Modul-GUID und die UI-Kultur, um die CAB-Datei zu identifizieren.

4. `Update-Help` die CAB-Datei entpackt, überprüft die Hilfe Inhaltsdateien und speichert die Hilfe Inhaltsdateien in die sprachspezifischen Unterverzeichnis des Modulverzeichnisses auf dem Computer des Benutzers.

5. `Update-Help` erstellt eine lokale HelpInfo XML-Datei durch Kopieren der remote HelpInfo XML-Datei an. Die lokale HelpInfo XML-Datei bearbeitet, damit sie Elemente nur für die CAB-Datei enthält, die es installiert. Anschließend speichert die lokale HelpInfo XML-Datei im Modulverzeichnis gespeichert und wird abgeschlossen, das Update.