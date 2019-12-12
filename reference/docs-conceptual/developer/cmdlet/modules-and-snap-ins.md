---
title: Module und Snap-Ins | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365369"
---
# <a name="modules-and-snap-ins"></a>Module und Snap-Ins

Cmdlets können einer Sitzung mithilfe von Modulen (eingeführt von Windows PowerShell 2,0) oder Snap-Ins hinzugefügt werden. Nachdem das Cmdlet der Sitzung hinzugefügt wurde, kann es Programm gesteuert von einer Host Anwendung oder interaktiv in der Befehlszeile ausgeführt werden.

Es wird empfohlen, Module als Übermittlungs Methode zum Hinzufügen von Cmdlets zu einer Sitzung aus den folgenden Gründen zu verwenden:

- Mit Modulen können Sie Cmdlets hinzufügen, indem Sie die Assembly laden, in der das Cmdlet definiert ist. Es ist nicht erforderlich, eine Snap-in-Klasse zu implementieren.

- Mit Modulen können Sie weitere Ressourcen hinzufügen, z. b. Variablen, Funktionen, Skripts, Typen und Formatierungs Dateien.

- Snap-Ins können nur zum Hinzufügen von Cmdlets und Anbietern zur Sitzung verwendet werden.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
