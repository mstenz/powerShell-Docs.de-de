---
title: Benennen von Hilfedateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367009"
---
# <a name="naming-help-files"></a>Benennen von Hilfedateien

In diesem Thema wird erläutert, wie Sie eine XML-basierte Hilfedatei benennen, damit Sie vom Cmdlet " [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) " gefunden werden kann. Die namens Anforderungen unterscheiden sich für jeden Befehlstyp.

## <a name="cmdlet-help-files"></a>Cmdlet-Hilfedateien

Die Hilfedatei für ein C# Cmdlet muss für die Assembly, in der das Cmdlet definiert ist, benannt werden. Verwenden Sie das folgende Format des Datei namens:

```
<AssemblyName>.dll-help.xml
```

Das assemblynamensformat ist auch dann erforderlich, wenn es sich bei der Assembly um ein Netz Modul handelt.

Beispiel: [Get-WinEvent; PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) -Cmdlet ist in der Microsoft. PowerShell. Diagnostics. dll-Assembly definiert. Das Cmdlet "`Get-Help`" sucht in der Datei "Microsoft. PowerShell. Diagnostics. dll-Help. xml" im Modul Verzeichnis nach einem Hilfethema für das Cmdlet "`Get-WinEvent`".

## <a name="provider-help-files"></a>Anbieter Hilfedateien

Die Hilfedatei für einen Windows PowerShell-Anbieter muss für die Assembly benannt werden, in der der Anbieter definiert ist. Verwenden Sie das folgende Format des Datei namens:

```
<AssemblyName>.dll-help.xml
```

Das assemblynamensformat ist auch dann erforderlich, wenn es sich bei der Assembly um ein Netz Modul handelt.

Der Zertifikat Anbieter wird z. b. in der Microsoft. PowerShell. Security. dll-Assembly definiert. Das Cmdlet "`Get-Help`" sucht in der Datei "Microsoft. PowerShell. Security. dll-Help. xml" im Modul Verzeichnis nach einem Hilfethema für den Zertifikat Anbieter.

## <a name="function-help-files"></a>Funktionen-Hilfedateien

Funktionen können mithilfe der [Kommentar basierten Hilfe](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) dokumentiert werden oder in einer XML-Hilfedatei dokumentiert werden. Wenn die Funktion in einer XML-Datei dokumentiert ist, muss die Funktion über ein Kommentar Schlüsselwort `.ExternalHelp` verfügen, das die Funktion der XML-Datei zuordnet. Andernfalls kann das Cmdlet "`Get-Help`" die Hilfedatei nicht finden.

Es gibt keine technischen Anforderungen für den Namen einer Funktions Hilfedatei. Eine bewährte Vorgehensweise besteht jedoch darin, die Hilfedatei für das Skript Modul zu benennen, in dem die Funktion definiert ist. Beispielsweise ist die folgende Funktion in der Datei "MyModule. psm1" definiert.

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>CIM-Befehls Hilfedateien

Die Hilfedatei für einen CIM-Befehl muss für die cdxml-Datei benannt werden, in der der CIM-Befehl definiert ist. Verwenden Sie das folgende Format des Datei namens:

```
<FileName>.cdxml-help.xml
```

CIM-Befehle sind in cdxml-Dateien definiert, die in Module als geduckte Module eingeschlossen werden können. Wenn der CIM-Befehl als Funktion in die Sitzung importiert wird, fügt Windows PowerShell der Funktionsdefinition ein `.ExternalHelp`-Kommentar Schlüsselwort hinzu, das die Funktion einer XML-Hilfedatei zuordnet, die für die cdxml-Datei benannt ist, in der der CIM-Befehl definiert ist.

## <a name="script-workflow-help-files"></a>Skripterstellung für Workflow Hilfedateien

Skript Workflows, die in Modulen enthalten sind, können in XML-basierten Hilfedateien dokumentiert werden. Es gibt keine technischen Anforderungen für den Namen der Hilfedatei. Eine bewährte Vorgehensweise besteht jedoch darin, die Hilfedatei für das Skript Modul zu benennen, in dem der Skript Workflow definiert ist. Beispiel:

```
<ScriptModule>.psm1-help.xml
```

Im Gegensatz zu anderen Skript gesteuerten Befehlen benötigen Skript Workflows kein `.ExternalHelp`-Kommentar Schlüsselwort, um Sie einer Hilfedatei zuzuordnen. Stattdessen durchsucht Windows PowerShell die Benutzeroberflächen kulturspezifischen Unterverzeichnisse des Modul Verzeichnisses nach XML-basierten Hilfedateien und sucht in allen Dateien nach Hilfe für den Skript Workflow. `.ExternalHelp`-Kommentar Schlüsselwort wird ignoriert.

Da das Kommentar Schlüsselwort `.ExternalHelp` ignoriert wird, kann das `Get-Help`-Cmdlet Hilfe zu Skript Workflows nur dann finden, wenn Sie in Module enthalten sind.