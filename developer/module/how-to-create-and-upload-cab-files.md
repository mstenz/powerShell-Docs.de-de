---
title: Das Erstellen und Hochladen der CAB-Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082378"
---
# <a name="how-to-create-and-upload-cab-files"></a>Erstellen und Hochladen von CAB-Dateien

In diesem Thema erläutert die aktualisierbare Hilfe-CAB-Dateien erstellen und Hochladen in den Speicherort, in denen die Cmdlets der aktualisierbaren Hilfe diese finden können.

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>Das Erstellen und Hochladen der CAB-Dateien für aktualisierbare Hilfe

Sie können die aktualisierbare Hilfefunktion verwenden, um neue oder aktualisierte Hilfedateien für ein Modul in mehreren Sprachen und Kulturen zu übermitteln. Ein Paket der aktualisierbaren Hilfe für ein Modul besteht aus einer HelpInfo XML-Datei und eine oder mehrere CAB-Datei (. CAB-Datei)-Dateien. Jede CAB-Datei enthält die Hilfedateien für das Modul in einem UI-Kultur. Verwenden Sie das folgende Verfahren zum Erstellen von CAB-Dateien für aktualisierbare Hilfe an.

1. Organisieren Sie die Hilfedateien für das Modul, indem Sie UI-Kultur. Jede aktualisierbare Hilfe CAB-Datei enthält die Hilfedateien für ein Modul in einem UI-Kultur. Sie können mehrere Hilfe CAB-Dateien für das Modul für eine andere UI-Kultur übermitteln.

2. Stellen Sie sicher, die Hilfedateien enthalten nur die Dateitypen, die für aktualisierbare Hilfe werden dürfen, und überprüfen sie anhand eines Schemas der Hilfe-Datei. Wenn die `Update-Help` Cmdlet auftritt, eine Datei ist ungültig, oder ist kein zulässiger Typ ist, wird die ungültige Datei wird nicht installiert, und beendet die Installation von Dateien aus der CAB-Datei. Eine Liste der zulässigen Dateitypen, finden Sie unter [Datei Typen zulässig, in eine aktualisierbare Hilfe CAB-Datei](./file-types-permitted-in-an-updatable-help-cab-file.md).

3. Signieren Sie die Hilfedateien aus. Digitale Signaturen sind nicht erforderlich, aber sie sind eine bewährte Methode.

4. Umfassen Sie alle der Hilfe für das Modul in der Benutzeroberfläche Kultur, nicht nur die Dateien, die neu sind oder geändert wurden. Wenn die CAB-Datei nicht vollständig ist, werden Benutzer, die Hilfedateien zum ersten Mal laden oder jede Aktualisierung nicht herunterladen keine aller Modul Hilfedateien vorhanden sind.

5. Verwenden Sie ein Hilfsprogramm, das CAB-Dateien, z. B. MakeCab.exe erstellt. Windows PowerShell umfasst keine Cmdlets, die CAB-Dateien zu erstellen.

6. Benennen Sie die CAB-Dateien. Weitere Informationen finden Sie unter [eine aktualisierbare Hilfe CAB-Datei benennen](./how-to-name-an-updatable-help-cab-file.md).

7. Hochladen der CAB-Dateien für das Modul mit der angegebenen die **HelpContentUri** Element in der HelpInfo-XML-Datendatei für das Modul. Klicken Sie dann die HelpInfo XML-Datei hochladen, mit der angegebenen die **HelpInfoUri** des modulmanifests Schlüssel. Die **HelpContentUri** und **HelpInfoUri** kann an denselben Speicherort zeigen.

> [!CAUTION]
> Der Wert des der **HelpInfoUri** Schlüssel und die **HelpContentUri** Element muss mit "http" oder "Https" beginnen. Der Wert muss einen Speicherort im Internet angeben, und es dürfen keinen Dateinamen an.