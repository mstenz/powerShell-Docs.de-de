---
title: Schnellstart für Windows PowerShell-Anbieter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e879ba7-c334-460b-94a1-3e9b63d3d8de
caps.latest.revision: 5
ms.openlocfilehash: 949c0d63b1e5bca1bfe670362df4297c29e98fcc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359919"
---
# <a name="windows-powershell-provider-quickstart"></a>Windows PowerShell-Anbieter: Schnellstart

In diesem Thema wird erläutert, wie Sie einen Windows PowerShell-Anbieter erstellen, der über grundlegende Funktionen zum Erstellen eines neuen Laufwerks verfügt. Allgemeine Informationen zu Anbietern finden Sie unter [Übersicht über den Windows PowerShell-Anbieter](./windows-powershell-provider-overview.md). Beispiele für Anbieter mit Umfang vollem Funktionsumfang finden Sie unter [Anbieter Beispiele](./provider-samples.md).

## <a name="writing-a-basic-provider"></a>Schreiben eines einfachen Anbieters

Die grundlegendsten Funktionen eines Windows PowerShell-Anbieters sind das Erstellen und Entfernen von Laufwerken. In diesem Beispiel implementieren wir die [System. Management. Automation. Provider. drivecmdletprovider. newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) -und die [System. Management. Automation. Provider. drivecmdletprovider. removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) -Methode der [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Klasse. Außerdem erfahren Sie, wie Sie eine Anbieter Klasse deklarieren.

Wenn Sie einen Anbieter schreiben, können Sie Standard Laufwerke angeben, die automatisch erstellt werden, wenn der Anbieter verfügbar ist. Außerdem definieren Sie eine Methode, mit der neue Laufwerke erstellt werden, die diesen Anbieter verwenden.

Die in diesem Thema bereitgestellten Beispiele basieren auf dem [AccessDBProviderSample02](./accessdbprovidersample02.md) -Beispiel, das Teil eines größeren Beispiels ist, das eine Access-Datenbank als Windows PowerShell-Laufwerk darstellt.

### <a name="setting-up-the-project"></a>Einrichten des Projekts

Erstellen Sie in Visual Studio ein Klassen Bibliotheksprojekt mit dem Namen accessdbprovidersample. Führen Sie die folgenden Schritte aus, um das Projekt so zu konfigurieren, dass Windows PowerShell gestartet wird. der Anbieter wird dann in die Sitzung geladen, wenn Sie das Projekt erstellen und starten.

##### <a name="configure-the-provider-project"></a>Konfigurieren des Anbieter Projekts

1. Fügen Sie die System. Management. Automation-Assembly als Verweis auf das Projekt hinzu.

2. Klicken Sie **> Debuggen auf Projekt > accessdbprovidersample-Eigenschaften**. Klicken Sie unter **Projekt starten**auf **externes Programm starten**, und navigieren Sie zur ausführbaren Windows PowerShell-Datei (in der Regel c:\Windows\System32\WindowsPowerShell\v1.0\\. PowerShell. exe).

3. Geben Sie unter **Start Optionen**Folgendes in das Feld **Befehlszeilenargumente** ein: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>Deklarieren der Anbieter Klasse

Der Anbieter wird von der [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Klasse abgeleitet. Die meisten Anbieter, die echte Funktionen bereitstellen (Zugriff und Bearbeitung von Elementen, Navigation im Datenspeicher und das Festlegen und Festlegen von Inhalts Elementen), werden von der [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse abgeleitet.

Zusätzlich zur Angabe, dass die Klasse von [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)abgeleitet ist, müssen Sie Sie mit dem [System. Management. Automation. Provider. cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) ergänzen, wie im Beispiel gezeigt.

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System;
  using System.Data;
  using System.Data.Odbc;
  using System.IO;
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  #region AccessDBProvider

  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : DriveCmdletProvider
  {

}
}
```

### <a name="implementing-newdrive"></a>Implementieren von newdrive

Die [System. Management. Automation. Provider. drivecmdletprovider. newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) -Methode wird von der Windows PowerShell-Engine aufgerufen, wenn ein Benutzer das [Microsoft. PowerShell. Commands. newpsdrivecommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) -Cmdlet aufruft, das den Namen des Anbieters angibt. Der psdriveinfo-Parameter wird von der Windows PowerShell-Engine übergeben, und die-Methode gibt das neue Laufwerk an die Windows PowerShell-Engine zurück. Diese Methode muss innerhalb der oben erstellten-Klasse deklariert werden.

Die-Methode prüft zunächst, ob sowohl das Laufwerks Objekt als auch der Laufwerks Stamm vorhanden sind, die übergebenen sind, und gibt `null` zurück, wenn dies nicht der Fall ist. Anschließend wird ein Konstruktor der internen Klasse accessdbpsdriveingefo verwendet, um ein neues Laufwerk und eine Verbindung mit der Access-Datenbank zu erstellen, die das Laufwerk darstellt.

```csharp
protected override PSDriveInfo NewDrive(PSDriveInfo drive)
    {
      // Check if the drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   null));

        return null;
      }

      // Check if the drive root is not null or empty
      // and if it is an existing file.
      if (String.IsNullOrEmpty(drive.Root) || (File.Exists(drive.Root) == false))
      {
        WriteError(new ErrorRecord(
                   new ArgumentException("drive.Root"),
                   "NoRoot",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Create a new drive and create an ODBC connection to the new drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = new AccessDBPSDriveInfo(drive);
      OdbcConnectionStringBuilder builder = new OdbcConnectionStringBuilder();

      builder.Driver = "Microsoft Access Driver (*.mdb)";
      builder.Add("DBQ", drive.Root);

      OdbcConnection conn = new OdbcConnection(builder.ConnectionString);
      conn.Open();
      accessDBPSDriveInfo.Connection = conn;

      return accessDBPSDriveInfo;
    }
```

Im folgenden finden Sie die interne accessdbpsdriveinfo-Klasse, die den zum Erstellen eines neuen Laufwerks verwendeten Konstruktor enthält und die Zustandsinformationen für das Laufwerk enthält.

```csharp
internal class AccessDBPSDriveInfo : PSDriveInfo
  {
    /// <summary>
    /// A reference to the connection to the database.
    /// </summary>
    private OdbcConnection connection;

    /// <summary>
    /// Initializes a new instance of the AccessDBPSDriveInfo class.
    /// The constructor takes a single argument.
    /// </summary>
    /// <param name="driveInfo">Drive defined by this provider</param>
    public AccessDBPSDriveInfo(PSDriveInfo driveInfo)
           : base(driveInfo)
    {
    }

    /// <summary>
    /// Gets or sets the ODBC connection information.
    /// </summary>
    public OdbcConnection Connection
    {
        get { return this.connection; }
        set { this.connection = value; }
    }
  }
```

### <a name="implementing-removedrive"></a>Implementieren von removedrive

Die [System. Management. Automation. Provider. drivecmdletprovider. removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) -Methode wird von der Windows PowerShell-Engine aufgerufen, wenn ein Benutzer das Cmdlet " [Microsoft. PowerShell. Commands. removepsdrivecommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) " aufruft. Die-Methode in diesem Anbieter schließt die Verbindung mit der Access-Datenbank.

```csharp
protected override PSDriveInfo RemoveDrive(PSDriveInfo drive)
    {
      // Check if drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Close the ODBC connection to the drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = drive as AccessDBPSDriveInfo;

      if (accessDBPSDriveInfo == null)
      {
         return null;
      }

      accessDBPSDriveInfo.Connection.Close();

      return accessDBPSDriveInfo;
    }
```