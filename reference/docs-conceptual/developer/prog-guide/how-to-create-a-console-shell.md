---
title: Erstellen einer Konsolen Shell | Microsoft-Dokumentation
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
ms.openlocfilehash: 5ddf312228cb17628400ce8d8a3abbf9c888439e
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560320"
---
# <a name="how-to-create-a-console-shell"></a>Erstellen einer Konsolenshell

Windows PowerShell stellt ein Make-Shell-Tool bereit, das auch als "Make-Kit" bezeichnet wird und zum Erstellen einer Konsolen Shell verwendet wird, die nicht erweiterbar ist. Mit diesem neuen Tool erstellte Shells können nicht später über ein Windows PowerShell-Snap-in erweitert werden.

## <a name="syntax"></a>Syntax

Im folgenden finden Sie die Syntax, die zum Ausführen von Make-Shell aus einer Make-Datei verwendet wird.

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

Im folgenden finden Sie eine kurze Beschreibung der Parameter von Make-Shell.

> [!CAUTION]
> UNC-Pfade zu Assemblys werden von der Make-Shell nicht unterstützt.

|Parameter|Beschreibung|
|---------------|-----------------|
|-Out n. exe|Erforderlich. Der Name der zu erstellenden Shell. Der Pfad wird als Teil dieses Parameters angegeben.<br /><br /> "Make-Shell" fügt ". exe" an diesen Wert an, wenn er nicht angegeben ist. **Vorsicht:**  Erstellen Sie keine Ausgabedatei mit demselben Namen wie die DLL-Datei, auf die verwiesen wird. Wenn Sie dies versuchen, erstellt das Make-Shell-Tool eine CS-Datei mit dem gleichen Namen, die die CS-Datei mit dem Cmdlet-Quellcode überschreibt.|
|-Namespace-NS|Erforderlich. Der Namespace, der für die abgeleitete [System. Management. Automation. Runspaces. runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) -Klasse verwendet werden soll, die vom Make-Kit generiert und kompiliert wird.|
|-lib libdirectory1 [, libdirectory2,..]|Die Verzeichnisse, die nach .NET-Assemblys durchsucht werden, einschließlich der Windows PowerShell-Assemblys, der durch den-Parameter angegebenen Assemblys, Assemblys, `reference` auf die von einer anderen Assembly indirekt verwiesen|
|-Reference CA1. dll [, Ca2. dll,...]|Eine durch Trennzeichen getrennte Liste der Assemblys, die in der Shell enthalten sein sollen. Diese Assemblys enthalten alle Cmdlets und anbieteassemblys sowie Ressourcenassemblys, die geladen werden sollten. Wenn dieser Parameter nicht angegeben wird, wird eine Shell erstellt, die nur die Kern-Cmdlets und Anbieter enthält, die von Windows PowerShell bereitgestellt werden.<br /><br /> Die Assemblys können mithilfe Ihres vollständigen Pfads angegeben werden. andernfalls werden Sie nach dem durch den-Parameter angegebenen Pfad durchsucht `lib` .|
|-formatdata fd1. Format. ps1xml [, FD2. Format. ps1xml,...]|Eine durch Trennzeichen getrennte Liste von Format Daten, die in der Shell enthalten sein sollen. Wenn dieser Parameter nicht angegeben wird, wird eine Shell erstellt, die nur die von Windows PowerShell bereitgestellten Formatierungsdaten enthält.|
|-typedata TD1. Type. ps1xml [, TD2. Type. ps1xml,...]|Eine durch Trennzeichen getrennte Liste von Typdaten, die in der Shell enthalten sein sollen. Wenn dieser Parameter nicht angegeben wird, wird eine Shell erstellt, die nur die Typdaten enthält, die von Windows PowerShell bereitgestellt werden.|
|-Quelle C1.cs [, C2.cs,...]|Der Name einer Datei, die vom shellentwickler bereitgestellt wird und den Quellcode enthält, der zum Erstellen der Shell erforderlich ist.<br /><br /> Die Quell Code Datei kann jeden der folgenden Quell Code enthalten:<br /><br /> : Die Autorisierungs-Manager-Implementierung, die den Standard Autorisierungs-Manager überschreibt. (Dies kann auch in eine Assembly kompiliert werden.)<br />-Assembly-Informations Attribut Deklarationen: z. b. AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute und AssemblyTrademarkAttribute.|
|-AuthorizationManager authorizationmanagertype|Der Typ, der die Autorisierungs-Manager-Implementierung enthält. Dies kann im Quellcode definiert oder in eine Assembly (angegeben durch den- `reference` Parameter) kompiliert werden. Wenn dieser Parameter nicht angegeben wird, wird der Standard Sicherheits-Manager verwendet. Der Wert muss der vollständige Typname sein, einschließlich der Namespaces.|
|-win32icon i. ico|Das Symbol für die exe-Datei für die Shell. Wenn kein Wert angegeben wird, hat die Shell das Symbol, das der c#-Compiler enthält (sofern vorhanden).|
|-Initscript p. ps1|Das Start Profil für die Shell. Die Datei ist "unverändert" enthalten. keine Gültigkeits Überprüfung erfolgt durch make-Shell.|
|-builtinscript S1. ps1 [, S2. ps1,...]|Eine Liste der integrierten Skripts für die Shell. Diese Skripts werden vor Skripts im Pfad erkannt, und ihre Inhalte können nicht mehr geändert werden, nachdem die Shell erstellt wurde.<br /><br /> Die Dateien sind unverändert enthalten. keine Gültigkeits Überprüfung erfolgt durch make-Shell.|
|-Resource resourceFile. txt|Die txt-Datei, die Hilfe-und Banner Ressourcen für die Shell enthält. Die erste Ressource heißt "shellhelp" und enthält den Text, der angezeigt wird, wenn die Shell mit dem-Parameter aufgerufen wird `help` . Die zweite Ressource heißt shellbanner und enthält den Text und die Copyright Informationen, die angezeigt werden, wenn die Shell im interaktiven Modus gestartet wird.<br /><br /> Wenn dieser Parameter nicht angegeben wird oder diese Ressourcen nicht vorhanden sind, werden eine generische Hilfe und ein Banner verwendet.|
|cscflags-cscflags|Flags, die an den c#-Compiler (CSC. exe) übergeben werden sollen. Diese werden unverändert übermittelt. Wenn dieser Parameter Leerzeichen enthält, sollte er in doppelte Anführungszeichen eingeschlossen werden.|
|-?<br /><br /> -help|Zeigt die Copyright Meldung und die Befehlszeilenoptionen für die Befehlszeile an.|
|-verbose|Zeigt ausführliche Informationen an, während die Shell erstellt wird.|

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell-Programmiererhandbuch](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
