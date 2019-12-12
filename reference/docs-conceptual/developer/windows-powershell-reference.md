---
title: Windows PowerShell-Referenz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell SDK
ms.assetid: cbba4879-bcac-484a-9906-4bbe2cd1eb33
caps.latest.revision: 11
ms.openlocfilehash: 48b2b2b9ab2a39cf185ed54bcfa99d46562e13b6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366279"
---
# <a name="windows-powershell-reference"></a>Windows PowerShell-Referenz

Windows PowerShell ist eine mit Microsoft .NET Framework verbundene Umgebung, die für die administrative Automatisierung konzipiert ist. Windows PowerShell bietet einen neuen Ansatz für das Erstellen von Befehlen, das Erstellen von Lösungen und das Erstellen grafischer, auf der Benutzeroberfläche basierender Verwaltungs Tools.

Mithilfe von Windows PowerShell kann ein Systemadministrator die Verwaltung von Systemressourcen durch die Ausführung von Befehlen entweder direkt oder über Skripts automatisieren.

## <a name="developer-audience"></a>Entwicklerzielgruppe

Das Windows PowerShell Software Development Kit (SDK) wird für Befehls Entwickler geschrieben, die Referenzinformationen zu den von Windows PowerShell bereitgestellten APIs benötigen. Befehls Entwickler verwenden Windows PowerShell zum Erstellen von Befehlen und Anbietern, mit denen die von Windows PowerShell auszuführenden Aufgaben erweitert werden.

## <a name="windows-powershell-resources"></a>Windows PowerShell-Ressourcen

Zusätzlich zum Windows PowerShell SDK bieten die folgenden Ressourcen weitere Informationen.

[Einstieg in Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) Bietet eine Einführung in Windows PowerShell: die Sprache, die Cmdlets, die Anbieter und die Verwendung von Objekten.

[Schreiben eines Windows PowerShell-Moduls](./module/writing-a-windows-powershell-module.md) Bietet Informationen und Beispiele für Administratoren, Skriptentwickler und Cmdlet-Entwickler, die Ihre Windows PowerShell-Lösungen mithilfe von Windows PowerShell-Modulen Verpacken und verteilen müssen.

[Schreiben eines Windows PowerShell-Cmdlets](./cmdlet/writing-a-windows-powershell-cmdlet.md) Enthält Informationen und Codebeispiele für Programm-Manager, die Cmdlets entwerfen, sowie für Entwickler, die Cmdlet-Code implementieren.

[Windows PowerShell-Teamblog](https://blogs.msdn.microsoft.com/PowerShell/) Die beste Ressource für das Erlernen von und die Zusammenarbeit mit anderen Windows PowerShell-Benutzern. Lesen Sie den Windows PowerShell-Teamblog, und nehmen Sie am Windows PowerShell-Benutzer Forum Teil (Microsoft. public. Windows. PowerShell). Verwenden Sie Windows Live Search, um weitere Windows PowerShell-Blogs und-Ressourcen zu finden. Wenn Sie Ihr Know-how entwickeln, können Sie Ihre Ideen kostenlos einbringen.

[PowerShell-Modul Browser](/powershell/module/) Stellt die neuesten Versionen der Hilfe Themen für die Befehlszeile bereit.

## <a name="class-libraries"></a>Klassenbibliotheken

[System. Management. Automation](/dotnet/api/System.Management.Automation) dieser Namespace ist der Stamm Namespace für Windows PowerShell. Sie enthält die Klassen, Enumerationen und Schnittstellen, die erforderlich sind, um benutzerdefinierte Cmdlets zu implementieren. Insbesondere die [System. Management. Automation. Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) -Klasse ist die Basisklasse, von der alle Cmdlet-Klassen abgeleitet werden müssen. Weitere Informationen zu-Cmdlets finden Sie unter.

[System. Management. Automation. Provider](/dotnet/api/System.Management.Automation.Provider) dieser Namespace enthält die Klassen, Enumerationen und Schnittstellen, die erforderlich sind, um einen Windows PowerShell-Anbieter zu implementieren. Insbesondere die [System. Management. Automation. Provider. cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) -Klasse ist die Basisklasse, von der alle Windows PowerShell-Anbieter Klassen abgeleitet werden müssen.

[Microsoft. PowerShell. Commands](/dotnet/api/Microsoft.PowerShell.Commands) dieser Namespace enthält die Klassen für die Cmdlets und Anbieter, die von Windows PowerShell implementiert werden. Ebenso empfiehlt es sich, einen *yourname*zu erstellen. Der Befehle-Namespace für die Cmdlets, die Sie implementieren.

[System. Management. Automation. Host](/dotnet/api/System.Management.Automation.Host) dieser Namespace enthält die Klassen, Enumerationen und Schnittstellen, die vom Cmdlet zum Definieren der Interaktion zwischen dem Benutzer und Windows PowerShell verwendet werden.

[System. Management. Automation. Internal](/dotnet/api/System.Management.Automation.Internal) dieser Namespace enthält die Basisklassen, die von anderen Namespace Klassen verwendet werden. Beispielsweise ist die [System. Management. Automation. Internal. Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute) -Klasse die Basisklasse für die [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) -Klasse.

[System. Management. Automation. Runspaces](/dotnet/api/System.Management.Automation.Runspaces) dieser Namespace enthält die Klassen, Enumerationen und Schnittstellen, die verwendet werden, um einen Windows PowerShell-Runspace zu erstellen. In diesem Kontext ist der Windows PowerShell-Runspace der Kontext, in dem eine oder mehrere Windows PowerShell-Pipelines Cmdlets aufrufen. Das heißt, dass Cmdlets im Kontext eines Windows PowerShell-Runspace funktionieren. Weitere Informationen zu Windows PowerShell-Runspaces finden Sie unter [Windows PowerShell-Runspaces](https://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9).
