---
title: Entwerfen Ihre Windows PowerShell-Anbieter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], designing
ms.assetid: 11d20319-cc40-4227-b810-4af33372b182
caps.latest.revision: 10
ms.openlocfilehash: 711a85e9b2eade7b9095d7560f53610e709e380a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081817"
---
# <a name="designing-your-windows-powershell-provider"></a>Entwerfen eines Windows PowerShell-Anbieters

Sie sollten einen Windows PowerShell-Anbieter implementieren, wenn Ihr Produkt oder die Konfiguration einen Satz von gespeicherten Daten, z. B. eine Datenbank verfügbar macht, die der Benutzer navigieren oder durchsuchen soll. Wenn Ihr Produkt einen Container bereitstellt, auch wenn es sich nicht um einen Container mit mehreren Ebenen ist, ist es zudem sinnvoll, einen Windows PowerShell-Anbieter implementiert. Beispielsweise empfiehlt es sich um eine Windows PowerShell-Containeranbieter implementieren, wenn einer der Cmdlet-Verb kopieren, verschieben, umbenennen, neu, oder Entfernen einer Operation für Ihre Daten Produkts oder einer Konfiguration sinnvoll ist.

## <a name="windows-powershell-paths-identify-your-provider"></a>Windows PowerShell-Pfaden zu Ihrem Anbieter identifizieren.

Die Windows PowerShell-Laufzeit verwendet Windows PowerShell-Pfaden, um Zugriff auf den entsprechenden Windows PowerShell-Anbieter. Wenn ein Cmdlet einen dieser Pfade angegeben ist, weiß der Common Language Runtime, welcher Anbieter verwenden, um den zugehörigen Datenspeicher zuzugreifen. Diese Pfade enthalten laufwerkbezogenen Pfade, Anbieter vollqualifizierten Pfade, Anbieter-Direct-Pfade und internen Anbieter-Pfade. Jeder Windows PowerShell-Anbieter muss es sich um eine oder mehrere dieser Pfade unterstützen.

Weitere Informationen zu Windows PowerShell-Pfaden finden Sie in der Funktionsweise von Windows PowerShell.

### <a name="defining-a-drive-qualified-path"></a>Definieren einen Drive-Qualified Pfad

Damit wird die Benutzer den Zugriff auf Daten, die sich auf einem physischen Laufwerk befindet, muss Ihre Windows PowerShell-Anbieter einen Drive-qualified Pfad unterstützen. Dieser Pfad beginnt mit den Namen des Laufwerks, gefolgt von einem Doppelpunkt (:),), z. B. Mydrive:\abc\bar.

### <a name="defining-a-provider-qualified-path"></a>Definieren einen Anbieter qualifizierten Pfad

Um die Windows PowerShell-Laufzeit zu initialisieren und die Aufhebung der Initialisierung des Anbieters zu ermöglichen, muss Ihre Windows PowerShell-Anbieter einen Anbieter qualifizierten Pfad unterstützen. Z. B. FileSystem::\\\uncshare\abc\bar ist der Anbieter vollqualifizierten Pfad für der Filesystem-Anbieter zur Verfügung gestellt, von Windows PowerShell.

### <a name="defining-a-provider-direct-path"></a>Definieren einen Anbieter-Direct-Pfad

Um Remotezugriff auf Ihren Windows PowerShell-Anbieter zu ermöglichen, sollten sie einen Anbieter-Direct-Pfad direkt an den Windows PowerShell-Anbieter für die aktuelle Position übergeben unterstützen. Der Windows PowerShell-Registrierungsanbieter können z. B. \\\server\regkeypath als Anbieter-Direct-Pfad.

### <a name="defining-a-provider-internal-path"></a>Definieren einen internen Anbieter-Pfad

Um die Anbieter-Cmdlet, um Zugriff auf Daten, die mit nicht - Windows PowerShell, Application programming Interfaces (APIs) zu ermöglichen, sollte Ihre Windows PowerShell-Anbieter einen Anbieter-internen Pfad unterstützen. Dieser Pfad wird angegeben, nach der "::" im Anbieter vollqualifizierten Pfad. Die Anbieter-internen Pfad für die Windows PowerShell-Filesystem-Anbieter ist z. B. \\\uncshare\abc\bar.

## <a name="changing-stored-data"></a>Ändern von gespeicherten Daten

Beim Überschreiben von Methoden, die den zugrunde liegenden Datenspeicher zu ändern, rufen Sie immer die [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) Methode mit der neuesten Version des Elements geändert, -Methode. Die Infrastruktur wird bestimmt, ob das Objekt an die Pipeline, z. B. wenn der Benutzer gibt an, den - PassThru-Parameter übergeben werden muss. Wenn das aktuelle Element abrufen ein kostspieliger Vorgang (bemerkbar) ist, können Sie testen die Context.PassThru-Eigenschaft, um zu bestimmen, ob Sie tatsächlich das resultierende Element schreiben müssen.

## <a name="choose-a-base-class-for-your-provider"></a>Wählen Sie eine Basisklasse für den Anbieter

Windows PowerShell bietet es sich um eine Reihe von Basisklassen, die Sie verwenden können, um Ihren eigenen Windows PowerShell-Anbieter implementieren. Beim Entwerfen eines Anbieters, wählen Sie die Basisklasse, die in diesem Abschnitt beschrieben wird, die sich am besten für Ihre Anforderungen.

Jeder Windows PowerShell-Anbieter-Basisklasse stellt einen Satz von Cmdlets zur Verfügung. In diesem Abschnitt wird beschrieben, die Cmdlets, aber ihre Parameter wird nicht beschrieben.

Verwenden den Sitzungszustand, die Windows PowerShell-Laufzeit stellt mehrere Location-Cmdlets zur Verfügung bestimmte Windows PowerShell-Anbieter, wie z. B. die `Get-Location`, `Set-Location`, `Pop-Location`, und `Push-Location` Cmdlets. Sie können die `Get-Help` -Cmdlet zum Abrufen von Informationen zu diesen Location-Cmdlets.

### <a name="cmdletprovider-base-class"></a>CmdletProvider-Basisklasse

Die [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) -Klasse definiert einen einfachen Windows PowerShell-Anbieter. Diese Klasse unterstützt die Deklaration des Anbieters und stellt eine Reihe von Eigenschaften und Methoden, die auf alle Windows PowerShell-Anbieter verfügbar sind. Die Klasse wird aufgerufen, indem die `Get-PSProvider` -Cmdlet zum Auflisten aller verfügbaren Anbieter für eine Sitzung. Die Implementierung von diesem Cmdlet wird von der Sitzungsstatus zur Verfügung gestellt.

> [!NOTE]
> Windows PowerShell-Anbieter sind für alle Bereiche der Windows PowerShell-Sprache verfügbar.

### <a name="drivecmdletprovider-base-class"></a>DriveCmdletProvider-Basisklasse

Die [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Klasse definiert einen Anbieter der Windows PowerShell-Laufwerk, Vorgänge für neue Datenträger hinzufügen, entfernen die vorhandenen Laufwerke und initialisieren die Standard-Laufwerke unterstützt. Zum Beispiel initialisiert der FileSystem-Anbieter von Windows PowerShell bereitgestellt Laufwerke für alle Volumes, die bereitgestellt werden, z. B. Festplatten und CD/DVD-Gerät-Laufwerke.

Diese Klasse wird von der [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) Basisklasse. Die folgende Tabelle enthält die Cmdlets, die von dieser Klasse verfügbar gemacht werden. Zusätzlich zu den aufgeführt die `Get-PSDrive` -Cmdlet (bereitgestellt von Sitzungszustand) ist eine verwandte-Cmdlet, das zum Abrufen der verfügbaren Laufwerke verwendet wird.

|Cmdlet|Definition|
|------------|----------------|
|`New-PSDrive`|Erstellt ein neues Laufwerk für die Sitzung, und streamt Informationen zum Laufwerk.|
|`Remove-PSDrive`|Entfernt ein Laufwerk aus der Sitzung.|

### <a name="itemcmdletprovider-base-class"></a>ItemCmdletProvider-Basisklasse

Die [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse definiert einen Anbieter der Windows PowerShell-Element, die Operationen für die einzelnen Elemente des Datenspeichers, und sie einen beliebigen Container nicht vorausgesetzt oder Navigationsfunktionen. Diese Klasse wird von der [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Basisklasse. Die folgende Tabelle enthält die Cmdlets, die von dieser Klasse verfügbar gemacht werden.

|Cmdlet|Definition|
|------------|----------------|
|`Clear-Item`|Löscht den aktuellen Inhalt von Elementen an der angegebenen Position und mit dem "clear", vom Anbieter angegebenen Wert ersetzt. Dieses Cmdlet aus, übergibt ein Ausgabeobjekt über die Pipeline nicht, es sei denn, seine `PassThru` Parameter angegeben ist.|
|`Get-Item`|Ruft Elemente aus der angegebenen Position ab, und die resultierenden Objekte streamt.|
|`Invoke-Item`|Ruft die Standardaktion für das Element am angegebenen Pfad.|
|`Set-Item`|Legt ein Element am angegebenen Speicherort mit dem angegebenen Wert fest. Dieses Cmdlet aus, übergibt ein Ausgabeobjekt über die Pipeline nicht, es sei denn, seine `PassThru` Parameter angegeben ist.|
|`Resolve-Path`|Löst die Platzhalter für einen Windows PowerShell-Pfad und Datenströme Pfadinformationen.|
|`Test-Path`|Testet, die für den angegebenen Pfad und gibt `true` ggf. und `false` andernfalls. Dieses Cmdlet wird implementiert, zur Unterstützung der `IsContainer` -Parameter für die [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) Methode.|

### <a name="containercmdletprovider-base-class"></a>ContainerCmdletProvider-Basisklasse

Die [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) Klasse definiert einen Anbieter der Windows PowerShell-Container, die einen Container für Speicher Datenelemente, für den Benutzer verfügbar macht. Denken Sie daran, dass eine Windows PowerShell-Containeranbieter nur, wenn ein Container (keine geschachtelten Container) mit der Elemente verwendet werden kann. Wenn geschachtelte Container sind, müssen Sie eine Windows PowerShell-Navigationsanbieter implementieren.

Diese Klasse wird von der [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Basisklasse. In der folgende Tabelle definiert, die Cmdlets, die von dieser Klasse implementiert wird.

|Cmdlet|Definition|
|------------|----------------|
|`Copy-Item`|Kopiert die Elemente von einem Speicherort in einen anderen. Dieses Cmdlet aus, übergibt ein Ausgabeobjekt über die Pipeline nicht, es sei denn, seine `PassThru` Parameter angegeben ist.|
|`Get-Childitem`|Ruft die untergeordneten Elemente am angegebenen Speicherort ab und streamt sie als Objekte.|
|`New-Item`|Erstellt neue Elemente an der angegebenen Position und das resultierende Objekt streams.|
|`Remove-Item`|Entfernt Elemente aus der angegebenen Position.|
|`Rename-Item`|Benennt ein Element am angegebenen Speicherort. Dieses Cmdlet aus, übergibt ein Ausgabeobjekt über die Pipeline nicht, es sei denn, seine `PassThru` Parameter angegeben ist.|

### <a name="navigationcmdletprovider-base-class"></a>NavigationCmdletProvider-Basisklasse

Die [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) Klasse definiert einen Anbieter der Windows PowerShell-Navigation, die Vorgänge für Elemente, die mehr als ein Container verwenden. Diese Klasse wird von der [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) Basisklasse. Die folgende Tabelle listet die Cmdlets, die von dieser Klasse verfügbar gemacht werden.

|Cmdlet|Definition|
|------------|----------------|
|Combine-Pfad|Verknüpft zwei Pfade zu einem Pfad, mithilfe eines Trennzeichens anbieterspezifische zwischen Pfaden. Dieses Cmdlet streamt Zeichenfolgen.|
|`Move-Item`|Verschiebt Elemente in der angegebenen Position. Dieses Cmdlet aus, übergibt ein Ausgabeobjekt über die Pipeline nicht, es sei denn, seine `PassThru` Parameter angegeben ist.|

Eine zugehörige-Cmdlet wird die grundlegende Analyse-Path-Cmdlets, die zur Verfügung gestellt, von Windows PowerShell. Dieses Cmdlet kann verwendet werden, zum Analysieren von eines Windows PowerShell-Pfads zur Unterstützung der `Parent` Parameter. Die Zeichenfolge für den übergeordneten Pfad geleitet wird.

## <a name="select-provider-interfaces-to-support"></a>Wählen Sie die Anbieterschnittstellen an den Support

Zusätzlich zur Ableitung von einem Windows PowerShell-Basisklassen, kann Ihre Windows PowerShell-Anbieter andere Funktionen unterstützen, durch Ableiten von einer oder mehreren der folgenden anbieterschnittstellen. Dieser Abschnitt definiert die Schnittstellen und die Cmdlets, die unterstützt werden. Die Parameter für die Schnittstelle unterstützt Cmdlets wird nicht beschrieben. Cmdlet-Parameterinformationen finden Sie online mithilfe der `Get-Command` und `Get-Help` Cmdlets.

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

Die [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) Schnittstelle definiert einen Inhaltsanbieter, die Vorgänge für den Inhalt eines Datenelements ausführt. Die folgende Tabelle enthält die Cmdlets, die von dieser Schnittstelle verfügbar gemacht werden.

|Cmdlet|Definition|
|------------|----------------|
|`Add-Content`|Fügt die angegebenen Wert Längen auf den Inhalt des angegebenen Elements. Dieses Cmdlet aus, übergibt ein Ausgabeobjekt über die Pipeline nicht, es sei denn, seine `PassThru` Parameter angegeben ist.|
|`Clear-Content`|Legt den Inhalt des angegebenen Elements auf den Wert "clear" fest. Dieses Cmdlet aus, übergibt ein Ausgabeobjekt über die Pipeline nicht, es sei denn, seine `PassThru` Parameter angegeben ist.|
|`Get-Content`|Ruft den Inhalt der angegebenen Elemente ab und streamt die resultierenden Objekte.|
|`Set-Content`|Ersetzt den vorhandenen Inhalt für die angegebenen Elemente. Dieses Cmdlet aus, übergibt ein Ausgabeobjekt über die Pipeline nicht, es sei denn, seine `PassThru` Parameter angegeben ist.|

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

Die [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) Schnittstelle definiert ein Eigenschaftenanbieter für das Windows PowerShell, die Vorgänge für die Eigenschaften der Elemente im Datenspeicher ausführt. Die folgende Tabelle enthält die Cmdlets, die von dieser Schnittstelle verfügbar gemacht werden.

> [!NOTE]
> Die `Path` Parameter zu diesen Cmdlets gibt einen Pfad zu einem Element, anstatt eine Eigenschaft identifiziert.

|Cmdlet|Definition|
|------------|----------------|
|`Clear-ItemProperty`|Eigenschaften der angegebenen Elemente auf den Wert "clear" festgelegt. Dieses Cmdlet aus, übergibt ein Ausgabeobjekt über die Pipeline nicht, es sei denn, seine `PassThru` Parameter angegeben ist.|
|`Get-ItemProperty`|Ruft Eigenschaften aus den angegebenen Elementen ab und streamt die resultierenden Objekte.|
|`Set-ItemProperty`|Legt die Eigenschaften der angegebenen Elemente mit den angegebenen Werten. Dieses Cmdlet aus, übergibt ein Ausgabeobjekt über die Pipeline nicht, es sei denn, seine `PassThru` Parameter angegeben ist.|

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

Die [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) von abgeleitete Schnittstelle [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider), definiert ein Anbieter, der dynamische Parameter für die unterstützten Cmdlets angibt. Dieser Typ des Anbieters behandelt die Vorgänge, die für die Eigenschaften zur Laufzeit, z. B. eine neue Eigenschaft Operation definiert werden können. Solche Vorgänge sind nicht möglich, auf die Eigenschaften müssen statisch definierten Elemente. Die folgende Tabelle enthält die Cmdlets, die von dieser Schnittstelle verfügbar gemacht werden.

|Cmdlet|Definition|
|------------|----------------|
|`Copy-ItemProperty`|Kopiert eine Eigenschaft aus dem angegebenen Element in ein anderes Element an. Dieses Cmdlet aus, übergibt ein Ausgabeobjekt über die Pipeline nicht, es sei denn, seine `PassThru` Parameter angegeben ist.|
|`Move-ItemProperty`|Verschiebt eine Eigenschaft aus dem angegebenen Element in ein anderes Element. Dieses Cmdlet aus, übergibt ein Ausgabeobjekt über die Pipeline nicht, es sei denn, seine `PassThru` Parameter angegeben ist.|
|`New-ItemProperty`|Erstellt eine Eigenschaft für die angegebenen Elemente aus, und die resultierenden Objekte streamt.|
|`Remove-ItemProperty`|Entfernt eine Eigenschaft für die angegebenen Elemente.|
|`Rename-ItemProperty`|Benennt die Eigenschaft der angegebenen Elemente. Dieses Cmdlet aus, übergibt ein Ausgabeobjekt über die Pipeline nicht, es sei denn, seine `PassThru` Parameter angegeben ist.|

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

Die [System.Management.Automation.Provider.Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider) -Schnittstelle Deskriptor Sicherheitsfunktionen zu einem Anbieter. Diese Schnittstelle ermöglicht es den Benutzer zum Abrufen und Festlegen von Informationen der Sicherheitsbeschreibung für ein Element im Datenspeicher. Die folgende Tabelle enthält die Cmdlets, die von dieser Schnittstelle verfügbar gemacht werden.

|Cmdlet|Definition|
|------------|----------------|
|`Get-Acl`|Ruft ab, die Informationen in eine Zugriffssteuerungsliste (ACL), die Teil einer Sicherheitsbeschreibung, die Ressourcen des Betriebssystems, z. B. Schutz verwendet, eine Datei oder ein Objekt ist.|
|`Set-Acl`|Legt die Informationen für eine ACL fest. Es ist in Form von einer Instanz von [System.Security.Accesscontrol.Objectsecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity) auf die Elemente, die für den angegebenen Pfad festgelegt. Mit diesem Cmdlet kann Informationen zu Dateien, Schlüssel und Unterschlüssel in der Registrierung oder jedes andere Anbieter-Element, bei der Windows PowerShell-Anbieter die Einstellung der Sicherheitsinformationen unterstützt festlegen.|

## <a name="see-also"></a>Weitere Informationen

[Erstellen von Windows PowerShell-Anbieter](./how-to-create-a-windows-powershell-provider.md)

[Funktionsweise von Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)