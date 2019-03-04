---
title: 'Gewusst wie: Importieren von Modulen mit Cmdlets | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859146"
---
# <a name="how-to-import-cmdlets-using-modules"></a>Importieren von Cmdlets mit Modulen

Dieses Thema beschreibt, wie Sie Cmdlets in einer Windows PowerShell-Sitzung zu importieren, mit einem binären Modul.

> [!NOTE]
> Die Elemente der Module zählen die Cmdlets, Anbieter, Funktionen, Variablen, Aliase und vieles mehr. -Snap-ins können nur Cmdlets und Anbieter enthalten.

## <a name="how-to-load-cmdlets-using-a-module"></a>Gewusst wie: Laden Sie ein Modul mit cmdlets

1. Erstellen Sie einen Ordner "Module", die den gleichen Namen wie die Assemblydatei hat in der die Cmdlets implementiert werden. In diesem Verfahren wird der Ordner "Module" erstellt, der `system32` Ordner.

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. Stellen Sie sicher, dass die `PSModulePath` Umgebungsvariable enthält den Pfad zu Ihrem Ordner "Module". Wird standardmäßig der Ordner "System" wurde bereits hinzugefügt der `PSModulePath` -Umgebungsvariablen angegeben.

3. Kopieren Sie die Cmdlet-Assembly, in dem Ordner "Module".

4. Führen Sie den folgenden Befehl zum Hinzufügen der Cmdlets für die Sitzung ein:

   `import-module [Module_Name]`

   Dieses Verfahren kann verwendet werden, um Ihre Cmdlets zu testen. Alle Cmdlets hinzugefügt in der Assembly mit der Sitzung. Weitere Informationen zu Modulen, die verschiedenen Arten von Modulen, die verschiedenen Methoden zum Laden von Modulen und wie Sie die Elemente eines Moduls zu beschränken, die exportiert werden, finden Sie unter [Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Installieren von Modulen](../module/installing-a-powershell-module.md)