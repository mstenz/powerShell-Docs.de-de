---
title: Anzeigen von Fehlerinformationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858276"
---
# <a name="displaying-error-information"></a>Anzeigen von Fehlerinformationen

Dieses Thema beschreibt die Möglichkeiten, in denen Benutzer Informationen anzeigen können.

Wenn Ihr Cmdlet ein Fehler auftritt, wird die Präsentation der Fehlerinformationen die folgende Fehlerausgabe in der Standardeinstellung entsprechen.

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

Benutzer können jedoch anzeigen Fehler nach Kategorie durch Festlegen der `$ErrorView` Variable `"CategoryView"`. Kategorieansicht werden spezifische Informationen über die Error-Datensatzes und nicht über eine Freitext-Beschreibung des Fehlers. In dieser Ansicht kann nützlich sein, wenn man eine lange Liste von Fehlern zu überprüfen. In der Kategorieansicht wird die vorherigen Fehlermeldung wie folgt angezeigt.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

Weitere Informationen zu den Fehlerkategorien finden Sie unter [Windows PowerShell-Fehlerdatensätze](./windows-powershell-error-records.md).

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell-Error-Datensätze](./windows-powershell-error-records.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
