---
title: Schreiben eines benutzerdefinierten Windows PowerShell-Snap-Ins | Microsoft-Dokumentation
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
ms.openlocfilehash: aa6e4a4615f2681efa691008c86611f0df4e07d7
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870488"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a>Schreiben eines benutzerdefinierten Windows PowerShell-Snap-Ins

Dieses Beispiel zeigt, wie Sie ein Windows PowerShell-Snap-in schreiben, mit dem bestimmte Cmdlets registriert werden.

Bei dieser Art von Snap-in geben Sie an, welche Cmdlets, Anbieter, Typen oder Formate registriert werden sollen. Weitere Informationen zum Schreiben eines Snap-Ins, das alle Cmdlets und Anbieter in einer Assembly registriert, finden Sie unter [Schreiben eines Windows PowerShell-Snap-Ins](./writing-a-windows-powershell-snap-in.md).

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>Zum Schreiben eines Windows PowerShell-Snap-Ins, mit dem bestimmte Cmdlets registriert werden.

1. Fügen Sie das RunInstallerAttribute-Attribut hinzu.
2. Erstellen Sie eine öffentliche Klasse, die von der [System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn) -Klasse abgeleitet wird.

   In diesem Beispiel lautet der Klassenname "custompssnapintest".

3. Fügen Sie eine öffentliche Eigenschaft für den Namen des Snap-Ins hinzu (erforderlich). Verwenden Sie beim Benennen von Snap-Ins keines der folgenden Zeichen: `#`, `.`, `,`, `(`, `)`, `{`, `}`, `[`, `]`, `&`, `-`, `/`, `\`, `$`, `;`, `:`, `"`, `'`, `<`, `>`, `|`, `?`, `@`, `` ` ``, `*`

   In diesem Beispiel lautet der Name des Snap-Ins "custompssnapintest".

4. Hinzufügen einer öffentlichen Eigenschaft für den Anbieter des Snap-Ins (erforderlich).

   In diesem Beispiel ist der Lieferant "Microsoft".

5. Fügen Sie eine öffentliche Eigenschaft für die Vendor-Ressource des Snap-Ins hinzu (optional).

   In diesem Beispiel lautet die Ressource "Vendor" "custompssnapintest, Microsoft".

6. Fügen Sie eine öffentliche Eigenschaft für die Beschreibung des Snap-Ins hinzu (erforderlich).

   In diesem Beispiel lautet die Beschreibung: "Dies ist ein benutzerdefiniertes Windows PowerShell-Snap-in, das die `Test-HelloWorld`-und `Test-CustomSnapinTest`-Cmdlets enthält."

7. Fügen Sie eine öffentliche Eigenschaft für die Description-Ressource des Snap-Ins hinzu (optional).

   In diesem Beispiel lautet die Ressource "Vendor" wie folgt:

   > Custompssnapintest ist ein benutzerdefiniertes Windows PowerShell-Snap-in, das die Cmdlets "Test-HelloWorld" und "Test-customsnapintest" enthält.

8. Geben Sie die Cmdlets, die zum benutzerdefinierten Snap-in (optional) gehören, mithilfe der [System. Management. Automation. Runspaces. cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) -Klasse an. Die hier hinzugefügten Informationen umfassen den Namen des Cmdlets, den .NET-Typ und den Namen der Cmdlet-Hilfedatei (das Format des Cmdlet-Hilfe Dateinamens sollte` name.dll-help.xml`sein).

   In diesem Beispiel werden die Cmdlets Test-HelloWorld und testcustomsnapintest hinzugefügt.

9. Geben Sie die Anbieter an, die zum benutzerdefinierten Snap-in gehören (optional).

   In diesem Beispiel werden keine Anbieter angegeben.

10. Geben Sie die Typen an, die zum benutzerdefinierten Snap-in gehören (optional).

    In diesem Beispiel werden keine Typen angegeben.

11. Geben Sie die Formate an, die zum benutzerdefinierten Snap-in gehören (optional).

    In diesem Beispiel werden keine Formate angegeben.

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie Sie ein benutzerdefiniertes Windows PowerShell-Snap-in schreiben, das zum Registrieren der `Test-HelloWorld` und `Test-CustomSnapinTest`-Cmdlets verwendet werden kann. Beachten Sie, dass in diesem Beispiel die vollständige Assembly andere Cmdlets und Anbieter enthalten kann, die nicht von diesem Snap-in registriert werden.

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

Weitere Informationen zum Registrieren von Snap-Ins finden [Sie unter Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions/ms714644(v=vs.85)) im [Windows PowerShell-Programmier Handbuch](../prog-guide/windows-powershell-programmer-s-guide.md).

## <a name="see-also"></a>Siehe auch

[Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
