---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Verwenden von vertrauten Befehlsnamen
ms.openlocfilehash: 30b33bc8739975c1a40e51c04a3ee4e426c199e7
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030898"
---
# <a name="using-familiar-command-names"></a>Verwenden vertrauter Befehlsnamen

PowerShell unterstützt Aliase, um mit alternativen Namen auf Befehle zu verweisen. Durch Aliase können Benutzer mit Erfahrung in anderen Shell-Umgebungen gängige Befehlsnamen, die sie bereits kennen, für ähnliche Vorgänge in PowerShell verwenden.

Bei der Aliasverwendung wird einem Befehl ein neuer Name zugeordnet. Beispielsweise umfasst PowerShell eine interne Funktion namens `Clear-Host`, mit der das Ausgabefenster gelöscht wird. Sie können an einer Eingabeaufforderung entweder `cls` oder den Alias `clear` eingeben. PowerShell interpretiert diese Aliase und führt die Funktion `Clear-Host` aus.

Dieses Feature unterstützt Benutzer beim Erlernen von PowerShell. Zunächst beherrschen die meisten **cmd.exe**- und Unix-Benutzer ein großes Repertoire an Befehlen, deren Namen sie bereits kennen. Die PowerShell-Äquivalente führen möglicherweise nicht zu identischen Ergebnissen. Dennoch sind die Ergebnisse ähnlich genug, um Benutzern das Arbeiten ohne Kenntnis der PowerShell-Befehlsnamen zu ermöglichen. Das „Fingergedächtnis“ ist eine weitere Quelle für Frustrationen beim Erlernen einer neuen Befehlsshell. Wenn Sie seit Jahren **cmd.exe** verwenden, geben Sie möglicherweise reflexartig den Befehl `cls` ein, um den Bildschirm zu löschen. Ohne den Alias für `Clear-Host` erhalten Sie eine Fehlermeldung und wissen nicht, wie Sie zum Löschen der Ausgabe vorgehen müssen.

Die folgende Liste zeigt einige wenige der gängigen **cmd.exe**- und Unix-Befehle, die Sie in PowerShell verwenden können:

|||||
|-|-|-|-|
|cat|dir|mount|rm|
|cd|echo|move|rmdir|
|chdir|erase|popd|sleep|
|clear|h|ps|sort|
|cls|history|pushd|tee|
|copy|kill|pwd|type|
|del|lp|r|write|
|diff|ls|ren||

Das Cmdlet `Get-Alias` zeigt Ihnen den tatsächlichen Namen des nativen PowerShell-Befehls, der einem Alias zugeordnet ist.

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a>Interpretieren von Standardaliasen

Die zuvor beschriebenen Aliase wurden für Namenskompatibilität mit anderen Befehlsshells entworfen.
Die meisten der in PowerShell integrierten Aliase dienen der Verkürzung. Kürzere Namen sind einfacher einzugeben, aber schwer zu lesen, wenn Sie deren Bedeutung nicht kennen.

PowerShell-Aliase versuchen, einen Kompromiss zwischen Aussagekraft und Kürze zu schließen. PowerShell verwendet einen Standardsatz an Aliasen für gängige Nomen und Verben.

Beispielabkürzungen:

| Nomen oder Verb | Abkürzung |
|--------------|--------------|
| Abrufen          | g            |
| Festlegen          | s            |
| Element         | i            |
| Speicherort     | l            |
| Befehl      | cm           |
| Alias        | al           |

Diese Aliase sind verständlich, wenn Sie die Kurznamen kennen.

| Cmdlet-Name    | Alias |
|----------------|-------|
| `Get-Item`     | gi    |
| `Set-Item`     | si    |
| `Get-Location` | gl    |
| `Set-Location` | sl    |
| `Get-Command`  | gcm   |
| `Get-Alias`    | gal   |

Sobald Sie mit der Aliasverwendung in PowerShell vertraut sind, ist einfach zu erraten, dass **sal** sich auf `Set-Alias` bezieht.

## <a name="creating-new-aliases"></a>Erstellen neuer Aliase

Sie können mit dem Cmlet `Set-Alias` eigene Aliase erstellen. Mit den folgenden Anweisungen werden beispielsweise die zuvor besprochenen standardmäßigen Cmdlet-Aliase erstellt:

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

Intern verwendet PowerShell ähnliche Befehle während des Starts, aber diese Aliase können nicht geändert werden.
Wenn Sie versuchen, einen dieser Befehle auszuführen, erhalten Sie einen Fehler mit dem Hinweis, dass Aliase nicht geändert werden können. Beispiel:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```
