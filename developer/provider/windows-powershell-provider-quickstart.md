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
ms.openlocfilehash: ab78bcad301215bca9b5324bdb8de863899edec6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862146"
---
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="178e5-102">Windows PowerShell-Anbieter: Schnellstart</span><span class="sxs-lookup"><span data-stu-id="178e5-102">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="178e5-103">In diesem Thema wird erläutert, wie Sie einen Windows PowerShell-Anbieter erstellen, die grundlegende Funktionalität zum Erstellen eines neuen Laufwerks.</span><span class="sxs-lookup"><span data-stu-id="178e5-103">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="178e5-104">Allgemeine Informationen zu Anbietern finden Sie unter [Übersicht über Windows PowerShell-Anbieter](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="178e5-104">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="178e5-105">Beispiele für vollständige Funktionalität Anbieter, finden Sie unter [Beispiele für Tabellenprofilanbieter](./provider-samples.md).</span><span class="sxs-lookup"><span data-stu-id="178e5-105">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="178e5-106">Schreiben eines einfachen Anbieters</span><span class="sxs-lookup"><span data-stu-id="178e5-106">Writing a basic provider</span></span>

<span data-ttu-id="178e5-107">Die Grundfunktionen von einem Windows PowerShell-Anbieter ist zum Erstellen und Entfernen von Laufwerken.</span><span class="sxs-lookup"><span data-stu-id="178e5-107">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="178e5-108">In diesem Beispiel implementieren wir die [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) und [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) Methoden der [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="178e5-108">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="178e5-109">Außerdem sehen Sie, wie eine Anbieterklasse deklariert.</span><span class="sxs-lookup"><span data-stu-id="178e5-109">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="178e5-110">Wenn Sie einen Anbieter schreiben, können Sie standardmäßige Laufwerken-Laufwerke angeben, die automatisch erstellt werden, wenn der Anbieter verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="178e5-110">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="178e5-111">Außerdem definieren Sie eine Methode zum Erstellen von neuen Laufwerke, die diesen Anbieter verwenden.</span><span class="sxs-lookup"><span data-stu-id="178e5-111">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="178e5-112">Die Beispiele in diesem Thema basieren auf der [AccessDBProviderSample02](./accessdbprovidersample02.md) Beispiel, das Teil eines umfangreicheren Beispiels ist, die eine Access-Datenbank als ein Windows PowerShell-Laufwerk darstellt.</span><span class="sxs-lookup"><span data-stu-id="178e5-112">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="178e5-113">Einrichten des Projekts</span><span class="sxs-lookup"><span data-stu-id="178e5-113">Setting up the project</span></span>

<span data-ttu-id="178e5-114">Erstellen Sie in Visual Studio ein Klassenbibliotheksprojekt namens AccessDBProviderSample.</span><span class="sxs-lookup"><span data-stu-id="178e5-114">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="178e5-115">Führen Sie die folgenden Schritte aus, um Ihr Projekt konfigurieren, damit Windows PowerShell wird gestartet, und der Anbieter wird in der Sitzung geladen werden, wenn Sie beim Erstellen und starten Sie Ihr Projekt.</span><span class="sxs-lookup"><span data-stu-id="178e5-115">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="178e5-116">Konfigurieren Sie das Anbieterprojekt</span><span class="sxs-lookup"><span data-stu-id="178e5-116">Configure the provider project</span></span>

1. <span data-ttu-id="178e5-117">Fügen Sie die System.Management.Automation-Assembly als Verweis zum Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="178e5-117">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="178e5-118">Klicken Sie auf **Projekt > Eigenschaften von AccessDBProviderSample > Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="178e5-118">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="178e5-119">In **Startprojekt**, klicken Sie auf **externes Programm starten**, und navigieren Sie zu der ausführbaren Windows PowerShell-Datei (in der Regel c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).</span><span class="sxs-lookup"><span data-stu-id="178e5-119">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="178e5-120">Klicken Sie unter **Startoptionen**, geben Sie Folgendes in die **Befehlszeilenargumente** Feld: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="178e5-120">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="178e5-121">Die Anbieterklasse deklarieren</span><span class="sxs-lookup"><span data-stu-id="178e5-121">Declaring the provider class</span></span>

<span data-ttu-id="178e5-122">Abgeleitet von unserem Anbieter die [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="178e5-122">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="178e5-123">Leiten Sie die meisten Anbieter, die echte Funktion (zugreifen auf und Bearbeiten von Elementen, navigieren Sie in den Datenspeicher, und Abrufen und festlegen Inhalt von Elementen) bereitstellen, von der [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="178e5-123">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="178e5-124">Zusätzlich zum angeben, dass die Klasse abgeleitet [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), statten Sie müssen sie mit der [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) wie im Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="178e5-124">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

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

### <a name="implementing-newdrive"></a><span data-ttu-id="178e5-125">Implementieren von NewDrive</span><span class="sxs-lookup"><span data-stu-id="178e5-125">Implementing NewDrive</span></span>

<span data-ttu-id="178e5-126">Die [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) Methode wird von der Windows PowerShell-Engine aufgerufen, wenn ein Benutzer ruft die [Microsoft.Powershell.Commands.New-Psdrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)Cmdlet Geben Sie dabei den Namen des Anbieters.</span><span class="sxs-lookup"><span data-stu-id="178e5-126">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.Powershell.Commands.New-Psdrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="178e5-127">Der PSDriveInfo-Parameter wird von der Windows PowerShell-Engine übergeben, und die Methode gibt das neue Laufwerk für die Windows PowerShell-Engine zurück.</span><span class="sxs-lookup"><span data-stu-id="178e5-127">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="178e5-128">Diese Methode muss innerhalb der oben erstellten Klasse deklariert werden.</span><span class="sxs-lookup"><span data-stu-id="178e5-128">This method must be declared within the class created above.</span></span>

<span data-ttu-id="178e5-129">Die Methode überprüft zuerst, um sicherzustellen, dass das Laufwerk und den Stamm des Laufwerks, die übergeben wurden vorhanden, `null` ist davon nicht der Fall.</span><span class="sxs-lookup"><span data-stu-id="178e5-129">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="178e5-130">Anschließend werden mit einem Konstruktor, der internen Klasse AccessDBPSDriveInfo erstellen Sie ein neues Laufwerk, und eine Verbindung mit der Access-Datenbank das Laufwerk darstellt.</span><span class="sxs-lookup"><span data-stu-id="178e5-130">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

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

<span data-ttu-id="178e5-131">Folgendes ist die interne AccessDBPSDriveInfo-Klasse, die ab, der den Konstruktor verwendet, um ein neues Laufwerk zu erstellen und enthält die Statusinformationen für das Laufwerk.</span><span class="sxs-lookup"><span data-stu-id="178e5-131">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

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

### <a name="implementing-removedrive"></a><span data-ttu-id="178e5-132">Implementieren von RemoveDrive</span><span class="sxs-lookup"><span data-stu-id="178e5-132">Implementing RemoveDrive</span></span>

<span data-ttu-id="178e5-133">Die [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) Methode wird von der Windows PowerShell-Engine aufgerufen, wenn ein Benutzer ruft die [Microsoft.Powershell.Commands.Remove-Psdrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="178e5-133">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.Powershell.Commands.Remove-Psdrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet.</span></span> <span data-ttu-id="178e5-134">Die Methode in diesem Anbieter schließt die Verbindung mit der Access-Datenbank.</span><span class="sxs-lookup"><span data-stu-id="178e5-134">The method in this provider closes the connection to the Access database.</span></span>

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