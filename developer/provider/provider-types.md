---
title: Anbietertypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 37689571eb1650e5991af2e7002cd037ae99dd68
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057959"
---
# <a name="provider-types"></a>Anbietertypen

Anbieter definiert die grundlegende Funktionen durch Ändern der Durchführung ihrer Aktionen in die Anbieter-Cmdlets (bereitgestellt vom Windows PowerShell). Anbieter können z. B. die Standardfunktionalität der verwenden die `Get-Item` -Cmdlet, oder sie können ändern, wie dieses Cmdlet ausgeführt wird, wenn Sie Elemente aus dem Datenspeicher abrufen. Die Anbieterfunktionalität, die in diesem Thema beschriebenen enthält Funktionen, die durch Überschreiben der Methoden aus bestimmten Anbieter-Basisklassen und Schnittstellen definiert.

> [!NOTE]
> Anbieter-Features, die von Windows PowerShell vorab definiert sind, finden Sie unter [Funktionen des Anbieters](http://msdn.microsoft.com/en-us/864e4807-554a-4016-80ea-bf643a090fc6).

## <a name="drive-enabled-providers"></a>Anbieter fähigen

Fähigen Anbieter geben Sie die Standard-Laufwerke zur Verfügung, die dem Benutzer und ermöglicht dem Benutzer hinzufügen oder Entfernen von Laufwerken. In den meisten Fällen sind Anbieter-fähigen Anbieter aus, da sie einige Standard-Laufwerk, auf den Datenspeicher erfordern. Jedoch wenn Sie Ihren eigenen Anbieter schreiben Sie möglicherweise oder sollten Sie ermöglicht dem Benutzer zum Erstellen und entfernen die Laufwerke nicht.

Um einen-fähigen Anbieter erstellen, muss Ihre Anbieterklasse von abgeleitet werden die [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Klasse oder eine andere Klasse, die von dieser Klasse abgeleitet ist. Die [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Klasse definiert die folgenden Methoden für die Standard-Laufwerke des Anbieters zu implementieren und unterstützen die `New-PSDrive` und `Remove-PSDrive` Cmdlets. In den meisten Fällen ein Anbieter-Cmdlets unterstützen Sie müssen Überschreiben der Methode, die die Windows PowerShell-Engine aufgerufen wird, das-Cmdlet aufrufen, wie z. B. die `NewDrive` -Methode für die `New-PSDrive` -Cmdlet, und optional auch Sie können eine zweite Methode, wie z. B. überschreiben`NewDriveDynamicParameters`, für das Hinzufügen von dynamischer Parameters an das Cmdlet.

- Die [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) Methode definiert die Standard-Laufwerke, die für den Benutzer verfügbar sind, wenn der Anbieter verwendet wird.

- Die [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) und [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) Methoden definiert, wie Ihr Anbieter unterstützt die `New-PSDrive` Anbieter-Cmdlet. Mit diesem Cmdlet können den Benutzer, Laufwerke, auf den Datenspeicher zu erstellen.

- Die [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) Methode definiert, wie Ihr Anbieter unterstützt die `Remove-PSDrive` Anbieter-Cmdlet. Mit diesem Cmdlet können Laufwerke aus dem Datenspeicher entfernt.

## <a name="item-enabled-providers"></a>Providers Element aktiviert

Element-fähigen Anbieter ermöglichen den Benutzer abrufen, festlegen oder deaktivieren Sie die Elemente im Datenspeicher. Eine "Item" ist ein Element des Datenspeichers, die der Benutzer Zugriff auf oder unabhängig verwalten kann. Um ein Element aktiviert-Anbieter zu erstellen, muss Ihre Anbieterklasse von abgeleitet werden die [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse oder eine andere Klasse, die von dieser Klasse abgeleitet ist.

Die [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse definiert die folgenden Methoden zum Implementieren von bestimmten Anbieter-Cmdlets. In den meisten Fällen ein Anbieter-Cmdlets unterstützen Sie müssen Überschreiben der Methode, die die Windows PowerShell-Engine aufgerufen wird, das-Cmdlet aufrufen, wie z. B. die `ClearItem` -Methode für die `Clear-Item` -Cmdlet, und optional auch Sie können eine zweite Methode, wie z. B. überschreiben`ClearItemDynamicParameters`, für das Hinzufügen von dynamischer Parameters an das Cmdlet.

- Die [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) und [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) Methoden Definieren Sie, wie Ihr Anbieter unterstützt die `Clear-Item` Anbieter-Cmdlet. Mit diesem Cmdlet können die Benutzer das Entfernen des Werts eines Elements im Datenspeicher.

- Die [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) und [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) definieren Sie Methoden wie Ihr Anbieter unterstützt die `Get-Item` Anbieter-Cmdlet. Mit diesem Cmdlet können Benutzer Daten aus dem Datenspeicher abrufen.

- Die [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) und [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) definieren Sie Methoden wie Ihr Anbieter unterstützt die `Set-Item` Anbieter-Cmdlet. Mit diesem Cmdlet können den Benutzer zum Aktualisieren der Werte der Elemente im Datenspeicher.

- Die [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) und [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) Methoden Definieren Sie, wie Ihr Anbieter unterstützt die `Invoke-Item` Anbieter-Cmdlet. Mit diesem Cmdlet können den Benutzer zum Ausführen der Standardaktion, die durch das Element angegeben.

- Die [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) und [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) Methoden Definieren Sie, wie Ihr Anbieter unterstützt die `Test-Path` Anbieter-Cmdlet. Mit diesem Cmdlet können den Benutzer zu bestimmen, ob alle Elemente eines Pfads vorhanden sind.

  Zusätzlich zu den Methoden zum Implementieren von Anbieter-Cmdlets, die [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Klasse definiert außerdem die folgenden Methoden:

- Die [System.Management.Automation.Provider.Itemcmdletprovider.Expandpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) Methode ermöglicht dem Benutzer, die Platzhalter verwenden, wenn Sie den Pfad des Anbieters angeben.

- Die [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) wird verwendet, um zu bestimmen, ob ein Pfad syntaktisch und semantisch für den Anbieter gültig ist.

## <a name="container-enabled-providers"></a>Container-fähigen Anbieter

Container-fähigen Anbieter können Benutzer zum Verwalten von Elementen, die Container sind. Ein Container ist eine Gruppe von untergeordneten Elementen unter einem gemeinsamen übergeordneten Element. Um einen Container aktivierte Anbieter erstellen, muss Ihre Anbieterklasse von abgeleitet werden die [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) Klasse oder eine andere Klasse, die von dieser Klasse abgeleitet ist.

> [!IMPORTANT]
> Container-fähigen Anbieter können nicht Datenspeicher zugreifen, die geschachtelte Container enthalten. Wenn ein untergeordnetes Element eines Containers ein weiterer Container ist, müssen Sie einen Anbieter Navigation aktiviert implementieren.

Die [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) Klasse definiert die folgenden Methoden zum Implementieren von bestimmten Anbieter-Cmdlets. In den meisten Fällen ein Anbieter-Cmdlets unterstützen Sie müssen Überschreiben der Methode, die die Windows PowerShell-Engine aufgerufen wird, das-Cmdlet aufrufen, wie z. B. die `CopyItem` -Methode für die `Copy-Item` -Cmdlet, und optional auch Sie können eine zweite Methode, wie z. B. überschreiben`CopyItemDynamicParameters`, für das Hinzufügen von dynamischer Parameters an das Cmdlet.

- Die [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) und [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) definiert Methoden, wie Ihr Anbieter unterstützt die `Copy-Item` Anbieter-Cmdlet. Mit diesem Cmdlet können den Benutzer ein Element von einem Speicherort in einen anderen zu kopieren.

- Die [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) und [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) Methoden definieren, wie Ihr Anbieter unterstützt die `Get-ChildItem` Anbieter-Cmdlet. Mit diesem Cmdlet können Benutzer die untergeordneten Elemente des übergeordneten Elements abrufen.

- Die [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) und [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) Methoden definieren, wie Ihr Anbieter unterstützt die `Get-ChildItem` Anbieter-Cmdlet wenn seine `Name` Parameter angegeben ist.

- Die [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) und [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) definiert Methoden, wie Ihr Anbieter unterstützt die `New-Item` Anbieter-Cmdlet. Mit diesem Cmdlet können den Benutzer zum Erstellen neuer Elemente im Datenspeicher.

- Die [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) und [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) definiert Methoden, wie Ihr Anbieter unterstützt die `Remove-Item` Anbieter-Cmdlet. Mit diesem Cmdlet können Elemente aus dem Datenspeicher entfernt.

- Die [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) und [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) definiert Methoden, wie Ihr Anbieter unterstützt die `Rename-Item` Anbieter-Cmdlet. Mit diesem Cmdlet können den Benutzer, die Elemente im Datenspeicher umbenannt werden.

  Zusätzlich zu den Methoden zum Implementieren von Anbieter-Cmdlets, die [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) -Klasse definiert außerdem die folgenden Methoden:

- Die [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) Methode kann von der Provider-Klasse verwendet werden, um zu bestimmen, ob ein Element über untergeordnete Elemente verfügt.

- Die [System.Management.Automation.Provider.Containercmdletprovider.Convertpath*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) Methode kann von der Provider-Klasse verwendet werden, um einen neuen Anbieter-spezifischen Pfad aus einem angegebenen Pfad erstellen.

## <a name="navigation-enabled-providers"></a>Navigation-fähigen Anbieter

Navigation-fähigen Anbieter können Benutzer Elemente im Datenspeicher zu verschieben. Um einen Navigation-fähigen Anbieter erstellen, muss Ihre Anbieterklasse von abgeleitet werden die [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) Klasse.

Die [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) Klasse definiert die folgenden Methoden zum Implementieren von bestimmten Anbieter-Cmdlets. In den meisten Fällen ein Anbieter-Cmdlets unterstützen Sie müssen Überschreiben der Methode, die die Windows PowerShell-Engine aufgerufen wird, das-Cmdlet aufrufen, wie z. B. die `MoveItem` -Methode für die `Move-Item` -Cmdlet, und optional auch Sie können eine zweite Methode, wie z. B. überschreiben`MoveItemDynamicParameters`, für das Hinzufügen von dynamischer Parameters an das Cmdlet.

- Die [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) und [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) definiert Methoden, wie Ihr Anbieter unterstützt die `Move-Item` Anbieter-Cmdlet. Mit diesem Cmdlet können den Benutzer ein Element von einem Speicherort im Speicher an einen anderen Speicherort zu verschieben.

- Die [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) Methode definiert, wie Ihr Anbieter unterstützt die `Join-Path` Anbieter-Cmdlet. Mit diesem Cmdlet können den Benutzer auf einem übergeordneten und untergeordneten Pfadsegment zum Erstellen eines internen Anbieter-Pfads zu kombinieren.

  Zusätzlich zu den Methoden zum Implementieren von Anbieter-Cmdlets, die [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse definiert außerdem die folgenden Methoden:

- Die [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) -Methode extrahiert den Namen des untergeordneten Knotens eines Pfads.

- Die [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) -Methode extrahiert die übergeordneten Teil eines Pfads.

- Die [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) Methode bestimmt, ob das Element ein Containerelement ist. In diesem Kontext ist ein Container für eine Gruppe von untergeordneten Elementen unter einem gemeinsamen übergeordneten Element.

- Die [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) Methode gibt einen Pfad zu einem Element, das relativ zu einer angegebenen Basis-Pfad zurück.

## <a name="content-enabled-providers"></a>Inhalts-fähigen Anbieter

Inhalts-fähigen Anbieter erlauben Sie dem Benutzer zu löschen, abrufen, oder legen Sie den Inhalt von Elementen in einem Datenspeicher. Beispielsweise können mit der FileSystem-Anbieter Sie deaktivieren, erhalten, und legen Sie den Inhalt der Dateien im Dateisystem. Um einen aktivierten Inhaltsanbieter erstellen zu können, muss Ihrer Anbieterklasse die Methoden der implementieren die [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) Schnittstelle.

Die [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) Schnittstelle definiert die folgenden Methoden zum Implementieren von bestimmten Anbieter-Cmdlets. In den meisten Fällen ein Anbieter-Cmdlets unterstützen Sie müssen Überschreiben der Methode, die die Windows PowerShell-Engine aufgerufen wird, das-Cmdlet aufrufen, wie z. B. die `ClearContent` -Methode für die `Clear-Content` -Cmdlet, und optional auch Sie können eine zweite Methode, wie z. B. überschreiben`ClearContentDynamicParameters`, für das Hinzufügen von dynamischer Parameters an das Cmdlet.

- Die [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) und [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)Methoden definieren, wie Ihr Anbieter unterstützt die `Clear-Content` Anbieter-Cmdlet. Mit diesem Cmdlet können Benutzer den Inhalt eines Elements zu löschen, ohne das Element zu löschen.

- Die [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) und [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) Methoden definieren, wie Ihr Anbieter unterstützt die `Get-Content` Anbieter-Cmdlet. Mit diesem Cmdlet können Benutzer den Inhalt eines Elements abrufen. Die [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) Methode gibt ein [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) Schnittstelle, die definiert die Methoden verwendet, um den Inhalt zu lesen.

- Die [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) und [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) Methoden definieren, wie Ihr Anbieter unterstützt die `Set-Content` Anbieter-Cmdlet. Mit diesem Cmdlet können Benutzer den Inhalt eines Elements zu aktualisieren. Die [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) Methode gibt ein [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) Schnittstelle, die definiert die Methoden zum Schreiben des Inhalts verwendet wird.

## <a name="property-enabled-providers"></a>Anbieter-Eigenschaft aktiviert

Eigenschaft-fähigen Anbieter können Benutzer die Eigenschaften der Elemente im Datenspeicher verwalten. Zum Erstellen eines Anbieters-Eigenschaft aktiviert muss Ihrer Anbieterklasse die Methoden implementieren die [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) und [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) Schnittstellen. In den meisten Fällen ein Anbieter-Cmdlets unterstützen Sie müssen Überschreiben der Methode, die die Windows PowerShell-Engine aufgerufen wird, das-Cmdlet aufrufen, wie z. B. die `ClearProperty` -Methode für das Cmdlet Clear-Eigenschaft, und optional auch Sie können eine zweite Methode, wie z. B. überschreiben`ClearPropertyDynamicParameters`, für das Hinzufügen von dynamischer Parameters an das Cmdlet.

Die [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) Schnittstelle definiert die folgenden Methoden zum Implementieren von bestimmten Anbieter-Cmdlets:

- Die [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) und [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) Methoden definieren, wie Ihr Anbieter unterstützt die `Clear-ItemProperty` Anbieter-Cmdlet. Mit diesem Cmdlet können Benutzer den Wert einer Eigenschaft zu löschen.

- Die [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) und [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)Methoden definieren, wie Ihr Anbieter unterstützt die `Get-ItemProperty` Anbieter-Cmdlet. Mit diesem Cmdlet können Benutzer die Eigenschaft eines Elements abrufen.

- Die [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) und [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)Methoden definieren, wie Ihr Anbieter unterstützt die `Set-ItemProperty` Anbieter-Cmdlet. Mit diesem Cmdlet können den Benutzer zum Aktualisieren der Eigenschaften eines Elements.

  Die [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) Schnittstelle definiert die folgenden Methoden zum Implementieren von bestimmten Anbieter-Cmdlets:

- Die [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) und [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) Methoden definieren, wie Ihr Anbieter unterstützt die `Copy-ItemProperty` Anbieter-Cmdlet. Mit diesem Cmdlet können den Benutzer auf eine Eigenschaft und der Wert von einem Speicherort in einen anderen zu kopieren.

- Die [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) und [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) Methoden definieren, wie Ihr Anbieter unterstützt die `Move-ItemProperty` Anbieter-Cmdlet. Mit diesem Cmdlet können den Benutzer eine Eigenschaft und der Wert von einem Speicherort an einen anderen verschiebt.

- Die [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) und [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) Methoden definieren, wie Ihr Anbieter unterstützt die `New-ItemProperty` Anbieter-Cmdlet. Dieses Cmdlet ermöglicht den Benutzer eine neue Eigenschaft erstellen, und legen Sie dessen Wert an.

- Die [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) und [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) Methoden definieren, wie Ihr Anbieter unterstützt die `Remove-ItemProperty` Cmdlet. Mit diesem Cmdlet können Benutzer eine Eigenschaft und den Wert zu löschen.

- Die [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) und [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) Methoden definieren, wie Ihr Anbieter unterstützt die `Rename-ItemProperty` Cmdlet. Mit diesem Cmdlet können den Benutzer, den Namen einer Eigenschaft zu ändern.

## <a name="see-also"></a>Weitere Informationen

[Schreiben Sie ein Windows PowerShell-Anbieter](./writing-a-windows-powershell-provider.md)