---
title: Hinzufügen einer Cmdlet-Beschreibung
ms.date: 09/13/2016
ms.openlocfilehash: 2b98c4cefc3a55eccfeb7eba5a290e7d93a6088b
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893236"
---
# <a name="how-to-add-a-cmdlet-description"></a>Hinzufügen einer Cmdlet-Beschreibung

In diesem Abschnitt wird beschrieben, wie Sie Inhalte hinzufügen, die im Abschnitt **Beschreibung** der Cmdlet-Hilfe angezeigt werden. In der Hilfedatei wird dieser Inhalt dem **Befehls** Knoten für jedes Cmdlet hinzugefügt.

> [!NOTE]
> Eine umfassende Ansicht einer Hilfedatei erhalten Sie, indem Sie eine der `dll-Help.xml` Dateien im PowerShell-Installationsverzeichnis öffnen. Die `Microsoft.PowerShell.Commands.Management.dll-Help.xml` Datei enthält z. b. Inhalte für mehrere PowerShell-Cmdlets.

### <a name="to-add-a-description"></a>So fügen Sie eine Beschreibung hinzu

- Erläutern Sie zunächst die grundlegenden Features des Cmdlets ausführlicher. In vielen Fällen können Sie die im Cmdlet-Namen verwendeten Begriffe erläutern und unbekannte Konzepte mit einem Beispiel veranschaulichen. Wenn das Cmdlet z. b. Daten an eine Datei anfügt, erklären Sie, dass die Daten am Ende einer vorhandenen Datei hinzugefügt werden.

- Um alle Features des Cmdlets zu finden, überprüfen Sie die Parameterliste. Beschreiben Sie die primäre Funktion des Cmdlets, und schließen Sie dann weitere Funktionen und Funktionen ein. Wenn z. b. die Hauptfunktion des Cmdlets darin besteht, eine Eigenschaft zu ändern, das Cmdlet jedoch alle Eigenschaften ändern kann, sagen Sie dies in der detaillierten Beschreibung. Wenn die Cmdlet-Parameter den Benutzern die Möglichkeit geben, Informationen auf verschiedene Weise anzufordern, erklären Sie Sie.

- Enthalten Informationen zu Möglichkeiten, mit denen Benutzer das Cmdlet zusätzlich zu den offensichtlichen Verwendungsmöglichkeiten verwenden können. Beispielsweise können Sie das-Objekt verwenden, das das `Get-Host` Cmdlet abruft, um die Textfarbe im Windows PowerShell-Befehlsfenster zu ändern.

  Beispiel: "das `Get-Acl` Cmdlet ruft Objekte ab, die die Sicherheits Beschreibung einer Datei oder Ressource darstellen. Die Sicherheitsbeschreibung enthält die Zugriffssteuerungslisten (Access Control Lists, ACLs) der Ressource. Die ACL gibt die Berechtigungen an, die Benutzer und Benutzergruppen für den Zugriff auf die Ressource haben.

- Die ausführliche Beschreibung sollte das Cmdlet beschreiben, aber es sollte keine Konzepte beschreiben, die vom Cmdlet verwendet werden. Legen Sie Konzept Definitionen in zusätzlichen Notizen ab.

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell SDK](../windows-powershell-reference.md)
