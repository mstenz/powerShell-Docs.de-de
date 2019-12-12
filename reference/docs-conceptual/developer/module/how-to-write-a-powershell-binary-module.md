---
title: Schreiben eines PowerShell-Binär Moduls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367119"
---
# <a name="how-to-write-a-powershell-binary-module"></a>Schreiben eines PowerShell-Binärmoduls

Ein binäres Modul kann eine beliebige Assembly (DLL-Datei) sein, die Cmdlet-Klassen enthält. Standardmäßig werden alle Cmdlets in der Assembly importiert, wenn das binäre Modul importiert wird. Sie können jedoch die importierten Cmdlets einschränken, indem Sie ein Modul Manifest erstellen, dessen Stamm Modul die Assembly ist. (Beispielsweise kann der cmdletstoexport-Schlüssel des Manifests verwendet werden, um nur die benötigten Cmdlets zu exportieren.) Außerdem kann ein binäres Modul weitere Dateien, eine Verzeichnisstruktur und andere nützliche Verwaltungsinformationen enthalten, die ein einzelnes Cmdlet nicht.

Im folgenden Verfahren wird beschrieben, wie ein PowerShell-Binär Modul erstellt und installiert wird.

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>Erstellen und Installieren eines binären PowerShell-Moduls

1. Erstellen Sie eine binäre PowerShell-Projekt Mappe (z. b. ein C#in geschriebenes Cmdlet) mit den benötigten Funktionen, und stellen Sie sicher, dass Sie ordnungsgemäß ausgeführt wird.

   Aus Sicht des Codes ist das Kernstück eines binären Moduls einfach eine Cmdlet-Assembly. Tatsächlich behandelt PowerShell eine einzelne Cmdlet-Assembly als Modul im Hinblick auf das Laden und entladen, ohne zusätzlichen Aufwand für den Entwickler. Weitere Informationen zum Schreiben eines Cmdlets finden Sie unter [Schreiben eines Windows PowerShell-Cmdlets](../cmdlet/writing-a-windows-powershell-cmdlet.md).

2. Erstellen Sie ggf. den Rest der Lösung: (zusätzliche Cmdlets, XML-Dateien usw.), und beschreiben Sie Sie mit einem Modul Manifest.

   Neben der Beschreibung der Cmdlet-Assemblys in der Projekt Mappe kann ein Modul Manifest beschreiben, wie das Modul exportiert und importiert werden soll, welche Cmdlets verfügbar gemacht werden und welche zusätzlichen Dateien in das Modul gelangen.
   Wie bereits erwähnt, kann PowerShell ein binäres Cmdlet wie ein Modul ohne zusätzlichen Aufwand behandeln.
   Daher ist ein Modul Manifest besonders nützlich für das Kombinieren mehrerer Dateien in einem einzelnen Paket oder das explizite Steuern der Veröffentlichung für eine bestimmte Assembly.
   Weitere Informationen finden Sie unter Gewusst [wie: Schreiben eines PowerShell-Modul Manifests](how-to-write-a-powershell-module-manifest.md).

   Der folgende Code ist ein extrem einfacher C# Codeblock, der drei Cmdlets in der gleichen Datei enthält, die als Modul verwendet werden können.

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. Packen Sie die Projekt Mappe, und speichern Sie das Paket an einer beliebigen Stelle im PowerShell-Modulpfad.

   Die `PSModulePath` globale Umgebungsvariable beschreibt die Standard Pfade, die von PowerShell verwendet werden, um das Modul zu suchen. Beispielsweise wäre ein allgemeiner Pfad zum Speichern eines Moduls auf einem System `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`. Wenn Sie nicht die Standard Pfade verwenden, müssen Sie den Speicherort des Moduls während der Installation explizit angeben. Stellen Sie sicher, dass Sie einen Ordner erstellen, in dem das Modul gespeichert werden kann, da Sie möglicherweise den Ordner zum Speichern mehrerer Assemblys und Dateien für die Projekt Mappe benötigen.

   Beachten Sie, dass Sie das Modul nicht an einer beliebigen Stelle im `PSModulePath` installieren müssen. Dies sind lediglich die Standard Speicherorte, die PowerShell nach Ihrem Modul sucht. Es wird jedoch empfohlen, dies zu tun, es sei denn, Sie haben einen guten Grund, das Modul an anderer Stelle zu speichern. Weitere Informationen finden Sie unter [Installieren eines PowerShell-Moduls](./installing-a-powershell-module.md) und [Ändern des Installations Pfads des PowerShell-Moduls](./modifying-the-psmodulepath-installation-path.md).

4. Importieren Sie das Modul mit einem [Import-Module-](/powershell/module/Microsoft.PowerShell.Core/Import-Module)Befehl in PowerShell.

   Wenn Sie " [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) " aufrufen, wird das Modul in den aktiven Arbeitsspeicher geladen. Wenn Sie PowerShell 3,0 und höher verwenden, wird das einfache Aufrufen des Namens Ihres Moduls im Code ebenfalls importiert. Weitere Informationen finden Sie unter [Importieren eines PowerShell-Moduls](./importing-a-powershell-module.md).

## <a name="importing-snap-in-assemblies-as-modules"></a>Importieren von Snap-in-Assemblys als Module

Cmdlets und Anbieter, die in Snap-in-Assemblys vorhanden sind, können als binäre Module geladen werden. Wenn die Snap-in-Assemblys als binäre Module geladen werden, sind die Cmdlets und Anbieter im Snap-in für den Benutzer verfügbar, aber die Snap-in-Klasse in der Assembly wird ignoriert, und das Snap-in wird nicht registriert. Folglich können die von Windows PowerShell bereitgestellten Snap-in-Cmdlets das Snap-in nicht erkennen, obwohl die Cmdlets und Anbieter für die Sitzung verfügbar sind.

Außerdem können alle Formatierungs-oder Typen Dateien, auf die durch das Snap-in verwiesen wird, nicht als Teil eines binären Moduls importiert werden.
Zum Importieren der Formatierungs-und Typen Dateien müssen Sie ein Modul Manifest erstellen.
Weitere Informationen finden Sie unter Gewusst [wie: Schreiben eines PowerShell-Modul Manifests](how-to-write-a-powershell-module-manifest.md).

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Moduls](./writing-a-windows-powershell-module.md)
