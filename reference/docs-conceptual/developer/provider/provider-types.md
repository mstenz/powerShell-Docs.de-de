---
title: Anbieter Typen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 0a9bfe5dd0978ffce66db1b18ef4d82be6c1a7f2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359959"
---
# <a name="provider-types"></a>Anbietertypen

Anbieter definieren ihre grundlegende Funktionalität durch Ändern der Art und Weise, wie die von PowerShell bereitgestellten Anbieter-Cmdlets ihre Aktionen ausführen. Beispielsweise können Anbieter die Standardfunktionalität des `Get-Item`-Cmdlets verwenden, oder Sie können die Funktionsweise dieses Cmdlets ändern, wenn Elemente aus dem Datenspeicher abgerufen werden. Die in diesem Dokument beschriebene Funktionalität des Anbieters umfasst Funktionen, die durch Überschreiben von Methoden aus bestimmten Anbieter Basisklassen und-Schnittstellen definiert werden.

> [!NOTE]
> Informationen zu Anbieter Features, die von PowerShell vordefiniert sind, finden Sie unter [Anbieter Funktionen](/previous-versions//ee126189(v=vs.85)).

## <a name="drive-enabled-providers"></a>Laufwerks aktivierte Anbieter

Anbieter aktivierte Anbieter geben die Standard Laufwerke an, die dem Benutzer zur Verfügung stehen, und ermöglichen dem Benutzer das Hinzufügen oder Entfernen von Laufwerken. In den meisten Fällen sind Anbieter Anbieter aktivierte Anbieter, da Sie für den Zugriff auf den Datenspeicher ein Standard Laufwerk benötigen. Wenn Sie jedoch ihren eigenen Anbieter schreiben, möchten Sie möglicherweise nicht, dass der Benutzer Laufwerke erstellt und entfernt.

Zum Erstellen eines Laufwerks fähigen Anbieters muss die Anbieter Klasse von der [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Klasse oder einer anderen Klasse abgeleitet werden, die von dieser Klasse abgeleitet wird. Die **System. Management. Automation. Provider. drivecmdletprovider** -Klasse definiert die folgenden Methoden zum Implementieren der Standard Laufwerke des Anbieters und zum unterstützen der `New-PSDrive`-und `Remove-PSDrive`-Cmdlets. In den meisten Fällen müssen Sie zur Unterstützung eines Anbieter-Cmdlets die von der PowerShell-Engine aufgerufene Methode überschreiben, um das Cmdlet aufzurufen, wie z. b. die `NewDrive`-Methode für das `New-PSDrive`-Cmdlet, und optional können Sie eine zweite Methode überschreiben, z. b. `NewDriveDynamicParameters`, um dem Cmdlet dynamische Parameter hinzuzufügen

- Die [System. Management. Automation. Provider. drivecmdletprovider. initializedefaultdrives](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) -Methode definiert die Standard Laufwerke, die für den Benutzer verfügbar sind, wenn der Anbieter verwendet wird.

- Mit der [System. Management. Automation. Provider. drivecmdletprovider. newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) -und der [System. Management. Automation. Provider. drivecmdletprovider. newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) -Methode wird definiert, wie der Anbieter das `New-PSDrive` Provider-Cmdlet unterstützt. Dieses Cmdlet ermöglicht dem Benutzer das Erstellen von Laufwerken für den Zugriff auf den Datenspeicher.

- Die [System. Management. Automation. Provider. drivecmdletprovider. removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) -Methode definiert, wie der Anbieter das `Remove-PSDrive` Provider-Cmdlet unterstützt. Dieses Cmdlet ermöglicht dem Benutzer das Entfernen von Laufwerken aus dem Datenspeicher.

## <a name="item-enabled-providers"></a>Element aktivierte Anbieter

Element aktivierte Anbieter ermöglichen es dem Benutzer, die Elemente im Datenspeicher zu erhalten, festzulegen oder zu löschen. Ein "Item" ist ein Element im Datenspeicher, auf das der Benutzer unabhängig zugreifen und es verwalten kann. Um einen Element aktivierten Anbieter zu erstellen, muss die Anbieter Klasse von der [System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Klasse oder einer anderen Klasse abgeleitet werden, die von dieser Klasse abgeleitet wird.

Die **System. Management. Automation. Provider. itemcmdletprovider** -Klasse definiert die folgenden Methoden für die Implementierung spezifischer Anbieter-Cmdlets. In den meisten Fällen müssen Sie zur Unterstützung eines Anbieter-Cmdlets die von der PowerShell-Engine aufgerufene Methode überschreiben, um das Cmdlet aufzurufen, wie z. b. die `ClearItem`-Methode für das `Clear-Item`-Cmdlet, und optional können Sie eine zweite Methode überschreiben, z. b. `ClearItemDynamicParameters`, um dem Cmdlet dynamische Parameter hinzuzufügen

- Die [System. Management. Automation. Provider. itemcmdletprovider. ClearItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) -Methode und die [System. Management. Automation. Provider. itemcmdletprovider. clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) -Methode definieren, wie der Anbieter das `Clear-Item` Provider-Cmdlet unterstützt. Mit diesem Cmdlet kann der Benutzer den Wert eines Elements im Datenspeicher entfernen.

- Die [System. Management. Automation. Provider. itemcmdletprovider. GetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) -Methode und die [System. Management. Automation. Provider. itemcmdletprovider. getitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) -Methode definieren, wie der Anbieter das `Get-Item` Provider-Cmdlet unterstützt. Dieses Cmdlet ermöglicht dem Benutzer das Abrufen von Daten aus dem Datenspeicher.

- Die [System. Management. Automation. Provider. itemcmdletprovider. SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) -Methode und die [System. Management. Automation. Provider. itemcmdletprovider. setitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) -Methode definieren, wie der Anbieter das `Set-Item` Provider-Cmdlet unterstützt. Dieses Cmdlet ermöglicht dem Benutzer, die Werte von Elementen im Datenspeicher zu aktualisieren.

- Die [System. Management. Automation. Provider. itemcmdletprovider. invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) -Methode und die [System. Management. Automation. Provider. itemcmdletprovider. invokedefaultactiondynamicparameters](/dotnet/api/system.management.automation.provider.itemcmdletprovider.invokedefaultactiondynamicparameters) -Methode definieren, wie der Anbieter das `Invoke-Item` Provider-Cmdlet unterstützt. Mit diesem Cmdlet kann der Benutzer die vom Element angegebene Standardaktion ausführen.

- Mit der [System. Management. Automation. Provider. itemcmdletprovider. itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) -und der [System. Management. Automation. Provider. itemcmdletprovider. itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) -Methode wird definiert, wie der Anbieter das `Test-Path` Provider-Cmdlet unterstützt. Mit diesem Cmdlet kann der Benutzer bestimmen, ob alle Elemente eines Pfads vorhanden sind.

Zusätzlich zu den Methoden, die zum Implementieren von Anbieter-Cmdlets verwendet werden, definiert die **System. Management. Automation. Provider. itemcmdletprovider** -Klasse auch die folgenden Methoden:

- Die [System. Management. Automation. Provider. itemcmdletprovider. ExpandPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) -Methode ermöglicht dem Benutzer die Verwendung von Platzhaltern, wenn der Anbieter Pfad angegeben wird.

- Der [System. Management. Automation. Provider. itemcmdletprovider. IsValidPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) wird verwendet, um zu bestimmen, ob ein Pfad syntaktisch und semantisch für den Anbieter gültig ist.

## <a name="container-enabled-providers"></a>Container aktivierte Anbieter

Container aktivierte Anbieter ermöglichen es dem Benutzer, Elemente zu verwalten, die Container sind. Ein Container ist eine Gruppe von untergeordneten Elementen unter einem gemeinsamen übergeordneten Element. Zum Erstellen eines Container fähigen Anbieters muss die Anbieter Klasse von der [System. Management. Automation. Provider. containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) -Klasse oder einer anderen Klasse abgeleitet werden, die von dieser Klasse abgeleitet wird.

> [!IMPORTANT]
> Container aktivierte Anbieter können nicht auf Datenspeicher zugreifen, die Container enthalten. Wenn ein untergeordnetes Element eines Containers ein anderer Container ist, müssen Sie einen Navigations fähigen Anbieter implementieren.

Die **System. Management. Automation. Provider. containercmdletprovider** -Klasse definiert die folgenden Methoden für die Implementierung spezifischer Anbieter-Cmdlets. In den meisten Fällen müssen Sie zur Unterstützung eines Anbieter-Cmdlets die von der PowerShell-Engine aufgerufene Methode überschreiben, um das Cmdlet aufzurufen, wie z. b. die `CopyItem`-Methode für das `Copy-Item`-Cmdlet, und optional können Sie eine zweite Methode überschreiben, z. b. `CopyItemDynamicParameters`, um dem Cmdlet dynamische Parameter hinzuzufügen

- Die [System. Management. Automation. Provider. containercmdletprovider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) -Methode und die [System. Management. Automation. Provider. containercmdletprovider. copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) -Methode definieren, wie der Anbieter das `Copy-Item` Provider-Cmdlet unterstützt. Mit diesem Cmdlet kann der Benutzer ein Element von einem Speicherort in einen anderen kopieren.

- Die [System. Management. Automation. Provider. containercmdletprovider. getchilditems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) -Methode und die [System. Management. Automation. Provider. containercmdletprovider. getchilditemsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) -Methode definieren, wie der Anbieter das `Get-ChildItem` Provider-Cmdlet unterstützt. Dieses Cmdlet ermöglicht dem Benutzer das Abrufen der untergeordneten Elemente des übergeordneten Elements.

- Die [System. Management. Automation. Provider. containercmdletprovider. getchildnames](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) -Methode und die [System. Management. Automation. Provider. containercmdletprovider. getchildnamesdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) -Methode definieren, wie der Anbieter das `Get-ChildItem` Provider-Cmdlet unterstützt, wenn dessen `Name` Parameter angegeben wird.

- Die [System. Management. Automation. Provider. containercmdletprovider. netwitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) -Methode und die [System. Management. Automation. Provider. containercmdletprovider. netwitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) -Methode definieren, wie der Anbieter das `New-Item` Provider-Cmdlet unterstützt. Dieses Cmdlet ermöglicht dem Benutzer das Erstellen neuer Elemente im Datenspeicher.

- Die [System. Management. Automation. Provider. containercmdletprovider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) -Methode und die [System. Management. Automation. Provider. containercmdletprovider. removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) -Methode definieren, wie der Anbieter das `Remove-Item` Provider-Cmdlet unterstützt. Dieses Cmdlet ermöglicht dem Benutzer das Entfernen von Elementen aus dem Datenspeicher.

- Die [System. Management. Automation. Provider. containercmdletprovider. RenameItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) -Methode und die [System. Management. Automation. Provider. containercmdletprovider. renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) -Methode definieren, wie der Anbieter das `Rename-Item` Provider-Cmdlet unterstützt. Mit diesem Cmdlet kann der Benutzer Elemente im Datenspeicher umbenennen.

Zusätzlich zu den Methoden, die zum Implementieren von Anbieter-Cmdlets verwendet werden, definiert die **System. Management. Automation. Provider. containercmdletprovider** -Klasse auch die folgenden Methoden:

- Die [System. Management. Automation. Provider. containercmdletprovider. haschilditems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) -Methode kann von der Provider-Klasse verwendet werden, um zu bestimmen, ob ein Element über untergeordnete Elemente verfügt.

- Die [System. Management. Automation. Provider. containercmdletprovider. convertpath](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) -Methode kann von der Provider-Klasse verwendet werden, um einen neuen anbieterspezifischen Pfad aus einem angegebenen Pfad zu erstellen.

## <a name="navigation-enabled-providers"></a>Navigations aktivierte Anbieter

Navigations aktivierte Anbieter ermöglichen es dem Benutzer, Elemente im Datenspeicher zu verschieben. Um einen Navigations fähigen Anbieter zu erstellen, muss die Anbieter Klasse von der [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse abgeleitet werden.

Die **System. Management. Automation. Provider. navigationcmdletprovider** -Klasse definiert die folgenden Methoden für die Implementierung spezifischer Anbieter-Cmdlets. In den meisten Fällen müssen Sie zur Unterstützung eines Anbieter-Cmdlets die von der PowerShell-Engine aufgerufene Methode überschreiben, um das Cmdlet aufzurufen, wie z. b. die `MoveItem`-Methode für das `Move-Item`-Cmdlet, und optional können Sie eine zweite Methode überschreiben, z. b. `MoveItemDynamicParameters`, um dem Cmdlet dynamische Parameter hinzuzufügen

- Die [System. Management. Automation. Provider. navigationcmdletprovider. muveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) -Methode und die [System. Management. Automation. Provider. navigationcmdletprovider. muveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) -Methode definieren, wie der Anbieter das `Move-Item` Provider-Cmdlet unterstützt. Mit diesem Cmdlet kann der Benutzer ein Element von einem Speicherort im Speicher an einen anderen Speicherort verschieben.

- Die [System. Management. Automation. Provider. navigationcmdletprovider. makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) -Methode definiert, wie der Anbieter das `Join-Path` Provider-Cmdlet unterstützt. Dieses Cmdlet ermöglicht dem Benutzer, ein über-und untergeordnetes Pfad Segment zu kombinieren, um einen Anbieter internen Pfad zu erstellen.

Zusätzlich zu den Methoden, die zum Implementieren von Anbieter-Cmdlets verwendet werden, definiert die **System. Management. Automation. Provider. navigationcmdletprovider** -Klasse auch die folgenden Methoden:

- Die [System. Management. Automation. Provider. navigationcmdletprovider. getchildname](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) -Methode extrahiert den Namen des untergeordneten Knotens eines Pfads.

- Die [System. Management. Automation. Provider. navigationcmdletprovider. getcentpath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) -Methode extrahiert den übergeordneten Teil eines Pfads.

- Die [System. Management. Automation. Provider. navigationcmdletprovider. isitemcontainer](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) -Methode bestimmt, ob es sich bei dem Element um ein Containerelement handelt. In diesem Kontext ist ein Container eine Gruppe von untergeordneten Elementen unter einem gemeinsamen übergeordneten Element.

- Die [System. Management. Automation. Provider. navigationcmdletprovider. normalizerelativepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) -Methode gibt einen Pfad zu einem Element zurück, das relativ zu einem angegebenen Basispfad ist.

## <a name="content-enabled-providers"></a>Inhalts aktivierte Anbieter

Inhalts aktivierte Anbieter ermöglichen es dem Benutzer, den Inhalt von Elementen in einem Datenspeicher zu löschen, zu erhalten oder festzulegen.
Beispielsweise können Sie mit dem File System-Anbieter den Inhalt von Dateien im Dateisystem löschen, erhalten und festlegen. Zum Erstellen eines Inhalts fähigen Anbieters muss ihre Anbieter Klasse die Methoden der [System. Management. Automation. Provider. icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) -Schnittstelle implementieren.

Die **System. Management. Automation. Provider. icontentcmdletprovider** -Schnittstelle definiert die folgenden Methoden für die Implementierung spezifischer Anbieter-Cmdlets. In den meisten Fällen müssen Sie zur Unterstützung eines Anbieter-Cmdlets die von der PowerShell-Engine aufgerufene Methode überschreiben, um das Cmdlet aufzurufen, wie z. b. die `ClearContent`-Methode für das `Clear-Content`-Cmdlet, und optional können Sie eine zweite Methode überschreiben, z. b. `ClearContentDynamicParameters`, um dem Cmdlet dynamische Parameter hinzuzufügen

- Die [System. Management. Automation. Provider. icontentcmdletprovider. ClearContent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) -Methode und die [System. Management. Automation. Provider. icontentcmdletprovider. clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) -Methode definieren, wie der Anbieter das `Clear-Content` Provider-Cmdlet unterstützt. Mit diesem Cmdlet kann der Benutzer den Inhalt eines Elements löschen, ohne das Element zu löschen.

- Die [System. Management. Automation. Provider. icontentcmdletprovider. getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) -Methode und die [System. Management. Automation. Provider. icontentcmdletprovider. getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) -Methode definieren, wie der Anbieter das `Get-Content` Provider-Cmdlet unterstützt. Dieses Cmdlet ermöglicht dem Benutzer das Abrufen des Inhalts eines Elements. Die `System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader`-Methode gibt eine [System. Management. Automation. Provider. icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) -Schnittstelle zurück, die die zum Lesen des Inhalts verwendeten Methoden definiert.

- Die [System. Management. Automation. Provider. icontentcmdletprovider. getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) -Methode und die [System. Management. Automation. Provider. icontentcmdletprovider. getcontentschreiterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) -Methode definieren, wie der Anbieter das `Set-Content` Provider-Cmdlet unterstützt. Dieses Cmdlet ermöglicht dem Benutzer, den Inhalt eines Elements zu aktualisieren. Die `System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter`-Methode gibt eine [System. Management. Automation. Provider. icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) -Schnittstelle zurück, die die Methoden definiert, mit denen der Inhalt geschrieben wird.

## <a name="property-enabled-providers"></a>Eigenschaften aktivierte Anbieter

Eigenschaften aktivierte Anbieter ermöglichen es dem Benutzer, die Eigenschaften der Elemente im Datenspeicher zu verwalten.
Zum Erstellen eines Eigenschafts aktivierten Anbieters muss ihre Anbieter Klasse die Methoden der Schnittstellen [System. Management. Automation. Provider. ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) und [System. Management. Automation. Provider. idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) implementieren. In den meisten Fällen müssen Sie zur Unterstützung eines Anbieter-Cmdlets die von der PowerShell-Engine aufgerufene Methode überschreiben, um das Cmdlet aufzurufen, wie z. b. die `ClearProperty`-Methode für das Clear-Property-Cmdlet, und optional können Sie eine zweite Methode überschreiben, wie `ClearPropertyDynamicParameters`, um dem Cmdlet dynamische Parameter hinzuzufügen.

Die **System. Management. Automation. Provider. ipropertycmdletprovider** -Schnittstelle definiert die folgenden Methoden für die Implementierung spezifischer Anbieter-Cmdlets:

- Die [System. Management. Automation. Provider. ipropertycmdletprovider. clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) -Methode und die [System. Management. Automation. Provider. ipropertycmdletprovider. clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) -Methode definieren, wie der Anbieter das `Clear-ItemProperty` Provider-Cmdlet unterstützt. Dieses Cmdlet ermöglicht dem Benutzer das Löschen des Werts einer Eigenschaft.

- Die [System. Management. Automation. Provider. ipropertycmdletprovider. GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) -Methode und die [System. Management. Automation. Provider. ipropertycmdletprovider. getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) -Methode definieren, wie der Anbieter das `Get-ItemProperty` Provider-Cmdlet unterstützt. Dieses Cmdlet ermöglicht dem Benutzer das Abrufen der Eigenschaft eines Elements.

- Die [System. Management. Automation. Provider. ipropertycmdletprovider. SetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) -Methode und die [System. Management. Automation. Provider. ipropertycmdletprovider. setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) -Methode definieren, wie der Anbieter das `Set-ItemProperty` Provider-Cmdlet unterstützt. Dieses Cmdlet ermöglicht dem Benutzer, die Eigenschaften eines Elements zu aktualisieren.

  Die **System. Management. Automation. Provider. idynamicpropertycmdletprovider** -Schnittstelle definiert die folgenden Methoden für die Implementierung spezifischer Anbieter-Cmdlets:

- Die [System. Management. Automation. Provider. idynamicpropertycmdletprovider. copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) -Methode und die [System. Management. Automation. Provider. idynamicpropertycmdletprovider. copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) -Methode definieren, wie der Anbieter das `Copy-ItemProperty` Provider-Cmdlet unterstützt. Mit diesem Cmdlet kann der Benutzer eine Eigenschaft und ihren Wert von einem Speicherort in einen anderen kopieren.

- Mit der [System. Management. Automation. Provider. idynamicpropertycmdletprovider. muveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) -und der [System. Management. Automation. Provider. idynamicpropertycmdletprovider. muvepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) -Methode wird definiert, wie der Anbieter das Cmdlet "`Move-ItemProperty` Provider" unterstützt. Mit diesem Cmdlet kann der Benutzer eine Eigenschaft und ihren Wert von einem Speicherort an einen anderen verschieben.

- Die [System. Management. Automation. Provider. idynamicpropertycmdletprovider. newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) -Methode und die [System. Management. Automation. Provider. idynamicpropertycmdletprovider. newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) -Methode definieren, wie der Anbieter das `New-ItemProperty` Provider-Cmdlet unterstützt. Mit diesem Cmdlet kann der Benutzer eine neue Eigenschaft erstellen und deren Wert festlegen.

- Die [System. Management. Automation. Provider. idynamicpropertycmdletprovider. RemoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) -Methode und die [System. Management. Automation. Provider. idynamicpropertycmdletprovider. removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) -Methode definieren, wie der Anbieter das `Remove-ItemProperty`-Cmdlet unterstützt. Mit diesem Cmdlet kann der Benutzer eine Eigenschaft und ihren Wert löschen.

- Die [System. Management. Automation. Provider. idynamicpropertycmdletprovider. renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) -Methode und die [System. Management. Automation. Provider. idynamicpropertycmdletprovider. renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) -Methode definieren, wie der Anbieter das `Rename-ItemProperty`-Cmdlet unterstützt. Mit diesem Cmdlet kann der Benutzer den Namen einer Eigenschaft ändern.

## <a name="see-also"></a>Siehe auch

[about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)

[Schreiben eines Windows PowerShell-Anbieters](./writing-a-windows-powershell-provider.md)
