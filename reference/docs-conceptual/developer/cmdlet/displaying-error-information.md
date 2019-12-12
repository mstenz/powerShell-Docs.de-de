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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369969"
---
# <a name="displaying-error-information"></a>Anzeigen von Fehlerinformationen

In diesem Thema wird erläutert, wie Benutzerfehler Informationen anzeigen können.

Wenn das Cmdlet auf einen Fehler stößt, wird die Darstellung der Fehlerinformationen standardmäßig der folgenden Fehlerausgabe ähneln.

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

Allerdings können Benutzerfehler nach Kategorie anzeigen, indem Sie die `$ErrorView` Variable auf `"CategoryView"`festlegen. In der Kategorieansicht werden bestimmte Informationen aus dem Fehler Daten Satz und nicht eine frei Textbeschreibung des Fehlers angezeigt. Diese Ansicht kann nützlich sein, wenn Sie über eine lange Liste der zu überprüfenden Fehler verfügen. In der Kategorieansicht wird die vorherige Fehlermeldung wie folgt angezeigt.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

Weitere Informationen zu Fehlerkategorien finden Sie unter [Windows PowerShell-Fehler Datensätze](./windows-powershell-error-records.md).

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell-Fehler Datensätze](./windows-powershell-error-records.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
