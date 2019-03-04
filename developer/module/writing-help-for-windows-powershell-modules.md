---
title: Schreiben von Hilfe für Windows PowerShell-Module | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854066"
---
# <a name="writing-help-for-windows-powershell-modules"></a>Schreiben einer Hilfe für Windows PowerShell-Module

Windows PowerShell-Module können Hilfethemen, die über das Modul und die Member des Moduls, wie z. B. Cmdlets, Anbieter, Funktionen und Skripts enthalten. Die `Get-Help` Cmdlet zeigt die Modul-Hilfethemen im selben Format, wie es zeigt die Hilfe für andere Windows PowerShell-Elemente, und Benutzer können `Get-Help` Befehle aus, um die Hilfethemen zu erhalten.

In diesem Dokument wird erläutert, das Format und die korrekte Platzierung des Moduls Hilfethemen, und Richtlinien für das Modul Hilfeinhalt schlägt vor.

## <a name="types-of-module-help"></a>Typen von Hilfe zu Integrationsmodulen

Ein Modul kann die folgenden Typen von Hilfe enthalten.

- **Cmdlet-Hilfe**. Die Hilfethemen zu Cmdlets in einem Modul sind, dass die XML-Dateien, die dem Befehl Schema unterstützen

- **Hilfe durch Anbieter**. Hilfe zu Themen, die Anbieter in einem Modul zu beschreiben sind, dass die XML-Dateien, die den Anbieter verwenden, Schema unterstützen.

- **Funktionen**. Die Hilfethemen zu Funktionen in einem Modul kann sein, dass die XML-Dateien, die den Befehl verwenden, Schema oder die Kommentar-Hilfethemen innerhalb der Funktion oder des Skripts oder das Skriptmodul helfen

- **Skripts**. Die Hilfethemen zu Skripts in einem Modul möglich, dass die XML-Dateien, die den Befehl verwenden, Schema oder die Kommentar-Hilfethemen in das Skript oder das Modul "Script" können.

- **("Info") Hilfe konzeptionellen**. Sie können eines konzeptionellen ("Info") Hilfethema verwenden, um das Modul und ihre Member beschreiben und erläutern, wie die Elemente zusammen verwendet werden können für Aufgaben. Konzeptionelle Hilfethemen sind Textdateien mit der Codierung von Unicode (UTF-8). Verwenden Sie der Dateinamen muss die `about_<name>.help.txt` Format, z. B. about_MyModule.help.txt. Standardmäßig Windows PowerShell umfasst mehr als 100 konzeptionelle Themen zu unterstützen, und sie wie im folgenden Beispiel formatiert sind.

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a>Platzierung der Hilfe zu Integrationsmodulen

Die `Get-Help` Cmdlet sucht Modul Hilfedateien in sprachspezifischen Unterverzeichnissen des Modulverzeichnisses.

Das folgende Diagramm der Directory-Struktur zeigt beispielsweise den Speicherort für die Hilfethemen für das Modul SampleModule.

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> Im Beispiel die  *\<ModulePath >* steht für einen der Pfade in der `PSModulePath` Umgebungsvariablen wie z. B. $Home\Documents\Modules, $Pshome\Modules oder einen benutzerdefinierten Pfad, der den Benutzer angibt.

## <a name="getting-module-help"></a>Abrufen von Hilfe zu Integrationsmodulen

Wenn ein Benutzer ein Modul in eine Sitzung importiert, werden die Hilfethemen für das Modul in der Sitzung zusammen mit dem Modul importiert. Sie können die Hilfedateien im Wert des Schlüssels im modulmanifest FileList auflisten, aber Hilfethemen sind nicht betroffen von dem `Export-ModuleMember` Cmdlet.

Sie können die Modul-Hilfethemen in verschiedenen Sprachen bereitstellen. Die `Get-Help` Cmdlet zeigt automatisch die Modul-Hilfethemen in der Sprache, die für den aktuellen Benutzer in den Regions- und Sprachoptionen Element in der Systemsteuerung angegeben wird. In Windows Vista und höheren Versionen von Windows `Get-Help` sucht nach den Hilfethemen in sprachspezifischen Unterverzeichnissen des Modulverzeichnisses in Übereinstimmung mit der Sprache fallback Standards, die für Windows.

Ab Windows PowerShell 3.0, mit einem `Get-Help` -Befehl für ein Cmdlet oder eine Funktion löst automatischen Importieren des Moduls. Die `Get-Help` Cmdlet zeigt sofort den Inhalt der Hilfethemen im Modul.

Wenn das Modul enthält keine Hilfethemen, und es keine Hilfethemen für die Befehle im Modul auf dem Computer des Benutzers sind, `Get-Help` zeigt die automatisch generierte Hilfe an. Die automatisch generierte Hilfe umfasst die Befehlssyntax, Parameter und Eingabe-und Ausgabetypen, jedoch keine Beschreibungen. Die automatisch generierte Hilfe umfasst Text, der leitet den Benutzer mit der `Update-Help` -Cmdlet zum Herunterladen von Hilfe für den Befehl aus dem Internet oder eine Dateifreigabe. Außerdem empfiehlt die **Online** Parameter der `Get-Help` Cmdlet, um die Onlineversion des Hilfethemas abzurufen.

## <a name="supporting-updatable-help"></a>Unterstützung für aktualisierbare Hilfe

Benutzer von Windows PowerShell 3.0 und höheren Versionen von Windows PowerShell können herunterladen und Installieren der aktualisierten Hilfedateien für ein Modul aus dem Internet oder aus einer lokalen Dateifreigabe. Die `Update-Help` und `Save-Help` Cmdlets ausblenden, die verwaltungsdetails des Benutzers. Benutzer führen die `Update-Help` Cmdlet und verwenden Sie dann die `Get-Help` Cmdlet, um die neuesten Hilfedateien für das Modul an der Windows PowerShell-Eingabeaufforderung zu lesen. Benutzer müssen sich nicht auf Windows oder Windows PowerShell neu zu starten.

Benutzer hinter Firewalls und ohne Internetzugriff können aktualisierbare Hilfe, ebenfalls verwenden. Administratoren mit Internet zugreifen, verwenden die `Save-Help` -Cmdlet zum Herunterladen und installieren die neuesten Hilfedateien auf einer Dateifreigabe. Klicken Sie dann die Benutzer verwenden die **Pfad** Parameter der `Update-Help` Cmdlet, um die neuesten Hilfedateien aus der Dateifreigabe abzurufen.

Modulautoren können Hilfedateien in das Modul einschließen und aktualisierbare Hilfe verwenden, aktualisieren die Hilfedateien vorhanden sind, oder lassen Sie die Hilfedateien aus dem Modul und aktualisierbare Hilfe verwenden, installieren und diese aktualisieren.

Weitere Informationen zur aktualisierbaren Hilfe finden Sie unter [unterstützen aktualisierbarer Hilfe](./supporting-updatable-help.md).

## <a name="supporting-online-help"></a>Unterstützung für Onlinehilfe

Benutzer, die nicht möglich, oder installieren Sie nicht aktualisiert, Hilfe, die Dateien auf ihren Computern häufig die Onlineversion des Hilfethemen Modul abhängig. Die **Online** Parameter, der die `Get-Help` Cmdlet öffnet die Onlineversion eines Cmdlets oder die erweiterte Funktion-Hilfethema für den Benutzer in ihren Standard-Internetbrowser.

Die `Get-Help` Cmdlet verwendet den Wert der **HelpUri** Eigenschaft der Cmdlets oder einer Funktion, um die Onlineversion des Hilfethemas zu finden.

Ab Windows PowerShell 3.0, Sie können Benutzern helfen, die Onlineversion des Cmdlet- und Hilfethemen suchen, indem das HelpUri-Attribut in der Cmdlet-Klasse oder die **HelpUri** Eigenschaft der **CmdletBinding** Attribut. Der Wert des Attributs ist der Wert des der **HelpUri** Eigenschaft der Cmdlets oder der Funktion.

Weitere Informationen finden Sie unter [Supporting Online Help](./supporting-online-help.md).

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Moduls](./writing-a-windows-powershell-module.md)

[Unterstützung für aktualisierbare Hilfe](./supporting-updatable-help.md)

[Unterstützung von Onlinehilfe](./supporting-online-help.md)