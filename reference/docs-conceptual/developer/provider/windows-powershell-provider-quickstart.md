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
ms.openlocfilehash: 4693a2ec02a8f010f900bebf5a50853edef88cb1
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560932"
---
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="defd6-102">Windows PowerShell-Anbieter: Schnellstart</span><span class="sxs-lookup"><span data-stu-id="defd6-102">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="defd6-103">In diesem Thema wird erläutert, wie Sie einen Windows PowerShell-Anbieter erstellen, der über grundlegende Funktionen zum Erstellen eines neuen Laufwerks verfügt.</span><span class="sxs-lookup"><span data-stu-id="defd6-103">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="defd6-104">Allgemeine Informationen zu Anbietern finden Sie unter [Übersicht über den Windows PowerShell-Anbieter](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="defd6-104">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="defd6-105">Beispiele für Anbieter mit Umfang vollem Funktionsumfang finden Sie unter [Anbieter Beispiele](./provider-samples.md).</span><span class="sxs-lookup"><span data-stu-id="defd6-105">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="defd6-106">Schreiben eines einfachen Anbieters</span><span class="sxs-lookup"><span data-stu-id="defd6-106">Writing a basic provider</span></span>

<span data-ttu-id="defd6-107">Die grundlegendsten Funktionen eines Windows PowerShell-Anbieters sind das Erstellen und Entfernen von Laufwerken.</span><span class="sxs-lookup"><span data-stu-id="defd6-107">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="defd6-108">In diesem Beispiel implementieren wir die [System. Management. Automation. Provider. drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) -und die [System. Management. Automation. Provider. drivecmdletprovider. removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) -Methode der [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Klasse.</span><span class="sxs-lookup"><span data-stu-id="defd6-108">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="defd6-109">Außerdem erfahren Sie, wie Sie eine Anbieter Klasse deklarieren.</span><span class="sxs-lookup"><span data-stu-id="defd6-109">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="defd6-110">Wenn Sie einen Anbieter schreiben, können Sie Standard Laufwerke angeben, die automatisch erstellt werden, wenn der Anbieter verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="defd6-110">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="defd6-111">Außerdem definieren Sie eine Methode, mit der neue Laufwerke erstellt werden, die diesen Anbieter verwenden.</span><span class="sxs-lookup"><span data-stu-id="defd6-111">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="defd6-112">Die in diesem Thema bereitgestellten Beispiele basieren auf dem [AccessDBProviderSample02](./accessdbprovidersample02.md) -Beispiel, das Teil eines größeren Beispiels ist, das eine Access-Datenbank als Windows PowerShell-Laufwerk darstellt.</span><span class="sxs-lookup"><span data-stu-id="defd6-112">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="defd6-113">Einrichten des Projekts</span><span class="sxs-lookup"><span data-stu-id="defd6-113">Setting up the project</span></span>

<span data-ttu-id="defd6-114">Erstellen Sie in Visual Studio ein Klassen Bibliotheksprojekt mit dem Namen accessdbprovidersample.</span><span class="sxs-lookup"><span data-stu-id="defd6-114">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="defd6-115">Führen Sie die folgenden Schritte aus, um das Projekt so zu konfigurieren, dass Windows PowerShell gestartet wird. der Anbieter wird dann in die Sitzung geladen, wenn Sie das Projekt erstellen und starten.</span><span class="sxs-lookup"><span data-stu-id="defd6-115">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="defd6-116">Konfigurieren des Anbieter Projekts</span><span class="sxs-lookup"><span data-stu-id="defd6-116">Configure the provider project</span></span>

1. <span data-ttu-id="defd6-117">Fügen Sie die System. Management. Automation-Assembly als Verweis auf das Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="defd6-117">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="defd6-118">Klicken Sie **> Debuggen auf Projekt > accessdbprovidersample-Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="defd6-118">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="defd6-119">Klicken Sie unter **Projekt starten**auf **externes Programm starten**, und navigieren Sie zur ausführbaren Windows PowerShell-Datei (in der Regel c:\Windows\System32\WindowsPowerShell\v1.0 \\ . PowerShell. exe).</span><span class="sxs-lookup"><span data-stu-id="defd6-119">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="defd6-120">Geben Sie unter **Start Optionen**Folgendes in das Feld **Befehlszeilenargumente** ein:`-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="defd6-120">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="defd6-121">Deklarieren der Anbieter Klasse</span><span class="sxs-lookup"><span data-stu-id="defd6-121">Declaring the provider class</span></span>

<span data-ttu-id="defd6-122">Der Anbieter wird von der [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Klasse abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="defd6-122">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="defd6-123">Die meisten Anbieter, die echte Funktionen bereitstellen (Zugriff und Bearbeitung von Elementen, Navigation im Datenspeicher und das Festlegen und Festlegen von Inhalts Elementen), werden von der [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="defd6-123">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="defd6-124">Zusätzlich zur Angabe, dass die Klasse von [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)abgeleitet ist, müssen Sie Sie mit dem [System. Management. Automation. Provider. cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) ergänzen, wie im Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="defd6-124">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

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

### <a name="implementing-newdrive"></a><span data-ttu-id="defd6-125">Implementieren von newdrive</span><span class="sxs-lookup"><span data-stu-id="defd6-125">Implementing NewDrive</span></span>

<span data-ttu-id="defd6-126">Die [System. Management. Automation. Provider. drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) -Methode wird von der Windows PowerShell-Engine aufgerufen, wenn ein Benutzer das [Microsoft. PowerShell. Commands. newpsdrivecommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) -Cmdlet aufruft, das den Namen des Anbieters angibt.</span><span class="sxs-lookup"><span data-stu-id="defd6-126">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="defd6-127">Der psdriveinfo-Parameter wird von der Windows PowerShell-Engine übergeben, und die-Methode gibt das neue Laufwerk an die Windows PowerShell-Engine zurück.</span><span class="sxs-lookup"><span data-stu-id="defd6-127">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="defd6-128">Diese Methode muss innerhalb der oben erstellten-Klasse deklariert werden.</span><span class="sxs-lookup"><span data-stu-id="defd6-128">This method must be declared within the class created above.</span></span>

<span data-ttu-id="defd6-129">Die-Methode prüft zunächst, ob sowohl das Laufwerks Objekt als auch der Laufwerks Stamm vorhanden sind, die übergebenen sind, und gibt zurück, `null` Wenn dies nicht der Fall ist.</span><span class="sxs-lookup"><span data-stu-id="defd6-129">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="defd6-130">Anschließend wird ein Konstruktor der internen Klasse accessdbpsdriveingefo verwendet, um ein neues Laufwerk und eine Verbindung mit der Access-Datenbank zu erstellen, die das Laufwerk darstellt.</span><span class="sxs-lookup"><span data-stu-id="defd6-130">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

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

<span data-ttu-id="defd6-131">Im folgenden finden Sie die interne accessdbpsdriveinfo-Klasse, die den zum Erstellen eines neuen Laufwerks verwendeten Konstruktor enthält und die Zustandsinformationen für das Laufwerk enthält.</span><span class="sxs-lookup"><span data-stu-id="defd6-131">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

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

### <a name="implementing-removedrive"></a><span data-ttu-id="defd6-132">Implementieren von removedrive</span><span class="sxs-lookup"><span data-stu-id="defd6-132">Implementing RemoveDrive</span></span>

<span data-ttu-id="defd6-133">Die [System. Management. Automation. Provider. drivecmdletprovider. removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) -Methode wird von der Windows PowerShell-Engine aufgerufen, wenn ein Benutzer das Cmdlet " [Microsoft. PowerShell. Commands. removepsdrivecommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) " aufruft.</span><span class="sxs-lookup"><span data-stu-id="defd6-133">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) cmdlet.</span></span> <span data-ttu-id="defd6-134">Die-Methode in diesem Anbieter schließt die Verbindung mit der Access-Datenbank.</span><span class="sxs-lookup"><span data-stu-id="defd6-134">The method in this provider closes the connection to the Access database.</span></span>

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
