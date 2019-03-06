---
title: 'Vorgehensweise: Erstellen einer Windows PowerShell-Anbieter | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide]
- providers [PowerShellProgrammer's Guide], creating
- Windows PowerShell Programmer's Guide, providers
ms.assetid: 863e48e9-7206-4c6a-a59a-2ab2d30396bc
caps.latest.revision: 5
ms.openlocfilehash: 286df63e75d6372cb41c974e60e79b02bd13686e
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429668"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>Erstellen eines Windows PowerShell-Anbieters

Dieser Abschnitt beschreibt, wie Sie einen Windows PowerShell-Anbieter zu erstellen. Ein Windows PowerShell-Anbieter kann auf zweierlei Weise betrachtet werden. Für den Benutzer stellt den Anbieter für einen Satz von gespeicherten Daten. Die gespeicherten Daten können beispielsweise der Metabasis der Internetinformationsdienste (Internet Information Services, IIS), Microsoft Windows-Registrierung, das Windows-Dateisystem, Active Directory und die Variable und Alias-Daten, die von Windows PowerShell gespeichert sein.

Für den Entwickler ist der Windows PowerShell-Anbieter die Schnittstelle zwischen dem Benutzer und die Daten, die der Benutzer muss den Zugriff auf. Aus dieser Perspektive unterstützt jede Art von Anbieter, die in diesem Abschnitt beschriebenen einen Satz von bestimmten Basisklassen und Schnittstellen, mit denen die Windows PowerShell-Laufzeit zu bestimmten Cmdlets, die dem Benutzer eine gängige Methode verfügbar zu machen.

## <a name="providers-provided-by-windows-powershell"></a>Anbieter von Windows PowerShell bereitgestellt

Windows PowerShell stellt mehrere Anbieter (z. B. der FileSystem-Anbieter, Registrierungsanbieter und Alias-Anbieter), die verwendet werden, um bekannte Datenspeicher zugreifen. Weitere Informationen zu den vom Windows PowerShell-Anbietern verwenden Sie den folgenden Befehl, um die Onlinehilfe zugreifen:

**PS > Get-Help About_provider**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>Zugreifen auf den gespeicherten Daten mithilfe von Windows PowerShell-Pfaden

Windows PowerShell-Anbieter sind zugegriffen werden kann, um die Windows PowerShell-Laufzeit und Befehle programmgesteuert durch die Verwendung von Windows PowerShell-Pfaden. In den meisten Fällen, werden diese Pfade verwendet, um die Daten direkt über den Anbieter zugreifen. Allerdings können einige Pfade in internen Anbieter-Pfade aufgelöst sein, mit die ein Cmdlet aus, um nicht - Windows PowerShell für Anwendungsprogrammierschnittstellen (APIs) zu verwenden, um die Daten zugreifen können. Weitere Informationen zur Verarbeitung von Windows PowerShell-Anbietern innerhalb von Windows PowerShell finden Sie unter [Funktionsweise von Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>Verfügbarmachen von Anbieter-Cmdlets, die mithilfe von Windows PowerShell-Laufwerke

Ein Windows PowerShell-Anbieter macht die unterstützten Cmdlets, die mit virtuellen Windows-PowerShell-Laufwerke verfügbar. Die folgenden Regeln für ein Windows PowerShell-Laufwerk wird von Windows PowerShell angewendet:

- Der Namen eines Laufwerks kann eine beliebige Sequenz alphanumerisch sein.

- Ein Laufwerk kann an einem beliebigen gültigen Punkt ein "Path" Namens eine "Root" angegeben werden.

- Ein Laufwerk kann für alle gespeicherten Daten, nicht nur im Dateisystem implementiert werden.

- Jedes Laufwerk verfolgt die eigenen aktuellen arbeitsstandort festgelegt, damit der Benutzer Kontext beibehalten, zwischen Laufwerken verschoben.

## <a name="in-this-section"></a>In diesem Abschnitt

Die folgende Tabelle enthält Themen, die Codebeispiele enthalten, die aufeinander aufbauen. Das zweite Thema ab, die grundlegende Windows PowerShell-Anbieter initialisiert und von der Windows PowerShell-Laufzeit nicht initialisiert werden kann, im nächste Thema fügt Funktionen für den Zugriff auf die Daten, im nächste Thema fügt Funktionen zum Bearbeiten der Daten (hinzu. die Elemente in der gespeicherten Daten), und so weiter.

|Thema|Definition|
|-----------|----------------|
|[Entwerfen Ihre Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md)|Dieses Thema beschreibt Dinge, die Sie berücksichtigen sollten, bevor Sie einen Windows PowerShell-Anbieter implementieren. Es werden zusammengefasst, die Windows PowerShell-Anbieter-Basisklassen und Schnittstellen, die verwendet werden.|
|[Erstellen einen einfachen Windows PowerShell-Anbieter](./creating-a-basic-windows-powershell-provider.md)|In diesem Thema veranschaulicht, wie einen Windows PowerShell-Anbieter zu erstellen, der können die Windows PowerShell-Laufzeit zu initialisieren und die Aufhebung der Initialisierung des Anbieters.|
|[Erstellen eines Anbieters der Windows PowerShell-Laufwerk](./creating-a-windows-powershell-drive-provider.md)|In diesem Thema veranschaulicht, wie einen Windows PowerShell-Anbieter erstellen, der dem Benutzer ermöglicht, einen Datenspeicher über ein Windows PowerShell-Laufwerk zugreifen.|
|[Erstellen eine Windows PowerShell-Elementanbieter](./creating-a-windows-powershell-item-provider.md)|In diesem Thema veranschaulicht, wie einen Windows PowerShell-Anbieter erstellen, der dem Benutzer ermöglicht, die Elemente in einem Datenspeicher zu bearbeiten.|
|[Erstellen eine Windows PowerShell-Containeranbieter](./creating-a-windows-powershell-container-provider.md)|In diesem Thema veranschaulicht, wie einen Windows PowerShell-Anbieter erstellen, der dem Benutzer ermöglicht, die auf mehreren Ebenen Datenspeichern arbeiten.|
|[Erstellen eine Windows PowerShell-Navigationsanbieter](./creating-a-windows-powershell-navigation-provider.md)|In diesem Thema veranschaulicht, wie einen Windows PowerShell-Anbieter erstellen, der dem Benutzer ermöglicht, die Elemente eines Datenspeichers auf hierarchische Weise zu navigieren.|
|[Erstellen eines Anbieters der Windows PowerShell-Inhalte](./creating-a-windows-powershell-content-provider.md)|In diesem Thema veranschaulicht, wie einen Windows PowerShell-Anbieter erstellen, der dem Benutzer ermöglicht, den Inhalt von Elementen in einem Datenspeicher zu bearbeiten.|
|[Erstellen eines Anbieters der Windows PowerShell-Eigenschaft](./creating-a-windows-powershell-property-provider.md)|In diesem Thema veranschaulicht, wie einen Windows PowerShell-Anbieter erstellen, der dem Benutzer ermöglicht, die die Eigenschaften von Elementen in einem Datenspeicher zu bearbeiten.|

## <a name="see-also"></a>Weitere Informationen

[Funktionsweise von Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell Handbuch für Programmierer](./windows-powershell-programmer-s-guide.md)