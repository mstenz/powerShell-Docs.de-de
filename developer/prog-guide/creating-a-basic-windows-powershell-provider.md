---
title: Erstellen einen einfachen Windows PowerShell-Anbieter | Microsoft-Dokumentation
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
ms.openlocfilehash: 19cc3817016d96e1412a5f3506e9d694ba55b48d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082072"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>Erstellen eines Windows PowerShell-Standardanbieters

Dieses Thema ist der Ausgangspunkt für das lernen, wie Sie einen Windows PowerShell-Anbieter zu erstellen. Der hier beschriebene grundlegenden-Anbieter bietet Methoden zum Starten und beenden den Anbieter aus, und obwohl es sich bei diesem Anbieter nicht bietet eine Möglichkeit, auf einen Datenspeicher oder zum Abrufen oder Festlegen von Daten im Datenspeicher, bietet es die grundlegende Funktionalität, die erforderlich ist alle Anbieter.

Wie bereits erwähnt, den grundlegenden Anbieter beschrieben hier die Methoden zum Starten und beenden den Anbieter implementiert. Die Windows PowerShell-Laufzeit ruft diese Methoden zum Initialisieren und die Aufhebung der Initialisierung des Anbieters.

> [!NOTE]
> Ein Beispiel für diesen Anbieter finden Sie in der AccessDBSampleProvider01.cs-Datei, die von Windows PowerShell bereitgestellt.

In den Abschnitten in diesem Thema umfassen Folgendes:

- [Definieren der Windows PowerShell-Anbieter-Klasse](#Defining-the-Windows-PowerShell-Provider-Class)

- [Definieren anbieterspezifische Informationen](#Defining-Provider-Specific-State-Information)

- [Initialisieren des Anbieters](#Initializing-the-Provider)

- [Starten von dynamischen Parametern](#Start-Dynamic-Parameters)

- [Zum Aufheben der Initialisierung des Anbieters](#Uninitializing-the-Provider)

- [Codebeispiel](#Code-Sample)

- [Testen der Windows PowerShell-Anbieter](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>Definieren der Windows PowerShell-Anbieter-Klasse

Der erste Schritt beim Erstellen eines Windows PowerShell-Anbieters ist die Klasse .NET definiert. Dieser grundlegende Anbieter definiert eine Klasse namens `AccessDBProvider` abgeleitet, die die [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) Basisklasse.

Es wird empfohlen, dass Sie Ihre Anbieterklassen Platzieren einer `Providers` Namespace Ihres API-Namespace, z. B. Xxx. PowerShell.Providers. Dieser Anbieter nutzt die `Microsoft.Samples.PowerShell.Provider` -Namespace, in dem alle Beispiele von Windows PowerShell-Anbieter ausgeführt werden.

> [!NOTE]
> Die Klasse für einen Windows PowerShell-Anbieter muss explizit als öffentlich markiert werden. Klassen, die nicht als öffentlich markiert werden standardmäßig auf interne und werden von der Windows PowerShell-Laufzeit nicht gefunden werden.

So sieht die Klassendefinition für diesen grundlegenden Anbieter aus:

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

Direkt vor der Klassendefinition, müssen Sie deklarieren die [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) Attribut, mit der Syntax [CmdletProvider()].

Sie können die Attribut-Stichworte, um weitere Deklarieren der Klasse bei Bedarf festlegen. Beachten Sie, dass die [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) hier deklarierten Attributs enthält zwei Parameter. Der erste Attributparameter gibt an, den Standard-Anzeigenamen für den Anbieter, die der Benutzer später ändern können. Der zweite Parameter gibt an, die Windows PowerShell-definierte Funktionen, die der Anbieter für die Windows PowerShell-Laufzeit während der befehlsverarbeitung verfügbar macht. Die möglichen Werte für die Funktionen des Anbieters werden definiert, durch die [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) Enumeration. Da es sich um einen Basisanbieter handelt, wird keine Funktionen unterstützt.

> [!NOTE]
> Der vollqualifizierte Name des Windows PowerShell-Anbieters enthält der Name der Assembly und anderen Attributen, die von Windows PowerShell nach der Registrierung des Anbieters bestimmt.

## <a name="defining-provider-specific-state-information"></a>Definieren anbieterspezifische Informationen

Die [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) Basisklasse und alle abgeleiteten Klassen gelten als zustandslose daran, dass die Windows PowerShell-Laufzeit-Providerinstanzen nur nach Bedarf erstellt. Aus diesem Grund, wenn der Dienstanbieter, vollständige Kontrolle und Zustandsverwaltung für anbieterspezifische Daten benötigt, es muss leiten eine Klasse von der [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) Klasse. Die abgeleitete Klasse fest, die Elemente, die den Zustand beibehalten, damit die anbieterspezifische Daten zugegriffen werden können, wenn die Windows PowerShell-Laufzeit ruft die [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) Methode, um den Anbieter zu initialisieren.

Ein Windows PowerShell-Anbieter kann auch den verbindungsbasierte Zustand beibehalten. Weitere Informationen zum Verwalten des Status der Verbindung finden Sie unter [Erstellen eines Anbieters für die PowerShell-Laufwerk](./creating-a-windows-powershell-drive-provider.md).

## <a name="initializing-the-provider"></a>Initialisieren des Anbieters

Zum Initialisieren des Anbieters, die Windows PowerShell-Laufzeit ruft die [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) Methode, wenn Windows PowerShell gestartet wird. Der Anbieter kann die standardmäßige Implementierung dieser Methode, die gibt einfach auftragsantwortnachrichten zurück zum größten Teil, verwenden die [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) Objekt, das Ihr Anbieter beschreibt. Allerdings in der Fall, in dem Sie zusätzliche Initialisierungsinformationen hinzufügen möchten, sollten Sie implementieren Ihre eigenen [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) Methode, die eine geänderte Version des der zurückgibt.[ System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) -Objekt, das an dem Anbieter übergeben wird. Im Allgemeinen sollten diese Methode bereitgestellten zurückgeben [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) -Objekt übergeben wird, oder eine geänderte [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) -Objekt, enthält andere Initialisierungsinformationen.

Dieser grundlegende Anbieter wird diese Methode nicht überschrieben werden. Der folgende Code zeigt jedoch die Standardimplementierung dieser Methode:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

Der Anbieter kann anbieterspezifische Informationen den Status verwalten, wie in beschrieben [definieren anbieterspezifische Datensynchronisierungsstatus](#Defining-Provider-Specific-State-Information). In diesem Fall muss die Implementierung überschreiben die [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) Methode, um eine Instanz der abgeleiteten Klasse zurückzugeben.

## <a name="start-dynamic-parameters"></a>Starten von dynamischen Parametern

Die Implementierung von der [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) Methode handelt es sich möglicherweise um zusätzliche Parameter. In diesem Fall sollten der Anbieter überschreiben die [System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) Methode, und geben ein Objekt mit Eigenschaften und Felder mit der Analyse wie Attribute eine Cmdlet-Klasse oder ein [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt.

Dieser grundlegende Anbieter wird diese Methode nicht überschrieben werden. Der folgende Code zeigt jedoch die Standardimplementierung dieser Methode:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>Zum Aufheben der Initialisierung des Anbieters

Um Ressourcen freizugeben, die die Windows PowerShell-Anbieter verwendet, Ihr Anbieter sollte implementieren eine eigene [System.Management.Automation.Provider.Cmdletprovider.Stop*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) Methode. Diese Methode wird von der Windows PowerShell-Laufzeit den Anbieter am Ende einer Sitzung Aufhebung der Initialisierung aufgerufen.

Dieser grundlegende Anbieter wird diese Methode nicht überschrieben werden. Der folgende Code zeigt jedoch die Standardimplementierung dieser Methode:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>Codebeispiel

Vollständigen Beispielcode finden Sie unter [AccessDbProviderSample01 Codebeispiel](./accessdbprovidersample01-code-sample.md).

## <a name="testing-the-windows-powershell-provider"></a>Testen der Windows PowerShell-Anbieter

Nach Ihrer Windows PowerShell-Anbieter mit Windows PowerShell registriert wurde, können Sie es testen, indem die unterstützten Cmdlets in der Befehlszeile ausgeführt. Für diesen grundlegenden Anbieter, führen Sie die neue Shell, und Verwenden der `Get-PSProvider` -Cmdlet zum Abrufen der Liste der Anbieter, und stellen Sie sicher, dass der Anbieter AccessDb vorhanden ist.

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

[Erstellen von Windows PowerShell-Anbieter](./how-to-create-a-windows-powershell-provider.md)

[Entwerfen Ihre Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md)