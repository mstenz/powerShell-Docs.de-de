---
title: Benennen von Hilfedateien
ms.date: 09/12/2016
ms.openlocfilehash: ea95e6d6c87e553ed11fe6e3f058fc9a1b3d03f8
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893270"
---
# <a name="naming-help-files"></a>Benennen von Hilfedateien

In diesem Thema wird erläutert, wie Sie eine XML-basierte Hilfedatei benennen, damit Sie vom Cmdlet " [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) " gefunden werden kann. Die namens Anforderungen unterscheiden sich für jeden Befehlstyp.

## <a name="cmdlet-help-files"></a>Cmdlet-Hilfedateien

Die Hilfedatei für ein c#-Cmdlet muss für die Assembly, in der das Cmdlet definiert ist, benannt werden. Verwenden Sie das folgende Format des Datei namens:

```
<AssemblyName>.dll-help.xml
```

Das assemblynamensformat ist auch dann erforderlich, wenn es sich bei der Assembly um ein Netz Modul handelt.

Beispielsweise ist das [Get-WinEvent-](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) Cmdlet in der Microsoft.PowerShell.Diagnostics.dll-Assembly definiert. Das- `Get-Help` Cmdlet sucht in der- `Get-WinEvent` `Microsoft.PowerShell.Diagnostics.dll-help.xml` Datei im Modul Verzeichnis nach einem Hilfethema für das Cmdlet.

## <a name="provider-help-files"></a>Anbieter Hilfedateien

Die Hilfedatei für einen PowerShell-Anbieter muss für die Assembly benannt werden, in der der Anbieter definiert ist. Verwenden Sie das folgende Format des Datei namens:

`<AssemblyName>.dll-help.xml`

Das assemblynamensformat ist auch dann erforderlich, wenn es sich bei der Assembly um ein Netz Modul handelt.

Beispielsweise ist der Zertifikat Anbieter in der Assembly definiert `Microsoft.PowerShell.Security.dll` . Das- `Get-Help` Cmdlet sucht in der- `Microsoft.PowerShell.Security.dll-help.xml` Datei im Modul Verzeichnis nach einem Hilfethema für den Zertifikat Anbieter.

## <a name="function-help-files"></a>Funktionen-Hilfedateien

Funktionen können mithilfe der [Kommentar basierten Hilfe](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) dokumentiert werden oder in einer XML-Hilfedatei dokumentiert werden. Wenn die Funktion in einer XML-Datei dokumentiert ist, muss die Funktion über ein `.ExternalHelp` Kommentar Schlüsselwort verfügen, das die Funktion der XML-Datei zuordnet. Andernfalls kann das `Get-Help` Cmdlet die Hilfedatei nicht finden.

Es gibt keine technischen Anforderungen für den Namen einer Funktions Hilfedatei. Eine bewährte Vorgehensweise besteht jedoch darin, die Hilfedatei für das Skript Modul zu benennen, in dem die Funktion definiert ist. Beispielsweise ist die folgende Funktion in der Datei definiert `MyModule.psm1` .

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>CIM-Befehls Hilfedateien

Die Hilfedatei für einen CIM-Befehl muss für die cdxml-Datei benannt werden, in der der CIM-Befehl definiert ist. Verwenden Sie das folgende Format des Datei namens:

`<FileName>.cdxml-help.xml`

CIM-Befehle sind in cdxml-Dateien definiert, die in Module als geduckte Module eingeschlossen werden können. Wenn der CIM-Befehl als Funktion in die Sitzung importiert wird, fügt PowerShell `.ExternalHelp` der Funktionsdefinition ein Kommentar Schlüsselwort hinzu, das die Funktion einer XML-Hilfedatei zuordnet, die für die cdxml-Datei benannt ist, in der der CIM-Befehl definiert ist.

## <a name="script-workflow-help-files"></a>Skripterstellung für Workflow Hilfedateien

Skript Workflows, die in Modulen enthalten sind, können in XML-basierten Hilfedateien dokumentiert werden. Es gibt keine technischen Anforderungen für den Namen der Hilfedatei. Eine bewährte Vorgehensweise besteht jedoch darin, die Hilfedatei für das Skript Modul zu benennen, in dem der Skript Workflow definiert ist. Beispiel:

`<ScriptModule>.psm1-help.xml`

Im Gegensatz zu anderen Skript gesteuerten Befehlen benötigen Skript Workflows kein `.ExternalHelp` Kommentar Schlüsselwort, um Sie einer Hilfedatei zuzuordnen. Stattdessen durchsucht PowerShell die Benutzeroberflächen kulturspezifischen Unterverzeichnisse des Modul Verzeichnisses nach XML-basierten Hilfedateien und sucht in allen Dateien nach Hilfe für den Skript Workflow. `.ExternalHelp`das Kommentar Schlüsselwort wird ignoriert.

Da das `.ExternalHelp` Kommentar Schlüsselwort ignoriert wird, `Get-Help` kann das Cmdlet Hilfe zu Skript Workflows nur dann finden, wenn Sie in Modulen enthalten sind.
