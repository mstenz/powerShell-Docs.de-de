---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „Log“
ms.openlocfilehash: c7e1957540da2fd85a30f739e0f69bdb6975a4d8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219384"
---
# <a name="dsc-log-resource"></a>DSC-Ressource „Log“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource __Log__ in Windows PowerShell DSC bietet einen Mechanismus zum Schreiben von Meldungen in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

HINWEIS: Standardmäßig sind nur die Betriebsprotokolle für DSC aktiviert.
Das analytische Protokoll muss aktiviert werden, um verfügbar zu sein und angezeigt zu werden.
Weitere Informationen finden Sie in folgendem Artikel.

[Wo befinden sich die DSC-Ereignisprotokolle?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a>Eigenschaften
|  Eigenschaft  |  Beschreibung   |
|---|---|
| Message| Gibt die Meldung an, die Sie in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“ schreiben möchten.|
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Protokollmeldung geschrieben wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie Sie eine Meldung in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“ einschließen.

> **Hinweis**: Wenn Sie [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) mit dieser konfigurierten Ressource ausführen, wird stets **$false** zurückgegeben.

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost

    {
        Log LogExample
        {
            Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
        }
    }
}
```