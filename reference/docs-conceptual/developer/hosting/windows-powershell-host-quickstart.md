---
title: Schnellstart für Windows PowerShell-Host | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 390eb2d0153c65967d8c0711c852aa6e13fe4660
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360819"
---
# <a name="windows-powershell-host-quickstart"></a>Windows PowerShell-Host: Schnellstart

Um Windows PowerShell in Ihrer Anwendung zu hosten, verwenden Sie die [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) -Klasse.
Diese Klasse stellt Methoden bereit, mit denen eine Pipeline von Befehlen erstellt und diese Befehle anschließend in einem Runspace ausgeführt werden.
Die einfachste Möglichkeit zum Erstellen einer Host Anwendung besteht darin, den standardrunspace zu verwenden.
Der Standard-Runspace enthält alle Windows PowerShell-Kern Befehle.
Wenn Sie möchten, dass Ihre Anwendung nur eine Teilmenge der Windows PowerShell-Befehle verfügbar macht, müssen Sie einen benutzerdefinierten Runspace erstellen.

## <a name="using-the-default-runspace"></a>Verwenden des Standard-Runspace

Zunächst verwenden wir den standardrunspace und verwenden die Methoden der [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) -Klasse, um einer Pipeline Befehle, Parameter, Anweisungen und Skripts hinzuzufügen.

### <a name="addcommand"></a>AddCommand

Verwenden Sie die [System. Management. Automation. PowerShell. AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) -Methode, um der Pipeline Befehle hinzuzufügen.
Angenommen, Sie möchten die Liste der ausgelaufenden Prozesse auf dem Computer erhalten.
Der Befehl kann wie folgt ausgeführt werden.

1. Erstellen Sie ein [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) -Objekt.

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. Fügen Sie den Befehl hinzu, den Sie ausführen möchten.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. Rufen Sie den Befehl auf.

   ```csharp
   ps.Invoke();
   ```

Wenn Sie die AddCommand-Methode mehrmals aufrufen, bevor Sie die [System. Management. Automation. PowerShell. aufrufen](/dotnet/api/System.Management.Automation.PowerShell.Invoke) -Methode aufrufen, wird das Ergebnis des ersten Befehls an die zweite weitergeleitet usw.
Wenn Sie das Ergebnis eines vorherigen Befehls nicht an einen Befehl übergeben möchten, fügen Sie es hinzu, indem Sie stattdessen die [System. Management. Automation. PowerShell. addstatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) aufrufen.

### <a name="addparameter"></a>AddParameter

Das vorherige Beispiel führt einen einzelnen Befehl ohne Parameter aus.
Sie können dem Befehl Parameter hinzufügen, indem Sie die [System. Management. Automation. PSCommand. AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) -Methode verwenden.
Der folgende Code ruft beispielsweise eine Liste aller Prozesse ab, die `PowerShell` auf dem Computer ausgeführt werden.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

Sie können zusätzliche Parameter hinzufügen, indem Sie die AddParameter-Methode wiederholt aufrufen.

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

Sie können auch ein Wörterbuch mit Parameternamen und-Werten hinzufügen, indem Sie die [System. Management. Automation. PowerShell. AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) -Methode aufrufen.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>Addstatement

Sie können die Batch Verarbeitung simulieren, indem Sie die [System. Management. Automation. PowerShell. addstatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) -Methode verwenden, mit der am Ende der Pipeline eine zusätzliche-Anweisung hinzugefügt wird.
Der folgende Code Ruft eine Liste der laufenden Prozesse mit dem Namen `PowerShell`ab und ruft dann die Liste der laufenden Dienste ab.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

Sie können ein vorhandenes Skript ausführen, indem Sie die [System. Management. Automation. PowerShell. addScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) -Methode aufrufen.
Das folgende Beispiel fügt der Pipeline ein Skript hinzu und führt es aus.
In diesem Beispiel wird davon ausgegangen, dass bereits ein Skript mit dem Namen `MyScript.ps1` in einem Ordner namens `D:\PSScripts`vorhanden ist.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

Es gibt auch eine Version der addScript-Methode, die einen booleschen Parameter namens "`useLocalScope`" annimmt.
Wenn dieser Parameter auf `true`festgelegt ist, wird das Skript im lokalen Gültigkeitsbereich ausgeführt.
Mit dem folgenden Code wird das Skript im lokalen Gültigkeitsbereich ausgeführt.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>Erstellen eines benutzerdefinierten Runspace

Während der Standard-Runspace, der in den vorherigen Beispielen verwendet wird, alle Windows PowerShell-Kern Befehle lädt, können Sie einen benutzerdefinierten Runspace erstellen, der nur eine bestimmte Teilmenge aller Befehle lädt.
Dies ist möglicherweise sinnvoll, um die Leistung zu verbessern (das Laden einer größeren Anzahl von Befehlen ist eine Leistungs Beeinträchtigung) oder um die Fähigkeit des Benutzers einzuschränken, Vorgänge auszuführen.
Ein Runspace, der nur eine begrenzte Anzahl von Befehlen verfügbar macht, wird als eingeschränkter Runspace bezeichnet.
Um einen eingeschränkten Runspace zu erstellen, verwenden Sie die Klassen " [System. Management. Automation. Runspaces. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) " und " [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) ".

### <a name="creating-an-initialsessionstate-object"></a>Erstellen eines initialsessionstate-Objekts

Um einen benutzerdefinierten Runspace zu erstellen, müssen Sie zunächst ein [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt erstellen.
Im folgenden Beispiel wird mithilfe von [System. Management. Automation. Runspaces. runspacefactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) ein Runspace erstellt, nachdem ein Standardmäßiges initialsessionstate-Objekt erstellt wurde.

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>Einschränken des Runspace

Im vorherigen Beispiel haben wir ein Standardmäßiges [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt erstellt, das alle integrierten Windows PowerShell-Kernfunktionen lädt.
Wir könnten auch die [System. Management. Automation. Runspaces. initialsessionstate. CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) -Methode aufrufen, um ein initialsessionstate-Objekt zu erstellen, das nur die Befehle im Microsoft. PowerShell. Core-Snap-in Laden würde.
Um einen eingeschränkteren Runspace zu erstellen, müssen Sie ein leeres initialsessionstate-Objekt erstellen, indem Sie die [System. Management. Automation. Runspaces. initialsessionstate. Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) -Methode aufrufen und dann den initialsessionstate-Befehlen hinzufügen.

Wenn Sie einen Runspace verwenden, der nur die von Ihnen angegebenen Befehle lädt, wird die Leistung erheblich verbessert.

Verwenden Sie die Methoden der [System. Management. Automation. Runspaces. sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) -Klasse, um Cmdlets für den anfänglichen Sitzungs Status zu definieren.
Im folgenden Beispiel wird ein leerer ursprünglicher Sitzungszustand erstellt. Anschließend werden die `Get-Command`-und `Import-Module`-Befehle definiert und dem anfänglichen Sitzungszustand hinzugefügt.
Anschließend erstellen wir einen durch diesen anfänglichen Sitzungs Status eingeschränkten Runspace und führen die Befehle in diesem Runspace aus.

Erstellen Sie den anfänglichen Sitzungszustand.

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

Definieren und Hinzufügen von Befehlen zum anfänglichen Sitzungszustand.

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

Erstellen Sie den Runspace, und öffnen Sie ihn.

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

Führen Sie einen Befehl aus, um das Ergebnis anzuzeigen.

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

Wenn Sie ausführen, wird die Ausgabe dieses Codes wie folgt aussehen.

```powershell
Get-Command
Import-Module
```
