---
title: Erstellen eines einfachen Windows PowerShell-Anbieters | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- base provider [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], base provider
ms.assetid: 11eeea41-15c8-47ad-9016-0f4b72573305
caps.latest.revision: 7
ms.openlocfilehash: e825581b96f0f33893b38f9f6499dd46a7bf38eb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360519"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>Erstellen eines Windows PowerShell-Standardanbieters

Dieses Thema stellt den Ausgangspunkt für das Erstellen eines Windows PowerShell-Anbieters dar. Der hier beschriebene grundlegende Anbieter bietet Methoden zum Starten und Beenden des Anbieters, und obwohl dieser Anbieter keine Mittel zum Zugreifen auf einen Datenspeicher oder zum Abrufen oder Festlegen der Daten im Datenspeicher bereitstellt, stellt er die grundlegenden Funktionen bereit, die für erforderlich sind. alle Anbieter.

Wie bereits erwähnt, implementiert der hier beschriebene grundlegende Anbieter Methoden zum Starten und Beenden des Anbieters. Die Windows PowerShell-Laufzeit ruft diese Methoden auf, um den Anbieter zu initialisieren und deren Initialisierung zu initialisieren.

> [!NOTE]
> Sie finden ein Beispiel dieses Anbieters in der AccessDBSampleProvider01.cs-Datei, die von Windows PowerShell bereitgestellt wird.

## <a name="defining-the-windows-powershell-provider-class"></a>Definieren der Windows PowerShell-Anbieter Klasse

Der erste Schritt beim Erstellen eines Windows PowerShell-Anbieters ist die Definition der .NET-Klasse. Dieser grundlegende Anbieter definiert eine Klasse mit dem Namen "`AccessDBProvider`", die von der [System. Management. Automation. Provider. cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) -Basisklasse abgeleitet wird.

Es wird empfohlen, die Anbieter Klassen in einem `Providers`-Namespace ihres API-Namespace zu platzieren, z. b. xxx. PowerShell. Providers. Dieser Anbieter verwendet den `Microsoft.Samples.PowerShell.Provider`-Namespace, in dem alle Windows PowerShell-Anbieter Beispiele ausgeführt werden.

> [!NOTE]
> Die-Klasse für einen Windows PowerShell-Anbieter muss explizit als public gekennzeichnet werden. Klassen, die nicht als public gekennzeichnet sind, werden standardmäßig intern verwendet und werden von der Windows PowerShell-Laufzeit nicht gefunden.

Hier ist die Klassendefinition für diesen grundlegenden Anbieter:

[!code-csharp[AccessDBProviderSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

Direkt vor der Klassendefinition müssen Sie das [System. Management. Automation. Provider. cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) -Attribut mit der Syntax [cmdletprovider ()] deklarieren.

Sie können Attribut Schlüsselwörter festlegen, um die Klasse bei Bedarf weiter zu deklarieren. Beachten Sie, dass das [System. Management. Automation. Provider. cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) -Attribut, das hier deklariert ist, zwei Parameter enthält. Der erste Attribut Parameter gibt den standardmäßigen anzeigen Amen für den Anbieter an, der vom Benutzer später geändert werden kann. Der zweite Parameter gibt die Windows PowerShell-definierten Funktionen an, die der Anbieter während der Befehls Verarbeitung für die Windows PowerShell-Laufzeit verfügbar macht. Die möglichen Werte für die Anbieter Funktionen werden von der [System. Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration definiert. Da es sich hierbei um einen Basis Anbieter handelt, werden keine Funktionen unterstützt.

> [!NOTE]
> Der voll qualifizierte Name des Windows PowerShell-Anbieters schließt den Assemblynamen und andere Attribute ein, die von Windows PowerShell bei der Registrierung des Anbieters festgelegt wurden.

## <a name="defining-provider-specific-state-information"></a>Definieren Anbieter spezifischer Zustandsinformationen

Die [System. Management. Automation. Provider. cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) -Basisklasse und alle abgeleiteten Klassen werden als zustandslos angesehen, weil die Windows PowerShell-Laufzeit nur dann Anbieter Instanzen erstellt, wenn dies erforderlich ist. Wenn Ihr Anbieter eine vollständige Kontrolle und Zustands Verwaltung für anbieterspezifische Daten erfordert, muss daher eine Klasse von der [System. Management. Automation. ProviderInfo](/dotnet/api/System.Management.Automation.ProviderInfo) -Klasse abgeleitet werden. Ihre abgeleitete Klasse sollte die für die Beibehaltung des Zustands erforderlichen Elemente definieren, damit auf die anbieterspezifischen Daten zugegriffen werden kann, wenn die Windows PowerShell-Laufzeit die [System. Management. Automation. Provider. cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) -Methode aufruft. Initialisieren Sie den Anbieter.

Ein Windows PowerShell-Anbieter kann auch den verbindungsbasierten Status beibehalten. Weitere Informationen zum Beibehalten des Verbindungsstatus finden Sie unter [Erstellen eines PowerShell-Laufwerks Anbieters](./creating-a-windows-powershell-drive-provider.md).

## <a name="initializing-the-provider"></a>Initialisieren des Anbieters

Um den Anbieter zu initialisieren, ruft die Windows PowerShell-Runtime die [System. Management. Automation. Provider. cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) -Methode auf, wenn Windows PowerShell gestartet wird. Der Anbieter kann zum größten Teil die Standard Implementierung dieser Methode verwenden, die einfach das [System. Management. Automation. ProviderInfo](/dotnet/api/System.Management.Automation.ProviderInfo) -Objekt zurückgibt, das Ihren Anbieter beschreibt. Wenn Sie jedoch zusätzliche Initialisierungs Informationen hinzufügen möchten, sollten Sie eine eigene [System. Management. Automation. Provider. cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) -Methode implementieren, die eine geänderte Version von [zurückgibt. System. Management. Automation. ProviderInfo](/dotnet/api/System.Management.Automation.ProviderInfo) -Objekt, das an Ihren Anbieter übermittelt wird. Im Allgemeinen sollte diese Methode das bereitgestellte [System. Management. Automation. ProviderInfo](/dotnet/api/System.Management.Automation.ProviderInfo) -Objekt zurückgeben, das an Sie übermittelt wurde, oder ein geändertes [System. Management. Automation. ProviderInfo](/dotnet/api/System.Management.Automation.ProviderInfo) -Objekt, das weitere Initialisierungs Informationen enthält.

Dieser grundlegende Anbieter überschreibt diese Methode nicht. Der folgende Code zeigt jedoch die Standard Implementierung dieser Methode:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

Der Anbieter kann den Zustand der anbieterspezifischen Informationen wie unter [Definieren des anbieterspezifischen Daten Zustands](#defining-provider-specific-state-information)beschrieben beibehalten. In diesem Fall muss Ihre Implementierung die [System. Management. Automation. Provider. cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) -Methode überschreiben, um eine Instanz der abgeleiteten Klasse zurückzugeben.

## <a name="start-dynamic-parameters"></a>Dynamische Parameter starten

Die Anbieter Implementierung der [System. Management. Automation. Provider. cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) -Methode erfordert möglicherweise zusätzliche Parameter. In diesem Fall sollte der Anbieter die [System. Management. Automation. Provider. cmdletprovider. startdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) -Methode außer Kraft setzen und ein Objekt zurückgeben, das über Eigenschaften und Felder mit ähnlichen Attributen wie einer Cmdlet-Klasse oder einen [ System. Management. Automation. runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -Objekt.

Dieser grundlegende Anbieter überschreibt diese Methode nicht. Der folgende Code zeigt jedoch die Standard Implementierung dieser Methode:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>Aufheben der Initialisierung des Anbieters

Zum Freigeben von Ressourcen, die der Windows PowerShell-Anbieter verwendet, sollte Ihr Anbieter seine eigene [System. Management. Automation. Provider. cmdletprovider. Break *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) -Methode implementieren. Diese Methode wird von der Windows PowerShell-Laufzeit aufgerufen, um die Initialisierung des Anbieters bei der Sitzung zu beenden.

Dieser grundlegende Anbieter überschreibt diese Methode nicht. Der folgende Code zeigt jedoch die Standard Implementierung dieser Methode:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>Code Beispiel

Einen umfassenden Beispielcode finden Sie unter [AccessDbProviderSample01-Codebeispiel](./accessdbprovidersample01-code-sample.md).

## <a name="testing-the-windows-powershell-provider"></a>Testen des Windows PowerShell-Anbieters

Nachdem der Windows PowerShell-Anbieter bei Windows PowerShell registriert wurde, können Sie ihn testen, indem Sie die unterstützten Cmdlets in der Befehlszeile ausführen. Führen Sie für diesen grundlegenden Anbieter die neue Shell aus, und verwenden Sie das Cmdlet "`Get-PSProvider`", um die Liste der Anbieter abzurufen und sicherzustellen, dass der accessdb-Anbieter vorhanden ist.

```powershell
Get-PSProvider
```

Die folgende Ausgabe wird angezeigt:

```output
Name                 Capabilities                  Drives
----                 ------------                  ------
AccessDb             None                          {}
Alias                ShouldProcess                 {Alias}
Environment          ShouldProcess                 {Env}
FileSystem           Filter, ShouldProcess         {C, Z}
Function             ShouldProcess                 {function}
Registry             ShouldProcess                 {HKLM, HKCU}
```

## <a name="see-also"></a>Weitere Informationen

[Erstellen von Windows PowerShell-Anbietern](./how-to-create-a-windows-powershell-provider.md)

[Entwerfen Ihres Windows PowerShell-Anbieters](./designing-your-windows-powershell-provider.md)
