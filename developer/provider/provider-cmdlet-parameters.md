---
title: Anbieter-Cmdlet-Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d09eaa-924f-4e2b-adfb-14bb729090dd
caps.latest.revision: 8
ms.openlocfilehash: ad7f9737c646dd5cea5abb14b828236e40feac5a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057041"
---
# <a name="provider-cmdlet-parameters"></a>Anbieter-Cmdlet-Parameter

Anbieter-Cmdlets verfügen über einen Satz von statischen Parametern, die für alle Anbieter verfügbar sind, die vom Cmdlet unterstützt, auch als dynamische Parameter, die hinzugefügt werden, wenn der Benutzer einen bestimmten Wert für die bestimmte statische Parameter des Cmdlets, Anbieter angibt.

## <a name="provider-cmdlet-static-parameters"></a>Anbieter-Cmdlet-Static-Parameter

Statische Parameter werden von Windows PowerShell definiert. Eine große Anzahl dieser Parameter wird von Windows PowerShell, um Konsistenz für alle Anbieter bereitzustellen und eine einfachere Entwicklungsumgebung bereitzustellen implementiert. Beispiele für diese Parameter sind die `literalPath`, `exclude`, und `include` Parameter von der `Get-Item` Cmdlet. Eine kleinere Gruppe von diesen Parametern kann überschrieben werden, um Aktionen zu ermöglichen, die an Ihren Anbieter spezifisch sind. Beispiele für diese Parameter sind die `Path` und `Value` Parameter, der die `Set-Item` Cmdlet. Hier ist eine Liste der Parameter, die für die Anbieter-Cmdlets überschrieben werden kann.

`Clear-Content` Cmdlets können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path` Parameter der `Clear-Content` Cmdlet, durch die Implementierung der [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)Methode.

`Clear-Item` Cmdlets können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path` Parameter der `Clear-Item` Cmdlet, durch die Implementierung der [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) -Methode.

`Clear-ItemProperty` Cmdlets können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path` und `Name` Parameter der `Clear-ItemProperty` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) Methode.

`Copy-Item` Cmdlets können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path`, `Destination`, und `Recurse` Parameter der `Copy-Item` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) Methode.

Get-ChildItems-Cmdlet können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path` und `Recurse` Parameter von der `Get-ChildItem` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) und [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) Methoden.

`Get-Content` Cmdlets können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path` Parameter der `Get-Content` Cmdlet, durch die Implementierung der [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) Methode.

`Get-Item` Cmdlets können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path` Parameter der `Get-Item` Cmdlet, durch die Implementierung der [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) Methode.

`Get-ItemProperty` Cmdlets können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path` und `Name` Parameter der `Get-ItemProperty` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) Methode.

`Invoke-Item` Cmdlets können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path` Parameter der `Invoke-Item` Cmdlet, durch die Implementierung der [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)Methode.

`Move-Item` Cmdlets können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path` und `Destination` Parameter der `Move-Item` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) Methode.

`New-Item` Cmdlets können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path`, `ItemType`, und `Value` Parameter der `New-Item` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) Methode.

`New-ItemProperty` Cmdlets können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path`, `Name`, `PropertyType`, und `Value` Parameter der `New-ItemProperty` Cmdlet, durch die Implementierung der [ Microsoft.PowerShell.Commands.Registryprovider.Newproperty*](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) Methode.

`Remove-Item` Können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path` und `Recurse` Parameter von der `Remove-Item` Cmdlet, durch die Implementierung der [System.Management.Automation.Provider.Containercmdletprovider.Removeitem* ](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) Methode.

`Remove-ItemProperty` Können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path` und `Name` Parameter von der `Remove-ItemProperty` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) Methode.

`Rename-Item` Cmdlets können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path` und `NewName` Parameter der `Rename-Item` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) Methode.

`Rename-ItemProperty` Können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path`, `NewName`, und `Name` Parameter von der `Rename-ItemProperty` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) Methode.

`Set-Content` Cmdlets können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path` Parameter der `Set-Content` Cmdlet, durch die Implementierung der [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) Methode.

`Set-Item` Cmdlets können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path` und `Value` Parameter der `Set-Item` Cmdlet, durch die Implementierung der [System.Management.Automation.Provider.Itemcmdletprovider.Setitem* ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) Methode.

`Set-ItemProperty` Cmdlets können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path` und `Value` Parameter der `Set-Item` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) Methode.

`Test-Path` Cmdlets können Sie definieren, wie die Werte, die an der Anbieter verwenden, wird die `Path` Parameter der `Test-Path` Cmdlet, durch die Implementierung der [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)Methode.

Darüber hinaus Sie nicht angeben, die Merkmale dieser Parameter ein, z. B., ob sie optional oder erforderlich sind, noch können Sie diese Parameter geben Sie einen Alias oder geben Sie eine der Validierungsattribute. Sie können im Gegensatz dazu Parametereigenschaften in eigenständigen-Cmdlets angeben, wie z. B. mithilfe von Attributen der `Parameters` Attribut.

## <a name="provider-cmdlet-dynamic-parameters"></a>Anbieter-Cmdlet dynamische Parameter

Dynamische Parameter für Cmdlet-Anbieter sind ähnlich, dynamische-Anbieter für eigenständige-Cmdlets. In beiden Fällen werden die Parameter an das Cmdlet hinzugefügt, wenn der Benutzer einen bestimmten Wert für die Standardparameter eines, wie z. B. angibt die `path` Parameter. Nicht alle die statischen Parameter kann jedoch verwendet werden, um das Hinzufügen von dynamischen Parametern auszulösen. Weitere Informationen zu dynamischen Parametern finden Sie unter [Anbieter-Cmdlet dynamische Parameter](./provider-cmdlet-dynamic-parameters.md).

## <a name="see-also"></a>Weitere Informationen

[Anbieter-Cmdlet dynamische Parameter](./provider-cmdlet-dynamic-parameters.md)

[Schreiben Sie ein Windows PowerShell-Anbieter](./writing-a-windows-powershell-provider.md)