---
title: Fehler, die Konzepte der Berichterstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: 2f185e415e3effc2cf09a282ca1167e3bcfb7d6a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054406"
---
# <a name="error-reporting-concepts"></a>Konzepte der Fehlerberichterstattung

Windows PowerShell bietet zwei Mechanismen zum Melden von Fehlern: ein Mechanismus zum *Fehler beenden* und einen anderen Mechanismus für die *Fehler ohne Abbruch*. Es ist richtig, damit die hostanwendung, die Ihre Cmdlets ausgeführt wird, in geeigneter Weise reagieren kann wichtig für Ihre Cmdlets aus, um Fehler zu melden.

Sollte Ihr Cmdlet rufen Sie die [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) Methode, wenn ein Fehler auftritt, nicht, oder das-Cmdlet verarbeitet Eingabeobjekte weiterhin sollten nicht zulassen. Ihr Cmdlet aufrufen, sollte die [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) Methode zum Melden Fehler ohne Abbruch, wenn das Cmdlet die Eingabeobjekte Verarbeitung fortgesetzt werden kann. Beide Methoden bieten einen Fehlerdatensatz, den die hostanwendung verwenden können, um die Ursache des Fehlers untersuchen.

Verwenden Sie die folgenden Richtlinien, um zu bestimmen, ob ein Fehler ist ein Abbruch oder Fehler ohne Abbruch.

- Ein Fehler ist ein Fehler mit Abbruch an, wenn sie Ihr Cmdlet nicht fortgesetzt werden kann, um das aktuelle Objekt zu verarbeiten oder erfolgreich verarbeitet alle weiteren Eingabeobjekte, unabhängig von deren Inhalt verhindert.

- Ein Fehler ist ein Fehler mit Abbruch, wenn Sie nicht Ihr Cmdlet und weiter verarbeitet werden, das aktuelle Objekt oder weitere Eingabeobjekten, unabhängig von deren Inhalt möchten.

- Ein Fehler ist ein Fehler mit Abbruch an, oder wenn sie ein Cmdlet generiert wird, die nicht akzeptieren, oder Sie geben ein Objekt zurück, wenn es sich in einem Cmdlet auftritt, das akzeptiert oder gibt nur ein Objekt zurück.

- Ein Fehler ist ein Fehler ohne Abbruch, sollten Sie dem Cmdlet das aktuelle Objekt und alle weiteren Eingabeobjekte die Verarbeitung fortgesetzt.

- Ein Fehler ist ein Fehler ohne Abbruch, wenn er eine bestimmte input-Objekt oder eine Teilmenge der Eingabeobjekte verknüpft ist.

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell-Error-Datensätze](./windows-powershell-error-records.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
