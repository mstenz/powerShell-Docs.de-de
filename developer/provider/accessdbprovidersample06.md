---
title: AccessDBProviderSample06 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: f020f023f9a379ff8a610edb7d5dcfe207170394
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080984"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

Dieses Beispiel zeigt, wie inhaltsmethoden um Aufrufe unterstützen die `Clear-Content`, `Get-Content`, und `Set-Content` Cmdlets. Diese Methoden sollten implementiert werden, wenn der Benutzer den Inhalt der Elemente im Datenspeicher verwaltet muss. Die Anbieterklasse in diesem Beispiel ist abgeleitet von der [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse und implementiert die [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) Schnittstelle.

## <a name="demonstrates"></a>Zeigt

> [!IMPORTANT]
> Ihre Anbieterklasse wird wahrscheinlich von einem der folgenden Klassen abgeleitet werden und möglicherweise andere anbieterschnittstellen implementieren:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse. Finden Sie unter [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) Klasse. Finden Sie unter [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) Klasse.
>
> Weitere Informationen zum auswählen die Anbieterklasse basierend auf Funktionen des Datenanbieters abgeleitet, finden Sie unter [Entwerfen Ihrer Windows PowerShell-Anbieter](./provider-types.md).

Dieses Beispiel zeigt Folgendes:

- Deklarieren der `CmdletProvider` Attribut.

- Definieren eine abgeleitete Anbieterklasse die [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) darstellt und deklariert die [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) Schnittstelle.

- Überschreiben der [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) Methode zum Ändern des Verhaltens von der `Clear-Content` -Cmdlet, damit der Benutzer den Inhalt von einem Element zu entfernen. (Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `Clear-Content` Cmdlet.)

- Überschreiben der [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) Methode zum Ändern des Verhaltens von der `Get-Content` -Cmdlet, sodass der Benutzer zum Abrufen des Inhalts eines Elements. (Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `Get-Content` Cmdlet.).

- Überschreiben der [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) Methode zum Ändern des Verhaltens von der `Set-Content` -Cmdlet, damit der Benutzer den Inhalt eines Elements aktualisieren. (Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `Set-Content` Cmdlet.)

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie die Methoden zum deaktivieren, erhalten, und legen Sie den Inhalt von Elementen in einer Microsoft Access Basis erforderlich.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Entwerfen Ihre Windows PowerShell-Anbieter](./provider-types.md)