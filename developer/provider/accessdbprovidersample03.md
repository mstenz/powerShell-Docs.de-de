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
ms.openlocfilehash: 57b6cfaa5f29300c60a5a745797111b6beba3133
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859406"
---
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

Dieses Beispiel zeigt, wie die [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) und [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) Methoden zum Aufrufen von unterstützen die `Get-Item` und `Set-Item` Cmdlets. Die Anbieterklasse in diesem Beispiel ist abgeleitet von der [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse.

## <a name="demonstrates"></a>Veranschaulicht

> [!IMPORTANT]
> Ihre Anbieterklasse wird wahrscheinlich von einem der folgenden Klassen abgeleitet werden und möglicherweise andere anbieterschnittstellen implementieren:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse.
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) Klasse. Finden Sie unter [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) Klasse. Finden Sie unter [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Weitere Informationen zum auswählen die Anbieterklasse basierend auf Funktionen des Datenanbieters abgeleitet, finden Sie unter [Entwerfen Ihrer Windows PowerShell-Anbieter](./provider-types.md).

Dieses Beispiel zeigt Folgendes:

- Deklarieren der `CmdletProvider` Attribut.

- Definieren eine abgeleitete Anbieterklasse die [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse.

- Überschreiben der [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) Methode zum Ändern des Verhaltens von der `New-PSDrive` -Cmdlet, sodass des Benutzers neue Datenträger erstellen. (Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `New-PSDrive` Cmdlet.)

- Überschreiben der [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) Methode zum Entfernen der vorhandenen Laufwerke zu unterstützen.

- Überschreiben der [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) Methode zum Ändern des Verhaltens von der `Get-Item` -Cmdlet, sodass der Benutzer Elemente aus dem Datenspeicher abgerufen werden sollen. (Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `Get-Item` Cmdlet.)

- Überschreiben der [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) Methode zum Ändern des Verhaltens von der `Set-Item` -Cmdlet, sodass der Benutzer zum Aktualisieren der Elemente im Datenspeicher. (Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `Get-Item` Cmdlet.)

- Überschreiben der [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) Methode zum Ändern des Verhaltens von der `Test-Path` Cmdlet. (Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `Test-Path` Cmdlet.)

- Überschreiben der [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) Methode, um zu bestimmen, ob der angegebene Pfad gültig ist.

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie die Methoden zum Abrufen und Festlegen von Elementen in einer Microsoft Access-Basis erforderlich.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Entwerfen Ihre Windows PowerShell-Anbieter](./provider-types.md)