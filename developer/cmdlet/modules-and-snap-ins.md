---
title: Module und Snap-ins | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860496"
---
# <a name="modules-and-snap-ins"></a>Module und Snap-Ins

Cmdlets können per (von Windows PowerShell 2.0 eingeführt) Module oder Snap-ins zu einer Sitzung hinzugefügt werden. Sobald das-Cmdlet mit der Sitzung hinzugefügt wird, die sie programmgesteuert von einer hostanwendung oder interaktiv in der Befehlszeile ausgeführt werden kann.

Es wird empfohlen, als die Übermittlungsmethode für das Hinzufügen von Cmdlets zu einer Sitzung den folgenden Gründen Module zu verwenden:

- Module können Cmdlets hinzufügen, indem Sie das Laden der Assembly, in dem das Cmdlet definiert ist. Es ist nicht erforderlich, eine Snap-in-Klasse zu implementieren.

- Module können Sie andere Ressourcen, z. B. Variablen, Funktionen, Skripts, Typen und Formatierung Dateien und mehr hinzuzufügen.

- -Snap-ins kann verwendet werden, nur für Cmdlets und Anbieter zur Sitzung hinzufügen.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
