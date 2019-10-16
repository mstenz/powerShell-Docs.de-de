---
title: Anbieter Beispiele | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4933dad-fec9-4337-a1a9-9dc16ee87cc3
caps.latest.revision: 9
ms.openlocfilehash: 1e7aeb5bcb6bd5a2845648c3327e2245e6c428ba
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366299"
---
# <a name="provider-samples"></a>Anbieterbeispiele

Dieser Abschnitt enthält Beispiele von Anbietern, die auf eine Microsoft Access-Datenbank zugreifen. Diese Beispiele enthalten Anbieter Klassen, die von allen Basis Anbieter Klassen abgeleitet werden.

## <a name="in-this-section"></a>In diesem Abschnitt

In diesem Abschnitt werden folgende Themen behandelt:

[AccessDBProviderSample01-Beispiel](./accessdbprovidersample01.md) Dieses Beispiel zeigt, wie Sie die Anbieter Klasse deklarieren, die direkt von der [System. Management. Automation. Provider. cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) -Klasse abgeleitet wird. Wird hier nur aus Gründen der Vollständigkeit aufgeführt.

[AccessDBProviderSample02](./accessdbprovidersample02.md) In diesem Beispiel wird gezeigt, wie die Methoden [System. Management. Automation. Provider. drivecmdletprovider. newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) und [System. Management. Automation. Provider. drivecmdletprovider. removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) überschrieben werden, um Aufrufe des `New-PSDrive` zu unterstützen. und `Remove-PSDrive`-Cmdlets. Die Anbieter Klasse in diesem Beispiel wird von der [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Klasse abgeleitet.

[AccessDBProviderSample03](./accessdbprovidersample03.md) In diesem Beispiel wird gezeigt, wie die Methoden [System. Management. Automation. Provider. itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) und [System. Management. Automation. Provider. itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) überschrieben werden, um Aufrufe der `Get-Item` und @no__ zu unterstützen. t-4-Cmdlets. Die Anbieter Klasse in diesem Beispiel wird von der [System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Klasse abgeleitet.

[AccessDBProviderSample04](./accessdbprovidersample04.md) Dieses Beispiel zeigt, wie Sie Container Methoden überschreiben, um Aufrufe der Cmdlets "`Copy-Item`", "`Get-ChildItem`", "`New-Item`" und "`Remove-Item`" zu unterstützen. Diese Methoden sollten implementiert werden, wenn der Datenspeicher Elemente enthält, die Container sind. Ein Container ist eine Gruppe von untergeordneten Elementen unter einem gemeinsamen übergeordneten Element. Die Anbieter Klasse in diesem Beispiel wird von der [System. Management. Automation. Provider. containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) -Klasse abgeleitet.

[AccessDBProviderSample05](./accessdbprovidersample05.md) Dieses Beispiel zeigt, wie Sie Container Methoden überschreiben, um Aufrufe der Cmdlets `Move-Item` und `Join-Path` zu unterstützen. Diese Methoden sollten implementiert werden, wenn der Benutzer Elemente innerhalb eines Containers verschieben muss, und wenn der Datenspeicher geschachtelte Container enthält. Die Anbieter Klasse in diesem Beispiel wird von der [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse abgeleitet.

[AccessDBProviderSample06](./accessdbprovidersample06.md) In diesem Beispiel wird gezeigt, wie Inhalts Methoden überschrieben werden, um Aufrufe der Cmdlets `Clear-Content`, `Get-Content` und `Set-Content` zu unterstützen. Diese Methoden sollten implementiert werden, wenn der Benutzer den Inhalt der Elemente im Datenspeicher verwaltet muss. Die Anbieter Klasse in diesem Beispiel wird von der [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse abgeleitet und implementiert die [System. Management. Automation. Provider. icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) -Schnittstelle.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Anbieters](./writing-a-windows-powershell-provider.md)