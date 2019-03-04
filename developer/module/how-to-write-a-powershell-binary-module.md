---
title: 'Gewusst wie: Schreiben ein PowerShell-Binärdateien-Moduls | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: 9ddb3bc172c66314603d2be4df5192a76c92e05d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856486"
---
# <a name="how-to-write-a-powershell-binary-module"></a>Schreiben eines PowerShell-Binärmoduls

Ein binäres Modul kann es sich um eine beliebige Assembly (DLL) sein, die Cmdlet-Klassen enthält. Standardmäßig werden alle Cmdlets in der Assembly importiert, wenn das binäre Modul importiert wird. Allerdings können Sie die Cmdlets beschränken, die importiert werden, erstellen Sie ein modulmanifest, dessen stammmodul die Assembly ist. (Z. B. der Schlüssel CmdletsToExport des Manifests dienen nur diese Cmdlets zu exportieren, die erforderlich sind.) Darüber hinaus kann ein binäres Modul enthalten, zusätzliche Dateien, eine Verzeichnisstruktur und andere Angaben hilfreiches Verwaltungstool, für die ein einzelnes Cmdlet nicht.

Das folgende Verfahren beschreibt die zum Erstellen und ein binäres PowerShell-Modul installieren.

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>Das Erstellen und installieren ein binäres PowerShell-Modul

1. Erstellen Sie eine binäre PowerShell-Projektmappe (z. B. ein Cmdlet in geschriebenen C#), mit den Funktionen benötigt werden, und stellen Sie sicher, dass es ordnungsgemäß ausgeführt wird.

   Hinsichtlich der Code ist der Kern von einem binären Modul einfach eine Cmdlet-Assembly. In der Tat werden in PowerShell eine einzelnes Cmdlet-Assembly als Modul im Hinblick auf das Laden und Entladen von Assemblys, mit keinen zusätzlichen Aufwand seitens des Entwicklers behandelt werden. Weitere Informationen zu einem Cmdlet schreiben, finden Sie unter [Schreiben eines Windows PowerShell-Cmdlets](../cmdlet/writing-a-windows-powershell-cmdlet.md).

2. Erstellen Sie bei Bedarf den Rest der Lösung: (Weitere Cmdlets, XML-Dateien usw.) und eine Beschreibung für diese mit einem modulmanifest.

   Neben einer Beschreibung der Cmdlet-Assemblys in Ihrer Lösung, kann ein modulmanifest beschreiben, wie Ihr Modul exportiert und importiert werden sollen, welche Cmdlets verfügbar gemacht werden und was zusätzliche Dateien in das Modul gespeichert werden. Wie zuvor jedoch bereits erwähnt, kann ein binary-Cmdlet wie ein Modul mit keinen zusätzlichen Aufwand PowerShell behandelt werden. Daher empfiehlt sich ein modulmanifest hauptsächlich für das Kombinieren mehrerer Dateien in einem einzelnen Paket für die Veröffentlichung für eine bestimmte Assembly explizit zu steuern. Weitere Informationen finden Sie unter [Gewusst wie: Schreiben eines Modulmanifests PowerShell](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).

   Der folgende Code ist ein extrem einfaches C# Codeblock mit drei Cmdlets in der gleichen Datei, die als Modul verwendet werden kann.

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

3. Packen Sie die Projektmappe, und speichern Sie das Paket an eine Position in der PowerShell-Modul-Pfad.

   Die `PSModulePath` globalen Umgebungsvariablen beschreibt die Standardpfade, die mithilfe von PowerShell wird Ihr Modul zu suchen. Z. B. ein gemeinsamen Pfad um ein Modul auf einem System zu speichern wäre `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`. Wenn Sie die Standardpfade nicht verwenden, müssen Sie explizit angeben, den Speicherort Ihres Moduls während der Installation. Achten Sie darauf, dass Sie einen Ordner zum Speichern Ihres Moduls, zu erstellen, wie Sie den Ordner zum Speichern von mehreren Assemblys und Dateien für Ihre Lösung benötigen.

   Beachten Sie, dass technisch Sie nicht benötigen, Ihrem Modul eine beliebige Stelle auf installieren die `PSModulePath` -sind einfach die Standardspeicherorte, die PowerShell für Ihr Modul aussehen wird. Allerdings wird dies empfiehlt sich, hierzu betrachtet, es sei denn, Sie einen guten Grund haben für das Speichern von Ihrem Modul an anderer Stelle. Weitere Informationen finden Sie unter [Installieren eines PowerShell-Moduls](./installing-a-powershell-module.md) und [ändern den Installationspfad der PowerShell-Modul](./modifying-the-psmodulepath-installation-path.md).

4. Importieren des Moduls in PowerShell mit einem Aufruf von [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).

   Zum Aufrufen von [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) wird Ihr Modul in den aktiven Arbeitsspeicher geladen. Wenn Sie PowerShell 3.0 verwenden, und später im Code den Namen Ihres Moduls aufrufen importiert werden wird; Weitere Informationen finden Sie unter [Importieren eines PowerShell-Moduls](./importing-a-powershell-module.md).

## <a name="importing-snap-in-assemblies-as-modules"></a>-Snap-in-Assemblys werden als Module importiert.

-Cmdlets und Anbietern, die in-Snap-in-Assemblys vorhanden sind, können als binäre Module geladen werden. Wenn die-Snap-in-Assemblys als binäre Module geladen werden, die Cmdlets und Anbieter in das Snap-in für den Benutzer verfügbar sind, aber die Snap-in-Klasse in der Assembly wird ignoriert, und das Snap-in ist nicht registriert. Daher kann-Snap-in-Cmdlets, die von Windows PowerShell bereitgestellte das Snap-in nicht erkennen, obwohl die Cmdlets und Anbieter für die Sitzung verfügbar sind.

Darüber hinaus können keine formatierungs- oder Typen Dateien, die durch das Snap-in verwiesen werden, als Teil von einem binären Modul importiert werden. Um die Formatierung und Typen-Dateien importieren, müssen Sie ein modulmanifest erstellen. Angezeigt wird, [Gewusst wie: Schreiben Sie ein PowerShell-Modulmanifest](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Moduls](./writing-a-windows-powershell-module.md)
