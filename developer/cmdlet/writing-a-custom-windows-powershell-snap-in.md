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
ms.openlocfilehash: 4d50ef4dcd75d5c0ba802fbcfe2d7d1d7c954707
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067024"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a>Schreiben eines benutzerdefinierten Windows PowerShell-Snap-Ins

Dieses Beispiel zeigt, wie Sie ein Windows PowerShell-Snap-in zu schreiben, der bestimmte Cmdlets registriert wird.

Mit dieser Art des Snap-Ins geben Sie die Cmdlets, Anbieter, Typen und Formate zu registrieren. Weitere Informationen dazu, wie ein Snap-In zu schreiben, der die Cmdlets und Anbieter in einer Assembly registriert finden Sie unter [schreiben ein Windows PowerShell-Snap-in](./writing-a-windows-powershell-snap-in.md).

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>Um ein Windows PowerShell-Snap-in zu schreiben, der bestimmte Cmdlets registriert.

1. Fügen Sie das Attribut RunInstallerAttribute hinzu.

2. Erstellen Sie eine öffentliche abgeleitete Klasse die [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) Klasse.

   In diesem Beispiel ist der Klassenname "CustomPSSnapinTest".

3. Fügen Sie eine öffentliche Eigenschaft für den Namen des Snap-Ins (erforderlich). Bei der Benennung von-Snap-ins verwenden Sie nicht die folgenden Zeichen: #. , ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ? @ ` *

   In diesem Beispiel ist der Name des Snap-Ins "CustomPSSnapInTest".

4. Fügen Sie eine öffentliche Eigenschaft, für den Hersteller des Snap-Ins (erforderlich).

   In diesem Beispiel ist der Anbieter "Microsoft".

5. Fügen Sie eine öffentliche Eigenschaft für die Anbieter-Ressource des Snap-Ins (optional).

   In diesem Beispiel ist die Anbieter-Ressource "CustomPSSnapInTest, Microsoft".

6. Fügen Sie eine öffentliche Eigenschaft für die Beschreibung des Snap-Ins (erforderlich).

   In diesem Beispiel wird die Beschreibung: "Dies ist ein benutzerdefiniertes Windows PowerShell-Snap-in mit den Test-HelloWorld- und -Cmdlets Test-CustomSnapinTest".

7. Fügen Sie eine öffentliche Eigenschaft für die Ressource für die Beschreibung des Snap-Ins (optional) hinzu.

   In diesem Beispiel ist die Anbieter-Ressource an, "CustomPSSnapInTest, das ein benutzerdefiniertes Windows PowerShell-Snap-in, das die Cmdlets Test-HelloWorld" und "Test-CustomSnapinTest enthält ist".

8. Geben Sie die Cmdlets, die mit dem benutzerdefinierten-Snap-in (optional) gehören die [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) Klasse. Die hier hinzugefügte Informationen enthält den Namen des dem-Cmdlet, den Typ .NET und der Dateiname der Cmdlet-Hilfe (das Format des Dateinamens für den Cmdlet-Hilfe sollte Name.dll wurden-help.xml sein).

   In diesem Beispiel wird die Test-HelloWorld und TestCustomSnapinTest-Cmdlets.

9. Geben Sie die Anbieter, die zu der benutzerdefinierten-Snap-in (optional) gehören.

   In diesem Beispiel wird keine Anbieter angegeben.

10. Geben Sie die Typen, die zu der benutzerdefinierten-Snap-in (optional) gehören.

    In diesem Beispiel wird keine Typen angegeben werden.

11. Geben Sie die Formate, die zu der benutzerdefinierten-Snap-in (optional) gehören.

    In diesem Beispiel wird keine Formate angegeben werden.

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie Sie ein benutzerdefiniertes Windows PowerShell-Snap-in zu schreiben, die zum Registrieren der Test-HelloWorld und Test-CustomSnapinTest-Cmdlets verwendet werden können. Denken Sie daran, dass in diesem Beispiel die vollständige Assembly enthalten kann, andere Cmdlets und Anbieter, die nicht von diesem-Snap-in registriert werden.

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

Weitere Informationen zum Registrieren von-Snap-ins finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) in die [Windows PowerShell Handbuch für Programmierer](../prog-guide/windows-powershell-programmer-s-guide.md).

## <a name="see-also"></a>Weitere Informationen

[So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
