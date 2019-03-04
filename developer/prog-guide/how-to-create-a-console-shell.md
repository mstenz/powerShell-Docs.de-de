---
title: 'Vorgehensweise: erstellen eine Shell Konsole | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Make-Shell [PowerShell Programmer's Guide]
ms.assetid: 6c24dd44-a8ec-421d-ac86-90912e1a8cc6
caps.latest.revision: 5
ms.openlocfilehash: 7166881bd1403ea8c81ec2928321f6b93e3ac58d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853496"
---
# <a name="how-to-create-a-console-shell"></a>Erstellen einer Konsolenshell

Windows PowerShell bietet es sich um ein stellen-Shell-Tool, auch bezeichnet als das "Make-Kit", das verwendet wird, um eine Konsole Shell erstellen, die nicht erweiterbar ist. Shells, die mit diesem neuen Tool erstellten können nicht später durch ein Windows PowerShell-Snap-in erweitert werden.

## <a name="syntax"></a>Syntax

Hier ist die Syntax zum Ausführen von Stellen-Shell aus innerhalb einer stellen-Datei verwendet.

```
make-shell
  -out n.exe
  -namespace ns
  [ -lib libdirectory1[,libdirectory2,..] ]
  [ -reference ca1.dll[,ca2.dll,...] ]
  [ -formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...] ]
  [ -typedata td1.type.ps1xml[,td2.type.ps1xml,...] ]
  [ -source c1.cs [,c2.cs,...] ]
  [ -authorizationmanager authorizationManagerType ]
  [ -win32icon i.ico ]
  [ -initscript p.ps1 ]
  [ -builtinscript s1.ps1[,s2.ps1,...] ]
  [ -resource resourcefile.txt ]
  [ -cscflags cscFlags ]
  [ -? | -help ]
```

## <a name="parameters"></a>Parameter

Hier ist eine kurze Beschreibung der Parameter der Stellen-Shell.

> [!CAUTION]
> UNC-Pfade zu Assemblys werden von Stellen-Shell nicht unterstützt.

|Parameter|Beschreibung|
|---------------|-----------------|
|-out n.exe|Erforderlich. Der Name der Shell zu erzeugen. Der Pfad wird als Teil dieser Parameter angegeben.<br /><br /> Make-Shell wird ".exe" auf diesen Wert angefügt werden, wenn er nicht angegeben ist. **Vorsicht:**  Erstellen Sie eine Ausgabedatei nicht mit dem gleichen Namen wie die referenzierten DLL-Datei. Wenn Sie dies versuchen, erstellt das stellen-Shell-Tool eine CS-Datei mit dem gleichen Namen, der in der CS-Datei überschrieben werden, die den Cmdlet-Quellcode aufweist.|
|-Namespace ns|Erforderlich. Der Namespace für die Verwendung für die abgeleitete [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) -Klasse, die die Stellen-Kit generiert und kompiliert.|
|-lib libdirectory1 [, libdirectory2,...]|Die Verzeichnisse, die für .NET-Assemblys, einschließlich der Windows PowerShell-Assemblys vom angegebenen Assemblys durchsucht werden die `reference` -Parameter, Assemblys, die auf die indirekt von einer anderen Assembly verwiesen wird und die System-Assemblys von .NET.|
|-verweisen ca1.dll[,ca2.dll,...]|Eine durch Trennzeichen getrennte Liste der Assemblys, die in der Shell enthalten. Diese Assemblys enthält alle Cmdlets und Anbieterassemblys sowie Ressourcenassemblys, die geladen werden soll. Wenn dieser Parameter nicht angegeben wird, wird Klicken Sie dann eine Shell erzeugt, die nur die Kern-Cmdlets und Anbieter, die von Windows PowerShell bereitgestellt enthält.<br /><br /> Die Assemblys mithilfe von deren vollständiger Pfad angegeben werden, andernfalls werden sie für die Verwendung von angegebenen Pfads durchsucht werden die `lib` Parameter.|
|-formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...]|Eine durch Trennzeichen getrennte Liste der Formatdaten in der Shell eingeschlossen werden sollen. Wenn dieser Parameter nicht angegeben wird, wird Klicken Sie dann eine Shell erzeugt, die nur die Formatdaten, die von Windows PowerShell bereitgestellte enthält.|
|-Typedata-td1.type.ps1xml[,td2.type.ps1xml,...]|Eine durch Trennzeichen getrennte Liste von Daten vom Typ in der Shell eingeschlossen werden sollen. Wenn dieser Parameter nicht angegeben wird, wird Klicken Sie dann eine Shell erzeugt, die nur die Typdaten, die von Windows PowerShell bereitgestellte enthält.|
|-Quelle c1.cs [, c2.cs,...]|Der Name einer Datei, die von der Shell-Entwickler, mit dem Source Code zum Erstellen von der Shell benötigt bereitgestellt.<br /><br /> Die Quellcodedatei kann eine der folgenden Quellcode enthalten:<br /><br /> -Die Autorisierungs-Manager-Implementierung, die den Autorisierungs-Manager für standardmäßige überschreibt. (Dies kann auch angegeben werden in eine Assembly kompiliert.)<br />-Assembly nur zu Informationszwecken Attributdeklarationen: z. B. AssemblyCompanyAttribute-, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute-, AssemblyProductAttribute-, und AssemblyTrademarkAttribute.|
|-authorizationmanager authorizationManagerType|Der Typ, der die Autorisierungs-Manager-Implementierung enthält. Dies kann im Quellcode definiert sein in eine Assembly kompiliert (angegeben durch die `reference` Parameter). Wenn dieser Parameter nicht angegeben ist, wird der standardmäßige-Manager verwendet. Der Wert sollte der vollständige Typname, einschließlich Namespaces sein.|
|-win32icon i.ico|Das Symbol für die .exe-Datei für die Shell. Wenn nicht angegeben ist, haben die Shell das Symbol ist, das der c#-Compiler (sofern vorhanden) enthält.|
|-Initscript p.ps1|Das Start-Profil für die Shell. Die Datei enthalten ist "als-ist"; keine Prüfung der Gültigkeit erfolgt durch stellen-Shell.|
|-Builtinscript s1.ps1[,s2.ps1,...]|Eine Liste der integrierten Skripts für die Shell. Diese Skripts werden ermittelt, bevor Sie Skripts in den Pfad ein, und ihr Inhalt können nicht geändert werden, nachdem die Shell vorgesehen ist.<br /><br /> Die Dateien befinden sich "als-ist"; keine Prüfung der Gültigkeit erfolgt durch stellen-Shell.|
|-Resource-resourcefile.txt|Die TXT-Datei, die Hilfe und Banner Ressourcen für die Shell enthält. Die erste Ressource heißt ShellHelp und enthält den Text angezeigt, wenn die Shell aufgerufen wird, mit der `help` Parameter. Die zweite Ressource heißt ShellBanner, und er enthält den Text und das copyright-Informationen angezeigt, wenn die Shell im interaktiven Modus gestartet wird.<br /><br /> Wenn dieser Parameter nicht angegeben oder diese Ressourcen nicht vorhanden sind, werden eine allgemeine Hilfe und Banner verwendet.|
|-Cscflags cscFlags|Flags, die an übergeben werden sollen die C# -Compilers (csc.exe). Diese werden unverändert übergeben. Wenn dieser Parameter Leerzeichen enthält, sollte er in doppelte Anführungszeichen eingeschlossen werden.|
|-?<br /><br /> -Hilfe|Zeigt die copyright-Meldung und stellen-Shell-Befehlszeilenoptionen.|
|-verbose|Zeigt detaillierte Informationen, während die Shell erstellt wird.|

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell Handbuch für Programmierer](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)