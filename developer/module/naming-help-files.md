---
title: Benennen die Hilfedateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082176"
---
# <a name="naming-help-files"></a>Benennen von Hilfedateien

In diesem Thema wird erläutert, wie Sie eine XML-basierte-Hilfedatei zu benennen, damit die [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet finden. Die Anforderungen an den für jeden Befehl unterscheiden.

## <a name="cmdlet-help-files"></a>Cmdlet-Hilfedateien

Die Hilfedatei für ein C# Cmdlet muss den Namen für die Assembly, in dem das Cmdlet definiert wird. Verwenden Sie das folgende Namensformat für die Datei ein:

```
<AssemblyName>.dll-help.xml
```

Das Namensformat für die Assembly ist erforderlich, auch wenn die Assembly ein geschachteltes Modul ist.

Z. B. die [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) Cmdlet in der Microsoft.PowerShell.Diagnostics.dll-Assembly definiert ist. Die `Get-Help` Cmdlet sucht ein Hilfethema für das `Get-WinEvent` Cmdlet nur in der Microsoft.PowerShell.Diagnostics.dll help.xml Datei im Modulverzeichnis gespeichert.

## <a name="provider-help-files"></a>Anbieter-Hilfedateien

Die Hilfedatei für ein Windows PowerShell-Anbieter muss für die Assembly mit dem Namen werden in dem der Anbieter definiert ist. Verwenden Sie das folgende Namensformat für die Datei ein:

```
<AssemblyName>.dll-help.xml
```

Das Namensformat für die Assembly ist erforderlich, auch wenn die Assembly ein geschachteltes Modul ist.

Der Zertifikatanbieter ist z. B. in der Assembly Microsoft.PowerShell.Security.dll definiert. Die `Get-Help` Cmdlet sucht ein Hilfethema zum Certificate-Anbieter nur in der Microsoft.PowerShell.Security.dll help.xml Datei im Modulverzeichnis gespeichert.

## <a name="function-help-files"></a>Funktion-Hilfedateien

Funktionen können mithilfe von dokumentiert werden [kommentarbasierte Hilfe](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) oder in eine XML-Hilfedatei dokumentiert. Wenn die Funktion in eine XML-Datei dokumentiert ist, müssen die Funktion eine `.ExternalHelp` kommentieren Schlüsselwort, das die Funktion die XML-Datei zugeordnet. Andernfalls die `Get-Help` Cmdlet wurde die Datei nicht gefunden.

Es gibt keine technischen Vorschriften für den Namen einer Funktion-Hilfedatei. Ist jedoch eine bewährte Methode, um die Hilfedatei für das Skriptmodul zu benennen, in dem die Funktion definiert ist. Beispielsweise wird die folgende Funktion in der MyModule. Psm1-Datei definiert.

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>Hilfedateien für CIM-Befehl

Die Hilfedatei für einen CIM-Befehl muss für die CDXML-Datei benannt werden, in dem der CIM-Befehl definiert ist. Verwenden Sie das folgende Namensformat für die Datei ein:

```
<FileName>.cdxml-help.xml
```

CIM-Befehle werden in CDXML-Dateien definiert, die in Modulen, die als geschachtelte Module enthalten sein können. Wenn der CIM-Befehls in die Sitzung als Funktion importiert wird, fügt Windows PowerShell eine `.ExternalHelp` Kommentar-Schlüsselwort, um die Definition der Funktion, die ordnet die Funktion mithilfe einer XML-Datei, die den Namen für die CDXML-Datei, in dem der CIM-Befehl definiert ist.

## <a name="script-workflow-help-files"></a>Skript-Workflow-Hilfedateien

Skript-Workflows, die in Modulen enthalten sind, können in XML-basierte Hilfedateien dokumentiert werden. Es gibt keine technischen Vorschriften für den Namen der Hilfedatei. Ist jedoch eine bewährte Methode, um die Hilfedatei für das Skriptmodul zu benennen, in dem der skriptworkflow definiert ist. Beispiel:

```
<ScriptModule>.psm1-help.xml
```

Im Gegensatz zu anderen Skriptbefehle, skriptworkflows erfordern kein `.ExternalHelp` kommentieren Schlüsselwort, um sie einer Hilfedatei zuzuordnen. Windows PowerShell Sie stattdessen die UI-kulturspezifischen Unterverzeichnissen des Modulverzeichnisses für XML-basierte Hilfedateien durchsucht und nach Hilfe für den skriptworkflow in allen Dateien gesucht. `.ExternalHelp` Kommentarschlüsselwort werden ignoriert.

Da die `.ExternalHelp` Kommentarschlüsselwort wird ignoriert, die `Get-Help` Cmdlet kann Hilfeinformationen für skriptworkflows nur, wenn sie in Modulen enthalten sind.