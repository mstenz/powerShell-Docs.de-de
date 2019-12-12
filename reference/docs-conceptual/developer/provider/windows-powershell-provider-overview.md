---
title: Übersicht über den Windows PowerShell-Anbieter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82244fbd-07b9-47f3-805c-3fb90ebbf58a
caps.latest.revision: 13
ms.openlocfilehash: 81f6c8cd75ccea9e711cd8f6d6daa6cca5a499a0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366289"
---
# <a name="windows-powershell-provider-overview"></a>Windows PowerShell-Anbieter: Übersicht

Ein Windows PowerShell-Anbieter ermöglicht es, einen beliebigen Datenspeicher wie ein Dateisystem verfügbar zu machen, als ob es sich um ein bereitgestelltes Laufwerk handelt. Mit dem integrierten Registrierungs Anbieter können Sie z. b. in der Registrierung navigieren, wie Sie im `c` Laufwerk des Computers navigieren würden. Ein Anbieter kann auch die `Item`-Cmdlets (z. b. `Get-Item`, `Set-Item`usw.) überschreiben, sodass die Daten im Datenspeicher so behandelt werden können, wie Dateien und Verzeichnisse beim Navigieren in einem Dateisystem behandelt werden. Weitere Informationen zu Anbietern und Laufwerken sowie zu den integrierten Anbietern in Windows PowerShell finden Sie unter [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).

## <a name="providers-and-drives"></a>Anbieter und Laufwerke

Ein Anbieter definiert die Logik, die für den Zugriff, die Navigation und die Bearbeitung eines Datenspeicher verwendet wird, während ein Laufwerk einen bestimmten Einstiegspunkt in einen Datenspeicher (oder einen Teil eines Datenspeicher) angibt, der vom Typ ist, der vom Anbieter definiert wird. Beispielsweise ermöglicht der Registrierungs Anbieter den Zugriff auf Strukturen und Schlüssel in einer Registrierung, und die HKLM-und HKCU-Laufwerke geben die entsprechenden Strukturen innerhalb der Registrierung an. Die HKLM-und HKCU-Laufwerke verwenden beide den Registrierungs Anbieter.

Wenn Sie einen Anbieter schreiben, können Sie Standard Laufwerke angeben, die automatisch erstellt werden, wenn der Anbieter verfügbar ist. Außerdem definieren Sie eine Methode, mit der neue Laufwerke erstellt werden, die diesen Anbieter verwenden.

## <a name="type-of-providers"></a>Typ der Anbieter

Es gibt mehrere Typen von Anbietern, von denen jede eine andere Ebene der Funktionalität bietet. Ein Anbieter wird als Klasse implementiert, die von einem der nachfolgenden der [System. Management. Automation. Sessionstatus ecategory](/dotnet/api/system.management.automation.sessionstatecategory?view=pscore-6.2.0) - **cmdletprovider** -Klasse abgeleitet wird. Informationen zu den verschiedenen Typen von Anbietern finden Sie unter [Anbieter Typen](./provider-types.md).

## <a name="provider-cmdlets"></a>Anbieter-Cmdlets

Anbieter können Methoden implementieren, die Cmdlets entsprechen. Dadurch werden benutzerdefinierte Verhaltensweisen für diese Cmdlets erstellt, wenn Sie in einem Laufwerk für diesen Anbieter verwendet werden. Abhängig vom Typ des Anbieters sind unterschiedliche Sätze von Cmdlets verfügbar. Eine umfassende Liste der Cmdlets, die für die Anpassung in-Anbietern verfügbar sind, finden Sie unter [Provider-Cmdlets](./provider-cmdlets.md).

## <a name="provider-paths"></a>Anbieter Pfade

Benutzer navigieren wie Dateisysteme zu Anbieter Laufwerken. Aus diesem Grund erwarten Sie, dass die Syntax der Pfade den Pfaden entspricht, die in der Dateisystem Navigation verwendet werden. Wenn ein Benutzer ein Anbieter-Cmdlet ausführt, geben Sie einen Pfad zu dem Element an, auf das zugegriffen werden soll. Der angegebene Pfad kann auf verschiedene Weise interpretiert werden. Ein Anbieter sollte mindestens einen der folgenden Pfad Typen unterstützen.

### <a name="drive-qualified-paths"></a>Laufwerk qualifizierte Pfade

Bei einem Laufwerk qualifizierten Pfad handelt es sich um eine Kombination aus Elementname, Container und unter Containern, in der sich das Element befindet, und dem Windows PowerShell-Laufwerk, über das auf das Element zugegriffen wird. (Laufwerke werden vom Anbieter definiert, der für den Zugriff auf den Datenspeicher verwendet wird. Dieser Pfad beginnt mit dem Laufwerks Namen gefolgt von einem Doppelpunkt (:). Beispiel: `get-childitem C:`

### <a name="provider-qualified-paths"></a>Vom Anbieter qualifizierte Pfade

Damit die Windows PowerShell-Engine den Anbieter initialisieren und deren Initialisierung initialisieren kann, muss der Anbieter einen von einem Anbieter qualifizierten Pfad unterstützen. Beispielsweise kann der Benutzer den File System-Anbieter initialisieren und dessen Initialisierung initialisieren, da er den folgenden vom Anbieter qualifizierten Pfad definiert: `FileSystem::\\uncshare\abc\bar`.

### <a name="provider-direct-paths"></a>Anbieter-direkte Pfade

Um den Remote Zugriff auf Ihren Windows PowerShell-Anbieter zuzulassen, sollte er einen Anbieter-Direct-Pfad unterstützen, um direkt an den Windows PowerShell-Anbieter für den aktuellen Speicherort zu übergeben. Der Windows PowerShell-Anbieter für die Registrierung kann z. b. `\\server\regkeypath` als Anbieter-Direct-Pfad verwenden.

### <a name="provider-internal-paths"></a>Anbieter interne Pfade

Um dem Anbieter-Cmdlet den Zugriff auf Daten mit nicht-Windows PowerShell-APIs (Application Programming Interface) zu gestatten, sollte der Windows PowerShell-Anbieter einen Anbieter internen Pfad unterstützen. Dieser Pfad wird nach dem "::" im vom Anbieter qualifizierten Pfad angegeben. Beispielsweise ist der Anbieter interne Pfad für den Windows PowerShell-Anbieter "File System" `\\uncshare\abc\bar`.

## <a name="overriding-cmdlet-parameters"></a>Überschreiben der Cmdlet-Parameter

Das Verhalten einiger Anbieter spezifischer Cmdlets kann von einem Anbieter überschrieben werden. Eine Liste der Parameter, die überschrieben werden können, und wie Sie in ihrer Anbieter Klasse überschrieben werden können, finden Sie unter [Anbieter-Cmdlet-Parameter](./provider-cmdlet-parameters.md) .

## <a name="dynamic-parameters"></a>Dynamische Parameter

Anbieter können dynamische Parameter definieren, die einem Anbieter-Cmdlet hinzugefügt werden, wenn der Benutzer einen bestimmten Wert für einen der statischen Parameter des Cmdlets angibt. Ein Anbieter übernimmt dies durch Implementieren mindestens einer dynamischen Parameter Methode. Eine Liste der Cmdlet-Parameter, die verwendet werden können, um dynamischen Parameter hinzuzufügen, und die Methoden, die verwendet werden, um Sie zu implementieren, finden Sie unter [Anbieter-Cmdlet dynamische Parameter](./provider-cmdlet-dynamic-parameters.md).

## <a name="provider-capabilities"></a>Anbieter Funktionen

Die [System. Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration definiert eine Reihe von Funktionen, die Anbieter unterstützen können. Hierzu gehören die Möglichkeit, Platzhalter zu verwenden, Elemente zu filtern und Transaktionen zu unterstützen. Fügen Sie zum Angeben von Funktionen für einen Anbieter eine Liste der Werte des [Systems hinzu. die Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration, kombiniert mit einem logischen `OR` Vorgang, als die [System. Management. Automation. Provider. cmdletproviderattribute. providerfunktionalitäten *](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) -Eigenschaft (der zweite Parameter des Attributs) des [System. Management. Automation. Provider. cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) -Attributs für Ihre Anbieter Klasse. Das folgende Attribut gibt z. b. an, dass der Anbieter die **Transaktions** Funktionen " [System. Management. Automation. Provider. Providerfunktionen](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) **" und "** [System. Management. Automation. Provider. Providerfunktionen](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) " unterstützt.

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>Hilfe zum Anbieter-Cmdlet

Wenn Sie einen Anbieter schreiben, können Sie Ihre eigene Hilfe für die von Ihnen unterstützten Anbieter-Cmdlets implementieren. Dies umfasst ein einzelnes Hilfethema für jedes Provider-Cmdlet oder mehrere Versionen eines Hilfe Themas für Fälle, in denen das Provider-Cmdlet auf der Grundlage der Verwendung dynamischer Parameter unterschiedlich agiert. Zur Unterstützung von Anbieter-Cmdlet-spezifischer Hilfe muss Ihr Anbieter die [System. Management. Automation. Provider. icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) -Schnittstelle implementieren.

Die Windows PowerShell-Engine ruft die [System. Management. Automation. Provider. icmdletprovidersupportshelp. gethelpmaml *](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) -Methode auf, um das Hilfethema für die Anbieter-Cmdlets anzuzeigen. Die Engine gibt den Namen des Cmdlets an, das der Benutzer beim Ausführen des `Get-Help` Cmdlets angegeben hat, sowie den aktuellen Pfad des Benutzers. Der aktuelle Pfad ist erforderlich, wenn Ihr Anbieter verschiedene Versionen desselben Anbieter-Cmdlets für verschiedene Laufwerke implementiert. Die-Methode muss eine Zeichenfolge zurückgeben, die den XML-Code für die Cmdlet-Hilfe enthält.

Der Inhalt der Hilfedatei wird mithilfe von psmaml XML geschrieben. Dabei handelt es sich um dasselbe XML-Schema, das zum Schreiben von Hilfe Inhalten für eigenständige Cmdlets verwendet wird. Fügen Sie den Inhalt für die benutzerdefinierte Cmdlet-Hilfe der Hilfedatei für Ihren Anbieter unter dem `CmdletHelpPaths`-Element hinzu. Das folgende Beispiel zeigt das `command`-Element für ein einzelnes Anbieter-Cmdlet und zeigt, wie Sie den Namen des Anbieter-Cmdlets für Ihren Anbieter angeben. stützten

```xml
<CmdletHelpPaths>
  <command:command>
    <command:details>
      <command:name>ProviderCmdletName</command:name>
      <command:verb>Verb</command:verb>
      <command:noun>Noun</command:noun>
    <command:details>
  </command:command>
<CmdletHelpPath>
```

## <a name="see-also"></a>Weitere Informationen

[Funktionalität des Windows PowerShell-Anbieters](./provider-types.md)

[Anbieter-Cmdlets](./provider-cmdlets.md)

[Schreiben eines Windows PowerShell-Anbieters](./writing-a-windows-powershell-provider.md)