---
title: Importieren eines PowerShell-Moduls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 697791b3-2135-4a39-b9d7-8566ed67acf2
caps.latest.revision: 13
ms.openlocfilehash: bb5d036e5658c365a4fafa2cac05c0bba9f87019
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082243"
---
# <a name="importing-a-powershell-module"></a>Importieren eines PowerShell-Moduls

Nach Ihrer installiert ein Modul auf einem System, Sie möchten wahrscheinlich das Modul zu importieren. Das Importieren ist der Prozess, der das Modul in den aktiven Arbeitsspeicher geladen, damit ein Benutzer das Modul in ihrer PowerShell-Sitzung zugreifen kann. Sie können in PowerShell 2.0 mit einem Aufruf von einem neu installierten PowerShell-Modul importieren [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet. PowerShell kann in PowerShell 3.0 wird implizit ein Modul importieren, wenn eine der Funktionen oder Cmdlets im Modul von einem Benutzer aufgerufen wird. Beachten Sie, dass beide Versionen wird davon ausgegangen, dass Sie Ihr Modul an einem Standort installieren, in dem PowerShell suchen kann. Weitere Informationen finden Sie unter [Installieren eines PowerShell-Moduls](./installing-a-powershell-module.md). Sie können ein modulmanifest verwenden, um einzuschränken, welche Teile Ihres Moduls exportiert werden, und Sie können Parameter der `Import-Module` Aufruf, um einzuschränken, welche Teile importiert werden.

## <a name="importing-a-snap-in-powershell-10"></a>Importieren ein Snap-In (PowerShell 1.0)

Module in PowerShell 1.0 nicht existieren: stattdessen mussten Sie registrieren und Verwenden von-Snap-ins. Allerdings wird nicht empfohlen, dass Sie diese Technologie an diesem Punkt verwenden wie Module im Allgemeinen leichter sind zu installieren und zu importieren. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen Sie ein Windows PowerShell-Snap-in](../cmdlet/how-to-create-a-windows-powershell-snap-in.md).

## <a name="importing-a-module-with-import-module-powershell-20"></a>Importieren eines Moduls mit Import-Module (PowerShell 2.0)

PowerShell 2.0 verwendet den entsprechend benannten [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet, um Module zu importieren. Wenn dieses Cmdlet ausgeführt wird, durchsucht Windows PowerShell für das angegebene Modul in den Verzeichnissen, die im angegebenen die `PSModulePath` Variable. Wenn das angegebene Verzeichnis gefunden wird, wird Windows PowerShell nach Dateien in der folgenden Reihenfolge gesucht: modulmanifestdatei (psd1), skriptmoduldateien (psm1), binäre Moduldateien (.dll). Weitere Informationen zu Hinzufügen von Verzeichnissen zum Suchen, finden Sie unter [ändern den Installationspfad PSModulePath](./modifying-the-psmodulepath-installation-path.md). Der folgende Code zeigt, wie Sie ein Modul zu importieren:

```powershell
Import-Module myModule
```

Unter der Annahme, dass MyModule gefunden wurde die `PSModulePath`, PowerShell MyModule in den aktiven Arbeitsspeicher lädt. Wenn MyModule befand sich nicht auf eine `PSModulePath` Pfad, Sie können immer noch explizit angewiesen PowerShell wo Sie sich befindet:

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

Sie können auch den - verbose-Parameter zum Identifizieren, was aus dem Modul exportiert wird, und was in den aktiven Arbeitsspeicher importiert wird. Sowohl Exporte und Importe einschränken, was für den Benutzer verfügbar gemacht wird: der Unterschied besteht darin, die die Sichtbarkeit gesteuert wird. Im Wesentlichen werden die Exporte von Code innerhalb des Moduls gesteuert. Im Gegensatz dazu werden Importe gesteuert, von der `Import-Module` aufrufen. Weitere Informationen finden Sie unter **einschränken Mitglieder, importiert**weiter unten.

## <a name="implicitly-importing-a-module-powershell-30"></a>Implizit Importieren eines Moduls (PowerShell 3.0)

Ab Windows PowerShell 3.0 werden Module automatisch importiert, wenn ein Cmdlet oder eine Funktion im Modul in einem Befehl verwendet wird. Dieses Feature funktioniert für jedes Modul in einem Verzeichnis, das diese in den Wert des enthalten die **PSModulePath** -Umgebungsvariablen angegeben. Wenn Sie nicht Ihr Modul auf einen gültigen Pfad jedoch speichern, Sie können weiterhin einen Auslastungstest mit der expliziten [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Option oben beschriebenen.

Die folgenden Aktionen auslösen, automatischen Importieren eines Moduls, auch bekannt als "Modul automatisch geladen."

- Verwenden ein Cmdlet in einem Befehl. Geben Sie z. B. `Get-ExecutionPolicy` importiert das Microsoft.PowerShell.Security-Modul, enthält die `Get-ExecutionPolicy` Cmdlet.

- Mithilfe der [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) -Cmdlet zum Abrufen des-Befehls.  Geben Sie z. B. `Get-Command Get-JobTrigger` importiert die **PSScheduledJob** -Modul, enthält die `Get-JobTrigger` Cmdlet. Ein `Get-Command` -Befehl, der Platzhalterzeichen enthält, als Ermittlung werden betrachtet, und Importieren eines Moduls wird nicht ausgelöst.

- Mithilfe der [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) -Cmdlet zum Abrufen von Hilfe für ein Cmdlet. Geben Sie z. B. `Get-Help Get-WinEvent` importiert das Microsoft.PowerShell.Diagnostics-Modul, enthält die `Get-WinEvent` Cmdlet.

Zur Unterstützung der automatische Import von Modulen, die `Get-Command` Cmdlet Ruft alle Cmdlets und Funktionen in allen installierten Modulen ab, selbst wenn das Modul nicht in die Sitzung importiert wird. Weitere Informationen finden Sie im Hilfethema für das [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) Cmdlet.

## <a name="the-importing-process"></a>Der Prozess importieren

Wenn ein Modul importiert wird, wird ein neue Sitzungszustand für das Modul erstellt und ein [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) Objekt im Arbeitsspeicher erstellt wird. Status eine Sitzung wird erstellt für jedes Modul, das importiert wird (Dies schließt das stammmodul und alle geschachtelten Module). Die Elemente, die exportiert werden, aus dem Root-Modul, einschließlich der Mitglieder, die in der Root-Modul, indem Sie geschachtelte Module, exportiert wurden, werden dann in Sitzungsstatus des Aufrufers importiert.

Die Metadaten der Elemente, die von einem Modul exportiert werden müssen eine ModuleName-Eigenschaft. Diese Eigenschaft wird durch den Namen des Moduls aufgefüllt, die sie exportiert haben.

> [!WARNING]
> Wenn der Name eines exportierte Members ein nicht genehmigtes Verb verwendet oder eine Warnung, wenn der Name des Members eingeschränkte Zeichen verwendet angezeigt wird, wenn die [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet ausgeführt wird.

In der Standardeinstellung die [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet keine Objekte an die Pipeline zurück. Das Cmdlet unterstützt jedoch eine `PassThru` Parameter, der verwendet werden kann, um zurückzugeben eine [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) Objekt für jedes Modul, das importiert wird. Um die Ausgabe an den Host zu senden, die Benutzer ausführen sollte die [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) Cmdlet.

## <a name="restricting--the-members-that-are-imported"></a>Beschränken die Elemente, die importiert werden

Beim Importieren eines Moduls mit der [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) -Cmdlet standardmäßig alle exportierter Module, die Elemente werden in der Sitzung importiert einschließlich keine Befehle exportiert an das Modul durch ein geschachteltes Modul. Variablen und Aliase werden standardmäßig nicht exportiert. Um die Elemente einzuschränken, die exportiert werden, verwenden eine [modulmanifest](./how-to-write-a-powershell-module-manifest.md). Um die Elemente zu beschränken, die importiert werden, verwenden Sie die folgenden Parameter von der `Import-Module` Cmdlet.

- `Function`: Dieser Parameter schränkt die Funktionen, die exportiert werden. (Wenn Sie ein modulmanifest verwenden, finden Sie unter dem Schlüssel "functionstoexport".)

- `Cmdlet`: Dieser Parameter schränkt die-Cmdlets, die exportiert werden (Wenn Sie einer Modul Anwendungsmanifest ist, finden Sie unter den CmdletsToExport Schlüssel verwenden.)

- `Variable`: Dieser Parameter schränkt die Variablen, die exportiert werden (Wenn Sie einer Modul Anwendungsmanifest ist, finden Sie unter den VariablesToExport Schlüssel verwenden.)

- `Alias`: Dieser Parameter schränkt die Aliase, die exportiert werden (Wenn Sie einer Modul Anwendungsmanifest ist, finden Sie unter den AliasesToExport Schlüssel verwenden.)

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Moduls](./writing-a-windows-powershell-module.md)
