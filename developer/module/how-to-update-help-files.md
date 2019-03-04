---
title: Vorgehensweise beim Aktualisieren von Hilfedateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855526"
---
# <a name="how-to-update-help-files"></a>Aktualisieren von Hilfedateien

In diesem Thema wird erläutert, wie Hilfedateien für ein Modul zu aktualisieren, die aktualisierbare Hilfe unterstützt wird.

## <a name="updating-help-files"></a>Aktualisieren von Hilfedateien

Es gibt viele Gründe, um Hilfedateien vorhanden sind, z. B. das Beheben von Fehlern, Klärung ein Konzept, eine häufig gestellte Frage zu beantworten, neue Dateien hinzufügen oder Hinzufügen von neuen, besseren Beispiele zu aktualisieren.

So aktualisieren Sie eine Textdatei:

1. Ändern Sie die Dateien an.

2. Die Dateien in anderen UI-Kulturen übersetzt.

3. Sammeln Sie alle Hilfedateien (neuer, geänderter und nicht geändert) für das Modul in jede Benutzeroberflächenkultur an.

4. Überprüfen Sie die Dateien anhand des XML-Schemas.

5. Erstellen Sie die CAB-Dateien für jede Benutzeroberflächenkultur neu.

6. Erhöhen Sie in der HelpInfo-XML-Datendatei die Versionsnummern der CAB-Datei für jede Benutzeroberflächenkultur.

7. Die neuen CAB-Dateien hochzuladen, zu dem Speicherort, der durch den Wert der angegeben wird die **HelpContentUri** Element in der HelpInfo XML-Datei. Ersetzen Sie die ältere CAB-Dateien, durch die neuen CAB-Dateien.

8. Die aktualisierte HelpInfo XML-Datei hoch, mit der angegebenen die **HelpInfoUri** -Schlüssels im modulmanifest. Ersetzen Sie die ältere HelpInfo XML-Datei mit der neuen Datei ein.