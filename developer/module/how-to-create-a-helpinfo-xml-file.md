---
title: 'Vorgehensweise: erstellen eine HelpInfo-XML-Datei | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082412"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>Erstellen einer XML-Datei HelpInfo

Die Themen in diesem Abschnitt wird erläutert, wie zum Erstellen und Auffüllen einer hilfeinformationsdatei, häufig als "HelpInfo XML-Datei" für die Windows PowerShell aktualisierbare Hilfefunktion bezeichnet wird.

## <a name="helpinfo-xml-file-overview"></a>Übersicht über die HelpInfo-XML-Datei

Die HelpInfo XML-Datei ist die Hauptquelle für Informationen zur aktualisierbaren Hilfe für das Modul. Es enthält den Speicherort der Hilfedateien für Module, die unterstützten Benutzeroberflächenkulturen und die Versionsnummern, die aktualisierbare Hilfe verwendet, um zu bestimmen, ob der Benutzer die neuesten Hilfedateien.

Jedes Modul besitzt nur eine HelpInfo XML-Datei, selbst wenn das Modul mehrere Hilfedateien für mehrere UI-Kulturen enthält. Autor des Moduls die HelpInfo XML-Datei erstellt und platziert sie in dem Speicherort im Internet, die angegeben wird die **HelpInfoUri** -Schlüssels im modulmanifest. Wenn die Hilfedateien für Module aktualisiert und hochgeladen werden, wird den Autor des Moduls die HelpInfo XML-Datei aktualisiert und ersetzt die ursprüngliche HelpInfo XML-Datei mit der neuen Version.

Es ist wichtig, dass die HelpInfo XML-Datei sorgfältig beibehalten wird. Wenn Sie neue Dateien hochladen, aber vergessen, die Versionsnummern erhöht werden, werden aktualisierbare Hilfe nicht die neuen Dateien auf Computern der Benutzer heruntergeladen. Wenn Sie Hilfedateien für eine neue UI-Kultur, hinzufügen, aber nicht aktualisieren Sie die HelpInfo XML-Datei oder an der richtigen Speicherort zu platzieren, werden die neuen Dateien aktualisierbare Hilfe nicht herunterladen.

## <a name="in-this-section"></a>Inhalt dieses Abschnitts

In diesem Abschnitt werden folgende Themen behandelt.

- [HelpInfo-XML-Schema](./helpinfo-xml-schema.md)

- [HelpInfo-XML-Beispieldatei](./helpinfo-xml-sample-file.md)

- [Wie Sie eine HelpInfo-XML-Datei benennen](./how-to-name-a-helpinfo-xml-file.md)

- [Gewusst wie HelpInfo-XML-Versionsnummern](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>Weitere Informationen

[Unterstützung für aktualisierbare Hilfe](./supporting-updatable-help.md)