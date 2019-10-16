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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366309"
---
# <a name="provider-cmdlet-parameters"></a>Anbieter-Cmdlet-Parameter

Anbieter-Cmdlets verfügen über einen Satz statischer Parameter, die für alle Anbieter verfügbar sind, die das Cmdlet unterstützen, sowie dynamische Parameter, die hinzugefügt werden, wenn der Benutzer einen bestimmten Wert für bestimmte statische Parameter des Provider-Cmdlets angibt.

## <a name="provider-cmdlet-static-parameters"></a>Statische Cmdlet-Parameter des Anbieters

Statische Parameter werden von Windows PowerShell definiert. Eine große Menge dieser Parameter wird von Windows PowerShell implementiert, um Konsistenz für alle Anbieter bereitzustellen und eine einfachere Entwicklungsfunktion bereitzustellen. Beispiele für diese Parameter sind die Parameter "`literalPath`", "`exclude`" und "`include`" des `Get-Item`-Cmdlets. Ein kleinerer Satz dieser Parameter kann überschrieben werden, um Aktionen bereitzustellen, die für Ihren Anbieter spezifisch sind. Beispiele für diese Parameter sind der `Path`-und `Value`-Parameter des Cmdlets `Set-Item`. Im folgenden finden Sie eine Liste der Parameter, die für die Anbieter-Cmdlets überschrieben werden können.

`Clear-Content`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an den `Path`-Parameter des `Clear-Content`-Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) -Methode implementieren.

mit dem Cmdlet "`Clear-Item`" können Sie definieren, wie der Anbieter die Werte verwendet, die an den `Path`-Parameter des Cmdlets "`Clear-Item`" übergeben werden, indem Sie die [System. Management. Automation. Provider. itemcmdletprovider. ClearItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) -Methode implementieren.

mit dem Cmdlet "`Clear-ItemProperty`" können Sie definieren, wie der Anbieter die Werte verwendet, die an die Parameter "`Path`" und "`Name`" des `Clear-ItemProperty`-Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. ipropertycmdletprovider. clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) -Methode implementieren.

`Copy-Item`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an die Parameter "`Path`", "`Destination`" und "`Recurse`" des `Copy-Item`-Cmdlets übergeben werden, indem Sie " [System. Management. Automation. Provider. containercmdletprovider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) " implementieren. anzuwenden.

Cmdlet "Get-ChildItems" können Sie definieren, wie der Anbieter die Werte verwendet, die an die Parameter "`Path`" und "`Recurse`" des `Get-ChildItem`-Cmdlets übergeben werden, indem Sie " [System. Management. Automation. Provider. containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) " implementieren. und [System. Management. Automation. Provider. containercmdletprovider. getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) -Methoden.

`Get-Content`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an den `Path`-Parameter des `Get-Content`-Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. icontentcmdletprovider. getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) -Methode implementieren.

mit dem Cmdlet "`Get-Item`" können Sie definieren, wie der Anbieter die Werte verwendet, die an den `Path`-Parameter des Cmdlets "`Get-Item`" übergeben werden, indem Sie die [System. Management. Automation. Provider. itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) -Methode implementieren.

mit dem Cmdlet "`Get-ItemProperty`" können Sie definieren, wie der Anbieter die Werte verwendet, die an die Parameter "`Path`" und "`Name`" des `Get-ItemProperty`-Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) -Methode implementieren.

`Invoke-Item`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an den `Path`-Parameter des `Invoke-Item`-Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. itemcmdletprovider. invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) -Methode implementieren.

mit dem Cmdlet "`Move-Item`" können Sie definieren, wie der Anbieter die Werte verwendet, die an die Parameter "`Path`" und "`Destination`" des `Move-Item`-Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. navigationcmdletprovider. muveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) -Methode implementieren.

`New-Item`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an die Parameter "`Path`", "`ItemType`" und "`Value`" des `New-Item`-Cmdlets übergeben werden, indem Sie " [System. Management. Automation. Provider. containercmdletprovider. nwitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) " implementieren. anzuwenden.

`New-ItemProperty`-Cmdlet Sie können definieren, wie der Anbieter die Werte verwendet, die an die Parameter "`Path`", "`Name`", "`PropertyType`" und "`Value`" des `New-ItemProperty`-Cmdlets übergeben werden, indem [Microsoft. PowerShell. Commands. registryprovider. newproperty *](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) implementiert wird. anzuwenden.

`Remove-Item` Sie können definieren, wie der Anbieter die Werte verwendet, die an die Parameter "`Path`" und "`Recurse`" des `Remove-Item`-Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) -Methode implementieren.

`Remove-ItemProperty` Sie können definieren, wie der Anbieter die Werte verwendet, die an die Parameter "`Path`" und "`Name`" des `Remove-ItemProperty`-Cmdlets übergeben werden, indem Sie " [System. Management. Automation. Provider. idynamicpropertycmdletprovider. RemoveProperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) " implementieren. anzuwenden.

mit dem Cmdlet "`Rename-Item`" können Sie definieren, wie der Anbieter die Werte verwendet, die an die Parameter "`Path`" und "`NewName`" des `Rename-Item`-Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) -Methode implementieren.

`Rename-ItemProperty` Sie können definieren, wie der Anbieter die Werte verwendet, die an die Parameter `Path`, `NewName` und `Name` des `Rename-ItemProperty`-Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. idynamicpropertycmdletprovider. renameproperty * implementieren. ](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)-Methode.

mit dem Cmdlet "`Set-Content`" können Sie definieren, wie der Anbieter die Werte verwendet, die an den `Path`-Parameter des Cmdlets "`Set-Content`" übergeben werden, indem Sie die [System. Management. Automation. Provider. icontentcmdletprovider. getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) -Methode implementieren.

mit dem Cmdlet "`Set-Item`" können Sie definieren, wie der Anbieter die Werte verwendet, die an die Parameter "`Path`" und "`Value`" des `Set-Item`-Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) -Methode implementieren.

mit dem Cmdlet "`Set-ItemProperty`" können Sie definieren, wie der Anbieter die Werte verwendet, die an die Parameter "`Path`" und "`Value`" des `Set-Item`-Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) -Methode implementieren.

`Test-Path`-Cmdlet können Sie definieren, wie der Anbieter die Werte verwendet, die an den `Path`-Parameter des `Test-Path`-Cmdlets übergeben werden, indem Sie die [System. Management. Automation. Provider. itemcmdletprovider. invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) -Methode implementieren.

Außerdem können Sie die Merkmale dieser Parameter nicht angeben, z. b. ob Sie optional oder erforderlich sind, und Sie können diesen Parametern auch keinen Alias geben oder die Validierungs Attribute angeben. Im Gegensatz dazu können Sie Parameter Merkmale in eigenständigen Cmdlets mithilfe von Attributen wie dem `Parameters`-Attribut angeben.

## <a name="provider-cmdlet-dynamic-parameters"></a>Dynamische Parameter des Anbieter-Cmdlets

Dynamische Parameter für Cmdlet-Anbieter ähneln dynamischen Anbietern für eigenständige Cmdlets. In beiden Fällen werden die Parameter zum Cmdlet hinzugefügt, wenn der Benutzer einen bestimmten Wert für einen der Standardparameter angibt, z. b. den `path`-Parameter. Es können jedoch nicht alle statischen Parameter verwendet werden, um das Hinzufügen dynamischer Parameter zu initiieren. Weitere Informationen zu dynamischen Parametern finden [Sie unter Anbieter-Cmdlet-Parameter](./provider-cmdlet-dynamic-parameters.md).

## <a name="see-also"></a>Weitere Informationen

[Dynamische Parameter des Anbieter-Cmdlets](./provider-cmdlet-dynamic-parameters.md)

[Schreiben eines Windows PowerShell-Anbieters](./writing-a-windows-powershell-provider.md)