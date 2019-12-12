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
ms.openlocfilehash: 5c5168ffd74c15066b914ad1b39d9ead947c5e7f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365119"
---
# <a name="loading-and-exporting-formatting-data"></a>Laden und Exportieren von Formatierungsdaten

Nachdem Sie die Formatierungs Datei erstellt haben, müssen Sie die Format Daten der Sitzung aktualisieren, indem Sie Ihre Dateien in die aktuelle Sitzung laden. (Die Formatierungs Dateien, die von Windows PowerShell bereitgestellt werden, werden von Snap-Ins geladen, die registriert werden, wenn die aktuelle Sitzung geöffnet wird.) Nachdem die Format Daten der aktuellen Sitzung aktualisiert wurden, werden diese Daten von Windows PowerShell verwendet, um die .NET-Objekte anzuzeigen, die den in den geladenen Formatierungs Dateien definierten Sichten zugeordnet sind. Es gibt keine Beschränkung für die Anzahl der Formatierungs Dateien, die Sie in die aktuelle Sitzung laden können. Zusätzlich zum Aktualisieren der Formatierungsdaten können Sie die Formatierungsdaten in der aktuellen Sitzung zurück in eine Formatierungs Datei exportieren.

## <a name="loading-format-data"></a>Laden von Format Daten

Das Formatieren von Dateien kann mithilfe der folgenden Methoden in die aktuelle Sitzung geladen werden:

- Sie können die Formatierungs Datei von der Befehlszeile aus in die aktuelle Sitzung importieren. Verwenden Sie das [Update-formatdata-](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet, wie im folgenden Verfahren beschrieben.

- Sie können ein Modul Manifest erstellen, das auf Ihre Formatierungs Datei verweist. Mit Modulen können Sie die Formatierung von Dateien für die Verteilung verpacken. Verwenden Sie das [New-modulemanifest-](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) Cmdlet, um das Manifest zu erstellen, und das [Import-Module-](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet, um das Modul in die aktuelle Sitzung zu laden. Weitere Informationen zu Modulen finden Sie unter [Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md).

- Sie können ein Snap-in erstellen, das auf Ihre Formatierungs Datei verweist. Verwenden Sie " [System. Management. Automation. PSSnapIn. Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) ", um auf die Formatierungs Dateien zu verweisen. Es wird dringend empfohlen, Module zu verwenden, um Cmdlets und alle zugehörigen Formatierungs-und Typen Dateien für die Verteilung zu verpacken. Weitere Informationen zu Modulen finden Sie unter [Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md).

- Wenn Sie Befehle Programm gesteuert aufrufen, können Sie einen Formatierungs Datei Eintrag zum anfänglichen Sitzungs Status des Runspace hinzufügen, in dem die Befehle ausgeführt werden. Weitere Informationen zum .NET-Typ, der zum Hinzufügen der Formatierungs Datei verwendet wird, finden Sie unter [System. Management. Automation. Runspaces. sessionstateformatentry? Displayproperty = FullName](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) -Klasse.

Wenn eine Formatierungs Datei geladen wird, wird Sie einer internen Liste hinzugefügt, die Windows PowerShell verwendet, um zu bestimmen, welche Ansicht beim Anzeigen von Objekten in der Befehlszeile verwendet werden soll. Sie können die Formatierungs Datei am Anfang der Liste anfügen, oder Sie können Sie am Ende der Liste anfügen. Wenn Sie eine Formatierungs Datei laden, die eine Ansicht für ein Objekt definiert, für das eine vorhandene Sicht definiert ist, müssen Sie wissen, wo die Formatierungs Datei zu dieser Liste hinzugefügt wird, z. b. Wenn Sie ändern möchten, wie ein von einem Windows PowerShell Core-Cmdlet zurück gegebenes Objekt ist.  gestellte. Wenn Sie eine Formatierungs Datei laden, in der die einzige Ansicht für ein Objekt definiert ist, können Sie eine der zuvor beschriebenen Methoden verwenden.  Wenn Sie eine Formatierungs Datei laden, die eine andere Ansicht für ein Objekt definiert, müssen Sie das [Update-formatdata-](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet verwenden und die Datei am Anfang der Liste anfügen.

## <a name="storing-your-formatting-file"></a>Speichern der Formatierungs Datei

Es ist nicht erforderlich, dass die Formatierungs Dateien auf dem Datenträger gespeichert werden. Es wird jedoch dringend empfohlen, dass Sie diese im folgenden Ordner speichern: `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>Laden einer Format Datei mit Import-formatdata

1. Speichern Sie die Formatierungs Datei auf dem Datenträger.

2. Führen Sie das [Update-formatdata-](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet mit einem der folgenden Befehle aus.

   Verwenden Sie diesen Befehl, um die Formatierungs Datei am Anfang der Liste hinzuzufügen. Verwenden Sie diesen Befehl, wenn Sie ändern, wie ein Objekt angezeigt wird.

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   Verwenden Sie diesen Befehl, um die Formatierungs Datei am Ende der Liste hinzuzufügen.

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   Nachdem Sie mit dem [Update-formatdata-](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet eine Datei hinzugefügt haben, können Sie die Datei nicht aus der Liste entfernen, während die Sitzung geöffnet ist. Sie müssen die Sitzung schließen, um die Formatierungs Datei aus der Liste zu entfernen.

## <a name="exporting-format-data"></a>Exportieren von Format Daten

Abschnittstext hier einfügen.
