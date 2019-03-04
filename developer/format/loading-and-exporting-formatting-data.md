---
title: Laden und Exportieren von Formatierungsdaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 08c64d4094d8ba6c551b454887331666f0694f11
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860626"
---
# <a name="loading-and-exporting-formatting-data"></a>Laden und Exportieren von Formatierungsdaten

Nachdem Sie Ihre Formatierungsdatei erstellt haben, müssen Sie die Daten im Format der Sitzung zu aktualisieren, indem Sie Ihre Dateien in der aktuellen Sitzung zu laden. (Die Formatierungsdateien, die von Windows PowerShell bereitgestellt, werden von-Snap-ins, die registriert werden, wenn die aktuelle Sitzung geöffnet wird geladen.) Nachdem die Daten im Format der aktuellen Sitzung aktualisiert wurde, verwendet Windows PowerShell die Daten zum Anzeigen der .NET Objekte, die in den geladenen Formatierungsdateien definierten Sichten zugeordnet. Es gibt keine Beschränkung der Anzahl der Formatierungsdateien, die Sie in der aktuellen Sitzung laden können. Zusätzlich zum Aktualisieren der Formatierungsdaten, können Sie die Formatdaten in der aktuellen Sitzung an eine Formatierungsdatei exportieren.

## <a name="loading-format-data"></a>Laden von Daten im format

Die aktuelle Sitzung mithilfe der folgenden Methoden können Formatierungsdateien geladen werden:

- Sie können die Formatierungsdatei in der aktuellen Sitzung über die Befehlszeile importieren. Verwenden der [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet wie im folgenden Verfahren beschrieben.
- Sie können die Formatierungsdatei in der aktuellen Sitzung über die Befehlszeile importieren. Verwenden der [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet wie im folgenden Verfahren beschrieben.

- Sie können ein modulmanifest erstellen, die die Formatierung Datei verweist. Module können Sie die Formatierungsdateien für die Verteilung verpacken. Verwenden der [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) Cmdlet, um das Manifest zu erstellen und die [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet, um das Modul in die aktuelle Sitzung zu laden. Weitere Informationen zu Modulen finden Sie unter [Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md).
- Sie können ein modulmanifest erstellen, die die Formatierung Datei verweist. Module können Sie die Formatierungsdateien für die Verteilung verpacken. Verwenden der [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) Cmdlet, um das Manifest zu erstellen und die [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet, um das Modul in die aktuelle Sitzung zu laden. Weitere Informationen zu Modulen finden Sie unter [Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md).

- Sie können ein Snap-in erstellen, die die Formatierung Datei verweist. Verwenden der [System.Management.Automation.Pssnapin.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) auf Ihre Formatierungsdateien verweisen. Es wird dringend empfohlen, Module, die Paket-Cmdlets und zugeordnete Formatierung und Typen-Dateien für die Verteilung zu verwenden. Weitere Informationen zu Modulen finden Sie unter [Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md).

- Wenn Sie Befehle programmgesteuert aufrufen, können Sie einen Eintrag mit Formatierung Datei auf den anfänglichen Sitzungsstatus, der den Runspace hinzufügen, in dem die Befehle ausgeführt werden. Weitere Informationen zu .NET verwendet, um die Formatierungsdatei hinzuzufügen, finden Sie unter den [System.Management.Automation.Runspaces.Sessionstateformatentry? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) Klasse.

Wenn eine Formatierungsdatei geladen wird, wird einer internen Liste hinzugefügt, dass Windows PowerShell verwendet, um zu bestimmen, welche Ansicht in die bei der Anzeige von Objekten in der Befehlszeile verwendet. Können Sie Ihre Formatierungsdatei an den Anfang der Liste voranstellen, oder Sie fügen sie am Ende der Liste. Zu wissen, wo Ihre Formatierungsdatei zu dieser Liste hinzugefügt wird ist wichtig, wenn Sie Formatierungsdatei, die eine Ansicht für ein Objekt, die eine vorhandene Ansicht, die definiert laden definiert, wie z. B. Wenn Sie ändern, wie ein Objekt, das durch ein Windows PowerShell Core Cmdlet zurückgegeben wird wird möchten  angezeigt. Wenn Sie eine Formatierungsdatei, die die einzige Ansicht für ein Objekt definiert laden, können Sie eine der oben beschriebenen Methoden.  Wenn Sie eine Formatierungsdatei, die einer anderen Ansicht für ein Objekt definiert laden, müssen Sie verwenden die [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet, und stellen Sie die Datei auf den Anfang der Liste.
Wenn eine Formatierungsdatei geladen wird, wird einer internen Liste hinzugefügt, dass Windows PowerShell verwendet, um zu bestimmen, welche Ansicht in die bei der Anzeige von Objekten in der Befehlszeile verwendet. Können Sie Ihre Formatierungsdatei an den Anfang der Liste voranstellen, oder Sie fügen sie am Ende der Liste. Zu wissen, wo Ihre Formatierungsdatei zu dieser Liste hinzugefügt wird ist wichtig, wenn Sie Formatierungsdatei, die eine Ansicht für ein Objekt, die eine vorhandene Ansicht, die definiert laden definiert, wie z. B. Wenn Sie ändern, wie ein Objekt, das durch ein Windows PowerShell Core Cmdlet zurückgegeben wird wird möchten  angezeigt. Wenn Sie eine Formatierungsdatei, die die einzige Ansicht für ein Objekt definiert laden, können Sie eine der oben beschriebenen Methoden.  Wenn Sie eine Formatierungsdatei, die einer anderen Ansicht für ein Objekt definiert laden, müssen Sie verwenden die [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet, und stellen Sie die Datei auf den Anfang der Liste.

## <a name="storing-your-formatting-file"></a>Speichern Ihre Formatierungsdatei

Besteht keine Notwendigkeit, in dem Ihre Formatierungsdateien auf dem Datenträger gespeichert werden. Jedoch wird dringend empfohlen, dass Sie sie in den folgenden Ordner speichern: `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>Laden eine Formatdatei mit Import-FormatData

1. Store Ihre Formatierungsdatei auf dem Datenträger.

2. Führen Sie die [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet mit einem der folgenden Befehle aus.
2. Führen Sie die [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet mit einem der folgenden Befehle aus.

   Verwenden Sie diesen Befehl, um Ihre Formatierung hinzufügen Datei am Anfang der Liste. Verwenden Sie diesen Befehl aus, wenn Sie ändern möchten, wie ein Objekt angezeigt wird.

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   Verwenden Sie diesen Befehl, um Ihre Formatierung hinzufügen Datei am Ende der Liste.

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   Nachdem Sie eine Datei mit hinzugefügt, haben die [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) -Cmdlet, Sie können nicht entfernen Sie die Datei aus der Liste während die Sitzung geöffnet ist. Schließen Sie die Sitzung, um die Formatierungsdatei aus der Liste zu entfernen.
   Nachdem Sie eine Datei mit hinzugefügt, haben die [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) -Cmdlet, Sie können nicht entfernen Sie die Datei aus der Liste während die Sitzung geöffnet ist. Schließen Sie die Sitzung, um die Formatierungsdatei aus der Liste zu entfernen.

## <a name="exporting-format-data"></a>Exportieren von Daten im format

Abschnittstext hier einfügen.
