---
title: Beispiele für Tabellenprofilanbieter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4933dad-fec9-4337-a1a9-9dc16ee87cc3
caps.latest.revision: 9
ms.openlocfilehash: 1e7aeb5bcb6bd5a2845648c3327e2245e6c428ba
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080933"
---
# <a name="provider-samples"></a>Anbieterbeispiele

Dieser Abschnitt enthält Beispiele von Anbietern, die den Zugriff auf eine Microsoft Access-Datenbank. Diese Beispiele enthalten Anbieterklassen, die von allen Basisanbieter Klassen abgeleitet werden.

## <a name="in-this-section"></a>In diesem Abschnitt

In diesem Abschnitt werden folgende Themen behandelt:

[AccessDBProviderSample01 Beispiel](./accessdbprovidersample01.md) dieses Beispiel zeigt, wie die Provider-Klasse zu deklarieren, die direkt von abgeleitet ist die [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) Klasse. Wird hier nur aus Gründen der Vollständigkeit aufgeführt.

[AccessDBProviderSample02](./accessdbprovidersample02.md) dieses Beispiel zeigt, wie die [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) und [ System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) Methoden zum Aufrufen von unterstützen die `New-PSDrive` und `Remove-PSDrive` Cmdlets. Die Anbieterklasse in diesem Beispiel ist abgeleitet von der [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Klasse.

[AccessDBProviderSample03](./accessdbprovidersample03.md) dieses Beispiel zeigt, wie die [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) und [ System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) Methoden zum Aufrufen von unterstützen die `Get-Item` und `Set-Item` Cmdlets. Die Anbieterklasse in diesem Beispiel ist abgeleitet von der [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse.

[AccessDBProviderSample04](./accessdbprovidersample04.md) dieses Beispiel zeigt, wie containermethoden um Aufrufe unterstützen die `Copy-Item`, `Get-ChildItem`, `New-Item`, und `Remove-Item` Cmdlets. Diese Methoden sollten implementiert werden, wenn der Datenspeicher Elemente enthält, die Container sind. Ein Container ist eine Gruppe von untergeordneten Elementen unter einem gemeinsamen übergeordneten Element. Die Anbieterklasse in diesem Beispiel ist abgeleitet von der [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) Klasse.

[AccessDBProviderSample05](./accessdbprovidersample05.md) dieses Beispiel zeigt, wie containermethoden um Aufrufe unterstützen die `Move-Item` und `Join-Path` Cmdlets. Diese Methoden sollten implementiert werden, wenn der Benutzer Elemente innerhalb eines Containers verschieben muss, und wenn der Datenspeicher geschachtelte Container enthält. Die Anbieterklasse in diesem Beispiel ist abgeleitet von der [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) Klasse.

[AccessDBProviderSample06](./accessdbprovidersample06.md) dieses Beispiel zeigt, wie inhaltsmethoden um Aufrufe unterstützen die `Clear-Content`, `Get-Content`, und `Set-Content` Cmdlets. Diese Methoden sollten implementiert werden, wenn der Benutzer den Inhalt der Elemente im Datenspeicher verwaltet muss. Die Anbieterklasse in diesem Beispiel ist abgeleitet von der [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse und implementiert die [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) Schnittstelle.

## <a name="see-also"></a>Weitere Informationen

[Schreiben Sie ein Windows PowerShell-Anbieter](./writing-a-windows-powershell-provider.md)