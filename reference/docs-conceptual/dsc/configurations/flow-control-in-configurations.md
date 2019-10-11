---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Bedingte Anweisungen und Schleifen in Konfigurationen
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954077"
---
# <a name="conditional-statements-and-loops-in-configurations"></a>Bedingte Anweisungen und Schleifen in Konfigurationen

Sie können Ihre [Konfigurationen](configurations.md) dynamischer gestalten, indem Sie Ablaufsteuerungs-Schlüsselwörter von PowerShell verwenden. Dieser Artikel zeigt Ihnen, wie Sie bedingte Anweisungen und Schleifen verwenden können, um Ihre Konfigurationen dynamischer zu gestalten. Die Kombination von Bedingungen und Schleifen mit [Parametern](add-parameters-to-a-configuration.md) und [Konfigurationsdaten](configData.md) ermöglicht Ihnen mehr Flexibilität und Kontrolle bei der Kompilierung Ihrer Konfigurationen.

Genau wie eine Funktion oder ein Skriptblock können Sie jede beliebige PowerShell-Sprache innerhalb einer Konfiguration verwenden. Die von Ihnen verwendeten Anweisungen werden nur ausgewertet, wenn Sie Ihre Konfiguration aufrufen, um eine MOF-Datei zu kompilieren. Die folgenden Beispiele zeigen einfache Szenarien zur Veranschaulichung der Konzepte. Bedingte Anweisungen und Schleifen werden häufiger mit Parametern und Konfigurationsdaten verwendet.

In diesem einfachen Beispiel ruft der Ressourcenblock **Service** den aktuellen Zustand eines Diensts zur Kompilierungszeit ab, um eine MOF-Datei zu generieren, die ihren aktuellen Zustand beibehält.

> [!NOTE]
> Die Verwendung dynamischer Ressourcenblöcke verhindert die Effektivität von IntelliSense. Der PowerShell-Parser kann nicht bestimmen, ob die angegebenen Werte akzeptabel sind, bis die Konfiguration kompiliert wurde.

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

Zusätzlich können Sie für jeden Dienst auf dem aktuellen Computer eine **Service**-Blockressource erstellen, indem Sie eine `foreach`-Schleife verwenden.

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

Sie können auch nur Konfigurationen für Computer erstellen, die online sind, indem Sie eine einfache `if`-Anweisung verwenden.

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
> Die dynamischen Ressourcenblöcke in den oben aufgeführten Beispielen verweisen auf den aktuellen Computer. In diesem Fall wäre das der Computer, auf dem Sie die Konfiguration erstellen, und nicht der Zielknoten.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Zusammenfassung

Zusammenfassend lässt sich sagen, dass Sie jede beliebige PowerShell-Sprache innerhalb einer Konfiguration verwenden können.

Dazu zählen etwa:

- Benutzerdefinierte Objekte
- Hashtabellen
- Zeichenfolgenbearbeitung
- Remoting
- WMI und CIM
- Active Directory-Objekte
- und weitere...

Der gesamte PowerShell-Code, der in einer Konfiguration definiert ist, wird während der Kompilierung ausgewertet, aber Sie können auch Code in das Skript einfügen, das Ihre Konfiguration enthält. Der Code außerhalb des Konfigurationsblocks wird ausgeführt, wenn Sie Ihre Konfiguration importieren.

## <a name="see-also"></a>Siehe auch

- [Hinzufügen von Parametern zu einer Konfiguration](add-parameters-to-a-configuration.md)
- [Trennen von Konfigurationsdaten von Konfigurationen](configData.md)
