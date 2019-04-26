---
title: Windows PowerShell-Anbieter (Übersicht) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82244fbd-07b9-47f3-805c-3fb90ebbf58a
caps.latest.revision: 13
ms.openlocfilehash: 0d4addc0a064873701ae15c204dbd335f3374ab7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080905"
---
# <a name="windows-powershell-provider-overview"></a>Windows PowerShell-Anbieter: Übersicht

Ein Windows PowerShell-Anbieter kann einen beliebigen Datenspeicher als handele es sich um ein bereitgestelltes Laufwerk wie ein Dateisystem verfügbar gemacht werden. Z. B. des integrierten Registrierungsanbieters können Sie die Registrierung zu navigieren, wie Sie navigieren, würde die `c` Laufwerk des Computers. Ein Anbieter kann auch überschreiben, die `Item` Cmdlets (z. B. `Get-Item`, `Set-Item`usw.), dass die Daten im Datenspeicher können, wie Dateien behandelt werden und Verzeichnisse behandelt werden, wenn Sie ein Dateisystem zu navigieren. Weitere Informationen über Anbieter und Laufwerke und die integrierten Anbieter in Windows PowerShell finden Sie unter [About_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).

## <a name="providers-and-drives"></a>Anbieter und Laufwerke

Ein Anbieter definiert die Logik, die verwendet wird, den Zugriff, navigieren und einen Datenspeicher, zu bearbeiten, während ein Laufwerk einem bestimmten Einstiegspunkt zu einem Datenspeicher (oder einen Teil eines Datenspeichers) gibt an, der den Typ, der vom Anbieter definiert ist. Beispielsweise der Registrierungsanbieter können Sie den Zugriff auf Strukturen und Schlüssel in einer Registrierung, und die Laufwerke HKLM und HKCU Geben Sie die entsprechenden Strukturen in der Registrierung. Die Laufwerke HKLM und HKCU verwenden den Registrierungsanbieter.

Wenn Sie einen Anbieter schreiben, können Sie standardmäßige Laufwerken-Laufwerke angeben, die automatisch erstellt werden, wenn der Anbieter verfügbar ist. Außerdem definieren Sie eine Methode zum Erstellen von neuen Laufwerke, die diesen Anbieter verwenden.

## <a name="type-of-providers"></a>Der Typ von Anbietern

Es gibt mehrere Arten von Anbietern, von die jeder einen unterschiedlichen Grad an Funktionalität bietet. Ein Anbieter wird als eine von einem Nachfolgerelemente des abgeleitete Klasse implementiert die [System.Management.Automation.Sessionstatecategory.Cmdletprovider](/dotnet/api/System.Management.Automation.SessionStateCategory.CmdletProvider) Klasse. Weitere Informationen zu den verschiedenen Typen von Anbietern finden Sie unter [Anbietertypen](./provider-types.md).

## <a name="provider-cmdlets"></a>Anbieter-Cmdlets

Anbieter können Methoden, die Cmdlets entsprechen, implementieren und Erstellen von benutzerdefinierten Verhalten für diese Cmdlets aus, wenn in einem Laufwerk für diesen Anbieter verwendet. Je nach Art des Anbieters stehen unterschiedliche Sätze von Cmdlets. Eine vollständige Liste der Cmdlets für die Anpassung im Anbieter verfügbar sind, finden Sie unter [Anbieter-Cmdlets](./provider-cmdlets.md).

## <a name="provider-paths"></a>-Anbieterpfade

Benutzer navigieren Anbieter Laufwerken wie Dateisysteme. Aus diesem Grund erwarten, dass sie die Syntax von Pfaden zu den Pfaden, die in dateisystemnavigation verwendet entsprechen. Wenn ein Benutzer eine Anbieter-Cmdlet ausgeführt wird, geben sie einen Pfad zu das Element zugegriffen werden kann. Der angegebene Pfad kann auf verschiedene Weise interpretiert werden. Ein Anbieter sollte es sich um eine oder mehrere der folgenden Pfadtypen unterstützen.

### <a name="drive-qualified-paths"></a>Laufwerkbezogenen Pfade

Ein Drive-qualified Pfad ist eine Kombination aus den Namen, den Container und untergeordnete Container, in denen sich das Element befindet, und das Windows PowerShell-Laufwerk, das über den das Element zugegriffen wird. (Laufwerke werden vom Anbieter, die verwendet wird, Zugriff auf den Data Store definiert. Dieser Pfad beginnt mit den Namen des Laufwerks, gefolgt von einem Doppelpunkt (:). Beispiel: `get-childitem C:`

### <a name="provider-qualified-paths"></a>Anbieter vollqualifizierten Pfade

Um das Windows PowerShell-Modul zu initialisieren und die Aufhebung der Initialisierung der Ihren Anbieters zu ermöglichen, muss der Anbieter einen Anbieter-qualified Pfad unterstützen. Der Benutzer kann z. B. zu initialisieren und Initialisierung aufheben den FileSystem-Anbieter, da sie die folgenden Anbieter vollqualifizierten Pfad definiert: `FileSystem::\\uncshare\abc\bar`.

### <a name="provider-direct-paths"></a>Anbieter-Direct-Pfade

Um Remotezugriff auf Ihren Windows PowerShell-Anbieter zu ermöglichen, sollten sie einen Anbieter-Direct-Pfad direkt an den Windows PowerShell-Anbieter für die aktuelle Position übergeben unterstützen. Der Windows PowerShell-Registrierungsanbieter können z. B. `\\server\regkeypath` als Anbieter-Direct-Pfad.

### <a name="provider-internal-paths"></a>Anbieter-interne Pfade

Um die Anbieter-Cmdlet, um Zugriff auf Daten, die mit nicht - Windows PowerShell, Application programming Interfaces (APIs) zu ermöglichen, sollte Ihre Windows PowerShell-Anbieter einen Anbieter-internen Pfad unterstützen. Dieser Pfad wird angegeben, nach der "::" im Anbieter vollqualifizierten Pfad. Die Anbieter-internen Pfad für die Windows PowerShell-Filesystem-Anbieter ist z. B. `\\uncshare\abc\bar`.

## <a name="overriding-cmdlet-parameters"></a>Überschreiben die Cmdlet-Parameter

Das Verhalten einiger-spezifischen Cmdlets kann von einem Anbieter überschrieben werden. Eine Liste von Parametern, die überschrieben werden kann, und wie Sie sie in Ihrer Anbieterklasse außer Kraft setzen, finden Sie unter [Anbieter-Cmdlet-Parameter](./provider-cmdlet-parameters.md)

## <a name="dynamic-parameters"></a>Dynamische Parameter

Anbieter können dynamische Parameter definieren, die einem Anbieter-Cmdlet hinzugefügt werden, wenn der Benutzer einen bestimmten Wert für eine der statischen Parameter des Cmdlets angibt. Ein Anbieter wird durch die Implementierung eine oder mehrere dynamische Parameter-Methoden. Eine Liste der Cmdlet-Parameter, die zum Hinzufügen von dynamischer Parameter und die Methoden zur Implementierung verwendeten verwendet werden können, finden Sie unter [Anbieter-Cmdlet dynamische Parameter](./provider-cmdlet-dynamic-parameters.md).

## <a name="provider-capabilities"></a>Funktionen des Anbieters

Die [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) Enumeration definiert eine Reihe von Funktionen, die Anbieter unterstützen können. Dazu gehören die Möglichkeit, die Platzhalter verwenden, Filtern von Elementen und Unterstützung für Transaktionen. Um Funktionen für einen Anbieter zu anzugeben, fügen Sie eine Liste von Werten der [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) Enumeration, die in Kombination mit einer logischen `OR` -Operation, als die [ System.Management.Automation.Provider.Cmdletproviderattribute.Providercapabilities*](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) Eigenschaft (der zweite Parameter des Attributs), der die [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) Attribut für die Provider-Klasse. Das folgende Attribut gibt beispielsweise an, dass der Anbieter unterstützt die [System.Management.Automation.Provider.Providercapabilities.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.ShouldProcess) und [ System.Management.Automation.Provider.Providercapabilities.Transactions](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.Transactions) Funktionen.

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>Anbieter-Cmdlet-Hilfe

Wenn Sie einen Anbieter schreiben, können Sie Ihre eigenen Hilfe für die Anbieter-Cmdlets implementieren, die Sie unterstützen. Dies schließt ein einzelnes Hilfethema für jeden Anbieter-Cmdlet oder mehrere Versionen eines Hilfethemas für Fälle, in dem der Anbieter-Cmdlet fungiert, unterschiedlich basierend auf der Verwendung von dynamischen Parametern. Um Cmdlet-spezifische Hilfe durch Anbieter zu unterstützen, muss Ihr Anbieter implementieren die [System.Management.Automation.Provider.Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) Schnittstelle.

Ruft die Windows PowerShell-Engine die [System.Management.Automation.Provider.Icmdletprovidersupportshelp.Gethelpmaml*](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) Methode, um das Hilfethema für Ihre Anbieter-Cmdlets anzuzeigen. Das Modul gibt den Namen des Cmdlets, zu dem der Benutzer angegeben werden, bei der Ausführung der `Get-Help` Cmdlet und den aktuellen Pfad des Benutzers. Der aktuelle Pfad ist erforderlich, wenn Ihr Anbieter unterschiedliche Versionen des gleichen Anbieter-Cmdlets für unterschiedliche Laufwerke implementiert. Die Methode muss eine Zeichenfolge zurückgeben, die den XML-Code für die Cmdlet-Hilfe enthält.

Der Inhalt für die Hilfedatei wird mit PSMAML XML geschrieben. Dies ist das gleiche XML-Schema, das für das Schreiben von Hilfeinhalt für eigenständige-Cmdlets verwendet wird. Fügen Sie den Inhalt für Ihr benutzerdefiniertes Cmdlet-Hilfe zu der Hilfedatei für den Anbieter unter dem `CmdletHelpPaths` Element. Das folgende Beispiel zeigt die `command` -Element für ein einzelnen Anbieter-Cmdlet, und es wird gezeigt, wie Sie den Namen des Cmdlets, Anbieter angeben, die Ihrem Anbieter. supports

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

[Windows PowerShell-Anbieter-Funktion](./provider-types.md)

[Anbieter-Cmdlets](./provider-cmdlets.md)

[Schreiben Sie ein Windows PowerShell-Anbieter](./writing-a-windows-powershell-provider.md)