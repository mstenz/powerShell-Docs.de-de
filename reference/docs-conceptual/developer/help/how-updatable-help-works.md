---
title: Funktionsweise der aktualisierbaren Hilfe
ms.date: 09/13/2016
ms.openlocfilehash: 4849ce81e31171c6822a9078a77ebb45729185a3
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893287"
---
# <a name="how-updatable-help-works"></a>Funktionsweise der aktualisierbaren Hilfe

In diesem Thema wird erläutert, wie die aktualisierbare Hilfe die helpinfo-XML-Datei und die CAB-Dateien für jedes Modul verarbeitet und aktualisierte Hilfe für Benutzer installiert.

## <a name="the-update-help-process"></a>Der Update-help-Prozess

In der folgenden Liste werden die Aktionen des Cmdlets [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) beschrieben, wenn ein Benutzer einen Befehl ausführt, um die Hilfedateien für ein Modul in einer bestimmten UI-Kultur zu aktualisieren.

1. `Update-Help`Ruft die XML-Datei für die Remote-helpinfo von dem Speicherort ab, der durch den Wert des **helpinfouri** -Schlüssels im Modul Manifest angegeben wird, und überprüft die Datei anhand des Schemas. (Informationen zum Anzeigen des Schemas finden Sie unter [helpinfo-XML-Schema](./helpinfo-xml-schema.md).) `Update-Help`Sucht dann im Modul Verzeichnis auf dem Computer des Benutzers nach einer lokalen helpinfo-XML-Datei für das Modul.

1. `Update-Help`Vergleicht die Versionsnummer der Hilfedateien für die angegebene Benutzeroberflächen Kultur in den Remote-und lokalen helpinfo-XML-Dateien für das Modul. Wenn die Versionsnummer in der Remote Datei größer ist als die Versionsnummer in der lokalen Datei, oder wenn es keine lokale helpinfo-XML-Datei für das Modul gibt, `Update-Help` bereitet den Download neuer Hilfedateien vor.

1. `Update-Help`wählt die CAB-Datei für das Modul an dem Speicherort aus, der durch das **helpcontenturi** -Element in der XML-Datei für die Remote Hilfe angegeben wird. Er verwendet den Modulnamen, die Modul-GUID und die Benutzeroberflächen Kultur, um die CAB-Datei zu identifizieren.

1. `Update-Help`lädt die CAB-Datei herunter, entpackt Sie, überprüft die Hilfe Inhalts Dateien und speichert die Hilfe Inhalts Dateien im sprachspezifischen Unterverzeichnis des Modul Verzeichnisses auf dem Computer des Benutzers.

1. `Update-Help`erstellt eine lokale helpinfo-XML-Datei durch Kopieren der XML-Remote Datei. Die lokale helpinfo-XML-Datei wird bearbeitet, sodass Sie nur Elemente für die installierte CAB-Datei enthält.
   Anschließend wird die lokale helpinfo-XML-Datei im Modul Verzeichnis gespeichert und die Aktualisierung beendet.

## <a name="the-save-help-process"></a>Der Save-help-Prozess

In der folgenden Liste werden die Aktionen der Cmdlets " [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) " und " [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) " beschrieben, wenn ein Benutzer Befehle ausführt, um die Hilfedateien in einer Dateifreigabe zu aktualisieren, und dann diese Dateien verwenden, um die Hilfedateien auf dem Computer des Benutzers zu aktualisieren.

Das `Save-Help` Cmdlet führt die folgenden Aktionen als Reaktion auf einen Befehl aus, um die Hilfedateien für ein Modul in einer Dateifreigabe zu speichern, die durch den **DestinationPath** -Parameter angegeben wird.

1. `Save-Help`Ruft die XML-Datei für die Remote-helpinfo von dem Speicherort ab, der durch den Wert des **helpinfouri** -Schlüssels im Modul Manifest angegeben wird, und überprüft die Datei anhand des Schemas. (Informationen zum Anzeigen des Schemas finden Sie unter [helpinfo-XML-Schema](./helpinfo-xml-schema.md).) `Save-Help`Sucht dann in dem Verzeichnis, das durch den **DestinationPath** -Parameter im Befehl angegeben wird, nach einer lokalen helpinfo-XML-Datei `Save-Help` .

1. `Save-Help`Vergleicht die Versionsnummer der Hilfedateien für die angegebene Benutzeroberflächen Kultur in den Remote-und lokalen helpinfo-XML-Dateien für das Modul. Wenn die Versionsnummer in der Remote Datei größer ist als die Versionsnummer in der lokalen Datei, oder wenn keine lokale helpinfo-XML-Datei für das Modul im Verzeichnis **DestinationPath** vorhanden ist, wird vorbereitet, dass `Save-Help` neue Hilfedateien heruntergeladen werden.

1. `Save-Help`wählt die CAB-Datei für das Modul an dem Speicherort aus, der durch das **helpcontenturi** -Element in der XML-Datei für die Remote Hilfe angegeben wird. Er verwendet den Modulnamen, die Modul-GUID und die Benutzeroberflächen Kultur, um die CAB-Datei zu identifizieren.

1. `Save-Help`lädt die CAB-Datei herunter und speichert Sie im **DestinationPath** -Verzeichnis. (Es werden keine sprachspezifischen Unterverzeichnisse erstellt.)

1. `Save-Help`erstellt eine lokale helpinfo-XML-Datei durch Kopieren der XML-Remote Datei. Die lokale helpinfo-XML-Datei wird bearbeitet, sodass Sie nur Elemente für die von ihr gespeicherte CAB-Datei enthält.
   Anschließend wird die lokale helpinfo-XML-Datei im **DestinationPath** -Verzeichnis gespeichert und die Aktualisierung beendet.

   Das `Update-Help` Cmdlet führt die folgenden Aktionen als Reaktion auf einen Befehl aus, um die Hilfedateien auf dem Computer eines Benutzers aus den Dateien in einer Dateifreigabe zu aktualisieren, die durch den **SourcePath** -Parameter angegeben wird.

1. `Update-Help`Ruft die XML-Datei "Remote helpinfo" aus dem Verzeichnis " **SourcePath** " ab. Anschließend sucht er im Modul Verzeichnis auf dem Computer des Benutzers nach einer lokalen helpinfo-XML-Datei.

1. `Update-Help`Vergleicht die Versionsnummer der Hilfedateien für die angegebene Benutzeroberflächen Kultur in den Remote-und lokalen helpinfo-XML-Dateien für das Modul. Wenn die Versionsnummer in der Remote Datei größer ist als die Versionsnummer in der lokalen Datei, oder wenn keine lokale helpinfo-XML-Datei vorhanden ist, wird die `Update-Help` Installation neuer Hilfedateien vorbereitet.

1. `Update-Help`wählt die CAB-Datei für das Modul aus dem **SourcePath** -Verzeichnis aus. Er verwendet den Modulnamen, die Modul-GUID und die Benutzeroberflächen Kultur, um die CAB-Datei zu identifizieren.

1. `Update-Help`entpackt die CAB-Datei, überprüft die Hilfe Inhalts Dateien und speichert die Hilfe Inhalts Dateien im sprachspezifischen Unterverzeichnis des Modul Verzeichnisses auf dem Computer des Benutzers.

1. `Update-Help`erstellt eine lokale helpinfo-XML-Datei durch Kopieren der XML-Remote Datei. Die lokale helpinfo-XML-Datei wird bearbeitet, sodass Sie nur Elemente für die installierte CAB-Datei enthält.
   Anschließend wird die lokale helpinfo-XML-Datei im Modul Verzeichnis gespeichert und die Aktualisierung beendet.
