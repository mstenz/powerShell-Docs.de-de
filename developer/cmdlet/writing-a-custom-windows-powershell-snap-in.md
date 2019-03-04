---
title: Schreiben ein benutzerdefiniertes Windows PowerShell-Snap-in | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], custom PSSnapin example
- cmdlets [PowerShell SDK], specified in snap-ins
ms.assetid: 55c8b5cb-8ee2-4080-afc4-3f09c9f20128
caps.latest.revision: 6
ms.openlocfilehash: 20b7fdce1d31e3dee4598a7595962fca1c99d80a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863346"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a><span data-ttu-id="d81f1-102">Schreiben eines benutzerdefinierten Windows PowerShell-Snap-Ins</span><span class="sxs-lookup"><span data-stu-id="d81f1-102">Writing a Custom Windows PowerShell Snap-in</span></span>

<span data-ttu-id="d81f1-103">Dieses Beispiel zeigt, wie Sie ein Windows PowerShell-Snap-in zu schreiben, der bestimmte Cmdlets registriert wird.</span><span class="sxs-lookup"><span data-stu-id="d81f1-103">This example shows how to write a Windows PowerShell snap-in that registers specific cmdlets.</span></span>

<span data-ttu-id="d81f1-104">Mit dieser Art des Snap-Ins geben Sie die Cmdlets, Anbieter, Typen und Formate zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="d81f1-104">With this type of snap-in, you specify which cmdlets, providers, types, or formats to register.</span></span> <span data-ttu-id="d81f1-105">Weitere Informationen dazu, wie ein Snap-In zu schreiben, der die Cmdlets und Anbieter in einer Assembly registriert finden Sie unter [schreiben ein Windows PowerShell-Snap-in](./writing-a-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="d81f1-105">For more information about how to write a snap-in that registers all the cmdlets and providers in an assembly, see [Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).</span></span>

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a><span data-ttu-id="d81f1-106">Um ein Windows PowerShell-Snap-in zu schreiben, der bestimmte Cmdlets registriert.</span><span class="sxs-lookup"><span data-stu-id="d81f1-106">To write a Windows PowerShell Snap-in that registers specific cmdlets.</span></span>

1. <span data-ttu-id="d81f1-107">Fügen Sie das Attribut RunInstallerAttribute hinzu.</span><span class="sxs-lookup"><span data-stu-id="d81f1-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="d81f1-108">Erstellen Sie eine öffentliche abgeleitete Klasse die [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) Klasse.</span><span class="sxs-lookup"><span data-stu-id="d81f1-108">Create a public class that derives from the [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class.</span></span>

   <span data-ttu-id="d81f1-109">In diesem Beispiel ist der Klassenname "CustomPSSnapinTest".</span><span class="sxs-lookup"><span data-stu-id="d81f1-109">In this example, the class name is "CustomPSSnapinTest".</span></span>

3. <span data-ttu-id="d81f1-110">Fügen Sie eine öffentliche Eigenschaft für den Namen des Snap-Ins (erforderlich).</span><span class="sxs-lookup"><span data-stu-id="d81f1-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="d81f1-111">Bei der Benennung von-Snap-ins verwenden Sie nicht die folgenden Zeichen: #.</span><span class="sxs-lookup"><span data-stu-id="d81f1-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="d81f1-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span><span class="sxs-lookup"><span data-stu-id="d81f1-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span></span> <span data-ttu-id="d81f1-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="d81f1-113">@ \` \*</span></span>

   <span data-ttu-id="d81f1-114">In diesem Beispiel ist der Name des Snap-Ins "CustomPSSnapInTest".</span><span class="sxs-lookup"><span data-stu-id="d81f1-114">In this example, the name of the snap-in is "CustomPSSnapInTest".</span></span>

4. <span data-ttu-id="d81f1-115">Fügen Sie eine öffentliche Eigenschaft, für den Hersteller des Snap-Ins (erforderlich).</span><span class="sxs-lookup"><span data-stu-id="d81f1-115">Add a public property for the vendor of the snap-in (required).</span></span>

   <span data-ttu-id="d81f1-116">In diesem Beispiel ist der Anbieter "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="d81f1-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="d81f1-117">Fügen Sie eine öffentliche Eigenschaft für die Anbieter-Ressource des Snap-Ins (optional).</span><span class="sxs-lookup"><span data-stu-id="d81f1-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

   <span data-ttu-id="d81f1-118">In diesem Beispiel ist die Anbieter-Ressource "CustomPSSnapInTest, Microsoft".</span><span class="sxs-lookup"><span data-stu-id="d81f1-118">In this example, the vendor resource is "CustomPSSnapInTest,Microsoft".</span></span>

6. <span data-ttu-id="d81f1-119">Fügen Sie eine öffentliche Eigenschaft für die Beschreibung des Snap-Ins (erforderlich).</span><span class="sxs-lookup"><span data-stu-id="d81f1-119">Add a public property for the description of the snap-in (required).</span></span>

   <span data-ttu-id="d81f1-120">In diesem Beispiel wird die Beschreibung: "Dies ist ein benutzerdefiniertes Windows PowerShell-Snap-in mit den Test-HelloWorld- und -Cmdlets Test-CustomSnapinTest".</span><span class="sxs-lookup"><span data-stu-id="d81f1-120">In this example, the description is: "This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

7. <span data-ttu-id="d81f1-121">Fügen Sie eine öffentliche Eigenschaft für die Ressource für die Beschreibung des Snap-Ins (optional) hinzu.</span><span class="sxs-lookup"><span data-stu-id="d81f1-121">Add a public property for the description resource of the snap-in (optional).</span></span>

   <span data-ttu-id="d81f1-122">In diesem Beispiel ist die Anbieter-Ressource an, "CustomPSSnapInTest, das ein benutzerdefiniertes Windows PowerShell-Snap-in, das die Cmdlets Test-HelloWorld" und "Test-CustomSnapinTest enthält ist".</span><span class="sxs-lookup"><span data-stu-id="d81f1-122">In this example, the vendor resource is "CustomPSSnapInTest, This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

8. <span data-ttu-id="d81f1-123">Geben Sie die Cmdlets, die mit dem benutzerdefinierten-Snap-in (optional) gehören die [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) Klasse.</span><span class="sxs-lookup"><span data-stu-id="d81f1-123">Specify the cmdlets that belong to the custom snap-in (optional) using the [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) class.</span></span> <span data-ttu-id="d81f1-124">Die hier hinzugefügte Informationen enthält den Namen des dem-Cmdlet, den Typ .NET und der Dateiname der Cmdlet-Hilfe (das Format des Dateinamens für den Cmdlet-Hilfe sollte Name.dll wurden-help.xml sein).</span><span class="sxs-lookup"><span data-stu-id="d81f1-124">The information added here includes the name of the cmdlet, its .NET type, and the cmdlet Help file name (the format of the cmdlet Help file name should be name.dll-help.xml).</span></span>

   <span data-ttu-id="d81f1-125">In diesem Beispiel wird die Test-HelloWorld und TestCustomSnapinTest-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d81f1-125">This example adds the Test-HelloWorld and TestCustomSnapinTest cmdlets.</span></span>

9. <span data-ttu-id="d81f1-126">Geben Sie die Anbieter, die zu der benutzerdefinierten-Snap-in (optional) gehören.</span><span class="sxs-lookup"><span data-stu-id="d81f1-126">Specify the providers that belong to the custom snap-in (optional).</span></span>

   <span data-ttu-id="d81f1-127">In diesem Beispiel wird keine Anbieter angegeben.</span><span class="sxs-lookup"><span data-stu-id="d81f1-127">This example does not specify any providers.</span></span>

10. <span data-ttu-id="d81f1-128">Geben Sie die Typen, die zu der benutzerdefinierten-Snap-in (optional) gehören.</span><span class="sxs-lookup"><span data-stu-id="d81f1-128">Specify the types that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="d81f1-129">In diesem Beispiel wird keine Typen angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="d81f1-129">This example does not specify any types.</span></span>

11. <span data-ttu-id="d81f1-130">Geben Sie die Formate, die zu der benutzerdefinierten-Snap-in (optional) gehören.</span><span class="sxs-lookup"><span data-stu-id="d81f1-130">Specify the formats that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="d81f1-131">In diesem Beispiel wird keine Formate angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="d81f1-131">This example does not specify any formats.</span></span>

## <a name="example"></a><span data-ttu-id="d81f1-132">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d81f1-132">Example</span></span>

<span data-ttu-id="d81f1-133">Dieses Beispiel zeigt, wie Sie ein benutzerdefiniertes Windows PowerShell-Snap-in zu schreiben, die zum Registrieren der Test-HelloWorld und Test-CustomSnapinTest-Cmdlets verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="d81f1-133">This example shows how to write a Custom Windows PowerShell snap-in that can be used to register the Test-HelloWorld and Test-CustomSnapinTest cmdlets.</span></span> <span data-ttu-id="d81f1-134">Denken Sie daran, dass in diesem Beispiel die vollständige Assembly enthalten kann, andere Cmdlets und Anbieter, die nicht von diesem-Snap-in registriert werden.</span><span class="sxs-lookup"><span data-stu-id="d81f1-134">Be aware that in this example, the complete assembly could contain other cmdlets and providers that would not be registered by this snap-in.</span></span>

```csharp
[RunInstaller(true)]
public class CustomPSSnapinTest : CustomPSSnapIn
{
  /// <summary>
  /// Creates an instance of CustomPSSnapInTest class.
  /// </summary>
  public CustomPSSnapinTest()
          : base()
  {
  }

  /// <summary>
  /// Specify the name of the custom PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "CustomPSSnapInTest";
    }
  }

  /// <summary>
  /// Specify the vendor for the custom PowerShell snap-in.
  /// </summary>
  public override string Vendor
  {
    get
    {
      return "Microsoft";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the vendor.
  /// Use the format: resourceBaseName,resourceName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
        return "CustomPSSnapInTest,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the custom PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the description.
  /// Use the format: resourceBaseName,Description.
  /// </summary>
  public override string DescriptionResource
  {
    get
    {
        return "CustomPSSnapInTest,This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
    }
  }

  /// <summary>
  /// Specify the cmdlets that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<CmdletConfigurationEntry> _cmdlets;
  public override Collection<CmdletConfigurationEntry> Cmdlets
  {
    get
    {
      if (_cmdlets == null)
      {
        _cmdlets = new Collection<CmdletConfigurationEntry>();
        _cmdlets.Add(new CmdletConfigurationEntry("test-customsnapintest", typeof(TestCustomSnapinTest), "TestCmdletHelp.dll-help.xml"));
        _cmdlets.Add(new CmdletConfigurationEntry("test-helloworld", typeof(TestHelloWorld), "HelloWorldHelp.dll-help.xml"));
      }

      return _cmdlets;
    }
  }

  /// <summary>
  /// Specify the providers that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<ProviderConfigurationEntry> _providers;
  public override Collection<ProviderConfigurationEntry> Providers
  {
    get
    {
      if (_providers == null)
      {
        _providers = new Collection<ProviderConfigurationEntry>();
      }

      return _providers;
    }
  }

  /// <summary>
  /// Specify the types that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<TypeConfigurationEntry> _types;
  public override Collection<TypeConfigurationEntry> Types
  {
    get
    {
      if (_types == null)
      {
        _types = new Collection<TypeConfigurationEntry>();
      }

      return _types;
    }
  }

  /// <summary>
  /// Specify the formats that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<FormatConfigurationEntry> _formats;
  public override Collection<FormatConfigurationEntry> Formats
  {
    get
    {
      if (_formats == null)
      {
        _formats = new Collection<FormatConfigurationEntry>();
      }

      return _formats;
    }
  }
}
```

<span data-ttu-id="d81f1-135">Weitere Informationen zum Registrieren von-Snap-ins finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) in die [Windows PowerShell Handbuch für Programmierer](../prog-guide/windows-powershell-programmer-s-guide.md).</span><span class="sxs-lookup"><span data-stu-id="d81f1-135">For more information about registering snap-ins, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) in the [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d81f1-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d81f1-136">See Also</span></span>

[<span data-ttu-id="d81f1-137">So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen</span><span class="sxs-lookup"><span data-stu-id="d81f1-137">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="d81f1-138">So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen</span><span class="sxs-lookup"><span data-stu-id="d81f1-138">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="d81f1-139">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="d81f1-139">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
