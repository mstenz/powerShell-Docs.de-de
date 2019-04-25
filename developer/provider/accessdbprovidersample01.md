---
title: AccessDBProviderSample01 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 853b7e5d-76c1-490e-8269-0ef31ba2ff13
caps.latest.revision: 10
ms.openlocfilehash: dc1ae92af8a57d6197b595db8e098256ac444b78
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081120"
---
# <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

Dieses Beispiel zeigt, wie eine Anbieterklasse deklarieren, die direkt von abgeleitet ist die [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) Klasse. Wird hier nur aus Gründen der Vollständigkeit aufgeführt.

## <a name="demonstrates"></a>Zeigt

> [!IMPORTANT]
> Ihre Anbieterklasse wird wahrscheinlich von einem der folgenden Klassen abgeleitet werden und möglicherweise andere anbieterschnittstellen implementieren:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse. Finden Sie unter [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) Klasse. Finden Sie unter [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) Klasse. Finden Sie unter [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Weitere Informationen zum auswählen die Anbieterklasse basierend auf Funktionen des Datenanbieters abgeleitet, finden Sie unter [Entwerfen Ihrer Windows PowerShell-Anbieter](./provider-types.md).

Dieses Beispiel zeigt Folgendes:

- Deklarieren der `CmdletProvider` Attribut.

- Definieren einer Klasse, die direkt von abgeleitet ist die [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) Klasse.

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie eine Anbieterklasse definiert und deklariert die `CmdletProvider` Attribut.

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  /// <summary>
  /// This sample shows how to declare a provider class and how to
  /// declare the CmdletProvider attribute.
  /// </summary>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : CmdletProvider
  {
    // Add provider logic here.
  }
}
```

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Entwerfen Ihre Windows PowerShell-Anbieter](./provider-types.md)