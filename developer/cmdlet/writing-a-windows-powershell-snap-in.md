---
title: Schreiben ein Windows PowerShell-Snap-in | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], PSSnapin example
ms.assetid: 875024f4-e02b-4416-80b9-af5e5b50aad6
caps.latest.revision: 7
ms.openlocfilehash: ee8a6538fa6ad4d0f480f2dac46fe0f823a38be8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853766"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="3e0a1-102">Schreiben eines Windows PowerShell-Snap-Ins</span><span class="sxs-lookup"><span data-stu-id="3e0a1-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="3e0a1-103">Dieses Beispiel zeigt, wie Sie ein Windows PowerShell-Snap-in zu schreiben, die verwendet werden können, um alle Cmdlets und Windows PowerShell-Anbieter in einer Assembly zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="3e0a1-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="3e0a1-104">Mit dieser Art von-Snap-in Wählen Sie nicht die Cmdlets und Anbieter, die Sie registrieren möchten.</span><span class="sxs-lookup"><span data-stu-id="3e0a1-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="3e0a1-105">Um ein Snap-In zu schreiben, mit dem Sie auswählen, welche registriert ist, finden Sie unter [schreiben ein benutzerdefiniertes Windows PowerShell-Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="3e0a1-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="3e0a1-106">Schreiben eines Windows PowerShell-Snap-Ins</span><span class="sxs-lookup"><span data-stu-id="3e0a1-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="3e0a1-107">Fügen Sie das Attribut RunInstallerAttribute hinzu.</span><span class="sxs-lookup"><span data-stu-id="3e0a1-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="3e0a1-108">Erstellen Sie eine öffentliche abgeleitete Klasse die [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) Klasse.</span><span class="sxs-lookup"><span data-stu-id="3e0a1-108">Create a public class that derives from the [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="3e0a1-109">In diesem Beispiel ist der Klassenname "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="3e0a1-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="3e0a1-110">Fügen Sie eine öffentliche Eigenschaft für den Namen des Snap-Ins (erforderlich).</span><span class="sxs-lookup"><span data-stu-id="3e0a1-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="3e0a1-111">Bei der Benennung von-Snap-ins verwenden Sie nicht die folgenden Zeichen: #.</span><span class="sxs-lookup"><span data-stu-id="3e0a1-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="3e0a1-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span><span class="sxs-lookup"><span data-stu-id="3e0a1-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span></span> <span data-ttu-id="3e0a1-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="3e0a1-113">@ \` \*</span></span>

    <span data-ttu-id="3e0a1-114">In diesem Beispiel ist der Name des Snap-Ins "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="3e0a1-114">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="3e0a1-115">Fügen Sie eine öffentliche Eigenschaft, für den Hersteller des Snap-Ins (erforderlich).</span><span class="sxs-lookup"><span data-stu-id="3e0a1-115">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="3e0a1-116">In diesem Beispiel ist der Anbieter "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="3e0a1-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="3e0a1-117">Fügen Sie eine öffentliche Eigenschaft für die Anbieter-Ressource des Snap-Ins (optional).</span><span class="sxs-lookup"><span data-stu-id="3e0a1-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="3e0a1-118">In diesem Beispiel ist die Anbieter-Ressource "GetProcPSSnapIn01, Microsoft".</span><span class="sxs-lookup"><span data-stu-id="3e0a1-118">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="3e0a1-119">Fügen Sie eine öffentliche Eigenschaft für die Beschreibung des Snap-Ins (erforderlich).</span><span class="sxs-lookup"><span data-stu-id="3e0a1-119">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="3e0a1-120">In diesem Beispiel ist die Beschreibung "dies ein Windows PowerShell-Snap-in, der das Cmdlet" Get-Proc "registriert".</span><span class="sxs-lookup"><span data-stu-id="3e0a1-120">In this example, the description is "This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

7. <span data-ttu-id="3e0a1-121">Fügen Sie eine öffentliche Eigenschaft für die Ressource für die Beschreibung des Snap-Ins (optional) hinzu.</span><span class="sxs-lookup"><span data-stu-id="3e0a1-121">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="3e0a1-122">In diesem Beispiel ist die Anbieter-Ressource "GetProcPSSnapIn01, dies ein Windows PowerShell-Snap-in, der das Cmdlet" Get-Proc "registriert".</span><span class="sxs-lookup"><span data-stu-id="3e0a1-122">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="3e0a1-123">Beispiel</span><span class="sxs-lookup"><span data-stu-id="3e0a1-123">Example</span></span>

<span data-ttu-id="3e0a1-124">Dieses Beispiel zeigt, wie Sie ein Windows PowerShell-Snap-in zu schreiben, die verwendet werden kann, um das Get-Proc-Cmdlet in der Windows PowerShell-Shell zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="3e0a1-124">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="3e0a1-125">Denken Sie daran, dass in diesem Beispiel die vollständige Assembly nur die GetProcPSSnapIn01-Snap-in-Klasse und die Get-Proc-Cmdlet-Klasse enthält.</span><span class="sxs-lookup"><span data-stu-id="3e0a1-125">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the Get-Proc cmdlet class.</span></span>

```csharp
[RunInstaller(true)]
public class GetProcPSSnapIn01 : PSSnapIn
{
  /// <summary>
  /// Create an instance of the GetProcPSSnapIn01 class.
  /// </summary>
  public GetProcPSSnapIn01()
         : base()
  {
  }

  /// <summary>
  /// Specify the name of the PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "GetProcPSSnapIn01";
    }
  }

  /// <summary>
  /// Specify the vendor for the PowerShell snap-in.
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
  /// Use the format: resourceBaseName,VendorName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
      return "GetProcPSSnapIn01,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
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
      return "GetProcPSSnapIn01,This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="3e0a1-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3e0a1-126">See Also</span></span>

[<span data-ttu-id="3e0a1-127">So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen</span><span class="sxs-lookup"><span data-stu-id="3e0a1-127">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="3e0a1-128">So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen</span><span class="sxs-lookup"><span data-stu-id="3e0a1-128">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="3e0a1-129">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="3e0a1-129">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
