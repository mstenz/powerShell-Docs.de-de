---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Bedingte Anweisungen und Schleifen in Konfigurationen
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401250"
---
# <a name="conditional-statements-and-loops-in-configurations"></a>Bedingte Anweisungen und Schleifen in Konfigurationen

Möglich Ihre [Konfigurationen](configurations.md) dynamischer PowerShell flusssteuerung Schlüsselwörter verwenden. In diesem Artikel zeigt Ihnen, wie Sie bedingungsanweisungen und Schleifen verwenden können, um Ihre Konfigurationen dynamischer gestalten. Kombinieren von bedingten und Schleifen mit [Parameter](add-parameters-to-a-configuration.md) und [Konfigurationsdaten](configData.md) ermöglicht Ihnen mehr Flexibilität und Kontrolle beim Kompilieren von Konfigurationen Ihrer.

Genau wie eine Funktion oder ein Skriptblock können Sie alle PowerShell-Sprache in einer Konfiguration verwenden. Die Anweisungen, die Sie verwenden, werden nur ausgewertet, wenn Sie Ihre Konfiguration, um eine "MOF"-Datei kompilieren aufrufen. Die folgenden Beispiele zeigen die einfache Szenarios zur Veranschaulichung der Konzepte. Konditionelle Abschnitte bereit sind, Schleifen mit Parametern und Konfigurationsdaten, die häufiger verwendet werden.

In diesem einfachen Beispiel der **Service** Ressourcenblock Ruft den aktuellen Zustand eines Diensts, zum Zeitpunkt der Kompilierung zu eine "MOF"-Datei generiert, die den aktuellen Zustand beibehält.

> [!NOTE]
> Mithilfe von dynamischen ressourcenblöcke, wird die Effektivität von Intellisense verdrängen. Der PowerShell-Parser kann nicht bestimmen, wenn die angegebenen Werte zulässig sind, bis die Konfiguration kompiliert wird.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

Darüber hinaus können Sie erstellen eine **Service** blockieren Ressource für jeden Dienst auf dem aktuellen Computer mit einer `foreach` Schleife.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

Sie können auch nur Konfigurationen für Computer, die online sind, mithilfe einer einfaches erstellen `if` Anweisung.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> Die dynamische Ressource, die in den obigen Beispielen Verweis den aktuellen Computer blockiert. In dieser Instanz, die dem Computer erstellen Sie die Konfiguration auf, nicht das Ziel-Knoten.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Zusammenfassung

Zusammengefasst können Sie alle PowerShell-Sprache in einer Konfiguration verwenden.

Dazu zählen z. B.:

- Benutzerdefinierte Objekte
- Hashtabellen
- Zeichenfolgenbearbeitung
- Remoting
- WMI- und CIM
- Active Directory-Objekten
- und weitere...

Alle PowerShell-Code in einer Konfiguration definierten Zeitpunkt der Kompilierung ausgewertet werden, aber Sie können auch Code in das Skript mit der Konfiguration platzieren. Code außerhalb des Blocks für die Konfiguration wird ausgeführt werden, wenn Sie Ihre Konfiguration importieren.

## <a name="see-also"></a>Siehe auch

- [Hinzufügen von Parametern zu einer Konfiguration](add-parameters-to-a-configuration.md)
- [Trennen von Konfigurationsdaten von Konfigurationen](configData.md)
