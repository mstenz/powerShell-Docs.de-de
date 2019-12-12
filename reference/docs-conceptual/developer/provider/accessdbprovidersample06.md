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
ms.openlocfilehash: 9c00ec6de987729fec42dc57245a949d11e31f4b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366329"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

In diesem Beispiel wird gezeigt, wie Inhalts Methoden überschrieben werden, um Aufrufe der Cmdlets `Clear-Content`, `Get-Content`und `Set-Content` zu unterstützen. Diese Methoden sollten implementiert werden, wenn der Benutzer den Inhalt der Elemente im Datenspeicher verwaltet muss. Die Anbieter Klasse in diesem Beispiel wird von der [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse abgeleitet und implementiert die [System. Management. Automation. Provider. icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) -Schnittstelle.

## <a name="demonstrates"></a>Gegenstand

> [!IMPORTANT]
> Ihre Anbieter Klasse wird wahrscheinlich von einer der folgenden Klassen abgeleitet und kann möglicherweise andere Anbieter Schnittstellen implementieren:
>
> -   [System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Klasse. Siehe [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   [System. Management. Automation. Provider. containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) -Klasse. Siehe [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse.
>
> Weitere Informationen zum Auswählen der Anbieter Klasse, von der basierend auf den Anbieter Features abgeleitet werden soll, finden [Sie unter Entwerfen des Windows PowerShell-Anbieters](./provider-types.md).

Dieses Beispiel zeigt die folgenden Vorgänge:

- Deklarieren des `CmdletProvider` Attributs.

- Definieren einer Anbieter Klasse, die von der [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse abgeleitet wird und die die [System. Management. Automation. Provider. icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) -Schnittstelle deklariert.

- Überschreiben der [System. Management. Automation. Provider. icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) -Methode, um das Verhalten des `Clear-Content`-Cmdlets zu ändern, sodass der Benutzer den Inhalt aus einem Element entfernen kann. (In diesem Beispiel wird nicht gezeigt, wie dem `Clear-Content`-Cmdlet dynamische Parameter hinzugefügt werden.)

- Überschreiben der [System. Management. Automation. Provider. icontentcmdletprovider. getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) -Methode, um das Verhalten des `Get-Content`-Cmdlets zu ändern, sodass der Benutzer den Inhalt eines Elements abrufen kann. (In diesem Beispiel wird nicht gezeigt, wie dem `Get-Content`-Cmdlet dynamische Parameter hinzugefügt werden.)

- Überschreiben der [Microsoft. PowerShell. Commands. filesystemprovider. getcontentwriter *](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) -Methode, um das Verhalten des `Set-Content`-Cmdlets zu ändern, sodass der Benutzer den Inhalt eines Elements aktualisieren kann. (In diesem Beispiel wird nicht gezeigt, wie dem `Set-Content`-Cmdlet dynamische Parameter hinzugefügt werden.)

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie Sie die Methoden überschreiben, die zum Löschen, abrufen und Festlegen des Inhalts von Elementen in einer Microsoft Access-Datenbasis erforderlich sind.

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. Provider. containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Entwerfen Ihres Windows PowerShell-Anbieters](./provider-types.md)
