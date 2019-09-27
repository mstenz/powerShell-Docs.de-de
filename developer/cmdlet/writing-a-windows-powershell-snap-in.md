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
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322937"
---
# <a name="writing-a-windows-powershell-snap-in"></a>Schreiben eines Windows PowerShell-Snap-Ins

Dieses Beispiel zeigt, wie Sie ein Windows PowerShell-Snap-in schreiben, das zum Registrieren aller Cmdlets und Windows PowerShell-Anbieter in einer Assembly verwendet werden kann.

Bei dieser Art von Snap-in wählen Sie nicht die Cmdlets und Anbieter aus, die Sie registrieren möchten. Informationen zum Schreiben eines Snap-Ins, das Ihnen ermöglicht, die registrierten Elemente auszuwählen, finden Sie unter [Schreiben eines benutzerdefinierten Windows PowerShell-Snap-Ins](./writing-a-custom-windows-powershell-snap-in.md).

### <a name="writing-a-windows-powershell-snap-in"></a>Schreiben eines Windows PowerShell-Snap-Ins

1. Fügen Sie das RunInstallerAttribute-Attribut hinzu.

2. Erstellen Sie eine öffentliche Klasse, die von der [System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) -Klasse abgeleitet wird.

    In diesem Beispiel lautet der Klassenname "GetProcPSSnapIn01".

3. Fügen Sie eine öffentliche Eigenschaft für den Namen des Snap-Ins hinzu (erforderlich). Verwenden Sie beim Benennen von Snap-Ins keines der folgenden Zeichen: #. , () {} [] &-/\ $; : "' \< >;? @ ` *

    In diesem Beispiel lautet der Name des Snap-Ins "GetProcPSSnapIn01".

4. Hinzufügen einer öffentlichen Eigenschaft für den Anbieter des Snap-Ins (erforderlich).

    In diesem Beispiel ist der Lieferant "Microsoft".

5. Fügen Sie eine öffentliche Eigenschaft für die Vendor-Ressource des Snap-Ins hinzu (optional).

    In diesem Beispiel lautet die Ressource "Vendor" "GetProcPSSnapIn01, Microsoft".

6. Fügen Sie eine öffentliche Eigenschaft für die Beschreibung des Snap-Ins hinzu (erforderlich).

    In diesem Beispiel lautet die Beschreibung "Dies ist ein Windows PowerShell-Snap-in, das das Get-proc-Cmdlet registriert".

7. Fügen Sie eine öffentliche Eigenschaft für die Description-Ressource des Snap-Ins hinzu (optional).

    In diesem Beispiel lautet die Vendor-Ressource "GetProcPSSnapIn01, ein Windows PowerShell-Snap-in, das das Get-proc-Cmdlet registriert".

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie Sie ein Windows PowerShell-Snap-in schreiben, das zum Registrieren des Get-proc-Cmdlets in der Windows PowerShell-Shell verwendet werden kann. Beachten Sie, dass in diesem Beispiel die vollständige Assembly nur die GetProcPSSnapIn01-Snap-in-Klasse und die Get-proc-Cmdlet-Klasse enthalten würde.

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

## <a name="see-also"></a>Siehe auch

[Registrieren von Cmdlets, Anbietern und Host Anwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
