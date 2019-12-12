---
title: Erstellen einer helpinfo-XML-Datei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367319"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>Erstellen einer XML-Datei HelpInfo

In diesen Themen in diesem Abschnitt wird erläutert, wie Sie eine Hilfe Informationsdatei erstellen und Auffüllen, die im Allgemeinen als "helpinfo-XML-Datei" bezeichnet wird, für das Windows PowerShell-Feature zur aktualisierbaren Hilfe.

## <a name="helpinfo-xml-file-overview"></a>Hilfe zur helpinfo-XML-Datei

Die helpinfo-XML-Datei ist die primäre Quelle von Informationen über die aktualisierbare Hilfe für das Modul. Sie enthält den Speicherort der Hilfedateien für die Module, die unterstützten Benutzeroberflächen Kulturen und die Versionsnummern, die von der aktualisierbaren Hilfe verwendet werden, um zu bestimmen, ob der Benutzer über die neuesten Hilfedateien verfügt.

Jedes Modul verfügt nur über eine helpinfo-XML-Datei, auch wenn das Modul mehrere Hilfedateien für mehrere Benutzeroberflächen Kulturen enthält. Der Modul Autor erstellt die helpinfo-XML-Datei und legt Sie an dem Internet Speicherort ab, der durch den **helpinfouri** -Schlüssel im Modul Manifest angegeben wird. Wenn die Modul Hilfedateien aktualisiert und hochgeladen werden, aktualisiert der Modul Autor die helpinfo-XML-Datei und ersetzt die ursprüngliche helpinfo-XML-Datei durch die neue Version.

Es ist wichtig, dass die helpinfo-XML-Datei sorgfältig verwaltet wird. Wenn Sie neue Dateien hochladen, aber vergessen, die Versionsnummern zu erhöhen, werden die neuen Dateien von der aktualisierbaren Hilfe nicht auf die Benutzer Computer heruntergeladen. Wenn Sie Hilfedateien für eine neue Benutzeroberflächen Kultur hinzufügen, aber die helpinfo-XML-Datei nicht aktualisieren oder am richtigen Speicherort platzieren, werden die neuen Dateien durch die aktualisierbare Hilfe nicht heruntergeladen.

## <a name="in-this-section"></a>Inhalt dieses Abschnitts

In diesem Abschnitt werden folgende Themen behandelt.

- [Helpinfo-XML-Schema](./helpinfo-xml-schema.md)

- [Helpinfo-XML-Beispieldatei](./helpinfo-xml-sample-file.md)

- [Benennen einer helpinfo-XML-Datei](./how-to-name-a-helpinfo-xml-file.md)

- [Festlegen der helpinfo-XML-Versionsnummern](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>Weitere Informationen

[Unterstützen aktualisierbarer Hilfe](./supporting-updatable-help.md)