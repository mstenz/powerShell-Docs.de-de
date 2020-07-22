---
title: Aktualisieren von Hilfedateien
ms.date: 09/12/2016
ms.openlocfilehash: 80f7c8865729515de98648765fa36ce540e00162
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892947"
---
# <a name="how-to-update-help-files"></a>Aktualisieren von Hilfedateien

In diesem Thema wird erläutert, wie Sie Hilfedateien für ein Modul aktualisieren, das aktualisierbare Hilfe unterstützt.

## <a name="updating-help-files"></a>Aktualisieren von Hilfedateien

Es gibt viele Gründe, Hilfedateien zu aktualisieren, wie z. b. das Beheben von Fehlern, das verdeutlichen eines Konzepts, das Beantworten einer häufig gestellten Frage, das Hinzufügen neuer Dateien oder das Hinzufügen neuer und besserer Beispiele.

So aktualisieren Sie eine Hilfedatei:

1. Ändern Sie die Dateien.
1. Übersetzen Sie die Dateien in andere Benutzeroberflächen Kulturen.
1. Sammeln Sie alle Hilfedateien (neu, geändert und unverändert) für das Modul in jeder Benutzeroberflächen Kultur.
1. Überprüfen Sie die Dateien anhand des XML-Schemas.
1. Erstellen Sie die CAB-Dateien für jede Benutzeroberflächen Kultur neu.
1. Erhöhen Sie in der helpinfo-XML-Datei die Versionsnummern der CAB-Datei für jede Benutzeroberflächen Kultur.
1. Laden Sie die neuen CAB-Dateien an den Speicherort hoch, der durch den Wert des **helpcontenturi** -Elements in der helpinfo-XML-Datei angegeben wird. Ersetzen Sie die älteren CAB-Dateien durch die neuen CAB-Dateien.
1. Laden Sie die aktualisierte helpinfo-XML-Datei an den Speicherort hoch, der durch den **helpinfouri** -Schlüssel im Modul Manifest angegeben wird. Ersetzen Sie die ältere helpinfo-XML-Datei durch die neue Datei.
