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
ms.openlocfilehash: 151b7125afe1b0d386467a0e5f89225716857ac2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080882"
---
# <a name="windows-powershell-provider-quickstart"></a>Windows PowerShell-Anbieter: Schnellstart

In diesem Thema wird erläutert, wie Sie einen Windows PowerShell-Anbieter erstellen, die grundlegende Funktionalität zum Erstellen eines neuen Laufwerks. Allgemeine Informationen zu Anbietern finden Sie unter [Übersicht über Windows PowerShell-Anbieter](./windows-powershell-provider-overview.md). Beispiele für vollständige Funktionalität Anbieter, finden Sie unter [Beispiele für Tabellenprofilanbieter](./provider-samples.md).

## <a name="writing-a-basic-provider"></a>Schreiben eines einfachen Anbieters

Die Grundfunktionen von einem Windows PowerShell-Anbieter ist zum Erstellen und Entfernen von Laufwerken. In diesem Beispiel implementieren wir die [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) und [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) Methoden der [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Klasse. Außerdem sehen Sie, wie eine Anbieterklasse deklariert.

Wenn Sie einen Anbieter schreiben, können Sie standardmäßige Laufwerken-Laufwerke angeben, die automatisch erstellt werden, wenn der Anbieter verfügbar ist. Außerdem definieren Sie eine Methode zum Erstellen von neuen Laufwerke, die diesen Anbieter verwenden.

Die Beispiele in diesem Thema basieren auf der [AccessDBProviderSample02](./accessdbprovidersample02.md) Beispiel, das Teil eines umfangreicheren Beispiels ist, die eine Access-Datenbank als ein Windows PowerShell-Laufwerk darstellt.

### <a name="setting-up-the-project"></a>Einrichten des Projekts

Erstellen Sie in Visual Studio ein Klassenbibliotheksprojekt namens AccessDBProviderSample. Führen Sie die folgenden Schritte aus, um Ihr Projekt konfigurieren, damit Windows PowerShell wird gestartet, und der Anbieter wird in der Sitzung geladen werden, wenn Sie beim Erstellen und starten Sie Ihr Projekt.

##### <a name="configure-the-provider-project"></a>Konfigurieren Sie das Anbieterprojekt

1. Fügen Sie die System.Management.Automation-Assembly als Verweis zum Projekt hinzu.

2. Klicken Sie auf **Projekt > Eigenschaften von AccessDBProviderSample > Debuggen**. In **Startprojekt**, klicken Sie auf **externes Programm starten**, und navigieren Sie zu der ausführbaren Windows PowerShell-Datei (in der Regel c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).

3. Klicken Sie unter **Startoptionen**, geben Sie Folgendes in die **Befehlszeilenargumente** Feld: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>Die Anbieterklasse deklarieren

Abgeleitet von unserem Anbieter die [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Klasse. Leiten Sie die meisten Anbieter, die echte Funktion (zugreifen auf und Bearbeiten von Elementen, navigieren Sie in den Datenspeicher, und Abrufen und festlegen Inhalt von Elementen) bereitstellen, von der [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) Klasse.

Zusätzlich zum angeben, dass die Klasse abgeleitet [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), statten Sie müssen sie mit der [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) wie im Beispiel gezeigt.

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

### <a name="implementing-newdrive"></a>Implementieren von NewDrive

Die [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) Methode wird von der Windows PowerShell-Engine aufgerufen, wenn ein Benutzer ruft die [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)Cmdlet Geben Sie dabei den Namen des Anbieters. Der PSDriveInfo-Parameter wird von der Windows PowerShell-Engine übergeben, und die Methode gibt das neue Laufwerk für die Windows PowerShell-Engine zurück. Diese Methode muss innerhalb der oben erstellten Klasse deklariert werden.

Die Methode überprüft zuerst, um sicherzustellen, dass das Laufwerk und den Stamm des Laufwerks, die übergeben wurden vorhanden, `null` ist davon nicht der Fall. Anschließend werden mit einem Konstruktor, der internen Klasse AccessDBPSDriveInfo erstellen Sie ein neues Laufwerk, und eine Verbindung mit der Access-Datenbank das Laufwerk darstellt.

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

Folgendes ist die interne AccessDBPSDriveInfo-Klasse, die ab, der den Konstruktor verwendet, um ein neues Laufwerk zu erstellen und enthält die Statusinformationen für das Laufwerk.

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

### <a name="implementing-removedrive"></a>Implementieren von RemoveDrive

Die [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) Methode wird von der Windows PowerShell-Engine aufgerufen, wenn ein Benutzer ruft die [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) Cmdlet. Die Methode in diesem Anbieter schließt die Verbindung mit der Access-Datenbank.

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