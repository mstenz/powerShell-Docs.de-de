---
title: Konzepte für die Fehlerberichterstattung | Microsoft-Dokumentation
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364619"
---
# <a name="error-reporting-concepts"></a>Konzepte der Fehlerberichterstattung

Windows PowerShell bietet zwei Mechanismen zum Melden von Fehlern: einen Mechanismus zum *Beenden von Fehlern* und einen anderen Mechanismus für *Fehler ohne*Abbruch. Es ist wichtig, dass das Cmdlet Fehler ordnungsgemäß meldet, damit die Host Anwendung, die die Cmdlets ausführen, auf angemessene Weise reagieren kann.

Ihr Cmdlet sollte bei Auftreten eines Fehlers die [System. Management. Automation. Cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) -Methode aufgerufen werden, bei der das Cmdlet die Verarbeitung seiner Eingabe Objekte nicht zulässt. Ihr Cmdlet muss die [System. Management. Automation. Cmdlet. Write-error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode zum Melden von Fehlern ohne Abbruch verwenden, wenn das Cmdlet die Verarbeitung der Eingabe Objekte fortsetzen kann. Beide Methoden stellen einen Fehler Daten Satz bereit, der von der Host Anwendung verwendet werden kann, um die Ursache des Fehlers zu untersuchen.

Verwenden Sie die folgenden Richtlinien, um zu bestimmen, ob ein Fehler ein Abbruch Fehler oder ein Fehler ohne Abbruch ist.

- Ein Fehler ist ein Abbruch Fehler, wenn das Cmdlet verhindert, dass das aktuelle Objekt weiterhin verarbeitet wird oder wenn andere Eingabe Objekte unabhängig von Ihrem Inhalt erfolgreich verarbeitet werden.

- Ein Fehler ist ein Beendigungs Fehler, wenn Sie nicht möchten, dass das Cmdlet die Verarbeitung des aktuellen Objekts oder weiterer Eingabe Objekte, unabhängig von deren Inhalten, fortsetzt.

- Ein Fehler ist ein Abbruch Fehler, wenn er in einem Cmdlet auftritt, das ein Objekt nicht akzeptiert oder zurückgibt, oder wenn es in einem Cmdlet vorkommt, das nur ein Objekt akzeptiert oder zurückgibt.

- Ein Fehler ist ein Fehler ohne Abbruch, wenn Sie möchten, dass das Cmdlet die Verarbeitung des aktuellen Objekts und aller weiteren Eingabe Objekte fortsetzt.

- Ein Fehler ist ein Fehler ohne Abbruch, wenn er mit einem bestimmten Eingabe Objekt oder einer Teilmenge von Eingabe Objekten verknüpft ist.

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. Cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System. Management. Automation. Cmdlet. Write error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell-Fehler Datensätze](./windows-powershell-error-records.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
