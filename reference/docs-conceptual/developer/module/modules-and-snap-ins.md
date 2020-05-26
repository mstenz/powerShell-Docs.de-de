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
ms.openlocfilehash: b3d8209ea7e3e8353e73ebce1531991ec9519c74
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811659"
---
# <a name="modules-and-snap-ins"></a>Module und Snap-Ins

Cmdlets können einer Sitzung mithilfe von Modulen (eingeführt von Windows PowerShell 2,0) oder Snap-Ins hinzugefügt werden. Nachdem das Cmdlet der Sitzung hinzugefügt wurde, kann es Programm gesteuert von einer Host Anwendung oder interaktiv in der Befehlszeile ausgeführt werden.

Es wird empfohlen, Module als Übermittlungs Methode zum Hinzufügen von Cmdlets zu einer Sitzung aus den folgenden Gründen zu verwenden:

- Mit Modulen können Sie Cmdlets hinzufügen, indem Sie die Assembly laden, in der das Cmdlet definiert ist. Es ist nicht erforderlich, eine Snap-in-Klasse zu implementieren.

- Mit Modulen können Sie weitere Ressourcen hinzufügen, z. b. Variablen, Funktionen, Skripts, Typen und Formatierungs Dateien.

- Snap-Ins können nur zum Hinzufügen von Cmdlets und Anbietern zur Sitzung verwendet werden.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Moduls](writing-a-windows-powershell-module.md)

[Schreiben eines Windows PowerShell-Cmdlets](../cmdlet/cmdlet-overview.md)
