---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Direktes Aufrufen von DSC-Ressourcenmethoden
ms.openlocfilehash: 3ec3a3a8da615f45f3fdd28b1c1e46e312507ed5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189617"
---
# <a name="calling-dsc-resource-methods-directly"></a>Direktes Aufrufen von DSC-Ressourcenmethoden

>Gilt für: Windows PowerShell 5.0

Sie können das Cmdlet[Invoke-DscResource](https://technet.microsoft.com/library/mt517869.aspx) verwenden, um die Funktionen oder Methoden einer DSC-Ressource direkt aufzurufen (die Funktionen **Get-TargetResource**, **Set-TargetResource** und **Test-TargetResource** einer MOF-basierten Ressource oder die Methoden **Get**, **Set** und **Test** einer klassenbasierten Ressource).
Dieses kann von Drittanbietern verwendet werden, die DSC-Ressourcen verwenden möchten, oder als hilfreiches Tool bei der Entwicklung von Ressourcen.

Dieses Cmdlet wird in der Regel in Kombination mit einer Metakonfigurationseigenschaft `refreshMode = 'Disabled'` verwendet, kann aber unabhängig davon verwendet werden, auf was **refreshMode** festgelegt ist.

Beim Aufrufen des Cmdlets **Invoke-DscResource** geben Sie an, welche Methode oder Funktion aufgerufen werden soll, indem Sie den Parameter **Method** verwenden. Sie geben die Eigenschaften der Ressource an, indem Sie eine Hashtabelle als Wert des Parameters **Property** übergeben.

Im Folgenden finden Sie Beispiele für das direkte Aufrufen von Ressourcenmethoden:

## <a name="ensure-a-file-is-present"></a>Sicherstellen, dass eine Datei vorhanden ist

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a>Testen, ob eine Datei vorhanden ist

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a>Abrufen des Inhalts einer Datei

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

>**Hinweis:** Das direkte Aufrufen von Methoden für zusammengesetzte Ressourcen wird nicht unterstützt. Rufen Sie stattdessen die Methoden der zugrunde liegenden Ressourcen auf, aus denen die zusammengesetzte Ressource besteht.

## <a name="see-also"></a>Weitere Informationen
- [Schreiben einer benutzerdefinierten DSC-Ressource mit MOF](authoringResourceMOF.md)
- [Schreiben einer benutzerdefinierten DSC-Ressource mit PowerShell-Klassen](authoringResourceClass.md)
- [Debuggen von DSC-Ressourcen](debugResource.md)