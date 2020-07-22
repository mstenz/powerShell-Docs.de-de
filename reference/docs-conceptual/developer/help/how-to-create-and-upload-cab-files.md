---
title: Erstellen und Hochladen von CAB-Dateien
ms.date: 09/13/2016
ms.openlocfilehash: 247ed70ba206d70be01155653efbe887bf603f53
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893032"
---
# <a name="how-to-create-and-upload-cab-files"></a>Erstellen und Hochladen von CAB-Dateien

In diesem Thema wird erläutert, wie Sie aktualisierbare Hilfe-CAB-Dateien erstellen und an den Speicherort hochladen, an dem die aktualisierbaren Hilfe-Cmdlets Sie finden

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>Erstellen und Hochladen von aktualisierbaren Hilfe-CAB-Dateien

Sie können das Feature "aktualisierbare Hilfe" verwenden, um neue oder aktualisierte Hilfedateien für ein Modul in mehreren Sprachen und Kulturen bereitzustellen. Ein Aktualisier bares Hilfe Paket für ein Modul besteht aus einer helpinfo-XML-Datei und einer oder mehreren CAB- `.CAB` Dateien (). Jede CAB-Datei enthält Hilfedateien für das Modul in einer Benutzeroberflächen Kultur. Verwenden Sie das folgende Verfahren zum Erstellen von CAB-Dateien für die aktualisierbare Hilfe.

1. Organisieren Sie die Hilfedateien für das Modul anhand der Benutzeroberflächen Kultur. Jede aktualisierbare Hilfe-CAB-Datei enthält die Hilfedateien für ein Modul in einer Benutzeroberflächen Kultur. Sie können mehrere Hilfe-CAB-Dateien für das Modul bereitzustellen, jeweils für eine andere Benutzeroberflächen Kultur.

1. Stellen Sie sicher, dass Hilfedateien nur die Dateitypen enthalten, die für eine aktualisierbare Hilfe zulässig sind, und überprüfen Sie Sie anhand eines Hilfe Wenn das `Update-Help` Cmdlet auf eine Datei trifft, die ungültig ist oder kein zulässiger Typ ist, wird die ungültige Datei nicht installiert, und die Installation von Dateien aus dem CAB wird beendet. Eine Liste zulässiger Dateitypen finden Sie unter [in einer aktualisierbare Hilfe-CAB-Datei zugelassene Dateitypen](./file-types-permitted-in-an-updatable-help-cab-file.md).

1. Signieren Sie die Hilfedateien Digital. Digitale Signaturen sind nicht erforderlich, aber es handelt sich um eine bewährte Vorgehensweise.

1. Fügen Sie alle Hilfedateien für das Modul in die UI-Kultur ein, nicht nur Dateien, die neu sind oder geändert wurden. Wenn die CAB-Datei unvollständig ist, verfügt der Benutzer, der Hilfedateien zum ersten Mal herunterlädt oder nicht jedes Update herunterlädt, nicht über alle Modul Hilfedateien.

1. Verwenden Sie ein Hilfsprogramm, das CAB-Dateien erstellt, z `MakeCab.exe` . b. PowerShell umfasst keine Cmdlets, die CAB-Dateien erstellen.

1. Benennen Sie die CAB-Dateien. Weitere Informationen finden Sie unter [How to Name a Updatable Help CAB file](./how-to-name-an-updatable-help-cab-file.md).

1. Laden Sie die CAB-Dateien für das Modul an den Speicherort hoch, der durch das **helpcontenturi** -Element in der helpinfo-XML-Datei für das Modul angegeben wird. Laden Sie dann die helpinfo-XML-Datei an den Speicherort hoch, der durch den **helpinfouri** -Schlüssel des Modul Manifests angegeben wird. **Helpcontenturi** und **helpinfouri** können auf denselben Speicherort zeigen.

> [!CAUTION]
> Der Wert der **helpinfouri** -Taste und des **helpcontenturi** -Elements muss mit `http` oder beginnen `https` . Der Wert muss einen Internet Speicherort angeben und darf keinen Dateinamen enthalten.
