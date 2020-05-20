---
ms.date: 12/12/2018
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: Bedingte Anweisungen und Schleifen in Konfigurationen
ms.openlocfilehash: 86f75be4a3d1c1760dd6269335431e8ab9fd8d09
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736895"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a>Bedingte Anweisungen und Schleifen in einer Konfiguration

Sie können Ihre [Konfiguration](configurations.md) dynamischer gestalten, indem Sie PowerShell-Schlüsselwörter für die Ablaufsteuerung verwenden. Dieser Artikel zeigt Ihnen, wie Sie bedingte Anweisungen und Schleifen verwenden können, um Ihre `Configuration` dynamischer zu gestalten. Die Kombination von Bedingungen und Schleifen mit [Parametern](add-parameters-to-a-configuration.md) und [Konfigurationsdaten](configData.md) ermöglicht Ihnen mehr Flexibilität und Kontrolle bei der Kompilierung Ihrer `Configuration`.

Genau wie eine Funktion oder ein Skriptblock können Sie jedes beliebige PowerShell-Sprachfeature innerhalb einer `Configuration` verwenden.
Die von Ihnen verwendeten Anweisungen werden nur ausgewertet, wenn Sie Ihre `Configuration` aufrufen, um eine `.mof`-Datei zu kompilieren. Die folgenden Beispiele zeigen Szenarien zur Veranschaulichung der Konzepte. Bedingte Anweisungen und Schleifen werden häufiger mit Parametern und Konfigurationsdaten verwendet.

In diesem Beispiel ruft der Ressourcenblock **Service** den aktuellen Zustand eines Diensts zur Kompilierungszeit ab, um eine `.mof`-Datei zu generieren, die ihren aktuellen Zustand beibehält.

> [!NOTE]
> Die Verwendung dynamischer Ressourcenblöcke verhindert die Effektivität von IntelliSense. Der PowerShell-Parser kann nicht bestimmen, ob die angegebenen Werte akzeptabel sind, bis die `Configuration` kompiliert wurde.

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

Zusätzlich können Sie für jeden Dienst auf dem aktuellen Computer einen **Service**-Ressourcenblock erstellen, indem Sie eine `foreach`-Schleife verwenden.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        foreach ($service in $(Get-Service))
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

Sie können mithilfe einer `if`-Anweisung auch eine `Configuration` nur für Computer erstellen, die online sind.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    foreach ($computer in @('Server01', 'Server02', 'Server03'))
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
> Die dynamischen Ressourcenblöcke in den oben aufgeführten Beispielen verweisen auf den aktuellen Computer. In diesem Fall wäre das der Computer, auf dem Sie die `Configuration` erstellen, nicht der Zielknoten.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Zusammenfassung

Zusammenfassend lässt sich sagen, dass Sie jedes beliebige PowerShell-Sprachfeature innerhalb einer `Configuration` verwenden können.

Dazu zählen etwa:

- Benutzerdefinierte Objekte
- Hashtabellen
- Zeichenfolgenbearbeitung
- Remoting
- WMI und CIM
- Active Directory-Objekte
- und weitere...

Der gesamte PowerShell-Code, der in einer `Configuration` definiert ist, wird während der Kompilierung ausgewertet, aber Sie können auch Code in das Skript einfügen, das Ihre `Configuration` enthält. Sämtlicher Code, der sich außerhalb des `Configuration`-Blocks befindet, wird beim Import Ihrer `Configuration` ausgeführt.

## <a name="see-also"></a>Weitere Informationen

- [Hinzufügen von Parametern zu einer Konfiguration](add-parameters-to-a-configuration.md)
- [Trennen von Konfigurationsdaten von Konfigurationen](configData.md)
