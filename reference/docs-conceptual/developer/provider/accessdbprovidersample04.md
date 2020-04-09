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
ms.openlocfilehash: 0d3133c75d8e608967f15ffb7345fc0f63e1cd5c
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977504"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Dieses Beispiel zeigt, wie Sie Container Methoden überschreiben, um Aufrufe der Cmdlets `Copy-Item`, `Get-ChildItem`, `New-Item`und `Remove-Item` zu unterstützen. Diese Methoden sollten implementiert werden, wenn der Datenspeicher Elemente enthält, die Container sind. Ein Container ist eine Gruppe von untergeordneten Elementen unter einem gemeinsamen übergeordneten Element. Die Anbieter Klasse in diesem Beispiel wird von der [System. Management. Automation. Provider. containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) -Klasse abgeleitet.

## <a name="demonstrates"></a>Veranschaulicht

> [!IMPORTANT]
> Ihre Anbieter Klasse wird wahrscheinlich von [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) abgeleitet.

Dieses Beispiel zeigt die folgenden Vorgänge:

- Deklarieren des `CmdletProvider` Attributs.
- Definieren einer Anbieter Klasse, die von der [System. Management. Automation. Provider. containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) -Klasse abgeleitet wird.
- Überschreiben der [System. Management. Automation. Provider. containercmdletprovider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) -Methode, um das Verhalten des `Copy-Item`-Cmdlets zu ändern, das es dem Benutzer ermöglicht, Elemente von einem Speicherort in einen anderen zu kopieren. (In diesem Beispiel wird nicht gezeigt, wie dem `Copy-Item`-Cmdlet dynamische Parameter hinzugefügt werden.)
- Überschreiben der [System. Management. Automation. Provider. containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) -Methode, um das Verhalten des Cmdlets "Get-ChildItems" zu ändern, mit dem der Benutzer die untergeordneten Elemente des übergeordneten Elements abrufen kann. (Dieses Beispiel zeigt nicht, wie dem Cmdlet "Get-ChildItems" dynamische Parameter hinzugefügt werden.)
- Überschreiben der [System. Management. Automation. Provider. containercmdletprovider. getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) -Methode, um das Verhalten des Cmdlets Get-ChildItems zu ändern, wenn der `Name`-Parameter des Cmdlets angegeben wird.
- Überschreiben der [System. Management. Automation. Provider. containercmdletprovider. netwitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) -Methode, um das Verhalten des `New-Item`-Cmdlets zu ändern, das dem Benutzer das Hinzufügen von Elementen zum Datenspeicher ermöglicht. (In diesem Beispiel wird nicht gezeigt, wie dem `New-Item`-Cmdlet dynamische Parameter hinzugefügt werden.)
- Überschreiben der [System. Management. Automation. Provider. containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) -Methode, um das Verhalten des `Remove-Item`-Cmdlets zu ändern. (In diesem Beispiel wird nicht gezeigt, wie dem `Remove-Item`-Cmdlet dynamische Parameter hinzugefügt werden.)

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie Sie die Methoden überschreiben, die zum Kopieren, erstellen und Entfernen von Elementen erforderlich sind, sowie Methoden zum erhalten der untergeordneten Elemente eines übergeordneten Elements.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="11-1635":::

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. Provider. containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Entwerfen Ihres Windows PowerShell-Anbieters](./provider-types.md)
