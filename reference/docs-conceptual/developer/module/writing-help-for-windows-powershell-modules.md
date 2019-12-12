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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360559"
---
# <a name="writing-help-for-windows-powershell-modules"></a>Schreiben einer Hilfe für Windows PowerShell-Module

Windows PowerShell-Module können Hilfe Themen über das Modul und über die Modulmember enthalten, wie z. b. Cmdlets, Anbieter, Funktionen und Skripts. Das Cmdlet "`Get-Help`" zeigt die Modul Hilfe Themen im gleichen Format an, in dem die Hilfe für andere Windows PowerShell-Elemente angezeigt wird, und Benutzer verwenden Standard `Get-Help` Befehle, um die Hilfe Themen zu erhalten.

In diesem Dokument werden das Format und die richtige Platzierung der Hilfe Themen für Module erläutert, und es werden Richtlinien für den Inhalt der Modul Hilfe vorgeschlagen.

## <a name="types-of-module-help"></a>Arten der Modul Hilfe

Ein Modul kann die folgenden Arten von Hilfe enthalten.

- **Hilfe zu Cmdlets**. Die Hilfe Themen, in denen Cmdlets in einem Modul beschrieben werden, sind XML-Dateien, die das Befehls Hilfe Schema verwenden.

- **Anbieter Hilfe**. Die Hilfe Themen, in denen Anbieter in einem Modul beschrieben werden, sind XML-Dateien, die das Anbieter Hilfe Schema verwenden.

- **Hilfe zu Funktionen**. In den Hilfe Themen, in denen Funktionen in einem Modul beschrieben werden, kann es sich um XML-Dateien handeln, die das Befehls Hilfe Schema oder Kommentar basierte Hilfe Themen innerhalb der Funktion oder des Skripts oder Skript Moduls verwenden.

- **Skript-Hilfe**. In den Hilfe Themen, in denen Skripts in einem Modul beschrieben werden, kann es sich um XML-Dateien handeln, die das Befehls Hilfe Schema oder Kommentar basierte Hilfe Themen im Skript-oder Skript Modul verwenden.

- **Konzeptionelle Hilfe ("about")** . Sie können ein konzeptionelles ("about") Hilfethema verwenden, um das Modul und seine Member zu beschreiben und zu erläutern, wie die Member zum Ausführen von Aufgaben verwendet werden können. Konzeptionelle Hilfe Themen sind Textdateien mit Unicode-Codierung (UTF-8). Der Dateiname muss das `about_<name>.help.txt` Format verwenden, z. b. about_MyModule. Help. txt. Standardmäßig umfasst Windows PowerShell mehr als 100 dieser konzeptionellen Informationen zu Hilfe Themen, die wie im folgenden Beispiel formatiert sind.

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

## <a name="placement-of-module-help"></a>Platzierung der Modul Hilfe

Das Cmdlet "`Get-Help`" sucht nach Modul Hilfe Themendateien in sprachspezifischen Unterverzeichnissen des Modul Verzeichnisses.

Das folgende Verzeichnisstruktur Diagramm zeigt beispielsweise den Speicherort der Hilfe Themen für das SampleModule-Modul.

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
> Im Beispiel stellt der *\<modulepath >* Platzhalter einen der Pfade in der `PSModulePath`-Umgebungsvariablen dar, z. b. $Home \documents\modules, $PSHome \modules oder einen benutzerdefinierten Pfad, der vom Benutzer angegeben wird.

## <a name="getting-module-help"></a>Hilfe zum Modul

Wenn ein Benutzer ein Modul in eine Sitzung importiert, werden die Hilfe Themen für dieses Modul zusammen mit dem Modul in die Sitzung importiert. Sie können die Hilfe Themendateien im Wert des FileList-Schlüssels im Modul Manifest auflisten, aber die Hilfe Themen sind vom `Export-ModuleMember`-Cmdlet nicht betroffen.

Sie können Modul Hilfe Themen in verschiedenen Sprachen bereitstellen. Das Cmdlet "`Get-Help`" zeigt automatisch Modul Hilfe Themen in der Sprache an, die für den aktuellen Benutzer in der Systemsteuerung unter Regions-und Sprachoptionen angegeben ist. In Windows Vista und höheren Versionen von Windows sucht `Get-Help` nach den Hilfe Themen in sprachspezifischen Unterverzeichnissen des Modul Verzeichnisses in Übereinstimmung mit den für Windows eingerichteten sprach Fall Back Standards.

Ab Windows PowerShell 3,0 löst das Ausführen eines `Get-Help` Befehls für ein Cmdlet oder eine Funktion das automatische Importieren des Moduls aus. Mit dem Cmdlet "`Get-Help`" wird sofort der Inhalt der Hilfe Themen im Modul angezeigt.

Wenn das Modul keine Hilfe Themen enthält und keine Hilfe Themen für die Befehle im Modul auf dem Computer des Benutzers vorhanden sind, zeigt `Get-Help` automatisch generierte Hilfe an. Die automatisch generierte Hilfe umfasst die Befehlssyntax, Parameter und Eingabe-und Ausgabetypen, enthält jedoch keine Beschreibungen. Die automatisch generierte Hilfe enthält Text, der den Benutzer zum Versuch auffordert, das `Update-Help`-Cmdlet zum Herunterladen der Hilfe für den Befehl aus dem Internet oder einer Dateifreigabe zu verwenden. Außerdem empfiehlt es sich, den **Online-** Parameter des Cmdlets "`Get-Help`" zu verwenden, um die Online Version des Hilfe Themas zu erhalten.

## <a name="supporting-updatable-help"></a>Unterstützung für aktualisierbare Hilfe

Benutzer von Windows PowerShell 3,0 und höheren Versionen von Windows PowerShell können aktualisierte Hilfedateien für ein Modul aus dem Internet oder aus einer lokalen Dateifreigabe herunterladen und installieren. Die `Update-Help`-und `Save-Help`-Cmdlets blenden die Verwaltungs Details für den Benutzer aus. Benutzer führen das Cmdlet "`Update-Help`" aus und verwenden dann das `Get-Help`-Cmdlet, um die neuesten Hilfedateien für das Modul an der Windows PowerShell-Eingabeaufforderung zu lesen. Benutzer müssen Windows oder Windows PowerShell nicht neu starten.

Benutzer hinter Firewalls und denjenigen ohne Internet Zugriff können auch aktualisierbare Hilfe verwenden. Administratoren mit Internet Zugriff verwenden das `Save-Help`-Cmdlet zum herunterladen und Installieren der neuesten Hilfedateien auf einer Dateifreigabe. Anschließend verwenden die Benutzer den **path** -Parameter des `Update-Help`-Cmdlets, um die neuesten Hilfedateien aus der Dateifreigabe zu erhalten.

Modul Autoren können Hilfedateien in das Modul einschließen und die aktualisierbare Hilfe verwenden, um die Hilfedateien zu aktualisieren, oder Hilfedateien aus dem Modul weglassen und die aktualisierbare Hilfe verwenden, um Sie zu installieren und zu aktualisieren.

Weitere Informationen zur aktualisierbaren Hilfe finden Sie [unter unterstützen der aktualisierbaren Hilfe](./supporting-updatable-help.md).

## <a name="supporting-online-help"></a>Unterstützung für Onlinehilfe

Benutzer, die aktualisierte Hilfedateien auf ihren Computern nicht installieren können oder nicht installieren, basieren häufig auf der Online Version der Modul Hilfe Themen. Der **Online-** Parameter des `Get-Help`-Cmdlets öffnet die Online Version eines Cmdlets oder Hilfe Themas für erweiterte Funktionen für den Benutzer in seinem standardmäßigen Internet Browser.

Das `Get-Help`-Cmdlet verwendet den Wert der **HelpUri** -Eigenschaft des Cmdlets oder der Funktion, um die Online Version des Hilfe Themas zu suchen.

Ab Windows PowerShell 3,0 können Sie Benutzer bei der Suche nach der Online Version der Hilfe Themen zu Cmdlets und Funktionen unterstützen, indem Sie das HelpUri-Attribut in der Cmdlet-Klasse oder die **HelpUri** -Eigenschaft des **cmdletbinding** -Attributs definieren. Der Wert des-Attributs ist der Wert der **HelpUri** -Eigenschaft des Cmdlets oder der Funktion.

Weitere Informationen finden Sie [unter unterstützen der Online Hilfe](./supporting-online-help.md).

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Moduls](./writing-a-windows-powershell-module.md)

[Unterstützen aktualisierbarer Hilfe](./supporting-updatable-help.md)

[Unterstützen der Online Hilfe](./supporting-online-help.md)