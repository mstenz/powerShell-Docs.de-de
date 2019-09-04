---
title: Importieren von Cmdlets mithilfe von Modulen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/28/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: 2f145795a57c988da0cb4ed294142aa141c53cae
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215274"
---
# <a name="how-to-import-cmdlets-using-modules"></a>Importieren von Cmdlets mit Modulen

In diesem Artikel wird beschrieben, wie Sie Cmdlets mithilfe eines binären Moduls in eine PowerShell-Sitzung importieren.

> [!NOTE]
> Die Member von Modulen können Cmdlets, Anbieter, Funktionen, Variablen, Aliase und vieles mehr enthalten. Snap-Ins können nur Cmdlets und Anbieter enthalten.

## <a name="how-to-load-cmdlets-using-a-module"></a>Vorgehensweise beim Laden von Cmdlets mithilfe eines Moduls

1. Erstellen Sie einen Modul Ordner, der denselben Namen hat wie die Assemblydatei, in der die Cmdlets implementiert sind. In diesem Verfahren wird der Modul Ordner im Windows `system32` -Ordner erstellt.

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. Stellen Sie sicher, `PSModulePath` dass die Umgebungsvariable den Pfad zum neuen Modul Ordner enthält. Standardmäßig ist der Systemordner bereits der `PSModulePath` Umgebungsvariablen hinzugefügt. Geben Sie zum `PSModulePath`Anzeigen von Folgendes `$env:PSModulePath`ein:.

1. Kopieren Sie die Cmdlet-Assembly in den Modul Ordner.

1. Fügen Sie im Stamm Ordner des`.psd1`Moduls eine Modul Manifest-Datei () hinzu. PowerShell verwendet das Modul Manifest, um das Modul zu importieren. Weitere Informationen finden Sie unter Gewusst [wie: Schreiben eines PowerShell-Modul Manifests](../module/how-to-write-a-powershell-module-manifest.md).

1. Führen Sie den folgenden Befehl aus, um der Sitzung die Cmdlets hinzuzufügen:

   `Import-Module [Module_Name]`

   Mithilfe dieses Verfahrens können Sie die Cmdlets testen. Der Sitzung werden alle Cmdlets in der Assembly hinzugefügt. Weitere Informationen zu Modulen finden Sie unter [Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Siehe auch

[Schreiben eines PowerShell-Modul Manifests](../module/how-to-write-a-powershell-module-manifest.md)

[Importieren eines PowerShell-Moduls](../module/importing-a-powershell-module.md)

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[Installieren von Modulen](../module/installing-a-powershell-module.md)

[Ändern des psmodulepath-Installations Pfads](../module/modifying-the-psmodulepath-installation-path.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
