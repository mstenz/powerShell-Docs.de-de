---
title: Funktionsweise der aktualisierbaren Hilfe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: 5b6ae54ee6c843996c875189b6ee553be5e4f614
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367079"
---
# <a name="how-updatable-help-works"></a>Funktionsweise der aktualisierbaren Hilfe

In diesem Thema wird erläutert, wie die aktualisierbare Hilfe die helpinfo-XML-Datei und die CAB-Dateien für jedes Modul verarbeitet und aktualisierte Hilfe für Benutzer installiert.

## <a name="the-update-help-process"></a>Der Update-help-Prozess

In der folgenden Liste werden die Aktionen des Cmdlets [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) beschrieben, wenn ein Benutzer einen Befehl ausführt, um die Hilfedateien für ein Modul in einer bestimmten UI-Kultur zu aktualisieren.

1. `Update-Help` ruft die XML-Remote Datei aus dem Speicherort ab, der durch den Wert des **helpinfouri** -Schlüssels im Modul Manifest angegeben wird, und überprüft die Datei anhand des Schemas. (Informationen zum Anzeigen des Schemas finden Sie unter [helpinfo-XML-Schema](./helpinfo-xml-schema.md).) Anschließend sucht `Update-Help` nach einer lokalen helpinfo-XML-Datei für das Modul im Modul Verzeichnis auf dem Computer des Benutzers.

2. `Update-Help` vergleicht die Versionsnummer der Hilfedateien für die angegebene Benutzeroberflächen Kultur in den Remote-und lokalen helpinfo-XML-Dateien für das Modul. Wenn die Versionsnummer in der Remote Datei größer ist als die Versionsnummer in der lokalen Datei, oder wenn es keine lokale helpinfo-XML-Datei für das Modul gibt, bereitet `Update-Help` den Download neuer Hilfedateien vor.

3. `Update-Help` wählt die CAB-Datei für das Modul an dem Speicherort aus, der durch das **helpcontenturi** -Element in der XML-Datei "Remote helpinfo" angegeben wird. Er verwendet den Modulnamen, die Modul-GUID und die Benutzeroberflächen Kultur, um die CAB-Datei zu identifizieren.

4. `Update-Help` lädt die CAB-Datei herunter, entpackt Sie, überprüft die Hilfe Inhalts Dateien und speichert die Hilfe Inhalts Dateien im sprachspezifischen Unterverzeichnis des Modul Verzeichnisses auf dem Computer des Benutzers.

5. `Update-Help` erstellt eine lokale helpinfo-XML-Datei durch Kopieren der Remote-helpinfo-XML-Datei. Die lokale helpinfo-XML-Datei wird bearbeitet, sodass Sie nur Elemente für die installierte CAB-Datei enthält. Anschließend wird die lokale helpinfo-XML-Datei im Modul Verzeichnis gespeichert und die Aktualisierung beendet.

## <a name="the-save-help-process"></a>Der Save-help-Prozess

In der folgenden Liste werden die Aktionen der Cmdlets " [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) " und " [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) " beschrieben, wenn ein Benutzer Befehle ausführt, um die Hilfedateien in einer Dateifreigabe zu aktualisieren, und dann diese Dateien verwenden, um die Hilfedateien auf dem Computer des Benutzers zu aktualisieren.

Das Cmdlet "`Save-Help`" führt die folgenden Aktionen als Reaktion auf einen Befehl aus, um die Hilfedateien für ein Modul in einer Dateifreigabe zu speichern, die durch den **DestinationPath** -Parameter angegeben wird.

1. `Save-Help` ruft die XML-Remote Datei aus dem Speicherort ab, der durch den Wert des **helpinfouri** -Schlüssels im Modul Manifest angegeben wird, und überprüft die Datei anhand des Schemas. (Informationen zum Anzeigen des Schemas finden Sie unter [helpinfo-XML-Schema](./helpinfo-xml-schema.md).) Anschließend sucht `Save-Help` in dem Verzeichnis, das durch den **DestinationPath** -Parameter im `Save-Help`-Befehl angegeben wird, nach einer lokalen helpinfo-XML-Datei.

2. `Save-Help` vergleicht die Versionsnummer der Hilfedateien für die angegebene Benutzeroberflächen Kultur in den Remote-und lokalen helpinfo-XML-Dateien für das Modul. Wenn die Versionsnummer in der Remote Datei größer ist als die Versionsnummer in der lokalen Datei, oder wenn es keine lokale helpinfo-XML-Datei für das Modul im **DestinationPath** -Verzeichnis gibt, bereitet `Save-Help` das Herunterladen neuer Hilfedateien vor.

3. `Save-Help` wählt die CAB-Datei für das Modul an dem Speicherort aus, der durch das **helpcontenturi** -Element in der XML-Datei "Remote helpinfo" angegeben wird. Er verwendet den Modulnamen, die Modul-GUID und die Benutzeroberflächen Kultur, um die CAB-Datei zu identifizieren.

4. `Save-Help` lädt die CAB-Datei herunter und speichert Sie im **DestinationPath** -Verzeichnis. (Es werden keine sprachspezifischen Unterverzeichnisse erstellt.)

5. `Save-Help` erstellt eine lokale helpinfo-XML-Datei durch Kopieren der Remote-helpinfo-XML-Datei. Die lokale helpinfo-XML-Datei wird bearbeitet, sodass Sie nur Elemente für die von ihr gespeicherte CAB-Datei enthält. Anschließend wird die lokale helpinfo-XML-Datei im **DestinationPath** -Verzeichnis gespeichert und die Aktualisierung beendet.

   Das Cmdlet "`Update-Help`" führt die folgenden Aktionen als Reaktion auf einen Befehl aus, um die Hilfedateien auf dem Computer eines Benutzers aus den Dateien in einer Dateifreigabe zu aktualisieren, die durch den **SourcePath** -Parameter angegeben wird.

1. `Update-Help` ruft die XML-Datei "Remote helpinfo" aus dem Verzeichnis " **SourcePath** " ab. Anschließend sucht er im Modul Verzeichnis auf dem Computer des Benutzers nach einer lokalen helpinfo-XML-Datei.

2. `Update-Help` vergleicht die Versionsnummer der Hilfedateien für die angegebene Benutzeroberflächen Kultur in den Remote-und lokalen helpinfo-XML-Dateien für das Modul. Wenn die Versionsnummer in der Remote Datei größer ist als die Versionsnummer in der lokalen Datei, oder wenn es keine lokale helpinfo-XML-Datei gibt, bereitet `Update-Help` die Installation neuer Hilfedateien vor.

3. `Update-Help` wählt die CAB-Datei für das Modul aus dem **SourcePath** -Verzeichnis aus. Er verwendet den Modulnamen, die Modul-GUID und die Benutzeroberflächen Kultur, um die CAB-Datei zu identifizieren.

4. `Update-Help` entpackt die CAB-Datei, überprüft die Hilfe Inhalts Dateien und speichert die Hilfe Inhalts Dateien im sprachspezifischen Unterverzeichnis des Modul Verzeichnisses auf dem Computer des Benutzers.

5. `Update-Help` erstellt eine lokale helpinfo-XML-Datei durch Kopieren der Remote-helpinfo-XML-Datei. Die lokale helpinfo-XML-Datei wird bearbeitet, sodass Sie nur Elemente für die installierte CAB-Datei enthält. Anschließend wird die lokale helpinfo-XML-Datei im Modul Verzeichnis gespeichert und die Aktualisierung beendet.