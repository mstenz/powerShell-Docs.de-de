---
ms.date: 10/13/2017
keywords: dsc,powershell,configuration,setup
title: 'Desired State Configuration (DSC): Übersicht für Ingenieure'
ms.openlocfilehash: 0e599c2218cd2df29dbd0529006be5e1ef17ce5f
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953797"
---
# <a name="desired-state-configuration-overview-for-engineers"></a>Desired State Configuration (DSC): Übersicht für Ingenieure

Dieses Dokumente richtet sich an Ingenieure und Betriebsteams, um die Vorteile der Desired State Configuration (DSC) von PowerShell kennenzulernen.
Eine Ansicht des Werts auf höherer Ebene, den DSC bereitstellt, finden Sie unter [Desired State Configuration (DSC): Übersicht für Entscheidungsträger](decisionMaker.md)

## <a name="benefits-of-desired-state-configuration"></a>Vorteile von DSC

Mit DSC können Sie Folgendes tun:

- Die Komplexität der Skripterstellung in Windows verringern
- Die Geschwindigkeit der Iteration erhöhen

Das Konzept der „kontinuierlichen Bereitstellung“ gewinnt immer mehr an Wichtigkeit.
Die kontinuierliche Bereitstellung ermöglicht häufige Bereitstellungen, womöglich mehrmals pro Tag.
Der Zweck dieser Bereitstellungen ist nicht, etwas zu reparieren, sondern etwas schnell veröffentlichen zu können.
Dadurch, dass neue Features durch die Entwicklung so reibungslos und verlässlich wie möglich in Betrieb genommen werden können, kann die Amortisierungszeit der neuen Businesslogik verringert werden.

Der Wechsel zum Cloudcomputing beinhaltet eine Bereitstellungslösung, bei der ein „deklaratives“ Vorlagenmodell verwendet wird. Hierbei wird eine Umgebung im Endzustand als Text deklariert und in einer Bereitstellungs-Engine veröffentlicht.
Diese Bereitstellungstechnik ermöglicht schnelle Änderungen im erforderlichen Umfang, mit robustem Schutz vor Ausfallrisiken, da die Bereitstellung jederzeit konsistent wiederholt werden kann, um einen Endzustand zu gewährleisten.
Die Erstellung von Tools und Diensten, die diese Art der Vorgänge durch Automatisierung unterstützen, ist eine Reaktion auf diese Änderungen.

DSC ist eine Plattform, die deklarative und idempotente (wiederholbare) Bereitstellung, Konfiguration und Konformität bereitstellt.
Mit der DSC-Plattform stellen Sie sicher, dass die Komponenten Ihrer Datencenter über die ordnungsgemäße Konfiguration verfügen, wodurch Fehler sowie teure Probleme bei der Bereitstellung vermieden werden können.
Dadurch dass die DSC-Konfiguration als Teil eines Anwendungscodes angesehen wird, ermöglicht DSC die kontinuierliche Bereitstellung.
Die DSC-Konfiguration sollte als Teil der Anwendung aktualisiert werden, wodurch sichergestellt werden kann, dass das erforderliche Wissen für die Bereitstellung der Anwendung immer auf dem neuesten Stand und zum Gebrauch bereit ist.

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>„Ich besitze PowerShell, warum brauche ich Desired State Configuration?“

Die DSC-Konfigurationen trennen die Absicht – oder „was ich machen will“ – von der Ausführung – oder „wie ich es machen will.“
Dies bedeutet, dass die Logik der Ausführung in den Ressourcen enthalten ist.
Benutzer müssen nicht wissen, wie Sie eine Funktion implementieren oder bereitstellen, wenn eine DSC-Ressource für diese Funktion verfügbar ist.
Dies ermöglicht es dem Benutzer, sich auf die Struktur der Bereitstellung zu konzentrieren.

PowerShell-Skripts sollten beispielsweise so aussehen:
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
Dieses Skript ist einfach, verständlich und unkompliziert.
Wenn Sie jedoch versuchen, dieses Skript in die Produktionsumgebung einzufügen, werden Sie auf verschiedene Probleme stoßen.
Was geschieht, wenn, das Skript zweimal hintereinander ausgeführt wird?
Was geschieht, wenn Bob bisher Vollzugriff auf die Freigabe hatte?

Um diese Probleme zu berücksichtigen, wird eine „echte“ Version des Skripts genauer auf Beispiele wie das folgende eingehen:
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

Dieses Skript ist komplexer, mit sehr viel Logik und Fehlerbehandlung.
Das Skript ist komplexer, da Ihnen nicht mehr angezeigt wird, was geschehen soll, jedoch *wie es funktioniert*.

Mit DSC können Sie angeben, was Sie tun möchten, und die zugrunde liegende Logik wird entfernt.

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Bob"
          FullAccess  = "Alice"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

Dieses Skript ist ordnungsgemäß formatiert und einfach zu lesen.
Die Logikpfade und Fehlerbehandlungen sind weiterhin, in der Implementierung der [Ressource](../resources/resources.md) vorhanden, sind jedoch für den Autor des Skripts nicht sichtbar.

## <a name="separating-environment-from-structure"></a>Trennen der Umgebung von der Struktur

In DevOps kommt es häufig vor, dass es mehrere Umgebungen für die Bereitstellung gibt.
Es kann z.B. eine „dev“-Umgebung vorhanden sein, die zum schnellen Erstellen von Prototypen für neuen Code verwendet wird.
Der Code aus der „dev“-Umgebung (Entwicklungsumgebung) wird dann in eine „test“-Umgebung (Testumgebung) verschoben, wo andere Personen die neue Funktion überprüfen.
Schließlich gelangt der Code in „prod“ (Produktionsumgebung) oder in die Livesite-Produktionsumgebung.

DSC-Konfigurationen berücksichtigen diese dev-test-prod-Pipeline durch Verwendung von [Konfigurationsdaten](../configurations/configData.md).
Dadurch wird der Unterschied zwischen der Struktur der Konfiguration noch weiter von den verwalteten Knoten abstrahiert.
Sie können beispielsweise eine Konfiguration definieren, die einen SQL-Server, einen IIS-Server und einen Server auf mittlerer Ebene erfordert.
Unabhängig davon, welche Knoten die verschiedenen Teile dieser Konfiguration erhalten, werden diese drei Elemente immer vorhanden sein.
Sie können Konfigurationsdaten verwenden, um alle drei Elemente auf den gleichen Computer für eine dev-Umgebung zu verweisen, die drei Elemente auf drei verschiedene Computer für eine Testumgebung zu verteilen und schließlich auf all Ihre Produktionsserver für die Produktionsumgebung.
Damit Sie eine Bereitstellung in unterschiedlichen Umgebungen durchführen können, können Sie **Start-DscConfiguration** mit den richtigen Konfigurationsdaten für die Zielumgebung aufrufen.

## <a name="see-also"></a>Weitere Informationen

[Konfigurationen](../configurations/configurations.md)

[Konfigurationsdaten](../configurations/configData.md)

[Ressourcen](../resources/resources.md)
