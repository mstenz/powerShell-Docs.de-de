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
# <a name="writing-a-windows-powershell-snap-in"></a>Schreiben eines Windows PowerShell-Snap-Ins

Dieses Beispiel zeigt, wie Sie ein Windows PowerShell-Snap-in zu schreiben, die verwendet werden können, um alle Cmdlets und Windows PowerShell-Anbieter in einer Assembly zu registrieren.

Mit dieser Art von-Snap-in Wählen Sie nicht die Cmdlets und Anbieter, die Sie registrieren möchten. Um ein Snap-In zu schreiben, mit dem Sie auswählen, welche registriert ist, finden Sie unter [schreiben ein benutzerdefiniertes Windows PowerShell-Snap-in](./writing-a-custom-windows-powershell-snap-in.md).

### <a name="writing-a-windows-powershell-snap-in"></a>Schreiben eines Windows PowerShell-Snap-Ins

1. Fügen Sie das Attribut RunInstallerAttribute hinzu.

2. Erstellen Sie eine öffentliche abgeleitete Klasse die [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) Klasse.

    In diesem Beispiel ist der Klassenname "GetProcPSSnapIn01".

3. Fügen Sie eine öffentliche Eigenschaft für den Namen des Snap-Ins (erforderlich). Bei der Benennung von-Snap-ins verwenden Sie nicht die folgenden Zeichen: #. , ( ) { } [ ] & - /\ $ ; : " ' \< > ; ? @ ` *

    In diesem Beispiel ist der Name des Snap-Ins "GetProcPSSnapIn01".

4. Fügen Sie eine öffentliche Eigenschaft, für den Hersteller des Snap-Ins (erforderlich).

    In diesem Beispiel ist der Anbieter "Microsoft".

5. Fügen Sie eine öffentliche Eigenschaft für die Anbieter-Ressource des Snap-Ins (optional).

    In diesem Beispiel ist die Anbieter-Ressource "GetProcPSSnapIn01, Microsoft".

6. Fügen Sie eine öffentliche Eigenschaft für die Beschreibung des Snap-Ins (erforderlich).

    In diesem Beispiel ist die Beschreibung "dies ein Windows PowerShell-Snap-in, der das Cmdlet" Get-Proc "registriert".

7. Fügen Sie eine öffentliche Eigenschaft für die Ressource für die Beschreibung des Snap-Ins (optional) hinzu.

    In diesem Beispiel ist die Anbieter-Ressource "GetProcPSSnapIn01, dies ein Windows PowerShell-Snap-in, der das Cmdlet" Get-Proc "registriert".

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie Sie ein Windows PowerShell-Snap-in zu schreiben, die verwendet werden kann, um das Get-Proc-Cmdlet in der Windows PowerShell-Shell zu registrieren. Denken Sie daran, dass in diesem Beispiel die vollständige Assembly nur die GetProcPSSnapIn01-Snap-in-Klasse und die Get-Proc-Cmdlet-Klasse enthält.

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

## <a name="see-also"></a>Weitere Informationen

[So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)