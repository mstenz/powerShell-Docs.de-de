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
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733737"
---
# <a name="windows-powershell-reference"></a>Windows PowerShell-Referenz

Windows PowerShell handelt es sich um eine Microsoft .NET Framework-verbundenen Umgebung für die administrative Automatisierung. Windows PowerShell bietet es sich um einen neuen Ansatz für Befehle erstellen, Erstellen von Lösungen und grafische Schnittstelle der richtlinienbasierten Verwaltung-Tools erstellen.

Windows PowerShell ermöglicht Systemadministratoren zum Automatisieren der Verwaltung von Systemressourcen durch die Ausführung von Befehlen entweder direkt oder über Skripts.

## <a name="developer-audience"></a>Entwicklerzielgruppe

Für Befehl Entwickler, die Informationen zu den APIs von Windows PowerShell benötigen, wird die Windows PowerShell Software Development Kit (SDK) geschrieben. Befehls-Entwickler verwenden Windows PowerShell zum Erstellen sowohl Befehle als auch Anbieter, die die Aufgaben zu erweitern, die von Windows PowerShell ausgeführt werden können.

## <a name="windows-powershell-resources"></a>Windows PowerShell-Ressourcen

Die folgenden Ressourcen bieten zusätzlich zu Windows PowerShell SDK Weitere Informationen.

[Erste Schritte mit Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) bietet eine Einführung in Windows PowerShell: die Sprache, die Cmdlets, Anbieter und die Verwendung von Objekten.

[Schreiben ein Windows PowerShell-Modul](./module/writing-a-windows-powershell-module.md) enthält Informationen und Beispiele für Administratoren, Skriptentwickler und Cmdlet-Entwickler, die zum Verpacken und verteilen ihre Windows PowerShell-Lösungen mithilfe von Windows PowerShell-Module benötigen.

[Schreiben eines Windows PowerShell-Cmdlets](./cmdlet/writing-a-windows-powershell-cmdlet.md) bietet Informationen und Codebeispiele, Programm-Managern, die Cmdlets entwerfen und für Entwickler, die Cmdlet-Code implementieren.

[Windows PowerShell-Teamblog](https://blogs.msdn.microsoft.com/PowerShell/) die beste Ressource für sowie für die Zusammenarbeit mit anderen Windows PowerShell-Benutzern. Lesen Sie den Windows PowerShell-Team-Blog ein, und verknüpfen Sie anschließend die Windows PowerShell-Benutzerforum (microsoft.public.windows.powershell). Verwenden Sie Windows Live Search, um andere Windows PowerShell-Blogs und Ressourcen zu suchen. Klicken Sie dann Ihre Kenntnisse bei der Entwicklung bringen Sie kostenlos Ihre Ideen.

[PowerShell-modulbrowser](/powershell/module/) bietet die neuesten Versionen der Befehlszeilentools Hilfethemen.

## <a name="class-libraries"></a>Klassenbibliotheken

[System.Management.Automation](/dotnet/api/System.Management.Automation) dieser Namespace ist der Stammnamespace für Windows PowerShell. Es enthält die Klassen, Enumerationen und Schnittstellen zum Implementieren von benutzerdefinierten Cmdlets erforderlich. Insbesondere die [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) -Klasse ist die Basisklasse, von welchem Cmdlet allen Klassen abgeleitet werden müssen. Weitere Informationen zu den Cmdlets finden Sie unter.

[System.Management.Automation.Provider](/dotnet/api/System.Management.Automation.Provider) dieser Namespace enthält die Klassen, Enumerationen und Schnittstellen erforderlich, um ein Windows PowerShell-Anbieter implementiert. Insbesondere die [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) Klasse ist die Basisklasse, die von der alle Windows PowerShell-Anbieterklassen abgeleitet werden müssen.

[Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) dieser Namespace enthält die Klassen für die Cmdlets und Anbieter von Windows PowerShell implementiert. Auf ähnliche Weise, es wird empfohlen, die Erstellung einer *IhrName*. Namespace-Befehle für diese Cmdlets, die Sie implementieren.

[System.Management.Automation.Host](/dotnet/api/System.Management.Automation.Host) dieser Namespace enthält die Klassen, Enumerationen und Schnittstellen, die mit dem-Cmdlet wird verwendet, um die Interaktion zwischen Benutzer und Windows PowerShell zu definieren.

[System.Management.Automation.Internal](/dotnet/api/System.Management.Automation.Internal) dieser Namespace enthält die Basisklassen, die von anderen Namespaceklassen verwendet. Z. B. die [System.Management.Automation.Internal.Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute) -Klasse ist die Basisklasse für die [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) Klasse.

[System.Management.Automation.Runspaces](/dotnet/api/System.Management.Automation.Runspaces) dieser Namespace enthält die Klassen, Enumerationen und Schnittstellen, die für eine Windows PowerShell-Runspace zu erstellen. In diesem Kontext ist der Windows PowerShell-Runspace des Kontexts, in denen eine oder mehrere Windows PowerShell-Pipelines Cmdlets aufzurufen. Das heißt, arbeiten Cmdlets im Kontext einer Windows PowerShell-Runspace. Weitere Informationen AboutWindows PowerShell-Runspaces, finden Sie unter [Windows PowerShell-Runspaces](https://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9).
