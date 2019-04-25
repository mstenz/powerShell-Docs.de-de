---
title: Anbieter-Cmdlets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2465420-0970-4408-9ee5-260cf444cb67
caps.latest.revision: 8
ms.openlocfilehash: e6a0711cff6a550100f584fb64ae7f59f71a3cfb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080950"
---
# <a name="provider-cmdlets"></a>Anbieter-Cmdlets

Die Cmdlets, die der Benutzer ausführen kann, um einen Datenspeicher verwaltet werden als Anbieter-Cmdlets bezeichnet. Um diese Cmdlets unterstützen zu können, müssen Sie einige der Methoden definiert, die vom Basisanbieter Klassen und Schnittstellen zu überschreiben.

## <a name="provider-cmdlets"></a>Anbieter-Cmdlets

Hier sind die Anbieter-Cmdlets, die vom Benutzer ausgeführt werden können:

### <a name="psdrive-cmdlets"></a>PSDrive-cmdlets

- `Get-PSDrive`: Dieses Cmdlet gibt zurück, dass die Windows PowerShell-Laufwerke in der aktuellen Sitzung. Sie müssen keine Methoden zur Unterstützung der mit diesem Cmdlet überschreiben.

- `New-PSDrive`: Mit diesem Cmdlet können den Benutzer, Windows PowerShell-Laufwerke, auf den Datenspeicher zu erstellen. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) und [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) Methoden.

- `Remove-PSDrive`: Mit diesem Cmdlet können Benutzern, Windows PowerShell-Laufwerke zu entfernen, die auf den Datenspeicher zugreifen. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) Methode.

### <a name="item-cmdlets"></a>Item-cmdlets

- `Clear-Item`: Mit diesem Cmdlet können den Benutzer den Wert eines Elements im Datenspeicher zu entfernen. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) und [ System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) Methoden.

- `Copy-Item`: Mit diesem Cmdlet können den Benutzer ein Element von einem Speicherort in einen anderen zu kopieren. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Containercmdletprovider.Copyitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) und [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) Methoden.

- `Get-Item`: Mit diesem Cmdlet können Benutzer Daten aus dem Datenspeicher abrufen. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Itemcmdletprovider.Getitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) und [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) Methoden.

- `Get-ChildItem`: Mit diesem Cmdlet können Benutzer die untergeordneten Elemente des übergeordneten Elements abrufen. Um dieses Cmdlet aus, zu unterstützen, überschreiben Sie die folgenden Methoden:

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`: Mit diesem Cmdlet können den Benutzer zum Ausführen der Standardaktion, die durch das Element angegeben. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) und [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) Methoden.

- `Move-Item`: Mit diesem Cmdlet können den Benutzer ein Element von einem Speicherort an einen anderen Speicherort zu verschieben. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) und [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)s-Methoden.

- `New-ItemProperty`: Mit diesem Cmdlet können den Benutzer zum Erstellen eines neuen Elements im Datenspeicher.

- `Remove-Item`: Mit diesem Cmdlet können Elemente aus dem Datenspeicher entfernt. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Containercmdletprovider.Removeitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) und [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) Methoden.

- `Rename-Item`: Mit diesem Cmdlet können den Benutzer, die Elemente im Datenspeicher umbenannt werden. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Containercmdletprovider.Renameitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) und [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) Methoden.

- `Set-Item`: Mit diesem Cmdlet können den Benutzer zum Aktualisieren der Werte der Elemente im Datenspeicher. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Itemcmdletprovider.Setitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) und [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) Methoden.

### <a name="item-content-cmdlets"></a>Content-Item-cmdlets

- `Add-Content`: Mit diesem Cmdlet können den Benutzer auf Inhalte für ein Element hinzuzufügen.

- `Clear-Content`: Mit diesem Cmdlet können Benutzer Inhalt aus einem Element zu löschen, ohne das Element zu löschen. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) und [ System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) Methoden.

- `Get-Content`: Mit diesem Cmdlet können Benutzer den Inhalt eines Elements abrufen. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) und [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) Methoden. Die [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) Methode gibt ein [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) Schnittstelle, die definiert die Methoden verwendet, um den Inhalt zu lesen.

- `Set-Content`: Mit diesem Cmdlet können Benutzer den Inhalt eines Elements zu aktualisieren. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) und [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) Methoden. Die [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) Methode gibt ein [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) Schnittstelle, die definiert die Methoden zum Schreiben des Inhalts verwendet wird.

### <a name="item-property-cmdlets"></a>Item-Eigenschaft-cmdlets

- `Clear-ItemProperty`: Mit diesem Cmdlet können Benutzer den Wert einer Eigenschaft zu löschen. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) und [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) Methoden.

- `Copy-ItemProperty`: Mit diesem Cmdlet können den Benutzer auf eine Eigenschaft und der Wert von einem Speicherort in einen anderen zu kopieren. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) und [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) Methoden.

- `Get-ItemProperty`: Dieses Cmdlet Ruft die Eigenschaften eines Elements ab. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) und [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) Methoden.

- `Move-ItemProperty`: Mit diesem Cmdlet können den Benutzer eine Eigenschaft und der Wert von einem Speicherort an einen anderen verschiebt. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) und [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) Methoden.

- `New-ItemProperty`: Dieses Cmdlet ermöglicht den Benutzer eine neue Eigenschaft erstellen, und legen Sie dessen Wert an. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) und [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) Methoden.

- `Remove-ItemProperty`: Mit diesem Cmdlet können Benutzer eine Eigenschaft und den Wert zu löschen. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) und [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) Methoden.

- `Rename-ItemProperty`: Mit diesem Cmdlet können den Benutzer, den Namen einer Eigenschaft zu ändern. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) und [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) Methoden.

- `Set-ItemProperty`: Mit diesem Cmdlet können den Benutzer zum Aktualisieren der Eigenschaften eines Elements. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) und [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) Methoden.

### <a name="location-cmdlets"></a>Location-cmdlets

- `Get-Location`: Ruft Informationen zu den aktuellen arbeitsspeicherort ab. Sie müssen keine Methoden zur Unterstützung der mit diesem Cmdlet überschreiben.

- `Pop-Location`: Dieses Cmdlet ändert den aktuellen Speicherort auf den Speicherort, der die zuletzt auf dem Stapel abgelegt. Sie müssen keine Methoden zur Unterstützung der mit diesem Cmdlet überschreiben.

- `Push-Location`: Dieses Cmdlet fügt die aktuelle Position am Anfang einer Liste von Speicherorten (einen "Stapel"). Sie müssen keine Methoden zur Unterstützung der mit diesem Cmdlet überschreiben.

- `Set-Location`: Dieses Cmdlet legt den aktuellen arbeitsspeicherort auf einer angegebenen Position fest. Sie müssen keine Methoden zur Unterstützung der mit diesem Cmdlet überschreiben.

### <a name="path-cmdlets"></a>Pfad-cmdlets

- `Join-Path`: Mit diesem Cmdlet können den Benutzer auf einem übergeordneten und untergeordneten Pfadsegment zum Erstellen eines internen Anbieter-Pfads zu kombinieren. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) Methode.

- `Convert-Path`: Dieses Cmdlet konvertiert einen Pfad aus einem Windows PowerShell-Pfad in einen Windows PowerShell-anbieterpfad.

- `Split-Path`: Gibt den angegebenen Teil eines Pfads zurück.

- `Resolve-Path`: Löst die Platzhalterzeichen in einem Pfad auf und zeigt den Inhalt des Pfads an.

- `Test-Path`: Dieses Cmdlet bestimmt, ob alle Elemente eines Pfads vorhanden sind. Um dieses Cmdlet aus, zu unterstützen, überschreiben die [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) und [ System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) Methoden.

### <a name="psprovider-cmdlets"></a>PSProvider-cmdlets

- `Get-PSProvider`: Dieses Cmdlet gibt Informationen über die in der Sitzung verfügbaren Anbieter zurück. Sie müssen keine Methoden zur Unterstützung der mit diesem Cmdlet überschreiben.