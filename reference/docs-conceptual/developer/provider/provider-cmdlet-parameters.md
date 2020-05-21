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
ms.openlocfilehash: 8ce13032a55d164121a073ef94086dc1de09b902
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564205"
---
# <a name="provider-cmdlet-parameters"></a>Anbieter-Cmdlet-Parameter

Anbieter-Cmdlets verfügen über einen Satz statischer Parameter, die für alle Anbieter verfügbar sind, die das Cmdlet unterstützen, sowie dynamische Parameter, die hinzugefügt werden, wenn der Benutzer einen bestimmten Wert für bestimmte statische Parameter des Provider-Cmdlets angibt.

## <a name="provider-cmdlet-static-parameters"></a>Statische Cmdlet-Parameter des Anbieters

Statische Parameter werden von Windows PowerShell definiert. Eine große Menge dieser Parameter wird von Windows PowerShell implementiert, um Konsistenz für alle Anbieter bereitzustellen und eine einfachere Entwicklungsfunktion bereitzustellen. Beispiele für diese Parameter sind der `literalPath` `exclude` -Parameter, der-Parameter und der- `include` Parameter des `Get-Item` Cmdlets. Ein kleinerer Satz dieser Parameter kann überschrieben werden, um Aktionen bereitzustellen, die für Ihren Anbieter spezifisch sind. Beispiele für diese Parameter sind der `Path` -Parameter und der- `Value` Parameter des `Set-Item` Cmdlets. Im folgenden finden Sie eine Liste der Parameter, die für die Anbieter-Cmdlets überschrieben werden können.

`Clear-Content`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an den- `Path` Parameter des `Clear-Content` Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) -Methode implementieren.

`Clear-Item`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an den- `Path` Parameter des `Clear-Item` Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. itemcmdletprovider. ClearItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) -Methode implementieren.

`Clear-ItemProperty`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an den `Path` -Parameter und den- `Name` Parameter des `Clear-ItemProperty` Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. ipropertycmdletprovider. clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) -Methode implementieren.

`Copy-Item`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an die `Path` `Destination` Parameter, und `Recurse` des `Copy-Item` Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. containercmdletprovider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) -Methode implementieren.

Cmdlet "Get-ChildItems" können Sie definieren, wie der Anbieter die Werte verwendet, die an den `Path` -Parameter und den- `Recurse` Parameter des `Get-ChildItem` Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) -und [System. Management. Automation. Provider. containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

`Get-Content`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an den- `Path` Parameter des `Get-Content` Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. icontentcmdletprovider. getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) -Methode implementieren.

`Get-Item`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an den- `Path` Parameter des `Get-Item` Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) -Methode implementieren.

`Get-ItemProperty`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an den `Path` -Parameter und den- `Name` Parameter des `Get-ItemProperty` Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) -Methode implementieren.

`Invoke-Item`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an den- `Path` Parameter des `Invoke-Item` Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. itemcmdletprovider. invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) -Methode implementieren.

`Move-Item`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an den `Path` -Parameter und den- `Destination` Parameter des `Move-Item` Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. navigationcmdletprovider. muveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) -Methode implementieren.

`New-Item`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an die `Path` `ItemType` Parameter, und `Value` des `New-Item` Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. containercmdletprovider. netwitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) -Methode implementieren.

`New-ItemProperty`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an die `Path` `Name` Parameter,, `PropertyType` und `Value` des `New-ItemProperty` Cmdlets übergeben werden, indem Sie die [Microsoft. PowerShell. Commands. registryprovider. newproperty *](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) -Methode implementieren.

`Remove-Item`Sie können definieren, wie der Anbieter die Werte verwendet, die an den `Path` -Parameter und den- `Recurse` Parameter des `Remove-Item` Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) -Methode implementieren.

`Remove-ItemProperty`Sie können definieren, wie der Anbieter die Werte verwendet, die an den `Path` -Parameter und den- `Name` Parameter des `Remove-ItemProperty` Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. idynamicpropertycmdletprovider. RemoveProperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) -Methode implementieren.

`Rename-Item`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an den `Path` -Parameter und den- `NewName` Parameter des `Rename-Item` Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) -Methode implementieren.

`Rename-ItemProperty`Sie können definieren, wie der Anbieter die Werte verwendet, die an `Path` die `NewName` Parameter, und `Name` des `Rename-ItemProperty` Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. idynamicpropertycmdletprovider. renameproperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) -Methode implementieren.

`Set-Content`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an den- `Path` Parameter des `Set-Content` Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. icontentcmdletprovider. getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) -Methode implementieren.

`Set-Item`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an den `Path` -Parameter und den- `Value` Parameter des `Set-Item` Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) -Methode implementieren.

`Set-ItemProperty`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an den `Path` -Parameter und den- `Value` Parameter des `Set-Item` Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) -Methode implementieren.

`Test-Path`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an den- `Path` Parameter des `Test-Path` Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. itemcmdletprovider. invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) -Methode implementieren.

Außerdem können Sie die Merkmale dieser Parameter nicht angeben, z. b. ob Sie optional oder erforderlich sind, und Sie können diesen Parametern auch keinen Alias geben oder die Validierungs Attribute angeben. Im Gegensatz dazu können Sie Parameter Merkmale in eigenständigen Cmdlets mithilfe von Attributen wie dem-Attribut angeben `Parameters` .

## <a name="provider-cmdlet-dynamic-parameters"></a>Dynamische Parameter des Anbieter-Cmdlets

Dynamische Parameter für Cmdlet-Anbieter ähneln dynamischen Anbietern für eigenständige Cmdlets. In beiden Fällen werden die Parameter zum Cmdlet hinzugefügt, wenn der Benutzer einen bestimmten Wert für einen der Standardparameter angibt, z. b. den- `path` Parameter. Es können jedoch nicht alle statischen Parameter verwendet werden, um das Hinzufügen dynamischer Parameter zu initiieren. Weitere Informationen zu dynamischen Parametern finden [Sie unter Anbieter-Cmdlet-Parameter](./provider-cmdlet-dynamic-parameters.md).

## <a name="see-also"></a>Weitere Informationen

[Dynamische Parameter des Anbieter-Cmdlets](./provider-cmdlet-dynamic-parameters.md)

[Schreiben eines Windows PowerShell-Anbieters](./writing-a-windows-powershell-provider.md)
