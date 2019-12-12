---
title: Schreiben eines Windows PowerShell-Snap-Ins | Microsoft-Dokumentation
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
ms.openlocfilehash: 465ab9e8fa29716ce0f46ad0dcf01d0ddd615bcd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364229"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="cd2ba-102">Schreiben eines Windows PowerShell-Snap-Ins</span><span class="sxs-lookup"><span data-stu-id="cd2ba-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="cd2ba-103">Dieses Beispiel zeigt, wie Sie ein Windows PowerShell-Snap-in schreiben, das zum Registrieren aller Cmdlets und Windows PowerShell-Anbieter in einer Assembly verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="cd2ba-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="cd2ba-104">Bei dieser Art von Snap-in wählen Sie nicht die Cmdlets und Anbieter aus, die Sie registrieren möchten.</span><span class="sxs-lookup"><span data-stu-id="cd2ba-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="cd2ba-105">Informationen zum Schreiben eines Snap-Ins, das Ihnen ermöglicht, die registrierten Elemente auszuwählen, finden Sie unter [Schreiben eines benutzerdefinierten Windows PowerShell-Snap-Ins](./writing-a-custom-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="cd2ba-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="cd2ba-106">Schreiben eines Windows PowerShell-Snap-Ins</span><span class="sxs-lookup"><span data-stu-id="cd2ba-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="cd2ba-107">Fügen Sie das RunInstallerAttribute-Attribut hinzu.</span><span class="sxs-lookup"><span data-stu-id="cd2ba-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="cd2ba-108">Erstellen Sie eine öffentliche Klasse, die von der [System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) -Klasse abgeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="cd2ba-108">Create a public class that derives from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="cd2ba-109">In diesem Beispiel lautet der Klassenname "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="cd2ba-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="cd2ba-110">Fügen Sie eine öffentliche Eigenschaft für den Namen des Snap-Ins hinzu (erforderlich).</span><span class="sxs-lookup"><span data-stu-id="cd2ba-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="cd2ba-111">Verwenden Sie beim Benennen von Snap-Ins keines der folgenden Zeichen: #.</span><span class="sxs-lookup"><span data-stu-id="cd2ba-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="cd2ba-112">, () {} [] &-/\ $; : "" \< >;?</span><span class="sxs-lookup"><span data-stu-id="cd2ba-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span></span> <span data-ttu-id="cd2ba-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="cd2ba-113">@ \` \*</span></span>

    <span data-ttu-id="cd2ba-114">In diesem Beispiel lautet der Name des Snap-Ins "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="cd2ba-114">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="cd2ba-115">Hinzufügen einer öffentlichen Eigenschaft für den Anbieter des Snap-Ins (erforderlich).</span><span class="sxs-lookup"><span data-stu-id="cd2ba-115">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="cd2ba-116">In diesem Beispiel ist der Lieferant "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="cd2ba-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="cd2ba-117">Fügen Sie eine öffentliche Eigenschaft für die Vendor-Ressource des Snap-Ins hinzu (optional).</span><span class="sxs-lookup"><span data-stu-id="cd2ba-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="cd2ba-118">In diesem Beispiel lautet die Ressource "Vendor" "GetProcPSSnapIn01, Microsoft".</span><span class="sxs-lookup"><span data-stu-id="cd2ba-118">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="cd2ba-119">Fügen Sie eine öffentliche Eigenschaft für die Beschreibung des Snap-Ins hinzu (erforderlich).</span><span class="sxs-lookup"><span data-stu-id="cd2ba-119">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="cd2ba-120">In diesem Beispiel lautet die Beschreibung "Dies ist ein Windows PowerShell-Snap-in, das das Get-proc-Cmdlet registriert".</span><span class="sxs-lookup"><span data-stu-id="cd2ba-120">In this example, the description is "This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

7. <span data-ttu-id="cd2ba-121">Fügen Sie eine öffentliche Eigenschaft für die Description-Ressource des Snap-Ins hinzu (optional).</span><span class="sxs-lookup"><span data-stu-id="cd2ba-121">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="cd2ba-122">In diesem Beispiel lautet die Vendor-Ressource "GetProcPSSnapIn01, ein Windows PowerShell-Snap-in, das das Get-proc-Cmdlet registriert".</span><span class="sxs-lookup"><span data-stu-id="cd2ba-122">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="cd2ba-123">Beispiel</span><span class="sxs-lookup"><span data-stu-id="cd2ba-123">Example</span></span>

<span data-ttu-id="cd2ba-124">Dieses Beispiel zeigt, wie Sie ein Windows PowerShell-Snap-in schreiben, das zum Registrieren des Get-proc-Cmdlets in der Windows PowerShell-Shell verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="cd2ba-124">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="cd2ba-125">Beachten Sie, dass in diesem Beispiel die vollständige Assembly nur die GetProcPSSnapIn01-Snap-in-Klasse und die Get-proc-Cmdlet-Klasse enthalten würde.</span><span class="sxs-lookup"><span data-stu-id="cd2ba-125">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the Get-Proc cmdlet class.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cd2ba-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="cd2ba-126">See Also</span></span>

[<span data-ttu-id="cd2ba-127">Registrieren von Cmdlets, Anbietern und Host Anwendungen</span><span class="sxs-lookup"><span data-stu-id="cd2ba-127">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="cd2ba-128">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="cd2ba-128">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
