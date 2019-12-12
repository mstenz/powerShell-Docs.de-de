---
title: AccessDBProviderSample03 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e576199-49c7-4355-9686-f9ed40c64a5f
caps.latest.revision: 10
ms.openlocfilehash: aa67bb605f90c1ea40323b4583766069ff1226fb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359989"
---
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

In diesem Beispiel wird gezeigt, wie die Methoden [System. Management. Automation. Provider. itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) und [System. Management. Automation. Provider. itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) überschrieben werden, um Aufrufe an die `Get-Item`-und `Set-Item`-Cmdlets zu unterstützen. Die Anbieter Klasse in diesem Beispiel wird von der [System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Klasse abgeleitet.

## <a name="demonstrates"></a>Gegenstand

> [!IMPORTANT]
> Ihre Anbieter Klasse wird wahrscheinlich von einer der folgenden Klassen abgeleitet und kann möglicherweise andere Anbieter Schnittstellen implementieren:
>
> -   [System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Klasse.
> -   [System. Management. Automation. Provider. containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) -Klasse. Siehe [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse. Siehe [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Weitere Informationen zum Auswählen der Anbieter Klasse, von der basierend auf den Anbieter Features abgeleitet werden soll, finden [Sie unter Entwerfen des Windows PowerShell-Anbieters](./provider-types.md).

Dieses Beispiel zeigt die folgenden Vorgänge:

- Deklarieren des `CmdletProvider` Attributs.

- Definieren einer Anbieter Klasse, die von der [System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Klasse abgeleitet wird.

- Überschreiben der [System. Management. Automation. Provider. drivecmdletprovider. newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) -Methode, um das Verhalten des `New-PSDrive`-Cmdlets zu ändern, sodass der Benutzer neue Laufwerke erstellen kann. (In diesem Beispiel wird nicht gezeigt, wie dem `New-PSDrive`-Cmdlet dynamische Parameter hinzugefügt werden.)

- Überschreiben der [System. Management. Automation. Provider. drivecmdletprovider. removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) -Methode, um das Entfernen vorhandener Laufwerke zu unterstützen.

- Überschreiben der [System. Management. Automation. Provider. itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) -Methode, um das Verhalten des `Get-Item`-Cmdlets zu ändern, sodass der Benutzer Elemente aus dem Datenspeicher abrufen kann. (In diesem Beispiel wird nicht gezeigt, wie dem `Get-Item`-Cmdlet dynamische Parameter hinzugefügt werden.)

- Überschreiben der [System. Management. Automation. Provider. itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) -Methode, um das Verhalten des `Set-Item`-Cmdlets zu ändern, sodass der Benutzer die Elemente im Datenspeicher aktualisieren kann. (In diesem Beispiel wird nicht gezeigt, wie dem `Get-Item`-Cmdlet dynamische Parameter hinzugefügt werden.)

- Überschreiben der [System. Management. Automation. Provider. itemcmdletprovider. itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) -Methode, um das Verhalten des `Test-Path`-Cmdlets zu ändern. (In diesem Beispiel wird nicht gezeigt, wie dem `Test-Path`-Cmdlet dynamische Parameter hinzugefügt werden.)

- Überschreiben der [System. Management. Automation. Provider. itemcmdletprovider. IsValidPath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) -Methode, um zu bestimmen, ob der angegebene Pfad gültig ist.

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie Sie die Methoden überschreiben, die zum Abrufen und Festlegen von Elementen in einer Microsoft Access-Datenbank erforderlich sind.

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. Provider. containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Entwerfen Ihres Windows PowerShell-Anbieters](./provider-types.md)
