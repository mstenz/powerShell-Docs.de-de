---
title: Importieren eines PowerShell-Moduls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/03/2020
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 697791b3-2135-4a39-b9d7-8566ed67acf2
caps.latest.revision: 13
ms.openlocfilehash: d5ce61a1cba1d91c130394c5cf7249021e95f485
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996023"
---
# <a name="importing-a-powershell-module"></a>Importieren eines PowerShell-Moduls

Wenn Sie ein Modul auf einem System installiert haben, möchten Sie wahrscheinlich das Modul importieren. Beim Importieren wird das Modul in den aktiven Arbeitsspeicher geladen, sodass ein Benutzer in der PowerShell-Sitzung auf das Modul zugreifen kann. In PowerShell 2,0 können Sie ein neu installiertes PowerShell-Modul mit dem Cmdlet " [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) " importieren. In PowerShell 3,0 kann PowerShell ein Modul implizit importieren, wenn eine der Funktionen oder Cmdlets im Modul von einem Benutzer aufgerufen wird. Beachten Sie, dass bei beiden Versionen angenommen wird, dass Sie das Modul an einem Speicherort installieren, an dem PowerShell ihn finden kann. Weitere Informationen finden Sie unter [Installieren eines PowerShell-Moduls](./installing-a-powershell-module.md).
Mithilfe eines Modul Manifests können Sie einschränken, welche Teile des Moduls exportiert werden, und Sie können Parameter des `Import-Module` Aufrufes verwenden, um einzuschränken, welche Teile importiert werden.

## <a name="importing-a-snap-in-powershell-10"></a>Importieren eines Snap-Ins (PowerShell 1,0)

Module waren in PowerShell 1,0 nicht vorhanden: stattdessen mussten Sie Snap-Ins registrieren und verwenden. Es wird jedoch nicht empfohlen, diese Technologie zu diesem Zeitpunkt zu verwenden, da Module im Allgemeinen einfacher zu installieren und zu importieren sind. Weitere Informationen finden Sie unter [Erstellen eines Windows PowerShell-Snap-Ins](../cmdlet/how-to-create-a-windows-powershell-snap-in.md).

## <a name="importing-a-module-with-import-module-powershell-20"></a>Importieren eines Moduls mit Import-Module (PowerShell 2,0)

PowerShell 2,0 verwendet das entsprechend benannte Cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) zum Importieren von Modulen. Wenn dieses Cmdlet ausgeführt wird, sucht Windows PowerShell in den Verzeichnissen, die in der `PSModulePath` Variablen angegeben sind, nach dem angegebenen Modul. Wenn das angegebene Verzeichnis gefunden wird, sucht Windows PowerShell nach Dateien in der folgenden Reihenfolge: Modul Manifest-Dateien (. psd1), Skript Moduldateien (. psm1), binäre Moduldateien (. dll). Weitere Informationen zum Hinzufügen von Verzeichnissen zur Suche finden Sie unter [Ändern des psmodulepath-Installations Pfads](./modifying-the-psmodulepath-installation-path.md).
Im folgenden Code wird beschrieben, wie Sie ein Modul importieren:

```powershell
Import-Module myModule
```

Wenn sich MyModule im `PSModulePath`befindet, lädt PowerShell MyModule in den aktiven Arbeitsspeicher. Wenn "MyModule" nicht in einem `PSModulePath` Pfad gefunden wurde, können Sie PowerShell trotzdem explizit mitteilen, wo Sie Sie finden:

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

Sie können auch den `-Verbose`-Parameter verwenden, um zu ermitteln, was aus dem Modul exportiert wird und was in den aktiven Speicher importiert wird. Sowohl Exporte als auch Importe schränken die Informationen ein, die dem Benutzer zur Verfügung stehen: der Unterschied besteht darin, wer die Sichtbarkeit steuert. Im Grunde werden Exporte durch Code im Modul gesteuert. Im Gegensatz dazu werden Importe durch den `Import-Module`-Aufrufe gesteuert. Weitere Informationen finden Sie weiter unten unter **Einschränken von importierten**Membern.

## <a name="implicitly-importing-a-module-powershell-30"></a>Implizites Importieren eines Moduls (PowerShell 3,0)

Ab Windows PowerShell 3.0 werden Module automatisch importiert, wenn ein Cmdlet oder eine Funktion im Modul in einem Befehl verwendet wird. Diese Funktion funktioniert in jedem Modul in einem Verzeichnis, das in den Wert der **psmodulepath** -Umgebungsvariablen eingeschlossen ist. Wenn Sie das Modul jedoch nicht unter einem gültigen Pfad speichern, können Sie es dennoch mithilfe der oben beschriebenen expliziten [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) -Option laden.

Mit den folgenden Aktionen wird das automatische Importieren eines Moduls, auch bekannt als "Automatisches Laden von Modulen", auslöst.

- Verwenden eines Cmdlets in einem-Befehl. Wenn Sie beispielsweise `Get-ExecutionPolicy` eingeben, wird das Microsoft. PowerShell. Security-Modul importiert, das das `Get-ExecutionPolicy`-Cmdlet enthält.

- Verwenden des Cmdlets [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) , um den Befehl zu erhalten. Wenn Sie beispielsweise `Get-Command Get-JobTrigger` eingeben, wird das **psscheduledjob** -Modul importiert, das das `Get-JobTrigger`-Cmdlet enthält. Ein `Get-Command` Befehl, der Platzhalter Zeichen enthält, wird als Ermittlung angesehen und löst nicht das Importieren eines Moduls aus.

- Verwenden des Cmdlets " [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) ", um Hilfe zu einem Cmdlet zu erhalten. Wenn Sie beispielsweise `Get-Help Get-WinEvent` eingeben, wird das Microsoft. PowerShell. Diagnostics-Modul importiert, das das `Get-WinEvent`-Cmdlet enthält.

Um das automatische Importieren von Modulen zu unterstützen, ruft das Cmdlet "`Get-Command`" alle Cmdlets und Funktionen in allen installierten Modulen ab, auch wenn das Modul nicht in die Sitzung importiert wird. Weitere Informationen finden Sie im Hilfethema für das Cmdlet " [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) ".

## <a name="the-importing-process"></a>Der Import Vorgang.

Wenn ein Modul importiert wird, wird ein neuer Sitzungs Status für das Modul erstellt, und ein [System. Management. Automation. psmoduleinfo](/dotnet/api/System.Management.Automation.PSModuleInfo) -Objekt wird im Arbeitsspeicher erstellt. Ein Sitzungszustand wird für jedes importierte Modul erstellt (Dies schließt das Stamm Modul und alle in der Tabelle enthaltenen Module ein). Die Elemente, die aus dem Stamm Modul exportiert werden, einschließlich aller Member, die von einem der in das Stamm Modul exportierten Module exportiert wurden, werden dann in den Sitzungszustand des Aufrufers importiert.

Die Metadaten von Membern, die aus einem Modul exportiert werden, verfügen über eine ModuleName-Eigenschaft. Diese Eigenschaft wird mit dem Namen des Moduls aufgefüllt, das Sie exportiert hat.

> [!WARNING]
> Wenn der Name eines exportierten Members ein nicht genehmigtes Verb verwendet oder der Name des Members eingeschränkte Zeichen verwendet, wird beim Ausführen des [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) -Cmdlets eine Warnung angezeigt.

Standardmäßig gibt das [Import-Module-](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet keine Objekte an die Pipeline zurück. Allerdings unterstützt das Cmdlet einen **passthru** -Parameter, mit dem ein [System. Management. Automation. psmoduleinfo](/dotnet/api/System.Management.Automation.PSModuleInfo) -Objekt für jedes importierte Modul zurückgegeben werden kann. Um die Ausgabe an den Host zu senden, müssen Benutzer das Cmdlet " [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) " ausführen.

## <a name="restricting--the-members-that-are-imported"></a>Einschränken der importierten Member

Wenn ein Modul mithilfe des [Import-Module-](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlets importiert wird, werden standardmäßig alle exportierten Modul Elemente in die Sitzung importiert, einschließlich aller Befehle, die von einem Netz Modul in das Modul exportiert werden. Standardmäßig werden Variablen und Aliase nicht exportiert. Verwenden Sie ein [Modul Manifest](./how-to-write-a-powershell-module-manifest.md), um die exportierten Member einzuschränken.
Verwenden Sie die folgenden Parameter des `Import-Module`-Cmdlets, um die importierten Member einzuschränken.

- **Function**: dieser Parameter schränkt die exportierten Funktionen ein. (Wenn Sie ein Modul Manifest verwenden, finden Sie weitere Informationen unter dem functionstoexport-Schlüssel.)

- `**Cmdlet**: dieser Parameter schränkt die exportierten Cmdlets ein (wenn Sie ein Modul Manifest verwenden, finden Sie weitere Informationen unter dem cmdletstoexport-Schlüssel.)

- **Variable**: dieser Parameter schränkt die exportierten Variablen ein (wenn Sie ein Modul Manifest verwenden, finden Sie weitere Informationen unter variablestoexport-Schlüssel.)

- **Alias**: dieser Parameter schränkt die exportierten Aliase ein (wenn Sie ein Modul Manifest verwenden, finden Sie weitere Informationen unter dem Schlüssel "aliasestoexport").

## <a name="see-also"></a>Siehe auch

[Schreiben eines Windows PowerShell-Moduls](./writing-a-windows-powershell-module.md)
