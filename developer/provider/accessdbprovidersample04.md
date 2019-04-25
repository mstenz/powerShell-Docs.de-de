---
title: AccessDBProviderSample04 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: d9109e8d5b69a25ad52b90bcaff9628b01067211
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081020"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Dieses Beispiel zeigt, wie containermethoden um Aufrufe unterstützen die `Copy-Item`, `Get-ChildItem`, `New-Item`, und `Remove-Item` Cmdlets. Diese Methoden sollten implementiert werden, wenn der Datenspeicher Elemente enthält, die Container sind. Ein Container ist eine Gruppe von untergeordneten Elementen unter einem gemeinsamen übergeordneten Element. Die Anbieterklasse in diesem Beispiel ist abgeleitet von der [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) Klasse.

## <a name="demonstrates"></a>Zeigt

> [!IMPORTANT]
> Die Anbieterklasse in den meisten Fällen von abgeleitet der [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

Dieses Beispiel zeigt Folgendes:

- Deklarieren der `CmdletProvider` Attribut.

- Definieren eine abgeleitete Anbieterklasse die [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) Klasse.

- Überschreiben der [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) Methode zum Ändern des Verhaltens von der `Copy-Item` Cmdlet, das dem Benutzer ermöglicht, Elemente aus einem Speicherort in einen anderen zu kopieren. (Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `Copy-Item` Cmdlet.)

- Überschreiben der [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) Methode, um das Verhalten des Cmdlets Get-ChildItems ändern, in denen dem Benutzer ermöglicht, die die untergeordneten Elemente des übergeordneten Elements abrufen. . (Dieses Beispiel zeigt keine dynamischen Parameter an das Cmdlet Get-ChildItems hinzufügen.)

- Überschreiben der [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) Methode, um das Verhalten des Cmdlets Get-ChildItems ändern bei der `Name` -Parameter des Cmdlets angegeben ist.

- Überschreiben der [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) Methode zum Ändern des Verhaltens von der `New-Item` -Cmdlet, das dem Benutzer ermöglicht, Elemente mit dem Datenspeicher hinzuzufügen. (Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `New-Item` Cmdlet.)

- Überschreiben der [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) Methode zum Ändern des Verhaltens von der `Remove-Item` Cmdlet. (Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `Remove-Item` Cmdlet.)

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie die Methoden zum Kopieren, erstellen und Entfernen von Elementen sowie Methoden zum Abrufen der untergeordneten Elemente eines übergeordneten Elements benötigt.

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Entwerfen Ihre Windows PowerShell-Anbieter](./provider-types.md)