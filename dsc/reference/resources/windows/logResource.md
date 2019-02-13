---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „Log“
ms.openlocfilehash: 1f94a2d847a4ef63f81e2fb83d1a0f76f5677b09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677765"
---
# <a name="dsc-log-resource"></a>DSC-Ressource „Log“

> _Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0_

Die Ressource __Log__ in Windows PowerShell DSC bietet einen Mechanismus zum Schreiben von Meldungen in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> Standardmäßig sind nur die Betriebsprotokolle für DSC aktiviert. Das analytische Protokoll muss aktiviert werden, um verfügbar zu sein und angezeigt zu werden. Weitere Informationen finden Sie im Abschnitt „Wo befinden sich die DSC-Ereignisprotokolle?“ im Artikel [Problembehandlung bei DSC](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).

## <a name="properties"></a>Eigenschaften

| Eigenschaft | Beschreibung |
| --- | --- |
| Message| Gibt die Meldung an, die Sie in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“ schreiben möchten.|
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Protokollmeldung geschrieben wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = '[ResourceType]ResourceName'`.|

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie Sie eine Meldung in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“ einschließen.

> [!NOTE]
> Wenn Sie [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) mit dieser konfigurierten Ressource ausführen, wird stets **$false** zurückgegeben.

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```
